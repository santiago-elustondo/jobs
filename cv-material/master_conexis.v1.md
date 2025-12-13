# Conexis VMS — Client Engagement (TypeFirst Consulting)

**Technical Lead / Technical Consultant**
**Jan 2024 – May 2024**
(Client engagement via TypeFirst Consulting)

Connexis VMS is a recruitment and staffing management platform enabling enterprise clients to manage contingent hiring workflows, including job publication, candidate intake, contract stages, document exchange, and provider communication through a unified portal.

Engaged to de-risk enterprise onboarding, resolve architectural deficiencies, and **transition platform ownership away from a single external agency toward internal control**.

---

## Strategic Mandate

* Reduce organizational and technical dependency on an external development agency.
* Stabilize delivery for an imminent enterprise client onboarding.
* Establish credible internal ownership across infrastructure, repositories, documentation, and domain knowledge.
* Act as a technical bridge between:

  * Enterprise clients and their engineering teams
  * Business leadership
  * Offshore developers
* Prepare the platform—architecturally and operationally—for multi-tenant enterprise usage.

---

## Ownership Transition & Asset Reclamation

* Led the **migration of platform ownership** from an external agency to Connexis-controlled infrastructure and tooling.
* Transferred and re-established ownership of:

  * Source code repositories
  * Cloud infrastructure (Azure)
  * Documentation (migrated, cleaned, and rationalized from agency-owned systems)
* Audited and consolidated fragmented documentation, filling gaps through direct interviews with engineers and stakeholders.
* Identified and explicitly documented:

  * Known system behavior
  * Unknown or poorly understood areas
  * Technical debt and risk concentrations
* Enabled leadership to operate from a **clear technical baseline** rather than inherited assumptions.

---

## Technical Leadership & Team Enablement

* Embedded directly into an offshore team operating semi-autonomously on sprint cycles.
* Provided senior-level technical oversight through:

  * Pull request review and architectural guidance
  * Direct problem-solving on complex or blocking issues
  * Clarification of framework-level and system-level concerns
* Mentored junior engineers, improving delivery velocity and confidence despite limited prior exposure to the full system.
* Served as a **communication amplifier**, leveraging Spanish fluency to reduce friction between offshore developers and local stakeholders.

---

## Hiring & Team Strategy

* Advised leadership on alternatives to agency-based staffing models.
* Recommended and executed a **hybrid hiring approach**, combining:

  * Local strategic leadership
  * Direct individual contributors in Colombia (non-agency)
* Led external hiring process for a senior individual contributor:

  * Sourced candidate
  * Conducted technical evaluation
  * Validated communication and collaboration fit
* Successfully placed a high-performing hire at a sustainable cost point, materially reducing agency dependence while retaining regional advantages.

---

## Enterprise Integration & Client-Facing Engineering

### Identity & Authentication

* Designed and implemented **enterprise SSO** using Azure Active Directory.
* Integrated OAuth / SAML-based authentication flows with client identity providers.
* Coordinated directly with enterprise client IT/security teams to validate assumptions, credentials, and login semantics.
* Audited an existing custom authentication system that lacked internal ownership or understanding.
* Documented authentication behavior and failure modes to reduce long-term operational risk.

---

### External Job Feed Ingestion

* Designed and delivered ingestion of enterprise job postings via **RSS feeds** already distributed to third-party job boards.
* Implemented a **standalone Node.js ingestion service**, deployed independently on Azure, that:

  * Monitored external feeds
  * Detected new and updated postings
  * Normalized and mirrored external data into the internal domain model
* Adapted database schemas and ingestion logic to support:

  * Idempotent updates
  * Source attribution
  * Ongoing reconciliation
* Enabled externally sourced jobs to function as first-class entities within the platform.

---

### Multi-Tenancy Hardening

* Re-evaluated the platform’s **theoretical multi-tenant design**, which had never been exercised in production.
* Led a systematic validation of tenant isolation across:

  * Request handling
  * Data access paths
  * Background processes
* Identified and remediated issues including:

  * Missing tenant scoping on requests
  * Hard-coded tenant identifiers
  * Implicit single-tenant assumptions
* Restored confidence that the platform could safely onboard additional enterprise tenants.

---

### Reporting & Data Modeling

* Led deep analysis of a PostgreSQL schema that had evolved organically without formal domain modeling.
* Existing reporting consisted primarily of raw exports and unstructured JSON.
* Conducted prolonged discovery with stakeholders to:

  * Clarify recruiting lifecycle concepts
  * Map implicit relationships across entities
* Designed backend APIs and data views to support meaningful client-facing reports without destabilizing write paths.
* Enabled business teams to answer client questions with data rather than ad-hoc explanations.

---

### Client Integration via Redis & Eventing

* Integrated outbound data sharing with an enterprise client via a **shared Redis instance on Azure**.
* Coordinated directly with the client’s engineering team to:

  * Negotiate key namespaces
  * Define data contracts
  * Avoid collisions with existing usage
* Introduced **Redis Pub/Sub** as a more explicit integration mechanism.
* Implemented Node.js-based publishers and consumers to support event-driven coordination between systems.

---

## Pre-Sales, Onboarding & Client Readiness

* Acted as technical partner to business leadership during enterprise onboarding.
* Assisted in:

  * Validating feature readiness
  * Identifying edge cases likely to surface during demos
  * Distinguishing product gaps from client misunderstandings
* Co-authored internal and external explanatory material:

  * Technical documentation
  * Client-facing walkthroughs
  * Presentation scripts for onboarding sessions
* Ensured that demonstrations and commitments were technically accurate and defensible.

---

## Technologies

TypeScript, Node.js, NestJS, React, PostgreSQL, Azure, OAuth, SAML, Redis, Redis Pub/Sub, RSS ingestion, REST APIs