---
title: unified-sockets.notes.md
---

* implementation parts
    * "socket.update": socket.update() instead of property assign => sends pubsub update, updates prop on socket object, remembers so that we send it with every message from now on
        * problem: updating socket data from another region
    * "redis meta": store meta in regional redis
        * do we need this? if we're attaching pod ids/socket ids, and making sure same pod handles events, seems like we dont
    * "pod id": each socket pod has its own id / subscription, and we tack pod id and socket id onto messages
        * so that same pod handles events from another regions. this way we can do socket.emit() and socket.broadcast (and dont need redis)
    * "tracing": we tack tracing info for logging onto messages
        * so we can debug across regions
* doc
    * solution overview: 
        * pubsub: as a global communication channel between regions
            * layout diagram
                * all pods connect to pubsub topic individually
                * show pods in both regions connected via socket
                * show users subscribed to room connected to pods across regions
        * mock socket: so we dont have to change the application behaviour
    * explain problems
    * explain solutions
    * example cases (flow diag + explanation + pubsub message structure)
        * user socket msg, meta updates, does socket.join, does socket.broadcast (translates to broadcast if youre the pod with connection, or emit to room) emits msg to room, handled by foreign region
            * prep
                * regions/pods/clients/rooms, etc
                    * client_r1_p1_1 (main)
                    * client_r1_p1_2
                    * client_r1_p2_1
                    * client_r2_p1_1
                * user msg handler (subscribe)
                    * resolveTargetRegion: topic id
                    * handle: 
                        * check has access in topic database
                        * update meta to include channel
                        * do socket.join
                        * broadcast presence
                        * emit msg to room 
            * flow steps
                * client_1 (pod_1, region_1) sends subscribe request to pod_1 (region_1). 
                * handler target region resolver says region_2
                * pubsub msg to region 2 (includes originator pod id and tracing, etc)
                * region 2 receives, makes fake socket, runs handler
                    * update meta sends out pubsub msg to pod
                    * socket.join sends pubsub msg to pod
                    * socket.broadcast sends ps msg to pod and everyone else
                    * room emit sends msg to everyone
    * fake socket api overview
        * emit, broadcast, etc..
        * update() &lt;- mine
        * registerHandler() &lt;- mine