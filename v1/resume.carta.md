---
name: Santiago Elustondo
email: santi@blast-engine.io
phone: (416) 662 8602
address: 30 Whistle Post st. Toronto, On. M4E3W8 
title: resume.carta.md
---

## Experience

### TypeFirst *(Jan 2024 – Present)*

* *Principal Engineer / Co-Founder*

TypeFirst is an independent consulting and technical leadership practice focused on **platform architecture, type-driven system design, and frontend/backend scalability**. Operated as senior technical authority across discovery, architecture, delivery, and organizational enablement for early-stage and growth companies, with a mandate to reduce key-person risk, stabilize delivery, and establish architectures that scale across teams rather than features.

Work consistently emphasized **platform leverage**: shared abstractions, enforceable contracts, monorepo hygiene, and developer-experience improvements that enable multiple engineers and teams to ship safely in parallel. Engagements combined hands-on implementation with architectural correction, documentation, hiring support, and stakeholder translation.

In parallel with client delivery, TypeFirst serves as a vehicle for **explicit platform thinking**: developing, testing, and articulating architectural patterns around TypeScript, React, and large-scale JavaScript systems.

* Advanced **type-driven architecture** patterns that use the TypeScript compiler as an enforcement mechanism for invariants, contracts, and architectural boundaries.
* Developed practical approaches to **AI-assisted development** constrained by strong type systems, reducing entropy in large codebases.
* Produced long-form technical writing and talks on frontend and platform engineering topics, including monorepo design, purity/immutability, state modeling, and developer-experience as a scaling constraint.
* Fed these patterns directly back into client work, ensuring that public thought leadership translated into concrete delivery leverage rather than abstract theory.

---

#### Sector Growth — Integration Platform & Monorepo Architecture  
**TypeScript | React | Node.js | MongoDB | GCP | HubSpot | Shopify | NetSuite**

Architect and technical lead for a series of bespoke integration platforms extending HubSpot beyond native capabilities for large commercial clients.

* Designed and implemented a **TypeScript monorepo** (Yarn workspaces, shared tsconfig) spanning React dashboards and stateless Node.js services, with **isomorphic domain models and service contracts** shared across client and server.
* Built a **type-safe action/RPC layer** with a shared async interface and registry, enabling client↔server calls with full autocomplete, compile-time contract enforcement, and build-time failure on incomplete implementations.
* Delivered cloud-hosted integration services combining **webhook ingestion, scheduled polling, and workflow orchestration**, coordinating complex cross-system business processes across Shopify, HubSpot, and NetSuite.
* Modeled reconciliation-centric data domains in MongoDB, maintaining a canonical internal representation while detecting, surfacing, and resolving discrepancies across multiple external systems of record.
* Built React-based operational dashboards allowing clients to inspect cross-system state, audit workflows, trigger manual syncs, and schedule consistency checks.
* Acted as senior technical counterpart to business stakeholders; translated ambiguous operational workflows into extensible, strictly-typed frameworks reused across engagements.
* Led hiring and oversight of contract engineers (including nearshore teams), while retaining ownership of framework-level and high-risk technical work.

---

#### Oralinx — Platform Assessment & Frontend Performance Remediation  
**TypeScript | Next.js | React | GraphQL | PostgreSQL | Azure | AKS | Terraform**

Senior technical consultant engaged to prepare a healthcare platform for scale, investor scrutiny, and team growth.

* Conducted a **full-stack architecture and operations audit**, externalizing system knowledge into reviewable documentation and eliminating reliance on tribal knowledge.
* Diagnosed and corrected **Next.js anti-patterns** where the application functioned as a hydration-gated SPA; moved critical data paths to SSR and restructured data-fetching to reduce request fan-out and perceived latency.
* Established normalized frontend data access patterns and caching strategies to stabilize performance under growing datasets.
* Codified infrastructure with Terraform and introduced production-like staging environments, materially reducing release anxiety and regression risk.
* Improved observability, logging discipline, and operational runbooks, enabling non-authors to diagnose issues independently.

---

#### Conexis VMS — Delivery Stabilization & Enterprise Hardening  
**TypeScript | NestJS | Next.js | PostgreSQL | Azure | Redis | OAuth | SAML**

Technical lead responsible for stabilizing delivery and reclaiming ownership of a business-critical vendor management platform.

* Recovered platform ownership from an offshore agency by centralizing repositories, credentials, and documentation under client control.
* Designed and implemented **enterprise SSO** (Azure AD via OAuth/SAML), coordinating directly with client security teams and documenting authentication boundaries and failure modes.
* Built a standalone **RSS ingestion service** to normalize externally published job postings into the platform’s internal domain model with idempotent, replay-safe semantics.
* Led deep data-modeling work to rationalize an organically grown PostgreSQL schema into reportable, defensible business views without destabilizing transactional paths.
* Hardened multi-tenancy assumptions across backend services, background jobs, and data access layers.
* Diagnosed and remediated frontend performance and architectural issues in a Next.js codebase that underutilized server capabilities, reducing duplicated queries and cascading client-side loads.
* Served as de facto technical lead for an offshore team, providing architectural correction, PR oversight, and hiring guidance to reduce long-term agency dependence.

---

### Vaco *(June 2020 – Nov 2021)* **[1 year, 6 months]**  
- *Director, Technical Solution Delivery* *(Nov 2020 – Nov 2021)*  
- *Technical Lead* *(June 2020 – Nov 2020)*

Senior technical delivery leader for Vaco Toronto consulting engagements, operating across discovery, architecture, execution, and escalation management. Owned the translation of stakeholder goals into executable engineering systems: defined requirements, success KPIs, and non-negotiable constraints; decomposed ambiguous problem spaces into phased roadmaps; staffed and enabled delivery teams; and sustained execution under real production and release pressure.

Acted as the primary technical interface between client leadership, Vaco recruiting, and delivery teams. Responsibilities spanned architecture correction, platform design, delivery governance, and operational unblocking—explicitly optimizing for platform outcomes (many engineers shipping safely in parallel) rather than individual feature throughput.

- Led technical assessments of complex, high-IO JavaScript systems; produced modernization plans centered on developer experience, dependency hygiene, performance ceilings, and operational risk reduction.  
- Established delivery operating cadence across multi-repo codebases: structured discovery → design → implementation → review flow; clear ownership and escalation paths; and release practices that reduced integration risk without stalling velocity.  
- Drove engineering health initiatives (testing posture, regression strategy, debugging ergonomics, documentation discipline), reducing key-person dependency and making systems operable by teams rather than individuals.

---

#### Avaya — Avaya Spaces *(Frontend & Realtime Platform, Multi-Region)*  
**typescript | react | redux | node | socket.io | kubernetes | gcp | mongo | redis pub-sub | gcp pubsub | terraform | k6**

Technical lead on Avaya Spaces, a globally distributed enterprise communication and collaboration platform supporting web, desktop, and mobile clients, operating under strict data residency and sovereignty requirements.

- Led platform-level architecture enabling **geo-distributed deployments (“flavors”)**, separating global metadata from regional user-generated data to enforce data-at-rest and data-in-transit constraints by construction.  
- Architected and delivered a **platform-agnostic TypeScript client SDK** to replace and deprecate web-client-specific DAL logic. The SDK became the canonical client interface for both the existing web app and a new React Native client team, encapsulating federation-aware routing, endpoint resolution, and multi-region websocket subscription management.  
- Designed and implemented a **Node.js realtime socket abstraction** that preserved the socket.io server programming model while enabling compliant cross-region messaging.  
  - Local delivery used socket.io + Redis adapter within a region.  
  - Cross-region delivery encrypted payloads and relayed them via global GCP Pub/Sub, then decrypted and emitted within the destination region using local socket infrastructure.  
  - The abstraction minimized server-side handler changes, allowing geo-distribution to be introduced without a full application rewrite.  
- Drove design of cross-region socket state management and traceability: routing to point-of-contact pods, per-region keying strategies, subscription state modeling, and end-to-end tracing to support debuggability in a distributed realtime system.  
- Led performance and reliability investigations under load, particularly around MongoDB write amplification and index pressure in core messaging collections; proposed and evaluated remediation strategies (index rationalization, data separation, read-optimized views) grounded in observed access patterns rather than theoretical schema design.  
- Defined and enforced release and QA strategy across multiple repositories: PR visibility and review discipline, dedicated regression deployments to avoid blocking shared pipelines, E2E execution scheduling, and explicit triage workflows to convert test failures into actionable work.  
- Supported Terraform-based provisioning of new regional deployments and validated end-to-end rollout mechanics (infra → services → enablement → controlled exposure), reducing operational risk as regional coverage expanded.

---

#### Frontend Platform Work — UWF (Unified Widget Framework)  
**react | typescript | redux | web components | node**

Led frontend platform work on **UWF**, a shared UI surface intended to be embedded across products while remaining independently deployable.

- Created a standalone React application capable of compiling into a **reusable Web Component**, enabling consistent UI embedding without coupling host applications to internal implementation details.  
- Defined build and run scripts supporting dual modes (standalone app vs Web Component), lowering friction for local development, testing, and integration.  
- Drove refactors to shared `@avaya-spaces/ui-components` and a shared redux-state package to support reuse across both the primary application and UWF without duplicating logic or state models.  
- Contributed to the design of a supporting **authentication microservice** to enable refreshable JWTs, remove secrets from client code, and establish stateless-first scaling characteristics, including dependency-injection and unit-test scaffolding for long-term maintainability.

---

#### Public Technical Talks *(Vaco Representative)*

- Represented Vaco Toronto through multiple public technical talks on scaling **“high-powered MERN”** systems, drawing on consulting experience across large, long-lived JavaScript codebases.  
- Addressed platform-level failure modes in React and MERN ecosystems: architectural entropy in monorepos, hidden side effects, brittle tests, and build/debug friction.  
- Advocated for platform fundamentals—immutability and purity boundaries, explicit dependency rules, testable state models, and developer experience as a first-class scaling constraint—positioning Vaco as a **platform-minded engineering partner**, not staff augmentation.

---

### Rangle.io *(Nov 2022 – Dec 2023)*  
- *Technical Director - DevEx Lead* *(July 2023 – Dec 2023)*  
- *Technical Director* *(Nov 2022 – July 2023)*  

Technical Director responsible for **frontend platform strategy, architectural risk management, and internal capability development** across multiple concurrent enterprise engagements. Operated as senior technical authority spanning client advisory, internal R&D, performance engineering, and people leadership, with an explicit mandate to elevate delivery quality, technical judgment, and organizational leverage.

Role combined **hands-on deep technical work** with **executive-level advisory**, translating ambiguous future-proofing goals into concrete, defensible architectural decisions while protecting delivery velocity and maintainability.

---

#### Frontend Platform & Architecture Strategy  
**React | Next.js | Angular | TypeScript | Webpack | Rollup | Nx | Storybook | SSR**

Led and influenced platform-level frontend decisions affecting multiple teams and clients.

* Acted as principal advisor on **design system and frontend platform architecture**, particularly around cross-framework strategies (React, Angular, Web Components).
* Evaluated Web Components, Angular Elements, and framework-native libraries as **organizational scaling mechanisms**, explicitly modeling tradeoffs across DX, QA cost, performance, adoption risk, and long-term maintainability.
* Established and communicated a defensible architectural position:
  * Rejected **atomic Web Components** as a primary design-system strategy due to empirical integration, testing, and form-control failures across frameworks.
  * Endorsed **framework-native design systems** (Angular/React) with **selective Web Component or Angular Element usage** only at larger, isolated UI boundaries (widgets, dialogs, MFEs).
* Advised client leadership (notably Dealer-FX) through high-stakes architecture decisions, reframing “future-proofing” from speculative technology bets into **costed risk tradeoffs** grounded in prior enterprise experience.

---

#### Performance Engineering & Build Optimization  
**Webpack | Bundle Analyzer | Statoscope | Next.js | CI/CD**

Drove measurable performance improvements and converted one-off debugging into repeatable organizational capability.

* Led production bundle-size investigations, tracing transitive dependency inclusion through bundler graphs rather than surface-level imports.
* Reduced parsed JavaScript bundle size in a production Next.js application by **~50% (≈1.84 MB → ≈931 KB)** through targeted dependency pruning and selective imports.
* Authored a comprehensive internal/external guide on **bundle size optimization**, documenting a repeatable workflow using Webpack Bundle Analyzer and Statoscope.
* Advocated for **performance budgets and bundle-size governance** integrated into CI/CD, reframing performance as a continuously enforced constraint rather than a reactive concern.
* Mentored teams on interpreting bundler output (parsed vs gzip, entrypoints, issuer paths) to enable independent diagnosis and remediation.

---

#### Internal Enablement, R&D, and Knowledge Infrastructure

Established structured internal programs to multiply technical impact beyond individual projects.

* Designed and maintained a centralized **Notion-based technical knowledge system**, organizing R&D, architecture decisions, project learnings, and capability tracking.
* Led recurring internal technical sessions covering:
  * React and Next.js performance characteristics
  * Modern build tooling (Webpack, Rollup, code-splitting)
  * Web Components, Angular Elements, and cross-framework integration pitfalls
  * TypeScript language evolution and architectural patterns
* Authored and curated long-form technical materials (articles, slide decks, demo repos) intended for **durable reuse**, not one-off presentations.
* Used internal projects (e.g., Rangle website) as **real-world laboratories** for platform techniques, feeding concrete learnings back into client engagements.

---

#### Client Delivery Oversight & Platform Correction

Provided senior technical leadership across multiple enterprise clients under delivery pressure.

* Supported and unblocked teams on complex frontend initiatives, including CMS-driven design systems, SSR behavior, and responsive layout edge cases.
* Led deep technical spikes (e.g., SVG clip-path responsiveness) where naive implementations posed long-term maintainability and correctness risks, producing robust patterns rather than fragile hacks.
* Reviewed and corrected architectural anti-patterns in active codebases, prioritizing system health over short-term feature velocity.
* Acted as escalation point for high-risk technical decisions, balancing delivery timelines with long-term platform integrity.

---

#### People Leadership & Organizational Architecture

Managed and developed engineers while shaping technical culture.

* Conducted performance reviews, capability assessments, and promotion advocacy grounded in observed technical impact and growth trajectory.
* Mentored engineers transitioning from task execution to architectural reasoning, emphasizing problem framing, constraint identification, and tradeoff analysis.
* Actively shaped hiring, staffing, and team composition decisions to reduce single-point-of-failure risk and improve long-term sustainability.

---

#### Public Technical Advocacy & Thought Leadership

Extended Rangle’s technical voice through credible, experience-backed content.

* Delivered internal and public talks on frontend architecture, Web Components, and performance engineering.
* Produced technically rigorous content grounded in real production systems rather than theoretical examples, reinforcing Rangle’s reputation for pragmatic senior-level engineering.

---

### Lululemon  
- *Engineering Lead* *(Dec 2021 – Oc)*  
**react | next.js | node | github actions | AWS | terraform**

I work with and across agile teams to design, build, and support new tooling and features for Lululemon's suite of applications. Each project is a collaborative effort involving stakeholders, teams, and repositories from across Lululemon's product and engineering community.

---

### Vaco *(July 2020 – Nov 2021)* **[1 year, 6 months]**  
- *Director of Technical Solution Delivery* *(May 2021 – Dec 2021)*  
- *Technical Lead* *(July 2020 – May 2021)*

I lead and support the assessment and delivery efforts for Vaco Toronto's consulting engagements. I gather requirements and KPIs, reach consensus regarding solutions and roadmaps, work with recruiting department to assemble the teams, and provide support throughout the engagement on a technical and organizational capacity, addressing feedback and escalations from all corners.

#### Avaya – Avaya Spaces  
**react | redux | node | express | kubernetes | gcp | mongo | redis pub-sub | terraform**

- Avaya Spaces is suite of globally-distributed enterprise communication and collaboration tools, supporting a large array of client devices.

---

### Avanade *(October 2018 – July 2020)* **[2 years, 1 month]**  
- *Technical Lead* *(November 2019 – July 2020)*  
- *Sr Consultant* *(October 2018 – November 2019)*

I lead agile delivery teams (4–6 devs, 2 QA, 1 SM) in technical planning and implementation: providing team with guidance and support, handling technical escalations, and converting requirements into scalable technical solutions that fit client timelines and expectations.

#### Telus – MyWifi  
**node | jest | microservices | aws | docker | jenkins | redis | openshift | mongo**

- Develop horizontally-scaling (distributed) NodeJS microservices to serve as backend for the Telus MyWifi app, which interoperates with a number of downstream systems and devices to allow users to configure and monitor their home WiFi.

#### Accenture – Mortgage Cadence Platform  
**angular | typescript | sql-server | azure | mocha | selenium | graphql | .net**

- MC is an enterprise fintech application used by the largest mortgage lenders in North America. Audit performance, discuss findings and solution proposals with client architecture leads, and undertake improvements to core libraries.

#### High-Performance React Training Bootcamps  
**react | react-native | redux | ecmascript | design patterns**

- Designed and delivered in-depth multi-day training programs for client organizations on the subject of performance profiling and optimization of web apps, using modern client-side JS frameworks (primarily Angular and React).

---

### Rangle.io *(April 2017 – Oct 2018)* **[1 year, 7 months]**  
- *Developer / Consultant* *(April 2017 – Oct 2018)*

I work with agile teams that analyze, design, and implement solutions using the best modern tools and practice, bringing our full-stack JavaScript expertise to the table for consulting and development. We assist clients in upgrading and modernizing their software, as well as getting new high quality engaging products to market quickly, streamlining the Agile flow to bring the most value out of every engagement.

#### Angular Devtools – Augury  
**angular | DOM service workers | circle-ci | typescript | lerna**

- Augury is an open-source Angular debugging and profiling toolkit developed and maintained by Rangle.io in partnership with the Angular team.

#### Vitamin Shoppe – e-Commerce Migration  
**angular | redux | prerender-io | java-spring**

- Provided guidance, support, and training for enterprise client migration from AngularJS 1.6 to Angular 4.

#### KagenAir  
**angular | apache-cordova | webrtc | native plugins**

- Performance audit followed by bottleneck resolutions on iOS/Android application written in AngularJS (1.6) running on Apache Cordova, specifically WebRTC video conferencing feature utilizing native Cordova plugins.

#### Atlas – Resourcing Portal  
**react | node | redux | mongo | graphql | circle-ci**

- Designed and implemented application features, devops pipeline improvements, and performance enhancements on enterprise staffing portal.
- Investigated feasibility of stakeholder requests for features and improvements. Provided time/cost estimations, recommendations, timelines, and progress reports.

---

### ApplianceInfo *(June 2016 – April 2017)* **[11 months]**  
- *Lead Developer* *(June 2016 – April 2017)*  
**angular | firebase | redux | mongo | graphql**

- Appliance Info is a business-facing software-as-a-service for appliance retail stores.
- I Lead small agile product development team (3 dev). I conduct interviews, provide technical training and support, advise CEO regarding costs and roadmaps, and lead design and implementation.

---

### Influicity *(March 2015 – June 2016)* **[1 year, 4 months]**  
- *Full-Stack Developer* *(March 2015 – June 2016)*  
**react | php | my-sql**

- Influicity is a platform that brings together social media influencers and marketers wishing to showcase their products. We streamline the process from networking, to content review, to analytics.

---

### The Cube School of Technology *(Jan 2016 – May 2016)* **[5 months]**  
- *Instructor* *(Jan 2016 – May 2016)*  
**react | node | ecmascript | unity**

- I teach ReactJS, JavaScript, and game development courses.
- I develop course content and materials, and chat with prospective students about their interests.

---

## Education

**York University** — Computer Science  
**George Brown College** — Software Development

---

## Languages

**English** — Primary  
**Spanish** — Fluent