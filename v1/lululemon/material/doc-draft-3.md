


* doc #1 questions
    * feature depend on feature?
        * original idea
            * A unit is generic if the functionality it provides is not feature-specific and can be used on its own in the construction of a different feature. A feature may depend on another feature, but that doesn’t make the individual units of the base feature generic.
                * A modal opener that accepts some content to show is generic.
                * A stateful service within the “auth” feature that tells us if the user is logged in is feature functionality, even if the “loyalty” feature uses it in order to adjust its content. This is a case of the “loyalty” feature depending on the “auth” feature
        * is "auth" a feature or a generic?
            * maybe we can solve the auth question by saying: anything that features build on is a "generic"
                * would mean if someone depended on loyalty, now thats a generic. what does generic even mean then? does generic have an ownership implication?
        * a feature is owned by a feature team. like, the repository code-owners are the feature team and they are on call. generic code is maintained more like open source, although at the end of the say its still owned by a specific team. generic i guess is just a "feature", but just at the bottom of the dependency chain, and today we can make this distinction because there are no stacked dependencies. thus, we should call auth a "generic" and we have a clean divide for now.
            * but "auth" has UI, we can still call it generic? we could
            * but "auth" has a dedicated team (login) and perhaps its own repo later, can we still call it generic? i guess notz
    * 
* doc #1: distribution of functional units
    * what is HIP
        * The **Horizontal Implementation Pattern (HIP)** is a set of implementation guidelines for functionality that is not contained within a single MFE, but instead extends across the application horizontally.
        * // these are exposed as libraries that are imported into consumer applications equipped to serve pages via next.js.
        * // we have examples of libraries already like pattern-library and mwa-libraries
        * // we want to develop more features in this way, and have feature teams own their work across multiple mfes. auth and loyalty are two examples of this. 
    * goals: determine where code should live
        * Oftentimes, some of the functionality required for a feature can be better reused and maintained if it is housed in a repository different from the feature itself. For example, a simple button component with some styling should exist within pattern-library. This document describes the logic to determine where each part of our code belongs.
    * define `functional unit`
        * a `functional unit` is a self-contained piece of functionality that we can import/export
            * react components
            * utilities: stateless functionality or immutable values
                * pure functions
                * stateless api wrappers/fetchers
                * navigation functions
            * services: stateful classes, things that we instantiate
                * event emitters
                * redux store
                * singletons
    * descriptive axes & types
        * descriptive axes
            * unique/shared
            * simple/complex
            * independent/dependent 
                * needs services provided at runtime
                    * loyalty benefits modal is dependent on generic modal container, but it doesnt need a service, we can call it independent because it just imports some static behaviour wrapper, it doesnt depend on some stateful outside service (aka side effects). the modal doesnt need to be provided at runtime
            * generic/feature
                * to me this is the only axis that determines whether the code is owned by feature team and lives in feature lib.
                * contrary approach is that some (maybe `simple`, `unique` or `independent` ones) 
            * component/utility/service 
                * should this be an axis? is this a real distinction? i would call everything "sdk"
                * services are instantiated and shared as singletons, utilities are just used
                * this is an axis because it defines which shared repo it should go into (pattern lib / mwa)
        * each `unit` must fall into one camp for each of our `descriptive axes`, giving us our `descriptive factors`, which together make up the `unit`'s `descriptive type`.
        * so, if we have a simple button component, we can say that it's `descriptive type` is "shared simple independent generic component" where our descriptive factors are 'shared', 'simple' etc
    * organizational types
        * `organizational types` apply to one or more `descriptive types`, and tell us how this `unit` should be treated.
            * organizational type
                * generic ui
                    * generic independent components
                    * home: pattern-library
                * generic sdk
                    * generic independent utilities/services
                    * generic dependent components
                    * home: mwa-libraries
                * feature sdk
                    * everything that has `feature` as a descriptive factor
                    * owned by feature team. component-level-ownership.
                        * technical implementation patterns described in doc #2
                    * home: feature-lib
                * feature satellite
                    * unique simple independent feature components
                    * owned by host/consumer/delivery team
                    * this is a piece of functionality that is hard-coded in-place where it is to be used, and not imported from the feature sdk
    * examples
* doc #2: component level ownership techn
    *  \

* random
    * terms:
        * unit: a self contained piece of code (service, utility, or component)
    * case examples
        * auth
            * sdk: 
                * context service
                    * current auth data: logged in user info
            * ui: 
                * auth modal
        * loyalty
            * unique dumb ui components
    * unit categories
        * for each category
            * who owns it
            * where does it live
        * category definition axes
            * unique/shared
            * simple/complex
            * independent/dependent 
                * needs services provided at runtime
                    * loyalty benefits modal is dependent on generic modal container, but it doesnt need a service, we can call it independent because it just imports some static behaviour wrapper, it doesnt depend on some stateful outside service (aka side effects). the modal doesnt need to be provided at runtime
            * generic/feature
                * to me this is the only axis that determines whether the code is owned by feature team and lives in feature lib.
                * contrary approach is that some (maybe `simple`, `unique` or `independent` ones) 
            * component/utility/service 
                * should this be an axis? is this a real distinction? i would call everything "sdk"
                * services are instantiated and shared as singletons, utilities are just used
                * this is an axis because it defines which shared repo it should go into (pattern lib / mwa)
        * metacategories
            * feature unit
                * lives in feature team's own rush repo
                * owned/maintained by feature team
            * generic unit
                * lives in pattern-library or mwa-libraries
                * owned/maintained by dedicated maintainer team for that repo
        * examples
            * loyalty dashboard
                * unique complex dependent feature component
                    * dependent on loyalty backend svc
                * where: loyalty-feature-lib
            * loyalty header banner
                * unique simple independent feature component
                * where: loyalty-feature-lib
            * loyalty benefit info modal
                * shared simple independent feature component
                    * its dependent on generic modal container, but it doesnt need a service, we can call it independent because it just imports some static behaviour wrapper, it doesnt depend on some stateful outside service (aka side effects)
                * where: loyalty-feature-lib
            * generic modal container
                * shared simple independent generic component
                * where: pattern-library 
            * auth sdk (ui like modals and services/data like "who am i" data)
                * shared complex independent generic
                * where: mwa-libraries ("mwa-auth" exists)
    * what does it mean to own?
        * sentry logs to your sentry? should it log to both sentries (also consumer)?
    * implementation patterns
        * services instantiated by consumer (with their dependencies) and provided via context
        * error bounding via react error boundary and function wrappers
            * when u throw error we pass a value (process.env.currenthost) that identifies which team's sentry it should go to
            * "distributed logging" "sentry hub"
                * import sentry registrar: 
                    * doesnt export anything, registers to the global sentry on window, and then we that available
        * e2e testing:
            * lib has thorough e2e to test for regressions. loads components into an isolated environment like storybook (we can also develop them there)
            * consumer has e2e just to test that foreign components load and do what they need
    * questions
        * FM
            * server side rendering
                * currently FM is only fetched on the client, but we would use software streaming at some point to make sure we have it on server
            * * instantiating services: if we're instantiating at consumer root, then publishing an update would not update our service. how to do this?
                * dont poison global scope because server is not gonna clear out global scope, only rerun modules. its not like restarting the process