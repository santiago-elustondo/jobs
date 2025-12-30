### typefirst
* 2024/01 - present
#### sector growth
* Architected a TypeScript monorepo (Yarn workspaces, shared top-level tsconfig) spanning a React SPA client and stateless Node.js backend, with shared isomorphic domain models and service contracts.
* Designed a type-safe, isomorphic action layer with a shared async interface and registry, enabling RPC-style client↔server calls with automatic method derivation, full autocomplete, and compile-time contract enforcement.
* Implemented server-side contract validation and endpoint generation, failing builds when action implementations were incomplete and enforcing serializable-only inputs and returns, ensuring consistent, drift-free APIs across runtime boundaries.
* Led the design and delivery of custom integration services extending HubSpot beyond native capabilities, supporting complex client-specific workflows across Shopify, HubSpot, and NetSuite.
* Architected cloud-hosted TypeScript microservices that combined webhook ingestion, scheduled polling, and workflow-driven actions to orchestrate cross-platform business processes.
* Designed reconciliation-centric data models backed by MongoDB, maintaining a canonical internal representation while detecting and resolving discrepancies across multiple external systems of record.
* Built operational dashboards and control surfaces (React) enabling clients to inspect cross-system state, trigger manual syncs, schedule consistency checks, and audit workflow execution.
* Acted as technical lead and client-facing authority, translating ambiguous business workflows into extensible, strictly-typed frameworks reused across engagements; led hiring, interviews, and oversight of contract engineers.
