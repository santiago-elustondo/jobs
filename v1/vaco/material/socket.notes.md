---
title: socket.notes.md
---

* problems
    * private key per client
    * which users are subscribed/connected/joined to rooms?
        * currently inside redis socketio
        * if we want single socket
            * user1 (CA) and 2 (UK) both joined room a (CA)
            * user sends message, suppose to send to all users in room
    * i (server) have list of users that should receive a message if connected
        * i need if they are connected and their private keys so i (server) can encrypt
        * users are connected to various different POCs 
* arch 
    * each client has unique key for each region 
        * otherwise we have to store a private key for each user/region and provide it as part of post-authentication user info. solves the problem of DR just fine, we already have authentication/authorization done through other means. performance-wise not that much better, unless user has tons of tabs.
* SOT state
    * public keys for servers (in order to do single handshake)
    * subscriptions (spaces, user presence maybe by company)
    * connected user clients 
        * point-of-contact it is connected to
        * client's public keys (one per region)
* cases
    * user connect
        * poc code: call sdk's "client connected" after handshake
    * user join space
        * server/poc code: call sdk's "subscribe to space" / "user enter space"
    * space event for connected users
        * server code: create event 
        * server sdk: 
            * ask SOT for who is subscribed (each client/public key)
            * encrypt message for each client using public key
            * emit encrypted messages for clients (batched)
        * sot: pass messages down to pocs
        * poc: pass message down to client
        * client: decrypt message
    * space event for members
        * server code:
            * create event
            * figure out which users should receive
        * server sdk:
            * ask SOT for clients for these users (we get only those connected)
            * encrypt message for each client using public key
            * emit encrypted messages for clients (batched)
        * sot: pass messages down to pocs
        * poc: pass message down to client
        * client: decrypt message