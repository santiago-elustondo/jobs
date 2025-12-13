# Oralinx — Client Engagement (TypeFirst Consulting)

## Oralinx

**Senior Technical Consultant / Architectural Advisor**
(Client engagement via TypeFirst Consulting)

Oralinx is a professional network and consumer portal for dentistry specialists, enabling patient discovery, intra-network referrals, and compliant information exchange across practices. The platform embeds legal and regulatory guardrails governing disclosure, referrals, and data handling, supporting both consumer discovery and provider-to-provider workflows.

I was engaged during a growth transition following acquisition and early funding, where increased traffic, organizational scaling, and regulatory obligations had outpaced the platform’s internal technical maturity.

---

## Engagement Mandate

* Provide **senior technical oversight** where the internal team lacked architectural leadership bandwidth.
* Reduce **key-person dependency** on one or two engineers holding siloed system knowledge.
* Produce documentation and architectural clarity sufficient to:

  * Onboard new hires
  * Support investor and external expert review
  * Enable confident, long-term platform evolution
* Address **production performance issues** emerging under increased traffic.
* Establish pragmatic DevOps and deployment guardrails without destabilizing production.

---

## Platform Context (As Found)

* **Frontend:** Next.js / React (underutilized SSR, islands, and data-fetching capabilities)
* **Backend:** Node.js (with legacy Golang services still in operation)
* **APIs:** GraphQL
* **Database:** PostgreSQL
* **Infrastructure:** Azure Kubernetes Service (AKS)
* **DevOps:** Minimal automation; manual cluster and production management
* **Observability:** Effectively absent; diagnosis dependent on individual engineers

---

## Architectural Assessment & Documentation

* Conducted a **full technical audit** spanning:

  * Application architecture
  * Infrastructure topology
  * Deployment practices
  * Data access patterns
* Produced clear, structured documentation covering:

  * Current-state architecture
  * Known technical debt and risk areas
  * Components suitable as reference implementations
  * Legacy systems requiring containment or deprecation
* Authored **forward-looking architectural guidance** aligning:

  * Business growth goals
  * Regulatory and legal constraints
  * Engineering capacity and hiring plans
* Provided material suitable for validation by:

  * External technical advisors
  * Investor-supplied engineering reviewers

---

## Performance & Frontend Architecture Improvements

* Diagnosed **front-facing latency and load-time issues** caused by:

  * Inefficient data fetching
  * Cascading client-side dependencies
  * Overfetching and duplicated GraphQL queries
* Re-architected frontend data access by:

  * Moving appropriate data fetching to **server-side rendering (Next.js)**
  * Introducing **progressive disclosure** via island-style component boundaries
  * Front-loading asynchronous data requests to eliminate sequential blocking
* Implemented a shared **data service layer** to:

  * Aggregate GraphQL queries
  * Eliminate duplicate fetches across islands
  * Provide a central store (Redux-like) consumable by multiple UI surfaces
* Reduced payload size and request fan-out by consolidating queries and removing redundant data.

These changes materially improved perceived responsiveness without requiring wholesale rewrites.

---

## DevOps & Deployment Stabilization

* Introduced a **branch-based deployment strategy** tied to GitHub Actions and AKS.
* Enabled non-production environments suitable for:

  * Feature validation
  * Stakeholder review
  * Safer release preparation
* Preserved **manual production control** (by design) while eliminating the prior “local-only until release” risk profile.
* Established deployment and operational documentation sufficient for:

  * New engineer onboarding
  * Reduced reliance on tribal knowledge

---

## Organizational & Strategic Support

* Acted as a **technical translator** between:

  * Business leadership
  * Product stakeholders
  * Engineers
* Participated in higher-level discussions on:

  * Feature prioritization
  * Regulatory and legal considerations
  * Trade-offs between velocity, safety, and maintainability
* Provided leadership with **evidence-backed technical reasoning**, enabling confident decision-making without requiring them to trust opaque engineering intuition.

---

## Technologies

TypeScript, Node.js, Next.js, React, GraphQL, PostgreSQL, Azure Kubernetes Service (AKS), GitHub Actions