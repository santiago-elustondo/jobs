

* benefits of using library for all loyalty ui
    * federated during dev
    * its a good pattern to build upon, it helps us be able to not have so many app shells in the future, cause app shells would have no actually feature logic coupled with it
        * u still want a loyalty package within mfe monorepos to do any tie-in logic you need, for example, if you want to use their specific modal thing, or any wrappers or HOCs, then you can provision the library imports there
        * 
![alt_text](images/image1.png "image_tooltip")


------



* ownership: auth owned by accounts, loyalty owned by loyalty
    * auth owned by them but we want to help
        * we dont want to do it in place 
        * also we want to make sure that the security services are not initialized until modal is opened
* contentful might be able to leverage a bunch of this
* landing page: 
    * ecom web app (recommendation)
    * standalone mfe
        * add reasons for not: performance, pip
    * wae-coco

--------



* foundational needs
    * minor contributions/collaboration with ecom-web-client, wae-partials
        * static content
    * major contributions/collaboration with ecom-checkout-client
        * global auth tools
        * rich content
    * library exports
* materials
* [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP) 
* overview
    * loyalty example
        * touches many other teams
        * loyalty accounts / checkout is very coupled with us, and we might encounter other similar situations
    * goals
        * velocity / flexibility 
            * our own release schedule
            * minimize overhead: communication overhead, 
            * bottlenecks: waiting on other teams
            * flexibility important for loyalty a lot of stuff isnt fully ironed out in design, likely changes
        * technical complexity
        * organizational complexity
        * documentation requirement
        * maintainability
            * all loyalty stuff in same place, so stuff doesnt get lost
        * robustness 
            * we want our own test suites that are loyalty specific, within our own repos
        * project scalability
        * organizational scalability: how do we affect the whole organization's scalability
    * problems
        * ownership
        * maintainability
* options
    * 1) expose library (component-level ownership)
        * [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP) 
        * definition:
            * component-level ownership contract: 
                * ex:
                    * components are self-contained and will not cause side effects unless a well-defined service prop is passed in
                    * tight error boundary and error-handling within component
            * intake for other teams to just put in a component from library
            * will require working with other team to figure out what the component should do in this case (like ui structure)
            * delivery via: module federated / npm install
                * module federated more flexibility
                * npm install if client team doesnt support MF, or are uncomfortable with dependency code update without their deploy process
        * need:
            * we would need to define a component-level ownership contract and officially promote this method (checkout/accounts was nervous to start just putting stuff in)
        * general pro: 
            * does not require hybrid approach
            * deploy is independent
            * everything is maintained together (testing, etc)
            * less inter-team complexity/overhead
            * less documentation needed (in terms of record keeping, we only need to keep track of where our components are being consumed, but you dont need too much context)
        * general cons:
            * in some cases, it is added overhead in the short term
                * collaborating with close-knit teams, like contributing via PRs, is relatively painless, so it could arguably be
            * more technical complexity for us
                * isolation: cant consume frontend services and patterns existing another teams' applications. also cant leverage other resources like their qa automation, etc
                * encapsulation: would need to bundle the services (apis/streams/etc) that we need, and make them available to our components in an encapsulated way
            * $ robustness: Depends a bit on FM vs npm. If FM, a release could pass QA, but later our FM changes, in which case it doesnt. however, the test suites would be maintained by our team, and the isolated nature of the approach makes it so that the other teams' changes should never impact us (as opposed to writing our code and tests in their repo using their pattens and services)
            * $ maintainability: good because. having tests in different projects means you could have duplications or lack of clarity about whether something is already tested somewhere else
    * 2) contributing loyalty code to teams' repos
        * requires hybrid approach
        * general con: release pipeline is distributed and dependent on other teams. we have to wait / request different types of deploys / work with diff QA teams and systems
        * GC: more documentation required to explain where all the pieces of the project are, how to maintain, etc. hard to keep documentation updated
        * GC: although lower technical complexity because we can use stuff from environment and we dont need to encapsulate our own data and state services, velocity arguably is still not better because we still have to figure out how stuff works in depth and design solutions taking into account existing patterns and their limitations. design decisions, especially if something needs to change, would need to be approved by team, which adds organizational complexity overhead
        * GC: ownership. 
            * other team's tech manager problem: about what is being done in their repo by a project they are not very involved in. if we need to change something that touches the code that the visitor put in?
            * our problem: who will maintain this? what if changes are made 
        * GP: if this other team should be logically integrated, they can share context tools. these front-end services usually are only set up to serve the specific code where they are written. there would be duplication if we dont share it.
            * like if loyalty and accounts should be, kind of like merging teams
                * can use accounts' patterns for communicating with GIH, even their setup for QA, etc.
        * GC: merging teams not a very scalable general strategy since we would rather have smaller repos
        * LC: already a lot of teams working on this repo
        * LC: different tech managers all the way up, its easier to collaborate with teams that you are more connected with, like PEPS
        * LP: happens to be the case that accounts and loyalty are very logically related
    * 3) requesting loyalty code from other teams
        * many teams..
* notes: 
    * deploying our own nextjs application (MFE)
        * doesnt qualify as an option because it cannot be our only solution. we need to integrate into other teams components/pages for certain requirements
        * page reloads
        * puts arbitrary limitations on UX based on organization structure: if we have our own page in accounts, we cant put any loyalty info in profile page, it must all be in loyalty page
    * hybrid approaches
        * require more documentation and more technical effort enablement/maintenance/docs
* table
    * columns
        * 
* todo
    * look at options in 2 ways: general pros/cons, loyalty specific (accounts partnership is useful for us)
* doc
    * crossing teams has overhead
        * adding work to their plate, and can get blocked or bottlenecked depending how busy bumping library versions takes a while
        * need to be aware of process patterns and guidelines unique to each team
        * code that is left in other teams can be changed by them in the future for something they're trying to accomplish, which leads to coupling.
        * documentation of where everything is, KT
    * collaboration with accounts
        * our collaboration strategy with accounts requires special attention, since is this the project that we have the most overlap with.
        * what we need
            * global auth library
                * export as lib
                * refactor auth, possible keep both until ready
            * add rich data-driven UI elements (page, widgets)
        * options 
            * auth lib
                * do it in place or external
                    * need to outfit repo for library export
                    * we would be further entrenching ourselves in a repo accounts wants to split from. if we do temporary duplicate, then there will be substantial duplication left in place, which if we dont end up taking, then it would be more difficult to remove once its there and part of the test suite.
                    * external would let us soak it for a while, using only for loyalty until mature.
                    * we make progress toward split.
            * loyalty becomes accounts 2.0 (1 repo instead of 2 in the case of auth lib in new repo)
                * considering the possibility that we decide to separate in the future: we can keep a clean separation at the package level
                * profile and loyalty share many use cases and services, will always be collaborating teams.
                * we want to make the lll whole experience more personal, and bring profile and loyalty to everywhere. we will usually want both.
* opts
    * pure lib
        * define:
            * `me` service in lib (cant avoid signup modal)
        * options: 
            * repo can build part as FM and part as npm module, if we dont want anything complicated in FM. we do as module what we would have done in-place.
            * preferably we are using new `me` service in checkout/accounts and also same auth components, since `me` is the new accounts. but we dont necessarily have to, it can be a stretch goal.
        * pros:
            * everything together
            * clean monitoring, clean feature flagging, etc
            * down the line when we need to do more backend stuff, we'll have more malleability
        * questions:
            * can we do fully our own test suites (including e2e). would we have to also test on the consumer? we could do just a smoke test there, with the thorough one being ours
        * notes:
            * we're not any more or less independent we still have to work in accounts a lot, and we have to put in the components into places. we were already pretty flexible before.
    * hybrid no `me`
        * define:
            * everything in-place EXCEPT:
                * shared stuff like our own services or config or modals
                * pure component internals (logic/render) for quick iterating
                * 
* doc
    * todo
        * structure
        * write
        * draw diagrams
        * format
    * misc
        * the abdalla problem we fix with an event emitter its not a big deal
        * if we do the global auth stuff (signup modals), then that could be the beginning of splitting out accounts
        * (we shouldnt forget that future growth or design revision might bring rich UI components to other mfes)
        * dont be that definitive with the 2 patterns, we can mention that there are other deprecated patterns like wae-partials injection.
        * dont be all that definitive regarding mfe features being vertical and self-contained, or provide a caveat disclaimer. for example: auth/account stuff is supposedly all in ecom-checkout-client, but theres some stuff in the header.
        * issue with create account: doenst ask for name?
            * 
![alt_text](images/image2.png "image_tooltip")

    * ideas
        * maybe we dont need the global auth. maybe redirect is fine?
            * they show the header signup prompt and your name on the navbar profile icon, so clearly we can query auth/account info.
            * we might have some limitations outside of checkout/accounts without some new services, but thats fine for now.
        * however we end up making signup modal present everywhere (current idea is to piggyback on MegaNav), we can inject, as part of this, a global service to get account/loyalty data. this will feed our widgets
            * this is going to house all our main service functionality, makes sense to put there since they are closely related to signup
            * thus, we are only then putting all our interactive IO code on checkout/accounts because all the interactive stuff happen to be there. if we need to add a widget like that on another repo, no problem.
        * modal opening callback is an example of something simple enough that we can take as prop for a remote component. no dangerous side effects
        * so, how its done
            * global auth/account service (including signin component)
            * loyalty features
                * simple unique widgets are hardcoded
                * simple repeated widget stuff (modals) is remote component
                * simple pages are hardcoded (probably in different repo to get desired url)
                * interactive IO stuff (pages/widgets)
                    * UI logic and view are remote components
                    * contextual services (not auth/account) are interacted with in hardcoded manner, only providing the simplest props/callbacks to components
                    * auth/account IO comes from global auth/account service. or, if there are impediments, then for now hardcode in checkout/accounts like contextual services. we can do this for now because all interactive stuff happens in checkout/accounts. later we would have to figure out how to make a global service if we want interactive elsewhere
    * categories of deliverables
        * global authentication
        * static widgets on existing pages [pdp, signup, banners]
            * they do: 
                * open auth modal
                * open other modals
                * links
                * basic data (auth/account/loyalty) (isAuth, name)
            * 
![alt_text](images/image3.png "image_tooltip")

![alt_text](images/image4.png "image_tooltip")

![alt_text](images/image5.png "image_tooltip")

![alt_text](images/image6.png "image_tooltip")

        * static pages (ui, links, signup prompt) ["story"]
            * 
![alt_text](images/image7.png "image_tooltip")

        * interactive widgets on existing pages (more data / logic) [account dashboard]
            * 
![alt_text](images/image8.png "image_tooltip")

        * interactive pages ["loyalty-hub"]
            * 
![alt_text](images/image9.png "image_tooltip")

    * approaches
        * component-level ownership (our repo)
            * interesting con: the organizational direction is not settled regarding remote components. (we could unify the app) trailblazing might be premature.
            * con: if we are not contributing to host, we would have to define a component-level ownership contract
            * pro: well-organized and maintainable test suites. BUT we actually cant take full advantage of this because e2e tests must be done on the host..
            * pro: independent releases
            * pro: centralized vertical slice (maintainable). but this is arguably not the right vertical slice to cut. accounts and loyalty should be the same slice. if everything were in a central repo and exposed as a library, we would need less documentation since everything is together (self documenting)
            * con: if we are not contributing to the host and we use any host services (through props) it will be hard/impossible to achieve strict-defined component-level ownership contract guarantees (ownership model / error and side-effect containment)
            * con: if we are not contributing to the host complexity affects us more due to component-level ownership contract requirements (defensive programming, have to take in well-defined stuff through props and prevent side effects)
            * con: if we are not contributing to the host communication would be necessary to negotiate what services we are using and how
            * con: if we are not contributing to the host, we also have the option of encapsulation as opposed to taking in services. would mean that we can define a better component-level ownership contract guarantee, and also achieve tighter centralization. means we cant take advantage of existing solutions, possibly duplication or challenging/unfeasible refactor. also we would have to deal with complexities like sharing services across components to avoid doing stuff like requests multiple times, and also it will be difficult to not add extra requests overall beyond what we have today (if we contribute, we can use the same request to get more data)
            * con: having our own data services makes no sense since we are the same thing as accounts, and we should be unified. the same could be said about components to some degree, best example being the accounts dashboard, where we are adding interactive loyalty behaviour to profile page. its all the same (part of accounts)
            * con: if our component is hosted by a repo that we are not contributing to, we will have to use intakes to put it in, and then every time we need to change the api 
            * con: hard technical limitations (no websocket stream)
            * con: technology adoption is immature and has technical debt
                * tried and tested for simple and independent components (PEPS)
                * run-time based is a problem because no guarantee, liability
                * (withApp)
                * its a fickle mess, nobody wants to touch it, impossible to KT
                * so fucking many nested providers and stuff
            * if we're contributing to checkout/accounts (which is pretty much a must: technical limitations with federated modules, global signup), then in order to publish remote components we will have to also have a separate repo for them, because we would need to make significant changes to accounts to export modules from there. reasons: 1) building fed modules from checkout/accounts would be an invasive change to the plumbing of a production repo, would take a long time to discuss and review, it would also just add complexity (does more things) to an already complex repository that is due for a split (acounts split from checkout) 2) federated modules are, again, a complex and not mature feature of our system, and so we would want to build and publish simple modules, which are most easily served from a dedicated repo for this purpose. 3) we would be adding components to checkout/accounts that have nothing to do with checkout/accounts, stuff for other pages like PDP
        * intake requests (others repos)
            * if we can contribute, we can collaborate. makes sense for global signup since we might need it to expose loyalty data as well.
            * pro: other teams have the context needed to design and implement faster than us. the higher the complexity and the contextual challenges, the more true this is (signup is perfect example, this isnt even a new ask to them, they've already considered it)
            * con: more docs to describe the inter-team layout
            * con: communication overhead
            * con: blocked on other teams, especially if we cant collaborate
            * con: not independent at all, even if collaborating, we rely on their team from story acceptance to design to implementation to review to qa
        * contributions (others repos)
            * accounts and loyalty both have account signups as KPI