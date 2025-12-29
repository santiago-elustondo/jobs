---
title: misc-0.notes.md 
---

* which context has copy of production data (for anon users stuff)
* before eric leaves
    * kt about artillery
    * k6 discuss

actionables:
* eric demonstrate how he found / resolve the database down issue

question:
* why dont I see any socketio redis data?

Anon table:
* we're not calling expire when create, only refresh (jiamin wrote code 9 months ago)

--
eric said:

Hey Santiago - I was going through the `topicmessages` collection and definitely see the problem. 

The indexes are heavy - I am guessing the writes/updates/deletes are causing them a lot of issues. 

I can see why there is a bottleneck there with that said - I need some clarification on this:

* When we query this collection are we actually using all these fields - as there are a lot of compound indexes - and if yes how frequently are we using them - are there any rare queries - where a scan can be sufficient - need to identify all the access patterns
* Based on what I understand this collection acts as the fundamental of all the messages being sent between users - few questions:
    * Do we purge any of the data or archive it - what retention policy do we require
* The way I see it we can go with a few options to deal with this issue (and depending on the above questions)
    * Option 1 - we try to go through all the queries and see the frequencies they are used and try to eliminate/combine them
    * Option 2 - we split the data into individual collection and combine the data - unfortunately lookup does not work on shared collection - so need to do it ourself
    * Option 3 - which I think would be ideal in this situation - using event sourcing and CQRS - where we split the writes and reads - where we create a mongoldb view for our reads using aggregation pipeline - to transform the data as needed and run our queries against the view
        * This approach has a lot of benefits and flexibility and decouples the system but it adds its own complexity 

These are some options - but I need to really get a better understanding on the queries that this collection is hit with.
