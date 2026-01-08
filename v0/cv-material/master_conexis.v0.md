# Conexis VMS — Client Engagement (TypeFirst Consulting)

* **Technical Lead / Technical Consultant**
* Jan 2024 – May 2024
* (Client engagement via TypeFirst Consulting)

Conexis is a **recruitment and staffing management platform** providing enterprise clients with a self-service portal for managing the full lifecycle of contingent hiring. The platform enables client organizations to publish roles, review candidates, manage contract stages, exchange documents, and communicate with staffing providers operating on their behalf.

I was engaged to stabilize delivery, resolve integration-blocking technical risks for a major enterprise client, and progressively transfer architectural ownership from an offshore agency team to an integrated in-house engineering team.

---

## Mandate & Context

* Joined during a period of **delivery risk** driven by:
  * Heavy reliance on an offshore engineering team with limited client-facing communication capacity.
  * Accumulated architectural and operational debt.
  * Imminent deadlines tied to onboarding a high-value enterprise customer.
* Acted as a **technical intermediary** between:
  * Enterprise client stakeholders (identity, integrations, reporting requirements)
  * Business development leadership
  * Offshore engineering team
* Established a path toward **local technical ownership**, documentation, and team expansion.

---

## Platform Overview (As Found)

* **Backend:** NestJS, NextJS, Node.js
* **Frontend:** React SPA served via NestJS
* **Database:** PostgreSQL with ORM-managed schema (legacy, partially denormalized)
* **Infrastructure:** Cloud-hosted, VM-centric deployments with manual SSH-based operations
* **Authentication:** Custom, minimal in-house implementation with limited documentation

---

## Key Technical Contributions

### Enterprise Single Sign-On (SSO)

* Designed and delivered **enterprise SSO integration** with client **Azure Active Directory**.
* Implemented OAuth / SAML-based authentication flows aligned with client security requirements.
* Coordinated directly with client IT/security teams to validate:

  * Identity assertions
  * Token handling
  * Account provisioning semantics
* Audited and documented the existing authentication system, which had:

  * Custom key-signing logic
  * Limited team understanding
  * No prior external identity integrations
* Introduced clearer authentication boundaries and documentation to reduce future risk.

---

### External Job Feed Ingestion (RSS → Platform)

* Implemented ingestion of **external job posting feeds** already distributed by the client to third-party job boards.
* Designed a **standalone Node.js ingestion service** that:

  * Monitored enterprise RSS feeds
  * Detected new and updated job postings
  * Normalized and mirrored external data into the platform’s internal domain model
* Deployed service independently (Azure), operating as a long-running, fault-tolerant process.
* Adapted internal schemas to support:

  * Source attribution
  * Update reconciliation
  * Idempotent ingestion behavior
* Enabled the platform to treat externally sourced jobs as first-class entities, indistinguishable from manually created postings.

---

### Reporting & Data Model Rationalization

* Led a deep **domain-level analysis** of an organically grown PostgreSQL schema supporting recruiting workflows.
* Existing reporting consisted primarily of raw table exports and semi-structured JSON blobs.
* Conducted structured discovery with stakeholders to:

  * Clarify business concepts and lifecycle stages
  * Identify implicit relationships across entities (candidates, roles, contracts, providers, stages)
* Translated findings into:

  * A reportable conceptual model
  * Backend API endpoints optimized for frontend consumption
* Enabled richer, client-facing reporting without destabilizing legacy write paths.

---

### Architectural Assessment & Technical Debt Mapping

* Performed a comprehensive assessment of **framework usage, infrastructure practices, and ownership gaps**.
* Identified risks including:

  * Underutilized NestJS capabilities
  * VM-centric operations with manual intervention
  * Limited internal understanding of core security mechanisms
* Produced clear documentation outlining:

  * Existing system behavior
  * High-risk areas
  * Recommended remediation and modernization paths
* Provided leadership with a **credible technical baseline** for future refactors and team growth.

---

## Team & Delivery Leadership

* Acted as de-facto **technical lead** for an offshore team:

  * Clarifying requirements
  * Translating client constraints into implementable tasks
  * Unblocking delivery through direct technical intervention
* Supported hiring and team transition planning by:

  * Identifying skill gaps
  * Assisting with technical interviews
  * Advising on local vs offshore role allocation
* Restored delivery confidence for both internal stakeholders and enterprise client.

---

## Technologies

TypeScript, Node.js, NestJS, React, PostgreSQL, Azure, OAuth / SAML, RSS ingestion, REST APIs

---

# Notes on Resume Strategy (Important)

* This is **master-resume depth**.
* For most applications, this collapses to **4–6 bullets** emphasizing:

  * Enterprise SSO
  * External system integrations
  * Data modeling & reporting
  * Cross-team technical leadership

Critically, this now reads as:

> “Senior consultant brought in to rescue delivery, integrate an enterprise client, and impose architectural clarity.”

—which is exactly what happened.

---

## Next Steps (Suggested)

1. I can:

   * Collapse this into **three different targeted variants** (IC-heavy, Lead-heavy, Platform-heavy), or
   * Apply the same treatment to **Auralink** and **Sector Growth**, or
   * Integrate this cleanly into the **TypeFirst Consulting** section we defined earlier.

Say which direction you want to go.
