---
title: geo-policy-v1.doc.md
---

# Avaya Spaces: Geographic Policy Feature

## General Overview

### Business Goals & Requirements

#### Goals

The goal behind the **Geographic Policy (GP)** feature is to enable clients to configure a policy dictating the geographical locations where their data may exist in readable form until it reaches an authorized user. 

When some data belonging to a client, before reaching an authorized user, exists in readable form only within the regions allowed by that client's GP, we can say that this data is **GP compliant.**

If we can guarantee all data belonging to all clients is GP compliant when it is **at rest** (or **stored**), then we can say that we offer a **Data Residency (DR) **guarantee.** **

If we can guarantee all data belonging to all clients is GP compliant when it is at rest *and *when it is transit, then we can say that we offer a **Data Sovereignty (DS)** guarantee.** **

#### Requirements

##### User Ownership

Every user account has a **primary company**. A user's primary company is the one associated with the email address domain for that user. We can also say that a user *belongs* to their primary company ("primary company" is implied when we say "a user's company"). A company's GP applies to all its users.

##### Components of a GP

A company's GP defines the following:

1) A **home region (HR)** selected from a list of supported regions. If none is selected, then that client's home region is Frankfurt, Germany. 

The terms **foreign** and **local** refer to the region housing some entity or data from the perspective of a company or user, such that the entity or data is *local* if housed in the company or user's home region, or otherwise *foreign*. From a company's perspective, the **local region** is that company's HR, while all others are **foreign regions**. 

Likewise:
* From a company's perspective, a **foreign company** 's HR is different from its own (inverse being **local company**). 
* From a user's perspective, a **foreign user**'s HR is different from their own (inverse being **local user**).

2) A **strictness** setting. 

A GP may be **not strict**, in which case users of that company may generate data in foreign spaces. If a GP is **strict**, then it may **whitelist** a subset of foreign regions, allowing users to generate data in only those regions as well as the company's HR. 

##### Space Ownership

Every space is owned by a single company, and housed in that company's HR. All user-generated data (text, attachments, etc) within a space belongs to the company that owns the space and is housed within that company's HR. From a user or company's perspective, a **foreign space** is a space owned by a foreign company (inverse being **local space**). 

Every group space belongs to creator user's company. If a space is housed in a region that is disallowed by a user's GP, the user is blocked from entering.

A direct messaging (DM) space may only be created if the recipient's GP does not block the initiator's region. If creation is allowed, the space belongs to the initiator's company.

##### Configuration

A company's GP is configured by an administrator user within that company's *admin settings* page.

### Architecture

#### Global vs regional resources/services

A **regional resource** exists in readable form within a particular region, and can only be read or stored by services within that region (**regional services**). Databases, file systems, and processes are services, and they may only read or store regional resources if they are are housed in the same region. All user-generated content is a regional. Requesting a user-uploaded file, for example, will yield the requested file only if the request is made to an API server running in the region where the file is located. All regions that Avaya Spaces supports have the same regional services.

Inversely, **global resources** and **global services** are available to all regions. Metadata and system configurations is global and can be accessed by services running in any region. A map like `SpaceID => ListOfUserIDs`, representing the users that are members of a space, contains no user-generated content. Thus, it is valid metadata and may be considered a global resource and stored using a global database accessible to all services regardless of their region.

### Client Development Guide

#### Initialization

We need some extra information to initialize a client. We call `/api/flavor` to know what regions exist and how to reach them. Sample response payload shown here.

![alt_text](images/image1.png "image_tooltip")

We also need to know the current user's GP. This information has been added to an endpoint we already call when initializing. `/api/users/me/settings` has extra property homeFlavorUrls with id and urls of home flavor, show below. \

![alt_text](images/image2.png "image_tooltip")

After getting the above, we'll have all the information we need to get the data we need. All requests show be made to our home region by default, unless we know that we specifically need data from another region.

#### Locating Resources

We commonly need to know where a specific resource is located. We might have the ID of a space we want to join, but we need to know which region it belongs to make a join request or any other request for that space's data. We can find out the region that a resource like a space or user belongs to by using these global endpoints, which can be **served by any region**.	

* `/api/flavor/${id}` (get urls for region)
* `/api/users/${userId}/flavor` (get user's region)
* `/api/flavor/topic/${topicId}` (get space's region)
* `/api/flavor/email/${email}` (get personal space's region)
* `/api/flavor/invite/${inviteId}` (get invite space's region)

#### Regional Endpoints

Once we know the url for the region housing our resource, we can interact with it using the endpoints we're used to, only using the region's url as our base url.

This applies to all endpoints that expose a query or operation on* a specific space*. Endpoints that take a space ID as a parameter fall into this category.

Other applicable endpoints:

* `/api/files/getdownloadurl`, `/api/files/getuploadurl` (request should be made to the file's space's region)
* `/api/users/meetingroom/${email}` (request should be made to the user's region)
* `/api/confnumbers` (request should be made to the space's region)
* `/api/apps/pair` (request should be made to the space's region)
* `/api/mediasessions/mpaas/${spaceId}/streams/remove` (request should be made to the space's region)
* `/api/messages/parselink` (request should be made to the message's space's region)
* `/api/ideas/${ideaId}/messages`, `/api/tasks/${taskId}/messages` (request should be made to the space's region)

#### Cross-Regional Endpoints

Sometimes we need to query for resources that exist across multiple regions. For example, a user's recent spaces may include spaces from different regions. In these cases, since no single region has access to all the resources relevant to the query, a separate request to each of the regions containing some relevant resource is needed.

The responses for these requests now have an added property in their payload containing the list of other regions containing some relevant results. The client is responsible for querying all listed regions and merging the results into a single final list.

Relevant endpoints:

* `/api/users/me/tasks`
* `/api/users/me/ideas`
* `/api/users/me/spaces`
* `/api/users/me/meetings`
* `/api/users/me/attachments/natives`

#### Websocket Connections

Websocket message interfaces have not changed. The only thing we must consider is that a websocket connection is made to a particular region, so socket messages regarding a particular space will only come through the connection to that space's region, and we must send websocket messages regarding the space using this connection as well.

If we need to connect via websockets to multiple spaces simultaneously, and these spaces are in different foreign regions, we must have an open connection to each one of these regions.

We also must always keep open a connection to the global region, and also to our home region, if it is different. This is necessary to receive messages regarding global and user events respectively.
