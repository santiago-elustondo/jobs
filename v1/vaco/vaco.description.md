---
title: vaco.description.md
---

### vaco
* 2020/06 - 2021/11
* roles:
  * director, technical solution delivery (2020/11 - 2021/12)
  * technical lead (2020/06 - 2021/04)
* Technologies: Gcp-networking, terraform, k6, typescript, gcp-pubsub, gcp, socket.io, redux , mongo, redis
* Led and supported the assessment and delivery efforts for Vaco Toronto's consulting engagements. Gathered requirements and KPIs, reached consensus on solutions and roadmaps, worked with the recruiting department to assemble teams, and provided support throughout the engagement in both technical and organizational capacities, addressing feedback and escalations from all corners.
* Led the Avaya Spaces project, a suite of globally-distributed enterprise communication and collaboration tools, supporting a large array of client devices.
#### avaya
* to enable new react-native client app team & formalize front-end data model (including encryption/server api layer & business domain), architected and delivered typescript sdk package repo to replace & deprecate existing web client parts & be used also by new react native client. avaya client-side sdk had to make requests to various independent regional cluster deployments depending on company data location & maintain subscriptions to multiple socket conns, etc. our platform-agnostic client-side DAL importable library abstracted this away, taking, for example, target user for message, and either reading from there or querying global federation service (which held ony metadata) to learn that user's company's data location as configured by their company's admin.
* designed & impemented, in collab with my team (5 eng) and client's engineering leadership (vp of tech & his people), a nodejs service abstration for real-time socket communication that "mocked" server-side socket.io object-oriented api (socket.emit(), socket.userdata = {..}, io.on('connect', cb)). it internally continued to use socket.io with redis pub-sub adapter when both users' companies resided (as per company admin config) in the same geographic full-stack deployment region, since the socket connections would both be present within one of the cluster instance connected to our redis instance (single per cluster). otherwise, the message would be encrypted & published to our google pubsub (global), decrypted by the target region cluster (encrypted  using target private key, publisher public key) and emitted using local socketio redis. the api interface remained largely unchanged from socketio, requiring very little change in server code to enable geo-distributed transmission compliant with data sovereignty/residency requirements of regional laws such as GDPR/california.