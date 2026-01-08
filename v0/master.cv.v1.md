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

### rangle
#### website
* Led internal website and design-system efforts, establishing UI patterns used both for Rangle’s public site and downstream client work.
* Re-architected hero / branding component by replacing JavaScript-driven geometry with SVG mask–based CSS rendering to eliminate resize jitter and re-render loops.
* Enabled CMS-driven visual customization by allowing geometric masks to be authored in figma, exported as SVG, and injected at runtime via Sanity-backed configuration.
* Delivered a stateless, memoizable component architecture, improving performance, responsiveness, and rendering smoothness across breakpoints.
* Extended the system to support SVG-native animation, enabling fluid, declarative shape and image motion without runtime layout computation.
* Integrated the component into the broader design-system framework, reinforcing a pattern of CMS-configurable, reusable primitives adaptable across projects and clients.
#### get ahead
* Led a 4-engineer agile development team as senior technical resource to deliver an embedded React application supporting live online therapy sessions and regulation-compliant clinical record generation.
* Took ownership of a high-ambiguity engagement, resolving major discrepancies between client requirements, design mockups, and AI pipeline assumptions while operating under a tight delivery timeline.
* Designed and delivered a micro-frontend React SPA packaged as a CI-produced artifact and embedded within a Flutter host application, with the host injecting serialized runtime arguments, strictly typed and validated using Zod.
* Defined the frontend–AI service contract, enabling in-session practitioner interactions to drive agentic generation workflows (RAG-based) for structured clinical notes, templates, and derived insights from live transcripts.
* Established a clear end-to-end data and execution model, spanning runtime embedding, backend orchestration, AI service invocation, and deterministic record output suitable for compliance and audit requirements.
* Acted as primary client-facing technical lead, translating unclear or conflicting inputs into concrete implementation plans, stabilizing team confidence, and unblocking delivery through direct architectural decisions.
* Successfully delivered the project to client satisfaction, resulting in a follow-on engagement to lead a larger greenfield platform for therapist practitioners.
#### jet blue
* Embedded as a senior technical authority on an early-stage JetBlue engagement to stabilize delivery, support architectural decision-making, and build confidence across both client stakeholders and the delivery team.
* Supported the architectural definition of a centrally maintained, application-agnostic design system intended to unify brand and UX across a large, heterogeneous consumer web surface.
* Designed a web-component–first design system strategy capable of spanning React, Angular, jQuery, and legacy platforms (ASP.NET, Java Spring Boot) without framework lock-in.
* Architected a monorepo-based system with raw web components as the canonical core, complemented by framework-specific TypeScript packages for React and Node-based consumers.
* Evaluated and spiked multiple authoring approaches (Lit, Stencil, no-framework custom elements), ultimately selecting Lit based on technical tradeoffs and client feedback.
* Delivered the design system via multiple distribution channels, including private npm packages and CDN-hosted web components, enabling drop-in adoption through standard HTML tags.
* Presented the project’s findings on web components as a foundation for cross-framework design systems at a professional community event on behalf of Rangle.

### lululemon
* Built and deployed a horizontal loyalty feature set across a large-scale React/Node platform composed of independently owned microfrontends, integrated via Webpack Module Federation.
* Architected a dedicated loyalty engineering repository and component library designed for safe adoption across teams, enabling consistent loyalty behavior in checkout, product, search, and account surfaces.
* Delivered self-contained, error-bounded React components with SSR-compatible serializable props, internal context wiring, and error boundaries, minimizing integration risk for host applications.
* Integrated observability and control primitives directly into exported components, including isolated Sentry alerting, analytics events, Contentful-driven configuration, and centrally managed feature flags.
* Established a cross-repo integration workflow, submitting and coordinating PRs across multiple team-owned microfrontends to mount and approve loyalty components within their release pipelines.
* Designed a local development and demo strategy using monorepo tooling and Git submodules of host microfrontends, enabling live dependency resolution, bundle impact analysis, and peer-dependency validation prior to rollout.
* Navigated strict architectural, security, and compliance review—particularly for checkout-critical surfaces—securing approval through clear implementation plans and bounded integration contracts.