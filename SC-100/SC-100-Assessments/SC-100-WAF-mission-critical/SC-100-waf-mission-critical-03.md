# Answer Q03-A01

## Selected Options

---

# Q03

## Mission Critical: Application Design

# Have you designed your application to use loosely coupled microservices with asynchronous event-driven communication?

[Mission Critical: Application Design - Have you designed your application to use loosely coupled microservices with asynchronous event-driven communication?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=702e3c29-ab92-4b08-9945-fd247131dd47&category=437b295b-90d3-4190-812e-34f7ebb05df2)

---

##  Options 01
Services are free to use different technologies and design patterns based on their unique requirements.

Loosely coupled services that communicate with each other through well-defined interfaces allow for inherit flexibility in the composition of each service. Each service can be developed using the most appropriate language and hosted on compute and data platforms that best fit its use case.

##  Options 02
Services can scale independently to optimize the use of underlying Azure platform resources.

In a microservice architecture, each service can be developed to scale independently based on characteristics about the operation of that service, such as queue length or resource utilization.

##  Options 03
The application implements end-to-end instrumentation and tracing that spans service boundaries.
In a loosely coupled microservice architecture, end-to-end tracing requires more complex orchestration since it must traverse service boundaries that likely encompass different technology stacks.

##  Options 04
Failures can be handled separately and don't affect client transactions.
A loosely coupled microservice application should be designed such that failures within a single service don't take the full application down and can be handled independently.

##  Options 05
The solution is designed to manage transactional integrity across different services.
Transactional integrity ensures that when the application attempts to commit a transaction, if part of the transaction fails, none of the transaction will be committed. Transactional integrity can be harder to manage in a distributed microservice environment because data creation and persistence might happen within separate services.

##  Options 06
None of the above.
---