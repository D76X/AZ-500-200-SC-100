# Answer Q04-A01

## Selected Options

##  Options 03
Application code uses standardized packages to implement resiliency patterns, such as Polly for C# or Microsoft Sentinel for Java.

Most programming languages provide standardized and validated packages for resiliency patterns that can be used to optimize code reliability.

---

> Refs

[Polly Is Going Paid. Here Are Your Options. Milan Jovanović](https://www.youtube.com/watch?v=WwaagsisO1o&t=1s)  

---

# Q04

## Mission Critical: Application Design

## [Has the application code been designed and developed to be resilient?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=3f7e518b-119a-481a-ab7d-b58197e67a0e&category=437b295b-90d3-4190-812e-34f7ebb05df2)

## Has the application code been designed and developed to be resilient?

A mission-critical application must be developed with resiliency in mind. 
It is therefore critical for the application code to be designed and developed to be resilient, ensuring that the application can respond to failure, which is an unavoidable characteristic of highly distributed multi-tenant cloud environments like Azure.

---

##  Options 01
Application components have been designed to apply key resiliency patterns for self-healing, such as retries with back-off and circuit breaker.

The application code should address as many failure scenarios as possible in order to maximize service availability and reliability. Application code resiliency patterns go great lengths to transparently handle transient faults such as network packet loss, or the temporary loss of a downstream dependency.

##  Options 02
Built-in resiliency capabilities within Azure service SDKs, such as retry mechanisms, are applied.

Vendor-provided SDKs, such as the Azure service SDKs, will typically provide built-in resiliency capabilities. These capabilities provide a standardized and validated approach to optimize the reliability of application code.

##  Options 03
Application code uses standardized packages to implement resiliency patterns, such as Polly for C# or Microsoft Sentinel for Java.

Most programming languages provide standardized and validated packages for resiliency patterns that can be used to optimize code reliability.

##  Options 04
Application code implements the retry pattern to handle transient failures effectively and transparently.

An application should handle transient failures when attempting to connect to a dependent service or network resource, by transparently retrying failed operations. A retry pattern can greatly improve the overall stability of application code.

##  Options 05
Functional checks are exposed through health endpoints that external monitoring solutions can poll to retrieve application component health statuses.

Health Endpoint Monitoring should be interpreted alongside key operational metrics to inform application health and trigger operational responses, such as raising an alert or performing a compensating roll-back deployment.

##  Options 06
Correlation IDs are used for all trace events and log messages to tie them to a given request.
A correlation ID is a GUID automatically generated for every incoming request.

##  Options 07
Common engineering criteria is defined for all microservice teams to drive consistency in the use of application-level resiliency patterns.
Common engineering criteria is an essential tool for a complex mission-critical workload to ensure code quality across service teams, as well as to accelerate development.

##  Options 08
None of the above.

---