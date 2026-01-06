# Santiago Elustondo

**Senior / Lead Full Stack Engineer**  
Toronto, ON · On-Site / Hybrid / Remote  
santi@blastengine.ai · (416) 662 8602
TypeScript · React · React Native · Node.js · GraphQL · Distributed Systems

---

## Profile

Senior full-stack engineer and technical lead with **10+ years of experience** delivering **production-critical, customer-facing web and mobile systems** in enterprise and high-growth environments. Proven ability to operate across **frontend, backend, and platform layers**, leading teams through ambiguous problem spaces while remaining deeply hands-on. Strong record of stabilizing complex systems, improving performance and reliability, and mentoring engineers in modern JavaScript/TypeScript practices. Most effective in product-oriented teams where collaboration, scalability, and long-term system health matter.

---

## Core Technical Competencies

**Frontend & Mobile**
- React, React Native, Next.js, Angular
- Mobile-first, responsive UI architectures
- State management (Redux and derivative patterns)
- Frontend performance profiling and optimization

**Backend & APIs**
- Node.js (Express-style services)
- GraphQL and REST API design
- Authenticated, multi-tenant systems
- Realtime and collaboration workflows

**Data & Infrastructure**
- SQL & NoSQL databases (Postgres, MongoDB, Redis)
- Cloud platforms (AWS, Azure, GCP exposure)
- Containerized services, CI/CD pipelines
- Observability, logging, and production monitoring

**Engineering Leadership**
- Feature ownership and system stewardship
- Code review, mentoring, and technical onboarding
- Agile delivery in cross-functional product teams
- Root-cause analysis and production incident response

---

## Professional Experience

---

## Blast Engine Inc. (TypeFirst Consulting)

**Founder / Technical Consultant**  
*Jan 2024 – Present*

Founder of a hands-on consulting practice focused on **designing, modernizing, and stabilizing full-stack SaaS systems**. Embedded with client teams as a senior engineer and technical lead, balancing architecture with direct implementation.

- Designed and implemented **TypeScript/Node.js backends** and **React frontends** for B2B SaaS platforms, with emphasis on maintainability and operational clarity.
- Led system decomposition efforts: clarifying domain boundaries, API contracts, and data ownership to reduce coupling and long-term risk.
- Owned production issues end-to-end, from initial diagnosis through remediation and preventative architectural changes.
- Partnered closely with product managers and designers to translate ambiguous requirements into concrete, incremental delivery plans.
- Mentored client engineers through structured code reviews, pairing, and architectural guidance, raising overall team effectiveness.

---

## Rangle.io

**Technical Director / DevEx Lead**  
*Nov 2022 – Dec 2023*

Senior technical leader responsible for **engineering quality, developer experience, and team growth** across multiple client engagements and internal initiatives.

- Led and mentored **~10 engineers** across seniority levels, including QA-to-developer transition cohorts.
- Acted as escalation point for complex frontend and full-stack issues, particularly around performance, build systems, and architectural debt.
- Drove internal R&D, knowledge-sharing, and technical standards through talks, internal documentation, and hands-on support.

### Selected Engagements

**Momentive (SurveyMonkey)**  
- Led a production initiative to **reduce frontend bundle size** with minimal functional change.
- Performed dependency and import-path audits, refined bundler configuration, and validated results with bundle analysis tooling.
- Demonstrated measurable improvements and coached team members to independently apply the techniques, culminating in published technical learnings.

**Get Ahead (Healthcare / Therapy Platform)**  
- Technical lead for an **embedded React application** delivered as a micro-frontend and hosted within a Flutter mobile application.
- Built clinician-facing workflows supporting session management, collaboration, and AI-assisted documentation.
- Navigated unclear requirements, regulatory constraints, and tight timelines through structured technical leadership and close product collaboration, resulting in a successful delivery and follow-on work.

---

## Lululemon

**Engineering Lead — Loyalty Platform**  
*Nov 2021 – Nov 2022*

Engineering lead and technical authority for a **horizontal loyalty initiative** spanning a large, federated React/Node ecosystem composed of many independently owned micro-frontends assembled at runtime via **Webpack Module Federation**. Operated at the intersection of **platform architecture, hands-on delivery, and cross-team coordination** in a security-, compliance-, and performance-sensitive retail environment.

### Platform Scope & Organizational Context

- Lululemon’s frontend architecture consisted of **dozens of team-owned micro-frontends**, each with independent release cycles, assembled client-side via Module Federation.
- Content and presentation were heavily driven by a **customized Contentful-based CMS framework**, enabling dynamic content orchestration at scale.
- The loyalty initiative required **horizontal integration** across checkout, PDP, search, account, and navigation surfaces—many of which were owned by teams with strict quality, security, and stability constraints (notably checkout).

### Loyalty Platform Architecture

- Designed and established the **Loyalty component library** as a first-class platform primitive rather than a feature-specific code drop.
- Defined a strict **component-level ownership and isolation model**:
  - Host applications passed only **typed, serializable props**.
  - All internal state, side effects, data fetching, and integrations were fully encapsulated within the loyalty library.
  - No implicit coupling to host routing, state, or lifecycle assumptions.

- Implemented a lightweight internal framework layered around exported components, providing:
  - **Service provisioning via React Context** for auth state, feature flags, analytics, and CMS-driven content.
  - **Mandatory error boundaries** wrapping every exported surface, ensuring runtime failures could not cascade into host MFEs.
  - **Centralized Sentry instrumentation**, automatically tagging errors with host application identity, component name, and execution context to enable cross-repository production triage.
  - **Feature flagging and controlled rollout** (LaunchDarkly) baked into component wrappers, allowing loyalty-owned deployment strategies without requiring host-team releases.
  - Consistent analytics and event emission, ensuring loyalty behavior could be measured uniformly across disparate surfaces.

### CMS & Content Integration

- Integrated **Contentful-driven content models directly into the loyalty library**, aligning with Lululemon’s highly customized CMS abstraction layer.
- Enabled content editors to adjust copy, layouts, and promotional messaging without requiring redeployment of host applications.
- Balanced dynamic content flexibility with strict runtime safety and type guarantees at the component boundary.

### Development Workflow & Integration Strategy

- Architected a development workflow that mirrored real production conditions:
  - Loyalty monorepo included **host micro-frontend repositories as Git submodules**.
  - Allowed the loyalty library to be developed and tested against **live host builds**, rather than mocked shells.
  - Enabled early detection of:
    - Bundle size and dependency impact.
    - Peer dependency conflicts.
    - SSR / prerendering behavior differences.
    - Runtime integration edge cases specific to each host.

- This approach significantly reduced downstream integration risk and increased confidence during cross-team PR reviews.

### Cross-Team Coordination & Governance

- Worked closely with checkout, accounts, platform, and analytics teams to secure **architectural and security approvals**, particularly around:
  - Authentication and authorization boundaries.
  - JWT and session transitions across MFEs.
  - Analytics event ownership and data protection constraints.
- Authored and circulated **architecture proposals and integration guidelines** to align expectations across teams with differing priorities and risk tolerances.
- Served as the primary technical point of contact for loyalty-related questions across the broader frontend organization.

### Legacy System Evaluation

- Led technical investigations into legacy Membership / Events systems.
- Produced concrete recommendations to **rewrite rather than incrementally upgrade**, citing:
  - Tooling and dependency obsolescence.
  - Insufficient monitoring and observability.
  - QA fragility and regression risk.
  - Long-term maintenance and opportunity cost.
- Presented findings to engineering leadership to inform roadmap and investment decisions.

### Communication & Enablement

- Authored internal documentation and **architectural walkthroughs** explaining federation strategy, component isolation, observability, and error containment.
- Presented **quarterly demos** showcasing loyalty integration patterns, rollout strategies, and lessons learned for broader adoption.

### Key Outcomes

- Loyalty features shipped horizontally across **multiple business-critical surfaces** without destabilizing host teams’ release cycles.
- Integration risk materially reduced through enforced isolation, observability, and centralized control.
- Established a scalable, repeatable model for cross-team feature delivery within a highly distributed frontend organization.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Senior delivery and technical authority for complex consulting engagements, operating across **architecture definition, hands-on system design, escalation management, and team leadership**. Worked directly with client engineering leadership, product stakeholders, and Vaco recruiting to assemble and guide teams, while remaining deeply involved in the most technically risky areas of each platform.

### Platform Architecture & Distributed Systems Leadership

* Served as technical lead on large-scale, **globally distributed collaboration platforms** with strict **data residency and sovereignty constraints**, requiring architectural guarantees rather than policy-only enforcement.
* Led the design of **multi-region system boundaries**, separating global metadata from regionally constrained data, ensuring that readable-at-rest user data never crossed jurisdictional boundaries while still supporting cross-region collaboration.
* Designed and reviewed **geo-aware API routing strategies**, enforcing correct region selection at the client and service layers, and eliminating accidental cross-region reads or writes by construction.

### Real-Time Systems & Messaging Infrastructure

* Led architecture and implementation of a **unified real-time messaging abstraction** that preserved existing socket-based programming models while enabling compliant cross-region communication.
* Designed server-side abstractions that:

  * Maintained local real-time delivery via **socket.io + Redis pub/sub** within a region.
  * Enabled cross-region delivery via **encrypted payloads over global pub/sub**, decrypted and re-emitted within destination regions.
* Defined the **state-of-the-world model** for distributed sockets: connected clients, subscriptions, region-specific public keys, and point-of-contact routing, enabling deterministic message delivery and debuggability.
* Balanced backward compatibility with distributed-systems correctness, allowing large existing codebases to adopt geo-distribution with minimal business-logic changes.

### Client SDKs & Frontend Platform Enablement

* Architected a **platform-agnostic TypeScript client SDK** consumed by multiple frontend surfaces (web and React Native), consolidating:

  * Region discovery and routing
  * API endpoint selection
  * Websocket connection orchestration across multiple regions
* Encoded multi-region complexity behind stable domain-level APIs, preventing feature teams from duplicating routing, subscription, or federation logic.
* Enabled frontend teams to reason in terms of **business intent** (target user, space, or resource) rather than infrastructure topology.

### Delivery Governance, Release Engineering & QA

* Owned delivery mechanics for multi-repo, multi-team initiatives under tight timelines.
* Defined and enforced:

  * Clear ownership and escalation paths
  * PR visibility and review discipline across parallel workstreams
  * Structured discovery → design → implementation → validation flows
* Designed release strategies that acknowledged backend coupling realities, using:

  * Dedicated validation deployments
  * Coordinated regression testing rather than fragile feature-sliced releases
* Integrated E2E test execution into scheduled pipelines (non-blocking), establishing triage workflows that converted failures into actionable engineering work.
* Led validation of **new-region provisioning flows**, coordinating Terraform-based infrastructure creation, service deployment, configuration enablement, and controlled exposure.

### Performance, Data-Layer & Reliability Engineering

* Led investigations into production performance degradation under load, particularly in **high-write MongoDB workloads** supporting messaging and collaboration features.
* Analyzed query patterns, index pressure, write amplification, and retention behavior.
* Produced concrete remediation strategies including:

  * Index rationalization
  * Data separation by access pattern
  * Architectural alternatives (event-based persistence, read-optimized views)
* Treated databases as explicit execution surfaces with measurable cost and performance budgets rather than opaque persistence layers.

### Team Leadership & Technical Culture

* Acted as senior escalation point for engineers, QA, and client stakeholders.
* Mentored teams on:

  * Distributed systems reasoning
  * Correctness under concurrency
  * Defensive API and client design
  * Debuggability and operational thinking
* Led internal and external technical sessions (e.g., **high-powered MERN architecture**) focused on scaling JavaScript systems beyond single-team complexity, emphasizing immutability, clear dependency direction, and effect containment.

**Key Outcomes**

* Enabled compliant global scaling without destabilizing existing platforms or requiring large-scale rewrites.
* Reduced delivery and operational risk through explicit architectural constraints, release governance, and observability.
* Converted fragmented, tribal-knowledge-driven systems into **predictable, reviewable, and operable platforms** suitable for continued growth.


---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**  
*Oct 2018 – Jun 2020*

Senior consultant and hands-on technical lead delivering **enterprise-grade systems** across telecom and financial-services clients. Operated across **backend services, data-intensive platforms, and large-scale frontend applications**, with a strong emphasis on **performance analysis, system reliability, and production remediation**. Regularly staffed into high-impact problem areas where platforms were underperforming or exhibiting systemic instability.

### Mortgage Cadence Platform (Enterprise Fintech)

Large-scale enterprise fintech platform used by major North American mortgage lenders, built on a **.NET backend, SQL Server**, GraphQL APIs, and a substantial **Angular frontend** maintained by multiple independent teams.

- Worked primarily on the **.NET backend and data layer**, with a heavy focus on **SQL Server query design, optimization, and performance analysis**.
- Designed, optimized, and refactored **complex SQL queries** supporting high-volume financial workflows, addressing execution-plan inefficiencies, locking behavior, and data access patterns.
- Implemented and optimized **GraphQL resolvers in .NET**, reducing over-fetching and N+1 query patterns by restructuring resolver execution and query composition.
- Collaborated closely with frontend teams to improve **client-side GraphQL query design**, aligning query shape and pagination strategies with backend execution characteristics.
- Contributed feature work across backend services and APIs while maintaining strict performance and correctness requirements typical of regulated financial systems.

**Frontend Performance & Architecture (Angular)**

- Brought in to address **severe responsiveness and UI performance issues** in a large Angular application used by internal and external stakeholders.
- Conducted deep runtime analysis using browser profiling tools, flamegraphs, and instrumentation to identify bottlenecks in data-heavy grids, animations, and change-detection behavior.
- Re-architected critical UI components around a **unidirectional state flow**, separating:
  - A **stateful orchestration layer** responsible for data flow and interaction logic.
  - A highly optimized **OnPush-rendered presentation layer**, minimizing change-detection frequency and rendering cost.
- Eliminated unnecessary interval-driven JavaScript work, replacing it with **CSS-based rendering** where possible or executing logic **outside Angular’s zone**.
- Demonstrated and documented measurable improvements in interaction latency and frame consistency to client architecture leadership.

### Telus Digital — MyWiFi Platform (Telecom)

Backend-only engagement supporting a consumer-facing application for managing and monitoring home Wi-Fi networks.

- Designed and implemented **Node.js microservices** serving as the backend for the *Telus MyWiFi* application.
- Worked in a distributed systems environment integrating with **unreliable downstream services and physical devices**, requiring defensive design and resilience strategies.
- Investigated production issues caused by downstream instability, timeouts, and partial failures; implemented mitigation strategies at the service boundary.
- Built and improved **observability and operational tooling**, including structured logging, metrics, and deployment instrumentation.
- Worked with **OpenShift-based deployments**, AWS infrastructure components, and **Terraform** to support environment provisioning and operational consistency.
- Collaborated with client engineers to improve service reliability, deployment confidence, and incident response practices.

### Team & Delivery Responsibilities

- Technical lead for **cross-functional agile teams** (typically 4–6 developers, QA, and a Scrum Master).
- Owned technical planning, architectural decisions, and escalation management.
- Regularly interfaced with client architects and engineering leadership to review findings, propose remediation strategies, and guide implementation.

**Technologies & Platforms**

.NET, C#, SQL Server, GraphQL, Angular, TypeScript, JavaScript, Node.js, OpenShift, AWS, Terraform, Docker, CI/CD pipelines.

**Key Outcomes**

- Delivered substantial backend and data-layer performance improvements on a mission-critical fintech platform.
- Restored frontend responsiveness and usability through targeted architectural refactors.
- Improved reliability and observability of backend services operating in unstable, real-world environments.
- Enabled client teams with clearer performance models and more resilient system designs.

---

## Rangle.io

**Software Developer**  
*Apr 2017 – Oct 2018*

Full-stack JavaScript developer contributing to both client projects and open-source tooling.

- Core contributor to **Augury**, the official Angular DevTools extension, including performance-profiling features.
- Built React, Angular, and Node.js features for enterprise clients across multiple domains.
- Led performance audits and AngularJS → Angular migrations.
- Delivered production improvements impacting SEO, runtime performance, and long-term maintainability.