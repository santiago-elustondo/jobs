---
title: typefirst.cv.lean.gen.md
---

### TypeFirst *(Jan 2024 – Present)*

* *Founder / Principal Engineer*

Founder and principal engineer of TypeFirst, an independent consulting and technical leadership practice focused on **platform architecture, type-driven system design, and frontend/backend scalability**. Operated as senior technical authority across discovery, architecture, delivery, and organizational enablement for early-stage and growth companies, with a mandate to reduce key-person risk, stabilize delivery, and establish architectures that scale across teams rather than features.

Work consistently emphasized **platform leverage**: shared abstractions, enforceable contracts, monorepo hygiene, and developer-experience improvements that enable multiple engineers and teams to ship safely in parallel. Engagements combined hands-on implementation with architectural correction, documentation, hiring support, and stakeholder translation.

---

#### Sector Growth — Integration Platform & Monorepo Architecture  
**TypeScript | React | Node.js | MongoDB | GCP | HubSpot | Shopify | NetSuite**

Architect and technical lead for a series of bespoke integration platforms extending HubSpot beyond native capabilities for large commercial clients.

* Designed and implemented a **TypeScript monorepo** (Yarn workspaces, shared tsconfig) spanning React dashboards and stateless Node.js services, with **isomorphic domain models and service contracts** shared across client and server.
* Built a **type-safe action/RPC layer** with a shared async interface and registry, enabling client↔server calls with full autocomplete, compile-time contract enforcement, and build-time failure on incomplete implementations.
* Delivered cloud-hosted integration services combining **webhook ingestion, scheduled polling, and workflow orchestration**, coordinating complex cross-system business processes across Shopify, HubSpot, and NetSuite.
* Modeled reconciliation-centric data domains in MongoDB, maintaining a canonical internal representation while detecting, surfacing, and resolving discrepancies across multiple external systems of record.
* Built React-based operational dashboards allowing clients to inspect cross-system state, audit workflows, trigger manual syncs, and schedule consistency checks.
* Acted as senior technical counterpart to business stakeholders; translated ambiguous operational workflows into extensible, strictly-typed frameworks reused across engagements.
* Led hiring and oversight of contract engineers (including nearshore teams), while retaining ownership of framework-level and high-risk technical work.

---

#### Oralinx — Platform Assessment & Frontend Performance Remediation  
**TypeScript | Next.js | React | GraphQL | PostgreSQL | Azure | AKS | Terraform**

Senior technical consultant engaged to prepare a healthcare platform for scale, investor scrutiny, and team growth.

* Conducted a **full-stack architecture and operations audit**, externalizing system knowledge into reviewable documentation and eliminating reliance on tribal knowledge.
* Diagnosed and corrected **Next.js anti-patterns** where the application functioned as a hydration-gated SPA; moved critical data paths to SSR and restructured data-fetching to reduce request fan-out and perceived latency.
* Established normalized frontend data access patterns and caching strategies to stabilize performance under growing datasets.
* Codified infrastructure with Terraform and introduced production-like staging environments, materially reducing release anxiety and regression risk.
* Improved observability, logging discipline, and operational runbooks, enabling non-authors to diagnose issues independently.

---

#### Conexis VMS — Delivery Stabilization & Enterprise Hardening  
**TypeScript | NestJS | Next.js | PostgreSQL | Azure | Redis | OAuth | SAML**

Technical lead responsible for stabilizing delivery and reclaiming ownership of a business-critical vendor management platform.

* Recovered platform ownership from an offshore agency by centralizing repositories, credentials, and documentation under client control.
* Designed and implemented **enterprise SSO** (Azure AD via OAuth/SAML), coordinating directly with client security teams and documenting authentication boundaries and failure modes.
* Built a standalone **RSS ingestion service** to normalize externally published job postings into the platform’s internal domain model with idempotent, replay-safe semantics.
* Led deep data-modeling work to rationalize an organically grown PostgreSQL schema into reportable, defensible business views without destabilizing transactional paths.
* Hardened multi-tenancy assumptions across backend services, background jobs, and data access layers.
* Diagnosed and remediated frontend performance and architectural issues in a Next.js codebase that underutilized server capabilities, reducing duplicated queries and cascading client-side loads.
* Served as de facto technical lead for an offshore team, providing architectural correction, PR oversight, and hiring guidance to reduce long-term agency dependence.

---

#### Internal Platform Thinking & Technical Advocacy (TypeFirst)

In parallel with client delivery, TypeFirst served as a vehicle for **explicit platform thinking**: developing, testing, and articulating architectural patterns around TypeScript, React, and large-scale JavaScript systems.

* Advanced **type-driven architecture** patterns that use the TypeScript compiler as an enforcement mechanism for invariants, contracts, and architectural boundaries.
* Developed practical approaches to **AI-assisted development** constrained by strong type systems, reducing entropy in large codebases.
* Produced long-form technical writing and talks on frontend and platform engineering topics, including monorepo design, purity/immutability, state modeling, and developer-experience as a scaling constraint.
* Fed these patterns directly back into client work, ensuring that public thought leadership translated into concrete delivery leverage rather than abstract theory.
