# Oralinx — Specialist Network & Consumer Platform

**Senior Technical Consultant / Architectural Advisor**
**May 2024 – Aug 2024**

*(Client Engagement via TypeFirst Consulting)*

Oralinx is a specialist dentistry network and consumer portal enabling patient discovery, practice search, referral routing within a provider network, and compliant information exchange governed by disclosure guardrails. The platform supports consumer-facing search and reviews, provider-facing referral workflows, and operational administration under legal and privacy constraints.

I was engaged as a **senior technical consultant** to assess platform readiness for growth, eliminate key-person dependency, remediate performance and reliability risks exposed by rising traffic, and establish architectural and operational clarity sufficient to support hiring, investment scrutiny, and long-term evolution.

---

## Engagement Conditions & Initial State

Platform had successfully reached early-market adoption and funding, but
* Growth pressure exposed:
  * Core performance bottlenecks. Initial page loading times becoming unacceptable with growing datasets.
* Delivery constraints included:
  * Limited observability: diagnostic ability reliant on specific overburdened individuals.
  * Manual operations: Kubernetes cluster changes and deployments performed directly, with limited automation.
  * High operational anxiety: new features remained local until release time, because there was no safe staging path resembling production.
  * Important features delayed or blocked by technical debt and backlogged technical roadmapping tasks.
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
  * Most data fetching occurred client-side.
  * Pages exhibited cascading loads driven by sequential dependencies.
  * Repeated GraphQL queries across UI islands caused unnecessary request fan-out.

### Backend

* **Node.js** services supporting platform functionality: authentication service, patient records service, practicitioner directory service, application data service, events service, graph service (GraphQL aggregator API)
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
  * Frontend/backend data flow, with a focus on fata access patterns driving user-facing latency.
  * Deployment mechanics, failure modes, and operational choke points.
* Produced structured documentation for:
  * New engineer onboarding.
  * External review by investors’ technical advisors or short-term experts.
  * Leadership planning and roadmap sequencing.
* Delivered artifacts including:
  * Current-state system map (services, ingress, domains, data stores).
  * “How it works” narratives for authentication/session flow, request routing, and data loading.
  * Technical debt register with severity and remediation options.
  * Target-state recommendations (what to modernize, what to contain, what to deprecate).
  * Deployment, diagnostic, and health check guides using Azure console and AKS. 

---

## Frontend Performance & Data-Flow Remediation (Next.js)

### Observed Failure Mode

Despite using Next.js, the frontend behaved effectively as a client-heavy SPA:
* Large initial client bundle and hydration dependence.
* Page sections loaded serially behind gating dependencies (auth/session → user context → downstream data).
* Redundant queries executed by multiple islands independently.

### Interventions

* Partially re-architected page loads to use **server-side rendering** for session-bound and above-the-fold data.
* Introduced a **normalized client-side caching & data service abstraction exposed via hooks** to optimize the data subscriptions and fetches of stateful components. Consolidated isolated data updates and subscriptions into compound actions updating a centralized data store for local propagation of updates.

These changes improved responsiveness while preserving the existing application structure.

---

## DevOps & Deployment Stabilization

* Codified existing stack as Terraform files capable of deploying fully independent vertical stacks. Created 2 fully functional and independent staging environments, complete with a branch-based environment strategy in CI tied to GitHub Actions and AKS. Preserved manual control over production deployments (explicitly) while drastically improving pre-prod confidence.

---

## Observability & Operational Legibility

* Established a **baseline observability posture** appropriate for the platform’s scale:

  * Structured logging expectations.
  * Consistent request tracing and correlation discipline.
* Integrated services with Azure-native monitoring tooling to:

  * Surface latency and error patterns.
  * Enable diagnosis without reliance on specific individuals.
* Authored runbook-style documentation outlining:

  * Where to look when things fail.
  * Common failure modes and mitigation paths.

---

## Legacy Containment & Migration Planning

* Mapped the role of legacy Go service still participating in request flows. Identified high-risk migration points and areas suitable for containment rather than immediate rewrite.
* A state-of-the-client overview of different areas of the client, noting technical debt where present, guidelines, and prioritization.

---

## Organizational Enablement & Technical Translation

* Functioned as a technical counterpart to leadership, converting business requirements (growth, compliance, usability, reliability) into:

  * Concrete architecture workstreams.
  * Sequenced technical debt remediation.
  * Hiring priorities and onboarding structures.
* Provided evidence-backed reasoning suitable for validation by external experts, reducing leadership’s dependence on “trust me” engineering narratives.

---

## Technologies

TypeScript, Node.js, Next.js, React, GraphQL, PostgreSQL, Azure Kubernetes Service (AKS), GitHub Actions, legacy Go services, containerized deployments, Azure monitoring stack (Monitor / Log Analytics / App Insights)
