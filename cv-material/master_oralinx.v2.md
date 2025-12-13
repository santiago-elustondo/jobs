# Oralinx — Specialist Network & Consumer Platform

**Senior Technical Consultant / Architectural Advisor**
**May 2024 – Aug 2024**

*(Client Engagement via TypeFirst Consulting)*

Oralinx is a **platform product** serving specialist dentistry networks and insurance-aligned provider groups. It combines a consumer-facing discovery portal with provider and network-facing tooling to support referrals, reviews, eligibility guidance, and compliant information exchange across practices. Organizations such as insurance networks and specialist groups onboard onto the platform to publish offerings, manage network participation, and route referrals under defined legal and disclosure constraints.

I was engaged as a **senior technical consultant** to assess platform readiness for growth, eliminate key-person dependency, remediate performance and reliability risks exposed by rising traffic, and establish architectural and operational clarity sufficient to support hiring, investment scrutiny, and long-term evolution.

---

## Engagement Conditions & Initial State

* Platform had successfully reached early-market adoption and funding, but:

  * System knowledge was siloed in one or two engineers.
  * Documentation was sparse, outdated, or informal.
  * Delivery velocity was constrained by operational anxiety rather than raw engineering capacity.
* Growth pressure exposed:

  * Frontend performance issues under increased consumer traffic.
  * Operational fragility in deployment and debugging workflows.
  * Difficulty onboarding new engineers into a coherent mental model of the system.

My mandate was to provide **senior-level architectural perspective** while executing targeted technical improvements that unblocked scale without destabilizing production.

---

## System Architecture (As Found)

### Frontend

* **Next.js (React)** application serving:

  * Consumer discovery and review flows
  * Provider-facing referral and network interaction surfaces
* Framework capabilities existed but were underutilized:

  * Most data fetching occurred client-side.
  * Pages exhibited cascading loads driven by sequential dependencies.
  * Repeated GraphQL queries across UI islands caused unnecessary request fan-out.

### Backend

* **Node.js** services supporting platform functionality.
* **GraphQL** API layer exposing domain entities such as practices, specialists, referrals, reviews, eligibility metadata, and disclosure states.
* **Legacy Go services** still present in the request path for select functionality, with an ongoing but incomplete migration toward Node-based services.

### Data & Persistence

* **PostgreSQL** as the primary datastore.
* Schema maturity varied:

  * Core entities were reasonably structured.
  * Peripheral and historical areas reflected organic growth and expedient modeling decisions.
* Query patterns had not been revisited as traffic and data volume increased.

### Infrastructure & Operations

* **Azure Kubernetes Service (AKS)** hosting core services.
* GitHub Actions in place for CI, but:

  * Deployments were largely manual.
  * Environment parity was weak.
  * Observability was minimal and reactive.

---

## Architectural Assessment & Knowledge Externalization

* Conducted a comprehensive **architecture and operations review**, covering:

  * Service topology and dependencies.
  * Frontend/backend data flow.
  * Deployment mechanics and failure modes.
* Produced durable documentation intended to:

  * Replace tribal knowledge with explicit system understanding.
  * Support onboarding of mid- and senior-level engineers.
  * Enable leadership to reason about technical trade-offs without relying on a single individual.
* Artifacts typically included:

  * System diagrams and request flows.
  * Identification of architectural exemplars vs legacy patterns.
  * A categorized technical debt inventory with remediation options.

---

## Frontend Performance & Data-Flow Remediation (Next.js)

### Observed Failure Mode

Despite using Next.js, the frontend behaved effectively as a client-heavy SPA:

* Sequential client-side data fetching caused cascading delays.
* Duplicate GraphQL queries were issued by independent page regions.
* Large initial payloads and hydration costs reduced perceived performance.

### Interventions

* Reworked data-loading strategy to **use server-side rendering where it materially improved UX**:

  * Applied SSR (`getServerSideProps`) for session-bound and above-the-fold data.
* Introduced a **shared data service layer** to coordinate fetches:

  * Aggregated GraphQL queries.
  * Eliminated duplicate requests across islands.
  * Normalized responses into a central client-accessible store abstraction.
* Parallelized fetch initiation to remove sequential gating effects.
* Reduced over-fetching by tightening GraphQL selections and consolidating queries.

These changes improved responsiveness while preserving the existing application structure.

---

## DevOps & Deployment Stabilization

* Introduced a **branch-based environment strategy** tied to GitHub Actions and AKS:

  * Automated deployments for non-production branches.
  * Safer feature validation paths without forcing premature production releases.
* Preserved manual production deployment control while dramatically reducing pre-release risk.
* Documented deployment and rollback procedures to support team growth and reduce operational anxiety.

---

## Observability & Operational Legibility

* Established a **baseline observability posture** appropriate for the platform’s scale:

  * Structured logging expectations.
  * Consistent request tracing and correlation discipline.
* Integrated services with Azure-native monitoring tooling to:

  * Surface latency and error patterns.
  * Enable diagnosis without reliance on specific individuals.
* Authored runbook-style documentation outlining:

  * Where to look when things fail.
  * Common failure modes and mitigation paths.

---

## Legacy Containment & Migration Planning

* Mapped the role of legacy Go services still participating in request flows.
* Identified:

  * High-risk migration points.
  * Areas suitable for containment rather than immediate rewrite.
* Produced a pragmatic roadmap aligning:

  * Technical cleanup
  * Team capacity
  * Business priorities

---

## Organizational Enablement & Technical Translation

* Acted as a technical counterpart to leadership during growth planning discussions.
* Translated product and business objectives into:

  * Architectural implications
  * Sequenced technical work
  * Hiring and onboarding requirements
* Provided evidence-backed technical reasoning suitable for validation by external advisors or investor-affiliated experts.

---

## Technologies

TypeScript, Node.js, Next.js, React, GraphQL, PostgreSQL, Azure Kubernetes Service (AKS), GitHub Actions, legacy Go services, containerized deployments, Azure monitoring stack
