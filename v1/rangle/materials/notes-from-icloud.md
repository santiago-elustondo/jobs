

## 23-10-18

w_todo



* wc: notion page 
* *** wc: put up repo
    * someone needs to do this:[ https://blog.logrocket.com/how-to-build-component-library-react-typescript/](https://blog.logrocket.com/how-to-build-component-library-react-typescript/) 
* onboard onto kenvue

wc_talk



* show "webcomponents everywhere"
* clone example repos of wc compatibility instead of writing own demos (including dfx)
    * ** but we need one to demonstrate the monorepo architecture in react
        * [https://blog.logrocket.com/how-to-build-component-library-react-typescript/](https://blog.logrocket.com/how-to-build-component-library-react-typescript/) 
        * we should provide our example repo as link in the slides
* why 
    * angularJS migrations
    * dont do it if you dont need cross-compat
    * ~~Web components particularly excel as **leaf components**. ~~
        * ~~this is relevant to "architecting"~~
        * ~~react is better at state management (and generally application writing)~~
            * ~~this is the purpose of react~~
            * ~~this is why we still want react~~
    * ~~Web Components are *literally*, the standard component model of the web, written into the HTML specification.  (fasti-ui)~~
        * ~~thus likely to be the future, many features planned~~
            * ~~state management, etc. what react does now~~
        * ~~shadow dom solves encapsulation problems such that we dont need extra tooling headaches in order to achieve this with css modules or other options. ~~
            * ~~they can be a pain to import in consumer app, which is especially relevant for design systems~~
            * ~~debugging/experimenting/inspecting can be a pain (class names messy)~~
            * ~~not to be confused with virtual dom~~
    * ~~con: seo is a bit of a mystery~~
    * ~~con: accessibility requires special consideration, it must be done differently. screen readers can't always do their thing if they can't traverse the dom tree~~
    * ~~con: not as much collective experience as a community, harder to find info online compared to react~~
    * ~~adoption is new "Across the industry, we see a pretty big adoption since January 2020." fast-ui~~
        * ~~we're at a tipping point, with react about to release full support~~
* topics (slides)
    * anatomy of a web component + how to write a web component
        * dashes mean custom element
        * htmlelement is a class shipped with browsers
        * we need to define the element before using it
        * slots
        * controllers
        * shadow dom & shadow roots
    * ~~performance implications~~
        * ~~html templates mount/paint quickly because its a browser api~~
            * ~~react has to use the document properties api to apply the output~~
            * ~~deltas are similar because react will optimize to the minimum updates (like we do when writing wc) and in both cases we have to update using dom apis because we use javascript~~
            * ~~startup times are often the most crucial for ux~~
    * web components everywhere
    * ssr
    * library adoption and integration within org 
        * **** (dfx sticky notes) *****
        * * this is important because its somewhat relevant to arch
    * Attribute values can only be strings.
    * angular elements (shit all over it, its react to)
    * stencil vs lit vs ?
* todo
    * (slides) *** listen to architecture call (dfx)
        * also see tickets created by dfx team (even without rangle)
    * (slides) write down challenges => make slides
        * ask people from dealer-fx 
            * show us pull requests
            * any other repos we can look at?
        * anatomy of a web component, how do they work
            * extending htmlelement / registering
            * reactive controllers
    * (demo) clone and show dfx repo itself
    * **** check out below (DEMO REPOS) ****
        * [https://web-highlights.com/blog/how-to-use-web-components-in-react/](https://web-highlights.com/blog/how-to-use-web-components-in-react/)  (demo!)
            * dealing with typescript types
        * [https://coryrylan.com/blog/how-to-use-web-components-in-react](https://coryrylan.com/blog/how-to-use-web-components-in-react) (demo!)
            * experimental react + wc
        * [https://css-tricks.com/building-interoperable-web-components-react/](https://css-tricks.com/building-interoperable-web-components-react/)  (demo!)
            * doesnt use experimental, does the ref trick and talks about attribute strings etc
            * great solutions described
        * react compat utils (** try these)
            * [https://www.npmjs.com/package/@lit-labs/react](https://www.npmjs.com/package/@lit-labs/react) 
            * [https://github.com/adobe/react-webcomponent](https://github.com/adobe/react-webcomponent) 
        * [https://blog.bitsrc.io/how-to-use-web-components-with-react-5b8bb59d6c5](https://blog.bitsrc.io/how-to-use-web-components-with-react-5b8bb59d6c5) (demo!)
            * wc lib: fast-ui (you dont have to write your own components necessarily, but can extend)
                * microsoft
                * they have a wrapper library for mounting on react
            * related topics
                * micro frontends[ https://blog.bitsrc.io/how-we-build-micro-front-ends-d3eeeac0acfc](https://blog.bitsrc.io/how-we-build-micro-front-ends-d3eeeac0acfc) 
                * monorepos
                * code sharing and reuse[ https://bit.dev/blog/how-to-reuse-react-components-across-your-projects-l4pz83f4/](https://bit.dev/blog/how-to-reuse-react-components-across-your-projects-l4pz83f4/) 
                * design systems[ https://blog.bitsrc.io/how-we-build-our-design-system-15713a1f1833](https://blog.bitsrc.io/how-we-build-our-design-system-15713a1f1833) 
        * [https://bootcamp.uxdesign.cc/the-power-of-web-components-in-frontend-development-with-angular-6ef04bdc62aa](https://bootcamp.uxdesign.cc/the-power-of-web-components-in-frontend-development-with-angular-6ef04bdc62aa) (demo!)
            * angular elements
            * ** we use straight webcomponents in dfx right?
        * [https://www.reddit.com/r/Angular2/comments/omlqwu/thoughts_on_angular_element_aka_web_components_in/](https://www.reddit.com/r/Angular2/comments/omlqwu/thoughts_on_angular_element_aka_web_components_in/) 
            * angular elements
            * interesting migration reasoning!
            * bad performance: bundle sizes are large and bad performance
        * [https://webcomponents.dev/blog/all-the-ways-to-make-a-web-component/](https://webcomponents.dev/blog/all-the-ways-to-make-a-web-component/) 
            * performance comparisons, has react but no angular (preact is good)
        * [https://www.angulararchitects.io/blog/angular-elements-web-components-with-standalone-components/](https://www.angulararchitects.io/blog/angular-elements-web-components-with-standalone-components/) 
            * with angular we can use shadow dom
        * [https://www.fast.design/docs/resources/why-web-components/](https://www.fast.design/docs/resources/why-web-components/)
            * fast-ui claims its easy to interoperate and that performance is improved
        * [https://medium.com/jens-jansson/start-using-web-components-in-react-6ccca2ca21f9](https://medium.com/jens-jansson/start-using-web-components-in-react-6ccca2ca21f9)
            * old article about polyfills for old browsers
                * now everyone supports, except for IE and other dinosaurs
                * * and for these u just include the polyfill.
                    * if you dont care about old browsers, you save yourself some bundle size by not including
        * ***[ https://lit.dev/docs/frameworks/react/](https://lit.dev/docs/frameworks/react/) 
            * ** explains react compatibility problems + react wrappers generated via utils
                * slots, events
                * mapping DOM events to React-style callbacks, and enables correct type-checking in JSX by TypeScript.
            * custom hooks from [reactive controllers](https://lit.dev/docs/composition/controllers/). 
            * new and experimental, as is all of lit labs
        * [https://lit.dev/docs/ssr/dom-emulation/](https://lit.dev/docs/ssr/dom-emulation/)
            * lit is a great choice today, they considered all the important problems like ssr and compatibility with react including hook for controller
            * ssr feature is experimental
            * When running in Node, Lit automatically imports and uses a set of DOM shims, and defines the customElements global.
        * [https://developer.vonage.com/en/blog/using-web-components-in-a-react-application-dr](https://developer.vonage.com/en/blog/using-web-components-in-a-react-application-dr) 
            * React has its [SyntheticEvent](https://reactjs.org/docs/events.html) instance that is a wrapper around a browser's native event. 
        * **[ https://stenciljs.com/docs/react](https://stenciljs.com/docs/react)
            * stencil also generates wrappers
            * ** endorses monorepo structure
            * ** monorepo build tools setup guide
            * all framework integrations:[ https://stenciljs.com/docs/overview](https://stenciljs.com/docs/overview) 
                * angular[ https://stenciljs.com/docs/angular](https://stenciljs.com/docs/angular) 
        * *[ https://react.dev/reference/react-dom/components#custom-html-elements](https://react.dev/reference/react-dom/components#custom-html-elements) 
            * "dont use experimental in prod"
        * **[ https://github.com/facebook/react/issues/11347](https://github.com/facebook/react/issues/11347) 
            * discussion about using react inside webcomponents
            * some other useful general comments from meta people
            * * it is scheduled for react 19
            * more about react integrations
        * [https://www.grapecity.com/blogs/using-web-components-with-react-2019](https://www.grapecity.com/blogs/using-web-components-with-react-2019) 
        * [https://itnext.io/react-and-web-components-3e0fca98a593](https://itnext.io/react-and-web-components-3e0fca98a593) 
            * online web component registry
            * generally good and comprehensive article about react + wc

w_workstreams



* video content with jaffree and (new alicia, what was her name?)
* bench 
    * presentations (kt): 
        * platforms/devops/aws
        * deep dives: react performance
        * build tools: rollup, webpack, etc
        * js frameworks & utils: svelte, 
        * wc: stencil etc
        * typescript: show us some examples of new and interesting feature
        * angular standalone components[ https://www.angulararchitects.io/blog/angular-elements-web-components-with-standalone-components/](https://www.angulararchitects.io/blog/angular-elements-web-components-with-standalone-components/) 
        * our solutions (open source solutions or just an approach that worked): 
            * michael's figma to panda (kenvue)
    * research (r&d)
        * ** design systems with dynamic cms (like lululemon and kenvue)
            * contentful issues
        * monorepo tools comparison
            * nx generations (scaffolding)

gah_app



* How does content get into the system? 
    * Created by hand (eg/ typing) 
    * Podcast aggregation (eg/ system subscribes to a "feed") 
    * Blog scraping/subscription (one of our users has their own blog or similar on other social media platforms… and allow us to get the content - automatically ). NB/ Still requires curator/publisher to publish. 
    * Job Board via external linkage
* questions
    * platform limitations, what are we using
    * what was that about rss feed?
        * assuming we mean the app's home/browse/for u page?
        * i think also we mean external content like podcasts, which we aggregate into our feed?
            * how do we consume these? 
                * do we upload them manually? (i think so)
                    * is there some webhook we should use? (or possibly an endpoint to poll)
                    * keep them in db as a post? (i think so)
                    * * we shouldnt do this now
* notes
* todo
* outstanding questions (ask bert)
    * what should we use for analytics (a/b testing, etc)
* arch
    * webapp, port into phone apps later
    * url map
    * entities
    * auth + (? any other integrations with existing system)
        * return from redirect
    * platform
        * ? limitations: there are some (rec?)
        * app
            * next.js ? (ask ranglers)
                * ssr for search engines
                * ? how
                    * data loaders/spinners
                    * patterns
                    * dev tools
        * database
            * mongo atlas?
        * hosting/cdn for content assets
            * file sizing (shrink pictures)
        * hosting/cdn for client build
        * devops
            * github actions?
            * vercel?
        * server
            * lambdas?
            * kube?
        * observability
            * telemetry ()
            * analytics (ab tests)
        * not firebase
            * they dont need live subscriptions
            * they would have to use firework, which is too invasive
            * stuck on node version



## 23/10/31


## w_notes



* next week 


## w_todo



* ken radius meets
* ask fidelia how promotion/analytics work
* cicero create video of his wc his presentation
* jason about thomas
* content: make leah's webpack video, wc reactto
* free agents 
    * schedule recurring friday presentations
    * review adam article
        * [https://docs.google.com/document/d/1BaeWXbCJyFb8j2Q5ZDV3DO3eVtNyN5NPnXo2dh7kruM/edit?usp=sharing](https://docs.google.com/document/d/1BaeWXbCJyFb8j2Q5ZDV3DO3eVtNyN5NPnXo2dh7kruM/edit?usp=sharing)
* tech regroup topics
    * free agents
        * spencer: ng 17 article
        * matt: ng for react devs article
        * adam: 3 articles
        * will: next.js presentation friday
    * radius-wc
        * cicero: dfx challenges & notion info pages
* kenvue: reschedule daily dev huddle
* * gah: 
    * get opinions on cms/db (mike, bert, steph)
    * *** review anuj proposal (make notes/comments)


## kenvue



* nathan: 
    * current: image subheadline text (priority, started today)
    * needs reviews on 2 prs on dev channel (details in recording)
* raven: 
    * current: programatic presents in stackbit (starting research)
    * previously did some work on card carousel
* bohdan: 
    * current: article page layout (going strong, small blocker cleared)
    * worked on hero banner integration on an unrelated story branch. 
        * moving to its own branch and santi takes it
* dewan: connect
    * current: card carousel (santi will check in)
* karen + shatabdi: product list
* santi: 
    * [https://rangle.kanbanize.com/ctrl_board/4/cards/198/details/](https://rangle.kanbanize.com/ctrl_board/4/cards/198/details/)  (mike may have context)
    * [https://rangle.kanbanize.com/ctrl_board/4/cards/159/details/](https://rangle.kanbanize.com/ctrl_board/4/cards/159/details/)  (hero banner integration)


## 23/10/16



* old phone photos

w_todo



* (meet) catch up with: 
    * jason offet
    * nathan
* * webcomponents presentation
    * (meet) bring wc r&d team together
    * [https://www.notion.so/rangle/Web-Components-03d4432ff8a24814b58dc9c1d415ce7a](https://www.notion.so/rangle/Web-Components-03d4432ff8a24814b58dc9c1d415ce7a) 
    * [https://www.notion.so/rangle/study-wc-design-systems-443b2d223f99499283aa0adeceb7169d](https://www.notion.so/rangle/study-wc-design-systems-443b2d223f99499283aa0adeceb7169d) 
* * (meet) support dfx team
    * * talk to ken / thomas
        * thomas feedback style
* let jason know about jetblue
* * (meet) momentive
* catherine re vacation
* * free agents
* *** jason: ask about momentive td

w_workstreams



* jb + platform
    * let jason know about the jimmy talk, we need radius platform
* momentive
* dfx + web components
    * radius web components team
* gah
* internal
    * free agents 
        * catch up
    * upskill: presentations and articles
        * projects
            * angular/react under the hood
            * web components
    * notion track
        * amt of cumulative bench time
        * amt of knowledge sharing/presentations per week
        * amt of pairing hours per week on particular projects
        * amt of learning time for each people
* reports
    * how to help jason offet?
    * culture amp stuff
    * talk to thomas: needs tech up
    * talk to joaquim: promotion / web components

meet_poliana



* any idea what is holding up design
* monorepo issues resolved?
* what r u working on, can i help
* what kind of help does thomas provide
* ** talk to ken / thoms

meet_gah-2



* the user retention you're after and certainly the gamification aspect depends heavily on the quality of our UX. how are we planning to undertake product design? 

	•		⁃	how are you planning to host the data and infra generally? how much of this is net new? the authentication clearly isnt \



## 23/09/27

feedback interviews



* rbc: joaq, rafae, deidre
    * scott
* jetblue: mamadou

review interviews 



* report
    * what projects were u in, tell me about them
    * how do you think you've grown these last 6 months
        * how do you want to grow the next 6 months
    * ask capability survey questions
        * top 3 techs and how good are you?
        * how good are we as a company in different techs? (the ones they have an opinion about)
        * what are you interested in learning
    * ask general feel questions: 
        * enthusiasm / motivation / happiness / stress
        * do you want longevity at the company
        * what kind of role model do you have for your near future
        * do you feel supported?
    * i give them feedback
* peers
    * what was it like working with them
    * how have they grown
    * what should they work on to get to the next level?

#thomas



* [https://docs.google.com/document/d/1uDq-7m4FFuc8mhK4N7geuvaf7y7PeplIPnc8Y1k387c/edit#heading=h.ic9xmphh48ms](https://docs.google.com/document/d/1uDq-7m4FFuc8mhK4N7geuvaf7y7PeplIPnc8Y1k387c/edit#heading=h.ic9xmphh48ms) 

#rafae  



* RBC BGD
    * building components for specific feature on existing angular app
    * there were cool technical challenges: 
        * fixes a lot of stuff with broken application, rxjs not done properly, ngrx
            * andrew lam was good so you he got to learn from him
    * andrew lam (SA), eduardo (dev, now SA), nathan, cher g, gavin
* RBC CLC (client life cycle - leafs)
    * new internal angular application
    * full stack angular + internal component lib (rig)
    * feels: managed very well.
        * frustration: technical decision that should be revisited
    * jas, robyn, joaquim, will, cicero
* how is joaquim (really well)
* strong suit
    * a lot of angular
    * not a lot of ng
    * node
* 

#jordan (rec)



* they kept him on dreamfactory for an extra using underspend, william rolled off. i guess that means he was doing comparatively better?
* projects
    * momentive
    * backfilled on jb .com (6 weeks)
        * translation service 
    * bench ai
    * dreamfactory (jas)
* techs
    * css 
    * angular / react
        * 3-4 / 5
        * arch interest
        * performance interest
    * not so much platform
* learnings
    * momentive taught a lot
    * project with spencer was fun, doing research together
* collective capacity
    * biweekly tech huddles have great knowledge, but its not transmitted
    * more mentor, knowledge 
* emotion
    * happy, stressed, excitement
* sept_27 review at home
    * he's a doer not an architect
        * he understands and follows set patterns well 

#geethu (rec)



* projects
    * website team (until march)
        * nataliya, nancy, yena
    * movebuddy (2-3 months) (together with jet blue)
        * working relationships
            * adam (most senior), vyk, tarek
                * got a lot of support from adam
                * very impressed by adam's leadership on the project
            * matthew thomas?
        * challenges
        * what did you learn
            * a lot from adam: not jumping to conclusions and commitments before understanding
            * a lot about front end work
        * how did you feel
            * she misses the project and wishes she could have stayed longer
    * jetblue bds (4 months)
        * general 
            * everything already automated, project had been going for a long time, also some manual stuff
        * working relationships
            * namrta, natalia m, matthew ford (client), Teunis
        * challenges
            * felt like couldnt contribute much cause project is already well established. figured out and brought in an accessibility assessment plugin, thats the only thing she 
        * what did you learn
            * tech: mable (e2e)
            * accessibility
        * how did you feel
            * not very challenged
    * fast-track
    * svg-clips
        * challenges
            * figuring out the responsiveness part
                * seeked out a lot of support: karen, thomas, nataliya
                    * karen really helped a lot. debugged and learned together.
                * LEARNINGS: "how to think like a developer" 1) define what we are doing and what we are not doing (scope), how to research solutions and how to ask questions. 
                    * thought of putting everything in one file or another, different approaches.
            * had a platform to show her skills
* how have u grown
    * she knew html tags, had some theoretical knowledge of js
        * now she knows how to tackle functionality and build things
        * 1.5/10 -> 6/10
* capability 
    * testing: 
        * e2e
            * mabel
            * cypress 4.5/5 (best tool i can suggest, some people say selenium, but we dont use it much for our projects, would use cypress over mabel)
        * integration
            * testcafe 3/5 (kind of theoretical still)
        * regression
            * mabel + testcafe
    * react (3/5) "put me in a project, i will research and get it done"
    * javascript (3/5) "enrolled myself in udemy"
    * css (3.5/5)
* ask general feel questions: 
    * "happy where i am now, company wise. everyone is so supportive"
        * thomas, santi
    * it's been 2 years since last raise, she deserves one

todo



* talk to abdalla/ben about ai. they go to ai meetups and do a podcast.
* meet with mat and leah

leah_meet



* 1) react: 3.5/5
* 2) cms: 3.5/5
* 3) typescript: 3/5
* can see herself at rangle in 5 years, doesnt like to jump around a lot.
    * michael mrowtez is inspiration
* called out thomas garrison in particular
* notes
    * motivation
    * people like to help
    * people will credit you with 

people



* #leah 
    * todo
        * digest 1:1
* #jason-offet 
    * todo
        * read docs:[ https://docs.google.com/document/d/1a4lcQbjtOuM2KiiXxXMlIK2WNOitMX-aephs9scM8gQ/edit](https://docs.google.com/document/d/1a4lcQbjtOuM2KiiXxXMlIK2WNOitMX-aephs9scM8gQ/edit) 
    * 1:1 observations
        * anderson client projectreally good comms, clear explanations. seems like he really understood the client team dynamic
            * **[get jason feedback]**
    * **[release article]**
* #geethu 
    * todo
        * X off the top
        * X direct dms
        * X peer feedbacks on cultureamp
        * otter recordings
        * (only a few) slack messages anywhere
        * (todo) interview peers
        * write my cultureamp feedback
        * X interview
        * competencies
        * compare with role checklists
        * write: improvement/growth
        * read self reflection
            * [https://rangle.cultureamp.com/performance/completed_self_reflection?selfReflectionId=5727683](https://rangle.cultureamp.com/performance/completed_self_reflection?selfReflectionId=5727683) 
    * channels
        * personal dms
    * growth
        * 0 dev -> PR, succesdsful research, and presentation in svg-clip
    * recollections
        * caught up quickly after time off
            * unplanned leave of absence due to urgent family stuff
            * came back and was eager to get caught up quickly **[ownership]**
            * recruited asokan's help catching up, who graciously helped out **[seek support]**
        * svg-clips
            * took ownership over her task even though it was out of her comfort zone (could be trusted to seek the support she needed)
                * got help from nataliya, who graciously helped out
                * asked me for help as well
                * very dedicated to solving bugs and devex problems, asked for support and made herself very available at short notice
                * proactive at keeping team up to date with progress and challenges
                    * [https://rangle.slack.com/archives/D04L2SM6VL5/p1689081118693069](https://rangle.slack.com/archives/D04L2SM6VL5/p1689081118693069) 
            * worked hard on her presentation
                * i gave her feedback, she redid script and applied feedback perfectly, no further changes needed
            * understood problem, tools, context
                * sanity, next, storybook, etc. she would only get stuck on project-specific things that were actually weird and hard to debug
                * * found a better (cleaner) solution to the problem than the one we had suggested. it was in fact better and more sophisticated. defining and switching the paths directly in CSS. rather than multiple svgs to contain
        * fast-track
            * i could tell that she understood the concepts when i was explaining
            * she got a lot of progress when time allowed, and would reach out when she had time to ask what she should do
        * reached a number of times to ask for 1:1s
            * what to do next, how to learn/grow. for fast-track & fried-rice-balls
            * what to have ready for svg-clips
        * chromatic: gave great info, very valuable to final report
            * [https://rangle.slack.com/archives/D04L2SM6VL5/p1689963913963199](https://rangle.slack.com/archives/D04L2SM6VL5/p1689963913963199) 
        * very dedicated to growth
            * jumps on anything
            * wrote an article early on, which alicia liked
                * [https://rangle.slack.com/archives/D04L2SM6VL5/p1676486616372379](https://rangle.slack.com/archives/D04L2SM6VL5/p1676486616372379) 
                * [https://rangle.slack.com/archives/D04L2SM6VL5/p1675802608090219](https://rangle.slack.com/archives/D04L2SM6VL5/p1675802608090219) 
                * [https://docs.google.com/document/d/1h5P-x7I1G2kaeUWWkbkNbo-pJQQnDeJvNCU-tOcuJNE/edit?usp=drive_web](https://docs.google.com/document/d/1h5P-x7I1G2kaeUWWkbkNbo-pJQQnDeJvNCU-tOcuJNE/edit?usp=drive_web) 
            * first person to dive right into learning js (dev-fast-track)
                * [https://rangle.slack.com/files/U02EVGF3MH6/F04PCTMPFPS/screen_shot_2023-02-08_at_11.43.13_am.png](https://rangle.slack.com/files/U02EVGF3MH6/F04PCTMPFPS/screen_shot_2023-02-08_at_11.43.13_am.png) 
            * showed interest in CMS
                * [https://rangle.slack.com/archives/D04L2SM6VL5/p1689867071275349](https://rangle.slack.com/archives/D04L2SM6VL5/p1689867071275349) 
            * made sure to stay involved even while on projects, as far as project allows
                * [https://rangle.slack.com/archives/D04L2SM6VL5/p1688758008899489](https://rangle.slack.com/archives/D04L2SM6VL5/p1688758008899489) 
                * [https://rangle.slack.com/archives/D04L2SM6VL5/p1679508430302469](https://rangle.slack.com/archives/D04L2SM6VL5/p1679508430302469) 
        * diligent and thorough regarding visibility and team collab
            * [https://rangle.slack.com/archives/D04L2SM6VL5/p1688066928233299](https://rangle.slack.com/archives/D04L2SM6VL5/p1688066928233299) 
    * messages "from geethu" anywhere
        * collaborated with karen and gave updates for team
            * [https://rangle.slack.com/archives/C05DQJUF4ER/p1691087163409299](https://rangle.slack.com/archives/C05DQJUF4ER/p1691087163409299) 
        * let me know every time there was a personal situation that needed attention and would keep her away for a while, even if she could have not told me. otherwise she was always available. also informed every time she could not attend a meeting due to conflict, and otherwise was reliably present and engaged
    * cultureamp reviews
        * mamadou
            * you improved a lot and put in serious effort
        * thomas
            * he was very impressed, brilliant feedback
            * "upskill with amazing speed and proficiency"
            * "amazing attitude and ability to collaborate"
            * "great initiative"
        * karen
            * "keen to learn, always working on acquiring new skills and practicing existing skills"

	•		⁃	"c


## 23/08/31 \
 \
**#dfx-comparison**


## todo



* jihyun interview video
* brenda's tradeoffs doc
* brenda's poll
* interview other ranglers that were involved in WC projects 
    * jason santos was there with brenda
    * (take opportunity to talk about reports for perf review? could even just list out all reports and ask who they worked with)
* other dealerfx videos?
* what about non-technical design part?
    * like, whether we base our designs on existing libraries and just match their designs (look at their css)
* our figma miro board (link in resources)
* slack search


## tarek's decision criteria



* time to adoption
* long-term health
* dfx ability to support
* flexibility (snap-on)


## resources



* brenda's tradeoffs doc
    * [https://docs.google.com/document/d/1kLa8vCFQil9SZIO4MnaNXxol-0L2fJ_sHyNIO7optpU/edit#heading=h.seot8ujji778](https://docs.google.com/document/d/1kLa8vCFQil9SZIO4MnaNXxol-0L2fJ_sHyNIO7optpU/edit#heading=h.seot8ujji778) 
* jihuyn
    * [https://drive.google.com/file/d/1pfASTNRgmMwpxCNmltDCHsowhF73b-SI/view?usp=sharing](https://drive.google.com/file/d/1pfASTNRgmMwpxCNmltDCHsowhF73b-SI/view?usp=sharing) 
* our comparison board (figma)
    * [https://www.figma.com/file/fThbkCVWHQY8DQRWsgEYvC/Next-Steps-for-DFX?type=whiteboard&node-id=0-1&t=x9HwwYwbPAv6UbyN-0](https://www.figma.com/file/fThbkCVWHQY8DQRWsgEYvC/Next-Steps-for-DFX?type=whiteboard&node-id=0-1&t=x9HwwYwbPAv6UbyN-0) 
* brenda's slack survey
    * [https://rangle.slack.com/archives/C03BB9SAK9Q/p1692709118860499](https://rangle.slack.com/archives/C03BB9SAK9Q/p1692709118860499) 


## strategic updates for tarek & brenda



* from the video i think he would actually go with our recommendation if laid out with clarity.


## questions



* for each
    * question overview
    * variables 
        * is the question valid? does it depend on another answe?
        * what factors affect the calculus
    * considerations
        * what do we care about? kind of like goals
        * how important is each consideration
    * options
        * for each
            * option overview
            * pros/cons


* goals
    * ? long term: support react
* misc
    * brenda has a ton of experience with web componets, she's been part of the conversation for many years.[ https://rangle.slack.com/archives/CC5CN2QA0/p1579370445005800?thread_ts=1579271329.000700&cid=CC5CN2QA0](https://rangle.slack.com/archives/CC5CN2QA0/p1579370445005800?thread_ts=1579271329.000700&cid=CC5CN2QA0) 
        * her intuition should be trusted 
* rangle experiences
    * wabtec (WC using stencil.js)
        * [https://www.notion.so/rangle/Wabtec-Volt-b04be351857644fab4416430e6dbcfc1](https://www.notion.so/rangle/Wabtec-Volt-b04be351857644fab4416430e6dbcfc1)
            * "There were a number of bugs and unexpected issues that came up as we tried to work with it & other technologies."
            * "When working with new technologies, it should be expected that it will take longer for teams to get comfortable with. Two technologies will not always be easy to set up together as experience with Stencil.Js. This should be taken into consideration in estimates earlier on during pitch."
        * [https://rangle.io/our-work/wabtec](https://rangle.io/our-work/wabtec)
            * "Leveraged Stencil as a technological vehicle to output web components and components compatible with Angular and React"
    * * ceridian (2022)
        * [https://www.notion.so/rangle/Ceridian-Platfor-bc079d7768bb48a5b9c23d7b0b0e298f](https://www.notion.so/rangle/Ceridian-Platfor-bc079d7768bb48a5b9c23d7b0b0e298f) 
        * people: jason santos, stephanie zeng, nancy, adam sullovey, evelyn cheung
        * [https://rangle.slack.com/archives/C03BB9SAK9Q/p1692709118860499](https://rangle.slack.com/archives/C03BB9SAK9Q/p1692709118860499)
            * steph: (they moved from lit to fast) "When I started at Ceridian they already moved on to use Fast from MS. My impression is Lit is good for react project and stenciljs for Angular?" 
            * jason: "but my question is: were they used in a successful feature?"
            * steph: "The FAST components are a few components such as checkboxes. There were many discussion how we should migrate them back to React components, but the leads prioritized other work instead because they really wanted to see a web component future."
            * * jason: "that’s usually the problem. Web components behave marvelously in isolation in laboratory conditions.. but when it comes to compose them in the real world, there’s a ton of small annoying things that you need to worry about"
            * jason: "I remember having issues with layout shift, because of loading the components then hydrating the custom elemetns, and, of course, cost of building components.. they were a bit harder to write and required the devs to understand a bit more of javascript than framework components. Loading complex data into components also required you to manually grab the element and use attributes — which required the components to have an additional ‘pre-loaded’ state.. Stencil solved some of these things a bit, but not all of them and not in all cases."
    * willian: web components and the dilemma of future-proof solutions
        * [https://www.notion.so/rangle/WebComponents-and-a-the-dilema-of-future-proof-solutions-dd830eb97d3c41749f657dfd1c04a1ae#679ccac830b24e1c80285eb2f9001e88](https://www.notion.so/rangle/WebComponents-and-a-the-dilema-of-future-proof-solutions-dd830eb97d3c41749f657dfd1c04a1ae#679ccac830b24e1c80285eb2f9001e88) 
        * contributions from Ken, Artem, Stephanie, Evelyn and Adam
    * [https://rangle.io/blog/web-components-part-2](https://rangle.io/blog/web-components-part-2) 
        * [https://custom-elements-everywhere.com/](https://custom-elements-everywhere.com/) 
            * ? is this still valid? ?? (react stuff is 2017, also why does it say angular is fine)
                * if up to date, then there must be issues that they are not capturing
            * "React passes all data to Custom Elements in the form of HTML attributes. For primitive data this is fine, but the system breaks down when passing rich data, like objects or arrays. In these instances you end up with stringified values like some-attr="[object Object]" which can't actually be used."
                * "Custom Elements are the lynchpin in the Web Components specifications."
            * "Because React implements its own synthetic event system, it cannot listen for DOM events coming from Custom Elements without the use of a workaround. Developers will need to reference their Custom Elements using a ref and manually attach event listeners with addEventListener. This makes working with Custom Elements cumbersome."
    * [https://react.dev/reference/react-dom/components#custom-html-elements](https://react.dev/reference/react-dom/components#custom-html-elements) 
        * at least they are working on better react integration.
        * * eventually the web-components solution should be a good idea, but it might be too early. Lit will change, react will change, there will be a lot of maintenance necessary. from our experiene we know that its not ready
    * nancy seems to have looked into lit integrations.
    * TIAA
        * people: robin dalgleish
        * [https://www.notion.so/rangle/Material-Component-Quick-Audit-2f3fad69d2264f9baacf5edf17e99e29](https://www.notion.so/rangle/Material-Component-Quick-Audit-2f3fad69d2264f9baacf5edf17e99e29) 
            * "RISK: State projection/binding in web components"
            * "RISK: Unsure of behaviour or feasibility of ngx-skeleton-loader in web components"
        * [https://www.notion.so/rangle/7-8-2022-Spike-stand-up-notes-7aae5bf52c664e4896298e2f3bd7b2d4#8395f17c88944d63a5e871baf079b362](https://www.notion.so/rangle/7-8-2022-Spike-stand-up-notes-7aae5bf52c664e4896298e2f3bd7b2d4#8395f17c88944d63a5e871baf079b362) 
            * "Concerned with bundle size of web components as angular element bundles can start to get larger and larger especially when angular material is implemented. Not too bad for small components but with larger ones the bundles will increase fast ex. Button vs. Table"
        * had to migrate from lit1 (2019) to lit2 (2021): major changes, new API
            * [https://www.infoq.com/news/2021/09/lit-2-custom-directive-reactive/#:~:text=Lit%202%20features%20a%20new,was%20released%20in%20February%202019](https://www.infoq.com/news/2021/09/lit-2-custom-directive-reactive/#:~:text=Lit%202%20features%20a%20new,was%20released%20in%20February%202019) 
            * also LitElements before, which was worse
        * [https://rangle.slack.com/archives/D04LU0RQ24A/p1692715878066969?thread_ts=1692714789.244309&cid=D04LU0RQ24A](https://rangle.slack.com/archives/D04LU0RQ24A/p1692715878066969?thread_ts=1692714789.244309&cid=D04LU0RQ24A) 
            * brenda: "Mixing was an issue for TIAA because we were composing out of wrapped Angular Material elements.  What a mess! But still, we would have an Angular/Vue/React/JQuery parent component, which will need to interact with it's child Web Components.  In the form example, each framework is expecting to talk to the children a different way, so we would need to provide a protocol (or set of protocols) for the components to talk to the parent form."
        * *[ https://rangle.slack.com/archives/C04AB9K9G/p1642712925001200](https://rangle.slack.com/archives/C04AB9K9G/p1642712925001200) 
            * good stuff here
        * *[ https://rangle.slack.com/archives/C029Z63MA/p1634031398058000](https://rangle.slack.com/archives/C029Z63MA/p1634031398058000)
            * review of blog posts after some time
            * adam: "Part 2 feels optimistic after I’ve faced some challenges with WCs."
* misc
    * there's work to still do in WC to make it work properly, and patterns to set (for integration and 



* brenda tradeoffs doc
    * "understandings" section
        * ** point 3: the planned work on legacy apps is either a rewrite in angular or outside of scope. so we don't need to support jquery or vue for legacy. (i confirmed this during an interview)
        * "Lit provides a wrapper for React, which is still in the experimental stage."
            * react wrapper isnt even there, we're gonna have to change later if they release
        * (weak point) lit has other limitations and will likely not keep up: accessibility, SSR, etc.
        * "In order for a Lit component to integrate with a form, it will need to handle the expected behaviours for form components.  A React or Vue form would expect different behaviours to be implemented.  A jQuery application would also need to be updated to work with whatever architecture was implemented for forms."
            * you cant actually reuse the atoms cleanly across frameworks. you end up having implement interfaces for each (might as well implement the whole atom). devs will add in components and only build or test the interface for their platform. at best you end up with 2 separate libraries in one, one for react, one for angular.
            * "For instance, if the application opted to use the popular library react-hook-forms there would be different integration considerations for form components than if there was no library in use."
        * "It has been our experience that as we test Web Components that we have developed across different frameworks, we often find that we need a second pass on the components to fix issues that we have missed in one of the frameworks."
            * this is terrible for process (dev & QA). going to kill velocity and quality
        * If we're using ElasticUI, React applications have the option of using the EUI React Component Library. Same with Material UI. So, pure "chunks" (molecules) + MFEs (organisms) + open source component library (atoms)
        * ? "There is no efficient way that we know of to use Angular Design System components in another framework."
            * ? what do we mean by this?
        * ? ng elements MFE
            * ? can we not keep them pure? (only UI logic, ideally stateless)
        * ? in order to support react in future, do we need to consider or do any work towards the react integrations now? or can we just ignore it and when the time comes they only need to figure out an adapter layer? like, do we need to build the components in a particular way? or, worse yet, would we need to test the components in react also to be sure it will work?
        * ? "Web Components usually need extra scaffolding in the consuming application at integration time."
            * ? are we just talking about the adapter layer here?
            * ? also, is the adapter later a once and done, or does work need to be done on most components, tests added for them, and mounted on storybook again, all for react?
  


* jihuyn ("june") interview [CONTINUE AT 31:00]
    * performance is one of his concerns. he mentioned a table that would remount slowly on refresh to the detriment of UX
    * "its important to save people's time and effort. a ui library that everyone contributes to and shares"
        * it will be hard to share across angular and react. this isnt done on open source libs for a reason, its not actually workable. you risk non-adoption or non-maintenance. material defines its design patterns, but implementation is done separately for react/angular.
        * you could share just figma designs, not necessarily the components themselves
    * "angular capability is there but not WC, ability to support is limited"
        * tarek also asked why there isnt a push to move everything to angular. in fact as i understand it there is. all net new stuff for DFX is in angular.
        * "we're trying to future-proof as well." | "if they ask we're react but want to use your design system, we don't want to have to say that no cause angular. we want to be able to say yes" | "i think we've had some request before like this" (sounds like the likelihood is not super high)
            * tarek: "also the other portfolio companies that snap-on owns, correct?"
            * my initial questions (basically asking: do we even need this?) 
                * do they have the same UI/brand language? 
                    * otherwise we'll have to support theming, which is a big deal thus a big gamble (what if we dont need)
                * do the teams actually collaborate? they will have to not only adopt it but maintain it together, adding what they need to the repo while taking care not to cause issues or drift towards bad practice
            * "react is becoming a bigger player, we might want to switch to react at some point, we dont want to limit ourselves, i want to be prepared"
            * brenda: "do you know for sure that you'll have to support react?"
            * how much are we willing to invest to mitigate these risks.
                * brenda: angular will go much faster. lit will be more work at all levels: development, integration, etc.
                * brenda: "i wonder if its worth the effort" 
                    * i would frame it as: "i wonder if its worth the risk (to non-adoption or non-maintenance)"
                * jihuyn was interested: "so you think it will go much faster if we do it in angular?"
                    * brenda answers in the affirmative but in my opinion not authoritatively enough. 
                        * "well, in my opinion" | "a lot of things to work around"
                    * * we need to bring our experience to bear by asking other people that were involved in WC projects to get their takes as well.
                        * brenda did an internal poll about what the painpoints are. but she didnt have the results handy at the time, we need these.
                            * "accessibility was a big one"
                * jihuyn: we actually have felt the pain points 
                    * the library right now doesnt integrate properly, if i remember correctly, because they are not able to pass inputs/outputs up and down. this is something we had to work around with significant effort. "we were hoping that you would actually help us lift that pain so that we could actually move forward"
                        * using the solutions we found, do you have to expose each input/output explicitly?
                * brenda: form controls. you have to wrap each piece in a wrapper so it can talk to the external form.
                    * * jihuyn: "jacob and i were actfually strickly talking about this right now, how to handle form controls" | "we tried it already, its not working" so they are thinking of making their own `su-inputs` | "we're trying stuff out trying to look for other means to do it" | "definitely has some problem there" 
                * you will have to solve the integration problems with every new consumer: vue, react. you need to figure out the wrapper adapters that we had to for angular, and this requires a pretty senior experienced developer who understands how this stuff works. you need to understand zonejs and stuff.
            * j: "another thing is that if we did WC we wouldnt have to not have to revamp the whole older UI"
                * j: "although steven doesnt think that's gonna happen" (doesn't think we will be able to use the older UI)
                    * j: "but its because he doesnt think its possible at the moment"
                * what older UI, the existing SocketUI library that is not being used? something else?
      * b: if we need to integrate as WC into react, we can do it in bigger chunks, at the molecule level.
we can use "angular elements" to achieve this, we've done it before and it works well. the integration surface is much more manageable here. 
a button can be replicated in react more easily and to better result (dev time/debug/maintain/etc) than importing it as WC
the molecule would be built in a standalone manner within the DS, in a different area. this is not an anti-pattern, and would in fact provide great example use cases to follow.
molecule: has a specific contextual function, not generic, while not being a complete UI solution that could be considered independent and complete for a given scope.
j: really considers it "hm, but what would be the actual benefit then?" 23:40 (seems to get a bit lost here , i think it could be made more clear, returns to basics)
"i think the goal was to have a design system that is easy to ____ (unintelligible, probably like "use". * this is important cause we're trying to make it easier to use and maintain). not just a pattern but also the UI library as well."
b used the term "micro front-end" and then tried to clarify that you would also have a DS, MFE only for the react apps. idk if the term is used to mean what she means, an MFE makes its own network requests and stuff, here we're talking about pure UIs (could be stateless).
* j: "that would be nice. that's actually interesting" | "we actually have done something similar. payment portal widget written in stencil that is doing exactly that, opens up a dialogue and does all its stuff there. so yea, that could be a definite route" | "i'm only concerned about complexity here, idk maybe you're right, you may identify good candidates for this"
* i think he is indeed thinking of a legit MFE, this widget does all its own stuff, you just mount it on a dialogue and let it do its thing. the complexity concern i think is based on the same misunderstaning, because the complexity he's talking about is building functionality as independent MFEs (difficult to draw those separating lines) that are stateful and will probably need to talk to each other (event emitter layer or something, extra work to pass around events). these would only be applicable to MFEs, a stateless or minimally stateful molecule lets you write all the stateful and data-driven functionality in the base app. also integrating is no problem, no need to mount in a modal or some other separate area.
any such "chunk"/molecule could be actually shared across different apps, if we identify a shared piece
j: "yea, that will definitely work too" 
j: "so the angular elements thing works for angular too?" 26:03
b tried to explain but i think he didnt understand that you put the "chunk"/molecule together as an angular component, and then export it ALSO as a WC using angular elements. this way you get the best of both worlds, cause in an angular environment you get full devex (debug, reading source code, ng dev contributions, etc)
j: "tried importing ng elements into ng and zonejs was failing"
b: "yea, we did that and that was a huge issue. i dont recommend nesting with ng components. i'm only talking about big chunks or MFEs that do a bunch of functionality, not DS."
this sounds like maybe she is indeed talking about actual MFES
other factors that make it untenable to export atomic ng elements:
advanced/subtle considerations that multiply dramatically in impact when importing atoms: are we loading angular code for every WC? are we running an angular engine and zone instance for every WC?
* confirm: can we not expose as angular DS + chunks, and then ng element chunks (chunks as both) ?
* j: online scheduler might be a good candidate for MFE. mounted onto client website in an iframe. 
this is not a problem at all with our solution (ng elements for react)
but if we have use cases for actual MFEs like this, then I would say we make a separate repo for them so we don't pollute DS (+ chunks) with api services and data logic
b: "so angular is not off the table? (not at all) ok that makes me happy"
a bit too opinionated here, sounds biased. also in the beginning she said "i'm disappointed" when it sounded like he wanted WC
tarek: "dont worry we're not deciding this now"
then b backs off: "we'll discuss it and maybe it makes sense maybe it doesnt. we'll give you a list of tradeoffs"
j: "so WC atoms would be ideal, but angular atoms with WC MFEs via ng elements, i'm ok with that." | "if you can convince me, i'm open for anything"
* b: "so my recommendation would be the DS and atoms in angular, and anything to share with legacy app or react, an MFE with ng elements." | 
* j: "its good that you're bringing up this topic, cause it has been on my mind a lot."
"although i've been going this route -- and i have to tell people what to do, so i have to be definite about my decision -- i have thoughts in the back of my mind." | "honestly, the fight is not settled in my mind"
"if we did it in angular, it will be easier. wouldnt have to go through these crazy hurdles."
b: "what's more important: getting it done faster? best support for the new angular apps? legacy apps? future possibilities in react?"
we need to expand this. i don't think that we should go full WC DS even if legacy & future are priorities. adoption, new workflows (how/who builds new stuff, maintains, adopts), dev capability, etc are still better our way.
j: "i'm more worried about the future apps" 
j: "if we build these components with angular, then there's no way to move away from angular, right?"
i guess so, but you could say the same for Lit. you cant move away from it after. being stuck with Lit is worse.
b didn't have a good answer: "idk, coming down the pikes there's always something new, and you can't predict what you'll want to use in 3 years"
i think this is a good argument to use ng over Lit. lit is much more likely to lose support, be overtaken, and be old tech in 3 years. happened to polymer (in fact polymer is lit's predecessor). WC framework is not established yet.
brenda's tradeoffs doc: in fact, lit moves slowly, they promise things that they dont deliver and a lot of their stuff is in labs (promised)
lit has competitors, like stencil, which we've had better (and more) experience with
b: lit itself is likely to have major updates and need migration, they are working on new stuff in lit labs. 31:00
i would add 
there will be a performance impact, having to wrap every piece before bringing to angular. 
brenda: "there's not much overhead there in terms of performance, but there is for devex"
it will be difficult to maintain because they will be written in a different way, different framework. devs will be hesitant, not follow best practices, or run into difficulties caused by the integration (a silly mistake like forgetting to wrap a new form control could manifest in very difficult bugs for a dev that has not been there before (zonejs stuff)
it will make the application much more difficult to debug for your developers 



## 23/08/02 \
 \
**% #w_workstreams (deprecated)**


## **<span style="text-decoration:underline;">**!!CLEAN THIS UP!!**</span>**


## ***for each: consider if/how to track progress \
 \
***#w_organize



* update todos and workstreams


## #w_reports / **performance-reviews**



* write my feedbacks
* create file for each person -> figure out who to connect with and what projects to get feedback
* **[p90] **set up 1:1s (#w_performance-reviews)
* * reach out to new reports (mamadou + deirdre)
    * deirdre’s reports: william henlin, vasu
    * who is no longer my report? (jason, natalyia)
    * restructuring doc:[ https://docs.google.com/document/d/1vL6_LznRH9vVvywdTB4oH6HaT33keY2lNhM9tCKqO0c/edit](https://docs.google.com/document/d/1vL6_LznRH9vVvywdTB4oH6HaT33keY2lNhM9tCKqO0c/edit) 


## #w_free-agents 



* #w_svg-clip 


## #w_consulting_workshop (#w_tara, #w_mike-phung)



* ** collect and organize all materials (recordings, assignments)
* #wt** **write about tara’s call with jeffrey, send to tara
    * write commentary about lectures and assignments
* #w_habits (before workshop) do assignment


## #wt #w_important **catch up!**


## **operations and intelligence ***(overlap between projects, staffing, operational, consulting, case studies)*



* ** collect and organize all recordings


## **case studies ***(overlap between projects, staffing, operational, consulting, case studies)*



* init case studies (after done collecting, reviewing and organizing) 


## #w_operational *(overlap between projects, staffing, operational, consulting, case studies)*



* #w_habit explore people’s calendars
* create 
* (tech &lt;-> non-tech) recurring syncs and document maintenance about tech &lt;-> not-tech (sales, strategy, etc)
* *** habit: look at people’s calendars to learn of meetings and efforts
* #w_habit #w_important prep for tech regroup
* #w_capability 
    * start/discuss #w_skills-assessment (nancy, arseny)
    * **(later)** discuss #w_performance-reviews 
* * #wt reach out to new operations person
* continue building out notion “internal”
    * purposes
        * website
        * performance reviews
        * cms study/workshops &lt;— this is a project
        * capability and growth tracking
        * projects / staffing / consulting / o&i 
        * etc..
    * templates for new projects / contributors / etc
    * allow individuals edit access to specific areas, while keeping it read only otherwise
    * project database views should not be editable
    * contributors should see their aggregated tasks
    * (later) some dashboard views to showcase status and progress?


## ** #w_projects & #w_staffing (#w_awareness , #w_mike-phung)



* #wt study 
    * staffing scratchpad:**[ https://docs.google.com/spreadsheets/d/1Sk4f9sdej7662lZ9i1AFgNDZGwSm7RZ8Kim0MaDZRsQ/edit#gid=220787023](https://docs.google.com/spreadsheets/d/1Sk4f9sdej7662lZ9i1AFgNDZGwSm7RZ8Kim0MaDZRsQ/edit#gid=220787023) **
* #w_habits #w_important study the staffing scratchpad before **every thursday**
* attend & prep for every **staffing / sosos** meet **every thursday **(staffing scratchpad)
* #wt learn about all major projects 
* #w_tara ask about alexey’s documentation of our sales approach (jason santos mentioned)
* * collect and organize existing information
    * notion has some docs on projects
    * also check cmap and staffing scratch
* projects
    * jet blue (titus, platform)
    * rbc (joaquim, rafae, scott mingie)


## #w_cms-workshops (#w_education, #w_nancy, #w_natalyia, #w_scott)



* collect, review, organize all cms materials. figure out what we need and plan how to get it (questions, etc)
* #w_asap meet with #w_nancy to discuss (and prepare for it)
* #w_asap collect, study and organize cms materials (blog, book, case studies)
    * then: kt and collab meets with scott, natalyia 
* study
    * [https://github.com/rangle/headless-workshop](https://github.com/rangle/headless-workshop)  
    * [https://github.com/rangle/cms-components](https://github.com/rangle/cms-components) 
    * [https://rangle.io/blog/headless-cms-101](https://rangle.io/blog/headless-cms-101) 
    * *[ https://tbw.rangle.io/headless-cms-playbook/introduction/what-is-a-headless-cms](https://tbw.rangle.io/headless-cms-playbook/introduction/what-is-a-headless-cms) 


## #w_capability 



* #todo check out arseny’s curriculum (#w_mamadou sent on slack)
* #w_skills-assessment (#w_nancy, #w_arseny, #w_ditmar, #w_bertrand) 
    * discuss with: #w_arseny, #w_bodhan, #w_nancy, #w_bertrand 
    * #asap write questions for devs, questions for leaders
        * get feedback from people: nancy, bert, jason santos, etc..
    * also just compile info about what we’re been using on project, challenges, and opportunities


## #w_performance-reviews 



* #w_asap** [p70] **schedule 1:1s (except #w_vaibhab) and tell them to ask for feedback (#w_reports)
    * ask leah if she’ll leave a decent review for him (#_vaibhab)
* ask mike costanzo if he’ll give #_vaibhab a decent review


## #w_radius (#w_jason-santos)



* #important get KT from nathan (and others)
* read radius gitbook / materials


## #w_people 



* #w_nancy 


## #w_asap** **prep and meet with #w_nancy call to discuss:



    * #w_cms-workshops
    * #w_skills-assessment 
* #w_jason-santos   
* #w_titus 
* #w_ditmar 
    * todo: have meet to talk about willian’s leaving and what i can do support transition
* #w_adrienne 


## #w_content



* *** #w_module-bundling (#w_leah)
    * finish script 
    * **record footage for videos **
    * work with thomas to edit
    * release and announce
* content: debugging prod issue cpu leak / apollo memory leak


## #w_fast-track  



* #wt **onboard website**


## 23/08/02 \
 \
**% #work (deprecated)**



* ***important***
    * ***performance: ***
        * ***write report / strategy recommendation doc***
        * ***gather intel & memories on reports***
* *dormant worksteams*
    * *intelligence*
    * *o&i*
    * *consulting*
* *future task: history/badges pages on notion *
    * *(i like it, but not yet too early, in a couple months maybe)*
    * *for now start tracking in people pages*
* ***** momentive computer***
* *#work: 2023/07/06 *
* *#w_workstreams: 2023/06/29*


## **<span style="text-decoration:underline;">general</span>**



* create tasks for myself for everything in notion
    * everything can have its own linked tasks. projects (client & internal) will have tasks as well
* (daily) update tasks, workstreams etc. stuff from notes
* *** (tmrw) send momentive computer back!
* read:[ https://www.linkedin.com/posts/mike-costanzo_building-blazing-fast-websites-with-nextjs-activity-7080742007874191360-NTxv?utm_source=share&utm_medium=member_ios](https://www.linkedin.com/posts/mike-costanzo_building-blazing-fast-websites-with-nextjs-activity-7080742007874191360-NTxv?utm_source=share&utm_medium=member_ios)


## **<span style="text-decoration:underline;">workstreams</span>**



* #w_self 
    * * #wtr (* daily @ night) update #work (new tasks)
    * * #wtr (* daily @ night) track energy/focus during workday 
        * also variables like amount of sleep and stress factors
        * like journal but concise
* #w_free-agents 
    * #wtr (daily @ morn) update list (staffing scratchpad) 
    * #wtr (daily) reach out to fas without project / not contributing
    * % #wt (jul 26) figure out what else to talk about to fill time
        * advertise people to pitch projecs
        * advertise automation project(s)
        * advertise website seo project + progress (shoutout to brenda)


## 	⁃		⁃	? present jb-platform (needs something to show)



* #w_help
    * #wtr (daily) check / resolve
    * #wtr (2 days) encourage someone to post
* #w_reports 
    * * #wtr (weekly) 1:1s
    * * #wt (* july) write personal feedbacks
        * natalyia (helped karen at midnight)
        * tarek
        * thomas
        * ...
* #w_jb-platform 
* #wt invite self to platform meets (check their calendars)
    * * #wt github actions + kube + azure + node (show sumit & steph)
* #w_svg-clip 
    * % * #wt thomas blog feedback, karen problem
        * => describe problem in document (karen could help)
            * ? refactor code with karen (and some other person could help)
    * % #wt help geethu
* #w_capability 
    * jason offet + arseny initiative (jason could do cms workshops next)
    * #w_cms-workshops (#w_education, #w_nancy, #w_natalyia, #w_scott)
        * collect, review, organize all cms materials. figure out what we need and plan how to get it (questions, etc)
        * #w_asap meet with #w_nancy to discuss (and prepare for it)
        * #w_asap collect, study and organize cms materials (blog, book, case studies)
            * then: kt and collab meets with scott, natalyia 
        * study
            * [https://github.com/rangle/headless-workshop](https://github.com/rangle/headless-workshop)  
            * [https://github.com/rangle/cms-components](https://github.com/rangle/cms-components) 
            * [https://rangle.io/blog/headless-cms-101](https://rangle.io/blog/headless-cms-101) 
        * *[ https://tbw.rangle.io/headless-cms-playbook/introduction/what-is-a-headless-cms](https://tbw.rangle.io/headless-cms-playbook/introduction/what-is-a-headless-cms) 
* #w_programs
    * 
* #w_publications
    * module bundlers video


## **<span style="text-decoration:underline;">value-adds</span>** (every type of notion page can link to related tasks)



* **r&d project: svg clips**
    * ** review demo repo and add labels, comments and questions in markup, as well as containers to resize, etc. basically shape it into a structured document
* **r&d project: bundle optimizations**
    * !! ** (jul 4) write scripts (long and short), prep demos, and record videos
* **free agents**
    * recurring tasks
* **document project proposals (encourage commentary / collaboration)**
    * what capabilities do we need (minimum + opportunities)
    * potential people to staff
    * who has context
    * opportunities & strategy discussion
        * link to these in consulting workshop
* **document active/past projects (encourage commentary / collaboration)**
    * * start with momentive, since we have access to channels, and we know everyone in the project
        * * surveymonkey_program_account channel has great information
        * case studies: 
            * (tag: technical) mike's performance debugging (create tasks for r&d)
            * (tag: consulting) mike's "create" proposal, and there have to be other proposals from before. these proposals also go in project materials, outside of case study.
    * other projects:
        * jb platform (titus + tara) 
            * [https://rangle.slack.com/archives/C024N2TPN/p1687379468408009](https://rangle.slack.com/archives/C024N2TPN/p1687379468408009) 
    * tasks: 
        * apparently we couldnt handle some of the platform work so we let JB internal team do it.  titus knows about it, he was the one that called it out. was it a cabability shortfall?
        * connect with naim yagoub once we have something, he'll probably be supportive
    * who has context (including past devs and what they worked on)
    * what have we learned about the company (technical stuff, people)
    * case studies of what worked, what didnt work 
        * link to these in consulting workshop
    * opportunities & strategy discussion
        * link to these in consulting workshop
    * gather materials (prioritize most recent)
        * existing in notion
        * in slack conversations (ask to be added to channels)
        * * otter transcripts (SOSOS) 
        * * sosos channel
    * recurring tasks: update after weekly SOSOS
* **consulting workshop: collect/organize materials**
* **tools/resources: centralize all access with albert and create index document.**
    * decision backed up by jason santos
    * announce the move
    * create document with all the tools/resources and their current status
        * obviously we need to gather list items that we dont know about
* **consulting workshop: write content (encourage commentary / collaboration)**
    * tara's conversation video
    * link to project case studies, questions, and opportunities 
        * * start with momentive, since we have access to channels, and we know everyone in the project
* **o&i: collect/organize materials**
    * o & i recordings
    * town hall recordings (jun 29 nick gave a relevant presentation)
    * * capabilities report + technology strategy discussion (nick encouraged)
* **capability: system**
    * check out survey:[ https://rangle.slack.com/archives/D53JHGJKE/p1687184564244349](https://rangle.slack.com/archives/D53JHGJKE/p1687184564244349) 
    * * domain starter: arseny's front-end doc:[ https://www.notion.so/rangle/Frontend-fundamentals-4f764546ea184a11926d957d898914f6](https://www.notion.so/rangle/Frontend-fundamentals-4f764546ea184a11926d957d898914f6)  
    * each domain
        * overview / highlights (highlights link to whatever)
        * current capability (how good are we at this generally)
        * how valuable is it to us
            * overview
            * posts filtered by relevancy=domain-value
        * status: build / maintain / release
            * overview just shows the status tag and links to status page, containing rest
            * context description (reasoning for status)
            * comments / updates / discussion
            * posts filtered by relevancy=domain-status
        * learning materials
            * blog posts
            * external materials
        * people that know stuff (did related project work, did related r&d)
        * projects
            * link to active/past projects
        * case studies [db] (shared with projects, both client and r&d, domain elements)
        * elements (tools & methods) [db] 
            * link to radar entries
            * link to canvas entries
        * canvas entries filtered by current domain
        * posts (generic information, guides, discussions, news, etc) [db: filter by domain]
        * events (calendar) [db]
        * publications (media, open-source) [db: r&d filtering only publications]
        * r&d [db: r&d filtering not publications]
        * tasks (active and pending r&d or info gathering whatever)
        * questions [db: filter by domain]
    * other domains
        * * headless cms
            * [https://rangle.slack.com/archives/C024N2TPN/p1687455490729919?thread_ts=1685719588.997409&cid=C024N2TPN](https://rangle.slack.com/archives/C024N2TPN/p1687455490729919?thread_ts=1685719588.997409&cid=C024N2TPN) 
        * ? platform
        * ? devops
        * SEO (pagespeed insights)
            * ask leah 
    * recurring tasks: review and update status/capability/value
* **capability: report + discussions**
    * do
        * interviews
        * survey
    * nick encouraged stuff like this for O&I
* **performance reviews: document process**
    * stuff that jason provided
        * levels definitions (self-assessment doc) (jason said it's accurate)
            * [https://docs.google.com/spreadsheets/d/1IM80njXunokCdJ9nI4cv2ool8SP0nbQBzznJVvRiL1M/edit#gid=1019938858](https://docs.google.com/spreadsheets/d/1IM80njXunokCdJ9nI4cv2ool8SP0nbQBzznJVvRiL1M/edit#gid=1019938858)
        * competencies (jason said might be a bit old or not fully accurate or complete)
            * [https://www.notion.so/rangle/Technology-ed06736f35884915b7202936f8abbec9](https://www.notion.so/rangle/Technology-ed06736f35884915b7202936f8abbec9) 
        * career framework
            * [https://docs.google.com/presentation/d/1NKfqTQCbjMOC0xksmgqsS4iK-PSnFQUGoRj-4oUtEH0/edit#slide=id.g7a475307b1_0_12](https://docs.google.com/presentation/d/1NKfqTQCbjMOC0xksmgqsS4iK-PSnFQUGoRj-4oUtEH0/edit#slide=id.g7a475307b1_0_12)
    * notes regarding process
        * don't share performance review details down or horizontally
* **performance reviews: document individual persons**
    * collect stuff: 
        * existing record: culture amp, talent snapshot
        * projects, r&d
        * notes
    * schedule 1-on-1s
        * ask them to send me a list of stuff they did (description/challenges, people they worked with, maybe slack channels, maybe PRs we can look at)
    * people
        * * thomas feedback: really great leadership and technical work on svg-clips
            * also really helped me when i was struggling to onboard onto momentive
            * reached out for help often on momentive with well-defined problems, which is great
            * expanded code following the patterns set (routes) without any such instructions, and also coached the whole team to do the same
            * reached out to nathan about it, as well as the fast-track people, inspired and supported them. they were able to contribute a lot of value because of it
            * he is an extremely pleasant guy to work with. always has camera on, is a proactive participant in slack channels, is driven/passionate and humble, and impressed everyone with his amazing lip sync skills.
            * did a heads down deep dive until he felt comfortable with the complex subject matter and then opened up and led the team with his knowledge
    * tasks: gather feedback and info
    * write my first-hand experience feedback
        * from the master copy on notion we produce culture-amp feedback by redacting
        * considerations
            * goal orientation and consistency (do they set goals and follow through?)
    * generic notes [inline private db]
    * projects: what they did, their experience, feedback given
    * r&d 
    * recurring tasks: 1 on 1, gather feedback, update with recent history
* **radar / canvas**
    * recurring tasks


## 23/06/12 \



## **#wt **



* **o and i #w_oni**
    * ** attend tmrw:[ https://docs.google.com/document/d/15GnnbivEDBBVIQJx0f1jRMZJkHLp3iiC6JCtyt90mgM/edit#heading=h.7ng1x9a0nte4](https://docs.google.com/document/d/15GnnbivEDBBVIQJx0f1jRMZJkHLp3iiC6JCtyt90mgM/edit#heading=h.7ng1x9a0nte4) 
* **free agents #w_free-agents **
    * create tickets: 
        * open research: ai, appleview, etc (capability meets will inform)
        * my tickets: content (bug 
    * who is a new free agent?
    * check in: tarek and vyk
    * * check in: thomas and jason svg-clips
        * prep: list of points to understand / demonstrate / document
* **website #w_website **
    * * radius ticket (michael asked on friday)
        * prep: gather what we can learn from threads
        * reach out to yena, filip, naim yagoub, ditmar
    * standup: 
        * radius project, i’m gathering reqs
        * albert request (new ticket)
            * [https://rangle.slack.com/archives/C05BR15NFUM/p1686321563805389](https://rangle.slack.com/archives/C05BR15NFUM/p1686321563805389) 
        * deploy all prs and clear board for radius stuff
    * organize roadmap / backlog (after radius meet)
        * tech debt (context switching, data migrations)
        * measuring velocity (estimations)
    * ** (before standup) deployment testing/process doc
* **fast-track #w_fast-track **
    * (before tuesday meet) get website admin
* **performance reviews #w_performance-reviews **
    * * feedback: vaib (ask leah about that comms thing)
    * write other feedback from me (culture amp for )
        * tarek failed me at reproducing michael’s bug
        * vyk doesn’t really 
    * * schedule 1:1s (they should ask for written feedback)
    * reach out to team members of reports 
        * learn about projects, get feedback on reports. then we write the feedback ourselves
* **capability #w_capability **
    * write survey drafts and prep for meets (list of people and questions)
    * cms upskill
* **content #w_content **
    * * write script for module bundling
* **consulting workshop #w_consulting_workshop **
    * ** feedback on last week’s meet (watch rec)
    * * write about tara’s call with jeffery and post
    * jb case study
        * find people to interview
        * start writing docs
* **projects #w_projects / staffing #w_staffing **
    * list / study staffing scratchpad and active projects 
    * prep for staffing and sosos
* **reach out / schedule meets**
    * * yena: (radius gitbook, cms upskilling) 
        * prep: collect / study cms material
    * * mike costanzo (website progress/admin, jb case study?, capability)
        * prep: what’s our current velocity on website
        * prep: what projects is he on?
    * nathan (1:1, radius kt)
    * titus (jb case study, capability)
    * jas (jb case study, capability)
    * adrienne
    * alexey (capability, projects)
    * ditmar (radius gitbook project, capability, projects)
* *** (wednesday) office: bertrand kt**


## **free agents**



* cloudformation
    * #todo 
* svg (jason & thomas)
    * thomas G: makes list to figure out
        * jason offet: “can we parse the path”
    * #todo follow up meet:
        * requirements/goals list to understand/demonstrate/document and limitations/preconditions to consider as rules
            * svg should have an id on clippath to use, 
        * what is our approach?


## **website-standup**



* #todo follow up with vaib, any issues wrapping up PRs?
* #todo megamenu approve
* #todo radius -> meet for backlog
    * gather historical


## 	•		⁃	tech debt tickets


## 23/05/19 \
 \
**23/05/19 - friday**


## **w_today**



* website onboard
    * understand merge/deploy process (natalyia)
        * [before 1] check out sanity and vercel portals
        * do we have pr builds (staging environments) ?
        * where is the “prod” storybook? link + where is it hosted
    * sanity endpoints for local dev,
        * if running next app, how do we tell it to use local sanity
        * does local sanity use prod data? is there an option?
    * changing name or removing a property, what happens, do we lose the data
    * am i supposed to have access to this?[ https://rangleio-sanity-hpdg9fzfs-rangleionext.vercel.app/](https://rangleio-sanity-hpdg9fzfs-rangleionext.vercel.app/) 
    * we have ‘picture’ schema type, but docs say ‘image’


## #w_read willian's linkedin (cms)


## #wt #asap svg clips finish study and do a patch pr (create examples for content as byproduct)


## #w_mega-menu 



* [later] pictures should be all or nothing (it might look broken if you put pictures on some but not others within the same section)
    * “image: if yes require all for submenu”
* [todo] handle aspect ratios, provide ideal aspect ratio in description
* [todo] light refactor of styled nav menu item: rename “submenuItems” to “submenus”


## #w_main-hero 



* background question (natalyia)
* layout question
* some refactor?
* make sure all AC’s are met
* pr description
* [story] video on hero svg cutouts
* [story] stats grid (sananda designed it on figma)
    * you put a number and an image, and we cut out the number shape
* [spike] self-hosted video
    * we want to do a component like CaseStudy card but with video support


## #read ai:[ https://www.linkedin.com/posts/zainkahn_the-death-of-google-and-search-is-near-activity-7064572663620415489-9NwM?utm_source=share&utm_medium=member_ios](https://www.linkedin.com/posts/zainkahn_the-death-of-google-and-search-is-near-activity-7064572663620415489-9NwM?utm_source=share&utm_medium=member_ios)


## #w_website


## #w_copypasta 



* cloudinary: User: bertrand@rangle.io Pass: x8LbqKMuDBP*


## #w_website-arch 



* general responsiveness strategy (css hiding for SSR)
* ds types match sanity schema, but one is not derived from the other, we need to always ensure that they match


## **w_standup**



* [prep] create pr, delete other prs/branches
* we have 2 stories pretty much ready to fly (for mike)
    * main-hero: vaib worked a lot on it on it, and yena helped out a ton.
        * great onboarding story: not only in terms of how to achieve these really cool graphics, general responsiveness, but yena’s contributions (which are  are exemplary, great kt around sanity, theming, styling and wiring across packages)
    * mega-menu: leah has kept this story moving on her own, i don’t have as much context into this one, but it’s looking solid and if not done, pretty close to done. 
* today collab to merge/deploy main-hero, and hopefully mega-menu
    * and do thorough QA, make sure we’re meeting all AC
        * live pr reviews, record for future reference
    * make any required changes 
    * document all arch decisions and outstanding questions
    * understand, document, and kt everything relating to deploy process and monitoring
* clean up board, bring back some process (sprints, planning, other tools on notion)
    * tuesday we groom, plan. & wednesday will be first day of sprint
    * no ticket for megamenu


## **w_follow-up**



* so, i’m very confident and optimistic
* but we had a bit of a rocky start
    * part of the impetus for the structured approach i was talking about. 
    * onboarding this team has defnitely been a challenge
    * although i feel like we’ve managed well enough so far, and i feel like i am in control.
* the nature problems we had came from left field
    * there’s a complex set of factors at play
    * i’ve working to untangle them and keep the team on th


## #w_vaib  



* important conversation with mike fri may 19th. 
* even if we saw progress and it looked like with the right coaching he would improve, the well is so poisoned that he has become toxic himself. what happened with nancy wasn’t right, but it’s still an indicator of the effect that he has on other people. everyone seems to share the same opinion about him, and keeping him on, even if it was progressing, would likely have a detrimental effect on our teams.
    * the people that create rangle’s culture of excellence and innovation would be demoralized, because why should i work so hard if he’s useless
    * also sucks up resources: he’ll need extra support from his SAs, TDs and peers
    * we could be using this slot on payroll for someone else
    * but we have to consider the fact that the arguments made here may also apply to a wider subset of our talent. in vaibhab’s case there’s added factor of existing prejudice from past experience puts the nail in the coffin.
* he has reacted to the coaching with great dedication and hard work. his communication is much better. however, he’s just not very good at the job itself, and that’s going to be very hard to improve. he had the deck stacked against him, some may have been rooting for him to fail, but still, he had my support and encouragement, high morale, put in the work, but didn’t produce the results we need. it’s an uncomfortable and tragic reality.
* #wt send vaib report to willian


## #w_read[ https://rangle.io/our-work/endy-headless-ecommerce](https://rangle.io/our-work/endy-headless-ecommerce)<span style="text-decoration:underline;"> </span>


## <span style="text-decoration:underline;">#w_read[ https://rangle.io/blog/build-a-headless-e-commerce-site-with-sanity-and-shopify](https://rangle.io/blog/build-a-headless-e-commerce-site-with-sanity-and-shopify)</span> 


## #baby 



* failed to help with lll comps, taxes, budgeting/expense tracking, getting a drivers license


## 23/05/10 \
 \
**23/05/10 - wednesday**



* todo 
    * p mason tux
    * p finance / org
        * use apple notes 
            * for wishlist, org, music, whatever
            * use tags, smart folders
                * do tags mean we should do shorter notes?
            * get good at notes:[ https://support.apple.com/en-ca/guide/notes/apd46c25187e/mac](https://support.apple.com/en-ca/guide/notes/apd46c25187e/mac)  
            * clean up existing tags
    * * p mimi letter
    * * p [today] tell people i have a thing on tuesday
        * mimi / rob / kody / armin / licky
    * p msgs
        * reid: album for concentration
    * * p [today] download all bank statements from app
    * * p [today] pharmacy: get more pristiq, speed
    * * p ram clinic appt
    * p sleep clinic call
        * im too busy to go for another study, just give me same prescription for cpap
    * * p house (mimi?)
        * take out trash
        * alien litter
        * dishes
    * * w video script
    * * w [early] read leah article
    * * w [early] vaibhav svg
    * * w [early] van service call
    * w pending schedule
        * nathan 1:1
    * * w msgs
        * leah 
            * #w_content i read the article, lets leave it for a bit until i finish the video, so we can make a splash? 
        * jordan 
            * got him three days
    * w [scheduled] meets
        * rafae
            * ask for participation in arch
            * delays due to politics not technical
        * joaquim
            * video stuff
    * w read mike’s doc: #w_study[ https://docs.google.com/document/d/1YCcHkqsDRz5qw5Wm5XssYz2Pzs-rNlOefYBJLIHKJHY/edit#heading=h.f1o10sqpwkzo](https://docs.google.com/document/d/1YCcHkqsDRz5qw5Wm5XssYz2Pzs-rNlOefYBJLIHKJHY/edit#heading=h.f1o10sqpwkzo) 
    * ** w [soon] write down clip path story for #w_content 
* reorg questions for willian
    * deidre has reports
        * she’s an SA, didn’t know could have reports
        * did she switch to Staff Dev? document does not state thus
* reports changes
    * + mamadou
    * + deidre
    * - thomas schemmer
    * - jason offet


## #w_content 



* great content: clip path thing
    * same as bundle thing: article + short
* consider also putting out a longer video 
    * alternative to an article
    * we might as well film more
        * we dont need to do so much editing on that one
        * we’ll surely have more to say (flesh out / expand)


## #w_content #w_memo 


## connect with jordan, think together of a cool angular thing we can do in our 1 week. connect with jimmy and robyn or whoever from Jet Blue to find out what other tools or problems we should consider.


## #w_thoughts kind of obvious, but if a free agent knows something about their upcoming project, we should seek to make content/contributions using those tools


## #memo when we get paid, buy the ableton vsts


## #w_content using our website as an example for things has an extra marketing benefit. 



* #w_svg-clip  for the svg clip-paths episode/installment, we link to our site so they can see the finished product, and they will likely do so. this is going to be very well received by all of rangle’s leadership. **perfect**
* for the bundle analysis one, at least we get to show the website in the demo, product placement and builds brand by putting us in a cool, highly technical demonstration. **good**


## #w_svg-clip



* facts
* plan 
    * work with vaibhab like this: using my branch, ask him for the next thing to figure out and then he should produce it such that it answers the question, essentially what we’re doing right now but with him doing the googling and reading and then trying to explain to me or present me with clean and minimal working examples that i can understand.
* materials
    * ** our initial trail has been vindicated through multiple confirmations.
        * our first article:[ https://davesmyth.com/clip-path-scaling](https://davesmyth.com/clip-path-scaling) 
            * talks about** clipPathUnits="objectBoundingBox" **and how all the values need to be between 0 and 1
        * another article on the same:[ https://www.smashingmagazine.com/2015/05/creating-responsive-shapes-with-clip-path/](https://www.smashingmagazine.com/2015/05/creating-responsive-shapes-with-clip-path/)  
    * ***[ https://stackoverflow.com/questions/17388689/svg-clippath-and-transformations](https://stackoverflow.com/questions/17388689/svg-clippath-and-transformations) 
    * *[ https://stackoverflow.com/questions/57543066/svg-clippath-clipped-area-offset-and-size-problem](https://stackoverflow.com/questions/57543066/svg-clippath-clipped-area-offset-and-size-problem) 
        * you can load images within svg. they have an &lt;image/> tag
    * **!! what is VIEWBOX** (i don’t understand this yet, seems **critical**):[ https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox) 
        * what is a viewport (note difference in viewbox doc above)
            * [https://developer.mozilla.org/en-US/docs/Glossary/Viewport](https://developer.mozilla.org/en-US/docs/Glossary/Viewport) 
        * this again mentions viewbox as a solution to similar issues
            * **[ https://stackoverflow.com/questions/34064917/how-to-resize-svg-clip-path](https://stackoverflow.com/questions/34064917/how-to-resize-svg-clip-path) 
    * *** this is very similar to what i was doing. (**in fact identical**)
        * [https://stackoverflow.com/questions/60491855/how-to-resize-the-clippath-area-of-svg](https://stackoverflow.com/questions/60491855/how-to-resize-the-clippath-area-of-svg) 
            * **!! what is MASK**
                * *[ https://stackoverflow.com/questions/62409895/css-property-mask-is-not-working-properly-for-svg](https://stackoverflow.com/questions/62409895/css-property-mask-is-not-working-properly-for-svg) 
    * [https://stackoverflow.com/questions/48152326/how-to-resize-svg-clip-path-to-be-same-size-as-image](https://stackoverflow.com/questions/48152326/how-to-resize-svg-clip-path-to-be-same-size-as-image) 
        * * clipPathUnits="objectBoundingBox" is the way we *automatically *fit the size of an image. this would be for continuous responsiveness, so i dont think we need to do this.
        * confirms what the first article said: 
            * “For use this mode for clip paths, you need to set clipPathUnits="objectBoundingBox". Then you just need to scale all your polygon coordinate values so that the are between 0 and 1.”
            * another:[ https://stackoverflow.com/questions/69492283/how-to-scale-clip-path-path](https://stackoverflow.com/questions/69492283/how-to-scale-clip-path-path) 
            * another:[ https://stackoverflow.com/questions/25901569/svg-scaling-and-clip-path](https://stackoverflow.com/questions/25901569/svg-scaling-and-clip-path) 
                * **? the last response is interesting, not sure how to interpret**: “The clipPath is defined in absolute units (pixels). If it was being applied to something in the SVG, it would get scaled. But the HTML side of things doesn't know that. It just applies the clipPath as defined.”
                    * it is also **confirmed **by the comment
    * [https://stackoverflow.com/questions/58645497/svg-clipping-path-not-working-correctly-with-css-animation](https://stackoverflow.com/questions/58645497/svg-clipping-path-not-working-correctly-with-css-animation) 
    * &lt;g/> not allowed in clipPath. I was scratching my head over why that wasnt working earlier today.
        * [https://github.com/w3c/fxtf-drafts/issues/17](https://github.com/w3c/fxtf-drafts/issues/17) 
        * [https://lists.w3.org/Archives/Public/www-svg/2016Aug/0000.html](https://lists.w3.org/Archives/Public/www-svg/2016Aug/0000.html) 


## #w_memo (coordinate with vaibhab tmrw morning, what are his cues)


## #w_svg-clip 



* website scrum tomorrow (thursday)
    * first off, communication
        * nancy and i had our follow up yesterday re timeline for hero story
            * i did not know that we had a deadline or particular date in mind at all, nevermind that we were already operating behind shedule
        * we should be talking more about our timeline, roadmap and goals, estimating and together
        * i’m super confident that we can meet and maybe even exceed our current goals once we sync up and pick up a solid rhythm 
        * i know expectations and mutual understanding and **flow **feels natural once you’ve been on a project for a while, but consider that we are very **new to the team**, coming in as blank slates and at very short notice, such that **we had WIP to wrap up **while onboarding as well. 
        * on top of that, this particular story is very **technically complex** (not just in achieving the desired result through svg clip paths, but also in designing and organizing the polymorphic responsive behaviour. its a lot of code, and it leverages apis that can’t be reasoned about and explored like you might a javascript library, but rather studied, and the answers are not forthcoming, they come in bits and pieces, we’re using stack overflow posts with no answers and mozilla docs), using svg apis that we never even knew existed before, that have very scant documentation or answers online.
            * we had a nice example to work from ([drw.com](http://drw.com)), scott and steph provided some source code (but they didn’t know much about how it worked either), but naive transplantation doesn’t yield (we were very persistent, but the behaviour is very unpredictable). even if we got it working, **it would be a huge liability,** we wouldnt be able to guarantee reliability, stability or maintainability. 
                * *** the[ drw.com](http://drw.com) example relies on the entire site being perfectly still because they are using discrete responsive resizing. auto-filling would not be restrictive in that way, allowing components to fill space leveraging the standard approach using flex (which adjusts dynamically and continuously).**
            * we need to transform the svg dynamically, using computed values as svg attributes, to properly generalize the code. 
                * we need to make **many very specific decisions **based on subtle differences that reqire esoteric knowlege, **because we’re not dealing with empirical scripting languages here, **where you can read or specify a precise behaviour.** the most important parts of our code here all rely on declarative apis **where the relations and interactions between different statements is** obscure and must be theorized.**
                    * **image can be brought in witin svg or outside html **and have the clip path exctracted from within the svg and applied via css, with operate differently.
                    * **clip paths can be defined within css vs svg. **the decision here is easy because svg is much more powerful and flexible, but i only know that after deep spike, and the repercussions of what at first glance looks like a trivial detail are profound and demand we consider **ramifications and interplay with the rest of our code.**
                * ***basically, we need to learn svg to do this properly.***
            * ***if we’re planning to make this a recurring theme/motif on the site, we need to understand it well enough to develop a robust and maintainable design pattern. sananda seems to be planning to use these shapes quite a lot. ***
    * anyway, after the initial attempts to use[ drw.com](http://drw.com) example naively, we made the pivot this week took a deep dive into the subject and learned a lot. *vaibhab has been doing really good work and crunching hard to get this out asap.*
        * **We made a ton of progress yesterday, I only started a focused study yesterday afternoon, and I already much more clarity end-to-end. **
        * **I’m confident we’ll have a complete implementation strategy and some demos next week.**
            * we just need to bring it all together and design for replication and robustness.
        * **At that point hammering out the pull requests should be straightforward, not only for the hero banner but for the other planned svg clip graphics.**
        * *********************
            * **CONCLUSIVE TLDR:**
                * we delay the release of this hero
                * **but once we finish the spike, we will be able to bring all the svg magic to life. **
                    * by then we should have all the svg designs greenlit
                * we will pursue transparency and collaboration, keeping you up to date and involved
                * **UNLESS we dont actually want to use svg clip graphics in other places. **
                    * in this case we still would still need to spike, but with lesser complexity and thus faster. 
        * *********************
    * we looked into a number of ways this can be achieved
            * also big thanks to sananada for helping to keep us unblocked with her fast turnarond on svg modifications
        * the cheapest option is the one i’m more interested in. vaibhab can tell us more about it in a second. **[edit: in fact we might want to solve the problem of auto-fitting and continuous resizing for the future theme series, so that we dont get stuck having to make a polymorphic component when all we want to do is shrink accordingly, and to prevent weird proportions because small changes in screen size that do not trigger a media query will result in proportional variance, since our graphics will be static]**
            * i personally like the cheap option because the solution becomes orders of magnitude more complex with every variable we introduce like freeform picture ratios or continous responsive scaling.


## 	⁃		⁃	these behaviours are/seem possible, however, we have some working examples, but neither of them seems to be to be valuable enough to warrant the extra time, work, and future maintainability.



* so vaibhab, do you want to talk about where we are progress wise and maybe then open it up for discussion? 


## 23/02/03 \
 \
**23/02/03 friday night**



* workstreams
    * **~~free agents~~**
        * ~~$ headless CMS outreach (by feb 28!)~~
            * ~~cultureamp goal:[ https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069788&selectedTeamId=53f197f8-72fd-4ec4-895e-b697322f7da5](https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069788&selectedTeamId=53f197f8-72fd-4ec4-895e-b697322f7da5) ~~
            * ~~some work done by abdel we could take to the finish line:[ https://www.notion.so/rangle/How-cloud-native-affects-performance-and-distribution-of-modern-stacks-352ff3a6a83d4224860ca24a9c37dbaa](https://www.notion.so/rangle/How-cloud-native-affects-performance-and-distribution-of-modern-stacks-352ff3a6a83d4224860ca24a9c37dbaa) ~~
    * **~~* qa (digital ops)~~**
        * ~~$ get them promoted by June~~
            * ~~cultureamp goal:[ https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069242&selectedTeamId=bd4fd239-cff6-444e-9b64-79ebb9494538](https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069242&selectedTeamId=bd4fd239-cff6-444e-9b64-79ebb9494538) ~~
            * ~~we should make it seem more pressing. we should say that this is the latest possible time, that at this time i will be reallocated and we will not continue the current effort.~~
                * ~~not now, we just said end of june, and we dont want to seem like what we tell them is not reliable.~~
                * ~~maybe this can be communicated when someone is not progressing at the pace we need, on an individual meet~~
        * ~~react skill:[ https://www.notion.so/rangle/React-f25912be6d454bdca3c7d683917d460f](https://www.notion.so/rangle/React-f25912be6d454bdca3c7d683917d460f) ~~
        * ~~questions:~~
            * ~~what is "digital ops"? I also see this in our mooncamp goals as a possible "pillar". is this meant to say that we want the qas to be not just developers but developers with devps chops?~~
        * ~~backlog~~
            * ~~clean up react skill~~
    * **reports**
        * $ staff developer candidates
        * show growth and goal-setting
    * *** okr: build capability **
        * cultureamp goal:[ https://rangle.cultureamp.com/performance/new_goals/department?goalId=3068781](https://rangle.cultureamp.com/performance/new_goals/department?goalId=3068781) 
        * mooncamp goal:[ https://app.mooncamp.com/#/goals/31248649](https://app.mooncamp.com/#/goals/31248649) 
        * dxp platform pillars are:
            * cultureamp: 
                * design system / radius 
                    * "already in progress and established"
                * headless CMS (current focus)
                * digital ops
                    * * needs clarity, how does this relate to qa transition to developer? 
            * mooncamp
                * design system / radius 
                    * "pillar ready"
                * Headless CMS
                    * "possible new pillar"
                * Digital Ops
                    * "possible new pillar"
                * MACH
                    * "possible new pillar"
                * Open Banking
                    * "possible new pillar"
        * * questions:
            * what do we mean by "1 of 3 today"? (in cultureamp)
                * cultureamp makes it seem like we mean that right now i am only focusing on headless. this that why we only have key results related to headless
                * mooncamp makes it seem like it we mean that radius / design systems is the 1, since it's moving already
                    * should i have any key results related to radius?
            * Digital Ops is mentioned as a pillar, but we are actioning on it already, so should we not have key results? i do see how that could be redundant, since it's tracked in team goals
    * *** radius / knowledge**
        * is this related to any of our culture amp goals?
        * what are the key results here? how do we track?
    * *** projects: momentive **
        * what are the key results here? how do we track? no goal?
        * i have reports that are in projects i'm not onboarded onto, so clearly there're project-level goals here. maybe just feedback?
        * backlog
            * [before monday] review more prs and stuff
            * study tools (nextjs, etc)
            * [monday] get help to get everything working and questions answered
            * [tuesday] pick up a small ticket
* backlog work
    * follow up with natalyia about free agents cms and her project help
    * follow up with leah about the accessibility stuff with geethu
    * follow up with 100ms & hyperbeam (eventually, no rush)
    * review cultureamp feedback
    * find free agents for cms
    * talk to harish about software developer
    * review more momentive prs
    * schedule short but frequent 1:1s
    * put my own personal goals on culture amp
* habits work 
    * keep track of daily activities as a spreadsheet for visibility, we'll show it to willian weekly, as well as other spreadsheets to show like, goal progress, whatever. we can provide it on friday and ask for feedback mondays.
    * check bamboohr for tasks (how often?)
    * (later) give/ask for feedback from people (when we have a good opportunity)
    * update mooncamp?
    * check notion for "updates" (mentions, etc)
    * update tech leadership notion
        * task board
        * talent snapshot
* resources work
    * mooncamp 
        * goals links
            * [https://app.mooncamp.com/#/goals/27337079](https://app.mooncamp.com/#/goals/27337079) 
                * * main one for us? ^
            * [https://app.mooncamp.com/#/goals/26082403](https://app.mooncamp.com/#/goals/26082403) 
        * * i dont understand how we get to the above goals from the top level goals (i do have everything checked in the dropdown). they dont seem to be there? I would expect to find the "annual: operationalize the digital..." in the top level "all goals" list
    * tech leadership
        * task board
            * [https://www.notion.so/rangle/e838b39d7402436a98676c50b066da15?v=b7452ba0c2dc4a1e8053cfcfe4194ae1](https://www.notion.so/rangle/e838b39d7402436a98676c50b066da15?v=b7452ba0c2dc4a1e8053cfcfe4194ae1) 
            * * questions:
                * should we use cultureamp goals for ourselves? jason is using it and it make sense to me, i can see how they refer to different things, but there's a lot of overlap, and you might be able to use the task board for your goals as well?
        * talent snapshot 
            * [https://www.notion.so/rangle/a89e5957c0af4517a4919bea06eafc05?v=a6a215beb4304ae9a3ecff656a68c5eb](https://www.notion.so/rangle/a89e5957c0af4517a4919bea06eafc05?v=a6a215beb4304ae9a3ecff656a68c5eb)  
* momentive onboarding
    * repos
        * **smquestions (works)**:[ https://code.corp.surveymonkey.com/webplatform/smquestions](https://code.corp.surveymonkey.com/webplatform/smquestions)  
            * * npm run lint: hangs after 1/2 tasks?
            * npm run storybook: works (after error resolved)
                * did not work at first
    * fixed with: 
        * export NODE_OPTIONS=--openssl-legacy-provider
        * [https://stackoverflow.com/questions/69692842/error-message-error0308010cdigital-envelope-routinesunsupported](https://stackoverflow.com/questions/69692842/error-message-error0308010cdigital-envelope-routinesunsupported) 
* 
    * *** smweb (issues)**:[ https://code.corp.surveymonkey.com/webplatform/smweb](https://code.corp.surveymonkey.com/webplatform/smweb) 
        * repo docs:[ https://code.corp.surveymonkey.com/pages/webplatform/smweb](https://code.corp.surveymonkey.com/pages/webplatform/smweb) 
        * * smweb: what's approuter?
            * [https://code.corp.surveymonkey.com/ACMe/approuter#if-your-app-normally-runs-ssl-certs-on-production](https://code.corp.surveymonkey.com/ACMe/approuter#if-your-app-normally-runs-ssl-certs-on-production) 
            * webplat requires:[ https://code.corp.surveymonkey.com/pages/webplatform/smweb/#/pages/smweb/getting-started](https://code.corp.surveymonkey.com/pages/webplatform/smweb/#/pages/smweb/getting-started)  
        * * api/graphapi: npm start (after npm i)
            * asks for corp username and password, but they dont work. "invalid credentials" (tried with and without domain)
                * "Secrets are **not** stored in .env or local.env files, so you will need to load them from Vault."
* * call outs (not a big deal, just describing my experience) 
    * prs usually not linked to jira tickets (and vice versa)
    * prs not very descriptive
* prs
    * smweb
        * chore(nextweb): add apollo query timing logging
            * owner: michael mrowetz
            * link:[ https://code.corp.surveymonkey.com/webplatform/smweb/pull/13503](https://code.corp.surveymonkey.com/webplatform/smweb/pull/13503) 
        * build(nextweb): enable eslint check on prod builds
            * owner: michael mrowetz
            * link:[ https://code.corp.surveymonkey.com/webplatform/smweb/pull/13468](https://code.corp.surveymonkey.com/webplatform/smweb/pull/13468) 
        * Rawr 1252 Matrix integration to nextweb
            * owner: thomas garrison
            * link:[ https://code.corp.surveymonkey.com/webplatform/smweb/pull/13436/files](https://code.corp.surveymonkey.com/webplatform/smweb/pull/13436/files) 
            * questions:
                * what is a nextweb/patches/*.patch file?
                * what does matrix integration mean?
                    * seems like matrix is a type of question
                * how do these "generated types" work?
        * fix: Update script to install question-widgets, fix isDark imports, exclude package.json in the patch file #13343
            * owner: mat findlay
            * link:[ https://code.corp.surveymonkey.com/webplatform/smweb/pull/13343/files](https://code.corp.surveymonkey.com/webplatform/smweb/pull/13343/files) 
            * questions: what the hell is going on here??
* * general questions
    * what type of things do we do on smweb vs smquestions?
        * i see a lot more commits from our team on smquestions, and the commits have more code (ui stuff)
    * task board
* notes work
    * ssr react blog (good example, willian favorite)
        * [https://rangle.io/blog/building-react-components-with-server-side-rendering-in-mind](https://rangle.io/blog/building-react-components-with-server-side-rendering-in-mind)  
* notes study: nextjs
    * [https://learning.oreilly.com/library/view/real-world-next-js](https://learning.oreilly.com/library/view/real-world-next-js) 


## 23/01/25 \
**23/01/25 wednesday**



* radar meets
    * conversation: what do we know about it
    * otter subscribe
* meet: momentive: Web Platform SOS
    * questions
        * what is create migration, how will it be different from what we’re currently doing
    * we have some ssr problems
        * study up on ssr and next (the blog post, and general nextjs study)
* bootcamp react
    * CRA basic todo app (only create / delete)
    * schedule view 
        * side-by-side
        * learning: sharing state across components
    * modal (editing items)
    * search
        * hide all that dont match (from schedule too
        * learn: logic (pure)
    * save state
        * learn: local storage
        * learn: initializing data and updating through a central point
    * showing current time as a line in the schedule
    * performance
        * optimizing renders
        * separate challenges (contrived examples)
    * developer tools / architecture
        * goal: unit tests, types (because it helps us scale out the code without breaking, decreased dev velocity, or decreased performance)
        * intro to unit tests (assignment)
        * intro to typescript (assignment)
        * attempt to bring into project (should be difficult)
        * intro to architecture (refactoring and organization) (opinionated)
            * code organization
                * modular vs functional directory structure
                * code types (define each and how it will tested / typed)
                    * pure cmp
                    * connected cmp
                    * logic (pure)
                    * example data
                    * services (singleton, stateful, effects) (hooks and hocs)
                        * mocks
            * functional patterns
                * centralize state
                * learn: redux architecture
                * services / daemons aka “sagas” (singletons) (hooks and hocs)
        * now do the unit tests, types, and performance optimizations
    * routing (schedule view)
    * libraries
        * material
        * redux
    * e2e tests: cypress
* work backlog
    * create k6 radar blip from zoom rec
    * how is the radar ui made? can you mount like a react extension? cause we could use that for our  tech-initiatives
    * * post something on team-s (we havent gotten through all the 1:1s this week, and had to cancel some)
    * think about radar and knowledge. whats the plan here?
        * this seems relevant, but not in technology craft, so not sure if valid
            * [https://www.notion.so/rangle/Quick-Reference-Guide-of-Tools-and-Frameworks-615af846bd7a44ca90dba9c42ba65561](https://www.notion.so/rangle/Quick-Reference-Guide-of-Tools-and-Frameworks-615af846bd7a44ca90dba9c42ba65561) 
    * read react ssr blog
    * * schedule michael meets
    * onboard onto cmap
        * slack message:[ https://rangle.slack.com/archives/C04LWNKA25P](https://rangle.slack.com/archives/C04LWNKA25P) 
        * notion page:[ https://www.notion.so/rangle/CMap-cfd3f37f39a2497f80b421126423005e](https://www.notion.so/rangle/CMap-cfd3f37f39a2497f80b421126423005e) 
    * momentive
        * ticket: planning automation, integration tests. wdio
            * some existing question types (
            * some docs exist
            * kt with arthi (test engineer on momentive side)
                * invite everyone
            * selenium grid / mt1
            * these are e2e tests
            * #webdriverio channel on momentive slack
            * [https://code.corp.surveymonkey.com/pages/qa/webplatform/#/](https://code.corp.surveymonkey.com/pages/qa/webplatform/#/) 
        * onboard
            * ashis meets
            * michael meets
* momentive-meet-ashis
    * i have many questions, and i will have many more soon. i how much time do we have for questions
    * questions
        * what do you see as our current challenges
        * # how independently do we operate, where are our contact points for integration
            * devops, qa is momentive
                * how well do these work, any bottlenecks?
            * architecture / system design?
            * are there non-ranglers on our scrum team?
            * do we “own” anything? any repos? any non-ranglers contributing to the nextjs repo
            * pr approvals
            * & 
                * own jira board
                * all rangle scrum
        * i understand we have a technical knowledge bottleneck
        * i understand a migration is taking place from some python-based services to nextjs for the survey product, but i know also other separate projects have occurred
            * what other projects have happened
            * what other projects might happen in the future
        * what aspects of the current project are the most crucial for success
        * how can we achieve visibility and organizational impact (as rangle within momentive)
        * what relationships/people should we take care of
        * what repos / technologies do we touch / read / contribute?
    * actionables
        * message ashis about ad hoc meetings


- bootcamp react
    - CRA basic todo app (only create / delete)
    - schedule view 
        - side-by-side
        - learning: sharing state across components
    - modal (editing items)
    - search
        - hide all that dont match (from schedule too
        - learn: logic (pure)
    - save state
        - learn: local storage
        - learn: initializing data and updating through a central point
    - showing current time as a line in the schedule
    - performance
        - optimizing renders
        - separate challenges (contrived examples)
    - developer tools / architecture
        - goal: unit tests, types (because it helps us scale out the code without breaking, decreased dev velocity, or decreased performance)
        - intro to unit tests (assignment)
        - intro to typescript (assignment)
        - attempt to bring into project (should be difficult)
        - intro to architecture (refactoring and organization) (opinionated)
            - code organization
                - modular vs functional directory structure
                - code types (define each and how it will tested / typed)
                    - pure cmp
                    - connected cmp
                    - logic (pure)
                    - example data
                    - services (singleton, stateful, effects) (hooks and hocs)
                        - mocks
            - functional patterns
                - centralize state
                - learn: redux architecture
                - services / daemons aka “sagas” (singletons) (hooks and hocs)
        - now do the unit tests, types, and performance optimizations
    - routing (schedule view)
    - libraries
        - material
        - redux
    - e2e tests: cypress

- work backlog
    - create k6 radar blip from zoom rec
    - how is the radar ui made? can you mount like a react extension? cause we could use that for our  tech-initiatives
    - * post something on team-s (we havent gotten through all the 1:1s this week, and had to cancel some)
    - think about radar and knowledge. whats the plan here?
        - this seems relevant, but not in technology craft, so not sure if valid
            - https://www.notion.so/rangle/Quick-Reference-Guide-of-Tools-and-Frameworks-615af846bd7a44ca90dba9c42ba65561 
    - read react ssr blog
    - * schedule michael meets
    - onboard onto cmap
        - slack message: https://rangle.slack.com/archives/C04LWNKA25P 
        - notion page: https://www.notion.so/rangle/CMap-cfd3f37f39a2497f80b421126423005e 
    - momentive
        - ticket: planning automation, integration tests. wdio
            - some existing question types (
            - some docs exist
            - kt with arthi (test engineer on momentive side)
                - invite everyone
            - selenium grid / mt1
            - these are e2e tests
            - #webdriverio channel on momentive slack
            - https://code.corp.surveymonkey.com/pages/qa/webplatform/#/ 
        - onboard

23/01/25 wednesday

- radar meets
    - conversation: what do we know about it
    - otter subscribe

- meet: momentive: Web Platform SOS
    - questions
        - what is create migration, how will it be different from what we’re currently doing
    - we have some ssr problems
        - study up on ssr and next (the blog post, and general nextjs study)

- bootcamp react
    - CRA basic todo app (only create / delete)
    - schedule view 
        - side-by-side
        - learning: sharing state across components
    - modal (editing items)
    - search
        - hide all that dont match (from schedule too
        - learn: logic (pure)
    - save state
        - learn: local storage
        - learn: initializing data and updating through a central point
    - showing current time as a line in the schedule
    - performance
        - optimizing renders
        - separate challenges (contrived examples)
    - developer tools / architecture
        - goal: unit tests, types (because it helps us scale out the code without breaking, decreased dev velocity, or decreased performance)
        - intro to unit tests (assignment)
        - intro to typescript (assignment)
        - attempt to bring into project (should be difficult)
        - intro to architecture (refactoring and organization) (opinionated)
            - code organization
                - modular vs functional directory structure
                - code types (define each and how it will tested / typed)
                    - pure cmp
                    - connected cmp
                    - logic (pure)
                    - example data
                    - services (singleton, stateful, effects) (hooks and hocs)
                        - mocks
            - functional patterns
                - centralize state
                - learn: redux architecture
                - services / daemons aka “sagas” (singletons) (hooks and hocs)
        - now do the unit tests, types, and performance optimizations
    - routing (schedule view)
    - libraries
        - material
        - redux
    - e2e tests: cypress

- work backlog
    - create k6 radar blip from zoom rec
    - how is the radar ui made? can you mount like a react extension? cause we could use that for our  tech-initiatives
    - * post something on team-s (we havent gotten through all the 1:1s this week, and had to cancel some)
    - think about radar and knowledge. whats the plan here?
        - this seems relevant, but not in technology craft, so not sure if valid
            - https://www.notion.so/rangle/Quick-Reference-Guide-of-Tools-and-Frameworks-615af846bd7a44ca90dba9c42ba65561 
    - read react ssr blog
    - * schedule michael meets
    - onboard onto cmap
        - slack message: https://rangle.slack.com/archives/C04LWNKA25P 
        - notion page: https://www.notion.so/rangle/CMap-cfd3f37f39a2497f80b421126423005e 
    - momentive
        - ticket: planning automation, integration tests. wdio
            - some existing question types (
            - some docs exist
            - kt with arthi (test engineer on momentive side)
                - invite everyone
            - selenium grid / mt1
            - these are e2e tests
            - #webdriverio channel on momentive slack
            - https://code.corp.surveymonkey.com/pages/qa/webplatform/#/ 
        - onboard
            - ashis meets
            - michael meets

- momentive-meet-ashis
    - i have many questions, and i will have many more soon. i how much time do we have for questions
    - questions
        - what do you see as our current challenges
        - # how independently do we operate, where are our contact points for integration
            - devops, qa is momentive
                - how well do these work, any bottlenecks?
            - architecture / system design?
            - are there non-ranglers on our scrum team?
            - do we “own” anything? any repos? any non-ranglers contributing to the nextjs repo
            - pr approvals
            - & 
                - own jira board
                - all rangle scrum
        - i understand we have a technical knowledge bottleneck
        - i understand a migration is taking place from some python-based services to nextjs for the survey product, but i know also other separate projects have occurred
            - what other projects have happened
            - what other projects might happen in the future
        - what aspects of the current project are the most crucial for success
        - how can we achieve visibility and organizational impact (as rangle within momentive)
        - what relationships/people should we take care of
        - what repos / technologies do we touch / read / contribute?
    - actionables
        - message ashis about ad hoc meetings

23/02/03 friday night

- workstreams
    - free agents
        - $ headless CMS outreach (by feb 28!)
            - cultureamp goal: https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069788&selectedTeamId=53f197f8-72fd-4ec4-895e-b697322f7da5 
            - some work done by abdel we could take to the finish line: https://www.notion.so/rangle/How-cloud-native-affects-performance-and-distribution-of-modern-stacks-352ff3a6a83d4224860ca24a9c37dbaa 
    - * qa (digital ops)
        - $ get them promoted by June
            - cultureamp goal: https://rangle.cultureamp.com/performance/new_goals/team?goalId=3069242&selectedTeamId=bd4fd239-cff6-444e-9b64-79ebb9494538 
            - we should make it seem more pressing. we should say that this is the latest possible time, that at this time i will be reallocated and we will not continue the current effort.
                - not now, we just said end of june, and we dont want to seem like what we tell them is not reliable.
                - maybe this can be communicated when someone is not progressing at the pace we need, on an individual meet
        - react skill: https://www.notion.so/rangle/React-f25912be6d454bdca3c7d683917d460f 
        - questions:
            - what is "digital ops"? I also see this in our mooncamp goals as a possible "pillar". is this meant to say that we want the qas to be not just developers but developers with devps chops?
        - backlog
            - clean up react skill
    - reports
        - $ staff developer candidates
        - show growth and goal-setting
    - * okr: build capability 
        - cultureamp goal: https://rangle.cultureamp.com/performance/new_goals/department?goalId=3068781 
        - mooncamp goal: https://app.mooncamp.com/#/goals/31248649 
        - dxp platform pillars are:
            - cultureamp: 
                - design system / radius 
                    - "already in progress and established"
                - headless CMS (current focus)
                - digital ops
                    - * needs clarity, how does this relate to qa transition to developer? 
            - mooncamp
                - design system / radius 
                    - "pillar ready"
                - Headless CMS
                    - "possible new pillar"
                - Digital Ops
                    - "possible new pillar"
                - MACH
                    - "possible new pillar"
                - Open Banking
                    - "possible new pillar"
        - * questions:
            - what do we mean by "1 of 3 today"? (in cultureamp)
                - cultureamp makes it seem like we mean that right now i am only focusing on headless. this that why we only have key results related to headless
                - mooncamp makes it seem like it we mean that radius / design systems is the 1, since it's moving already
                    - should i have any key results related to radius?
            - Digital Ops is mentioned as a pillar, but we are actioning on it already, so should we not have key results? i do see how that could be redundant, since it's tracked in team goals
    - * radius / knowledge
        - is this related to any of our culture amp goals?
        - what are the key results here? how do we track?
    - * projects: momentive 
        - what are the key results here? how do we track? no goal?
        - i have reports that are in projects i'm not onboarded onto, so clearly there're project-level goals here. maybe just feedback?
        - backlog
            - [before monday] review more prs and stuff
            - study tools (nextjs, etc)
            - [monday] get help to get everything working and questions answered
            - [tuesday] pick up a small ticket

- backlog work
    - follow up with natalyia about free agents cms and her project help
    - follow up with leah about the accessibility stuff with geethu
    - follow up with 100ms & hyperbeam (eventually, no rush)
    - review cultureamp feedback
    - find free agents for cms
    - talk to harish about software developer
    - review more momentive prs
    - schedule short but frequent 1:1s
    - put my own personal goals on culture amp

- habits work 
    - keep track of daily activities as a spreadsheet for visibility, we'll show it to willian weekly, as well as other spreadsheets to show like, goal progress, whatever. we can provide it on friday and ask for feedback mondays.
    - check bamboohr for tasks (how often?)
    - (later) give/ask for feedback from people (when we have a good opportunity)
    - update mooncamp?
    - check notion for "updates" (mentions, etc)
    - update tech leadership notion
        - task board
        - talent snapshot

- resources work
    - mooncamp 
        - goals links
            - https://app.mooncamp.com/#/goals/27337079 
                - * main one for us? ^
            - https://app.mooncamp.com/#/goals/26082403 
        - * i dont understand how we get to the above goals from the top level goals (i do have everything checked in the dropdown). they dont seem to be there? I would expect to find the "annual: operationalize the digital..." in the top level "all goals" list
    - tech leadership
        - task board
            - https://www.notion.so/rangle/e838b39d7402436a98676c50b066da15?v=b7452ba0c2dc4a1e8053cfcfe4194ae1 
            - * questions:
                - should we use cultureamp goals for ourselves? jason is using it and it make sense to me, i can see how they refer to different things, but there's a lot of overlap, and you might be able to use the task board for your goals as well?
        - talent snapshot 
            - https://www.notion.so/rangle/a89e5957c0af4517a4919bea06eafc05?v=a6a215beb4304ae9a3ecff656a68c5eb  

- momentive onboarding
    - repos
        - smquestions (works): https://code.corp.surveymonkey.com/webplatform/smquestions  
            - * npm run lint: hangs after 1/2 tasks?
            - npm run storybook: works (after error resolved)
                - did not work at first
￼
                - fixed with: 
                    - export NODE_OPTIONS=--openssl-legacy-provider
                    - https://stackoverflow.com/questions/69692842/error-message-error0308010cdigital-envelope-routinesunsupported 
            - 

        - * smweb (issues): https://code.corp.surveymonkey.com/webplatform/smweb 
            - repo docs: https://code.corp.surveymonkey.com/pages/webplatform/smweb 
            - * smweb: what's approuter?
                - https://code.corp.surveymonkey.com/ACMe/approuter#if-your-app-normally-runs-ssl-certs-on-production 
                - webplat requires: https://code.corp.surveymonkey.com/pages/webplatform/smweb/#/pages/smweb/getting-started  
            - * api/graphapi: npm start (after npm i)
                - asks for corp username and password, but they dont work. "invalid credentials" (tried with and without domain)
                    - "Secrets are not stored in .env or local.env files, so you will need to load them from Vault."
    - * call outs (not a big deal, just describing my experience) 
        - prs usually not linked to jira tickets (and vice versa)
        - prs not very descriptive
    - prs
        - smweb
            - chore(nextweb): add apollo query timing logging
                - owner: michael mrowetz
                - link: https://code.corp.surveymonkey.com/webplatform/smweb/pull/13503 
            - build(nextweb): enable eslint check on prod builds
                - owner: michael mrowetz
                - link: https://code.corp.surveymonkey.com/webplatform/smweb/pull/13468 
            - Rawr 1252 Matrix integration to nextweb
                - owner: thomas garrison
                - link: https://code.corp.surveymonkey.com/webplatform/smweb/pull/13436/files 
                - questions:
                    - what is a nextweb/patches/*.patch file?
                    - what does matrix integration mean?
                        - seems like matrix is a type of question
                    - how do these "generated types" work?
            - fix: Update script to install question-widgets, fix isDark imports, exclude package.json in the patch file #13343
                - owner: mat findlay
                - link: https://code.corp.surveymonkey.com/webplatform/smweb/pull/13343/files 
                - questions: what the hell is going on here??
    - * general questions
        - what type of things do we do on smweb vs smquestions?
            - i see a lot more commits from our team on smquestions, and the commits have more code (ui stuff)
        - task board
    - notes work
        - ssr react blog (good example, willian favorite)
            - https://rangle.io/blog/building-react-components-with-server-side-rendering-in-mind  

    - notes study: nextjs
        - https://learning.oreilly.com/library/view/real-world-next-js 

23/02/06 monday



- todo tonight
    - fix vault thing
    - momentive onboarding document on notion, and activity timeline on jira comments
    - add cycles to jira board
        - getting cycles out of free-agents and qa-dev
    - dev-fast-track channels
        - write some stuff in each one
        - archive old ones like tech-skills
    - make loopback work
    - updat

- meet: natalyia 
    - https://www.notion.so/rangle/Headless-CMS-Initiative-5119d49aabca4f8db1be2b81e9ec7771
    - cms platforms we use
        - Sanity
        - Contentful
        - Strapi (current)

- leah accessibility with geethu? or something else

- meet: momentive monthly check in
    - get the slides

- momentive: mat findlay's onboard
    - i need vault (jason)
    - resources
        - https://momentiveai.atlassian.net/wiki/spaces/A/pages/667289130/Rangle+Home+Page
        - https://momentiveai.atlassian.net/wiki/spaces/A/pages/800882899/Requesting+Vault+Policies+for+SMWeb
    - mat's repos repos
        - approuter
            - repo created by ??
            - you just get the config to work and you're done
            - you have to restart it and update it anyway
        - kickstart
            - purpose: generates a token to use for the valut
        - automation 
            - purpose: e2e regression tests.
            - what are we testing? tests on the question types within smweb
            - probably the last one you need to learn
            - wdio stuff is here
            - repo created by rangle
        - smquestions 
            - types of questions: matrix, etc
            - repo created by rangle
            - >%30
        - smweb
            - >%30
            - repo created by rangle

- figure out when to hang out with joaquim (thursday)

- work habits
    - check up on the people that i recruit to do something i need. they need constant support

- momentive update for scrum
    - i'm going to get it all in writing, tracked on jira, for now i'll read it
    - goals
        - full IT onboarding and access
        - get everything installed and running
        - understand the product
        - understand our team objectives
        - understand the technical landscape
            - identify all the tools that are relevant to our work. understand how they work, what purpose they serve, if/how/why we interact with them
            - understand the architectural patterns, philosophies, and guidelines in place. (within our technical scope)
        - understand our implementation plan
        - understand our team. our strengths and weaknesses as individual and as a team. 
            - skill levels and interest
        - understand our delivery timelines and estimations
    - progress updates
        - full IT onboarding and access done
        - get everything installed and running: smquestions yes, smweb not bc approuter
        - understand the product
        - understand our team objectives
        - understand the technical landscape
        - understand our implementation plan
        - understand our team. our strengths and weaknesses as individual and as a team. 
        - understand our delivery timelines and estimations
    - 


- right now
    - update momentive jira, slack

- todo today (find the time, before willian meet)

- todo before 10
    - update momentive jira
    - compile reports files
        - -> update leadership / talent snapshot
        - -> send them goal ideas
        - -> update goals on cultureamp
    - schedule
        - willian meet for questions
            - what do we mean by "1 of 3 today"? (in cultureamp)
                - cultureamp makes it seem like we mean that right now i am only focusing on headless. this that why we only have key results related to headless
                - mooncamp makes it seem like it we mean that radius / design systems is the 1, since it's moving already
                    - should i have any key results related to radius?
            - should we make it a habit to update skills base regularly? i would track the activity with a ticket.
            - Digital Ops is mentioned as a pillar, but we are actioning on it already, so should we not have key results? i do see how that could be redundant, since it's tracked in team goals
        - update leadership board / talent snapshot
            - execute on some and add some new ones
            - create report files,  and then create some goals 

- todo during lunch
    - collect all my stuff and receipts from around the house into backpack
    - message nataliya asking how’s it going so far

- org plan (in order)
    - pass: exec
    - pass: notes/docs: transcripts, etc (people, workstreams, etc)
    - update tools: 
        - visibility: jira, cultureamp, leadership board, talent snapshot… etc (what else?)
        - management: skills (react skill)
    - schedule
    - personal schedule
    - personal finance
    - study momentive (until sleep)


- * track habits (maybe spreadsheet at end of day along with finance?) (also add mana’s advice)
￼

- work
    - keep an eye on https://docs.google.com/spreadsheets/d/1ez1pE6d89L4a-oVktsndj4afU_Va3Ar9yCpUjuSt32M/edit#gid=220787023&fvid=662829501 
        - especially in preparation for staffing meetings

- work: free agents
    - * habit: every friday update the FA list
    - current free agents
        - Abi Aderoju
        - vaibhav Dixit (cant today, starts project in a couple of days)
        - Sananda Dutta (starts being free agent tmrw tuesday)
        - William Henlin (starts project in a couple of days)
        - Nathan Kanigsberg (OOO)
        - Tammy Li
        - Yena Lee (role doesnt qualify)
        - Tarek Mavani (is busy with other stuff, not sure if qualifies)
    - free agent stakeholders 
        - jason santos
        - willian
    - how do i remove people from channels?
        - cant, has to be a private channel
        - its fine anyway, for visibility
    - * how do i remove people from events?

free agents
- angular schem (stephanie)
    - https://www.notion.so/rangle/Use-Angular-Schematics-to-Supercharge-Your-Design-System-Dev-Experience-b9d9157dc2fc4a91b0a5a8295ac4d4ba 
    - stephanie is so fucking cool
    - ng update
        - will update design system
        - code gen
        - like scaffolding
- product at rangle (tammy)
    - https://docs.google.com/document/d/1hMOTQQE13HqUwVK6nfWvxHMWa9dGLbxtW5zBb3zxxNc/edit?usp=sharing
- angular + cms + schematics (william)
    - ask him if he wants to join steph’s demo, they can do a cool joint thing
    - what should we build/do (ask willian)
    - 

- primary momentive client stakeholders
    - 1) greg is our sponsor
    - 2) deepa is principal engineer
    - 3) tim lang 

- momentive 
    - guy we met at sushi we need to connect with is waseem el-mawaz
    - the Account Team Sync meeting is very important, i have to bring material for this. (once we are onboarded, of course)
        - Account Plan: https://docs.google.com/spreadsheets/d/1I-St47d9sap0pHAYq-t9b2HrcrfRqofl4Tx9gssJeK4/edit#gid=1073614395  
        - Account Team Board: https://www.notion.so/rangle/Account-Hub-7853a8e0f324480bbd103b5971a30bcc 
        - https://www.notion.so/rangle/Momentive-ai-Program-a05073d1d9b54497b86f4ff7975bdc66 

exec-work

oneoffs
- radius entries (k9)
- dev-fast-track
    - next meet: review submissions
    - move remaining challenge submissions to ..-projects
    - karen should try hooks now, since she did what i asked already, the code is so much uglier in classes, poor girl
- reconnect with Tarek Hasabelnaby about cloud thing
- update willian on vacations
    - rafae: "I'm waiting until the end of the engagement. I usually take a week max"
        - but it looks like only a few days in between RBC stints?
    - harish: ?? 
        - he has 6 days booked
- * willian report
- goals follow up
    - mat findlay: hould be more specific/measurable, and shorter term (he has it set for december)
    - leah: none yet
- asokan/tarek transfer? (in order)
    - ask jas (i can offer the people that are on vacation)
    - ask willian
- ** talk to ashis about scott conversation and plan to not take tickets
- ai-mafia
    - find people for ai-mafia
- (see below)
￼

projects
- contentful project w stephanie
- podcasts / meetups (follow up with alice, with some examples)
- ai-mafia

questions
- willian
    - can i get asokan on my team? we can trade?
    - how should we do radar / knowledge
        - should we consider radar stuff similar to headless CMS, in that we encourage knowledge/outreach contributions?
        - there is knowledge out there about k6, for example (michael in momentive)
        - what should i be getting FAs to do besides headless CMS?
    - mooncamp. how should i updating it, given what's in my report?
    - * can we move asokan to my report? (jas)
        - i can trade for shatabdi

ongoing
- [weekly] report  for willian (accomplishments + learnings + objectives for next week)
- [bi-daily] cultureamp goals for reports, feedback
- [daily] talent snapshot update (after every 1:1 at least, or when responses posted)
- [daily] leadership task board frequently (after every 1:1 at least)
- [daily] bamboo check for tasks (vacation, etc)
- [weekly] cmap check if new people on bench (on mondays)

notes
- reports
    - Geethu Krishnaswamy (qa)
    - Harish Vijayaraghavalu (qa)
    - Jason Offet (sd)
    - Thomas Garrison (dev, under Jason Offet)
    - Gowdilya Jeyakumar (dev, under Jason Offet)
    - Joaquim Grilo (dev)
    - Jordan Finch (dev, momentive)
    - Leah Williams (dev)
    - Mat Findlay (dev, momentive)
    - Nataliya Ioffe (dev)
    - Nathan Kanigsberg (dev)
    - Rafae Ashraf (dev)
    - Shatabdi Bhattacharjee (dev)
    - Thomas Schemmer (sa)

23/01/26 NIGHT

 
- work backlog (later)
    - work
        - move stuff to notion
            - campaigns page using 

- backlog (weekend)
    - work
        - review free-agency etc materials from jason santos
        - finish tech-rally prep
            - notion pages 
                - including up-to-date entries for campaigns, skills, etc
                - match willian’s aesthetic (tech craft area)
                    - https://www.notion.so/rangle/Community-e7860df326bd41d8a6ef09a238d54316 
            - slack messages
        - check that our new institutions/communities dont exist already
            - otherwise we’ll have problems when we ask willian for permission to move them out of our own teamspace
            - we are not deprecating stuff, only filling gaps
        - update exec
        - update notes 
            - including meeting recordings/transcripts
            - report files
        - update talent snapshot with report goals (add to exec habits)
        - radar entries
        - momentive onboard
    - personal 
        - finance doc (doesnt have to be complete)
        - [needs personal finance] visit fam / rob
        - update exec
        - cpa4it
    - schedule
        - 1:1s
        - free agent meets/demo
        - qa meets
        - organizing / reserved time blocks
        - campaign context meets (headless CMS, Radius)

- slack channels
    - [later] #tech-meta (institution)
        - task board for like, updates to our tech system itself
            - examples
                - moving stuff from slack channel into a notion widget
                - decomissioning a community or institution
        - ideas
            - centralize badges system, such that you can get them from skills, campaign contributions, etc (can possibly extend indefinitely)
        - backlog
            - integrate further with rest of technology notion. 
                - examples
                    - add links to and from legacy stuff 
                - we are not deprecating stuff, only filling gaps.
    - #tech-campaigns (institution)
        - institution owner / maintainer
        - notion home
            - campaigns are found on our slack channel, although we’re working to transition the workflow into notion pages. 
            - workflow changes will be announced via slack channel
        - campaigns have 
            - status: active/inactive (inactive while info gathering/getting approves, etc)
            - descriptions, resources, history, etc
            - owner(s)
            - objective(s)
            - priority level
            - contribution invitations/opportunities/requests
            - task board / backlog
            - contributor acknowledgements
        - starters
            - headless CMS (GTM)
            - radius (accelerator)
            - transition QA talent into engineering (tech initiative)
        - maintenance
            - boards, statuses, contributor acks, etc
    - #tech-help (institution)
        - institution owner / maintainer
        - asks have
            - status: open/closed
                - closed when no longer wants the answer or
            - content (question, request, or whatever)
            - conversation
            - contributor acknowledgements
        - maintenance
            - follow up on asks, ensure they are reaching whoever should be reached if they are not being resolved, ensure asks are not open if the help is no longer required, ensure contributors are being acklowledged
    - #tech-skills (institution)
        - institution owner / maintainer
        - notion home: `Tech - Skills`
            - todo (weekend)
                - solution for earned badges records, notion board?
                - solution for discussion around badge creation/update
                - solution for submissions, feedback and approvals
                    - create new private repo in rangle org with specific name so we can search. can fork a starter repoand make changes. 
                        - 
                        - if approved, then 
            - content:
                - what is this for
                    - guiding expediting learning
                    - aligning on rangle technical philosophies and opinions
                - what is a skill badge
                    - not a full course, assumes self-directed learning using external materials
                        - materials to guide learning
                            - recommended external materials and context
                        - supplemental instructional content
                            - maybe we explain a common pitfall or an important pattern
                            - maybe example repositories
                        - rangle guidelines and opinions
                    - earned badges publicly available
                        - * solution for earned badges records
                    - stages: 
                        - badge `proposed`
                            - we discuss value of the skill for rangle, value of internal alignment around that skill (is it better that we all share certain understandings?), how much more efficient will it make learning? (our skill badges are more valuable if the learning path is not clear already. for example angular has already a guided learning guide, but react is much less structured and there are many tools and styles to discover and compare making self-directed learning more difficult), scope of badge (what are the specific requirements that define this skill), effort required to produce materials
                            - we record who the sponsors were that commissioned it
                        - materials and challenges `commissioned`
                            - work on actual material, help can be requested via #tech-campaigns, etc.
                            - finally approved and switched on
                        - badge `active`
                            - submissions reviewed and badges actively granted
                        - badge `decommissioned`
                            - no longer maintained, submissions no longer reviewed
                            - can be recommissioned, of course, if we gain more reviewing capacity or make whatever updates it needs or whatever
                    - challenge(s) for badge approved by Skills Advisory Board (or whatever, we dont need to over-formalize it, approved by rangle, lets say. as long as we’re documenting who endorsed/approved it)
                    - you make
                - Skills Advisory Board
                    - access to the historical submissions list, with comments
                    - commission new badges
                    - appoints or serves as Reviewers
                - Reviewer
                    - access to the historical submissions list, with comments.
                    - give feedback on submissions until approve
                        - can provide access to historical submissions (normally by giving access to submission repo) on discretionary basis
                    - badge granted once all challenges are approved
                        - announce somewhere
                        - add to registry (with name of reviewer)
        - notion skill - react: ``
    - #tech-projects (institution) 
        - projects have
            - approval (if active)
            - status: pending / active / closed
                - state reason for pending (need collabs?)
                - state reason for closing (cancelled? outcomes?)
            - objectives
                - deliverables: blog post, knowledge bank entry, demo, whatever
                - due date (if active)
            - owner(s)
            - timeframe
            - contribution invitations
            - contribution acknowledgements (when closed)
    - Free Agents (community)
        - notion home: `Free Agents` (legacy)
            - https://www.notion.so/rangle/Free-Agents-31a122ae00154710b6e629e64d4d829f 
        - notion board: `Free Agency Projects` (legacy)
            - https://www.notion.so/rangle/Free-Agency-Projects-b651c758dba648278618b53be8820660  
        - slack: (legacy)
        - todo (weekend):
            - review and update notion pages
            - ensure all FAs are on slack channel
            - prepare slack message
        - resources: 
            - notion board
            - 
    - QA Specialists (community)
        - notion home: `QA Specialists - Community`
            - https://www.notion.so/rangle/QA-Specialists-Community-7774cb9fc8a746efaef666802829a60c
        - ? notion board: `QA Specialists - Board`
        - slack: #tech-qa-specialists 
        - todo (weekend):
            - finish notion pages (own board page?)
            - add members list
        - resources: 
            - knowledge
            - cultureamp (for feedback and goal setting)
    - Team S (community)
        - notion: `Team S - Community`
            - https://www.notion.so/rangle/Team-S-Community-3b7ff5c8545542cfa77a8d12ad4a29fe
        - slack: #team-s 
        - todo (weekend):
            - finish notion page
            - add members list
        - resources:
            - 
            - [later] #tech-skills 
            - radar
            - knowledge
            - canvas
            - cultureamp (for feedback and goal setting)
    - [later] Infra & Devops (community)
        - slack: #tech-infra-and-devops 

- prep meet willian
    - here’s the plan
    - tell me if i missed anyone from communities
    - slack free agents
        - free agents channel not maintained (owned)
            - old members, no clear membership (who is actually expected to do stuff, etc)
        - more than just technology (should i reach out to non-tech? idk what to do there)

- backlog tonight
    - leadership
        - finish defining institutions and communities
        - create channels
            - identify all free agents
            - identify all qa
        - 1) * write messages to communities
        - schedule stuff
            - review leadership plan with willian
    - onboard onto momentive]
        - list stuff to study
        - prepare questions
        - schedule stuff
            - onboard with mike and jason (need questions)

- leadership goals
    - collaboration
    - support (from peers and seniors)
    - knowledge dissemination
    - visibility (encourage contributions and supporting others)
- institutions
    - tech-endorsements
        - official approved list of knowledge or assets that tech craft is most interested in developing
            - guides self-driven contributions (especially free agents) and tech community initiatives
        - sources
            - GTMs
                - headless CMS
            - active accelerators
                - Radius
            - active/approved radar blips
            - requests from active projects
        - methods
            - maintain list of interests
                - now: slack channel
                - ? later: notion page
            - virtual events to discuss, pitch, explain, or rally for support around an interest (preferably including people from the source)
    - tech-help
        - free-form tech help requests
            - kudos for providing support where possible, or bringing question to someone that resolves
            - must be a specific request for help, but it could be an open ended question or request for active support like a meet or whatever
        - community-builder: more support for everyone
        - right now needs a curator, for example to pass on questions and give kudos
        - slack for now, something better later
            - would be great to have something that keeps track of your answers
    - tech-skills
        - a bootcamp contains challenges that a tech learner can submit and have reviewed and get feedback or approval. can also contain materials like repos, resources like external links, and some written guides and explanations 
            - we dont actually write how-tos, except where we are expressing some rangle opinion
            - we expect them to learn on their own, possibly using tech-help
        - they can gain an award or certification upon completion of bootcamp
        - we can have bootcamps for various topics: react, devops, whatever. 
            - we can use this to instill a rangle approach and 
        - we can use the challenges for interviews
        - bootcamps are informed by knowledge bank
        - no bottleneck problem, can be scaled out
    - tech-projects
        - people can post approved active side projects (blogs, knowledge posts, POCs, whatever) they’re working on
        - they can get support, contributions, collaborators
        - they can post updates and details, we can share this with marketing or accross rangle
        - announcements like demo days
- communities
    - qa-engineers
        - source: owner checks cmap regularly (“quality”) until done
    - free-agents
        - weekly demo (fun)
        - source: owner checks cmap regularly (“bench” and only dev, sa, qa)
    - infra-and-devops
        - source: opt in
    - team-s
        - my reports
        - source: willian
- workstreams
    - momentive onboard
    - qa transition
        - uses tech-bootcamps
    - free agents
    - radar
        - process
            - initial discussion to flesh out blip
                - good learning for people, its a good opportunity since they have the tool fresh in mind
            - create blip from discussion content
                - benefit: fleshed out blip with multiple sides.
                - problem: transcription work. im a bottleneck. how is it gonna work without me.
                - possibility: some way of having this conversation happen in writing? in the blip itself like a slack thread? feels like you dont get the same amount of interest and energy that way, you end up with no contributions, feels like work. i think the verbal aspect is valuable. maybe some newbies can always transcribe?
            - present during tech regroup (having distributed the fleshed out stuff beforehand, possibly a written thread having added to it)
            - if green light, then we can add invite contributions via tech-interests.
    - reports
        - backlog
            - gather notes so far
            - * update talent snapshot
            - review the meeting with willian where he explained if goals can be project-oriented
    - knowledge
        - QUESTION
    - ~ infra and devops
    - ~ partnerships

- community people
    - free agents
        - Abi Aderoju
        - vaibhav Dixit (cant today, starts project in a couple of days)
        - Sananda Dutta (starts being free agent tmrw tuesday)
        - William Henlin (starts project in a couple of days)
        - Nathan Kanigsberg (OOO)
        - Tammy Li
        - Yena Lee (role doesnt qualify)
        - Tarek Mavani (is busy with other stuff, not sure if qualifies)
    - qa
        - Geethu Krishnaswamy
        - Karen Cardoz
        - Harish Vijayaraghavalu
        - Vasundhara Gogineni
        - Mamadou N'Diaye
        - Asokan Gunanathan

new-gah-app

reqs
features
new data
media uploads
"posts"
? "users" (our own representation)
new app
SSR
new server functionality
? consume external feeds
devex/devops features (these are optional/nice-to-haves)
[later?] a/b testing (validate changes)
[later?] user behaviour analytics (who is using snd how)

implementation
new app
? next, native app via capacitor
? the server inside next??
isnt it better to separate serving app from server actions? 
i guess they could be in the same code even if they are deployed to different places, but i dont like this intuitively. next merges the 2 types of things too much
i wouldnt mind a nextjs app if it was there just for SSR, and talked to a separate server
how do you scale horizontally

questions
? what was that data localization requirement? (do we sync content across borders or fully independent?)
? how do we integrate with system (auth + what else)
