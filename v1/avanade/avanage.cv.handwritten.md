### avanade
* 2018/10 - 2020/06
* roles: senior software consultant -> technical lead
* Technologies: Angular, typescript, sql-server, azure, mocha, node, jest, microservices, aws, graphql, net, docker,enkins, redis,openshift, mongo,selenium
* Led agile delivery teams (4-6 developers, 2 QA, 1 Scrum Master) in technical planning and implementation, providing guidance and support, handling technical escalations, and converting requirements into scalable technical solutions that fit client timelines and expectations.
* Develop horizontally-scaling (distributed) NodeJS microservices to serve as backend for the Telus MyWifi app, which interoperates with a number of downstream systems and devices to allow users to configure and monitor their home WiFi.
* Audit performance, discuss findings and solution proposals with client architecture leads, and undertake improvements to core libraries for the Mortgage * * Cadence Platform, an enterprise fintech application used by the largest mortgage lenders in North America.
* Designed and delivered in-depth multi-day training programs for client organizations on the subject of performance profiling and optimization of web apps, using modern client-side JS frameworks (primarily Angular and React).
#### advanced react workshop
#### telus digital 
#### mortgage cadence platform (accenture)
* large angular application with many independent teams contributing. i was asked to analyze poor responsiveness issues in pages with large grids or animations, jankiness. rearchitected grid components to use a unidirectional state cycle, and separated them into 2 separate components, an orchestrator/state-machine smart stateful wrapper api surface and an internal OnPush UI renderer with optimization logic in its attribute setters to minimize change detection frequency and cost. also identified numerous cases of intervallic javascript activity that could be converted into css code in the case of visual animations, or alternatively executed "outside of angular". used performance flamegraphs with ui snapshots to demonstrate radical responsiveness improvements.