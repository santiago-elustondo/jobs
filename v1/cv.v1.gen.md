# Santiago Elustondo


**Senior Frontend Platform Engineer / Technical Lead**  
Toronto, ON · TypeScript / React / Frontend Infrastructure


---


## Profile


Platform-oriented frontend engineer with 10+ years building, stabilizing, and scaling **large React and JavaScript systems** across enterprise and high-growth environments. Repeatedly trusted with **horizontal platforms**: monorepos, shared SDKs, federated micro-frontends, build systems, and developer-experience infrastructure used by **hundreds of engineers**.


Strengths lie in **making large frontend organizations predictable**: dependency hygiene, performance ceilings, correctness boundaries, release safety, and tooling that multiplies engineering velocity rather than constraining it. Comfortable operating where product delivery, platform architecture, and organizational mechanics intersect.


---


## Core Technical Focus


* Frontend Platforms & Monorepos (Yarn / pnpm / Lerna, shared tsconfig, dependency governance)
* React at scale (context isolation, error boundaries, hydration/SSR boundaries, federated modules)
* Build & Tooling (Webpack, Module Federation, Rspack evaluation, bundle analysis, CI)
* Performance Engineering (bundle size, main-thread scheduling, rendering correctness)
* Developer Experience (standards, internal SDKs, documentation, enablement)
* TypeScript as an architectural tool (contract enforcement, shared domain models)


---


## Experience


### Blast Engine *(Jan 2024 – Sept 2025)*


**CoFounder / Principal Engineer**


Founder of an independent consulting practice focused on **frontend platform architecture, monorepos, and type-driven system design**. Acted as senior technical authority across discovery, architecture correction, and delivery stabilization for multiple clients.


* Designed and implemented **large TypeScript monorepos** supporting React frontends and Node backends with shared domain contracts and compile-time enforcement.
* Built **platform-level abstractions** (typed RPC layers, shared SDKs, action registries) that eliminated class-of-error failures and reduced cognitive load for feature teams.
* Led frontend performance remediation in Next.js/React systems suffering from hydration-gated SPAs, excessive client fetch fan-out, and unstable data layers.
* Delivered DevEx improvements (tooling, scripts, conventions, documentation) that allowed teams to scale without senior engineers becoming bottlenecks.
* Regularly translated ambiguous business workflows into enforceable technical contracts and extensible platform primitives.


---


### Rangle.io *(Nov 2022 – Jan 2024)*


**Technical Director — DevEx**


Senior technical leader responsible for **frontend platform strategy, performance engineering, and developer experience** across multiple enterprise engagements.


* Led ~10 engineers across senior/junior roles, QA-to-dev transition cohorts, and solution architects.
* Acted as escalation point for platform-level frontend issues: build instability, performance regressions, architectural drift.
* Sponsored internal standards, documentation systems, and technical enablement initiatives.


**Momentive (SurveyMonkey)**


* Reduced parsed JS bundle size by ~50% with minimal code change using systematic dependency tracing and import hygiene.
* Established a **repeatable bundle-analysis methodology**.
* Mentored engineers through publishing performance engineering articles.


**JetBlue**


* Early architecture for a **framework-agnostic design system** using Web Components.
* Evaluated Lit vs Stencil vs no-framework approaches; converged on Lit.
* Designed delivery via npm packages + CDN artifacts.
* Presented architectural findings and implementation tradeoffs at public technical talks and community events representing Rangle.


---


### Lululemon *(Nov 2021 – Nov 2022)*


**Engineering Lead — Loyalty Platform & Horizontal Frontend Architecture**


Engineering lead for lululemon’s **Loyalty initiative**, responsible for delivering a **horizontal frontend feature set** across a highly federated React ecosystem.


lululemon’s frontend was composed of many **team-owned micro-frontends**, assembled via **Webpack Module Federation**, with independent release cycles and strict stability requirements (especially checkout).


Key platform contributions:


* Architected a **library-first loyalty platform** consumed by many MFEs rather than embedded feature code.
* Designed exported React components to be:
  * fully **self-contained**
  * **error-bounded** (error boundaries, zero host blast radius)
  * strictly typed with **serializable props only**
* Implemented **library-level observability**:
  * loyalty-owned Sentry projects
  * analytics and experimentation hooks
  * attribution by host surface and component
* Standardized **feature flagging and rollout** inside the loyalty boundary, enabling safe deploy-before-enable workflows across teams.
* Designed local development fidelity via **git submodules of host MFEs**, enabling in-situ testing of bundle impact, peer dependencies, and federation behavior before downstream PRs.
* Navigated architectural approval with risk-sensitive teams (checkout), aligning on security, performance, and failure-mode containment.


Outcome: loyalty functionality became **incrementally adoptable, safe by construction**, and operable across one of the most complex frontend environments in retail.


---


### Vaco *(Jun 2020 – Nov 2021)*


**Director of Technical Solution Delivery / Technical Lead**


Senior delivery authority for Vaco Toronto consulting engagements, spanning discovery, architecture, execution, and escalation.


* Led technical assessments of large JavaScript systems; produced modernization plans centered on **DX, dependency hygiene, and performance ceilings**.
* Established delivery cadence across multi-repo environments: discovery → design → implementation → review.
* Reduced key-person risk through documentation, standards, and reproducible workflows.


**Avaya — Avaya Spaces**


* Led platform architecture for a **globally distributed React/Node collaboration system** under strict data residency constraints.
* Architected a **platform-agnostic TypeScript client SDK** used by web and React Native clients.
* Designed a **socket abstraction** preserving socket.io ergonomics while enabling cross-region messaging via Redis + GCP Pub/Sub.
* Led release governance, QA strategy, and Terraform-based regional expansion workflows.


**Frontend Platform — UWF**


* Built a React application that compiled into a **reusable Web Component**, enabling embeddable UI without coupling hosts to implementation.
* Defined dual-mode build/run workflows (standalone app vs WC).
* Refactored shared UI and Redux state packages for cross-surface reuse.


---


### Avanade *(Oct 2018 – Jun 2020)*


**Senior Consultant / Technical Lead**


Senior technical lead embedded in large enterprise programs.


* Led Angular performance remediation in a large fintech application:
  * re-architected grid components into orchestrator + OnPush renderer
  * eliminated change-detection storms
  * moved animation work to CSS / outside Angular zone
* Built horizontally scalable Node.js microservices for Telus MyWiFi.
* Delivered multi-day **Angular & React performance workshops** grounded in real production profiling.


---


### Rangle.io *(Apr 2017 – Oct 2018)*


**Software Developer**


Full-stack consultant and **primary maintainer of Augury**, the Angular DevTools extension.


* Maintained framework-level tooling used by the global Angular community.
* Designed Canary release channels and performance-safe instrumentation.
* Built early monorepo experience (Lerna/Yarn) in open source.
* Delivered SEO-critical Angular prerendering for The Vitamin Shoppe, producing measurable traffic recovery.