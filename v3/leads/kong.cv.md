# Santiago Elustondo

**Staff Full-Stack Engineer / Technical Lead**
React · TypeScript · Distributed Frontends · Performance & Reliability
Toronto, ON · On Site / Hybrid / Remote
santi@blastengine.ai · (416) 662 8602
[linkedin](linkedin.com/in/santiago-elustondo)
[github](github.com/santiago-elustondo)
[github](github.com/blast-engine)
[github](github.com/type-first)
[npm](npmjs.com/org/blast-engine)
[npm](npmjs.com/org/typefirst)

---

## Profile

Senior engineer with 10+ years building and stabilizing large, customer-facing web applications in environments where frontend failures directly impact revenue, compliance, or operational trust. Specializes in React architecture at scale, cross-repo integration, runtime isolation, and **performance debugging under real production constraints. Repeatedly brought in to untangle systems that already ship, already have users, and already hurt when they break.

---

## Core Technical Focus

* React at scale: long-lived applications, federated MFEs, shared component platforms
* Frontend performance: bundle analysis, render cost, runtime isolation, integration failure modes
* Contract-driven integration: typed boundaries, serialized props, defensive exports
* Authenticated applications: session propagation, auth context boundaries, analytics side effects
* Delivery mechanics: CI enforcement, PR review, regression containment, rollout safety

---

## Professional Experience

---

## Blast Engine Inc. (Consulting)

**Founder / Senior Technical Consultant**
*Jan 2024 – Present*

Embedded senior engineer for teams struggling with frontend correctness, performance ceilings, or architectural drift in shipped products.

* Diagnosed React applications suffering from over-fetching, duplicated client state, and accidental N+1 GraphQL patterns, tracing issues across both client and resolver layers.
* Refactored data-loading strategies to align with framework primitives (server boundaries, request coalescing, cache locality), reducing initial load times without UX regressions.
* Untangled implicit coupling between UI state, analytics side effects, and auth/session context that caused non-deterministic behavior in production.
* Produced concrete architectural recommendations (rewrite vs refactor) grounded in tooling obsolescence, test surface area, and operational risk—not aesthetics.
* Worked directly with product and design to convert ambiguous requirements into small, reversible UI changes, minimizing blast radius.

---

## Rangle.io

**Technical Director / Developer Experience Lead**
*Nov 2022 – Dec 2023*

Senior IC and escalation point across multiple enterprise client teams. Responsible for frontend reliability, performance, and technical confidence.

### Momentive (SurveyMonkey)
* Led a targeted frontend performance investigation after persistent regressions in a mature Next.js application.
* Identified bundle bloat caused by:
  * Transitive dependencies pulled via barrel exports
  * Non-tree-shakable imports
  * Shared utilities leaking server-only code into client bundles
* Reduced parsed JS size by ~60%, measurably improving TTI and main-thread contention.
* Documented a repeatable audit process (bundle analyzer → import graph → dependency surface) and coached team members to apply it independently.

### Get Ahead (Healthcare Platform)

* Technical lead for an embedded React application hosted inside a Flutter mobile shell.
* Designed the integration boundary between host and embedded UI:
  * Serialized configuration contracts
  * Explicit lifecycle ownership
  * Isolation from host navigation and state
* Delivered clinician-facing workflows under regulatory pressure while stabilizing a team operating under high uncertainty and delivery anxiety.
* Resulted in follow-on work and expanded scope due to regained delivery confidence.

### JetBlue (Design System Initiative)

* Contributed to a framework-agnostic design system delivered via Web Components.
* Evaluated Lit vs Stencil vs bare-metal approaches with a focus on:
  * Long-term maintainability
  * Cross-framework consumption (React, Angular, legacy stacks)
  * CDN delivery vs npm coupling
* Helped establish patterns that avoided React-specific leakage into shared primitives.

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Technical lead for a horizontal loyalty initiative** spanning a federated React ecosystem assembled at runtime via **Webpack Module Federation.

This role is high signal because of *constraints*, not buzzwords.

* Designed a shared loyalty component platform consumed by checkout, PDP, search, account, and navigation MFEs owned by different teams.
* Enforced a strict contract model:
  * Typed, serializable props only
  * No shared runtime state
  * All side effects encapsulated internally
* Implemented mandatory error boundaries around all exported components to prevent host-level crashes.
* Centralized Sentry instrumentation, tagging errors by host app, component identity, and execution context to enable cross-repo triage.
* Integrated Contentful-driven content models directly into the component layer, enabling dynamic content updates without redeploying host apps.
* Established a dev workflow that tested components against real host MFEs using git submodules in monorepo, surfacing bundle collisions, peer dependency conflicts, and prerendering failures early.
* Led technical investigation of a legacy membership/events system and produced a defensible recommendation to rewrite rather than incrementally upgrade, based on tooling rot, monitoring gaps, and QA risk.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Senior technical authority on multi-team systems with distributed state, realtime constraints, and production volatility.

* Led frontend and client-side architecture for platforms interacting with:
  * Multi-region backends
  * Realtime messaging layers
  * Downstream services with inconsistent SLAs
* Designed shared client SDKs to hide backend fragmentation from UI teams, preserving feature velocity.
* Diagnosed production failures caused by:
  * Socket lifecycle mismatches
  * Backpressure from unreliable downstream services
  * Implicit coupling between UI behavior and backend timing
* Formalized release and validation workflows across multiple repos to reduce regression risk.

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Enterprise delivery across fintech and telecom clients.

* Contributed to large Angular applications with heavy data density and complex interaction patterns.
* Identified and resolved severe UI performance issues caused by:
  * Excessive change detection
  * Poor component boundary design
  * Inefficient data binding
* Worked closely with backend teams on GraphQL query and resolver behavior, reducing over-fetching and improving perceived performance.
* Delivered internal training on frontend performance profiling grounded in real client systems.

---

## Rangle.io

**Software Developer**
*Apr 2017 – Oct 2018*

* Core contributor to Augury, the official Angular DevTools extension.
* Built performance inspection and profiling features used by the Angular community.
* Led AngularJS → Angular migrations and frontend performance audits for enterprise clients.