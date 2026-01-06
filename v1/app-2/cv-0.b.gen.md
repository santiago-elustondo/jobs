---
title: cv-0.b.gen.md
---

# Santiago Elustondo

Lead Full Stack Engineer / Technical Lead
Toronto, ON · Hybrid-ready (downtown Toronto, 2x/week)

## Profile

Senior full-stack engineer and technical leader with deep specialization in **frontend architecture, developer experience, and performance engineering**, paired with production-grade backend and distributed systems delivery. Known for turning fragile, organically grown systems into **legible, testable, and operable platforms**, and for raising team effectiveness through explicit architecture, tooling, and mentorship. Extensive experience leading engineers through modernization efforts, performance remediation, and platform consolidation across large, multi-team environments.

---

## Blast Engine Inc. (TypeFirst Consulting)

**Founder / Technical Consultant**
*Jan 2024 – Present*

Independent technical consultant focused on **platform clarity, frontend systems, and architectural rehabilitation** for early-stage and mid-market products preparing for scale, hiring, or enterprise scrutiny.

* Acted as senior architectural advisor on frontend-heavy systems with growing complexity, diagnosing failure modes related to state explosion, hidden side effects, and brittle integration seams.
* Designed and implemented **clean architectural boundaries** (domain logic vs effects, state vs IO, platform primitives vs product features) to make systems reviewable and safe to extend.
* Delivered TypeScript-first modeling approaches emphasizing compile-time guarantees, explicit contracts, and removal of implicit runtime assumptions.
* Supported clients through documentation, onboarding materials, and architectural narratives that reduced reliance on individual contributors and enabled sustainable team growth.

---

## Rangle.io

**Technical Director, DevEx Lead**
*Nov 2022 – Dec 2023*

Senior technical leader responsible for **frontend and full-stack architecture quality**, developer experience, and engineering capability building across client engagements and internal initiatives.

### Developer Experience & Engineering Enablement

* Led internal DevEx initiatives focused on **build tooling, test posture, architectural hygiene, and performance literacy** across teams.
* Designed internal reference architectures and guidance for:

  * modern React and Next.js systems
  * state modeling and side-effect containment
  * bundle size control and dependency hygiene
* Delivered internal talks, demos, and written guidance translating hard-won consulting lessons into repeatable engineering practices.
* Mentored engineers across experience levels, including structured support for QA-to-developer transition cohorts, emphasizing confidence, correctness, and architectural reasoning.

### Frontend Performance & Tooling Leadership

* Led multiple performance investigations across large React and Angular codebases, using bundle analyzers, runtime profiling, flamegraphs, and targeted instrumentation.
* Standardized a **performance investigation workflow** (baseline → isolate → remediate → verify → document) so improvements survived beyond the initial fix.
* Championed performance as a **platform concern** rather than a feature-level afterthought, reframing slow builds, brittle tests, and oversized bundles as systemic liabilities.

---

## Lululemon

**Engineering Lead — Loyalty Platform**
*Nov 2021 – Nov 2022*

Frontend-focused technical lead for a horizontally integrated loyalty initiative across a large, federated frontend architecture.

* Designed a **frontend platform library** intended for consumption by multiple independently owned micro-frontends, prioritizing defensive integration patterns.
* Established strict component boundaries using React context, typed props, and error boundaries to isolate failures and prevent cascading runtime errors.
* Integrated with a sophisticated CMS-driven content architecture, ensuring components were configurable, data-driven, and safe to evolve without redeploying host applications.
* Worked closely with platform and federation architects to ensure compatibility with Webpack Module Federation constraints, peer dependency resolution, and runtime composition behavior.
* Provided technical leadership during quarterly demos and cross-team reviews, translating architectural tradeoffs into language accessible to product and non-owning engineering teams.

---

## Vaco Toronto

**Director, Technical Solution Delivery / Technical Lead**
*Jun 2020 – Nov 2021*

Senior technical authority responsible for **assessment, architecture, and delivery mechanics** across consulting engagements, with a strong emphasis on frontend systems and realtime interaction models.

### Frontend Architecture & State Modeling

* Drove frontend architectural standards emphasizing:

  * pure domain logic separated from effects
  * predictable state transitions
  * serializable, inspectable application state
* Advocated Redux-style state modeling as a **platform primitive**, not a UI convenience, enabling debugging, replayability, and regression isolation.
* Identified and eliminated hidden side effects and implicit lifecycle coupling that made systems brittle under team growth.

### Embedded Frontend Systems (Web Components)

* Led early platform work on embedded React applications compiled and shipped as Web Components.
* Defined dual-mode workflows (standalone app vs embedded artifact), enabling reuse of a single codebase across multiple integration contexts.
* Addressed authentication, token refresh, and secret-handling constraints unique to embedded environments, influencing backend service design to support frontend needs safely.

### Technical Advocacy

* Represented Vaco publicly through technical talks on **scaling MERN systems**, focusing on immutability, dependency direction, and effect isolation as enablers of velocity.
* Used public and internal presentations to elevate architectural literacy and position engineering rigor as a competitive advantage in consulting engagements.

---

## Avanade (Accenture)

**Senior Software Consultant / Technical Lead**
*Oct 2018 – Jun 2020*

Frontend-leaning full-stack consultant with a strong focus on **performance engineering and UI responsiveness** in large enterprise applications.

* Conducted deep performance audits on Angular applications suffering from UI jank, grid-heavy layouts, and animation-induced frame drops.
* Re-architected UI components into:

  * stateful orchestration layers
  * stateless, OnPush-rendered view components
    significantly reducing change-detection overhead.
* Identified numerous cases where JavaScript-driven animations and polling could be replaced with CSS or executed outside Angular’s zone, yielding measurable UX gains.
* Delivered multi-day client workshops on frontend performance profiling, teaching teams how to use flamegraphs, timeline tools, and change-detection diagnostics.

---

## Rangle.io

**Software Developer**
*Apr 2017 – Oct 2018*

Early-career full-stack engineer working across frontend frameworks, tooling, and performance diagnostics.

* Core contributor and maintainer of an Angular debugging/profiling browser extension, including performance-focused features that visualized component hierarchies and runtime behavior.
* Investigated performance regressions related to state serialization and extension-runtime interactions, applying complexity-reduction techniques to keep tooling usable at scale.
* Performed performance audits and remediation on AngularJS/Cordova hybrid mobile applications, including WebRTC-heavy flows with native plugin interactions.
* Supported enterprise AngularJS → Angular migrations, improving correctness, maintainability, and runtime performance.