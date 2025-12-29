---
title: uwf.notes.md
---

* chores
    * organize all existing docs and link them in tasks
    * kt session for how to run and test authorization microsevice
* asana tasks
    * ***authentication microservice***
        * owner: leandro
        * goals:
            * problem
                * current way works only for spaces-front app, we cant refresh access tokens
                    * **why? (ask ray)**
                * spaces-front currently holds secrets, which we cant have in UWF
                    * **why? what secret? clients dont usually hold private keys? anything in any client is accessible to any user**
            * solution
                * microservice create/refresh jwts
        * status:
            * code
                * progress
                    * main features
                        * happy paths pretty much done
                        * we need more error handling
                    * missing functionality
                        * widget-user company validation
                            * list of allowed widgets per company, comes from accounts system. so we need to enforce this.
                    * currently relies on 3 secrets that should be generated on runtime or injected from cloud
                        * currently hardcoded in .env
                        * **we need to consult team to figure out correct approach**
                * arch
                    * scalability
                        * redis if we need state
                        * **do we need state? stateless would be awesome**
                    * code structure
                        * unidirectional dependency tree is there
                        * **dependency injection: santi pr**
                    * style
                        * name parameters: santi pr
                    * testing
                        * **nothing right now: santi pr will get us started**
            * infra/devops/monitoring
                * **we havent discussed it**
                    * **discuss with ray & friends (umair)**
                    * **get implementation help from roman & vlad**
        * subtasks
            * santi: create pr with dependency injection and unit tests
            * leandro: widget-user company validation
            * leandro: we need more error handling
            * leandro: handle secrets properly
                * blocker: consult team to figure out approach
    * ***create react application "uwf" that compiles into web-component***
        * owner: santiago
        * goals:	
            * should consume @avaya-spaces/ui-components
            * should have these scripts
                * run-app: runs app as normal react app
                * build: builds app as normal
                * build-wc: builds app as wc
                * run-wc: runs wc build locally
        * subtasks:
            * santi: create new package "uwf" with basic react app, make sure it can import @avaya-spaces/ui-components
            * santiago: research and consult team to figure out how we should do wc
            * santiago: add script to build app as wc
                * blocker: research and consult team to figure out how we should do wc
    * ***refactor ui-components***
        * owner: nicolas
        * goals:
            * questions: 
                * **meeting: should we be integrating our refactored components back into app, like TopicIcon? the problem here is that every time somebody wants to change ui, they'll have to test it against both app, and uwf.**
            * MVP component groups
                * spaces list
                * contact list
                * simple chat
                    * **consult with team: only DMs? or spaces? how should it look?**
        * subtasks:
            * sidebar component group
                * general approach: go to sidebar, and drill down to the simplest components that it uses. copr or rewrite that component into ui-components, make it work in storybook.
    * ***create redux-state package and import in "uwf"***
        * owner: santi