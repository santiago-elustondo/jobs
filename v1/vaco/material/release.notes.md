---
title: release.notes.md
---

* how to split up the code commits by feature
    * client changes are more, but we can have the client use old logic and continue working.
    * backend changes are more difficult to separate, but they are less
* can we just deploy all changes into staging (sharing database) and validate with deep regression via QA. this way we dont have to deploy piecemeal by feature.
    * ray: yea
    * we can't sit in staging for too long, because we'll block the pipeline, so we should use our own deploy to perform QA (see below)
* ray: clean up and **raise PRs for logan and spaces-front**, so we can have more visibility into proposed changes. We don't have to merge it, but we can do thorough reviews while we work.
    * 1) make private branch from feat/multi-cluster -> santi/multi-cluster
    * 2) make branch from feature/candidate -> feature/multi-cluster
    * 3) make pr from santi/multi-cluster to feature/multi-cluster
* can we ask **QA to perform regressions on our deployment**?
    * ray: yes, we can. but QA team is busy so we need to find a timeslot
    * we should put **fake accounts in a document** to share with QA people, accounts will be in different flavors, etc
* adrian: we should set up the existing **E2Es** to run in our deploy pipeline
    * ray: yes, and we should add more E2Es while we're at it
    * some staging cloudbuild triggers have E2Es integrated, ask hong to help us set it up. it takes pretty long to run (6hrs), so we should** add it to cloudscheduler **to run every day but not hold up deploys. we need to learn how to identify errors and log them into asana, assign a daily task to the team to review E2E fails.
* we need to test the **process of adding new flavors** while using, so we know what to expect when we are in prod and decide to add a new flavor
    * terraform should build new flavor infra, then deploy services, then we enable flavor in db, then a company becomes able to select this flavor for their company. should not cause issues? validate
* ray: we should provide the feature **as a "beta" feature**. not sure what changes would be required here. what does it mean for us to release as "beta"?
    * the main difference here is logistical: bug fixes and support are "hot issues", a lot more urgent than if we're testing in shadow (not real users)
* **"shadow" release**
    * raised hands feature is released like this
    * only available to specific companies (you give it to them as a super admin)
    * enable it for product managers, etc
        * problem: all these people are in the "avaya" company, so its all or nothing for the avaya company, unless they create new accounts
            * we can override company settings via user settings, set by superadmin. we have a single function determineFlavorForUser(). so it doesnt matter if they have a different flavor than rest of company. (validate this and integrate into the current feature toggle ui for super admin)