---
title: cv-0.a.gen.md
---

# Santiago Elustondo

**Sr Full Stack Engineer / Technical Lead**
Toronto, ON · On-Site / Hybrid / Remote
santi@blastengine.io / (416) 662 8602
[linkedin](https://www.linkedin.com/in/santiago-elustondo)

## Profile

Full-stack technical lead with 10+ years delivering enterprise software across frontend, backend, and cloud infrastructure. Track record designing distributed, high-availability systems; converting ambiguous requirements into enforceable architecture; and owning production reliability through diagnosis, remediation, and operational process. Strengths include TypeScript/Node delivery at scale, realtime systems, identity/integration work, and mentoring teams through high-pressure delivery constraints. Grounded in “correct-by-construction” architecture: explicit invariants, bounded contracts, and operational semantics that survive multi-team change.

## Core Competencies

TypeScript/JavaScript, Node.js, JVM-adjacent systems (Java integration exposure), React, Angular, API design, distributed messaging, realtime/websockets, microservices, Redis, Pub/Sub, MongoDB, PostgreSQL, CI/CD, IaC (Terraform), cloud delivery across AWS/Azure/GCP, observability and incident response, delivery governance, stakeholder alignment, mentorship.

---

## Blast Engine Inc. (TypeFirst Consulting)

**Founder / Technical Consultant**
*Jan 2024 – Present*

Consulting technical lead for client platforms under delivery pressure, with emphasis on platform stabilization, enterprise integration, and making systems operable by internal teams (reduced key-person dependency; documentation, interfaces, and process).

### Conexis VMS — Managed Vendor Management Platform

* Led enterprise integration work spanning identity, ingestion, multi-tenancy hardening, and client-facing engineering, operating as senior technical authority for correctness, defensibility, and delivery sequencing. 
* Designed and implemented enterprise SSO integration (Azure AD; OAuth/SAML flows), including direct coordination with client IT/security stakeholders, and documented authentication behavior/failure modes to reduce operational ambiguity. 
* Delivered an external job-feed ingestion service: standalone Node.js service (deployed independently) monitoring RSS feeds, normalizing postings, performing idempotent updates, and mapping externally sourced data into internal domain entities. 
* Hardening of “paper multi-tenancy” into exercised multi-tenant invariants: validated tenant scoping across request handling, data access, and background processes; remediated implicit single-tenant assumptions (missing scoping, hard-coded tenant IDs). 
* Reporting/data-model remediation: analyzed organically grown PostgreSQL schema and ad-hoc reporting practices; led stakeholder discovery to recover recruiting lifecycle semantics and designed APIs/views for durable reporting without destabilizing write paths. 
* Implemented evented client integration via shared Redis on Azure: negotiated namespaces and contracts with client engineering; introduced Redis Pub/Sub for explicit integration semantics; shipped Node publishers/consumers supporting event-driven interoperability. 
* Led hiring and team strategy improvements: executed a hybrid model to reduce agency dependence while retaining regional advantages; ran technical evaluation and placement for senior IC hire. 

---

## Rangle.io

**Technical Director, DevEx Lead**
*Nov 2022 – Dec 2023*

Senior technical leadership spanning delivery stabilization, developer experience, and team growth. Operated as escalation point for complex performance/reliability issues, while driving repeatable engineering practices: standards, reviews, and knowledge dissemination.

* Led and mentored a ~10-person mixed cohort (junior/senior engineers and QA-to-dev transition), focusing on growth plans, demonstrable skill development, and delivery confidence under ambiguity (internal enablement + client work). 
* Drove practical performance workstreams (diagnosis → measurement → remediation → communicated proof), pairing engineering outcomes with internal knowledge capture (talks, demos, articles) to make improvements repeatable across teams. 

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Led delivery of a horizontally integrated loyalty feature set across a federated React/Node ecosystem with independently owned micro-frontends and tightly governed release cycles.

* Architected and led a dedicated loyalty platform repository delivering versioned, self-contained UI modules intended for integration across multiple host micro-frontends (checkout, PDP, search, account surfaces) while minimizing host-team coupling and integration risk.
* Established “safe-by-default” exported component contracts: strictly typed/serializable props, error-boundary containment, and internal instrumentation patterns so integrations fail closed rather than destabilizing host surfaces.
* Ran cross-team architecture alignment and approval with security-sensitive stakeholders (notably checkout) and coordinated integration PR workflows across multiple repositories with independent ownership and release governance.
* Built a development workflow that mirrored host runtime constraints (bundle impact, peer dependency conflict detection, and integration behavior) before host-team adoption, enabling earlier detection of compatibility and deployment hazards.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Combined hands-on architecture with delivery governance for consulting engagements: requirements/KPI capture, roadmap construction, team formation, escalation handling, and production-grade implementation under multi-repo, multi-team constraints. 

### Enterprise Realtime Collaboration Platform (Geo-Distributed Deployments)

* Led architecture enabling geographically constrained deployments as a first-class capability to satisfy data sovereignty/residency constraints, separating global metadata/indirection from regionally readable content/services and forcing compliance as an architectural invariant rather than a UI promise. 
* Formalized geographic policy semantics into enforceable rules (home region, strictness/whitelisting, company-owned space placement, creation/entry constraints), ensuring disallowed readable-at-rest states are structurally unrepresentable without correct routing. 
* Architected and delivered a platform-agnostic TypeScript client SDK as the canonical client-side DAL for both web and React Native surfaces: callers express business intent; SDK resolves region placement via federation metadata and routes requests to correct regional clusters, including concurrent websocket subscriptions across global/home/foreign regions as required by active resources. 
* Designed a cross-region realtime messaging abstraction preserving server-side socket.io ergonomics while swapping transport semantics under the hood: intra-region delivery remains socket.io + Redis adapter; cross-region payloads are encrypted and relayed via a global Pub/Sub channel then re-emitted locally inside the destination region. 
* Addressed correctness and operability of a unified sockets model: stable referential routing, propagation of socket metadata, end-to-end traceability, and avoidance of leaky distributed socket-state designs (origin pod identity, socket identifiers, tracing context carried through pub/sub). 
* Led performance/reliability hardening under write pressure for messaging persistence (MongoDB): analyzed workload/query/index costs, retention behavior, and remediation options ranging from index rationalization to structural approaches (e.g., read-optimized views), paired with incident-response reproducibility to reduce key-person dependency. 
* Instituted delivery mechanics that made multi-repo, coupled backend+client change shippable: explicit task/PR linkage and ownership semantics, staged discovery→implementation flow, release strategy aligned to integration realities, QA discipline via dedicated deploys, and Terraform-driven provisioning procedures for new regional deployments. 

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Technical lead on enterprise delivery across telecom and fintech, with emphasis on performance engineering, scalable backend services, and training/enablement.

* Led agile delivery teams (4–6 developers, 2 QA, 1 Scrum Master) through technical planning, estimation, implementation, and escalation handling; translated stakeholder requirements into defensible architectures aligned to client timelines.
* Built horizontally scalable Node.js microservices supporting a consumer MyWiFi platform integrating with downstream systems/devices; focused on reliability, operational supportability, and production-grade API behaviors.
* Performed deep performance profiling and remediation for large Angular applications exhibiting responsiveness issues under grid-heavy/animated UI workloads: re-architected components into stateful orchestration layers with optimized OnPush renderers; reduced change detection cost via controlled update surfaces and selective execution outside Angular; demonstrated improvements via flamegraphs and UI snapshots.

---

## Rangle.io

**Software Developer**
*Apr 2017 – Oct 2018*

Full-stack consultant across multiple client engagements, combining production delivery with performance profiling and modernization work.

* Maintained and evolved an Angular developer tooling extension (debugging/profiling), including handling performance concerns in serialized state transfer to browser tooling, and diagnosing complex interactions surfaced through stack traces and runtime profiling.
* Delivered performance audits and bottleneck remediation for hybrid mobile (AngularJS/Cordova) applications including WebRTC-heavy flows, focusing on end-user experience and stability under constrained mobile runtimes.
* Supported enterprise modernization work (AngularJS → Angular) and production remediation efforts improving crawlability/SEO and user experience by reducing client-side error surfaces and improving render determinism.