# Conexis VMS — Managed Vendor Management Platform

**Technical Lead / Senior Technical Consultant**
**Jan 2024 – May 2024**

*(Client Engagement via TypeFirst Consulting)*

Conexis VMS is a **Vendor Management System (VMS) delivered as a managed recruitment service**, providing enterprise clients with outsourced contingent-hiring operations backed by custom client and vendor portals. The platform supports job intake and publication, candidate review, contract lifecycle management, document exchange, reporting, and regulated communication between enterprise clients, staffing vendors, and Conexis’ internal operations teams.

I was engaged as the **senior technical authority** to stabilize delivery, resolve enterprise-blocking technical risks, and transition the platform away from agency-owned infrastructure and tribal knowledge toward an internally sustainable engineering organization.

---

## Engagement Conditions & Initial State

* Platform was business-critical to an upcoming **enterprise client onboarding**, with contractual delivery timelines.
* Engineering execution was constrained by:

  * Full dependence on a single offshore development agency
  * Limited English-language client communication within the delivery team
  * Fragmented documentation and unclear ownership boundaries
* Leadership lacked a reliable technical picture of:

  * How authentication and integrations actually worked
  * Where data integrity guarantees did and did not exist
  * Whether the platform could safely support multiple enterprise tenants

My mandate spanned **architecture, delivery, hiring, documentation, and direct implementation**, with explicit responsibility for de-risking service delivery.

---

## System Architecture (As Recovered & Corrected)

### Backend

* **NestJS (Node.js)** services, organized around:

  * Decorator-based controllers
  * Service and domain layers
  * ORM-managed persistence
* **PostgreSQL** as the primary datastore:

  * Organically evolved schema
  * Partial denormalization
  * Mixed relational and JSONB usage
* Likely ORM: TypeORM or similar Nest-integrated ORM (based on usage patterns and conventions).

### Frontend

* **Next.js (React)** application in a **separate repository**.
* Nominally a server-capable framework, but in practice:

  * Predominantly client-side data fetching
  * Minimal SSR usage
  * Cascading request dependencies
  * Duplicated GraphQL queries across UI surfaces
* Frontend architecture had grown reactively rather than being intentionally designed.

### Infrastructure & Ops

* Azure-hosted infrastructure.
* VM-centric operational model with manual SSH-based workflows.
* Limited CI/CD automation and almost no observability.
* Authentication, deployments, and background processes depended on individual engineers’ memory.

---

## Ownership Transfer & Technical Baseline Recovery

* Led **full reclamation of platform ownership** from the external agency:

  * Migrated repositories into Conexis-controlled version control
  * Re-established ownership of Azure resources and credentials
  * Centralized documentation previously scattered across agency-owned tooling
* Conducted systematic interviews with engineers and stakeholders to:

  * Identify undocumented behavior
  * Surface unknowns and hidden coupling
* Produced structured technical documentation covering:

  * Current-state architecture
  * Authentication flows
  * Integration boundaries
  * Known technical debt and risk concentrations
* Converted inherited tribal knowledge into **explicit, reviewable artifacts** suitable for hiring, audits, and investor scrutiny.

---

## Identity, Security & Enterprise SSO

* Designed and implemented **enterprise SSO integration** with **Azure Active Directory**.
* Implemented OAuth / SAML authentication flows consistent with enterprise IT requirements.
* Coordinated directly with enterprise client security teams to validate:

  * Token issuance and verification
  * Claim mapping and user provisioning semantics
* Audited an existing custom authentication system that:

  * Used self-signed keys
  * Stored credentials in PostgreSQL
  * Had no shared internal understanding
* Documented authentication behavior, threat boundaries, and failure modes to reduce long-term operational risk.

---

## External Integrations & Data Ingestion

### Job Feed Ingestion

* Designed and implemented ingestion of enterprise job postings via **RSS feeds** already distributed to third-party job boards.
* Built a **standalone Node.js ingestion service**, deployed independently on Azure, responsible for:

  * Polling and monitoring RSS feeds
  * Detecting new and updated postings
  * Normalizing external data into Conexis’ internal domain model
* Implemented idempotent ingestion logic to support:

  * Replays
  * Partial failures
  * Update reconciliation
* Extended PostgreSQL schemas to track:

  * Source attribution
  * External identifiers
  * Sync state and timestamps
* Enabled externally sourced jobs to behave identically to internally created entities.

---

## Data Modeling, Reporting & Domain Rationalization

* Led deep analysis of a PostgreSQL schema that had grown incrementally without formal domain modeling.
* Existing reporting capabilities were limited to:

  * Raw table dumps
  * Semi-structured JSON exports
* Conducted prolonged discovery with business stakeholders to:

  * Clarify recruiting lifecycle stages
  * Identify implicit relationships across candidates, roles, vendors, contracts, and stages
* Designed a **conceptual domain model** suitable for reporting without destabilizing transactional paths.
* Implemented backend APIs and data views optimized for:

  * Client-facing reports
  * Operational insight for service teams
* Shifted reporting from ad-hoc explanations to defensible, queryable data.

---

## Multi-Tenancy Hardening (Service-Oriented)

* Re-evaluated the platform’s **theoretical multi-tenant design**, which had not been exercised in production.
* Validated tenant isolation across:

  * HTTP request paths
  * ORM query construction
  * Background jobs and ingestion services
* Identified and corrected issues including:

  * Missing tenant scoping
  * Hard-coded tenant identifiers
  * Implicit single-tenant assumptions
* Framed multi-tenancy in terms of **service isolation**, not just data isolation, consistent with Conexis’ managed-service delivery model.

---

## Eventing & Enterprise Client Coordination

* Integrated outbound data sharing with enterprise clients via a **shared Redis instance on Azure**.
* Negotiated namespaces and data contracts directly with client engineering teams.
* Introduced **Redis Pub/Sub** to formalize event-driven coordination.
* Implemented Node.js publishers and consumers to:

  * Emit operational events
  * Coordinate downstream processing
  * Avoid brittle polling-only integrations

---

## Frontend Architecture & Performance Remediation (Next.js)

* Diagnosed performance issues caused by:

  * Over-fetching
  * Sequential client-side data dependencies
  * Fragmented GraphQL usage
* Re-architected data access by:

  * Moving appropriate queries to **server-side rendering (Next.js)**
  * Introducing shared data-loading services
  * Aggregating GraphQL queries into compound fetches
* Reduced request fan-out and improved perceived latency by:

  * Eliminating duplicate queries
  * Front-loading async data fetches
* Established architectural guidance to prevent future regression into SPA-style anti-patterns.

---

## Team Leadership, Hiring & Enablement

* Acted as de-facto **technical lead** for an offshore engineering team.
* Provided senior oversight via:

  * Pull request review
  * Architectural correction
  * Direct intervention on complex issues
* Leveraged Spanish fluency to reduce communication friction and improve execution quality.
* Advised leadership on alternatives to agency-only staffing.
* Led hiring for direct individual contributors (Colombia-based), successfully reducing agency dependence while preserving delivery velocity.

---

## Pre-Sales, Onboarding & Service Readiness

* Partnered with business leadership during enterprise onboarding.
* Assisted with:

  * Feature readiness validation
  * Differentiating product gaps from client misunderstandings
  * Preparing technically accurate demos and onboarding narratives
* Co-authored internal and external documentation, walkthroughs, and presentation material used in client onboarding.

---

## Technologies

TypeScript, Node.js, NestJS, Next.js, React, GraphQL, PostgreSQL, Azure, OAuth, SAML, Redis, Redis Pub/Sub, RSS ingestion, REST APIs, CI/CD (GitHub Actions), ORM-based persistence