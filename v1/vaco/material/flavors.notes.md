--- 
title: flavors.notes.md
---

### notes:
* add "per-spaces/per-client" policy config / inheritance
* start in global deploy, allow customer to change region but loses all data 
* segmenting by location [https://cloud.mongodb.com/v2/5e7d862039503232e7e93d6d#clusters/connect?clusterId=yyz](https://cloud.mongodb.com/v2/5e7d862039503232e7e93d6d#clusters/connect?clusterId=yyz)

### terms / glossary:
* regional config
* regional deployment
* routing service: we need somewhere an association between a spaces client (corporate license) and a flavor.

### goals:
* provide "flavors", where clients can select regional distribution of their account. (example: flavor1 - global, flavor 2 - germany and belgium, flavor 3 - US primary with australia fallback)

### problem:
* we need somewhere an association between a spaces client (corporate license) and a deployment ("flavor"). then, when a user requests an action or resource, we must identify which flavor to execute it against, and prevent users of a space from accessing/storing stuff outside their space's distribution.

### solution:
* provide a globally-available lookup service that can provide users with the endpoint to use for flavorful requests, (maybe and authenticate/authorize a user to act upon that space/deployment, (maybe providing a token)).

### lookup service possibilities:
* the client lookup service needs to be globally available and needs to access certain data (ie: the space/flavor config lookup, user authorizations for that space)
* possibilities:
    * one database per flavor, and one database for lookup service
        * simpler architecture, we dont have to synchronize data
        * transitioning from current is more difficult, data migrations are more difficult
    * service data replicated in each of the flavors, and service endpoint provided in each of the flavors.
        * transitioning is easier, we can put up the other 2 flavors, test them, and then push a deploy into the first one that start to route away traffic to the other 2. data migration is a bit easier, we just need to move a subset of the database into the new flavor (all the service-relevant data, and data for spaces configured for that flavor, then remove the data for those spaces from the first one)