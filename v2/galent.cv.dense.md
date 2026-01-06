# Santiago Elustondo

**Technical Lead / Senior Full Stack Engineer**  
Toronto, ON · Hybrid-ready (3 days/week)  

Enterprise Systems · Distributed Architecture · SQL-Driven Platforms · Angular · Microservices

---

## Profile

Technical Lead and Senior Full Stack Engineer with **12+ years of experience** designing, optimizing, and stabilizing **enterprise-grade distributed systems** across fintech, telecom, retail, and SaaS domains. Proven track record leading teams, driving architectural decisions, and resolving performance and scalability issues in **Java/.NET/SQL-centric backends** paired with **large Angular frontend applications**. Operates effectively across backend services, data layers, frontend platforms, and cloud infrastructure, with a strong emphasis on **correctness, observability, and long-term system health**.

**Backend & Distributed Systems**
- Enterprise backend platforms (Java/J2EE & .NET ecosystems)
- RESTful APIs, service-oriented & microservices architectures
- Distributed messaging concepts (pub/sub, async workflows, event-driven systems)
- Concurrency, reliability, and failure-mode analysis

**Data & Persistence**
- MS SQL Server (schema design, query optimization, execution-plan analysis)
- Stored procedures, transactional integrity, performance tuning
- GraphQL resolver optimization and query-shape control
- Redis and caching strategies

**Frontend**
- Angular (large-scale enterprise applications, Angular 10+ era)
- TypeScript, state management, performance profiling
- UI architecture for data-heavy, workflow-driven systems

**Cloud & DevOps**
- Cloud-native deployments (AWS / Azure exposure)
- Containerized services (Docker, OpenShift, Kubernetes familiarity)
- CI/CD pipelines, release governance, environment provisioning
- Observability, logging, metrics, and APM-driven diagnostics

**Leadership & Delivery**
- Technical leadership for cross-functional Agile teams
- Architecture reviews, design governance, escalation ownership
- Mentoring senior and intermediate engineers
- Stakeholder communication and roadmap alignment

---

## Professional Experience
---

## Blast Engine Inc. (Consulting & Product Engineering)

**Co-Founder / Principal Engineer**
*Jan 2024 – Sept 2025*

Founder of a consulting-led engineering practice delivering **senior technical audits, architecture remediation, and production stabilization** for growth-stage and enterprise-adjacent SaaS platforms. Engagements focus on removing key-person dependency, restoring delivery confidence, improving performance and observability, and establishing **scalable, supportable system architectures** across backend, frontend, and cloud infrastructure.

### Conexis — Vendor Management System (Enterprise SaaS)

Enterprise VMS platform supporting contingent workforce management, complex reporting, and enterprise authentication requirements.

* Engaged as **senior technical authority** to stabilize delivery risk and transition architectural ownership away from a fully offshore team with limited system-level context.
* Performed deep **backend (Node.js / NestJS)** and **frontend (Next.js)** audits, identifying misuse and underuse of framework primitives that caused performance degradation, over-fetching, and brittle domain boundaries.
* Designed and implemented **enterprise SSO integration** with Azure Active Directory using OAuth2 / SAML flows, coordinating directly with client security and IT stakeholders.
* Architected and built a **cloud-hosted ingestion service** to consume external RSS job feeds, normalize heterogeneous data, detect deltas, and synchronize into internal domain models with idempotency guarantees.
* Reverse-engineered organically grown schemas and delivered **explicit data models and reporting APIs**, enabling reliable operational and client-facing reporting.
* Produced architectural documentation and system maps sufficient to **support hiring, onboarding, and internal ownership transfer**, directly addressing key-person dependency.
* Improved frontend performance and reliability by restructuring data-fetching patterns and aligning client behavior with **Next.js server-side and streaming capabilities**.

**Technologies:** TypeScript, Node.js, NestJS, Next.js, PostgreSQL, Azure, OAuth2 / SAML, GitHub Actions, Kubernetes

---

### Oralinx — Specialist Dentistry Network & Consumer Platform

Healthcare-adjacent professional network and consumer discovery platform operating under legal, disclosure, and performance constraints.

* Engagement centered on **technical audit, architectural clarification, and roadmap definition** rather than net-new feature delivery.
* Eliminated critical **single-engineer dependency** by producing system-level documentation covering architecture, data flows, deployment topology, and known operational failure modes.
* Diagnosed and remediated **frontend performance bottlenecks** caused by inefficient data-loading strategies as traffic scaled.
* Re-architected data access using **Next.js server-side rendering, progressive loading, and shared data services**, reducing initial payload size and time-to-interactive.
* Introduced shared domain services to eliminate redundant client-side requests across independently mounted UI surfaces.
* Delivered a **future-facing technical roadmap** explicitly separating acceptable legacy constraints from areas requiring investment to support hiring, scaling, and investor scrutiny.

**Technologies:** TypeScript, React, Next.js, Node.js, GraphQL, PostgreSQL, Azure, Kubernetes

---

### Sector Growth — Integration Hub & SaaS Enablement

Multi-tenant integration platform supporting CRM, CMS, and commerce ecosystems (Shopify, HubSpot, NetSuite, Zapier).

* Led architecture and implementation of **event-driven, cloud-native integration services** handling high-volume synchronization, reconciliation, and observability.
* Designed **ledger-based data models** and projection services enabling auditability, replay, and incremental reconciliation.
* Implemented webhook ingestion pipelines, scheduled backfills, and structured error-tracking to ensure operational reliability at scale.
* Worked directly with clients to formalize operational workflows, correctness guarantees, and measurable impact metrics.
* Delivered extensible APIs and internal tooling that allowed the platform to be sold as a standalone product alongside consulting services.

**Technologies:** TypeScript, Node.js, GraphQL, Event-driven architecture, Cloud-native services, Multi-tenant SaaS design

---

## Rangle.io

**Technical Director / Developer Experience (DevEx) Lead**
*Nov 2022 – Jan 2024*

Senior technical leader responsible for **delivery quality, frontend and full-stack architecture, performance engineering, developer experience, and team growth** across multiple concurrent enterprise client engagements. Operated as a hybrid **hands-on technical authority and people leader**, accountable for architectural decisions, delivery stability, and technical escalations in high-pressure consulting environments.

* Led and mentored ~**10 direct and indirect reports** spanning junior and senior engineers, QA engineers, QA-to-developer transition cohorts, and solution architects.
* Served as **primary escalation point** for complex frontend, full-stack, and performance failures.
* Balanced direct intervention with organizational leverage through standards, documentation, internal tooling, and knowledge dissemination.
* Supported hiring, onboarding, performance reviews, and promotion advocacy with an emphasis on technical rigor and autonomy.

---

### Momentive (SurveyMonkey) — Frontend Platform Performance & Stability

**React | Next.js | TypeScript | Webpack | Bundle Analyzer | Statoscope | GraphQL**

Embedded technical lead within Momentive’s web platform organization to address **performance regressions and delivery risk** in a large, long-lived React/Next.js codebase.

* Led a **bundle-size investigation and remediation initiative** targeting excessive JavaScript payloads caused by transitive dependencies, barrel exports, and non-tree-shakable import patterns.
* Used **Webpack Bundle Analyzer** and **Statoscope** to trace dependency graphs from entrypoints through issuer paths, identifying root causes rather than surface symptoms.
* Reduced parsed JavaScript bundle size by **~50% (≈1.84 MB → ≈0.93 MB)** with minimal code changes and no functional regressions.
* Established and documented a **repeatable performance-debugging methodology** (hypothesis → measurement → remediation → verification).
* Mentored team members through applying the technique independently; coached and sponsored a developer to publish a long-form technical article on bundle optimization.
* Provided stabilizing technical leadership during a **high-pressure period of attrition and morale risk**, restoring delivery confidence and predictability.

---

### Get Ahead — Embedded React Platform for Regulated AI Workflows

**React | TypeScript | Micro-frontends | CI/CD | AI-assisted systems**

Senior technical lead for a time-constrained, greenfield engagement delivering an embedded frontend platform for regulated mental-health practitioners.

* Led a **4-developer agile team** delivering a **micro-frontend React SPA** compiled as a CI artifact and embedded within a host **Flutter** application.
* Designed the **integration contract** between host and embedded app, including runtime argument injection, serialized configuration, and isolation boundaries.
* Worked directly with client stakeholders to resolve **misaligned requirements, incomplete designs, and unclear AI service constraints**, translating ambiguity into a concrete, shippable architecture.
* Enabled in-session **AI-assisted workflows** (live transcripts, guided record generation) while maintaining regulatory, auditability, and data-handling constraints.
* Guided an anxious early-stage team through delivery under tight timelines, resulting in a successful launch and **client re-engagement for a larger adjacent greenfield platform**.

---

### JetBlue — Cross-Framework Design System & Platform Architecture

**Web Components | Lit | React | Angular | Monorepos | CDN Delivery**

Senior technical authority supporting early-stage architecture for a multi-year design-system modernization initiative.

* Contributed to the architecture of a **framework-agnostic design system** supporting React, Angular, jQuery, and legacy backend-rendered applications.
* Led monorepo spikes evaluating **Lit, Stencil, and no-framework Web Component approaches**, converging on Lit based on maintainability and client constraints.
* Designed a dual delivery model where the core system shipped both as:

  * a **private npm package** for framework consumers, and
  * a **CDN-hosted artifact** consumable directly via HTML tags.
* Established clear boundaries between **platform primitives and framework adapters**, reducing coupling and long-term maintenance risk.
* Represented Rangle publicly by presenting learnings on **Web Components as application-agnostic design-system infrastructure** at a professional community event.

---

### Internal Platform Enablement & DevEx (Rangle.io)

* Built and maintained an internal **knowledge system** capturing architectural decisions, research outcomes, and delivery learnings across projects.
* Led recurring internal talks and workshops on frontend performance engineering, modern React/Next.js architecture, build tooling, and cross-framework interoperability.
* Sponsored and reviewed internal R&D initiatives, open-source contributions, and technical articles.
* Championed a culture of **technical ownership, performance awareness, and continuous improvement** across the organization.

---

## Lululemon

**Engineering Lead — Loyalty Platform**  
*Nov 2021 – Nov 2022*

Engineering lead for a **horizontal enterprise initiative** spanning multiple independently owned applications.

- Designed a shared frontend platform embedded across critical user journeys.
- Established strict integration boundaries, error containment, and observability.
- Coordinated architectural approvals with platform, security, and checkout teams.
- Led cross-team delivery in a highly regulated, high-traffic retail environment.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**  
*Jun 2020 – Nov 2021*

Senior technical delivery lead for complex, high-IO application platforms. Owned **end-to-end technical execution** across discovery, architecture, implementation, release governance, and production escalation. Operated as the integration point between client stakeholders, engineering teams, QA, and platform operations—converting ambiguous requirements and regulatory constraints into **explicit system invariants** (latency/error budgets, data-handling boundaries, rollout mechanics) and enforcing them through concrete engineering artifacts and process.

**Core Focus Areas**
TypeScript, Node.js, React, Redux, Socket.io, MongoDB, Redis, Kubernetes, GCP Pub/Sub, Terraform, CI/CD, k6

### Distributed Systems & Compliance Architecture (Multi-Region, Data Residency)

- Designed and delivered a **geo-aware architecture** supporting data residency and sovereignty constraints, separating globally accessible metadata from region-bound user-generated content.
- Formalized a **geographic policy model** (home region, strict vs whitelist semantics) and translated it into enforceable backend and client rules governing resource ownership, access, and routing.
- Implemented deterministic **region resolution** for users, spaces, and messages, ensuring correctness at rest and in transit rather than relying on UI-level conventions.

### Real-Time Messaging at Scale (Cross-Region)

- Architected a **cross-region realtime transport abstraction** that preserved existing socket semantics while enabling compliant multi-region delivery.
- Implemented regional fast-paths using socket.io + Redis adapters and cross-region delivery using encrypted payloads relayed via global pub/sub, minimizing handler churn and avoiding wholesale rewrites.
- Solved “state-of-the-world” concerns required for correctness in distributed socket systems: pod identity, socket metadata propagation, room membership, routing to the correct execution context, and cross-hop traceability for debugging.

### Platform Enablement & Frontend Integration Surfaces

- Led initial platform work to deliver an **embedded React surface compiled as a Web Component**, supporting both standalone and embedded execution modes with reproducible build and run scripts.
- Drove foundational engineering posture for embedded contexts: auth constraints, token refresh strategy, secret handling, dependency injection, unit-test scaffolding, and error-handling completeness.
- Identified and addressed platform gaps (JWT refresh incompatibilities, secret exposure risks) and proposed dedicated backend services where required.

### Data-Layer Performance & Production Diagnostics

- Led deep investigations into **MongoDB write amplification and index pressure** in message-heavy collections.
- Converted vague production symptoms into concrete remediation plans: access-pattern audits, index rationalization, retention policies, and evaluation of CQRS-style read models via aggregation pipelines.
- Treated lifecycle and retention defects as production-risk issues, not code-style concerns, and drove knowledge transfer to reduce single-expert dependency.

### Release Governance, QA Strategy, and Delivery Systems

- Established **multi-repo release discipline** under tight delivery constraints: PR visibility into dependent repositories, branch strategy for parallel work, and deterministic rollout sequencing.
- Enabled **deep regression testing on dedicated deployments** to avoid blocking shared staging pipelines.
- Integrated long-running E2E suites into CI/CD via scheduled execution, defined triage workflows, and operationalized failure handling as part of normal delivery.
- Defined controlled rollout strategies (shadow vs beta) and super-admin override mechanisms to enable partial exposure when company-level toggles were too coarse.

### Technical Leadership & Advocacy

- Led cross-functional teams (engineering, QA, product) through high-risk delivery phases, acting as escalation owner and architectural authority.
- Delivered public technical talks representing Vaco, focused on scaling complex MERN systems through explicit architectural constraints, immutability/purity discipline, and developer-experience as a measurable delivery multiplier (review quality, regression rate, change latency).

**Outcome**
Consistently delivered **auditable, repeatable delivery systems** under deadline pressure—reducing key-person risk, stabilizing production behavior, and enabling teams to ship complex distributed features safely across regions and surfaces.

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**  
*Oct 2018 – Jun 2020*

Delivered **enterprise-grade systems** for financial services and telecom clients, operating deeply in **Java/.NET/SQL/Angular ecosystems**.

### Mortgage Cadence Platform (Enterprise Fintech)

- Worked extensively on a **.NET + SQL Server backend** supporting high-volume mortgage workflows.
- Designed, analyzed, and optimized **complex SQL Server queries**, addressing:
  - Inefficient execution plans
  - Locking and contention issues
  - Transactional performance under load
- Implemented and optimized **GraphQL resolvers** in .NET, eliminating N+1 query patterns and reducing over-fetching.
- Collaborated with frontend teams to improve **client-side GraphQL query design**, aligning query shape with backend execution characteristics.
- Contributed feature work and performance improvements to a **large Angular application** maintained by multiple teams.
- Re-architected UI components to improve responsiveness in data-heavy views using unidirectional state flow and optimized change detection.

### Telus Digital — MyWiFi Platform

- Backend-focused role building **Node.js microservices** supporting a consumer WiFi management platform.
- Investigated failures caused by **unreliable downstream systems and devices**.
- Implemented defensive service boundaries, retries, and observability.
- Worked with **OpenShift, AWS, and Terraform** to support deployments and operational visibility.

---

## Rangle.io

**Software Developer**  
*Apr 2017 – Oct 2018*

- Contributor to **Augury**, the official Angular DevTools extension.
- Built and maintained Angular and Node.js features for enterprise clients.
- Led performance audits and AngularJS → Angular migrations.
- Worked extensively with large, data-driven Angular applications.
