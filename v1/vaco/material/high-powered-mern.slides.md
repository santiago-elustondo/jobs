---
title: high-powered-mern.slides.md
---

High-powered MERN architecture.
Some humble suggestions :)

Santiago ElustondoDirector, Technical Solution Delivery Vaco Toronto
A bit about me...
JavaScript NerdLove the language and the community.
Open-source ❤️blast-engine.io is a team of passionate contributors.LinkedIn > TikToklinkedin.com/in/santiago-elustondo

Our Goals, Simply Put..
Quality (Asset value) 
Correctness
Performance 
Robustness 



Agility (Investment value)
Velocity 
Cost 
Scalability 

purely engineering goals (does not include design goals, product goals)
Quality
this one is hard to ignore, because 	
it's what the product leadership will see immediately.
deemed high priority due to immediate business impact.
Development cost / velocity
this is the part of a the engineering dept's job that the higher ups and the users dont see,  it manifests through consistent delivery and outpacing competition, or  budgetary and timeline problems. 
its a big deal, we've all been on many projects where this is a serious problem.
its a long term payoff, and so the engineering owners need to be most aware of this, its them that will not be able to deliver in a year.
we want our engineering leads to not become a bottleneck or be unable to apply the full power of their skill by being weighed down

Agility Health Check
Do we trust our automated tests?Do we rely on manual regression?
Does new code tend to cause unexpected bugs?
Would intermediate devs say it's more pleasant or frustrating to do development work on the project? 
How much work is it to replicate and fix a bug? 
Do our development tools make it easier to debug or try out new ideas?Do our dev tools get in the way more than help?...
Do we have to read too much code to understand a specific behaviour?
Do PR reviews produce valuable insights about the proposed solution's merits?
Do we trust our devs (including fresh hires) to always commit code that will not be a detriment to the Goals?

Disclaimer
The examples, terminology, examples, and even some ideas are adapted to a particular type of project:  
Complex and Busy MERN projects 
.
I'll propose for wer consideration some patterns and practices that I've found consistently rewarding. But I'm eager to hear wer ideas and feedback after the presentation is done.While many of the ideas I will propose to we will be useful in a broad range of projects, this talk is specifically oriented towards complex, data-driven MERN applications. 
Improving the health of a legacy application is full of unique and fascinating challenges that I won't be able to cover here, but hopefully some of these ideas will help orient wer team.





this talk is focused on specific tech and specific type of app. we can take the ideas that we think still apply to wer type of project.
type of app: high-io, complex ui, inter-user interactions, graphical data structs
tech: MERN
not SQL, for example
we dont usually have the privilege of a greenfield project, the challenges of improving an existing system (audit, triage and refactor) are also very interesting, but we should start at greenfield, so that we have a common set of general goals in mind before we discuss transitioning to them. there will be more (blast-engine.io)
the examples i use are only to illustrate concepts, i will try to be clear, when discussing an example, about what parts are just arbitrary choices vs what parts are important to the concept at hand.


General Principles
Ideals to live by
we'll start with the most well known and least contested ones first.

Pure Beauty
effects:	 change stuff. something is different afterwards
immutability
Simply do not mutate JavaScript objects, ever.
we don't want to keep track of them, and what mutations occurred.
we don't want to be in a confusing situation because somewhere downstream wer object got mutated.
Immutable objects are predictable.
Operations on immutable objects are comparable and deterministic.
A mutation is a side-effect. We have to be really careful with those
purity
No effects (only a return value) No external influence  on result (only declared parameters) (independent of environment)"same input, same output"
Very testable and robust
Easy to read and understand
Highly Reusable
Purity can apply beyond functions. we can have a Pure Model: This would be an object that accepts certain parameters, and then provides functionality based on only them: uses nothing but the parameters provided, and causes no side effects.
An Immutable class that accepts data upon construction is a pure model.
These enjoy all the benefits of purity, while helping to organize and segregate functionality. 
In order to facilitate the use of a pure construct, we provision it (we provide some of its parameters and leave only the more use-case specific parameters to be given when the function is called)

// ----
we're just dioing reduc, we're just adding some structure to it , in fact we can use the library with a redux store, while continuing to use wer existing middleware and reducers, atctions. in fact our action type is a javascript symbol,, so we're guaranteed to never mistake our action for one of wers (but we can always do it explicitly.
in the playpen we can do cool things, and try out experiments, this is an important 
TDD is beautiful when we get this right
we're 100% doing redu herek
have 'testing.js' barrels basic index.js, so we can import the testing tools if we want, in the sandbox, thiis is not included the build -
OOP works well, we can still have very nice OOP patterns that help organize code. the reason OOP term fell out of fashion is because traditionally objects maintain their own state	when using classes, aways use arrow funcs for methods, so we can pass them around
we dont need heavy libraries like immutable.js, which pack a lot of functionality and can become performance problems since these operations need to be as light as possible, since we use them all the time.show immutable functions & tests
we should be pure even within functions, its makes them much easier to debug, show a step by step
examples:- (simple/independent) send emails to userIds (independent)	- use case: we get the users as a clean array, we do call effects and at the end we create a response like results = [{ user, result }] serialize it to send it out	- code: function passes to an effect function, this function calls another function to get some extra data whatever, and just adds it to the users, but this data has some circular shit and now we fail serialize, hard to debug-  (simple/independent) functions can be moved around with no context regard	- we have a function to check authentication, but we grab some config as an import, if we take it as param, its much easier to test it and move it around to other places- (simple/independent) function effects mess with it	- another function causes side effect mutating config obj, causing issue that we dont catch in test, since the effect didnt happen. it should still be instantiation from the same function.- pure models and provisioning	- gt state models (we can even show the gt code)	- unit tests: we can test the pure constructs as unit testsnotes:- pure constructs can run on any environment	it can be moved around 	it can be shared (tests, different platforms, different configurations)- "zen" because it provides clarity (less confusing, easier to reason about) and peace of mind (safety, we know what we are affecting)	the guarantee of immutability and purity clears wer mind of vague concerns about  potentialities like what might be affected- typescript becomes a better tool	allows for much stronger types, since there arent things coming in and out of objects, we dont have to consider how an object might change, so we can be more precise	 anytime the definition of wer inputs/outputs change, it will tell we everywhere that we need to update in wer code	
i can do a reference comparison because immutabilioty assummed
   if (this.type() !== query.type()) return false
   if (this.provisions !== query.provisions) return false
   if (this.options !== query.options) return false

this is connected to immutability, because a function that mutates something from outside is impure

Usable in so many contexts, since it doesnt care about context

Law and Order
Every line of code should exist in an explicitly defined "kind" of thing.
A kind of thing could be anything, a kind of function, a kind of data structure, a kind of file
Every kind has explicit rules about what it can and can't do. 
Thus, when solving a problem, we are bound by these building blocks, and this keeps the architecture design stable.
PRs are easier to review and more valuable, since if the tests pass, and the laws are being followed, the code has the architect's implicit approval, and violations of these rules are not up to interpretation.
The rules may be specific and creative, but usually they answer questions like:
What can this kind depend on? What can we import or accept as arguments?
What should this kind return? is it sync or async?
How is this kind to be tested?
What kind of logic should it contain? (business, plumbing, etc)
What should it be agnostic of, and what does it "know"?
Where in the directory tree should it be placed? how should it be exposed?
Unidirectional dependencies are often a good rule, even among kindreds (sometimes not possible)
The engineering lead's time is well spent updating these rules strategically, and juniors know what their tools are, and where to find what they need.
testing should be included alongside, unless they are full on examples, either way we dont export them in barrel files
----
there are many things we could call dependencies (imports, provisions, argument types), but theres not much to gain from categorizing thesea dependency relation is when something that "knows" about something else, plain and simpleunidirectional dependencies are the gold standard and have so many benefits. 2 things could be of the same "kind", but the first doesnt know about the other, which depends on it (queries, utils, etc)the only time that these different variants of what we would call a dependency are relevant is when defining rules that determine HOW these kinds are to interact. (many kinds of dependencies are only allowed as provisions [not that the depender knows about and asks for that dependency], while others are ok to import: utils, testing helpers like examples, etc) 
state-modelservices- all state (even streams, whatever, all go in state)controllers - no state like service- (expose actions that 
"promotion pattern"
unidirectional dependency chain
between files, directories, packages, everything, it should be a general way of life
think of the word dependency in the strictest possible way, for example: files in dir1 dont know anything about dir2, dir2 imports stuff from dir1.
sometimes we require a solution that involves circular, or a solution that adheres to this constraint would be vastly more complicated. always define exceptions with overriding mandates and define a boundary around it


Capturing Wild Effects
Could be an External API or not, redux store is a service, because dispatching an action and updating state is an effect.
We identify some effect api and wrap it in our own interface. We can then mock that interface.
Effects are not easy to test, so we always want to push our services far out as we can, and only interact with them once we've done all the complex work.
Keep them accessible for debugging. To test that our services are working well, especially when dealing with external apis, we often have to just try it out and see what happens. This is why we keep them segregated and accessible for debugging.
-------
store is a service, because state update is an effect	it accepts state model, and uses the model apis
services can tested as integration tests (in client too), but these should only be done by hand, cause they could be brittle) (api limits, cost, browser-like testing engine not support features, etc)- controllers define "actions" that use different independent services- ui components are a special type of service because their output is meant to be consumed by renderer	- using provisioning concept, we can make provisioned components with pure viewmodels function generators		- ui test with storybook (show we can swap out components)		- unit test for viewmodel (viewmodel should take all controller provisions, as well as state and props)
examples:	- (independent) service has subscription to some api
so far so good, all our code is super testable and clean. the problem is, side effects are the ultimate goal of the application, there's no escaping them. We  capture that functionality and state in a service, this we can mock. 
redux store, if we call same dispatch twice we get a different result, because its changing state, which is an effect

Don't Mock werself
We mock services because we want deterministic, reliable, simple tests. 
external services often will not produce the exact same behaviour every time. inconsistent.
establishing live services for common testing is too much boilerplate and room for error.
it could be expensive (imagine sending SMS every time we run jest).
However, we should not mock dependencies that are our own code!
writing the mocks will be like writing the thing twice
hardcoded input data or state is terrible
have to update all mocks and hardcoded when the dependency changes, PAIN
can fall out of sync and give we a false pass
unit-test mocks tend to be done lazily if they need to be done for every unit test, and dont actually simulate the target well enough. bad test.
we're only testing that unit, when we could be testing if it works with the system, after all that's the goal!
Instead, if we're testing a "kind" (K1) that takes input of another kind (K2), and we want to have different configurations of that input, produce those "mock" versions using the legitimate apis that produce K2. This should be legal by the Law of K1, since it "knows" about K2.
If K2 gets a breaking change, it will trigger a legitimate test fail for K1
I find it very nice when these variant K2 "mocks" are kept with K2 itself, as part of its exports.
------
we can use a pure function suite (provided by gt-store - using puresnap) to 		build states out of model updates
at the bottom of it all, we might need some data, but uou can just have a couple of example data that we can combine and manipulate through actual apis
concept of "		

Everything The Light Touches is Our Kingdom  
accessibility
we've already seen in the library scratchpads, but we want this in every application.
although this is very common practice in  functional programming, and among people that agree with the value of purity, i would HIGHLY discourage we from ever leaving things that we will continue to use within function closures.
this type of barrel creates a natural tree, use when they are different kindsthe above doesnt work during a jest run, wasted enough time on it, but scratchpads are cool :)also we can set up alias and be forced to explicitly say where we are grabbing each thing, easy to review
import { normalizeQueryModelDefinition } from './normalize-definition.fn'
import { GTQuery} from './query.class'
import { GTQueryCreator } from './query-creator.class'
import { GTQueryModel } from './query-model.class'
import { createQueryModel } from './create-query-model.fn'
import { provisioning } from './provisioning.utils'
import { operators } from './operators.utils'

export const queries = {
 normalizeQueryModelDefinition,
 GTQuery,
 GTQueryCreator,
 GTQueryModel,
 createQueryModel,
 provisioning,
 operators,
}


Having Fun Should Be Easy

scratchpads are awesome!
we can literally require files if we're in node
but we can also use imports and babel like we're writing src using node-babel
we can keep alive and just play with our node code, perfect for backend work


The Central State is the Final Authority
we don't want to have to keep track of separate stateful services that depend on each other. If we must have multiple "sources of truth" (it is often necessary), make sure they are different, independent truths.
we can still modularize wer state management. we can expose an OOP-style API to manage wer state, using pure models ;)
ACCESSIBLE
-----   - we want to keep ALL state, even streams, functions, whatever, in store, so that its accessible
can export a serializable state
some app state cant be captured (external apis: ex: what's in local storage, webworker state, etc, etc), this is stuff that a service would be able to tell us about if we asked, but the source or truth is not our store
if we want to restore a state from memory or from an error report, we need to serialize, not everything can be serialized, circular relations are useful, storing functions is also useful
strategy: 
keep portion of the module state that is serializable, simpler redundant representation, but can be used to
provide to module to expand out and fill circular deps and object types, whatever the module can do without any service help through arguments
services that depend on module can import and regenerate external apis state with it
we dont need to show a full example here (just an independent example maybe)
This one is another kind of obvious one by now, since redux took over.
redux gets messy though, because they dont provide a clear way to modularize and separate concerns, its very common to get totally lost in dispatch after dispatch, and actions that trigger side effects.
This principle, like all of them, is very much applicable to backend. i'm going to show we what i think is a fantastic data-io pattern in a bit.

Declare What we Need, Let Them Handle it
Having to manually manage numerous event subscriptions is detrimental to one's mental health.
It's hard to reason about, and really difficult to test, since the timing of events fired is unreliable by definition 
Redux's genius lies in defining components with declarative data subscriptions, handled by a central service. 
We dont have to keep track of what subscriptions we have open, or what to do when a certain event comes into one of our multiple handlerseverything is fed into the component as one, we get all wer latest event results every time, so we only need one handler, usually just the render function, to convert it to a UI representation. 
We also dont need to worry about unsubscribing when unmounting.
most importantly, it makes the component self-sufficient. It doesnt need its parent to take care of its data needs, so it can be moved around the application and will function the same way. this decoupling of components was revolutionary in its time.
This approach should be used for most other events that a component might want to subscribe to:
current location / route 
size of screen for responsive adjustment
webworker events
We achieve this with a Higher Order Component or a hook
// --- prevent leaks (subscriptions can keep stuff in services' cachesengine should provide the logic of changing one subscription with the result of another, which quickly gets very messy.example: we can show a declarative component getting chained data from firebase vs firework (and say "more to come on this")

Functional Legos for Scripting Fun
all async functions, can help to configure different types of running environments, builds, and configurations
all scripts in node is a good idea: cross platform
talk about our "context" package
show that we can run as simulation, run with preloaded state, run subsections of the app, storybook settings
dont call node_module bins in yarn scripts, write a script in node that does itthis way we can always add --inspect-brk to the command

The Ascendance
Full-Stack Redux

The Ultimate Source of Truth
Imagine a redux store that actually kept its state in the database.
Declarative subscription to remote database on a per component basis
wer component declares the data it wants from the state, but this state is the system database, shared by all users. 
The state operations we're used to, reducers, selectors, etc, would apply in the same way, but updating the central database itself as wer state. 
This frees up the problem of network requests having to be triggered and synchronized via actions, and websocket subscriptions being managed programmatically.
Isomorphic pure state model (platform agnostic)
The business logic that determines what to ask for and how to transform it is all pure models, which mean they can be used by backend, browser, react native, etc
Everyone is kept up to date by importing a shared package describing the central state.
Testing our business model becomes a breeze
The problem is: In redux we always have access to the whole state to derive the current value any of wer queries, and the results of wer different queries are always derived from the same dataset. 
Instead, here we'll always have an incomplete representation of the remote state in wer local cache, we need to fetch what we don't have, and utilize caching effectively. We need to be efficient about what we ask for, what we keep, and how we store it.

apollo for graphql tried something like this.  but we havent have a good way to do it, too much data transfer and gets lost. graphical data ends up getting just downloaded again and again, when we're using graphql


The Atomic Solution
An elegant solution to this problem that has been working very well for me is based around using atomic models as the building blocks that define the remote central state. 
we can think of an atomic model as a document in a collection. But often times when working with mongo we will return subsets of documents based on usefulness to the user or permissions.
A better definition of an atomic model would be:
A model such that we are ok with always receiving the whole data, no requests for partials.
A model such that users will have access to all or none of the data in that document.
These models can be received and stored in collections of the same type, and could be even represented that way in the mongodb collections, as they are in firebase.
The component would declare a composite query, but the query gets broken down by the service into individual subscriptions for its atomic elements. 	
the client stores the atoms as the arrive (in any order), and checks whether we have all the parts necessary to produce the computed, aggregated, or composite query of the component. Only then does it release the data event.
The models would be as denormalized as possible, opting for references over copies in most cases, since queries will reuse what is in the cache, only having to fetch the missing atoms to fulfill their request.
------
we can use a pure function suite (provided by firework) to 		build states out of model updates (we can use puresnap to get models out)		import built model mocks and insert into state

Multi-Level Caching for Turbo-Speed
The @blast-engine/firework framework only provides a firebase adapter today. However, a classic MERN stack could do a fantastic job of implementing this pattern. 
The server clusters would share the same state model as the client, which they would use to subscribe themselves to the mongo database via $streams, and keep their own shared cache of recent atom requests from all the users currently connected.
In the case of firework, we would need only to implement a mongo adapter to maintain those subscriptions. 
This would offer very fast data-io, since most data would not need a trip to the database. it would be an inherently predictive caching strategy naturally, and with an intuitive pure api that is clean and testable in the best ways possible

I very much look forward to wer critiques on my hypotheses,Please don't be shy, I would love to hear a challenging perspective.

I think SQL doesn't like it.
An SQL DB doesnt seem suited for this strategy, since unlike document DBs, here we are relinquishing the power of views, joins, etc.
I dont believe that the database structure itself needs to map directly to the atomic structure defined in the central state model. 
A database adapter for mongo, for example, could cheat and give me a partial document whenever I ask for an atom, and this would be perfectly fine as far as the framework is concerned. 
If achieving this in SQL is at all possible without losing the language benefits, I would guess that atoms would have to be represented as SQL "views", which can themselves use the whole power of the language for efficiency.
// ----
i consider this unresolved, i dont spend enough time with relational databases

That's all for now!
Please reach out with any content requests, 
questions, ideas, or to say hello. I'd love to connect.
Santiago ElustondoDirector, Technical Solution Delivery Vaco Toronto
linkedin.com/in/santiago-elustondo
blast-engine.io
santi@blast-engine.io
github.com/blast-engine
