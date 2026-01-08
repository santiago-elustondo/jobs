# Oralinx — Specialist Network & Consumer Platform

**Senior Technical Consultant / Architectural Advisor**
**May 2024 – Aug 2024**

*(Client Engagement via TypeFirst Consulting)*

Oralinx is a specialist dentistry network and consumer platform enabling patient discovery, practice search, referral routing within a provider network, and compliant information exchange governed by legal and disclosure guardrails. The platform supports consumer-facing search and reviews, provider-facing referral workflows, and operational administration under legal and privacy constraints.

I was engaged as a **senior technical consultant** to assess platform readiness for growth, eliminate key-person dependency, remediate performance and reliability risks exposed by rising traffic, and establish architectural and operational clarity sufficient to support hiring, investor scrutiny, and long-term evolution.

---

## Engagement Conditions & Initial State

Platform had successfully reached early-market adoption and funding, but
* Growth pressure exposed:
  * Core performance bottlenecks, with initial page load times degrading to unacceptable levels as datasets grew.
* Delivery constraints included:
  * Limited observability: effective diagnosis relied on a small number of overburdened individuals with implicit system knowledge.
  * Manual operations: Kubernetes cluster changes and deployments performed directly, with limited automation.
  * High operational anxiety: new features remained local until release due to the absence of a production-like staging environment.
  * Important features delayed or blocked by accumulated technical debt and the absence of a credible technical roadmap.
  * Unsustainable reliance on legacy services marked for deprecation.
  * System knowledge was siloed in one or two engineers.
  * Sparse system documentation was limiting both engineering velocity and stakeholder transparency.

My mandate was to provide **senior-level architectural perspective** while executing targeted technical improvements that unblocked scale without destabilizing production.

---

## System Architecture (As Found)

### Frontend

* **Next.js (React)** application serving:
  * Consumer discovery and review flows
  * Provider-facing referral and network interaction surfaces
* Problems:
  * Most data fetching occurred client-side, effectively treating Next.js as a client-rendered SPA.
  * Pages exhibited hydration-gated, cascading loads driven by sequential dependencies (auth → user context → downstream data).
  * GraphQL queries across independent UI islands caused unnecessary request fan-out and duplicated backend work.

### Backend

* **Node.js** services supporting platform functionality: authentication service, patient records service, practitioner directory service, application data service, events service, GraphQL gateway / aggregation layer
* **GraphQL** API layer exposing domain entities such as practices, specialists, referrals, reviews, eligibility metadata, and disclosure states.
* **Legacy Go services** still present in the request path for select functionality, with an ongoing but incomplete migration toward Node-based services.

### Data & Persistence

* **PostgreSQL** as the primary datastore.
* Schema maturity varied:
  * Core entities were reasonably structured.
  * Peripheral and historical areas reflected organic growth and expedient modeling decisions.
* Query patterns had not been revisited as traffic and data volume increased.

### Infrastructure & Operations

* **Azure Kubernetes Service (AKS)** hosting core service clusters.
* GitHub Actions in place for CI checks and reviews, but:
  * Deployments were largely manual.
  * Environment parity was weak.
  * Observability and alerting was limited.

---

## Architectural Assessment & Knowledge Externalization

* Conducted a comprehensive **architecture and operations audit**, covering:
  * Service topology and dependency graph.
  * Frontend/backend data flow, with a focus on data access patterns driving user-facing latency.
  * Deployment mechanics, failure modes, and operational choke points.
* Produced structured, **externally legible documentation** for:
  * New engineer onboarding.
  * External review by investors’ technical advisors or short-term experts.
  * Leadership planning and roadmap sequencing.
* Delivered artifacts including:
  * Current-state system map (services, ingress, domains, data stores).
  * “How it works” narratives for authentication/session flow, request routing, and data loading.
  * Technical debt register with severity and remediation options.
  * Target-state recommendations (what to modernize, what to contain, what to deprecate).
  * Deployment, diagnostic, and health-check guides for Azure and AKS, enabling on-call response without bespoke knowledge.

---

## Frontend Performance & Data-Flow Remediation (Next.js)

### Observed Failure Mode

Despite using Next.js, the frontend behaved effectively as a client-rendered SPA:
* Large initial client bundles with UX gated on hydration completion.
* Page sections loaded serially behind gating dependencies (auth/session → user context → downstream data).
* Redundant GraphQL queries executed independently by multiple UI islands.

### Interventions

* Re-architected page loads to use server-side rendering for session-bound and above-the-fold data, removing hydration-gated latency from critical paths.
* Introduced a normalized client-side data access and caching layer, exposed via hooks, to optimize the data subscriptions and fetches of stateful components. Consolidated isolated data updates and subscriptions into compound actions updating a centralized data store for local propagation of updates.

These changes materially reduced user-perceived latency while preserving the existing application structure, avoiding destabilizing rewrites.

---

## DevOps & Deployment Stabilization

* Codified the existing stack as Terraform, enabling reproducible deployment of fully independent vertical stacks. 
* Created two fully functional, production-like staging environments using a branch-based CI strategy tied to GitHub Actions and Azure Kubernetes Services. 
* Preserved explicit manual control over production deployments while drastically improving pre-production confidence and release safety.

---

## Observability & Operational Legibility

* Established a baseline observability posture appropriate for the platform’s scale:
  * Structured logging standards with consistent context propagation, enforced at compile time via typescript.
  * Consistent request tracing and correlation discipline.
* Integrated services with Azure-native monitoring tooling to:
  * Surface latency and error patterns.
  * Enable diagnosis of latency, errors, and failure modes without reliance on specific individuals.
* Authored runbook-style documentation outlining:
  * Where to look when things fail, and how to determine whether an issue is frontend, gateway, or downstream-service related.
  * Common failure modes and mitigation paths.

---

## Legacy Containment & Migration Planning

* Mapped the role of legacy Go services still participating in request flows. 
* Identified high-risk migration points and areas suitable for containment rather than immediate rewrite.
* A state-of-the-code overview of the frontend repository, identifying technical debt concentrations, ownership gaps, and migration priorities.

---

## Organizational Enablement & Technical Translation

* Functioned as a technical counterpart to leadership, converting business requirements (growth, compliance, usability, reliability) into:
  * Concrete architecture workstreams.
  * Sequenced technical debt remediation.
  * Hiring priorities and onboarding structures.
* Provided evidence-backed reasoning suitable for validation by external experts, reducing leadership’s dependence on “trust me” engineering narratives.

---

## Technologies

TypeScript, Node.js, Next.js, React, GraphQL, PostgreSQL, Azure Kubernetes Service (AKS), Terraform, GitHub Actions, Azure Monitor / Log Analytics / Application Insights, legacy Go services, containerized deployments
