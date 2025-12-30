### Avanade *(Oct 2018 – Jun 2020)*

*Senior Consultant / Technical Lead*

**Technologies:** Angular | TypeScript | Node.js | .NET | SQL Server | Azure | AWS | GraphQL | Docker | OpenShift | Redis | MongoDB | Jenkins | Selenium | Jest | Mocha

I operated as a senior technical lead within Avanade’s enterprise delivery organization, embedded in large, multi-team client programs where frontend performance, platform scalability, and delivery reliability were already under strain. My role combined hands-on architecture and implementation with delivery leadership: translating ambiguous or over-scoped requirements into executable technical plans, guiding cross-functional teams through complex refactors, and intervening directly in high-risk performance and correctness issues that threatened delivery timelines or user trust. Across engagements, the consistent theme was **making large, mature systems predictable again**—by re-establishing architectural boundaries, eliminating hidden performance debt, and teaching teams how to reason about their systems using measurable signals rather than intuition.

At the delivery level, I led agile teams typically composed of 4–6 developers, 1–2 QA engineers, and a Scrum Master. I was the primary technical escalation point: reviewing designs, unblocking implementation paths, mediating tradeoffs with client architects, and ensuring that short-term delivery pressure did not hard-code long-term instability. This included sprint-level planning, cross-team dependency coordination, and hands-on review of critical PRs where performance, concurrency, or correctness risks were concentrated.

#### Telus Digital — *MyWiFi Platform*

**Distributed Backend Services & Client Integration**

For Telus Digital, I worked on the backend platform supporting the **MyWiFi** application, a consumer-facing system allowing customers to configure, monitor, and troubleshoot home WiFi networks across a heterogeneous fleet of devices and downstream systems. The platform consisted of horizontally scaling Node.js microservices deployed in containerized environments, integrating with device APIs, provisioning systems, telemetry pipelines, and customer account services.

My contributions focused on:

* Designing and implementing **horizontally scalable Node.js services** with explicit statelessness, idempotent APIs, and clear separation between request handling, orchestration logic, and downstream integration layers.
* Addressing real-world distributed-systems concerns: retry semantics, partial failure handling, timeouts, and back-pressure when interacting with unreliable or latency-sensitive downstream systems.
* Auditing service behavior under load and failure conditions, identifying hidden coupling points (shared Redis state, implicit ordering assumptions, synchronous call chains), and proposing refactors that made scaling behavior explicit rather than emergent.
* Working with client architects to balance cloud-native design goals against operational realities, ensuring that performance and reliability improvements could be rolled out incrementally without destabilizing production traffic.

This work reinforced a recurring pattern in my later roles: **distributed systems fail at the seams**, and effective remediation requires making those seams explicit in both code and operational models.

#### Mortgage Cadence Platform (via Accenture)

**Angular Performance Architecture & Remediation**

A major engagement involved deep performance analysis and remediation for the **Mortgage Cadence Platform (MCP)**, a large-scale enterprise fintech application used by major mortgage lenders across North America. MCP was a mature Angular application with many independently contributing teams, extensive data-driven UI screens, large grids, and complex forms—exactly the kind of environment where incremental performance degradation compounds over time.

I was brought in specifically to diagnose and resolve **severe responsiveness issues**: UI jank, frozen interactions, delayed input feedback, and degraded scroll/animation performance on complex pages. My approach was deliberately systematic and evidence-driven:

* Conducted **CPU and network profiling** using Chrome DevTools and Angular-specific instrumentation, correlating flame graphs, layout recalculation events, and change-detection cycles with concrete user interactions.
* Distinguished clearly between **action fulfillment latency** (waiting for data) and **responsiveness** (UI reacting immediately to user input), framing performance not as a single metric but as competing resource budgets on the main thread.
* Identified Angular **change detection** as the dominant bottleneck in most problematic screens, exacerbated by two-way binding, excessive event listeners, interval-driven UI updates, and uncontrolled component tree traversal.

The core architectural remediation I led was a **re-architecture of grid and data-heavy UI components**:

* Split monolithic components into two explicit layers:

  * A **stateful orchestrator / state-machine wrapper** responsible for data acquisition, event handling, and explicit state transitions.
  * A strictly **OnPush, stateless rendering component** whose sole responsibility was to render a view model, with aggressive minimization of change-detection triggers.
* Enforced **unidirectional data flow** and immutable state updates so that reference equality could be used as a reliable signal for when re-rendering was actually required.
* Moved interval-driven visual behavior (spinners, animations) out of JavaScript and into **CSS or browser-native mechanisms**, or executed them explicitly *outside Angular’s zone* to avoid triggering global change detection.
* Replaced uncontrolled timers and host listeners with **batched and shared scheduling primitives**, dramatically reducing redundant event wake-ups on the main thread.

I used before/after profiler captures and live demonstrations to show the effect of these changes, making performance improvements concrete and undeniable to both engineers and non-technical stakeholders. In many cases, the absolute amount of work being done did not change dramatically—the key win was **making work schedulable and skippable**, so responsiveness was preserved even under heavy UI load.

#### Advanced Angular & React Performance Workshops

**Client Enablement & Knowledge Transfer**

Beyond direct project delivery, I designed and delivered **multi-day training programs and internal workshops** for client engineering teams focused on performance profiling and optimization in modern frontend frameworks (primarily Angular, with comparative references to React). These sessions were not abstract best-practice talks; they were grounded in real production case studies drawn from MCP and similar platforms.

The curriculum covered:

* A precise mental model of the **JavaScript execution environment**: single-threaded execution, event queues, painting, layout, garbage collection, and how browser scheduling decisions affect perceived performance.
* Deep dives into **Angular change detection mechanics** (NgZone, tree traversal, OnPush, markForCheck), contrasted with React’s reconciliation and scheduling model.
* Practical profiling techniques: interpreting CPU flame graphs, network waterfalls, layout thrashing indicators, and identifying false positives caused by tooling artifacts.
* Concrete refactoring strategies that teams could apply incrementally, even in large legacy codebases, without destabilizing delivery.

These workshops materially raised the performance literacy of client teams and reduced long-term reliance on external escalation by giving engineers the tools to reason about performance issues themselves.

---

**Throughline:**
Across Avanade engagements, my impact consistently lay in **turning opaque performance and scalability problems into explicit architectural and operational concerns**. Whether in distributed backend services or complex Angular frontends, I focused on making systems legible: isolating responsibilities, bounding side effects, and aligning code structure with the realities of execution environments. This period laid much of the groundwork for my later specialization in platform-level frontend architecture, developer experience, and large-scale system correctness.
