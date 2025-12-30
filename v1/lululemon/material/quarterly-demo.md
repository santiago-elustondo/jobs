

* missing
    * lenny part
    * too long
* todo in order
    * put in all current content
    * cleanup and speed 
    * record new content
        * mention component demos in intro (right now only mentioning technical runway
        * outro shouldnt show technical runway
    * add subtitles
    * put in lenny
* script
* intro
    * Hello everyone, my name is Santiago and I'm an engineer on the Loyalty team. In this video we'll be talking about the work we did during our first quarter as a team, Q1 2022.
    * Our technical runway consists of two main parts
        * an MFE to host Loyalty-owned pages, 
        * and a component library to bring Loyalty functionality to pages owned by other teams.
    * I'll talk a little bit about the latter, and then Lenny will talk about our MFE
* arch
    * The loyalty feature is present in some way on a lot of pages owned by a number of different teams. The functionality that we're bringing to these different repositories, however, is closely related and reusable.
        * Also importantly, we don't want to not make our problems the problems of the host app teams.



            * 
by guaranteeing our components wont bring regressions to the host application


            * 
by minimizing the complexity we bring to other teams repositories


            * 
by supporting our own work via centralized monitoring


    * To achieve this, our library implements a component-level-ownership pattern to provide self-contained components that share virtually nothing with the host application (state, utilities, etc).
        * Our simple framework provides our components with the services they need as dedicated loyalty instances, avoiding any side-effects, and error-bounds all of our components to prevent any errors from spilling out and causing problems for the host app
        * Errors or events needing attention are logged to the Loyalty sentry account, no matter what MFE they originate from, and are tagged with info telling us where they came from (which MFE and which component)
* comps
    * allow me to demonstrate
        * here we have the dashboard benefits component it uses ecom pattern library under the hood wherever possible.



            * 
[show functionality and responsive]


        * framework outfits every component we create with feature flag and ab-test toggles, without dev effort. we can toggle our feature flags for QA



            * 
[show feature flag]


        * in sentry, we can see a number of errors we produced during development, and you can see that we are easily able to determine exactly where that error came from. This is achieved by the framework for every component we create without dev effort.



            * 
[show sentry]


        * all our components load their content from contentful, which is handled by the framework as well with no dev effort
        * we can run our components in storybook, complete with all loyalty services including contentful, for a streamlined development and automation flow. 



            * 
[show storybook]


        * importing and using the library components is as easy as dropping them where we want to see them, they do the rest



            * 
[show import code]


* PR
    * some of our requirements we encountered were not able to be feasibly implemented as a library export.
        * in the case of the Loyalty Hub page of the user account area, adding a navbar tab and corresponding page route required code changes in-place on the ecom-checkout-client repo.
        * the new navbar item must be invisible until the feature flags are enabled. we import library functionality to achieve this, so we can ensure our feature flagging and ab-testing behaviour is consistent across the board.
* i hope this gave you some insight into the type of challenges we've worked through in Q1. Now Lenny will talk about some of the work we've done for our own Loyalty-owned pages, hosted on our own, brand-new Loyalty MFE.