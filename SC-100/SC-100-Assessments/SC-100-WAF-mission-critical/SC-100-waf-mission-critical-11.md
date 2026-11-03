# Answer Q11-A01

## Selected Options
Options 01
Options 02
Options 05

---

> Refs

[Domain-driven Design: CQRS in Practice - Lindsey Broos](https://app.pluralsight.com/ilx/video-courses/domain-driven-design-cqrs-practice/course-overview)  

[Microservice Architecture in ASP.NET Core by Roland Guijt](https://app.pluralsight.com/ilx/video-courses/clips/d5835b43-0391-4ac9-9af8-7d51047b54da)  

[Microservices: Developing Reactive Systems by Meenakshi Sharma - Event Sourcing for Reliability](https://app.pluralsight.com/ilx/video-courses/clips/679f7a5d-0c9b-4648-aa3a-8ad39f1a543c)  

[Managing Advanced Kubernetes Logging and Tracing course By Piotr Gaczkowski - Event Sourcing](https://app.pluralsight.com/ilx/video-courses/clips/052e4ac6-31e9-4af7-bc44-6b0e0aab6fa3)  

1. Command Query Separation Pattern (CQS)

- `Commands` perform an action and may change the state of an object 
- `Queries` only return data and never have side-effects, therefore neve change the state of any object
- in `CQS` no method should be at the same time a command and a query, it must be either 

2. Command Query Responsibility Segregation Pattern (CQRS)

This apttern is often used in reactive event-driven apps.

- `Commands` are incapsulated in models that perform an action that may change the state of an object: mutable operation  
- `Queries` are incapsulated in models that return data and never have side-effects, therefore neve change the state of any object: immutable operations  

3. Event Sourcing Pattern 

This pattern allows to replay the system state at any given point in time.
The events (the commands) are stored in some kind of a DB, typically called `Events Store`, and then applied in order.
This provides an automatic audit trail for the state of the system - its a way to implement its observability.

The following are the typical parts in the implementation of the `Event Sourcing Pattern`:

- `Event Queue` where all new events enter the system, i.e. use `Kafka Topics` 
- `Event Store` keeps a permanet record f all the events - a journal of everything that has ever happened, i.e. `Kaftka Event Store`
- `Event Hanlder` are the microsoervices that consumes events and act on them, i.e. CRUD ops on a DB
- `Snapshot Store` some event-handlers (microservices) create a snapshot,; simplified views of the latest state to improve the performance of queries. A snapshot is a sort of cache state that can always be reconstructured by replaying the events from the Event Store

---

# Q11

## Mission Critical: Data Platform

[How is data throughput factored into the application design?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=7508c73d-3c12-46d6-965a-93d1c9644997&category=29cd0819-ea59-4039-bc04-f46ee79cc22d)     

# How is data throughput factored into the application design?

The speed with which data is emitted from various application components, and the throughput requirements 
for how fast data needs to be committed and retrieved, are critical for determining an optimal data technology 
for key workload scenarios.

##  Options 01
Different data workloads (`transactional`, `analytical`) are separated.

Data can be used in different contexts and each context can use a different technical stack.

##  Options 02
Read and write throughput can scale according to expected load patterns.

Load levels will naturally fluctuate for many application scenarios, with natural peaks requiring 
a sufficient degree of elasticity to handle variable demand while maintaining throughput and latency.

##  Options 03
Load-leveling patterns are implemented for high-throughput scenarios.

Load-leveling patterns such as `CQRS` or `Event Sourcing` are commonly used to maintain steady performance under load.

##  Options 04
Data platform is ready for agile scaling.

If load levels are highly volatile, the data platform must be able to adjust capacity to maintain performance regardless of demand.

##  Options 05
Azure-native data services with automated scale-operations are prioritized.

Agile scalability is key to effectively support variable throughput and load levels without overprovisioning capacity levels.

##  Options 06
Read and write throughput is monitored against application capacity model.

Both read and write throughput must scale according to application requirements and load. 
Both vertical and horizontal scale operations can be applied to respond to changing load levels.

##  Options 07
None of the above.

---
