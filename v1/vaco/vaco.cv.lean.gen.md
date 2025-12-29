### Vaco *(June 2020 – Nov 2021)* **[1 year, 6 months]**  
- *Director of Technical Solution Delivery* *(Nov 2020 – Nov 2021)*  
- *Technical Lead* *(June 2020 – Nov 2020)*

Led Vaco Toronto consulting delivery across discovery, architecture, and execution. Defined requirements, success KPIs, and risk boundaries; converted them into phased roadmaps with explicit constraints; staffed and supported delivery teams; and owned cross-functional escalation paths to keep multi-repo work shippable under real release pressure.

#### Avaya – Avaya Spaces  
**typescript | react | redux | node | socket.io | kubernetes | gcp | mongo | redis pub-sub | gcp pubsub | terraform | k6**

- Technical lead for a globally distributed enterprise collaboration platform subject to data residency/sovereignty constraints.  
- Architected and delivered a platform-agnostic TypeScript client SDK to replace/deprecate web-client DAL code, enabling a new React Native client team and standardizing federation-aware routing + multi-region websocket subscriptions.  
- Designed and implemented a Node.js realtime socket abstraction mirroring the socket.io server API while supporting cross-region messaging: local delivery via socket.io + Redis adapter; cross-region delivery via encrypted payloads relayed over global GCP Pub/Sub and emitted within the target region with minimal handler churn.  
- Frontend platform work on “UWF” (unified-web-framework): created a standalone React application that also compiles into a reusable Web Component kit, and drove supporting platform refactors (shared UI components, shared redux-state package) plus an authentication microservice plan (refreshable JWTs, secret removal from clients, DI + unit-test scaffolding, and stateless-first scaling considerations).  

#### Public Technical Talks
- Delivered public presentations on “high-powered MERN” systems, emphasizing platform fundamentals (immutability/purity boundaries, explicit dependency rules, testability, and developer experience as a first-class scaling constraint).  