## Vaco Toronto *(Jun 2020 – Nov 2021)*

* **Director, Technical Solution Delivery** *(Nov 2020 – Nov 2021)*
* **Technical Lead** *(Jun 2020 – Nov 2020)*

Senior technical delivery lead for Vaco Toronto consulting engagements, spanning assessment, architecture, execution governance, and escalation handling. Owned requirements/KPI capture, solution consensus, roadmap decomposition, team formation with recruiting, and sustained delivery under production and release pressure.  

### Avaya — Avaya Spaces *(Realtime + Multi-Region Platform)*

**TypeScript | React | Redux | Node.js | socket.io | Kubernetes | GCP | MongoDB | Redis Pub/Sub | GCP Pub/Sub | Terraform | k6**  

Technical lead on a globally distributed enterprise collaboration platform, delivering geo-constrained deployments (“flavors”), multi-region client routing, and cross-region realtime semantics under explicit data residency / sovereignty constraints, collaborating with a ~5 engineer team and client engineering leadership. 

#### Geographic Policy (Data Residency / Sovereignty) and “Flavors”

Defined and implemented the Geographic Policy (GP) model as an enforceable system constraint: data must exist in readable form only within regions permitted by a client’s GP until it reaches an authorized user; DR = GP compliance at rest; DS = GP compliance at rest + in transit. 
Operationalized GP into concrete tenancy semantics (primary company ownership, home region default, strict vs whitelist behavior), and space ownership rules (space housed in owning company’s home region; entry blocked when a space’s region is disallowed by a user’s GP; DM creation gated by recipient GP constraints). 

#### Platform-Agnostic Client DAL as a TypeScript SDK

Architected and delivered a platform-agnostic TypeScript client SDK to replace web-client-specific DAL logic and serve as the canonical client interface for both the existing web application and a React Native client team. SDK responsibilities included federation-aware endpoint selection and maintaining multiple websocket subscriptions while hiding geo-topology from feature teams (callers express intent at the business level; SDK resolves region via federation metadata and routes accordingly).  

#### Unified Cross-Region Realtime via “Mock Socket” Abstraction

Designed and implemented a Node.js realtime abstraction preserving the socket.io server programming model while enabling compliant cross-region messaging. Same-region delivery used socket.io + Redis adapter inside the regional cluster; cross-region delivery encrypted payloads, relayed them via global GCP Pub/Sub, and decrypted/emitted inside the destination region using local socket infrastructure—minimizing handler churn and avoiding a full rewrite.  
Drove the mechanics needed for correctness and debuggability in a distributed socket system: per-pod identity and routing (pod id + socket id on messages to ensure the correct point-of-contact pod executes operations), socket metadata propagation (`socket.update()` semantics rather than ad-hoc property assignment), handler registration patterns, and trace propagation for cross-region observability.  
Worked through key-management and state-of-the-world (SOT) requirements for encrypted multi-region messaging (client/server public keys, subscription inventories, connected-client-to-POC mapping), including flows for connect, join/subscribe, presence, and room broadcast/emit in a mixed-region topology. 

#### Production Performance / Data-Model Pressure (MongoDB Messaging)

Led investigations into MongoDB write bottlenecks in core messaging collections (e.g., `topicmessages`) driven by heavy/compound indexing and high write/update/delete pressure; pushed for access-pattern validation (rare query scans vs index coverage), retention/archival decisions, and evaluated structural remediation options including index rationalization, collection splits, and CQRS/event-sourcing with read-optimized MongoDB views built via aggregation pipelines. 

#### Release Governance, QA, and Regression Strategy Across Multi-Repo Systems

Established release mechanics and QA strategy across multiple repositories: PR visibility discipline (raising PRs into dependent repos early for review without blocking ongoing work), regression execution on dedicated deployments to avoid shared staging pipeline contention, and operationalizing E2E execution via Cloud Build triggers with long-running suites scheduled via Cloud Scheduler (daily runs, triage workflow into the team’s tracking system). 
Owned “new flavor” readiness as an explicit operational capability: Terraform builds the flavor’s infrastructure, deploy services, enable the flavor in DB, then allow company selection—validated end-to-end as a rehearsed procedure rather than an ad-hoc production gamble. 
Defined controlled rollout semantics (shadow vs beta), including super-admin override strategies (per-user overrides via a single `determineFlavorForUser()` function) to enable partial exposure when company-level toggles are too coarse. 
