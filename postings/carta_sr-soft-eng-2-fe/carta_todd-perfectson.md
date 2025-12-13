# Todd Perfectson  
Senior Frontend Platform Engineer (Monorepos • React • Tooling • DX • AI-Assisted Development)

Toronto, Canada • todd.perfectson@gmail.com • https://github.com/toddperfectson • https://www.linkedin.com/in/toddperfectson  
Citizenship: Canada • Open to Remote/Hybrid (North America)

---

## Professional Profile

Platform-focused frontend engineer with 9+ years of experience designing and scaling frontend foundations for large engineering organizations. Specializes in monorepo architecture, React infrastructure, bundler/toolchain optimization, and developer experience at scale. Has led platform-level initiatives that improved build times, page performance, dependency hygiene, and CI/CD stability for hundreds of engineers. Comfortable operating as an internal “product team” for engineers, defining roadmaps, aligning stakeholders, and delivering global improvements that raise engineering velocity and code quality across the company. Pragmatic, data-driven, and opinionated about modern React paradigms, typed frontends, and AI-assisted development workflows.

---

## Core Competencies

- Frontend platform & infrastructure for 100+ engineer orgs  
- Monorepo design and maintenance (Nx, Rush, pnpm, Yarn workspaces, internal tooling)  
- React platform architecture: shared primitives, routing, SSR/SSG, design-system integration  
- Bundlers and build systems: Webpack, Rspack, Vite, esbuild, incremental builds, code splitting  
- CI/CD for frontend: GitHub Actions, CircleCI, Jenkins, build caching, artifact management  
- Page performance and reliability: Core Web Vitals, bundle analysis, regression guards  
- AI-assisted development strategy for frontend (linting, codemods, refactors, review support)  
- Cross-cutting upgrades: React/TypeScript major migrations, design-system rollouts, dependency hygiene  
- End-to-end testing infrastructure: Playwright, Cypress, Storybook, visual regression harnesses  
- Developer documentation, RFCs, standards, and onboarding material for frontend engineers

---

## Professional Experience

### Senior Software Engineer II — Frontend Platform  
**EquityGrid Systems (Toronto, ON)**  
2021–Present

Core member of the Frontend Platform team responsible for the monorepo, shared tooling, and DX for a 200+ engineer organization building a multi-surface private-markets and fund-operations platform.

**Monorepo Architecture & Tooling**

- Designed and maintained the company-wide frontend monorepo using Nx and pnpm, consolidating previously fragmented repositories into a single, strongly-typed workspace.  
- Introduced encapsulated project boundaries, enforceable lint rules, and dependency constraints to prevent cross-layer leakage and improve modularity.  
- Built custom Nx plugins and generators for feature scaffolding, test setup, and shared conventions, reducing boilerplate and cutting time-to-first-commit for new services and surfaces.

**React Platform & Global Improvements**

- Led React 16 → 18 migration across the entire monorepo, including concurrent features and Suspense-driven data fetching, coordinating with >30 product teams.  
- Defined standards for shared layout primitives, routing, and data-loading hooks, reducing divergence and simplifying cross-application navigation and refactoring.  
- Implemented a performance-focused component library integration with strict tree-shaking and design-token usage, reducing bundle size for key surfaces by up to 35%.

**Bundler & Build-System Optimization**

- Replaced legacy Webpack builds with a mixed Webpack/Rspack strategy, retaining compatibility where necessary while unlocking incremental builds, persistent caching, and parallel chunking.  
- Reduced median frontend build times in CI by 60% and local dev startup times by ~40% via Rspack adoption, build caching, and project-graph–aware pipelines.  
- Integrated build-step bundle analysis and size budgets into CI, surfacing regressions early and providing actionable diagnostics to product teams.

**CI/CD and Frontend DevOps**

- Designed multi-stage GitHub Actions pipelines for lint → typecheck → unit tests → Playwright suites → deployment, with granular caching and selective job fan-out based on the impacted project graph.  
- Built a platform-wide “safe deploy” strategy that combines automated smoke tests, feature-flag rollouts, and progressive exposure for customer-facing surfaces.

**AI-Assisted Development Strategy**

- Defined and implemented AI-assisted workflows for frontend engineers, including codemod generation, automated refactor proposals, and AI-augmented review hints based on static analysis and usage patterns.  
- Developed a small internal service that surfaces automated PR comments for common issues (performance anti-patterns, accessibility regressions, bundle bloat), integrated into GitHub checks.

**Cross-Org Collaboration & Enablement**

- Ran internal working groups on performance, testing, and migration strategy; authored platform RFCs and decision records for major changes (React upgrades, tooling swaps, lint rule hardening).  
- Partnered with product teams to align infrastructure improvements with roadmap timelines, ensuring platform changes translated into clear business and engineering outcomes.

---

### Senior Frontend Platform Engineer — Developer Experience & Monorepo  
**LedgerCraft Capital Technologies (Remote)**  
2017–2021

- Owned the frontend monorepo in a 120+ engineer org, based on Rush + Yarn workspaces, with a focus on deterministic installs, cacheable builds, and consistent lint/format/test workflows.  
- Led TypeScript 3 → 4 migrations and standardized strict typing settings across all packages, improving type safety and reducing production type-related incidents.  
- Introduced Storybook as the canonical environment for shared components and patterns, enabling visual regression testing and improving cross-team reusability.  
- Designed CI pipelines in CircleCI and Jenkins with matrix builds and distributed caching. Achieved 50–70% reduction in average pipeline times.

---

### Frontend Engineer → Senior Frontend Engineer — Product Applications  
**CapVent Platforms (Toronto, ON)**  
2014–2017

- Built React-based dashboards for fund operations, portfolio analytics, and LP reporting surfaces.  
- Introduced early frontend standards: eslint/Prettier configuration, shared components, and a single-source design system that later became the foundation for platform-level abstractions.  
- Drove the initial migration from a legacy multi-repo setup to a lightweight monorepo, providing the proof-of-concept that justified the creation of a dedicated platform team.

---

## Selected Platform Initiatives

**Company-Wide React Migration and Cleanup**

- Planned and executed multi-phase React migration (including router and state-management upgrades), with codemods, lint rules, and migration playbooks.  
- Introduced automated checks for deprecated APIs and unsafe lifecycle methods, ensuring consistent, forward-compatible usage across hundreds of codeowners.

**Rspack-Based Build System Modernization**

- Delivered a platform-wide bundler strategy using Rspack for most applications, while maintaining interoperability with legacy Webpack-based surfaces.  
- Implemented environment-aware configuration (dev vs CI vs production), using aggressive caching and minimal cold-start overhead.

**Playwright and Storybook-Based Testing Platform**

- Standardized Playwright for end-to-end testing with a shared test harness, fixtures, and cross-application utilities.  
- Integrated Storybook with visual regression tools to catch UI drift in foundational components before they hit user-facing flows.

**AI-Assisted Refactors and DX Tooling**

- Built a CLI and GitHub App that leverages AI to suggest codemods for repetitive refactors (e.g., prop renames, hook adoption, design-system migration), anchored by monorepo metadata and TypeScript types.  
- Used telemetry from build and lint systems to prioritize high-impact DX features and automated checks.

---

## Technical Skillset

**Frontend & Platform**

- React (Hooks, Suspense, Context, Concurrent features), TypeScript, JSX/TSX  
- Monorepos: Nx, Rush, pnpm, Yarn workspaces; internal tooling and generators  
- Tooling: eslint, Prettier, Storybook, Playwright, Jest, Vitest

**Build & DevOps**

- Bundlers: Webpack, Rspack, Vite, esbuild, Rollup (targeted usage)  
- CI/CD: GitHub Actions, CircleCI, Jenkins; build caching, matrix jobs, artifact promotion  
- Observability and quality gates integrated into pipelines: bundle size, perf budgets, smoke tests

**Ecosystem & Infrastructure**

- Node.js-based toolchains and services  
- Cloud: AWS (Lambda, S3, SQS, CloudFront, CloudWatch), edge/CDN patterns for asset delivery  
- API design for frontend–backend contracts, typed client generation

**AI & DX**

- AI-assisted code review and refactoring workflows  
- Codemod authoring (jscodeshift, ts-morph) and static analysis for automated suggestions  
- Internal documentation, standards, and onboarding guides for platform consumers

---

## Open Source & Community

- Maintainer of internal monorepo tooling plugins and shared configuration packages (eslint, TS, Jest).  
- Contributor to open-source tooling (small patches to bundler/plugin ecosystems and monorepo-related libraries).  
- Regular internal presenter on topics such as React migrations, performance engineering, and AI-assisted workflows.

---

## Education

**B.Sc. — Computer Science**  
University of Toronto  
Focus on software engineering, distributed systems, and programming languages.

---

## References

Available upon request.