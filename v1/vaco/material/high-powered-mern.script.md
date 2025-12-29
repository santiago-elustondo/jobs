---
title: high-powered-mern.script.md
---

* 1) [time: ?] High-powered MERN architecture. (Some humble suggestions :))
* 2) [time: ?] a little about me... [time: ?]
    * notes
        * encourage questions and opinions. i love to discuss and learn. obviously there a time constraint. obviously there a time constraint to keep in mind, but i will keep track of that
* 3) [time: ?] The Simple Goals of Software Engineering
    * dump
        * sometimes it does happen that further investment into a system is not worth it, but it still does its job, provides value. its fine to call that legacy and move away, at that point you dont care about goal #2
            * similarly, greenfield projets for example, #2 is all that matters, thats your lifebloos. it has like 3 features and it barely works, but the investment value is clear because of what or how we are building our product. startups are the ultimate version of this, they dont have money or time, since they need to be ahead of some trend. how fast your can iterate, how easy you can bring people on board almost matters more than your current codebase, which is probably going to get nuked and rewritten sooner than u thim
        * random 
            * simple doenst mean easy. achieving E=M2 is a simple equation
        * prev slide content
            * Quality: Current value "would you be ok with a  code freeze?"
                * Correctness (behaves as designer expects in every situation)
                * Performance (low latency and smooth/responsive)
                * Robustness (no surprises)
            * Agility: Investment value "Are we competing against other modern players, or trying to get ahead? do we have a vision or play for this product that is yet unfulfilled? are trying to grow the organization in hiring and client offerings"
                * Velocity (bring new features/patches to production quickly)
                * Cost (minimize collective time spent on a task, proportional to seniority)
                * Scalability (support a growing team without compromising other items)
            * The challenge is to nourish these two often-conflicting priorities, and stay healthy on both fronts. If either one gets out of control, it can be tremendously expensive to fix, and could very well be terminal.
* 4) Health Checlk
* 5) disclaimer 
    * obviously you will be able to take the high level ideas and apply them somewhere else.
    * smart clients makre lot of sense these days
    * Improving the health of a legacy application is full of unique and fascinating challenges that I won't be able to cover here, but hopefully some of these ideas will help guide your design thinking.
    * slides_dump

I'll propose for wer consideration some patterns and practices that I've found consistently rewarding. But I'm eager to hear wer ideas and feedback after the presentation is done. \
 \
While many of the ideas I will propose to we will be useful in a broad range of projects, this talk is specifically oriented towards complex, data-driven MERN applications. 

Improving the health of a legacy application is full of unique and fascinating challenges that I won't be able to cover here, but hopefully some of these ideas will help orient wer team.



            * this talk is focused on specific tech and specific type of app. we can take the ideas that we think still apply to wer type of project.
                * type of app: high-io, complex ui, inter-user interactions, graphical data structs
                * tech: MERN
                    * not SQL, for example
            * we dont usually have the privilege of a greenfield project, the challenges of improving an existing system (audit, triage and refactor) are also very interesting, but we should start at greenfield, so that we have a common set of general goals in mind before we discuss transitioning to them. there will be more (blast-engine.io)
            * the examples i use are only to illustrate concepts, i will try to be clear, when discussing an example, about what parts are just arbitrary choices vs what parts are important to the concept at hand.
* 6) title: General Principles
* 7) **effects**
    * effects change the code's environment (state, external apis, etc)
    * side effect is an effect that occurs in the process of doing some logic, we always want to avoid this
* **7) pure beauty**
    * Simply do not mutate JavaScript objects, ever.
        * we don't want to keep track of them, and what mutations occurred.
        * we don't want to be in a confusing situation because somewhere downstream wer object got mutated.
        * Immutable objects are predictable.
        * Operations on immutable objects are comparable and deterministic.
        * A mutation is a **side-effect**. We have to be really careful with those
* **purity**
    * **No effects** (only a return value)  \
**No external influence  **on result (only declared parameters) (independent of environment) \
**"same input, same output"**
        * Very testable and robust
        * Easy to read and understand
        * Highly Reusable
    * Purity can apply beyond functions. we can have a ***Pure Model***: This would be an object that accepts certain parameters, and then provides functionality based on only them: uses nothing but the parameters provided, and causes no side effects.
        * An Immutable class that accepts data upon construction is a pure model**.**
        * These enjoy all the benefits of purity, while helping to organize and segregate functionality. 
    * In order to facilitate the use of a pure construct, we **provision** it (we provide some of its parameters and leave only the more use-case specific parameters to be given when the function is called)

*// ----*

*we're just dioing reduc, we're just adding some structure to it , in fact we can use the library with a redux store, while continuing to use wer existing middleware and reducers, atctions. in fact our action type is a javascript symbol,, so we're guaranteed to never mistake our action for one of wers (but we can always do it explicitly.*

*in the playpen we can do cool things, and try out experiments, this is an important *

*TDD is beautiful when we get this right*

*we're 100% doing redu herek*

*have 'testing.js' barrels basic index.js, so we can import the testing tools if we want, in the sandbox, thiis is not included the build -*

*OOP works well, we can still have very nice OOP patterns that help organize code. the reason OOP term fell out of fashion is because traditionally objects maintain their own state \
	when using classes, aways use arrow funcs for methods, so we can pass them around*

*we dont need heavy libraries like immutable.js, which pack a lot of functionality and can become performance problems since these operations need to be as light as possible, since we use them all the time. \
**show immutable functions & tests***

***we should be pure even within functions, its makes them much easier to debug, show a step by step***

* \
**examples:** \
- (simple/independent) send emails to userIds (independent) \
	- use case: we get the users as a clean array, we do call effects and at the end we create a response like results = [{ user, result }] serialize it to send it out \
	- code: function passes to an effect function, this function calls another function to get some extra data whatever, and just adds it to the users, but this data has some circular shit and now we fail serialize, hard to debug \
-  (simple/independent) functions can be moved around with no context regard \
	- we have a function to check authentication, but we grab some config as an import, if we take it as param, its much easier to test it and move it around to other places \
- (simple/independent) function effects mess with it \
	- another function causes side effect mutating config obj, causing issue that we dont catch in test, since the effect didnt happen. it should still be instantiation from the same function. \
- pure models and provisioning \
	- gt state models (we can even show the gt code) \
	- unit tests: we can test the pure constructs as unit tests \
**notes:** \
- pure constructs can run on any environment \
	it can be moved around  \
	it can be shared (tests, different platforms, different configurations) \
- "zen" because it provides clarity (less confusing, easier to reason about) and peace of mind (safety, we know what we are affecting) \
	the guarantee of immutability and purity clears wer mind of vague concerns about  potentialities like what might be affected \
- typescript becomes a better tool \
	allows for much stronger types, since there arent things coming in and out of objects, we dont have to consider how an object might change, so we can be more precise \
	 anytime the definition of wer inputs/outputs change, it will tell we everywhere that we need to update in wer code \
	*


```
i can do a reference comparison because immutabilioty assummed
   if (this.type() !== query.type()) return false
   if (this.provisions !== query.provisions) return false
   if (this.options !== query.options) return false

```



* 