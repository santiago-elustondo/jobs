

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
