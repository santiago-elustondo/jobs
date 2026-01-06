---
title: app-2/avanade.gen-1.md
---

### Avanade
- *Senior Software Consultant → Technical Lead*

Led delivery of enterprise-grade, full-stack systems across telecom and financial-services clients, operating at the intersection of **hands-on architecture, performance engineering, and team leadership**. Functioned as both senior individual contributor and technical lead, accountable for design quality, delivery predictability, and escalation management in multi-team environments.

**Team & Delivery Scope**
- Technical lead for **cross-functional agile teams** (typically **4–6 developers, 2 QA, 1 Scrum Master**).
- Owned technical planning, architecture decisions, and risk mitigation while aligning delivery to fixed client timelines and regulatory constraints.
- Primary escalation point for complex production and performance issues; responsible for root-cause analysis and remediation planning with client architects.

**Telus Digital — MyWiFi Platform**
- Designed and implemented **horizontally scalable Node.js microservices** serving as the backend for the *Telus MyWiFi* application.
- Built APIs and service integrations enabling customers to **monitor, configure, and troubleshoot home Wi-Fi networks**, coordinating with downstream device services and third-party systems.
- Worked within a distributed systems environment emphasizing **high availability, fault tolerance, and operational observability**.
- Contributed across cloud and infrastructure layers (AWS/Azure hybrid context, Dockerized services, CI pipelines), ensuring services were production-ready under real consumer load.

**Mortgage Cadence Platform (Accenture) — Enterprise Fintech**
- Brought in specifically to diagnose **severe UI responsiveness and performance degradation** in a large Angular application developed by multiple independent teams.
- Performed deep performance audits using **browser profiling, flamegraphs, and runtime instrumentation** to identify bottlenecks in large data grids, animation-heavy views, and change-detection behavior.
- Re-architected core grid components around a **unidirectional state flow**, separating concerns into:
  - A **stateful orchestrator / state-machine layer** responsible for data flow and interaction logic.
  - A highly optimized **OnPush-rendered UI component** with defensive setters minimizing change-detection cost.
- Eliminated unnecessary interval-driven JavaScript work, replacing it with **CSS-driven rendering** where possible or executing logic **outside Angular’s zone** to reduce runtime overhead.
- Demonstrated measurable improvements in frame consistency and interaction latency, validated with before/after profiling evidence and presented directly to client architecture leadership.

**Performance Engineering & Enablement**
- Designed and delivered **multi-day training programs** for client engineering teams on **web performance profiling and optimization**, covering both Angular and React ecosystems.
- Topics included runtime analysis, change-detection strategies, rendering pipelines, memory behavior, and practical debugging workflows for large-scale applications.
- Enabled client teams to independently apply profiling techniques post-engagement, reducing reliance on external escalation.

**Technologies**
Angular, TypeScript, JavaScript, Node.js, SQL Server, MongoDB, Redis, GraphQL, Docker, Jenkins, Selenium, Azure, AWS, microservices architectures.

**Key Outcomes**
- Restored usability and performance to business-critical enterprise applications suffering from architectural entropy.
- Delivered scalable backend services supporting consumer-grade reliability expectations.
- Elevated client teams’ performance literacy through structured, technically rigorous training.

