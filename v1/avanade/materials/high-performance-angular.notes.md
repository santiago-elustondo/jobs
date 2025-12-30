
* presentation
    * [https://myoffice.accenture.com/:p:/r/personal/santiago_elustondo_accenture_com/_layouts/15/Doc.aspx?sourcedoc=%7BC6C36697-DD8A-4ADA-8E5E-CC8BE02E6A83%7D&file=Dev%20Fridays%20-%20High%20Performance%20Angular.pptx&action=edit&mobileredirect=true](https://myoffice.accenture.com/:p:/r/personal/santiago_elustondo_accenture_com/_layouts/15/Doc.aspx?sourcedoc=%7BC6C36697-DD8A-4ADA-8E5E-CC8BE02E6A83%7D&file=Dev%20Fridays%20-%20High%20Performance%20Angular.pptx&action=edit&mobileredirect=true)
* timeline (52 minutes)
    * content (47 minutes)
        * intro (2 minutes, 3:05)
        * what is performance (2 minutes, 3:07)
        * javascript fundamentals (5 minutes, 3:13)
        * frameworks and angular (10 minutes, 3:23)
        * general strategy (10 minutes, 3:33)
        * live overall before exploration (5 minutes, 3:38)
        * case studies (10 minutes, 3:48)
        * live overall after demo + remaining issues (3 minutes, 3:51)
    * questions (5 minutes)
* execution plan
    * we get prepared for our next subsection while the other is giving his, this way we can have examples ready to go, especially the live ones) 
* todo
    * finish content
* prepare how long we devote to each section
* prepare slides / drawings / code snippets
* prepare raw js examples
* prepare angular basic examples
* prepare live before / after
* prepare prerecorded case-study files

 



* for big improvement show 3
    * before any enhancements
    * after enhancements before wait to load grids
    * after wait to load grids
* content
    * **[S1] intro:** my name is santiago elustondo, i'm from mooseheads in toronto, and my team has been working in-part on performance improvements for mcp, this pi we've been working on a rewrite of the grids found on most mcp pages.
        * i'll be talking about some of the most important performance considerations when working on an angular app or really any modern browser app. everything i'll be covering today applies also to react and vue.js, since these frameworks operate internally in a comparable way, although there will be different names used for similar concepts. I'll try to point out how some of the concepts we touch on translate into these other frameworks as we go through them.
        * also we will be looking at mcp-specific case studies to see how these problems and solutions play out in the real world.
        * i'll be using chrome dev tools for most demonstrations. for anyone that isn't familiar with the features of chrome dev tools that we are using, i will be giving short explanations of what information is available, and encourage anyone to stop me at any time to ask questions about what we're currently looking at. just put up your hand on teams, and i'll make sure to circle around before moving changing what's on the screen.
    * Theory (examples here are basic angular app same version)
        * **[S2-T] goals // definition of performance (responsiveness, action fulfillment): **Ok, so what do we mean by performance in the context of a client application? We might mean one of two things, action fulfillment and/or responsiveness.
            * **[S3] action fulfillment:** How long does it take to fulfill user requests, for example some large computation, or, more commonly, make some requests and present some data or message from an API.
            * **[S4] responsiveness: **How fast do we show feedback to user  events/actions, like hover effects, and initial reactions to clicks. in other words, how fast how do me make it clear to the user that we have registered their action and are working on  it, if it needs time to complete, otherwise we want to show the requested UI right away.
                * Are transitions/animations smooth?
                    * Some performance bottlenecks will cause a drop in the application frame-rate, which again makes an application feel
            * **[S5] conflicts: **As we will come to see shortly, these 2 ways of measuring performance often conflict, and one may be increased by a sacrifice to the other. In client applications, responsiveness is usually more important to the user than action fulfillment speed. It is frustrating to click or tap on a button and feel that the application is "frozen", with no indication of what's happening. A user will generallly perceive an app as being of higher quality if it reacts quickly to the touch, has smooth UI transitions, even if it may present loading indicators for longer periods of time. 
        * **[S6-T] factors // resources (network, cpu).**
            * **[S7 -ST] cpu: **The central factor we usually consider when examining the performance of any application is cpu usage. cpu cycles are a finite resource for a given period of time.
                * **[S8] single threaded, event-driven and synchronous** 
                    * this is true for all javascript execution, including server-side.
                    * Javascript is single-threaded, which means an instance of JS runtime (aka: one javascript-machine) will only use 1 core, and can only execute one instruction at a time. Now, you may obviously spawn multiple instances, running the same or different code, but these instances do not share an execution context, which means references are not accessible across threads, unlike other programming languages.
                    * all Javascript execution begins with the initial execution of the file containing JS, or by a "Function Call" (AKA javascript event) done by the engine, where some JS handler is executed by the engine. function calls happen when an event with a registered callback function that is popped from the event waiting queue by the runtime engine.
                    * events are added to the waiting queue by our code, by native APIs like the DOM in the browser, user input, or network events including databases and redis connections in the case of node. 
                    * every registered event handler for a popped event will fire its own "function call" (javascript event), so one event could have multiple javascript runtime stacks associated with it. EVENTS THAT ARE NOT SUBSCRIBED TO DO NOT CALL THE JS THREAD AT ALL (no javascript events, the event did not happen as far as javascript is concerned).
                    * a common misconception is that javascript is an asynchronous language. in fact it is synchronous and blocking. the thread will execute every line of the event handler from first to last, and will not let go of the thread until reaching the last line, unlike other languages, which will make system calls and only execute the next line after it has been fulfilled (like an implicit "await" statement in modern JS and other languages). it is asynchronous only in that the external things that might put events in the queue are often asynchronous, for example network requests and user actions, and event handlers often fire in inconsistent orders.
                    * part of the synchronous work of the javascript thread while it is executing a handler is to schedule timeout events and add event handlers for native events. this is done via the classic JS setTimeout function, which synchronously adds a native "timeout", which means that the engine will add an event with a callback to the queue when the timeout has elapsed. setTimeouts do not guarantee it will fire at the scheduled time, but some time after that, because if there are other things in the queue, or currently executing, it cannot fire.
                    * [examples]
                        * examples
                            * 2 listeners on same event
                            * 3 timeouts at same time
                        * notes
                            * notice i am using incognito, because otherwise you might see events coming from installed extensions.
                            * the profiler uses a sampler, it will periodically check the current call stack and draw out what it found, so it may miss very short function calls.
                * **painting**
                    * The brower spawns one thread per tab, which means a browser application mainly relies on one thread for everything. other things can have their own threads as well, like extensions and web-workers.
                    * in a browser, the javascript engine is deeply integrated with the DOM, and so this same "thread" is used for executing JS code as well as painting the page, so it's more than just a javascript runtime, there are native APIs sharing this thread.
                        * [example: delayed UI rendering if cpu clogged]
                    * these are handled by the same thread, but by the native browser implementation, which is written in a lower level language and optimized.
                        * performing animations of DOM elements in javascript is usually a bad idea of this reason. [example]
                    * some js operations do "system calls" but only for things that share its thread (other parts of browser engine, like console.logs, paints, and alerts), operations are expensive, more so than pure javascript logic
                        * DOM updates / console logs
                        * javascript layout recalc
                            * some javascript functions are a lot more expensive than others. an expensive one, for example, is console.log, which is many thousands of times times slower than an empty function (it takes 1 millisecond to do a console.log in chrome with devtools open)
                                * [https://stackoverflow.com/questions/11426185/will-console-log-reduce-javascript-execution-performance/53476667](https://stackoverflow.com/questions/11426185/will-console-log-reduce-javascript-execution-performance/53476667)
                            * but the most expensive ones are layout recalc functions
                            * [layout recalc impact]
                * **requestIdleCallback() / requestAnimationFrame()**
                * **(short) garbage collection**
                    * hard to control since this is engine specific and not specified by ECMA
                    * but rule of thumb is that if youre doing a long recursion or iteration that must be done synchronously, thats when you watch for your memory usage inside function closures.
                * **(short) multithreading**
                    * javascript is single threaded, so to take advantage of multi-cores, you could run multiple instances, but they do not share memory as in C++ of Java, you can't reference the same variable, that's why it's called a single threaded lang. different javascript engines provide different ways of passing data across threads, you can use special APIs like SharedArrayBuffer in nodejs, or the postMessage() api on the browser.
                    * browser JS threads communicate through "messages" api (which is also used by chrome extensions) so your extensions are running in their own context, with their own variables, and can run in parallel, just like your worker threads.
                    * in node you can achieve a similar result in node with child_processes
                    * this is a good use for webassembly, since we're talking about cpu-intensive activities that can benefit a lot from the performance, while user interfaces are still usually better served by DOM/javascript, because of very powerful profiling and debugging capabilities of browser devtools. 
            * **network**
                * request limit
                    * this is mostly a request fulfillment drag
                    * [snapshot: request limit]
                * events triggered
                    * this is mostly a responsiveness drag
        * frameworks + angular
            * CD
                * **problem of ui reconciliation:** 
                    * browsers do not provide native binding to UI, instead they represent the current UI as a tree of elements called the DOM, which must be queried and updated imperatively through the DOM API.
                    * so the primary problem in complex JS apps that modern frameworks like React, Vue and Angular is abstracting this step of updating UI, and turn it into a declarative statement that will reconcile the DOM state with some javascript state.
                    * since we want to modularize our UI, all of these frameworks moduralize by mapping a "component" with a DOM node, such that reconciling this component will update that DOM node and its children
                    * these libraries provide a templating feature that allows us to declare a JS function that maps some javascript state into the DOM operations needed for reconciliation.
                        * in react, this is defined as a render function
                        * in angular the html template is compiled into functionally the same thing as a render function (you might have heard compilation in angular in the context of AOT compilation vs in-browser compilation. here they are talking both about typescript compilation into javascript as well as template compilation into render functions)
                        * [code snapshots: templates compiled]
                            * comparing template source and compiled, get from ng-basic
                            * also react render compiled
                    * the problem now becomes deciding when we should perform reconciliation  (run the render function, checking if we need to update the UI, and performing the updates synchronously). since this is JS code, and will block cpu (and 
                    * DOM mutations are expensive), we want to be smart about it.
                    * language note:
                        * the words "render" "check" and "reconciled" are used quite interchangeably, they just come from different frameworks
                * **tree-traversal / onpush**
                    * every CD run will traverse the component tree from the top, reconciling the component a component, which updates the inputs it's providing its children as well as the DOM nodes it controls directly, and then recursing into each child.
                        * [drawings: trees with arrows pointing down to each component, traversing depth-first]
                    * in order to make the traversal more efficient, all these frameworks provide ways to skip entire branches. traversal will skip a component and all of its children if during traversal it encounters a component that does not need to be checked.
                        * the different frameworks use the same overall approach to determine which components need rendering.
                        * react pure component, should component update / angular
                    * [code snippet for onpush setting]
                    * [drawing of tree]
                        * markForCheck()
                    * note that many developers get confused about when the lifecycle hooks fire, like ngAfterViewChecked(), and instead you want to check by using the {{render()}} trick.
                        * [code snippet for render trick]
                * **trackby / render-keys**
                * **[transition title slide] now the problem becomes, when to reconcile?**
                    * the problem now becomes deciding when we should perform reconciliation  (run the render function, checking if we need to update the UI, and performing the updates synchronously). since this is JS code, and will block cpu (and DOM mutations are expensive), we want to be smart about it.
                    * language note:
                        * the words "render" "check" and "reconciled" are used quite interchangeably, they just come from different frameworks
                    * here's where the major frameworks start to differentiate from each other
                * **react**
                    * react has a simple solution for this, every component will be reconciled whenever it's setState function is called or its props are updated (keep in mind this is only when using pure components, otherwise also whenever any of its parents calls setState). note that if you update a component object property like in angular, it won't reconcile.
                * **angular complexity**
                    * angular makes it a little harder for itself by not having a setState function, such that the properties of the component class are magically kept up date in UI, without having to call any special functions. also, angular supports 2-way data binding with NgModel, which further complicates things (2 way data binding means that your js state is kept up to date with the ui, in reverse fashion). 
                * **zone / angular change detection**
                    * zone itself for a long time was a separate project from angular itself, although it has now been integrated into the angular monorepo.
                    * monkey patches all methods
                        * what is monkey-patching?
                            * all global variables are properties of "window". calling a variable that does not exist in the current function scope is interpreted as *thing = *window.*thing*
                            * [code snippet]
                        * it monkey patches all the javascript methods that can queue an event and wrap the callback such that it can do some stuff before and after the actual event handler.
                        * [example in basic ng app]
                            * in console, and in stacktrace we can show monkeypatch
                        * if it doenst monkeypatch something, it won't run in zone (requestIdleCallback() isnt monkeypatched by our version of angular, so you need to run callback insize ngZone, there are other examples. google apis used to be a problem here, because it called onload in the html script attribute, which wasnt monkeypatched)
                        * it exists to provide separate "execution contexts" within one JS runtime. "You can think of it as [thread-local storage](http://en.wikipedia.org/wiki/Thread-local_storage) for JavaScript VMs." - summary sentence from repo docs.
                        * So basically, using this library you can create a "zone", where all async callbacks registered when the code is running in that "zone", are also in that "zone". you can use this to store data that is specific to that "zone", or register hooks to execute before or after any event callbacks.
                            * [code snippet: instantiate new zone]
                            * [example basic angular app: create a new zone from root]
                    * ngZone
                        * zones are useful to angular because it uses this as a trigger for CD, running CD at the end of every event, and thus ensuring that the UI is always up to date
                        * angular uses 1 zone, called ngZone. ngZone is a zone that has change detection registered at the end of every event handler.
                            * [example basic angular app: all timeouts and events will cause CD]
                        * runoutsideangular() / ngzone.run()
                            * these methods will switch zones synchronously. it switches the monkeypatching of all event registrations between root zone and ngzone, execute the code inside the callback function synchronously, and then put them back to continue the next line. any events handlers registered in the callback function will be executed in the other zone, and the hooks for the other zone are called before coming back. only events that occur within ngZone trigger change detection.
                            * [example: switching in and out of zone, put debuggers so we can see what happens when you call these: settimeout, etc change; zone.current changes.] the signalr service is a good example of this, though it wasn't written by us.
                    * change detection runs from the top of the component tree (and also from the top of all the ones marked for check) after every javascript event has completed, that way we can't possibly miss anything.
                    * we can also perform reconciliation synchronously for a specific component 
                * usually this is the bottleneck, other bottlenecks (like some very inefficient function that we run explicitly outside of reconciliation) are easier to fix.
                    * [performance snapshot image: sorting/grouping are seemingly expensive computations, but are insignificant when seen beside the CD cycle that follows them.]
                * fiber in react: requestIdleCallback() / requestAnimationFrame()
    * general strategy
        * items:
            * prioritize responsiveness: dont do work you dont need to, or if you do, and its low-priority, use requestIdleCallback()
                * it is common that action fulfillment and responsiveness will conflict with each other
                * example of waiting to load grids
                    * we can mount all the grids synchronously in one go, which will get the job done faster at the expense of a longer period of no response.
            * dont use setTimeouts or setIntervals carelessly
                * share them (we will discuss a strategy for sharing them using batchedTimeoutService)
                * run them outside of zone
                * [example: batched timeouts]
            * a lot of events can be listened to outsideOfAngular, when you need to react, you then go back inside angular. useful especially if these events dont need reaction most of the time. 
                * example: we are listening to a websocket stream, but we dont care about most of the messages.
                * [code snippet or example: runOutsideAngular()]
            * use css animations, or at least intervals outside of angular
            * dont do unnecessary work during CD (like a non-cached function call in the template)
                * especially javascript style recalc
                * [example: expensive CD]
            * dont use @hostlisteners in angular 8
                * [example in basic ng app]
            * use onpush as much as possible
                * [example in basic ng app]
            * try to avoid using application.tick, or detectChanges, since they might end up being called multiple times in the same event.  use markforcheck() instead.
                * uses for detectChanges or tick is when you're doing something, and then you need to update the UI in order to continue. for example, you toggle a state flag that mounts a button with *ngIf, and then you immediately want to grab the reference to that button.
                * in most cases we can rework this logic to do the same job asynchronously, and dont need to do that.
                * [example: tick()]
            * use onpush
                * [? example: onpush] (or in CD theory part)
            * using trackby is important
                * [? example: trackby] (or in CD theory part)
            * use less simultaneous HXR requests where possible 
                * or run them outside angular and fire one completion event inside angular. this is useful if you are using an API you dont control. 
                    * example: we added an endpoint that gets lookups for multiple binding paths, which every dropdown was calling individually.
            * its a good idea to give all functions names, so that they can be traced in stacktraces and performance profiles, rather than anon funcs
            * rxjs as well as zone, can obfuscate a stacktrace and make it harder to figure out what's going on when debugging or analysing performance. not much we can do about zone, but we can avoid rxjs when unnecessary.
            * use immutable patterns for state management. this means never mutate a state data object, but copy and replace it. this is not slower because you can recursively copy all the references of the children that are not changing. basically the guarantee behind the immutability pattern is that if two things are equal by reference, they they are equal in value, even recursively. this allows us to update our state and, if all our children are on-push, to have only the children that need to reconcile to do so, because they actually got a new reference value in its input	
                * [example: basic ng]
        * invisible issues matter
            * the user/developer/QA might not notice them when they first appear, because they dont affect overall performance  but they dont scale, so we will experience them they are accentuated by other issues. 
                * we will see examples of this. for example, if you're reacting to mousemove events and calling change detection on every event, the app might still be responsive while CD is cheap, but as soon as something else adds load to CD, all of the sudden this problem will show.
    * overall before
        * pages
            * sitemap
                * [http://localhost:5000/DataEntry/SiteMap?ActiveLoanId=3000000009](http://localhost:5000/DataEntry/SiteMap?ActiveLoanId=3000000009)
            * employment and income
                * [http://localhost:5000/DataEntry/Collection/d0ca83f8-bf6d-4c6e-8b62-7fd719961649/ScreenBuilderScreen/84e4ad7b-e428-40e2-9504-b1259f72d210?ActiveLoanId=3000000009&InitialLoad=true](http://localhost:5000/DataEntry/Collection/d0ca83f8-bf6d-4c6e-8b62-7fd719961649/ScreenBuilderScreen/84e4ad7b-e428-40e2-9504-b1259f72d210?ActiveLoanId=3000000009&InitialLoad=true)
            * test-mcp
                * [http://localhost:5000/DataEntry/ScreenBuilderScreen/8e0769b4-4760-49a0-83dd-35a12c644e6b?ActiveLoanId=3000000009](http://localhost:5000/DataEntry/ScreenBuilderScreen/8e0769b4-4760-49a0-83dd-35a12c644e6b?ActiveLoanId=3000000009)
            * santis screen 1
                * [http://localhost:5000/DataEntry/ScreenBuilderScreen/aea77510-c204-4c29-b5a2-c9f78e32b7e4?ActiveLoanId=3000000009](http://localhost:5000/DataEntry/ScreenBuilderScreen/aea77510-c204-4c29-b5a2-c9f78e32b7e4?ActiveLoanId=3000000009)
        * show
            * fully responsive indicator: can hover dropbox
            * drag indicators:
                * frozen white screen after select page from megamenu
                * click + type
                * try to blur and scroll
                * try to scroll from the start
            * employment and income
                * load / interact (separarte)
                * explore profiler
                    * spinner
                        * notice that its not a big jump in overall CPU usage in the beginning, but once there's more stuff on the page, all those events start to take up important painting time, especially because CD is more expensive. 
                        * every spinner fires its own intervals, so when you have a bunch, because every grid has its own, you multiply.
                        * the spinner needs the interval to fire in order to update its rotation position, so if other things are taking up CPU time and delaying intervals, it will look frozen.
                    * layout recalc by grids
                    * many requests
                    * show some layout recalcs
                    * notice DX causing some problems
                        * set timeouts
                        * events
                * cant load santis_screen_1
                    * we have about 15 grids or hcms, and 2 panels with about 8 other controls each, this is on the larger end of the expected screens used, but by no mean an outlier, this is a realistic screen according to product management guidelines provided.
        * "we will discuss at the end what strategies we applied here, and the issues that currently remain"
            * dx event listeners, dx control mounting (setTimeout)
    * Case Studies of improvements (dx will be talked about a lot here. mcp examples)
        * foreach case
            * show pr
            * show before/after json
            * 1 slide to explain
        * case studies
            * spinners
                * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11150?_a=files](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11150?_a=files)
            * session timeouts
                * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10898?_a=files](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/10898?_a=files)
            * hostlisteners
                * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11146?_a=files](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11146?_a=files)
            * batched timeouts
                * overall time doenst seem highly affected in recordings, focus on lack of cd runs
                * service:
                    * [https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11663?_a=files](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11663?_a=files)
                * clients:
                    * 
                * [code snippet]
                * [drawing of effect]
            * json lookups / loan data requests
                * these ones are about action fulfillment
                * no recording, only snapshot
                * lookups:[https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11567?_a=files&path=%2FSource%2FELC%2FWeb%2FApp%2FClientApp%2FModules%2FShared%2FComponents%2FBindables%2FPrimitives%2FBindableComboBoxPrimitive%2FBindableComboBoxPrimitive.ts](https://mc-co.visualstudio.com/Cadence/_git/ELCGIT2017/pullrequest/11567?_a=files&path=%2FSource%2FELC%2FWeb%2FApp%2FClientApp%2FModules%2FShared%2FComponents%2FBindables%2FPrimitives%2FBindableComboBoxPrimitive%2FBindableComboBoxPrimitive.ts)
                * loan data is similar
    * grid rewrite overview
        * state manager component, and onpush ui children
            * view model is part of the state of app, but there are parts of the state that are not part of view model.
            * this is because you only want to run CD when something that you care about actually changed. however, it is useful when managing state to not be skipped by CD, in case some outside factor needs to interact with the component state directly, and be able to subscribe to events that might cause change detection. since all of its children are onpush, they will not be rerendered if the part of the state they care about has not been updated.
            * MORE IMPORTANTLY: there are parts of the state of a complex component that we might need to keep but do not require a ui update every time we change it. like, if we say, we want to change the color on the 5th click, we need to keep a counter in the state but we do not need to rerender the ui until the 4th click. 
            * 
        * delay loading of grids until visible
        * use request idle callback to actually mount the rows, because mouning bindable controls is still expensive and we want to prioritize responsiveness and delay mounting if user is scrolling or hovering.
    * overall after
        * no lazy grids
            * employment and income 
            * santis_screen_1
        * lazy grids 
            * santis_screen_1
    * currently remaining issues
        * look at current performance rec
        * DX event listeners (we think this is one of the most important)
            * but we need to remove the entire library for this, which is a heavy task. so it's important to keep CD cycles short, because we have no choice but to run CD like 7 times per click.
        * quill
        * DX does set timeouts
    * [use some demonstrations on a clean angular project using same version of angular. (this is all before case studies)]
        * ngzone
        * on push
            * show how to look for renders (using ngOnChanges and {{render()}} instead of ngAfterViewChecked
        * network, etc
    * so let's look at a pretty bad case of this on mcp and try to deconstruct it.
        * you have probably all experienced some of the performance bottlenecks of MCP. here's what happened when you clicked to load certain screens a few months ago.
    * after the work we've so far, this is what it looks like.
        * it's a lot better, although there are still things we can improve.