# Conexis VMS — Vendor Management Platform
**Technical Lead / Senior Technical Consultant**
**Jan 2024 – May 2024**
**Client engagement via TypeFirst Consulting**
* Served as senior technical authority for a managed Vendor Management System (VMS) supporting enterprise contingent-hiring operations.
* Engaged to stabilize delivery for an imminent enterprise client onboarding with contractual timelines.
* Took explicit responsibility for de-risking service delivery across architecture, integrations, security, operations, and team structure.
* Led transition of platform ownership from a single offshore development agency to an internally sustainable engineering organization.
* Assessed and corrected inherited architecture spanning backend services, frontend application, data model, and infrastructure.
* Recovered a reliable technical baseline in an environment with fragmented documentation and unclear ownership boundaries.
* Analyzed system behavior where leadership lacked clarity on authentication, data integrity, and multi-tenant safety.
* Led full reclamation of platform assets from the external agency.
* Migrated source code repositories into Conexis-controlled version control.
* Re-established ownership of Azure infrastructure, credentials, and deployment resources.
* Centralized documentation previously scattered across agency-owned tools.
* Conducted systematic interviews with engineers and stakeholders to surface undocumented behavior and hidden coupling.
* Converted tribal knowledge into explicit, reviewable technical artifacts.
* Produced structured documentation covering current-state architecture, authentication flows, integration boundaries, and technical debt.
* Created documentation suitable for hiring, audits, and external technical review.
* Assessed backend architecture built on NestJS (Node.js) with decorator-based controllers, service layers, and ORM-managed persistence.
* Evaluated organically evolved PostgreSQL schema with partial denormalization and mixed relational / JSONB usage.
* Analyzed ORM usage patterns (TypeORM or similar) and their implications for data integrity and query behavior.
* Assessed frontend architecture implemented as a separate Next.js (React) repository.
* Identified predominant client-side data fetching despite nominal SSR capabilities.
* Diagnosed cascading request dependencies and inefficient data-loading patterns.
* Identified duplicated GraphQL queries across frontend UI surfaces.
* Determined frontend architecture had grown reactively rather than through intentional design.
* Assessed infrastructure hosted on Azure using a VM-centric operational model.
* Identified reliance on manual SSH-based workflows for deployments and maintenance.
* Identified minimal CI/CD automation and near-absence of observability.
* Documented operational risk caused by authentication, deployments, and background processes relying on individual engineers’ memory.
* Designed and implemented enterprise single sign-on (SSO) using Azure Active Directory.
* Implemented OAuth and SAML authentication flows aligned with enterprise IT requirements.
* Coordinated directly with enterprise client security teams on identity integration.
* Validated token issuance, verification, claim mapping, and user provisioning semantics.
* Audited an existing custom authentication system using self-signed keys and PostgreSQL-stored credentials.
* Identified lack of shared understanding of authentication behavior and threat boundaries.
* Documented authentication architecture, trust assumptions, and failure modes.
* Reduced long-term security and operational risk through explicit identity documentation.
* Designed and implemented ingestion of enterprise job postings via RSS feeds.
* Built a standalone Node.js ingestion service deployed independently on Azure.
* Implemented polling and monitoring of external RSS feeds.
* Detected new and updated job postings from external sources.
* Normalized external job data into Conexis’ internal domain model.
* Implemented idempotent ingestion logic supporting replays, partial failures, and reconciliation.
* Extended PostgreSQL schemas to track external source attribution and identifiers.
* Added sync state and timestamp tracking for externally sourced entities.
* Enabled externally sourced jobs to behave identically to internally created jobs.
* Led deep analysis of PostgreSQL schema that had grown without formal domain modeling.
* Identified reporting limitations driven by raw table dumps and semi-structured JSON exports.
* Conducted extended discovery with business stakeholders to clarify recruiting lifecycle concepts.
* Identified implicit relationships across candidates, roles, vendors, contracts, and workflow stages.
* Designed a conceptual domain model suitable for reporting without destabilizing transactional paths.
* Implemented backend APIs and data views optimized for client-facing reporting.
* Enabled operational teams to answer client questions with queryable data rather than ad-hoc explanations.
* Shifted reporting posture from narrative interpretation to defensible data outputs.
* Re-evaluated the platform’s theoretical multi-tenant design, which had not been exercised in production.
* Validated tenant isolation across HTTP request handling.
* Validated tenant scoping in ORM query construction.
* Audited background jobs and ingestion services for tenant isolation.
* Identified missing tenant scoping and hard-coded tenant identifiers.
* Corrected implicit single-tenant assumptions throughout the codebase.
* Framed multi-tenancy in terms of service isolation rather than data isolation alone.
* Aligned multi-tenant design with Conexis’ managed-service delivery model.
* Integrated outbound data sharing with enterprise clients via a shared Redis instance on Azure.
* Negotiated Redis key namespaces and data contracts with client engineering teams.
* Introduced Redis Pub/Sub to formalize event-driven integration.
* Implemented Node.js publishers and consumers for operational event emission.
* Enabled coordination of downstream processing without brittle polling-only integrations.
* Diagnosed frontend performance issues caused by over-fetching and sequential client-side dependencies.
* Identified fragmented GraphQL usage contributing to request fan-out.
* Re-architected frontend data access to leverage Next.js server-side rendering where appropriate.
* Introduced shared data-loading services to centralize frontend data access.
* Aggregated GraphQL queries into compound fetches to reduce request overhead.
* Reduced duplicated requests and improved perceived latency.
* Front-loaded asynchronous data fetches to improve page responsiveness.
* Established architectural guidance to prevent regression into SPA-style anti-patterns.
* Acted as de-facto technical lead for an offshore engineering team.
* Provided senior oversight through pull request review and architectural guidance.
* Intervened directly on complex or blocking technical issues.
* Leveraged Spanish fluency to reduce communication friction with offshore developers.
* Improved execution quality and delivery confidence through direct collaboration.
* Advised leadership on alternatives to exclusive agency-based staffing.
* Led hiring of direct individual contributors in Colombia.
* Reduced agency dependence while maintaining delivery velocity.
* Partnered with business leadership during enterprise client onboarding.
* Assisted with feature readiness validation prior to client launch.
* Helped distinguish true product gaps from client misunderstandings.
* Prepared technically accurate demos and onboarding narratives.
* Co-authored internal and client-facing documentation and walkthroughs.
* Supported pre-sales and onboarding with defensible technical explanations.
* Enabled leadership to operate from a clear technical baseline rather than inherited assumptions.
* Restored confidence that the platform could safely support enterprise and multi-tenant usage.