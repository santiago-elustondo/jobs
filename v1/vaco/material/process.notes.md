---
title: process.notes.md 
---

### avaya-spaces process

* [https://github.com/esna/Logan/wiki/Development-and-Asana-Task-Workflow](https://github.com/esna/Logan/wiki/Development-and-Asana-Task-Workflow) 
* [https://github.com/esna/Logan/wiki/Branching-strategy-and-environments](https://github.com/esna/Logan/wiki/Branching-strategy-and-environments) 
* /always/ put task owner's name in square brackets in task title whenever assigning it to another developer (ex: reviewer).
    * if another dev is going to contribute, we may assign a subtask to them instead (and not reassign task, therefore no need to put owners name in title)
* owner's name in branch name for task
* tasks should never be "due" in the past /the day youll handle it, dont stack/
* merging tasks
    * merging must always be done by the task's board's owner
        * exception: if adrian is board's owner then one of our team leads merges
    * if its our board and there are substantial logic changes to existing functionality, we require pr approval from avaya dev lead
    * if its a patch fix, when submitting to board owner
* put pr link in asana task, put asana link in pr description
* to move a task into "review" (pr review followed by merge)
    * always assign the task to whoever needs to look at it next (reviewer, merger)
    * Write down relevant description and test instructions if required on the Asana Item on the pr description to let the people reviewing or Testing know how to test your task or fix.
    * Assign an appropriate “Due Date” for the Reviewer so they know when to handle this task. Usually, it is set to today or else you can set it to tomorrow if the task is not urgent.

### prodigy-specific process

* when any task is created that is on our plate (anyone of our team), add it to team-prodigy board (todo column).
* columns
    * todo: havent started
    * discovery: gathering info (how to replicate, how does it work, etc)
    * design: figuring out a solution (sometimes this requires meetings, etc)
    * implementation [should have story points, completion date]
    * review: [pr exists and is awaiting approvals] and merge or it goes back to a previous stage
    * done
* try to get story points / completion date onto your task as soon as you have enough info. these can be amended with new info. 
    * story points / completion dates (including amendments) must be agreed on by peers. owner makes proposal.
    * story points are fibonacci 
    * 1 story point is an obvious text change with no complexity
* tasks should have story points / completion date when we're comfortable to make the guess. usually after leaving discovery. must have story points assigned if its in implementation.
    * can assign / amend points  / completion date even after completion (team must approve)
* subtasks may or may not be on the board. if they are on the board, they regular task rules

### efficiency 

* use aggregator views
    * my-tasks
    * inbox 