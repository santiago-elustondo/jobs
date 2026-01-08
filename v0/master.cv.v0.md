### typefirst
* 2024/01 - present

#### oralinx

A dentistry specialist network and consumer-facing portal. The platform supports patient discovery across different types of practices, internal referrals within the provider network, and review-based selection. A core differentiator is its embedded legal architecture, which enforces disclosure guardrails and information-handling constraints required for compliant referrals and insurance-aligned specialist matching.

This was not a feature-delivery engagement but a technical audit, architectural assessment, and documentation-focused consultancy, similar in shape to the Connexis work. Oralynx was a funded startup acquired with the intent to scale, but it remained constrained by siloed knowledge, minimal documentation, and heavy dependence on one or two individuals. Senior technical capacity was effectively unavailable: the same people responsible for day-to-day delivery were also expected to lead architecture, infrastructure, and growth planning, which created both delivery risk and organizational fragility.

The platform ran on Azure, used Kubernetes, and consisted primarily of a React / Node.js stack with legacy Golang components still in the critical path. DevOps maturity was extremely limited: deployments were largely manual, clusters were operated directly, and although some GitHub Actions existed, there was no meaningful pre-production environment strategy. New features were tested locally until release time, creating anxiety around every deployment. Observability was effectively absent, and system understanding lived almost entirely in the heads of a single engineer.

My mandate was to provide senior technical oversight, establish a credible architectural baseline, and produce documentation that made the system legible: how it worked, where it was sound, where it was fragile, what was legacy versus strategic, and how new engineers should reason about it. This included explicit mapping of technical debt, architectural exemplars to follow, deprecated paths to avoid, and forward-looking plans aligned with business growth. The goal was to enable hiring, onboarding, investor confidence, and informed decision-making rather than continued heads-down survival.

Performance had become a visible business issue as traffic increased, particularly front-facing load times driven by inefficient data access patterns and over-fetching. Oralynx used Next.js, but—like Connexis—it was not exploiting the framework’s strengths. Client-side rendering was overused, data fetching cascaded across islands, and multiple components redundantly requested the same data.

I restructured data access to better leverage server-side data fetching, progressive disclosure via islands, and a centralized client-side data service. Shared data was fetched once, earlier, and asynchronously, rather than sequentially gated behind authentication or individual component mounts. Redundant GraphQL queries were consolidated into compound queries, payload sizes were reduced, and data was normalized behind a service boundary analogous to a lightweight Redux-style store. This eliminated cascading load behavior and materially improved perceived performance.

On the infrastructure side, I introduced a branch-based deployment strategy integrated with GitHub Actions and Azure Kubernetes Services. Production deployments remained manual by design, but non-production branches became deployable and testable, eliminating the prior “local-only until release” failure mode and restoring confidence in feature development.

Throughout the engagement, I acted as the senior technical representative in higher-level discussions about platform evolution, safety and legal constraints, feature prioritization, and scalability tradeoffs. The organization needed a credible translator between business needs and technical reality—someone whose reasoning could be validated by short-term external experts or investor technical advisors and whose recommendations were grounded in concrete system knowledge rather than intuition.

The outcome was a stabilized platform, improved performance, materially stronger operational confidence, and a documented technical foundation that reduced key-person risk and made sustainable growth possible.

* significantly increased initial load times for a nextjs application by refactoring targeted component data into server-side. moving suitable components to be async ssr components, and injecting data elements with service cache prepopulation. also consolidated overlapping apollo graph calls independently executed by multiple islands via custom hooks that reduced redundancy and aggregated requests, and cached server-data state centrally as read-only unidirectional store.
* investigate and resolve performance issues with application (full stack React Node Postgres Azure)
* document technical debt and architecture roadmap.
* design and implement features including integrations with dentrix partner system.
* plan and implement alerting system for errors and system health metrics in coordination with customer support team

#### sector growth

This engagement also sat under TypeFirst, but represented a distinct class of work. Sector Growth is a business consultancy founded by former HubSpot sales and client-services professionals. Their role is to support larger HubSpot customers whose operational needs exceed what HubSpot’s core platform and standard services can provide. They advise clients on adoption patterns, workflow design, and migration from existing systems, often operating in parallel with HubSpot sales to de-risk adoption and close larger accounts.

A recurring gap in Sector Growth’s offerings was custom integration work beyond HubSpot’s native capabilities. While HubSpot exposes webhooks, triggers, and a plugin marketplace, many real-world workflows cannot be expressed cleanly within those constraints. In practice, certain data events are unavailable, some workflows require cross-system coordination, and others demand bulk or transactional updates spanning multiple platforms.

TypeFirst was engaged to design and implement custom integration services, most commonly between HubSpot and Shopify, and in one case NetSuite as well. The solution pattern was consistent: introduce a dedicated TypeScript-based integration service that listened to webhooks where possible, performed periodic polling where necessary, and executed workflow-specific actions such as bulk updates, reconciliation passes, or transactional mutations across systems.

These services were deployed independently on Google Cloud (App Engine) and operated as standalone systems rather than embedded extensions. Each engagement typically included a custom React dashboard that allowed operators to inspect data, trigger actions manually, run checks, and observe reconciliation state. Dashboards presented side-by-side views of how a given entity was represented in HubSpot, Shopify, or NetSuite, exposed discrepancies, and allowed controlled synchronization in either direction. Operators could query by object ID, inspect last-checked timestamps, view scheduled reconciliation cycles, and initiate corrective actions.

From a modeling perspective, each integration maintained its own persistent data store, typically MongoDB, acting as a master coordination layer. This database captured associations, extended metadata, reconciliation state, and operational annotations that did not belong cleanly in any upstream platform. The core challenge was representing a single business concept—orders, customers, contracts, or lifecycle stages—that existed in partial and divergent forms across multiple authoritative systems. The integration layer tracked discrepancies between sources, classified event types, scheduled batch consistency checks, and recorded when and how each object was last validated.

Observability was treated as a first-class concern. While cloud-native monitoring tools were available, most operational signals and aggregates were surfaced directly in the dashboards, which were customizable per client. Each deployment was single-tenant, with separate App Engine instances per engagement, although multi-tenancy was explored later in a separate internal product effort.

On the engineering side, I acted as technical lead and senior consultant. I interfaced directly with Sector Growth consultants and, when necessary, with their clients to resolve ambiguities at the technical boundary. I designed the core architecture, authored the framework-level, strictly typed TypeScript code that could be reused across engagements, and implemented large portions of the systems myself. A business-development counterpart handled primary client relationships, while I translated workflow intent into concrete technical designs.

Staffing followed a hybrid model. Domain expertise came from experienced HubSpot consultants, while development capacity was supplemented by contract engineers, primarily from Colombia. I conducted technical interviews, guided onboarding, and provided architectural direction to ensure maintainability once systems went live.

After multiple successful client integrations, this work informed an internal TypeFirst integration hub concept—a configurable, multi-tenant platform for defining reusable integration workflows. While that product did not ultimately ship, the Sector Growth engagements established the architectural patterns, data-modeling approach, and operational tooling that underpinned it.

* architected `@integration-hub` typescript monorepo (shared top-level tsconfig.json) using `yarn-workspaces` with `client` react SPA frontend and `server` nodejs stateless backend application packages. further packages included isomorphic stateless domain logic and models, and a shared `actions` package defining server-side async actions interface, fully typed, with a registry and abstract service class. the isomorphic service interface was extended by both application packages, the server-side package providing implementations and further definitions like injectable dependencies which are implementation details as far as API is concerned. server threw compilation error if not all actions were provided suitable implementations. client did not need to provide specific action definitions, as the client service simply mapped the registered actions into wrapped fetch calls to the server, RPC style. the client automatically derived its methods from the registered isomorphic interface, and provided full typed autocomplete and typed calls. both sides instantiated their own stateless action service implementation, the server side further used the service during boot to declare its express endpoints accordingly, taking each request, parsing, and calling the corresponding action, and sending back serialized return. the base action type definition required that all arguments as well as return types be serializable, so once the services were instantiated, there was no difference when calling an action in either server side or client side, effectively making the server-side actions api a identical type-safe isomorphic callable surface in both application packages.
* data model reconciliation/definition, central postgres with links and authoritative data.
* consult with clients to understand their operational flow, integration needs, and impact metrics.

#### conexis vms

For Conexis, I was brought in to support a Vendor Management System (VMS)—a recruitment and staffing platform used by enterprise clients to manage contingent hiring workflows. The system functions as a recruitment portal through which clients progress roles through intake, candidate review, contract stages, document exchange, and ongoing communication with staffing providers. Staffing agencies operate on behalf of the client, and the platform serves as the shared operational interface.

The engagement was triggered by delivery risk. Conexis relied heavily on an offshore team in Colombia, operating through an agency model. Communication constraints, uneven seniority, and slow execution created concern, particularly with an important enterprise client onboarding approaching. The company wanted to meet immediate deadlines while beginning a gradual transition toward internal ownership, knowledge transfer, and eventually building a local team.

I was engaged to address client-facing technical challenges that required senior-level coordination and architectural oversight. This included acting as the technical representative in discussions with Conexis’ enterprise client and translating external requirements into concrete system changes.

The platform architecture consisted of a NestJS backend and a Next.js frontend, maintained as separate repositories. The backend used PostgreSQL via an ORM and had received more deliberate framework-level design. The frontend, while built on Next.js, was effectively structured as a client-heavy SPA, underutilizing server-side rendering, data-fetching strategies, and caching. This resulted in inefficient loading behavior, cascading client-side requests, and avoidable performance issues. This same pattern later appeared at Oralynx and was addressed in both cases through more intentional use of Next.js features.

Infrastructure and operations were also immature. Although cloud-hosted, deployments were VM-centric and manually operated via SSH. DevOps practices were minimal, and system knowledge was fragmented and poorly documented.

One major responsibility was implementing enterprise single sign-on with the client’s Azure Active Directory, using OAuth / SAML-based flows. This work exposed a broader issue: no one on the team had a clear understanding of the existing authentication system. The platform used a simple, custom key-signing approach with credentials stored in the database, but it had never been formally reviewed or documented. I audited this system, documented its behavior, and established clear boundaries to safely integrate external identity providers.

Another critical initiative was external job feed ingestion. The enterprise client already distributed job postings via RSS feeds to third-party channels, and Conexis needed to ingest those feeds and represent the postings as first-class entities within its own system. I designed and implemented a standalone Node.js ingestion service, deployed independently on Azure, which continuously monitored RSS feeds, detected new and updated postings, normalized the data, and mirrored it into the platform’s domain model. This required adapting the schema to support source attribution, idempotent updates, and reconciliation semantics.

Reporting was a further area of concern. Existing reporting amounted to raw data exports from PostgreSQL tables, some of which contained semi-structured JSON. The schema had evolved organically without a clear domain model. I conducted extended discovery with stakeholders to understand recruiting lifecycle concepts and implicit relationships across entities, then translated that understanding into a reportable data model and backend API endpoints suitable for a modern frontend.

Finally, I produced a clear assessment of technical debt and ownership gaps. It became evident that the system had originally been built by more senior engineers at the agency and later handed off to junior developers without sufficient context. Core framework decisions, particularly on the frontend, were no longer well understood. My role was to impose structure: documenting what existed, identifying fragile or legacy areas, and providing leadership with a credible technical baseline for future refactors, hiring, and platform evolution.

The outcome was restored delivery confidence for the enterprise client, clearer architectural ownership, and a platform that leadership could reason about and evolve deliberately rather than defensively.

* worked with offshore development team and local business development team to reach consensus on requirements, insights, and estimations. Supported hiring efforts, identifying needs and assessing candidates.
* undertook requirements discovery effort in collaboration with our business leadership and with client technical leadership to design and implement critical system integrations for a full-stack React NestJS and Postgres system. Built out and deployed high observability automation features.
* oversaw all development timelines, reviewed pull requests, and led technical discussions, training sessions, and technical escalations for our development team
* worked with development team to build out functionality such as single sign-on support with Azure Active Directory, report-generation tools for client users, integrations with client vendors.

#### appliance info
* Gcp, redux, mongo, graphql
* Appliance Info is a business-facing software-as-a-service for appliance retail stores.
* Lead small agile product development team (3 dev). Conduct interviews, provide technical training and support, advise CEO regarding costs and roadmaps, and lead design and implementation.
#### fliporders
#### crafty
#### Elephant Space Toronto?
* Technologies: React, php, mysql, sass, wordpress
* Led Elephant Space's development teams in building and maintaining their custom Wordpress and React (JS) platform.
* Discussed ES's website and general technology needs with the board of directors and media team, and undertook solution design and implementation.
* Elephant Space is a non-profit organization providing drop-in after-school programs.
#### firstdate?

### rangle.io
* **2022/11 - 2024/01**
* qa to dev transition cohort
* 10? reports (jr/sr devs, qas, solutions arch). help them grow and demonstrate skills.
* community building, presentations at meetups
* bench work, R&D, website, internal knowledge capture/sharing (dev presentations).
* supported, approved, supported, reviewed, promoted demos / open source / articles / community presenetations/appearences / internal knowledge dissemination (lunch & learn) / bench work (outsider documentation projects, knowledge capturing/sharing, technical mentorship) / R&D projects according to our broader offerings and directional mandates. 
#### movebuddy
#### momentive (aka: survey monkey)
* led my team in bundle analysis task to significantly shrink application bundle sizing with minimal code changes and virtually no functional changes, targeting adequate tree-shaking using better import statements with slashes, library usage audits, and webpack bundler plugin settings. used bundle analyzer to investigate, and to demonstrate reduction. one of my recruits on the team used what we did together (myself teaching them) and their experience to write an article about the topic.
* momentive with leah bundle analyzer reduce bundle size.
* high-pressure situation, some devs were falling out (leah, thomas)
#### get ahead
* led agile 4-dev team as sr technical resource & point of contact to develop an embedded react client app to support online therapists in conducting their sessions and generating regulation-compliant records from the recorded meetings using ai-assisted features in-session. we had little clarity going in, with significant discrepancies between client-provided requirements and design mockups and a tight timeline, as well as technical clarity regarding ai service intended flow and delivery pipeline requirements for embedding onto client's flutter app. devs were anxious and uncertain. worked it all out with client, guided team to success & client re-hire for a larger greenfield project (adjacent content platform for therapist practitioners).
* project was a micro-frontend React SPA delivered as CI build artifact and mounted within flutter client app (runtime host injecting serialized args, react spa internally communicates with their backend for frontend to interact with agentic generation rag engine which uses specific serialized arguments for templates, user insight requests, and generated sections. practitioner interactions and live transcript guide record creation)
#### jet blue
* jumped into early-stage project for established client (jet blue) to boost project confidence (both client and team) by supporting discussion/work/spikes as senior technical resource. the project mandate was creation of a modern and centrally maintainable design system to support a large suite of consumer-facing applications. the idea being to define the brand design elements in one place and achieve a consistent user experience across the client's entire user-facing web surface, which was distributed across many different product teams and technologies such as react, angular, jquery and even legacy backend-framework applications in asp.net and java springboot using native web components as the core design system. we architected a monorepo with our raw web components as our core (spiked monorepo integration and authoring using lit, stencil, bareback no-lib, etc. finally chose lit for this project, according to client feedback), with separate packages compiling react and node typescript packages. the core package was delivered not only as a private npm importable (similar to react and angular), but also via cdn, allowing very easy importing onto any project using html tags, and use via html tags. presented our learnings about the power of web-components for application-agnostic design systems for web clients at professional community event, on behalf on rangle.io, recorded and available online.
#### endi
#### rangle website
* improved ui smoothness of ui hero/branding component that took images and cut them into configured geometric shapes. we used this for our website, and a client project where they liked our website look. previously this was done using a javascript computation that didnt resize smoothly, requiring a render constantly to keep updated, listening to media queries. i updated it to utilize css cutting via svg masked paths, so we could easily export the shapes as svg from figma and upload them into the CMS (sanity.io) config which the component received via our design-system integration framework layer, as we tried to always do where possible, so that our design systems where flexibly customizable on the fly via CMS. the component could be safely memoized, as it was now stateless and fully smooth as everything was rendered as css. we could even animate the shapes images using svg animation attributes.

### lululemon
* engineering lead
* 2021/11 - 2022/11
* Built, deployed, and monitored horizontal featureset to support a loyalty initiative onto a large React/Node application distributed across multiple repositories and orchestrated via Webpack federated modules system
* architected new repository for the loyalty engineering team, which had to bring loyalty features horizontally to the whole application, in checkout, product pages, search pages, etc. these were microfrontend repos managed by different teams, whos repos we would have to make PRs for to import our library (which were safe, error-bounded, self-contained components with their own sentry events tracking, google analytics hits, and feature flagging which our team controlled) and mount our components onto their pages. in order to do our own development and produce demos, our monorepo packages included git submodules of the host microfrontend repos. this way we could import our final library directly using a live development build of the library package, and we could predict how peer dependencies and bundles of the target hosts would be impacted when our library was added.
* lululemon's engineering dept was large and sophisticated. they used a very sophisticated custom contentful-cms integration framework that allowed for radical content management via contentful. they organized their front-end into numerous team-owned micro-frontends and libraries. the teams had their own release cycles, and the apps came together on the client using webpack remote federated modules system. the primary contributor of the webpack federation system was alan? jackson, and he was our lead architect. our team worked on the loyalty feature and we had to create a component library which carries its own sentry alerting, events, and contentful data subscriptions, and feature flagging, and were imported and integrated into other teams repos, those teams had to approve our PRs to their repos to take in and use our components in their own pages. 
* get arch runway / implementation plan approved by other teams, who would have to import and mount our components, and they had to be ok, especially checkout team which had tight oversight and security compliance requirements.
* use react context / error boundary wrapping for all our exported components, only taking specifically typed serializable props from parent component.

### vaco
* 2020/06 - 2021/11
* Technologies: Gcp-networking, terraform, k6, typescript, gcp-pubsub, gcp, socket.io, redux , mongo, redis
* Led and supported the assessment and delivery efforts for Vaco Toronto's consulting engagements. Gathered requirements and KPIs, reached consensus on solutions and roadmaps, worked with the recruiting department to assemble teams, and provided support throughout the engagement in both technical and organizational capacities, addressing feedback and escalations from all corners.
* Led the Avaya Spaces project, a suite of globally-distributed enterprise communication and collaboration tools, supporting a large array of client devices.
#### avaya
* to enable new react-native client app team & formalize front-end data model (including encryption/server api layer & business domain), architected and delivered typescript sdk package repo to replace & deprecate existing web client parts & be used also by new react native client. avaya client-side sdk had to make requests to various independent regional cluster deployments depending on company data location & maintain subscriptions to multiple socket conns, etc. our platform-agnostic client-side DAL importable library abstracted this away, taking, for example, target user for message, and either reading from there or querying global federation service (which held ony metadata) to learn that user's company's data location as configured by their company's admin.
* designed & impemented, in collab with my team (5 eng) and client's engineering leadership (vp of tech & his people), a nodejs service abstration for real-time socket communication that "mocked" server-side socket.io object-oriented api (socket.emit(), socket.userdata = {..}, io.on('connect', cb)). it internally continued to use socket.io with redis pub-sub adapter when both users' companies resided (as per company admin config) in the same geographic full-stack deployment region, since the socket connections would both be present within one of the cluster instance connected to our redis instance (single per cluster). otherwise, the message would be encrypted & published to our google pubsub (global), decrypted by the target region cluster (encrypted  using target private key, publisher public key) and emitted using local socketio redis. the api interface remained largely unchanged from socketio, requiring very little change in server code to enable geo-distributed transmission compliant with data sovereignty/residency requirements of regional laws such as GDPR/california.

### avanade
* 2018/10 - 2020/06
* roles: senior software consultant -> technical lead
* Technologies: Angular, typescript, sql-server, azure, mocha, node, jest, microservices, aws, graphql, net, docker,enkins, redis,openshift, mongo,selenium
* Led agile delivery teams (4-6 developers, 2 QA, 1 Scrum Master) in technical planning and implementation, providing guidance and support, handling technical escalations, and converting requirements into scalable technical solutions that fit client timelines and expectations.
* Develop horizontally-scaling (distributed) NodeJS microservices to serve as backend for the Telus MyWifi app, which interoperates with a number of downstream systems and devices to allow users to configure and monitor their home WiFi.
* Audit performance, discuss findings and solution proposals with client architecture leads, and undertake improvements to core libraries for the Mortgage * * Cadence Platform, an enterprise fintech application used by the largest mortgage lenders in North America.
* Designed and delivered in-depth multi-day training programs for client organizations on the subject of performance profiling and optimization of web apps, using modern client-side JS frameworks (primarily Angular and React).
#### advanced react workshop
#### telus digital 
#### mortgage cadence platform (accenture)
* large angular application with many independent teams contributing. i was asked to analyze poor responsiveness issues in pages with large grids or animations, jankiness. rearchitected grid components to use a unidirectional state cycle, and separated them into 2 separate components, an orchestrator/state-machine smart stateful wrapper api surface and an internal OnPush UI renderer with optimization logic in its attribute setters to minimize change detection frequency and cost. also identified numerous cases of intervallic javascript activity that could be converted into css code in the case of visual animations, or alternatively executed "outside of angular". used performance flamegraphs with ui snapshots to demonstrate radical responsiveness improvements.

### rangle
* 2017/04 - 2018/10
* Technologies: React, node, redux, mongo, typescript, lerna, graphql, angular, dom-service-workers, circle-ci
* Work with agile teams that analyze, design, and implement solutions using the best modern tools and practices, bringing full-stack JavaScript expertise to consulting and development. Assist clients in upgrading and modernizing their software, as well as getting new high-quality, engaging products to market quickly, streamlining the Agile flow to bring the most value out of every engagement.
* Augury - Angular Devtools: Augury is an open-source Angular debugging and profiling toolkit developed and maintained by Rangle.io in partnership with the Angular team.
* Atlas 
  * Designed and implemented new features on React/Redux/Node/Mongo enterprise staffing portal. 
  * Investigated possible new features and enhancements requested by stakeholders. Presented time/cost estimations, recommendations and progress reports to COO. 
* Vitamin Shoppe – e-Commerce Migration: enterprise client migration from AngularJS 1.6 to Angular 4.
* KagenAir: Performance audit followed by bottleneck resolutions on iOS/Android application written in AngularJS (1.6) running on Apache Cordova, specifically WebRTC video conferencing feature utilizing native Cordova plugins.
#### augury
* primary maintainer of the official chrome devtools extension for angular. worked with community to resolve issues and upgrades for new angular version releases. issues often included performance as angular state was transmitted to chrome extension in a serialized state, and there were interactions with other chrome extensions to consider. so frequently inspecting stack traces and bottlenecks, and implementing complexity reduction techniques. developed and architected augury-labs extension to do performance profiling on angular applications, showing flamegraphs and heatmaps mapping to components.
#### augury-labs
#### atlas resourcing
#### vitamin shoppe
#### kegan air
* KagenAir: Performance audit followed by bottleneck resolutions on iOS/Android application written in AngularJS (1.6) running on Apache Cordova, specifically WebRTC video conferencing feature utilizing native Cordova plugins.

### influicity
* 2015/05 - 2017/04
* Technologies: React, php, my-sql
* Influicity is a platform that brings together social media influencers and marketers wishing to showcase their products. We streamline the process from networking, to content review, to analytics.

### the cube school of technology
* Technologies: React, node, ecmascript,unity
* The Cube School of Technology offers a creative learning environment where technology and design converge.
* I teach ReactJS, JavaScript, and game development courses.
* I develop course content and materials, and chat with prospective students about their interests.


