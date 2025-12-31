# Santiago Elustondo

**Technical Lead / Sr Full-Stack Engineer**
Toronto, ON · On-Site / Hybrid / Remote
santi@blastengine.io / (416) 662 8602
[linkedin](https://www.linkedin.com/in/santiago-elustondo)
[github](https://github.com/santiago-elustondo)
[npm:blast-engine](https://www.npmjs.com/org/blast-engine)
[github:blast-engine](https://github.com/blast-engine)
[github:typefirst](https://github.com/type-first)

## Profile

Senior Technical Lead with **10+ years** architecting and delivering **enterprise modernization initiatives** across TypeScript/Node.js/React ecosystems. Proven record leading **CRM re-platforming, cloud migrations, and monolith decomposition** into API-driven microservices. Deep expertise in **cloud-native services, payment system integration, event-driven architecture**, and **hands-on team leadership** through complex delivery cycles. Specializes in converting legacy enterprise systems into secure, observable, and operationally mature platforms.

## Core Technical Competencies

**Languages & Frameworks:** TypeScript, JavaScript, Node.js, React, Next.js, Angular, NestJS  
**Cloud & Infrastructure:** AWS, GCP, Azure exposure, Kubernetes, Docker, CI/CD (GitHub Actions), Terraform, OpenShift containerization  
**Backend & Integration:** REST APIs, microservices, event-driven architecture, distributed systems, OAuth/SAML/JWT, enterprise SSO  
**Data & Performance:** PostgreSQL, SQL Server, MongoDB, Redis, performance optimization, bundle analysis, observability  
**DevOps & Delivery:** CI/CD pipelines, containerization, Agile leadership, architectural governance  
**Security & Compliance:** PCI-aware patterns, payment gateway integration, secure boundary design, identity management

---

## Blast Engine Inc.

**Co-Founder / Technical Consultant**
*Jan 2024 – Present*

Independent technical lead specializing in **enterprise modernization and cloud migration** for mid-market SaaS platforms requiring architectural stabilization, performance optimization, and operational maturity.

### Conexis — Vendor Management Platform (CRM Modernization)

**Enterprise SaaS platform modernization** with strict integration, compliance, and multi-tenant requirements.

* Led **architectural assessment and re-platforming strategy** for legacy CRM system, decomposing monolithic workflows into **modular, API-driven microservices** with cloud infrastructure.
* Designed and implemented **enterprise SSO integration** with **OAuth2/SAML flows**, coordinating directly with client IT and security teams to establish secure identity boundaries and document authentication behavior.
* Built **cloud-hosted ingestion microservices** using **Node.js/TypeScript** to consume external RSS feeds, normalize data, and perform **idempotent synchronization** with internal domain models—demonstrating event-driven, resilient integration patterns.
* **Hardened multi-tenancy constraints** across data access, background processing, and API boundaries, converting implicit assumptions into enforced architectural invariants with proper tenant scoping.
* Led **PostgreSQL performance optimization and reporting architecture** work: analyzed organically grown schemas, reverse-engineered business semantics, and delivered durable APIs enabling operational reporting without destabilizing write paths.
* Implemented **event-driven client integration** using **Redis Pub/Sub**, establishing namespaced contracts and building Node.js publishers/consumers to formalize cross-system interoperability.

**Technologies:** TypeScript, Node.js, NestJS, Next.js, PostgreSQL, Redis, OAuth/SAML/SSO, GitHub Actions, Kubernetes

### Oralinx — Healthcare Network Platform (Cloud Migration & Observability)

**Healthcare platform stabilization and cloud migration** with regulatory, performance, and operational constraints.

* Conducted comprehensive **system architecture audit** and led **Kubernetes migration**, establishing infrastructure-as-code (Terraform) for reproducible, production-like staging environments.
* **Optimized Next.js/React performance** by restructuring data-fetching strategies from client-side SPA patterns to **server-side rendering and progressive loading**, reducing initial payload size and time-to-interactive metrics.
* Established **cloud-native observability posture**: structured logging with correlation IDs, request tracing, latency/error monitoring, and runbook documentation for production incident response.
* Delivered operational documentation enabling team autonomy: deployment guides, health-check procedures, common failure modes, and diagnostic workflows.

**Technologies:** TypeScript, Next.js, React, Node.js, GraphQL, PostgreSQL, Kubernetes, Terraform, CI/CD

### Sector Growth — Integration Platform (Event-Driven Architecture)

**Multi-tenant SaaS integration platform** supporting CRM, commerce, and ERP system coordination (HubSpot, Shopify, NetSuite).

* Architected and delivered **event-driven, cloud-native integration services** using **TypeScript microservices**, supporting high-volume synchronization, reconciliation, and auditability across enterprise systems.
* Designed **ledger-based data models and projection services** enabling replay, incremental reconciliation, and audit trails for compliance-sensitive workflows.
* Implemented **workflow orchestration engine** with durable task dispatch, backoff strategies, and rate-limiting aligned with third-party API constraints.
* Deployed isolated service instances per client to support custom business logic while limiting blast radius and operational coupling.

**Technologies:** TypeScript, Node.js, GraphQL, Event-driven architecture, MongoDB, Cloud Tasks, Multi-tenant design

---

## Rangle.io

**Technical Director, DevEx Lead**
*Nov 2022 – Dec 2023*

Senior technical leader responsible for **delivery quality, architecture governance, and team growth** across multiple enterprise client engagements. Led **~10 developers** spanning performance optimization, modernization initiatives, and complex system delivery.

### Momentive (SurveyMonkey) — Frontend Performance Engineering

* Embedded technical lead addressing **performance degradation** in large React/Next.js codebase serving enterprise survey platform.
* Led **bundle-size investigation and optimization** using Webpack Bundle Analyzer and Statoscope, achieving **~50% reduction in parsed bundle size** (1.84 MB → 0.93 MB) through dependency graph analysis and tree-shaking improvements.
* Established **repeatable performance debugging methodology** and transferred expertise to client team through documentation and mentorship.

### Get Ahead — Embedded React Platform (Regulated AI Workflows)

* Led **4-developer agile team** delivering embedded React SPA for regulated mental-health AI workflows, compiled as CI artifact and integrated within Flutter host application.
* Designed **integration contracts** between host and embedded app, including runtime configuration injection and isolation boundaries.
* Enabled **AI-assisted workflows** while maintaining regulatory compliance and auditability constraints.

### JetBlue — Cross-Framework Design System & Platform Architecture  
**Web Components | Lit | React | Angular | Monorepos | CDN Delivery**

Senior technical authority supporting early-stage architecture for a multi-year design-system modernization initiative.

* Contributed to the architecture of a **framework-agnostic design system** supporting React, Angular, jQuery, and legacy backend-rendered applications.
* Led monorepo spikes evaluating **Lit, Stencil, and no-framework Web Component approaches**, converging on Lit based on maintainability and client constraints.
* Designed a dual delivery model where the core system shipped as:
  - a **private npm package** for framework consumers, and
  - a **CDN-hosted artifact** consumable directly via HTML tags.
* Established clear boundaries between **platform primitives and framework adapters**, reducing coupling and long-term maintenance risk.
* Represented Rangle publicly by presenting learnings on **Web Components as application-agnostic design-system infrastructure** at a professional community event.

### Internal Platform Enablement & DevEx (Rangle.io)

* Built and maintained internal **knowledge system** capturing architectural decisions, research outcomes, and delivery learnings.
* Led recurring internal talks and workshops on **frontend performance engineering, modern React and Next.js architecture, build tooling and bundlers, Web Components and cross-framework interoperability**.
* Championed **bundle optimization techniques** using Webpack Bundle Analyzer and Statoscope, achieving significant payload reductions through dependency analysis.

**Technologies:** React, Next.js, TypeScript, Webpack, Performance optimization, Micro-frontends, CI/CD

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Technical lead for **horizontal loyalty initiative** spanning federated React/Node ecosystem with **Webpack Module Federation** and security-sensitive retail constraints.

* Designed **loyalty component library** as platform primitive, enabling safe embedding across checkout, PDP, search, and account surfaces owned by independent teams.
* Implemented **component-level isolation** with typed props, error boundaries, and centralized instrumentation to prevent failures from propagating to host micro-frontends.
* Integrated **Contentful CMS-driven content models** directly into library, enabling dynamic updates without host application redeployment.
* Coordinated **security and architecture approval** across checkout, accounts, and platform teams, particularly around authentication flows and data protection constraints.

**Technologies:** React, Next.js, TypeScript, Webpack Module Federation, Micro-frontends, Contentful CMS, LaunchDarkly

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Senior technical authority responsible for **end-to-end delivery** across high-IO, multi-surface JavaScript systems with emphasis on **distributed architecture, performance optimization, and team leadership**.

### Multi-Region Compliance Architecture

* Designed and delivered **geo-aware routing and policy model** separating global metadata from region-bound content, enabling multi-region deployments while preventing data residency violations.
* Implemented **regional deployment flavors** with deterministic resolution from user/resource to target deployment, including explicit lookup services for flavor-scoped operations.

### Platform-Agnostic Client SDK (Cross-Surface, Cross-Region)

* Architected **TypeScript client SDK** serving as canonical data-access layer for multiple application surfaces, centralizing region resolution, websocket topology, and authentication management.

### Real-Time Messaging Transport (Cross-Region, Encrypted)

* Designed **Node.js realtime abstraction** preserving socket.io handler ergonomics while enabling compliant cross-region delivery via encrypted pub/sub relay and local re-emission.

### MongoDB Performance & Data-Layer Hardening

* Led **production diagnosis** of persistence bottlenecks: analyzed index pressure, write amplification, and retention behavior; delivered remediation strategies from index rationalization to read/write decoupling patterns.

**Technologies:** TypeScript, Node.js, React, Socket.io, MongoDB, Redis, GCP Pub/Sub, Kubernetes, Multi-region architecture

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Technical lead for **enterprise-grade delivery** across telecom and **financial services clients**, accountable for design quality, performance engineering, and **production system optimization**.

### Telus Digital — MyWiFi Platform (Node.js Microservices)

* Designed and implemented **horizontally scalable Node.js microservices** serving as backend for consumer Wi-Fi management application, integrating with downstream device services and third-party systems.
* Built fault-tolerant middleware using **ExpressJS, OAuth, and RabbitMQ** (distributed Redis queues) to handle unreliable downstream services with retry mechanisms.
* Implemented **OpenShift containerization** and **Redis-based Bull Queue** for durable task processing and improved system reliability.

### Mortgage Cadence Platform — **Enterprise Fintech Performance Optimization**

* Brought in specifically to diagnose **severe UI responsiveness degradation** in large Angular application serving **North America's largest mortgage lenders**.
* Performed **deep performance audits** using browser profiling, flamegraphs, and runtime instrumentation to identify bottlenecks in financial data grids and payment processing workflows.
* **Re-architected core components** around unidirectional state flow, separating stateful orchestration from optimized OnPush-rendered UI components, achieving measurable frame consistency improvements.
* Delivered **multi-day training programs** for client engineering teams on web performance profiling and optimization techniques.

**Technologies:** Angular, TypeScript, Node.js, GraphQL, .NET Core, SQL Server, Redis, Performance engineering, Enterprise fintech systems

---

## Rangle.io

**Software Developer**
*Apr 2017 – Oct 2018*

Full-stack consultant working across **frontend frameworks, performance diagnostics, and open-source tooling**.

* **Primary maintainer** of **Augury** (Angular DevTools extension), supporting multiple Angular versions and browser environments with performance-sensitive architecture, including Canary release channel implementation.
* Led **performance investigations** on AngularJS/Cordova hybrid mobile applications with **WebRTC integration**, including enterprise SEO remediation delivering measurable organic traffic recovery.
* Designed and operationalized **Canary release channel** with opt-in builds, enhanced analytics via Sentry, and cross-browser Firefox support.

**Technologies:** React, Angular, AngularJS, TypeScript, Node.js, Redux, Performance optimization, Open-source development

---

## Key Qualifications Summary

✅ **10+ years professional software engineering experience**  
✅ **Expert TypeScript, Node.js, React, Next.js** across enterprise systems  
✅ **Cloud services experience:** AWS, GCP, Kubernetes, Docker, OpenShift containerization  
✅ **GitHub Actions and CI/CD** pipeline experience  
✅ **SQL/NoSQL databases, performance tuning:** PostgreSQL, SQL Server, MongoDB, Redis  
✅ **Payment systems integration experience** (enterprise fintech platforms, Mortgage Cadence Platform)  
✅ **CRM modernization and re-platforming** (monolith to microservices, demonstrated in Conexis VMS work)  
✅ **Event-driven architecture, distributed systems** (multi-region messaging, pub/sub integration)  
✅ **OAuth2, SAML, JWT, enterprise SSO** integration (including Azure AD SAML flows documented in Conexis)  
✅ **Agile team leadership** (4-10 developers) with architectural governance experience  
✅ **Web Components, Webpack Module Federation, micro-frontends** for cross-team integration  
✅ **Performance engineering expertise** (bundle optimization, Angular performance auditing, profiling)