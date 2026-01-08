carta is all about startup funding. this is something i'm deeply passionate about, and the startup/founder experience might be actually a value-add

## end-to-end ERP platform for private markets
* what is an ERP platform
  * "Enterprise Resource Planning": integrated software systems that manage core business processes like finance, HR, inventory, and manufacturing in a single database
  * **NetSuite** (this is "the" ERP) - NetSuite® Official Site | An AI-Powered ERP System
  * **HubSpot** (this is CRM, related) - HubSpot CRM Software - Free Online CRM
* [study] what is a private market? a private fund?

## to replace outdated spreadsheets and fragmented service providers
* [study] what might these fragmented service providers be?
* [study] what data might be in these outdated spreadsheets?

## frontend experience
> The Frontend Platform team is the core infrastructure team that underpins the entire frontend experience at Carta.
* definitely done a lot of this. Rangle.io sells itself as a shop that builds "digital experiences" and are very front-end heavy, and my last position there was "Technical Director, DevEx Lead"

## our monorepo and other key FE repositories
* monorepos have been central to my development work for a long time. i've used lerna, yarn workspaces, pnpm, rollup, and i forget the name, but vercel's monorepo tool. i've heavily worked on managing dependencies and build pipelines using monorepos for years, linking  builds between packages and building out depenedency graphs and build processes all the way back to smackchat and the firework framework in 2018, i've dealt with versioning and hoisting, with integrating github submodules into monorepos, with react native challenges around monorepos, with isomorphic strongly typed packages serving backend services as well as client side for defining and integrating strongly typed DRY rpc api interfaces and for defining logical business domain definitions that work across applications (again, all the way back to smackchat, my startup app with custom firework framework in 2018, and ever since)

## that enable hundreds of engineers to build and ship high-quality, modern frontend applications
* lululemon's engineering dept was large and sophisticated. they used a very sophisticated custom contentful-cms integration framework that allowed for radical content management via contentful. they organized their front-end into numerous team-owned micro-frontends and libraries. the teams had their own release cycles, and the apps came together on the client using webpack remote federated modules system. the primary contributor of the webpack federation system was alan? jackson, and he was our lead architect. our team worked on the loyalty feature and we had to create a component library which carries its own sentry alerting, events, and contentful data subscriptions, and feature flagging, and were imported and integrated into other teams repos, those teams had to approve our PRs to their repos to take in and use our components in their own pages. 

## large-scale frontend monorepos (e.g. Nx / Rush, pnpm, vite, storybook, eslint)
* lululemon federated modules
## frontend build and delivery systems
* augury labs
* vaco i actually helped avaya set up a monorepo to share libs and resolve node_module  dependencies and all that! what was that monorepo i was helping them with? react native? i was setting up some greenfield thing. it was front-end too, should try to find notes about it
* rangle.io director role i touched a bunch of this stuff. momentive with leah bundle analyzer reduce bundle size. im sure we can find this.
## scalable foundations
## page performance
* avanade: performance improvements for pages in angular. responsiveness.
* rangle old: augury-labs
* firework
* oralinx: nextjs ssr
* conexis: reporting
## dependency management
## AI-assisted development strategy
* z-model
* type-first stuff generally, opinionated philosophy
## Deep React Knowledge
* react fiber, ssr, hydration
## optimizing bundlers (Webpack/RSpack)
* rangle leah: bundler optimizer
## CI/CD pipelines (Github Actions, Jenkins, CircleCI)
