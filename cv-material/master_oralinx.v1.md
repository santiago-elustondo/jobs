# Oralynx — Managed Specialist Network & Consumer Portal

**Senior Technical Consultant / Architectural Advisor**
**May 2024 – Aug 2024** 

*(Client Engagement via TypeFirst Consulting)*

Oralynx is a specialist dentistry network and consumer portal enabling patient discovery, practice search, referral routing within a provider network, and compliant information exchange governed by disclosure guardrails. The platform supports consumer-facing search and reviews, provider-facing referral workflows, and operational administration under legal and privacy constraints typical of healthcare-adjacent systems.

I was engaged as a **senior technical authority** to (1) eliminate key-person dependency, (2) produce a defensible technical baseline for hiring and scale, (3) remediate performance bottlenecks under rising traffic, and (4) introduce pragmatic deployment and observability foundations suitable for a growing team operating on Azure.

---

## Engagement Conditions & Initial State

* Organization was transitioning from “startup build mode” to “scale and operate,” with:

  * Increased traffic exposing latent performance and reliability issues.
  * Siloed knowledge concentrated in one or two engineers.
  * Minimal onboarding material, weak runbooks, and poor system legibility.
* Delivery constraints included:

  * Limited observability: diagnosis required asking a specific person “where to look.”
  * Manual operations: Kubernetes cluster changes and deployments performed directly, with limited automation.
  * High operational anxiety: new features remained local until release time, because there was no safe staging path resembling production.

My mandate combined **architectural audit + operational enablement + targeted remediation**, with direct responsibility for producing artifacts leadership could use to hire, prioritize, and execute.

---

## System Architecture (As Recovered & Normalized)

### Frontend

* **Next.js (React)** consumer portal and internal/admin surfaces.
* Framework usage existed but was under-leveraged:

  * Too much client-side fetching and hydration-driven composition.
  * Cascading loads caused by sequential dependencies between UI sections.
  * Over-fetching and duplicated requests across page regions.

### Backend

* **Node.js** services supporting core portal workflows and provider network functionality.
* **GraphQL** API layer aggregating access to core domain entities (providers, practices, referrals, reviews, eligibility/disclosure states).
* **Legacy Go services** in the critical path for select workloads; the organization was moving away from these but they remained operationally relevant for architecture, migration planning, and risk assessment.

### Data & Persistence

* **PostgreSQL** as primary system of record for network and portal entities.
* Mixed schema maturity typical of a growing product:

  * Some areas well-modeled; other areas shaped by historical constraints and patchwork evolution.
  * Query patterns increasingly expensive as dataset and traffic grew.

### Infrastructure & Ops

* **Azure Kubernetes Service (AKS)** hosting core services.
* CI existed (GitHub Actions), but deployments were still largely manual and cluster-managed directly.
* Observability was insufficient for rapid diagnosis and regression prevention (no reliable “single pane” for latency, error budgets, or saturation).

---

## Architectural Assessment & Technical Baseline Recovery

* Performed a full **architecture and operations audit**, spanning:

  * Service topology and dependency graph.
  * Deployment flows and release risk profile.
  * Data access patterns driving user-facing latency.
  * Failure modes and operational choke points.
* Produced structured documentation intended for:

  * New engineer onboarding.
  * External review by investors’ technical advisors or short-term experts.
  * Leadership planning and roadmap sequencing.
* Delivered concrete artifacts, typically including:

  * Current-state system map (services, ingress, domains, data stores).
  * “How it works” narratives for authentication/session flow, request routing, and data loading.
  * Technical debt register with severity and remediation options.
  * Target-state recommendations (what to modernize, what to contain, what to deprecate).

This work was explicitly oriented toward replacing “tribal knowledge” with **verifiable system understanding**.

---

## Frontend Performance Remediation (Next.js)

### Problem Pattern

The portal behaved “like an SPA wearing Next.js clothing”:

* Large initial client bundle and hydration dependence.
* Page sections loaded serially behind gating dependencies (auth/session → user context → downstream data).
* Redundant queries executed by multiple islands independently, multiplying request volume and latency.

### Interventions

* Re-architected data loading to use **server-side rendering** where it materially improved perceived latency and reduced client round-trips.

  * Applied `getServerSideProps` / SSR patterns for high-impact above-the-fold data and session-dependent payloads.
* Introduced a shared **data service layer** to eliminate duplicate fetches across page regions:

  * Aggregated GraphQL queries into compound fetches.
  * Normalized responses into a centralized client cache / store abstraction (Redux-like in behavior, whether or not Redux itself was used).
* Implemented **progressive disclosure** intentionally:

  * Explicit skeleton/placeholder states.
  * Parallelized fetch initiation to eliminate sequential blocking.
  * Reduced cascading effects by front-loading requests when JS mounted and/or moving them to SSR.
* Reduced over-fetching and payload bloat:

  * Tightened GraphQL selections.
  * Removed duplicate fields.
  * Consolidated queries that were previously scattered across components.

### Resulting Outcome (Resume-Safe)

* Improved user-facing load latency by removing sequential dependency chains and collapsing duplicated fetch patterns into fewer, predictable requests.
* Increased architectural clarity in the frontend by enforcing a coherent data-loading strategy compatible with Next.js strengths.

---

## DevOps & Release Safety Improvements (AKS + GitHub Actions)

* Introduced a **branch-based deployment strategy** suitable for a team without mature platform engineering:

  * Automated non-production deployments per branch or per environment class.
  * Preserved manual control over production deployments (explicitly) while drastically improving pre-prod confidence.
* Implemented CI/CD wiring between:

  * GitHub Actions build/test stages
  * Container build/publish (likely Azure Container Registry or equivalent)
  * AKS deploy steps (commonly via Helm/Kustomize manifests or `kubectl` apply—exact mechanism not critical, but the functional result is)
* Established a repeatable path to test and demonstrate features in an environment that resembles production, replacing the prior “local until release” failure mode.

---

## Observability & Operational Legibility

Oralynx’s operational constraint was not “lack of tools,” but “lack of visibility and ownership.”

* Established a practical observability baseline appropriate to Azure + Kubernetes:

  * Standardized logging expectations (structured logs, correlation IDs, request tracing discipline).
  * Wired service telemetry into Azure-native monitoring (Azure Monitor / Log Analytics / Application Insights are the typical stack, and consistent with the environment).
* Produced runbook-grade documentation:

  * Where to look for symptoms (latency, error spikes, pod churn).
  * How to reproduce common failure modes.
  * How to triage issues without requiring a specific individual.

The explicit goal was **de-risking hiring and on-call**, not building a perfect platform.

---

## Legacy Containment & Migration Planning (Go → Node)

* Mapped where legacy Go services remained in the request path.
* Identified:

  * Coupling points and migration hazards.
  * Areas where rewriting was high-risk vs areas where containment was sufficient.
* Produced a phased remediation plan aligned with business constraints:

  * Which components should be treated as “legacy islands.”
  * Which should be folded into the modern Node/Next architecture over time.

---

## Org-Level Enablement & Technical Translation

* Functioned as a technical counterpart to leadership, converting business requirements (growth, compliance, usability, reliability) into:

  * Concrete architecture workstreams.
  * Sequenced technical debt remediation.
  * Hiring priorities and onboarding structures.
* Provided evidence-backed reasoning suitable for validation by external experts, reducing leadership’s dependence on “trust me” engineering narratives.

---

## Technologies

TypeScript, Node.js, Next.js, React, GraphQL, PostgreSQL, Azure Kubernetes Service (AKS), GitHub Actions, legacy Go services, containerized deployments, Azure monitoring stack (Monitor / Log Analytics / App Insights)
