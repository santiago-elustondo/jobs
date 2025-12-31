# Santiago Elustondo

**Lead Full Stack Engineer / Technical Lead**
Toronto, ON · On-Site / Hybrid / Remote
santi@blastengine.io / (416) 662 8602
[linkedin](https://www.linkedin.com/in/santiago-elustondo)

---

## Profile

Lead Full Stack Developer with 10+ years delivering **enterprise, high-availability systems** across frontend, backend, and cloud infrastructure. Proven record of translating ambiguous business requirements into **enforceable technical architecture**, owning production reliability through root-cause analysis, and mentoring teams through complex delivery constraints. Deep experience in TypeScript/Node platforms, distributed and realtime systems, frontend architecture at scale, and operational delivery in regulated or high-risk environments.

---

## Core Technical Competencies

**Languages & Runtimes**
TypeScript, JavaScript, Node.js, JVM-adjacent systems (Java integration exposure)

**Cloud & Infrastructure**
AWS-style cloud architectures (Lambda patterns, API Gateway, object storage, NoSQL), Azure, GCP, Terraform, Docker, Kubernetes, CI/CD

**Backend & Distributed Systems**
REST APIs, event-driven systems, pub/sub, realtime messaging, authentication & identity, multi-region architectures

**Frontend & UX**
React, Angular, Redux, micro-frontends, Web Components, performance optimization, defensive integration patterns

**Data & Persistence**
PostgreSQL, MongoDB, Redis, NoSQL modeling, reporting pipelines

**Leadership & Delivery**
Agile delivery, system design, incident response, mentoring, stakeholder alignment, release governance

---

## Professional Experience

---

## Blast Engine Inc. (Consulting)

**Founder / Technical Consultant**
*Jan 2024 – Present*

Senior technical consultant engaged to **stabilize, harden, and unblock enterprise platforms** under delivery, growth, or operational pressure. Operates as hands-on technical authority across backend services, frontend architecture, identity, and data modeling.

**Representative Engagements**

* **Conexis VMS (Managed Vendor Management Platform)**

  * Led enterprise integrations spanning **identity, ingestion, and multi-tenancy hardening** for a platform supporting enterprise recruiting workflows.
  * Designed and implemented **SSO integration (Azure AD; OAuth/SAML)**, coordinating directly with client IT/security teams and documenting authentication semantics and failure modes to reduce operational ambiguity.
  * Built a standalone **Node.js ingestion service** consuming external job feeds (RSS), normalizing and idempotently updating records, and mapping external data into internal domain models.
  * Converted implicit, “paper” multi-tenancy into **enforced invariants** across request handling, background jobs, and data access, remediating hard-coded tenant assumptions.
  * Analyzed organically grown PostgreSQL schema and ad-hoc reporting paths; led discovery to recover recruiting lifecycle semantics and delivered durable APIs/views for reporting without destabilizing write paths.
  * Implemented event-driven client integration using **Redis Pub/Sub on Azure**, defining namespaces, contracts, and Node publishers/consumers to formalize interoperability.

* Provided architecture documentation, onboarding material, and delivery narratives sufficient to reduce key-person dependency and support internal hiring.

---

## Rangle.io

**Technical Director, DevEx Lead**
*Nov 2022 – Dec 2023*

Senior technical leader responsible for **delivery quality, developer experience, and engineering growth** across multiple concurrent client engagements.

* Led and mentored ~10 engineers across seniority levels, including **QA-to-developer transition cohorts**, with explicit growth plans and demonstrable skill progression.
* Acted as escalation point for complex frontend and full-stack issues, balancing direct intervention with systemic fixes (standards, tooling, documentation).

**Selected Workstreams**

* **Frontend Performance & Bundle Optimization (Enterprise React/Next.js)**

  * Led production bundle-size reduction initiatives using **dependency audits, import-path correction, and bundler configuration**.
  * Established a repeatable performance workflow (baseline → isolate → remediate → verify → document) and coached engineers to independently apply techniques; results were formalized into internal articles and talks.

* **Embedded Frontend Platforms**

  * Served as senior technical lead for **React micro-frontends embedded inside native host applications**, defining integration contracts, isolation boundaries, and delivery workflows under tight timelines and unclear requirements.

* Drove internal DevEx initiatives around **build tooling, test posture, architectural hygiene, and performance literacy**, translating consulting lessons into reusable guidance.

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Technical lead for a **horizontal loyalty initiative** integrated across a large, federated React/Node ecosystem composed of independently owned micro-frontends assembled via Webpack Module Federation.

* Architected a dedicated **loyalty platform repository** delivering versioned, self-contained UI modules consumed by checkout, PDP, search, and account experiences.
* Designed exported components to be **safe by default**: strictly typed and serializable props, React context isolation, error boundaries, and internal observability (analytics, error tracking, feature flags) owned centrally by the loyalty team.
* Coordinated architectural approvals with security- and compliance-sensitive teams (notably checkout), balancing velocity with strict integration requirements.
* Built development workflows mirroring host runtime constraints, surfacing bundle impact, peer-dependency conflicts, and runtime behavior before integration.
* Mentored engineers in distributed frontend architecture, defensive integration patterns, and production-grade React practices.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Delivery authority combining **hands-on architecture** with **governance and escalation ownership** across consulting engagements.

* Led discovery, KPI definition, roadmap construction, team formation, and production stabilization under multi-repo, multi-team constraints.

**Enterprise Realtime & Distributed Systems**

* Led architecture enabling **geo-constrained, multi-region deployments** as a first-class capability to satisfy data residency and sovereignty requirements.
* Formalized geographic policy semantics (home region, strictness/whitelisting, ownership rules) so disallowed readable-at-rest states were **structurally unrepresentable** without correct routing.
* Architected and delivered a **platform-agnostic TypeScript client SDK** used by web and React Native clients, centralizing region resolution, endpoint selection, and concurrent websocket subscriptions across global, home, and foreign regions.
* Designed a **cross-region realtime messaging abstraction** preserving socket.io ergonomics while introducing encrypted pub/sub transport for inter-region delivery (Redis intra-region, global Pub/Sub inter-region).
* Led root-cause analysis and remediation of persistence bottlenecks (MongoDB write amplification, index pressure, retention behavior).
* Established release governance, QA coordination, and **Terraform-driven environment provisioning** for new regional deployments.

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Technical lead on enterprise delivery across telecom and fintech clients.

* Led agile teams (4–6 developers, 2 QA, 1 Scrum Master), owning technical planning, estimation, and escalation handling.
* Built **horizontally scalable Node.js microservices** supporting a consumer MyWiFi platform integrating with downstream systems and devices.
* Conducted deep performance audits of large Angular applications suffering UI jank under grid-heavy and animation-heavy workloads.
* Re-architected components into **stateful orchestration layers with optimized OnPush renderers**, reducing change-detection cost; replaced interval-driven JavaScript with CSS or execution outside Angular zones.
* Delivered multi-day client training on **web performance profiling and optimization**.

---

## Rangle.io

**Software Developer**
*Apr 2017 – Oct 2018*

Full-stack consultant across multiple enterprise engagements.

* Core contributor to Angular debugging/profiling tooling, addressing performance challenges in serialized state transfer and extension runtime behavior.
* Performed performance audits and remediation for AngularJS/Cordova mobile applications, including WebRTC-heavy flows.
* Supported AngularJS → Angular migrations and production stabilization efforts.
