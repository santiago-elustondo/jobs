Mortgage Cadence - Architect and implement new features on an enterprise fintech application according to client specifications. - Stack includes: GraphQL / Angular / .NET 


* reduce number of loansession requests caused by hcm
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/12013](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/12013)
    * Problem: 
        * Grids and HCMs currently perform `loansession` requests on mount to get their data, instead of going through the central DataService used by other controls. 
        * This affects performance for a number of reasons: 
            * Requests for loan data for these controls are not being made until the controls are mounted, which occurs after the other required page data has arrived. If these requests were initiated earlier, page loading would finish earlier.
            * Each grid/hcm will perform its own requests independently, which can result in dozens of requests if numerous instances are present. this is detrimental to performance for 3 reasons:
                * Browsers have a simultaneous request limit, meaning that some requests will be stalled until some are complete. This occurs very often in these cases, frequently at least doubling the wait time.
                * Every time a request comes back, it triggers change detection in the angular app, which is an CPU-intensive process, given the number of components present on most pages.
                * The backend has to handle numerous requests to serve loan data for the page. serving a single request would be much faster, since all the loan data is all in the same place (redis cache) 
    * Solution:
        * As soon as we get the ScreenMeta info, before mounting any controls, we are already able to tell what data we will need for the page. The controls themselves only read this ScreenMeta object to figure out what they need to load. To make this request faster, we traverse through the ScreenMeta object, find all instances of HCMs or Grids, and make a list of all the loan paths that need to be fetched. All of these requests then are made in a single request, before mounting the page controls. 
        * In DataEntryService, as part of the screen loading process, we have a method getAuxiliaryDataRequirementsForScreen(), which traverses the ScreenMeta object and collects extra data that should be loaded for a screen. For every instance of a grid control that we find, we add all the binding paths to the list of IAuxiliaryDataRequirements. 


```
if ([
    hierarchyContentManager.ControlTypeId.value
  ].includes(controlMeta.screenBuilderControlTypeId.value)
) controlRequirements.push(
  ...createLoanDataRequirementsFromHCMMeta(controlMeta)
);

if ([
    dashboardGridConfig.ControlTypeId.value,
    sbLoanEntryDataGrid.ControlTypeId.value
 ].includes(controlMeta.screenBuilderControlTypeId.value)
) controlRequirements.push(
    ...createLoanDataRequirementsFromGridMeta(controlMeta)
);

```



        * We then batch them all into one request using LoanService.GetLoanPaths


```
public async effect_LoadLoanPaths(args: {
    loanDataRequirements: Array<ILoanDataRequirement>
}) {
    return new Promise(resolve => {
        this.loanService.GetLoanPaths(
            args.loanDataRequirements.map(req => req.bindingPath)
        ).subscribe(resolve);
    });
}

```



* After firing these requests, we proceed with mounting the controls. The controls now subscribe to be notified when their data is ready using HierarchyService.NotifyWhenAllAreLoaded, instead of triggering the request directly using LoanService.GetLoanPaths.


```
this.loanService.HierarchyService.NotifyWhenAllAreLoaded(...this.columns.map(c => c.BindingPath)).subscribe(done => {

```



* batched timeouts
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11688](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11688)
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11663](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11663)
    * textboxes, labels, bindablecontrols
    * Problem: 
        * A number of page control components call setTimeout() on mount. When multiple instances of these types of controls are present, a large number of setTimeout() calls are made where the handlers perform very small operations, usually a class property update, and are each followed by a round of change detection, which is CPU-intensive.
        * Examples: BindableTextbox, HCM, BindableLabel, BindableDataGrid, BindableControl
    * Solution:
        * By introducing the BatchedTimeoutService, we are able to batch setTimeout() calls. Timers scheduled to fire at the same time are fired as a single timer, each handler called synchronously, followed by a single change detection run.
        * Applying the solution is as simple as injecting the BatchedTimeoutService, and replacing problematic instances of setTimeout() by this.batchedTimeoutService.setTimeout()


![alt_text](images/image1.png "image_tooltip")




        * The BatchedTimeoutService works by setting a timer for each setTimeout requested, but also remembering when each timeout is scheduled for and what its handler is. When a timer fires, it doesn't just execute the handler for that timer, it also looks through all scheduled timeouts, and, for each timeout that was scheduled to happen already, all their handlers are called and their timers cancelled.
* batched lookups
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11567](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11567)
    * Problem:
        * A number of page controls require `lookups` data, which provide the options to show for dropdowns among other things. Network requests for `lookups` are made by each control on mount, resulting in a large number of such requests being made by pages that have numerous such controls on it. This is a performance liability because of the request throttling which a browser will do when many requests are queued, and because every HXR request will trigger change detection on completion, which is CPU-intensive.
    * Controls:
        * bindable field label
        * comboboxes
        * grids
    * Solution
        * As soon as we get the ScreenMeta object from the initial screen request, which gives us all the control configurations, we traverse through the control meta tree and identify all the controls that will need `lookups` data, we then make a single request for all of these lookups at once, and store them. We have the controls get their `lookups` data from the cache, instead of making their own requests.
        * To accomplish this we add the above logic to DataEntryService, and add an graph query on the backend to provide lookups for multiple binding paths at once

            
![alt_text](images/image2.png "image_tooltip")


* hostlisteners
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11146](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11146)
    * Problem: 
        * Angular @hostlisteners are used throughout the app to handle global events like keypresses and click. This is a performance issue because when one of these global events is fired, CD is performed after each individual handler, which is unnecessary and expensive. When page controls use this decorator, and numerous instances are present on a page, a large number of CD cycles are performed as a response to almost every user action, causing very poor responsiveness, taking more than a second to react to click and keypresses. All the relevant handlers should be called but only 1 CD should run as a response to this event.
    * Solution: 
        * A central service was created "EventListenerService", which registers global native listeners and calls each listener synchronously, triggering only 1 CD run after all have executed. \

![alt_text](images/image3.png "image_tooltip")

        * To use this service, we only need to inject the service, subscribe to a supported event, and make sure to unsubscribe when no longer needed.
        * 
![alt_text](images/image4.png "image_tooltip")

* session timers 
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10898](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10898)
    * Problem: 
        * Session timeouts are meant to end a session after the user has been inactive for a certain amount of time. This was previously implemented by listening to the global listeners for mousemove and keydown, and resetting the timer every time any of these fired. The problem with this approach is that every mousemove event, which get fired many times per second when the user is moving the mouse, would trigger change detection.
    * Solution:
        * rewrite this logic (SessionTimeoutService) such that all of these event handlers occur "outside of angular", and we only trigger CD when the user session is actually ended and the app needs to react.


![alt_text](images/image5.png "image_tooltip")
 \




* spinners
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11150](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11150)
    * Problem:
        * The app spinners (concentric circles) were previously implemented in a very poorly performing manner, which contributed greatly to loading times and lack of app responsiveness. The actual animation was achieved by setting intervals 15 milliseconds apart, during which the css was updated using javascript, causing CD to occur as well. This was a heavy CPU burden, even more so when multiple spinners were present at once.
    * Solution
        * rewrite Spinner component to use svg animations, which are natively implemented and do not cause change detection.


![alt_text](images/image6.png "image_tooltip")




* layout recalcs from hcm
    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10892](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10892)
    * Problem:
        * HCMs called expensive javascript functions (certain functions in javascript require synchronous style recalculation, which is cpu-intensive) during every change detection cycle, unnecessarily. This was put in place to enable height adjustment and enable animations when toggling between details view and grid view.
    * Solution:
        * Rewrite relevant HCM code to not call these functions during every change detection cycle, but instead only once after load and once when switching between details view and grid view. This is possible because if we render the content while keeping it hidden, we can still get its height, and then we can store the result of our query for later use, instead of recalculating every time.

* spinner
    * currently:
        * loading spinners (concentric circles) currently fire a timer every 15 milliseconds to recalc next animation position and draw, causing change detection every time.
    * consequence:
        * animation is choppy because this is cpu intensive (too much work to move circles), also not perfectly timed because timers are not serviced in guaranteed intervals (it doesnt actually fire every 15ms if cpu is clogged).
        * it takes up cpu time that slows down everything else
    * solution:
        * change spinner.ts to use css keyframe animation, or a gif, or at least to run outside of angular (running outside of angular would require changing the update strategy, because it currently relies on angular bindings).
    * AC:
        * spinner does not cause js activity? at least does not cause CD.
        * 
![alt_text](images/image1.png "image_tooltip")

* network requests
    * currently: 
        * many independent requests are made, in multiple rounds, during initial screen load, after controls have been mounted.
    * conseq:
        * when each request is resolved, it triggers a lot of CD, extending unreponsive period and delaying next round of requests.
    * solution
        * perform all these requests before mounting controls, and preferably outside of angular. add some sort of loader method that takes care of loading all necessary data for a screen so that controls dont have to ask for it on mount.
    * AC: 
        * screen controls are not mounted before all necessary data is collected.
    * 
![alt_text](images/image2.png "image_tooltip")

* hostlistener
    * currently
        * datagrid registers a callback to the global document click event using @hostlistener. angular does CD after each individual @hostlistener callback has been called.. (why?). furthermore even if no action was taken by the listener, CD is performed on that grid even if onpush is on, because the event is considered as being within the purview of that component, or something.
    * problems
        * clicking anywhere on the screen (even when it does nothing) will freeze the browser for 1s~ (not counting all the other events like mouse move etc, this is just click)
    * solutions
        * listen for document clicks in a service that emits an event and runs all the handlers synchronously before doing a single CD run.
        * figure out why we need to listen for clicks everywhere and only listen when we have to.
    * 
![alt_text](images/image3.png "image_tooltip")
