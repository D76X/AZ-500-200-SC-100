
# Design Pattern

# Authors

[Steve Michelotti](https://app.pluralsight.com/profile/author/steve-michelotti)

---

# Mediator 

[C# 8 Design Patterns: Mediator - Pluralsight - Steve Michelotti](https://app.pluralsight.com/ilx/video-courses/c-sharp-design-patterns-mediator/course-overview)  

---

# Composite

[C# 8 Design Patterns: Composite - Pluralsight - Steve Michelotti](https://app.pluralsight.com/ilx/video-courses/c-sharp-design-patterns-composite/course-overview)

---

# Load-leveling patterns CQRS and Event Sourcing

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