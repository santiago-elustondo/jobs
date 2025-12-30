### Vaco *(June 2020 – Nov 2021)* **[1 year, 6 months]**  
- *Director of Technical Solution Delivery* *(Nov 2020 – Nov 2021)*  
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
