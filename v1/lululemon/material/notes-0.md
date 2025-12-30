

* lll
    * cdp 266 [https://lululemon.atlassian.net/jira/software/c/projects/LOYALTY/boards/1934?modal=detail&selectedIssue=LOYALTY-266&assignee=61b78e12f19b53006a7b9b93](https://lululemon.atlassian.net/jira/software/c/projects/LOYALTY/boards/1934?modal=detail&selectedIssue=LOYALTY-266&assignee=61b78e12f19b53006a7b9b93)
        * before monday



            * 
incognito bug? update rituraj/monirul


                * when you add in a query param (which you sometimes do to view a pr env link), you lose promo tiles.. theres some bug there but its present in prod.
                    * this occurs even if u add a slash at the end like 
                        * slash, no tiles
                            * [https://shop.lululemon.com/c/men-joggers/_/N-8rt/](https://shop.lululemon.com/c/men-joggers/_/N-8rt/)
                        * no slash, tiles 
                            * [https://shop.lululemon.com/c/men-joggers/_/N-8rt](https://shop.lululemon.com/c/men-joggers/_/N-8rt)
                        * 



            * 
clean up PR


            * 
RFC contenful


            * 
apply the correct links (in contentful data)


            * 
update jira story


                * how to test / update contentful data
        * monday morning



            * 
PR approves


            * 
move ticket to qa ready


            * 
get people to look at RFC


* lll_think
    * **next week (lenny away) is a great chance to do a good job, ranjit is watching and we can go for a team drink after we finish the quarter successfully**
    * **i dont have a big story in my name, so i can focus on being present online and writing a lot**
* lll_today/tmrw
    * [100] early morning post on core tech team regarding stories 
        * CC ranjit, atal, lenny
    * [80] update stories on jira
    * [20] tmrw talk to ranjit, tell him what u did tonight (it was a lot of work, and worked with lenny to figure out what we should do)
        * there were a lot of problems with story



            * 
isLoggedIn


            * 
CI


    * [80] update original branch to use latest lib	
        * [https://github.com/Lululemon/ecom-web-app/pull/5848](https://github.com/Lululemon/ecom-web-app/pull/5848)
        * we need to import the "Wrapped" version
    * [90] fix issues in branches 
    * meet with devs about what we ended up doing.
        * had to write a lot of stuff again, that i think should be in lib



            * 
we now have 2 solutions to the same story


            * 
ended up in a situation where there is no logical division of code between what's on ecom-web-app and whats on lib


            * 
there is duplication


            * 
multiple sources of truth (example: config, flag behaviour)


                * flag behaviour is actually different, in lib we only use LD



            * 
there are context requirements to some hooks, etc that would be much nicer to have in our lib


        * we can always go back to the other pr (thinner, using lib) if we fix that bug
        * we're going to need to add a story to figure out if we refactor lib/fix issue, or do it like we did in ecom-web-app and lib is just a ui lib, or what
        * contentful / sentry / launchdarkly & ab testing, etc
        * we can refactor the lib to have the feature injection up top still, in order to allow host to give config, but have it be just that, config. every functional/stateful thing in the service should be in hooks or internal contexts
        * FYI, there's a particular test (in PDP, but unrelated to our code) that currently gives me a fail locally under specific conditions, but it seems to always pass in CI. Please connect with us if you want to discuss it.
* lll_routine
    * post on core tech team everyday
    * updates in jira everyday
    * chat
* lll
    * web-app
        * smoke test (make sure the imports are ok)
        * clean up 
        * tests
    * mwa

------------------



* lll
    * imports thing in mwa lib
    * isloggedin mismatch between partials and webapp
    * pipeline not passing for ecom-web-app (sentry?)
        * "build pr env" job
    * ask new manager for help (i'm sick)
        * ask dave for help
        * anyone else?
        * what fails



            * 
QA fails


    * currently showing returns on "finalSale" items in shipping section
        * 
![alt_text](images/image1.png "image_tooltip")

    * 
* lll_story_STANDUP
    * member vs not member, what's the difference (banner vs message)?
    * does text need to be contentful? we could hardcode it
    * we have to bring it library anyway, for modal, so might as well use flag from lib
    * abdalla: contentful selector for returns on markdowns specific card
    * abdalla: dynamic import problem on ecom-web-app?
    * abdalla: loyalty modal not showing up properly on storybook

----------



* 
![alt_text](images/image2.png "image_tooltip")

* todo: paras interviews
    * santi
        * create linkedin page for fliporders
    * paras
        * update linkedin
        * write draft of interview materials doc



            * 
tech stories


            * 
tools/terminology


                * testing
                    * jest
                    * enablement: babel, jsdom
                    * E2E: selenium, cypress 
                * building
                    * webpack (maybe gulp)
                * frameworks
                    * nextjs
                    * redux
                * devops
                    * github actions / circle ci / jenkins
                    * deployment (a little bit, surface level)
                        * s3 buckets
                        * CDNs, akamai 
* lll_backlog
    * 10 refactor: modals
    * **80 refactor: router & frame**
    * 20 refactor: old components
    * 60 refactor: review menu editor
    * 50 refactor: server
    * 100 deployments
    * lll
        * prs



            * 
ecom-checkout


                * linting



            * 
mwa


                * cursor: pointer on View member hub
                * mike's comment about css
    * lll_standup_notes
        * the redirect thing was a 5 pointer
        * 
    * lll (in order)
        * **meeting with cosy**



            * 
we want a model for benefit


                * 2 descriptions
                * contentful model (should be shared with the benefits cards component and possibly the modals, since they look like they use the same data)



            * 
use this model within abdalla's page


            * 
prep: 


                * abdalla's page model (has some benefits stuff)
        * **governance doc**
        * **dashboard benefits**



            * 
modal stuff


            * 
models?


        * check in on International



            * 
ask Andrew f he actually needs me


        * library update



            * 
second error bound before service


            * 
configure sentry (we dont want errors from dev mode)


            * 
IfFeatureEnabled has no error bound!


            * 
assuming that feature flag name is same as feature name


* script
    * intro
        * Hello everyone, my name is Santiago and I'm an engineer on the Loyalty team. In this video we'll be talking about the work we did during our first quarter as a team, Q1 2022.
        * Our technical runway consists of two main parts



            * 
an MFE to host Loyalty-owned pages, 


            * 
and a component library to bring Loyalty functionality to pages owned by other teams.


        * I'll talk a little bit about the latter, and then Lenny will talk about our MFE
    * arch
        * The loyalty feature is present in some way on a lot of pages owned by a number of different teams. The functionality that we're bringing to these different repositories, however, is closely related and reusable.



            * 
Also importantly, we don't want to not make our problems the problems of the host app teams.


                * by guaranteeing our components wont bring regressions to the host application
                * by minimizing the complexity we bring to other teams repositories
                * by supporting our own work via centralized monitoring
        * To achieve this, our library implements a component-level-ownership pattern to provide self-contained components that share virtually nothing with the host application (state, utilities, etc).



            * 
Our simple framework provides our components with the services they need as dedicated loyalty instances, avoiding any side-effects, and error-bounds all of our components to prevent any errors from spilling out and causing problems for the host app


            * 
Errors or events needing attention are logged to the Loyalty sentry account, no matter what MFE they originate from, and are tagged with info telling us where they came from (which MFE and which component)


    * comps
        * allow me to demonstrate



            * 
here we have the dashboard benefits component it uses ecom pattern library under the hood wherever possible.


                * [show functionality and responsive]



            * 
framework outfits every component we create with feature flag and ab-test toggles, without dev effort. we can toggle our feature flags for QA


                * [show feature flag]



            * 
in sentry, we can see a number of errors we produced during development, and you can see that we are easily able to determine exactly where that error came from. This is achieved by the framework for every component we create without dev effort.


                * [show sentry]



            * 
all our components load their content from contentful, which is handled by the framework as well with no dev effort


            * 
we can run our components in storybook, complete with all loyalty services including contentful, for a streamlined development and automation flow. 


                * [show storybook]



            * 
importing and using the library components is as easy as dropping them where we want to see them, they do the rest


                * [show import code]
    * PR
        * lastly, we should cover what it looks like when we encouter a requirement that cannot be feasibly implemented as a library export.



            * 
in the case of the Loyalty Hub page of the user account area, adding a navbar tab and corresponding page route required code changes in-place on the ecom-checkout-client repo.


            * 
the new navbar item must be invisible until the feature flags are enabled. we import library functionality to achieve this, so we can ensure our feature flagging and ab-testing behaviour is consistent across the board.


    * i hope this gave you some insight into the type of challenges we've worked through in Q1. Now Lenny will talk about some of the work we've done for our own Loyalty-owned pages, hosted on our own, brand-new Loyalty MFE.
* script
    * intro
        * Hello everyone, my name is Santiago and I'm an engineer on the Loyalty team. In this video we'll be talking about the work we did during our first quarter as a team, Q1 2022.
        * <span style="text-decoration:underline;">After gathering the requirements and guidelines for our team, and discussing strategies for engineering architecture and cross-team collaborations with our many stakeholders, we settled on a technical runway consisting of </span>



            * 
an MFE to host Loyalty-owned pages, 


            * 
and a component library to bring Loyalty functionality to pages owned by other teams.


        * I'll talk a little bit about the latter, and then Lenny will talk about our MFE
    * arch
        * Our library implements a component-level-ownership pattern. 



            * 
The loyalty feature is present in some way on a lot of pages owned by a number of different teams. The functionality that we're bringing to these different repositories, however, is closely related.


            * 
We need to


                * not make our problems their problems 
                    * not introducing possible bugs to their apps
                    * account for and support the functionality we bring to other teams's repos by monitoring our own errors
                    * have centralized control over the visibility of our feature and feature increments including ab-tests
                * minimize the complexity and coupling we bring to other apps
                    * we dont want to have the other teams have to now consider the loyalty functionality when making changes.
                    * code reuse
                * minimize our own complexity
                    * code reuse
                * maximize developer productivity and code quality in a distributed feature by minimizing the work we do on different repositories
                    * having our own patterns within the lib 
                        * better architecture and code reuse
                        * we dont have to consider what their patterns are
                    * having all our code in one repository using the save development and testing tools 
        * To achieve this, our library exposes self-contained components that share virtually nothing with the host application (state, utilities, etc).



            * 
Our simple framework provides our components with the services they need as dedicated loyalty instances, avoiding any side-effects, and we error bound all of our components prevent any issues from spilling out and causing problems for the host app


            * 
Any errors are logged to the Loyalty sentry account, no matter what MFE they come from, and are tagged with info telling us where exactly they came from (which MFE and which component)


        * Our library lives within mwa-libraries and is distributed as an npm package. We use storybook for isolated development and end-to-end testing of our components, since that are self-contained and standalone.
    * comps
        * allow me to demonstrate



            * 
here we have the dashboard benefits component it uses ecom pattern library under the hood wherever possible.


                * [show functionality and responsive]



            * 
framework outfits every component we create with feature flag and ab-test toggles, without dev effort. we can toggle our feature flags for QA


                * [show feature flag]



            * 
in sentry, we can see a number of errors we produced during development, and you can see that we are easily able to determine exactly where that error came from. This is achieved by the framework for every component we create without dev effort.


                * [show sentry]



            * 
all our components load their content from contentful, which is handled by the framework as well with no dev effort


            * 
we can run our components in storybook, complete with all loyalty services including contentful, for a streamlined development and automation flow. 


                * [show storybook]



            * 
importing and using the library components is as easy as dropping them where we want to see them, they do the rest


                * [show import code]
    * PR
        * lastly, we should cover what it looks like when we encouter a requirement that cannot be feasibly implemented as a library export.



            * 
in the case of the Loyalty Hub page of the accounts section, we were to define components implementing all the behaviour of the page itself, but adding a navbar tab and corresponding page route required code changes in-place on the ecom-checkout-client repo.


            * 
this navbar item must be invisible until the feature flags are enabled. we import library functionality to achieve this, so we can ensure our feature flagging and ab-testing behaviour is consistent across the board.


    * i hope this gave you some insight into the type of challenges we've faced in Q1, implementing a feature spanning numerous repositories. Now Lenny will talk about some of the work we've done for our own Loyalty-owned pages, hosted on our own, brand-new Loyalty MFE.
* tn
    * lll
        * video



            * 
100 - watch lennys


            * 
50 - record my videos


                * architecture & example components 
                    * arch: lib package, framework, importing and using, sentry, contentful, services in future, etc
                    * comps: dashboard benefits, homepage hero banner
                        * contentful content models hooked up
                * accounts contribution



            * 
40 - edit full video


        * PR change



            * 
100 read thread


            * 
80 make PR with changes


* lll-lib
* bottom error boundary that doesnt require service
    * then another error boundary after service
* turn off sentry for testing (right now mocking)
* lll
    * build spike prep 
        * make quick cra for testing
        * make empty project for building



            * 
imports ecom-pattern-library


            * 
has src with components with scss modules


            * 
imports ecom-pattern-library component


            * 
imports ecom-pattern-library scss vars


        * link into quick CRA
    * build goals
        * use and import scss modules
        * single output bundle 
        * styles are baked into the bundle
        * contains all dependencies except those flagged as "external"
    * arch goals
        * misc



            * 
ensure that we get our contexts from useContext(), otherwise wait


        * debug



            * 
config value passed to service init to put stuff in global scope


        * error bounding + sentry



            * 
turn sentry logging on/off on service init config


            * 
sentry service context: server or browser


            * 
service init config tells us what the host app is called -> tag


            * 
service provides captureError() function and derivative errorBoundedSyncFn and errorBoundedAsyncFn


                * these accept a parameter on construction with tags for sentry



            * 
error boundary HOC 


                * accepts tags for sentry



            * 
error data


                * breadcrumbs: user events
                * tags:
                    * set during init
                        * host-app: application host name 
                            * from service init config args
                            * set during init
                    * set right before captureError and then unset
                        * source: last second
                        * widget: widget name
                            * hardcoded as argument to widget boundary HOC
                            * exists when error caught in code or at error boundary, not when it is a service error
        * feature flagging



            * 
exported wrapper comp that renders children if loyalty flag is on


                * will use for feature satellites



            * 
AB test + launch darkly


        * contentful
    * problems
        * loyalty-lib



            * 
why does yarn hang when i try to yarn add local loyalty-lib


                * at least i can do yarn link



            * 
how do i compile the css in my ecom-pattern-library dependency? i still have `require("./grid-container.css");`


    * reasons to maybe split out now
        * cypress tests
        * put it in same mono as our next.js
        * dependency conflicts/pollution?
    * lib outfit
        * scss (like pattern-library?)



            * 
we want to import from pattern lib


        * storybook
        * jest
        * cypress
    * sentry
        * [https://docs.sentry.io/platforms/javascript/troubleshooting/#using-a-client-directly](https://docs.sentry.io/platforms/javascript/troubleshooting/#using-a-client-directly)
        * we use the sentry client instance approach because



            * 
some mfes dont use the mwa-logger thing


    * questions
        * dependency conflicts in mwa-libs
        * we actually dont bundle dependencies in mwa-libs?



            * 
what versions do i pick for my dependencies?


            * 
should we be bundling?


                * how should we bring the scss files in and other assets?
                    * right now just copying them in with babel --copy-files
                        * nvm....  cant do that
                            * error - ../../../mwa-libraries/packages/mwa-loyalty/dist/components/LoyaltyBanner.module.scss
                            * [1] CSS Modules **cannot** be imported from within **node_modules**.
                            * [1] Read more: https://nextjs.org/docs/messages/css-modules-npm
                * what if some consumer cant compile our files
        * we only seem to be using sentry in browser context in ecom-web-app
        * unit testing / storybook / cypress
* lll_zack
    * how do we deal with our library bundles having duplicated dependencies?
    * sentry: using client instances instead of distributed tracing. distributed tracing isnt what we want, we want it to go to a different sentry account.
* lll
    * arch meet
        * [https://lululemon.atlassian.net/wiki/spaces/MWAP/pages/2739078210/How+to+Package+and+Distribute+JS+Modules+in+the+MWA+Ecosystem+-+Decision+Summary](https://lululemon.atlassian.net/wiki/spaces/MWAP/pages/2739078210/How+to+Package+and+Distribute+JS+Modules+in+the+MWA+Ecosystem+-+Decision+Summary) 
        * learn rush
        * make options document with representative concrete examples
    * study
        * sentry (light)
        * rush (light)
        * contentful (light)
    * HIP (horizontal implementation pattern)
        * service provisioning
        * error bounding
        * sentry
        * cypress	



            * 
how are testing meganav


        * other possible questions



            * 
prerender + SEO


*  today
    * lenny:
        * ecom checkout client
        * sentry?
        * contentful?
        * mfe status
    * FM for SEO ?
* lll
    * ecom-web-app
        * services through react context
        * sentry setup
        * contentful setup
        * error bounding
        * exporting multiple outputs like a proper library (slash paths)
        * shouldnt be called "mwa-loyalty", should be "loyalty"
* today
    * meet with checkout/login/accounts devs to onboard a bit: 
        * learn how to run backend stuff locally, currently fails all requests
        * also pages show error page, although it doesnt seem to actually hit "componentDidCatch()"? where is it failing, whats going on?
        * why are my breakpoints not working? (in error boundary)
        * people



            * 
stephan redfield


            * 
Jeffery Shivers (checkout tech lead)


            * 
@Shane Henning  (login tech lead)


    * morning sync w lenny
        * [https://github.com/Lululemon/loyalty-mfe](https://github.com/Lululemon/loyalty-mfe)
        * [https://gitlab.com/lululemon/global-digital-tech/loyalty/loyalty-mfe](https://gitlab.com/lululemon/global-digital-tech/loyalty/loyalty-mfe)
    * auth-sdk
        * make work whats there: 



            * 
[https://github.com/Lululemon/ecom-checkout-client/pull/2376/files#diff-9f377d1f3bfe8a59d2266cacb90ab5d2d3cd4d00e64a94fbc69ad222619563f9L8](https://github.com/Lululemon/ecom-checkout-client/pull/2376/files#diff-9f377d1f3bfe8a59d2266cacb90ab5d2d3cd4d00e64a94fbc69ad222619563f9L8) 


            * 
[https://github.com/Lululemon/mwa-libraries/blob/master/packages/mwa-auth](https://github.com/Lululemon/mwa-libraries/blob/master/packages/mwa-auth) 


        * figure out shape thing



            * 
ecom-checkout-client/packages/ecom-core/src/components/shape-security.js 


    * ecom-checkout-client adblock bug
* lll
    * accounts/checkout pages are down?!
    * plan: MF next checkpoint
        * talk to zack once we have



            * 
FM locally working for ecom-web-app and refactored mwa-loyalty header banner stuff (ecom-web-app)


                * we can show him our approach to services
                    * approach options
                        * library entry file initializes them and shares them for all components of lib
                        * you have to import the module initializer and call it in consumer entry (allows opportunity to pass configuration or share services)



            * 
attempt to set up for ecom-checkout-client


                * we can ask him about ecom-checkout-client if we have trouble with it



            * 
run a few of the FM examples 


                * attempt some experiments to ask about?



            * 
questions for zack: 


                * best way of linking an FM lib within a monorepo to a consumer app within another monorepo
                    * currently just linking that package to the monorepo root (ecom-web-app)
                * how do you feel about TS?
                    * does mwa-libraries support TS? any idea what would have to change or how difficult it might be to bring it in?
    * ecom-web-app + mwa-loyalty
        * how do we publish our library / bump version? (i guess we just have to merge a PR into mwa-libraries)
        * this error? 



            * 
[1] ESLint couldn't determine the plugin "react" uniquely.


            * 
happens every time in postinstall


            * 
its loading .eslintrc files from inside node-modules


            * 
seems like it doesnt cause problems, just ignore


        * setup FM locally eventually

--------------------------



* lll_active
    * mfe
    * intl
    * mwa lib
        * build/deploy as either npm package or FM
        * build/deploy as bridge package (3rd option) so we can switch npm or FM from our end? maybe we dont even need this, better to have teams be aware of and agree to consume FM anyway
    * accounts dashboard
        * how do we get to the accounts page? need to be logged in somehow
    * ecom banner
        * questions



            * 
(lenny) how did building/deploying mwa-libraries work again? 


            * 
why does it create a bunch of files in ecom-pdp when i run yarn dev? transforms assets to js files? git status shows bunch of files


        * todo



            * 
(lenny) introduce sentry


            * 
(lenny) introduce contentful


            * 
make proper error boundary (fn, afn wrappers ?)


                * tests for error boundary?



            * 
lib


                * (1) import locally as npm package
                * (2) import locally as FM
* lll_notes
    * node versions
        * ecom-checkout-client: 14
        * ecom-web-app: 14
        * mwa-libraries: 14
* mod_fed
    * page by page
        * p14
            * "No framework - As long as both applications are using the same view framework, then they can both use the same code."
                * why is same "view framework" (aka renderer) a condition?
                    * the imported module could expose a mount function that takes a DOM element, for example, and mount a very different application
                    * the module could not have any rendering requirements at all (a utility/service)
                * what is meant by "they can both use the same code"?
                    * i think it means that you can write a react component and use it by either consumer
        * p12
            * "The second drawback is that when the Product Carousel is updated there is no guarantee that both the Home and Search pages will show the same versions of the carousel, because either or both, could have deployed with older versions of the library."
                * more problematic still is: say app A imports libs L1 and L2, and also L2 imports L1. L1 deploys new version. multiple ways where, with naive project config, we could end up with both versions in A's bundle. 
                    * A updates L1 dependency before L2. 
                    * more contrived, similar result: L2 updates it's L1 dependency and then bumps itself it order to redeploy, after deploy they request that A update its L1 dependency. A's team, unaware of L1's new version, and unaware of what the L2 update is, fulfills request by only bumping L2
        * p11
            * "fixing issues in the Product Carousel becomes laborious. They need to change projects, make the changes, fix the tests, bump the version and deploy the library. Then they need to bump the version of the library in both Home and Search and get those applications deployed."
                * lenny's problem
    * general 
        * notes
        * questions
            * are all front-end modules mfes? what if they dont have any UI components (only utility services or whatever)? maybe its just a terminology problem and we shouldnt call it an "mfe" (in my head it implies that it can run on its own (mounts and starts AKA application shell)
                * facts as i understand
                    * mfes dont need to be federated, as an mfe could be npm-imported AKA `build time deployment` (p8)
                    * you can mf on the backend too
                * what about backend/iso modules?
        * questions
            * `application shell`
                * definition:
                    * a front end app
                    * mounts onto the page (ReactDOM.render)
                    * ?special webpack config?
                        * we need a `shim library`
                * do we need special webpack build configuration for an `application shell`?
                * do non-`application shells` have a special webpack config/build as well?
                    * do they need a reverse `shim library`?
                    * i guess we need to bundle since we need to import it as a single file
                    * is a webpack bundle only importable as a FM if it is compiled with certain plugins or options, so that it has some extra format or compatibility layer? if so, then are FM-equipped modules importable as regular modules (as like an npm package)
            * check understanding: `polyliths` are applications composed of mfes where multiple mfes are also `application shells`. 
    * book: practical mf 2.0
        * notes
            * primary reason for mfes seems to be "amount of time to deploy either for production, or often just during development" (p9)
            * it sounds like what we have right now is a “polylith” or “multi-application architecture” (p9)
        * questions
            * (p11) "The figure below shows two applications, Home and Search. The Home page team currently has a Product Carousel on their page that we would like to reuse as an MFE on the Search page. 
                * is this advisable? should we be importing from another application (with its own `application shell`)? shou
            * runtime deployment: it updates everywhere when depolyed like hot module replacement. 
                * general HMR questions
                    * can/should we only HMR stateles lib modules? 
                        * but what if you have a stateful instance from that module in another module tho, or something similar? can you reinitialize a service during a module hook for the service module?
                    * how do we deal with state? do we get the state from the old version and have to ensure backwards compat with old state model?
                        * im guessing there must be api to pass stuff the new module
                    * what if that module had an open WS / stream connection or was waiting on an open http request.
                        * im guessing api gives you a dismount hook for module
    * [https://www.youtube.com/watch?v=2eGXIbc6lZA&ab_channel=ZackJackson](https://www.youtube.com/watch?v=2eGXIbc6lZA&ab_channel=ZackJackson)
        * topics_to_learn
            * that `remoteEntry` file that module federated plugin produced.
        * questions
            * why do we need a plugin to this? i understood the basic MF functionality was built into the webpack engine. 
                * maybe its just the "module promise" support that is built in?
                * "Module Federation is a feature built into Webpack 5 that makes it very easy to share code between applications." (p11)
            * button is not exported by the top index.js, we are importing using slash, so the package entry i guess must be the source folder. is webpack able to bundle source with some directory model such that we could import using slash after bundling? (if the answer is somehow yes, then i assume it wouldnt be able to do treeshaking, at least hahaha)
            * i assume the example itself is contrived, only used because it lent a visually interesting presentation. you wouldnt want to import from another app project, right?
* lll
    * do before monday
        * INTL update: jira + people
        * INTL code
        * respond splunk email
        * Loyalty update: jira
    * INTL update
        * The snippet was originally created because
            * when target loads onto the page, it updates the DOM according to the AB tests active for the user. Since target loads after the page has been rendered, and takes some time to be loaded in, the user will see the original content for a short time before target makes its updates, resulting in a content "flicker".
        * What the snippet did before 
            * 
![alt_text](images/image3.png "image_tooltip")

            * hide body until target loads and makes its changes. target will show the body content on its on-load event.
            * in case where target doesnt load because of technical failure or disallowed because of launch rules (its a GDPR country and user has not allowed cookies), then timeout prevent endless body hide.
        * problems with before
            * users that havent allowed target always have to wait until the timeout to see content
        * initial solution (eric)
            * read the satellite variables that determine whether target will be loaded or not, and show the body if not. this way we dont have to wait for timeout
        * problem #1
            * snippet runs before satellite exists on the page, cant read those variables.
        * solution #1
            * hide content and begin polling mechanism to wait until satellite is present. once we have it, then check variables to see if adobe will be loaded or not.
        * problem #2
            * launch / satellite is brought into the page at the bottom of the body, which causes many assets to queue up before launch in the network request pool.
            * on some environments, waiting for satellite with body hidden has a perceivable effect. production does not show a significant difference, but could still become a dormant problem that could be triggered if the assets loaded before it were to increase (like oversized or numerous images)
        * discussed performance concern with andrew julia and avinash
            * idea: read variables from env, not satellite
            * fact: production effect is negligible
        * concerns regarding idea
            * loss of control and too much hardcoding into hard to update place
        * discussed again
            * we definitely want the control and ease of update: integrate all the decision making logic into single launch variable
            * julia fact: the actual launch value is also saved in local storage, so we can actually just read this from localstorage
        * allowtarget created
        * another issue
            * when you allow functional cookies, launch wont update the sessionstorage value until after it loads next time, because the variable reads from the cookies on load.
                * this is because when launch loads, it reads the cookie setting. if the cookie setting is then changed, it only updates the next time it reads which is next load
                * effect is that you will see a layout shift the second load. (first time you never see AB content)
                * alternative is waiting for satellite when sessionStorage is false (which occurs when you hit yes for onetrust on the second load, or every load after hitting no)
                * another alternative is to have some other variable (maybe from launch) to indicate that we are past the first load post-ontrust select.
                    * maybe we could read the other onetrust variables, some are always true. 
                        * alaOnetrustActiveGroups &lt;- doesnt work because still we dont know if this is only our first time post-onetrust
                        * we need something that is set by LAUNCH post-onetrust
        * solution: using launch, we hook into the cookie acceptance actions to update the allowTarget var / sessionStorage value. now it can be trusted as the actual source of truth by our snippet
        * prob: localstorage not sessionstorage
* lll
    * general
        * check out our teams group, catch self up
    * tech connect meeting
        * notes regarding zack's decision
    * loyalty
        * MFE
            * make service now requests, update jira tickets
        * library
            * add launch darkly to ecom-checkout pr, try to get pr in
    * INTL
        * update script
        * update people
* lll
    * MFE
        * project details ([https://lululemon.atlassian.net/wiki/spaces/SRE/pages/1368645906/Prerequisites#Project-Details](https://lululemon.atlassian.net/wiki/spaces/SRE/pages/1368645906/Prerequisites#Project-Details))
            * account nickname: loyalty
            * domain prefix: lll
    * 
* lll
    * edmund: prep for 14th meet, write stuff into ticket
        * [https://lululemon.atlassian.net/browse/LOYALTY-122](https://lululemon.atlassian.net/browse/LOYALTY-122)
        * [https://lululemon.atlassian.net/browse/LOYALTY-12](https://lululemon.atlassian.net/browse/LOYALTY-12)3
* lll
    * INTL
        * respond to dan / update jira story
        * prep for working session with ayesha and friends
        * linda rothermich sent us some stuff
    * MFE
        * update stories / people
    * memberships
            * https://lululemon.sharepoint.com/:v:/s/PEPS/EQEryhuhPWBPpiFfHU6WNPcBRK2GCkYQNK7_bB3dUg8qIQ?e=Eii8Oo
            * PEPS Personalization promo video
            * PPI Personalization - cross-teams effort
            * https://lululemon.atlassian.net/wiki/spaces/p13n/overview?homepageId=2043285565
            * John Arnold to Everyone (7:04 PM)
            * https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2705328066/Adobe+Audience+Manager+PEPS+Segments  AAM PEPS Segments
        * accounts meeting with edmund, deirdre (manager), jeff (architect), jess (program)
        * contact mwa regarding auth: michael chen, jason cornwall 
            * auth lib: should we build onto mwa-auth?
        * sync with loyalty team regarding edmunds doc "details: loyalty team work"
        * INTL doc for monday
        * review contentful presentation, send out message to everyone
        * # update loyalty stories
            * edmunds doc
            * add mfe story
                * "make sure we have enough details in there or feel free to **utilize Atal for completeness**. Assign it to the Landing Page Epic."
        * # review eric brainmap and chat with him
        * # message the footwear people, tell them i'm not their guy anymore
        * # chat with terry
            * notes from personalization connect meet
            * questions
                * accounts wants to just take everything in. what does this mean for auth? there's already an auth library in mwa
                * international stuff (team wants to integrate)
        * # update loyalty arch runway and message notifying of update
            * add "decision" section
                * component level ownership for complex components
                * document for loyalty presence across the board
                * revert update including mfe in proposal, put it in decision
        * org: recs, links, etc

------------- ^ fri feb 25



* lll
    * footwear
        * "trufit"
        * talk to eric
        * talk to adam piette
* today
    * fliporders thing
    * cpa4it?
    * lll
        * footwear
        * snippet doc?
        * org: (recs, links, etc)
    * org
        * guitar
        * finance
* lll: snippet thing
    * todo
        * code
            * clean up
                * grab everything from global scope on demand
            * comment
            * defensive
                * try/catch
                * check shit is defined
                * timeout waiting for satellite
                * logs / errors
            * config
                * dont wait for satellite if config
                * always return true/false for conditionals
        * doc
            * describe problem
            * describe how shit works
            * describe every environment as-is
                * descriptors
                    * run a console.log script at various points
                    * adobe.target / network requests (`delivery`)
                    * do we ask for cookies / values in local storage
                    * is there a 3 sec wait
                    * experiments results on each env
                * envs
                    * development
                    * prod live
                        * au
                            * [https://www.lululemon.com.au/en-au/home](https://www.lululemon.com.au/en-au/home) 
                            * doesnt have local storage variable
                            * loads adobe target
                                * calls `delivery`
                                * window.adobe.target present
                        * uk
                            * [https://www.lululemon.co.uk/en-gb/home](https://www.lululemon.co.uk/en-gb/home) 
            * describe what should be done (solution)
            * describe every environment with solution (what did you do, what happens, and why)
                * code (configs, defensive code, logs)
                    * have to wait for adobe launch's satellite to load
                        * also have to wait for satellite to load methods
                * how to release
                    * adobe launch update to turn shit on (match env and prod evs)
                    * release snippet
        * meet with eric
            * fact-check doc
        * to reset cookies/local storage: application -> storage -> clear site data
        * adobe target
            * select emea properties
    * answered questions
        * what does "emea properties" stand for?
        * ** in development env, doesnt load target even though conditions met
            * using launch switch extension to use a dev environment
            * can the conditions present in dev build (has the cookie check) and logs 🚀 [Custom Script] OneTrust Performance Cookies Enabled (EU) - Tracking Enabled.
            * but no adobe.target in window or delivery call
            * **man, we needed to use a particular development environment, theyre not all the same**
![alt_text](images/image4.png "image_tooltip")

    * questions
        * if not all dev environments are the same (answered question), how do we set up a particular environment to use certain libs??
        * why does first condition include au, second one doesnt (confirmed)
            * 
![alt_text](images/image5.png "image_tooltip")

            * i guess because we want to add adobe target to au also? 
                * that would actually be different behaviour.
                * one of the location list conditions is always false for au, regardless of cookies thing
            * but this means that the location code in snippet is actually necessary (eric thought otherwise)
        * how to report errors in one-off snippets like this?
        * do we need to check location in snippet?
        * any visible adobe target A/B change we can look at to confirm?
        * why does au not have cookies prompt? is it not necessary there?
        * why does australia not ask about cookies? we dont have the localstorage value at all. if australia doesnt need us to ask, it seems unnecessarily complex to not have this at all. 
            * `PT 20 - All Pages - Load Adobe Target` (rule) programs that we check europe/australia AND allow cookies, 
                * 
![alt_text](images/image6.png "image_tooltip")

            * however `Cookies-AllowFunctional` (data element) checks samelocation again by itself and does an OR, thats how it works for au even though we dont ask for cookies on site
                * 
![alt_text](images/image7.png "image_tooltip")

    * notes
        * links
            * australia: [https://www.lululemon.com.au/en-au/home](https://www.lululemon.com.au/en-au/home) 
        * `Cookies-AllowFunctional` is not a cookie. it checks location
        * if we have target
            * `delivery?client=lululemon...` is the adobe target request for feature flags (according to bro)
                * ?? sif we block the `delivery` call, launch still removes #at-body-style (launch still considers it loaded)
            * window.adobe.target &lt;- populated
        * adobe launch has a logic that after we load target, it removes #at-body-style
        * #at-body-style
            * style tag with body: { display:none } 
                * shows nothing until target displayed
        * snippet injected by salesforce into head of page
            * appends #at-body-style
            * has 3000 timeout (in case adobe target doesnt remove it)
                * adobe shows up much earlier
        * _satellite
            * doesnt show up initially (first snippet exec, stop at line 247) 
    * experiments
        * preventing launch from removing
            * in au, run this code snippet with the parallel one, and it doesnt go away
                * let style2 = doc.createElement('style'); \
style2.id = 'test'; \
style2.innerHTML = def; \
parent.appendChild(style2);
            * then, run this snippet with the parallel one, and it goes away after the 3000ms callback is triggered
                * let style2 = doc.getElementById('test'); \
parent.removeChild(style2);
            * 
![alt_text](images/image8.png "image_tooltip")

        * 

------------------------------------------------



* lll
    * update doc => mfe
        * [https://lululemon.atlassian.net/wiki/spaces/Loyalty/pages/2707601825/Architecture+Runway](https://lululemon.atlassian.net/wiki/spaces/Loyalty/pages/2707601825/Architecture+Runway) 
* app framework & platform
    * 
* read confluence (mwap: terraform, etc)
* tasks updated
    * https://lululemon.atlassian.net/browse/LOYALTY-40
    * https://lululemon.atlassian.net/browse/LOYALTY-81 
    * https://lululemon.atlassian.net/browse/LOYALTY-80
* tasks created
    * https://lululemon.atlassian.net/browse/LOYALTY-89
    * https://lululemon.atlassian.net/browse/LOYALTY-90
    * https://lululemon.atlassian.net/browse/LOYALTY-91
* summer_do
    * go survive with rob in nature
* today
    * add pictures to file
* do
    * remove scalp cyst
* buy 
    * domain 5k
    * lumatone
* lll
    * eric meet for ramp up (brain map)
        * what access do i need?
    * links on docs
        * jira, confluence, target, etc
    * all my access on lll doc
        * jira, miro, adobe target, adobe launch
* tonight
    * INTL snippet thing
        * when done, update erics doc
    * jira stories
    * CPA4IT!!!!
    * proposal doc
* eric meet
    * cases in snippet
        * you pressed cookie -> target
        * no pressed cookie -> no target
        * no target -> release spinner
        * target -> set timeout in case target fails to load
* ask edmund if i can work holidays, also maybe weekends? 
    * (maybe not this time around, because it might seem like i wasnt working that much?)
* identity phase 1 proposal
    * Thisn order to achieve the goals of Loyalty Phase 1
    * phase 1
        * loyalty team creates new repo and new identity aws account
            * expose an identity library (npm & fm)
        * loyalty refactors auth tools into identity lib with accounts support
            * not touch auth stuff in ecom-checkout-client (deprecation model)
            * implemented by loyalty but supported by accounts team: 
                * accounts involved in design, kt, problem solving, acceptance signoff
        * loyalty team contributes loyalty-specific code into ecom-checkout-client (hub and dashboard) using identity lib where applicable. we import as fm during dev, and then switch to npm
            * we're going to have to add identity-lib as dependency
        * loyalty team contributes loyalty-specific code to ecom-web-app (landing page and other widgets) and wae-partials (navlinks) using identity lib where applicable. we import as fm during dev, and then switch to npm

---------------------------------



* membership subset
    * mytime: stop paying them
        * 70 locations => 70k
        * we upload a file to them every night (we need to stop doing that) stop the thing that uploads file
            * talk to them about getting rid of locations
    * aws accounts: 
        * events: lll.digital-events 
            * in cloud formation, delete some stacks
                * 1 delete mindbody-integ
                * 2 delete mytime in
                * 3 then the rest (digcore)
            * (IMPORTANT, DO FIRST) PagerDuty, Splunk and SignalFX are all monitoring the resources now. They should be disabled before you start tearing stuff down.
            * after deleting stacks, make sure the database in booking-srvc stack is gone
                * db is aurora: digcore in name
                * all snapshots 
            * priority list
                * stop paying money: stop mytime
                * removing pii (database)
                * saving aws resources: removing stacks
        * membership: lll.digital.membership
            * here we dont use cloud formation, we use terraform
            * use terraform destroy 
            * gitlab: 
                * dig-membership-srvc
                * digcore-booking-reports
                * digcore-store-import
                * enc-bk-*
* org phone todo list / tempdoc
* lll
    * membership
        * lenny
            * 1) links to membership need to redirect away (akamai)
            * kiwi-module-cne has package.json dependency to kiwi-module-memes (why)
            * talk to other people (dan)
            * we are gonna need memes to be there for when we do this. or at least for continued support
            * check out this chrome ext: webdeveloper
    * docs
        * proposal 
            * (after prepare doc) discuss with loyalists
        * sunset
            * (before prepare doc) discuss with loyalists
            * (before prepare doc) discuss with mark
    * update jira stories (comments & add stories)
    * onboard
        * read all of erics latest confluence
        * look for eric stuff on jira too
        * read all of loyalty-related groups and chats in ms teams
    * review launch darkly rec
    * read lennys linked docs (kiwi server, etc)
    * eric onboard onto 2 new things
        * what more service requests do i need?
            * dev env
                * username: Storefront 
                * pass:  lulustorefront
        * confluence: international shop adobetarget impementation architecture
    * new projects
        * (priority) gdpr
            * do: fill in missing part of doc
            * adobe experience platform -> tag properties -> cookies-alowfunctional
    * small
        * msg iheatu re: did you reach out to koala, we have meet?
* finance: investments
    * [https://www.youtube.com/c/FinancialEducation/videos](https://www.youtube.com/c/FinancialEducation/videos) 
    * corsair gaming
        * ask joey and andy
    * block inc 
        * ask jameel about block inc (square), why is it down
        * [https://www.investopedia.com/how-square-makes-money-4801197#:~:text=Block%20is%20a%20financial%20services,2020%20and%20is%20growing%20fast](https://www.investopedia.com/how-square-makes-money-4801197#:~:text=Block%20is%20a%20financial%20services,2020%20and%20is%20growing%20fast). 
        * 
![alt_text](images/image9.png "image_tooltip")

        * could be because pandemic? since festivals are coming back it might be a good buy. the sellers was a good profit driver. sellers also are like weed stores tho, festivals might not be as big a slice
            * in fact, the stock rose dramatically during pandemic
        * this cash app thing is like wealthsimple, seems like they were going hard on it, but the

-------

 \
 \
 \
lll analytics meeting recording

--------- tue feb 8 ^



* follow up with adam about remote
* lll
    * notes
        * what is cosy team again? (content team that works with contentful)
        * work on tech agreement story
            * get ok for pr marketing page to ecom-web-app for now
        * review our stories and stuff
    * 
* tonight (before day)
    * cra4it: jennifer's actionables
    * lll: doc
    * flip: start
* today
    * lll
        * install lenny and abdallah thing
        * diabetes meets
    * finance
        * pay credit cards
        * pay canadian tire credit card
        * call cra: i need that fucking code again

------- mon feb 7



* words
    * presumably