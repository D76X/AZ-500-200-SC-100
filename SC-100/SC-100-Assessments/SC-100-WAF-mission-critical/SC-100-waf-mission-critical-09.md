# Answer Q09-A01

## Selected Options
##  Options 01
##  Options 02
##  Options 03
---

# Q09

## Mission Critical: Application Design

[How are individual application components decoupled?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=b3dd6b56-94eb-4947-8c93-220c8a28f4a0&category=3b978c5b-050a-4758-91ce-15c48a3800e1)  

# How are individual application components decoupled?

When implementing loose coupling, event-driven architecture and asynchronous 
message processing are key design patterns for interactions that don't require 
an immediate response.

##  Options 01
Event Hubs are used for scenarios that require high throughput and 
that can work with message ordering on a partition-basis.

Event Hubs provide an Apache Kafka-compatible messaging interface.

##  Options 02
Individual application components are decoupled using asynchronous event-driven communication between them.

Individual application components don't depend on synchronous communication for operations that can be handled asynchronously.

##  Options 03
Azure Service Bus is used for scenarios that require a higher QoS and message guarantee by implementing two-phase commits.

Azure Service Bus provides reliable asynchronous message delivery that requires polling.

##  Options 04
None of the above.

---