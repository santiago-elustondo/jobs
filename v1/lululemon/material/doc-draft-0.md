
* doc_structure
    * overview
        * loyalty is holistic
            * loyalty is for creating a deeper connection with user, we want to be there with them all the time, encouraging them and making them feel appreciated and rewarded.
            * this is true even before a guest has made an account, a primary goal of loyalty is user acquisition, we want to invite the user at all the critical junctures, always extending an invitation to join the club
        * loyalty appears in many forms, mostly injected into existing views
            * in order to be ever present and ready to welcome a new lululemon patron or to support and encourage user, the loyalty feature must appear, in unobtrusive but dependable way, as part of numerous user interfaces, adjusting its message and presentation to match context
            * to accommodate a variety of contexts, loyalty UI takes the form of
                * promo pages, messages, banners, and prompts, designed to inform the user of our exciting program, usually in strategic locations within existing views 
                * as well as attractive and intuitive tools to view and manage one's rewards and offerings
        * challenge: how should it be built
            * the pattern to follow for implementation of a holistic client-side feature is not obvious. we have 2 general patterns. 
                * mfes
                    * the lll website is divided into various apps served independently (referred to as MFEs) which blend together via common ui elements, each housing a subset of the site's pages. (ecom-web-app, ecom-checkout-client, ecom-payment) 
                    * features that can be fully expressed within a discrete subset of pages are well accommodated by this pattern, and are entirely housed within one of the MFEs and its corresponding repository.
                    * Examples: 
                        * product browsing -> ecom-webapp (ecom-pdp)
                        * account management -> ecom-checkout-client
                        * events and classes -> wae-booking-details
                    * [DIAGRAM] 
                    * benefits for these features
                        * organizational model is clear and simple, as teams, working on different features, under a tech manager own an mfe, its QA, metrics, and maintenance.
                        * they are vertical slices fully contained within a single package within a single mfe. everything they need is there, (services, etc.) because they are fully contained. maintenance is nice. KT and onboarding is nice
                        * mfes iterate independently from each other, which means that the teams supporting features houses there must only organize internally
                    * challenges 
                        * hit a wall when try to extend the reach of a feature horizontally. 
                            * authentication / accounts stuff wants to be holistic but isnt today. 
                                * currently there are no invitations to create account when browsing around. to invitation to create account when checking out. there is only a header thing sometimes that prompts you to signup, but its small. i guess it wasnt so in your face before because it didnt have much to offer. we want to make a more enthusiastic show
                            * but the technical limitations are evident:
                                * auth actions requires redirect. 
                                * wae-partials fetches auth user data manually, hardcoding endpoint and fetch params
                * libraries
                    * npm modules
                        * these can be shared across mfes, but must be ultimately consumed or mounted by one of the mfes
                        * [DIAGRAM]
                        * example: ecom-pattern-library
                            * basic ui, no dependencies
                        * example: wae-partials (meganav, footer)
                            * (deprecated injection method is not a relevant alternative)
                            * fully self sufficient. complex components but self contained. all IO is hardcoded in its own way, endpoints, graphql queries: auth, analytics, launchdarkly (kind of duplicate), my-bag.
                                * thankfully these are all simple, so the duplication / maintenance isnt so bad.
                            * only dependency is ecom-pattern-library does not consume 
                    * federated/remote modules
                        * similar idea, but it gives you a bit more iterative velocity at the cost of some added underlying complexity.
                        * support for remote modules is universal as far as we're concerned, but still a bit immature
                        * peps is a holistic thing, and it uses federated modules
                            * peps is very independent, aims to be the only consumer of analytics tracking data and personalization endpoints, does not share service instances or state with any other module, and has no dependencies
                    * the organizational model here is a bit more elusive, since there are multiple layers, and if the library team is not also contributor to the consumer project, there must be collaboration between the teams of either side of the library API. 
                    * in order to minimize collaboration overhead, we strive towards a component-level ownership model. Ideally, this means a consumer-agnostic library that produces no side effects. 
                        * [https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP](https://lululemon.atlassian.net/wiki/spaces/PEPS/pages/2633171048/MultiTeam+Delivery+Component+Level+Ownership+WIP) 
        * what about loyalty
            * loyalty's promotional UI extends horizontally across mfes, appearing in many different views across the site. given today's wireframes we have: ecom-web-app, ecom-checkout-client, wae-partials.
                * a significant portion of the material is shared across the mfes. modals, links, etc.
                * this might suggest a library approach, however...
            * the core loyalty functionality is also deeply bound up with accounts/profile. one could go as far as calling it an extension of the accounts/profile feature. we even share some core KPIs like user acquisition
                * user accounts and their corresponding loyalty data are bound logically at the entity layer, so it makes sense to use adjacent or shared services.
                * all of loyalty's interactive and data-driven ui components are currently envisioned side-by-side a user's profile and wishlist in ecom-checkout-client
                * in fact, today's product vision includes a shared auth action modal usable outside of ecom-checkout-client, to be integrated as part of the loyalty recruitment flow. This means refactoring core parts of ecom-checkout-client.
                * so, in contrast to what we noted earlier with loyalty's user acquisition material, when it comes to loyalty's core functionality, the close dependency on accounts, the opportunity for harmonious resource sharing, and the confinement of all rich loyalty UI to views existing within ecom-checkout-client, make a strong case for implementation within the ecom-checkout-client mfe
            * *options*
                * *pure library *
                    * *core functionality will be difficult because we would have to encapsulate our own services, which means refactoring or duplicating, and then having issues with multiple requests, etc... or else depend on excessively complex services as parameters, which defeats the purpose of component-level ownership and*
                * *HYBRID*
                    * *we are both sides of the library api, efficient*