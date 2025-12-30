

## **--------- temp**

[https://lululemon.invisionapp.com/share/4GNU01VVSWT#/screens](https://lululemon.invisionapp.com/share/4GNU01VVSWT#/screens)

[https://lululemon.invisionapp.com/share/9ENU01T4PC7](https://lululemon.invisionapp.com/share/9ENU01T4PC7) 

[https://whimsical.com/archive-mobile-foundational-userflows-1-0-PyVVdUCFiS62MAVtXB8Ds9](https://whimsical.com/archive-mobile-foundational-userflows-1-0-PyVVdUCFiS62MAVtXB8Ds9) 



* lll
    * !! [MONDAY (trmw)] finish doc 
    * [monday (tmrw)] 
        * tell eduard about interview candidate
        * tell team about diabetes
    * 

!!! have private conversations with team about diabetes



* go through teams conversations for notes (links and info)
* !! onboard, install with new machine
* https://lululemon.atlassian.net/wiki/spaces/SRE/pages/1240179787/M+A+Planner+Membership+Services
* ecom-checkout-client
* ecom-webapp
* wae-coco
* lll org
    * look at recent meetings to remember notes
        * some of them have recordings (monday's DCP arch meet)
* lll
    * [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/1672336399/Personalization+of+Contentful+Content](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/1672336399/Personalization+of+Contentful+Content)
    * [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP) 
    * meeting questions
        * our own sentry (in component library)
    * remind edmund to schedule that meet (incude jessica and mark zehr)  

-------------- thur jan 20 ^

------------ monday jan 31



* lll do
    * do we need our own domain?? (prob not, seems like only the old ones do like legal, but not checkout or account)
    * accounts separating (eric / zack)
        * what does the architecture look like (should we be doing the same)
        * accounts and loyalty should be the same?
            * if not how are we integrating
            * we want to integrate with them because they have everything set up and maintained. we can use the team itself as a resource
    * !! mfes and refresh (eric / zack)
        * right now refreshing everything because prerender
        * accounts is leaving, how are they doing it planning to solve itlater
            * if were gonna add badges and other complex loyalty ui pages, then we might want to have our own nextjs/mfe
    * learn graphql / terraform / nextjs
        * nextjs
            * SSG Server Side Generated, Server Side Rendering, Pre-Rendering, Client-Side Routing
    * platform and devops stuff
        * mwa (kelly hall, michael chen)
            * study the repo and setup meetings
            * !!: once we have our repo done, we can give it to them. 
            * they work on koala templates and libraries, we're gonna contribute our library
        * koala/kiwi (lululemon/koala-template)
            * kiwi is for backend service
            * read docs and set up meetings
            * we want to make it transparent to the engineers for better adoption and contributions
    * ask eric to give me access to see his event info
    * read confluence pages written by eric (sort by date)
    * do my task (i had to figure something out): mfe? nah.. also refresh thing
    * collect recordings (MOST VALUABLE: lennys tour of repo today)
    * new linkedin picture
    * contentful / cozy
        * meetings
        * we need accounts
    * !! document options/decisions made during repo setup
        * federated mods over mfe
        * storybook for independent cypress and manual testing (without needing to do it on other teams pr)
    * make membership stories (figure out what we need to do)
        * document how we came to know what to do and what we are doing  
        * consider mobile app
    * acronyms
        * RFC request for comment
        * CDP customer data platform
        * LPE (lll) lululemon  personalization engine
* collab
    * loyalty-only pages (faq, loyalty landing page, possibly navlink in accounts to your loyalty stuff [which should be ideally integrated into account pages in our opinion]): goal is mfe, can be just a page in some home repo (accounts)
    * integrated into their pages 
        * they do it
        * we write it into their repo (if integrated with accounts, we can leverage their services and connectivity with the services we need, and provide loyalty services to the rest of checkout/accounts, which is gonna need little loyalty widgets with significant complexity)
        * federated modules (component-level ownership: error boundaries, no leaks in or out, we dont share services)
* mwap
* confluence
    * peps/data collection and protection federated analytics
* words
    * procurement
        * hopefully this doesnt require a multi-quarter vendor procurement process
* lll
    * org
        * find recordings
        * get presentation: PEPS NBA ML 2022-jan-18
            * ruslan kasymov
    * docs
        * memberships subset plan
        * tech runway plan
    * notes
        * checkout/accounts team
* 
* meet
    * factors
        * no regression scripts or thorough list user stories
        * no original qa team members
        * cypress has issues and tests not up to date
        * poor monitoring, sentry and not much else
    * options
        * extricate, keep EnC up (upgrades?)
        * decomission everything, extricate EnC when we want it up (upgrades?)
        * decomission everything, rewrite EnC when we want it up
    * cost items
        * extrication
            * EnC and Memb in front end is very mixed together so extrication means combing through all code. We might just copy code piecemeal into new updated starter kit.
            * Memb-gnostic code spills, no strict boundary. We would also need to make changes throughout
        * maintenance without upgrades
            * high-risk liability. limited monitoring, qa resources, collaboration and support capability.
        * upgrades
        * rewrite
            * much cheaper than all upgrades
    * misc
        * poor qa capability
            * no regression scripts or thorough feature/user story list doc
                * we could go through user stories and collect
            * we have some stuff done in testrail, we could get a regression script or tests
            * cypress down
            * original qa members are gone
            * we have unit
            * we have poor monitoring, we have sentry and not much else, so difficult to resolve issues
        * jwt -> gih
            * if we dont do it, we have no support for jwt, especially singe atg team put in a custom java thing for us
            * jwt used everywhere in the app
            * mytime actually developed some custom behavior to use/handle our jwt, would need similar for gih
        * behind on updates including security
        * way behind in project tooling and provisioning
            * we have poor monitoring, we have sentry and not much else
            * bringing it up is very expensive
                * devops now uses completely different tools. this is the last project created using the legacy pipeline a while back using travis and homegrown svar. now we use koala (terraforrm and gitlab)
                * platform team has changed frontend config drastically
                * there would need to be code changes front and back end
                * much easier to start from fresh updated starter kits and copy functionality over
            * if we don't bring it up:
                * its going to mean we fall further behind forever, since we cant make incremental improvements
                * prevents collaboration with other teams, since we're not using same tools
        * front end is already mixed together so extrication means going through all the code anyway, might as well be copying it over to new
        * backend code is also has memberships spilled out a bit, so it has to be combed through
        * some existing issues in previous version
            * pii's that we dont really need to store
    * options
        * 


## **--------- today**



* dan pickering
    * qas dont work here anymore
    * no qa scripts, only testrail
    * custom jwt reader in mytime, they would need to update
    * we cant just keep jwt either because the flag is put in there by some custom java code in atg someone from atg team wrote that is no longer maintained (jwts as a whole are deprecated)
    * "rewriting will be easier than updating jwt to gih"
    * cypress tests had issues and we turned them off a long time ago, so now we only have unit
    * "i think its better to turn it off and just use it as example to build a new one"
    * maintaining it is going to be perhaps uneventful but very difficult anytime anything comes up. its a liability
* loyalty doc
    * study miro boards
    * interviews
        * ruslan kaslan 
            * he was the tech guy during the planning phase and probably made the diagram that edmund showed us (the one eric walked us through)
        * eric
            * [https://lululemon.atlassian.net/wiki/spaces/Loyalty/pages/2683929735/Infrastructure+Repositories](https://lululemon.atlassian.net/wiki/spaces/Loyalty/pages/2683929735/Infrastructure+Repositories)
                * does this chart mean we are or we are not replacing? ^
* memes sunset doc
    * draft with existing ideas
    * interviews
        * patrick lam
        * ivan storck
            * [https://github.com/lululemon/wae-booking-details](https://github.com/lululemon/wae-booking-details)
                * memes frontend ^
            * brij shah: architect
        * mark zehr
        * daniel pickering
        * michael chen
        * marc chaix
    * consult
        * eric
        * lenny
    * considerations
        * if we want to add membership-type classes, or anything else, we should rewrite. basically if we dont rewrite we're stuck in code freeze


## **--------- backlog**



* schedule meets
    * members of other teams in edmund umbrella
        * ramp up on all of them
    * memes sunset
        * jason cornwall (cloud solutions tech stack architect)
            * jwe -> gih token ?
        * memes team again, after jason 
            * estimates
* misc resources to review
    * [https://lululemon.atlassian.net/wiki/spaces/TI](https://lululemon.atlassian.net/wiki/spaces/TI) 
* onboarding checklist
    * [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2667408857/Santiago+-+Engineer+Onboarding+Checklist](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2667408857/Santiago+-+Engineer+Onboarding+Checklist) 
* get walkthroughs
    * 
* org 
    * into lll and calendar
    * all access and links
    * materials
        * miro
        * confluence
        * teams
        * email
        * lulu doc [https://docs.google.com/document/d/1D_FHMXGtTtOBL8Gbv8DdVvkMtWwLITVjfWZmzN1z7rg/edit](https://docs.google.com/document/d/1D_FHMXGtTtOBL8Gbv8DdVvkMtWwLITVjfWZmzN1z7rg/edit) 
        * temp doc
        * recordings
    * lll doc content (everything has loyalty and memes)
        * notes
        * people
        * plan
        * actionables


## **--------- habits**



* 


## **--------- notes**



* general tech resources
    * acronyms [https://lululemon.atlassian.net/wiki/spaces/TI/pages/712151111/Acronyms+Initialisms+and+Terms+Main+List](https://lululemon.atlassian.net/wiki/spaces/TI/pages/712151111/Acronyms+Initialisms+and+Terms+Main+List) 
* loyalty
    * questions
        * transition from memberships
            * we are not using memberships at all right? cause we are reimplementing some of this it seems. its a bit of a rewrite?
            * examples:
                * sign ups and user accounts
                    * maybe not. this could be just GIH. [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1506282556/Membership+101](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1506282556/Membership+101) However, in eric's diagram we were interacting with GIH directly. in miro boards, it looks like the "my account" is a loyalty thing now.
        * tech planning (how do other teams do it? how should it be done?)
            * monitoring for system health and kpis
    * miro boards
        * [https://miro.com/app/board/o9J_l7ELnQw=/](https://miro.com/app/board/o9J_l7ELnQw=/) 
        * [https://miro.com/app/board/uXjVOZXxAOY=/](https://miro.com/app/board/uXjVOZXxAOY=/) 
        * [https://miro.com/app/board/o9J_lpdpUE8=/](https://miro.com/app/board/o9J_lpdpUE8=/) 
* memes
    * temp
        * none of the KT recordings are available (error: doesnt exist)
                * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1558986464/Knowledge+Transfer+for+Q4+2020](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1558986464/Knowledge+Transfer+for+Q4+2020) 
        * 
    * useful things
        * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1558986464/Knowledge+Transfer+for+Q4+2020](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1558986464/Knowledge+Transfer+for+Q4+2020) 
        * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/966298497/Membership+Architecture](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/966298497/Membership+Architecture) &lt;-- events & diagrams
        * 
    * questions
        * (unrelated to sunset, this is for loyalty) why was it decommissioned?
        * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/966298497/Membership+Architecture](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/966298497/Membership+Architecture) 
            * walk though services arch diagrams ^
        * how integrated are Events and Memberships? 
            * does events work without memberships?
            * does keeping events semi-alive mean keeping dead memberships code, or at least keeping a pattern built around memberships?
            * [https://lululemon.atlassian.net/wiki/spaces/ENC/pages/1368628378/Booking+Service+Membership+async+communication](https://lululemon.atlassian.net/wiki/spaces/ENC/pages/1368628378/Booking+Service+Membership+async+communication) 
                * looks like at least some dependency exists ^
            * bookings service requires membership service
                * [https://github.com/Lululemon/digcore-booking-srvc](https://github.com/Lululemon/digcore-booking-srvc) 
            * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1506282556/Membership+101](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/1506282556/Membership+101) 
                * looks like events is just part of memberships ^
        * was membership closed out before?
            * there are confluence pages like "2020 membership cohort closeout actions"
            * there was a "membership 2021 mvp"
        * what are MindBody/MyTime? why not just one of them?
            * it looks like the actual service data (events/bookings/etc..) are maintained by MindBody/MyTime. if so, the service isnt doing all that much? rewrite shouldnt be so bad?
        * what are local vs membership events?
        * what kind of maintenance work do we expect?
    * repos
        * events 
            * [https://github.com/Lululemon/digcore-booking-srvc](https://github.com/Lululemon/digcore-booking-srvc) 
    * confluence spaces
        * membership and events (MEMES) 
            * does not have much.. they just brought "EnC" and Memberships historical spaces together but did not add very much
            * [https://lululemon.atlassian.net/wiki/spaces/MEMES/pages/1903694571/Membership](https://lululemon.atlassian.net/wiki/spaces/MEMES/pages/1903694571/Membership) 
        * membership program
            * historical
            * [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/overview?homepageId=815339568](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/overview?homepageId=815339568) 
        * events & classes
            * historical
            * aka "EnC"
    * close-out plan
        * edmund's doc:  [https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/2625209369/Close+Out+Options+for+Membership+Program+2021](https://lululemon.atlassian.net/wiki/spaces/MBERSHIP/pages/2625209369/Close+Out+Options+for+Membership+Program+2021) 