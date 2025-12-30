before avanade i worked at **rangle.io** in toronto for about 1.5 to 2 years, something like that. this was a similar job description, it is also an **enterprise consultancy**, although rangle is a much more **focused offering**, they specialize in all things javascript, and there's a lot of **community involvement** and **knowledge creation** that happens there. Aside from my **client engagements**, I was the primary developer and maintainer of Augury for about 8 months. Augury is THE **open source developer toolkit to inspect and debug running angular apps** in the browser, similar to react dev tools, etc, it has been the primary dev tool for Angular for years, it exists as a devtools extension for most browsers, and as an library for automated testing in CI. 

Aside from that, I worked on a number of **assignments to client projects**. usually Rangle's projects are **front-end heavy**, we delivered web and native mobile apps written with various JavaScript frameworks, and took care of the deployment and devops as needed, they usually came paired with a **dedicated node BFF.**

This was a team of 2 \- 4 developers at any one time, myself being the **constant fixture**, and the other team members coming in and out for a few weeks to a few months, depending on availability. all types of **resources on the bench** would usually get tasked to help us while **awaiting an assignment**  (devs, designers, BAs), there was a lot of help, it was a **management challenge** because resource availability was very **unpredictable**. So, I was responsible for the development of the project, keeping the updates coming, doing investigations into new features requested by the community, planning and maintaining the backlog, and responding to requests from the open source community, and make use of the extra help when available. 

    - rangle atlas  
      - problem  
        - loading problem  
        - atlas had started as an add-on to resource guru and o  
        - api was poor, and forced us to do a data dump, all data updates were also expensive, and code was getting complex due to acrobatics the system had to do to insert more data into the available fields (serializing json into event descriptions, for example)  
        - resource guru was no longer seeing the same kind of maintenance, and we were phasing it out anyway.  
      - constraints  
        - no downtime  
        - some parts of organization still relied on RG availability  
          - most had already moved away  
      - solution  
        - mirrored the data, and did data dump ourselves.  
        - offered the apis  

  - augury: canary releases for community involvement in augury  
    - i was the primary developer and maintainer of Augury for about 8 months.   
    - Augury is the defacto Angular debugging tool, blah blah.  
    - REWRITE: We would get tons of **messages from the community,** many of them asking for features or bug fixes. the tool is meant to support **every version of Angular** at once, **changes in Angular**'s internal architecture with every release would be difficut to test for. Angular is a large, complex, and **greedy framework** that takes control of the entire **browser context with ngZone**, so it is prone to **interact with other elements** in the context in interesting ways. Beyond that, issues would arise from a vast number of places: **module bundlers, typescript compiler** versions (reflect\_metadata), as well as libraries **(even google’s own gapi client)** that would interfere with ngzone or mess with globals (**promise libraries)**, or app would use new features of angular (especially in dependency injection, which has evolved a lot over the years) somewhere in their application in an unorthodox way, we had cases where **other extensions** would mess with our messages (by flooding the browser message bus, or echoing back messages, which the augury developer tools extension relies on to communicate). it took very long to find the source of that problem since the problem was not replicable if you didnt also have that installed.  
      - point being, it was very **difficult to replicate the issues** that some users would report, as they normally didnt give us enough information. also it was difficult to prevent a new feature from **causing issues for some minority** of our users. this interfered with out **agility.** also difficult to roll out a potential solution that we expected to solve a problem that they were having, for the same reason.  
      - however, an asset was that we had a **large active community** of developers that we could communicate with.  
      - deployed **canary**, directed our users to try bug fixes there, and let new **features mature** there for a few weeks. we were able to add much more heavy **analytics and error reporting (using sentry)** that we had held back from doing in regular augury for **performance and privacy reasons,** but here it was acceptable since these were community contributors, so we could track the.  
      - canary is a great success.  
      - with the canary, we were able to **roll out to firefox** as well. we had been held back by uncertainty about the new challenges there. now we were able to **test out the waters** of course there were issues, but they were experienced by our developers in our community rather than the general public. they were able to report the issues to us intelligently and help us debug, also we had detailed tracking information about the errors.   
  - augury-labs project:  
    - forward thinking \-\> new agnostic engine   
    - ease of setup for user, integrate with angular-cli  
    - lerna/yarn workspaces for large project management (esp open source)  

 - kagen api investigation into issues, report to client. they made a determination and were happy we didnt take them down a rabbit hole. (delivered value, problem documentation, that they can use later when they decide to fix it)  
    
  - vitamin shoppe seo  
    - vitamin shoppe is an **large health product retailer** from the states, they have **storefronts and a website**. they were investing in upgrading their **ecommerce platform**, and they **came to rangle for guidance and assistance** in moving to an angular client, and integrating with their legacy spring backend, which they had began to do with some offshore teams.   
    - i was tasked to work with them full time and be their **point of contact.**  
    - one of the issues they faced was that their products would no longer **show up on search engines**. they had moved from static pages to a single page app. this was a serious problem for them.  
    - we found that the product pages were **not rendering properly for googlebot,** using the google webmaster tools, this was the **early days of angular2**, 2016, so crawlers werent good at **rendering SPAs** yet. we found that googlebot did not have **native promise support,** for example. since google is the only indexer that **offers tools to diagnose** this kind of issue, we decided to just set them up with a prendering service to serve static pages, and **configured their apache to point robots** to our prendered pages. we added the **necessary polyfills**, etc.  
    - the result was a great success and a ton of **very tangible and measurable value** for the company as a result of just a couple weeks of work. I was actually featured on the **internal rangle publication** along with some graphs of the drastic improvement in traffic to their site. I think I saved it somewhere, I could pull it up if you're interested.   

- product lead  
  - what they do:   
    - decide WHAT to build  
    - maintain backlog for (dev and design), prioritize in accordance with timelines and stakeholder feedback, and different costs of tasks/stories  
    - collect and analyse feedback from stakeholders (users, investors, analysts (marketing, business))   
  - my experience  
    - i did this during augury 100%  
      - STORY:  
        - problem:  
          - we had a lot of users, especially internationally, but still it was not widely used among the developer community, at least not as much as something like redux devtools.   
        - investigation:  
          - we collected feedback from users in open source community and did extensive internal interviews.  
        - feedback:   
          - there were some bugs that turned some people off. in particular, angular 5 was breaking augury, they had let go of the reflect metadata approach to typescript data injection.  
          - they heard about it but never felt like downloading it, never felt the pain point and had somebody tell them "oh yea, you can debug that with augury"  
          - its "cool" but doesnt solve tangible everyday problems.  
        - approach:  
          - current augury (quick wins):  
            - inject hype by giving it a facelift, fixing high-profile bugs, releasing for firefox, and writing articles  
            - some bugs were hard to fix: CANARY  
          - new engine (more long-term):  
            - solve more interesting problems that are hard to debug (as per asks from devs and architects)  
            - not easy to do on current codebase  
        - leadership  
          - worked with design teams  
          - worked with angular core team  
          - worked with devs on team  
          - stakeholder is CTO yuri   