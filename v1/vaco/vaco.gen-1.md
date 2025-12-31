## Vaco Toronto

**Director, Technical Solution Delivery → Technical Lead**  

Delivery authority and hands-on technical lead for complex, enterprise-grade consulting engagements. Operated across discovery, architecture, implementation, and production stabilization, with explicit ownership of technical risk, escalation handling, and delivery integrity. The role combined deep system design work with disciplined process engineering to make multi-team, multi-repository delivery predictable under real operational constraints.

### Avaya — Avaya Spaces (Global Collaboration Platform)

Enterprise real-time collaboration platform operating across multiple geographic regions, subject to strict **data residency and sovereignty requirements**. Led platform-level architecture and delivery across frontend, backend, realtime infrastructure, and release governance.

**Geographic Policy & Data Residency Architecture**

* Led the design and rollout of the **Geographic Policy (GP)** system, formalizing data residency (DR) and data sovereignty (DS) guarantees at the architectural level rather than via UI or convention.
* Defined and enforced a strict separation between **global metadata services** (routing, membership, configuration) and **regional services** (all readable-at-rest user content), ensuring that content could only be read or stored within permitted regions by construction.
* Designed deterministic routing semantics for spaces, users, and resources (home region, foreign/local classification, strict vs. whitelist policies), preventing accidental cross-region reads and invalid data placement.
* Authored and operationalized the client-facing development model: region discovery, resource location resolution, default home-region execution, and explicit cross-region query fan-out where required. :contentReference[oaicite:0]{index=0}

**Realtime Messaging & Distributed Socket Infrastructure**

* Architected and implemented a **cross-region realtime messaging abstraction** that preserved the existing socket.io programming model while enabling compliant inter-region delivery.
* Designed a “mock socket” layer that retained familiar APIs (`emit`, `broadcast`, room joins, socket metadata) while transparently switching transport semantics:
  * **Intra-region:** socket.io with Redis pub/sub adapter.
  * **Inter-region:** encrypted payloads relayed via global pub/sub, decrypted and emitted within the destination region.
* Introduced explicit **pod identity, socket identity, and tracing metadata** to guarantee correct routing and observability across regions, avoiding leaky distributed socket state.
* Added first-class support for socket metadata mutation (`socket.update`) with propagation guarantees across regions, enabling consistent presence, subscription, and authorization state. :contentReference[oaicite:1]{index=1}

**Client Platform & SDK Design**

* Architected a **platform-agnostic TypeScript client SDK** shared by the web client and a new React Native client initiative.
* Encapsulated federation logic, region resolution, endpoint selection, and multi-socket orchestration behind stable domain-level APIs, preventing feature teams from re-implementing geo-aware logic.
* Designed concurrent websocket connection management (global + home + foreign regions) with deterministic message routing per space and resource.
* Used the SDK as the primary correctness boundary for “where does this operation execute,” materially reducing integration errors across client surfaces.

**Backend Performance & Data-Layer Remediation**

* Led production root-cause analysis on MongoDB write-path bottlenecks in core messaging collections.
* Audited access patterns, compound index usage, retention requirements, and write amplification under load.
* Drove concrete remediation proposals (index rationalization, data separation, CQRS/event-sourcing alternatives with read views) and treated the database as a **costed execution surface** with explicit performance budgets rather than an opaque dependency. :contentReference[oaicite:2]{index=2}

**Release Engineering, QA, and Delivery Process**

* Established release governance for multi-repo, tightly coupled backend and client changes, favoring controlled integration deployments over fragile feature-sliced releases.
* Coordinated deep regression testing on isolated deployments to avoid blocking shared staging pipelines, and operationalized E2E execution via scheduled runs rather than gating deploys.
* Formalized task ownership, branching, PR visibility, and review/merge authority to eliminate ambiguity and reduce integration risk across teams. :contentReference[oaicite:3]{index=3}
* Supported Terraform-driven provisioning and validation of new regional deployments (“flavors”), including end-to-end rollout verification from infrastructure creation through controlled exposure.

**Internal Platform Leadership & Engineering Standards**

* Acted as a technical authority across Avaya Spaces and Vaco engagements, shaping architectural standards for large-scale MERN systems.
* Advocated for explicit separation of pure domain logic from effectful infrastructure (APIs, sockets, persistence), immutability as a default constraint, and dependency direction rules to keep systems reviewable as teams scaled.
* Delivered internal and public technical talks on high-powered MERN architecture, using real production failure modes to raise the bar on performance, correctness, and developer experience.

**Impact Summary**

* Enabled compliant global expansion without rewriting application-level business logic.
* Reduced production risk by making data residency and realtime delivery enforceable by architecture rather than convention.
* Converted tribal operational knowledge into documented, repeatable delivery and release systems that scaled across teams.
