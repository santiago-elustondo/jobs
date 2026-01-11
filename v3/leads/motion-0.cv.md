# Santiago Elustondo

**Staff Software Engineer — React & Node.js**
Toronto, ON · Available for On-Site / Hybrid roles
TypeScript · React · Node.js · Distributed Systems · Production Reliability
[email](santi@blastengine.ai) · (416) 662 8602
[linkedin](linkedin.com/in/santiago-elustondo)
[github](github.com/santiago-elustondo)
[github](github.com/blast-engine)
[npm](npmjs.com/org/blast-engine)
[npm](npmjs.com/org/typefirst)

---

## Profile

Senior full-stack engineer with **10+ years building and stabilizing customer-facing web platforms** in regulated, high-impact environments. Proven track record designing **robust frontend and backend systems**, diagnosing production failures, and incrementally improving reliability and performance without destabilizing live platforms. Frequently trusted with **ownership of critical surfaces**, architectural decisions, and mentoring engineers as teams scale.

---

## Core Technical Strengths

* **Frontend Systems**: React, TypeScript, Next.js, complex state and data-driven UIs
* **Backend & APIs**: Node.js, REST, GraphQL, auth-aware BFF patterns
* **Cloud-Native Delivery**: containerized services, CI/CD, production observability
* **Reliability & Performance**: error isolation, monitoring, load & failure analysis
* **Team Practices**: code reviews, architectural guidance, Agile delivery

---

## Professional Experience

---

## Blast Engine Inc. (Consulting)

**Founder / Senior Technical Consultant**
*Jan 2024 – Present*

Senior embedded engineer helping teams stabilize and extend **existing production systems**—not greenfield prototypes.

* Diagnosed React and Node.js applications exhibiting **non-deterministic behavior** caused by implicit coupling between UI state, analytics, and authentication flows.
* Refactored data access and API interaction patterns to reduce **over-fetching, duplicated client state**, and inconsistent cache behavior.
* Audited production telemetry and error streams to isolate root causes instead of symptom-level fixes.
* Delivered concrete architectural recommendations (refactor vs rewrite) grounded in **operational risk, tooling health, and test surface area**.
* Worked directly with product and design to translate ambiguous requirements into **small, reversible changes** with controlled rollout risk.

---

## Rangle.io

**Technical Director / Developer Experience Lead**
*Nov 2022 – Dec 2023*

Senior IC and escalation point across multiple enterprise teams delivering **React + Node.js applications** under real user load.

* Led frontend and full-stack performance investigations in mature applications already in production.
* Identified and corrected issues including:
  * bundle bloat from transitive dependencies,
  * server-only code leaking into client bundles,
  * inefficient data-loading patterns across authenticated flows.
* Reduced shipped JavaScript and improved time-to-interactive without UX regressions.
* Served as hands-on technical lead, performing deep code reviews and mentoring engineers through complex refactors.
* Helped teams regain delivery confidence by introducing **clear architectural boundaries** and pragmatic technical standards.

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Technical lead for a **horizontal loyalty initiative** integrated across a large, federated React ecosystem in a **security- and compliance-sensitive retail environment**.

* Designed a shared **Loyalty component platform** embedded into checkout, account, search, and product flows owned by independent teams.
* Enforced strict integration contracts:

  * typed, serializable props only,
  * no shared runtime state,
  * internal ownership of side effects (auth, analytics, feature flags).
* Implemented **mandatory error boundaries** around all exported components to prevent payment-adjacent failures from cascading into host applications.
* Centralized production observability (Sentry, analytics tagging) to support cross-team incident triage.
* Collaborated closely with checkout and platform teams on auth flows, data handling constraints, and rollout safety.
* Mentored engineers on defensive frontend patterns appropriate for **mission-critical user journeys**.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Senior technical authority on distributed platforms with **realtime communication, unreliable downstream services, and strict uptime requirements**.

* Led architecture and delivery of full-stack systems interacting with multiple backend services of varying reliability.
* Designed client-side abstractions that shielded UI layers from backend fragmentation and failure modes.
* Diagnosed production incidents involving socket lifecycle mismatches, backpressure, and timing-dependent bugs.
* Established release, validation, and rollback practices to reduce regression risk in customer-facing systems.
* Mentored senior and intermediate engineers while remaining hands-on in critical areas.

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Enterprise delivery across financial services and telecom.

* Contributed to large Angular and TypeScript applications with **dense data models and complex user workflows**.
* Led performance investigations targeting UI responsiveness, change detection cost, and rendering inefficiencies.
* Worked closely with backend teams on **GraphQL query and resolver optimization**, reducing over-fetching and improving perceived performance.
* Delivered production features while simultaneously improving long-term maintainability.

---

## Earlier Experience

**Rangle.io — Software Developer**
*Apr 2017 – Oct 2018*

* Core contributor to **Augury**, the official Angular DevTools extension.
* Built inspection and profiling features used to diagnose real-world Angular performance issues.
* Led AngularJS → Angular migrations and frontend audits for enterprise clients.