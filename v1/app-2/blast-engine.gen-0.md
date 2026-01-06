---
title: app-2/blast-engine.gen-0.md
---

## Blast Engine (Consulting & Product Engineering)

**Founder / Principal Engineer**

Consulting-led engineering practice delivering **senior-level technical audits, architecture remediation, and production stabilization** for growth-stage companies operating high-impact, customer-facing platforms. Engagements focused on removing key-person dependency, restoring delivery confidence, improving performance and observability, and establishing scalable architectural direction across frontend, backend, and cloud infrastructure.

### Conexis — Vendor Management System (VMS Platform)

Enterprise SaaS platform supporting contingent workforce management for large clients, with strict integration, reporting, and authentication requirements.

* Brought in as senior technical authority to **unblock enterprise delivery risk** and reduce dependence on an offshore-only team with limited architectural ownership.
* Performed deep **backend (NestJS) and frontend (Next.js)** analysis, identifying gaps where framework capabilities were underutilized, leading to cascading performance and maintainability issues.
* Designed and implemented **SSO integration** with enterprise Azure Active Directory (OAuth / SAML flows), coordinating requirements across client security teams.
* Built a **cloud-hosted ingestion service** to consume external RSS job feeds, normalize data, detect updates, and synchronize into internal domain models with idempotency guarantees.
* Led **data modeling and reporting architecture** work: reverse-engineered organically-grown schemas, formalized relationships, and delivered API endpoints supporting reliable operational reporting.
* Conducted architectural debt mapping and documentation to enable future hiring, onboarding, and internal ownership transfer.
* Improved frontend performance by restructuring data-fetching strategies and reducing client-side over-fetching, aligning usage with Next.js server-side capabilities.

**Technologies:** TypeScript, Node.js, NestJS, Next.js, PostgreSQL, Azure, OAuth/SSO, GitHub Actions, Kubernetes

---

### Oralinx — Specialist Dentistry Network & Consumer Platform

Healthcare-adjacent professional network and consumer discovery platform with legal, disclosure, and performance constraints.

* Engagement focused on **technical audit, documentation, and architectural planning** rather than feature delivery.
* Addressed critical **key-person dependency** by producing system-level documentation covering architecture, operational flows, deployment practices, and known failure modes.
* Diagnosed and resolved **frontend performance bottlenecks** caused by inefficient data loading patterns as traffic scaled.
* Re-architected data-fetching strategy using **Next.js server-side rendering and progressive loading**, reducing initial payload size and time-to-interactive.
* Introduced shared data services to eliminate redundant client-side requests across independently mounted UI islands.
* Provided a **future-facing technical roadmap**, clearly separating acceptable legacy constraints from areas requiring investment to support growth, hiring, and investor scrutiny.

**Technologies:** TypeScript, React, Next.js, Node.js, GraphQL, PostgreSQL, Azure, Kubernetes

---

### Sector Growth — Integration Hub & SaaS Enablement

Multi-tenant integration platform supporting CRM, CMS, and commerce systems (Shopify, HubSpot, NetSuite, Zapier).

* Led architecture and implementation of **event-driven, cloud-native integration services**, supporting high-volume sync, reconciliation, and observability.
* Designed ledger-based data models and projection services to support **auditability, replay, and incremental reconciliation**.
* Defined webhook ingestion, scheduled backfills, and error-tracking strategies to ensure operational reliability at scale.
* Consulted directly with clients on operational workflows, data correctness requirements, and impact metrics.
* Delivered extensible APIs and internal tooling enabling the platform to be sold as a standalone product alongside consulting services.

**Technologies:** TypeScript, Node.js, GraphQL, Event-driven architecture, Cloud services, Multi-tenant SaaS design
