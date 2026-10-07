# Mission Critical | Well-Architected Review - Oct 7, 2026 - 11:16:49 AM

[Assesment FAQs](https://learn.microsoft.com/en-us/assessments/support/)  

Mission Critical | Well-Architected Review
Evaluate your mission critical workloads by assessing the technical design areas and overall operational effectiveness.

- Length of assessment: 60 minutes
- Format: Multiple choice and multiple response questions.
- Results: Receive curated and personalized guidance that fits your specific scenarios.

---

# Q01

## Mission Critical: Application Design

# Can you scale the solution independently as logical scale-units?

To achieve a highly available application design, all functional aspects of the solution must be capable 
of scaling to meet changes in demand. A scale-unit architecture helps achieve this by allowing related 
components to be scaled independently as a logical unit or function. 

A scale-unit can be 

- application code components, 
- Azure resources, or even 
- deployment stamps that encompass multiple related components. 

Typically, a scale-unit architecture will consider multiple levels of nested scale-units to ensure 
key functional aspects can be scaled independently or together.

##  Options 01

Key non-functional requirements for performance and availability are defined for critical system/user flows.
Technical and business scenarios will likely have distinct considerations for resilience, availability, latency, capacity, and observability. Defining key non-functional requirements at the user-flow level will allow for relative flexibility in the design, tailoring the definition and boundary of scale-units.

##  Options 02

The scale limits of all application components and underlying Azure resources are understood.
Each Azure resource considers limits or quotas that can serve as barriers to scale if not appropriately considered within the design. All relevant limits should therefore be well understood in the context of the broader application architecture and scale requirements.

##  Options 03

All application components are able to scale, either as independent scale-units or as part of a logical scale-unit that encompasses multiple related components.
A scale-unit architecture helps to optimize end-to-end scalability so that all functional aspects of the solution can appropriately scale.

##  Options 04

The relationship between scale-units is defined according to a capacity model and non-functional requirements.
As one component scales, other related components should be modeled to scale appropriately. A capacity model captures the scale relationship between different application components as a ratio.

##  Options 05
An entire regional stamp can be deployed as one logical scale-unit.
A regional deployment stamp helps with complex deployment and update scenarios, as well as disaster recovery, since an entire region can be deployed as one unit.

##  Options 06

The time it takes to perform scale-out and scale-in operations is measured across all scale-units considered by the application.
The time it takes to perform scale operations should be understood within the context of performance requirements to ensure natural variations in traffic don't create an unacceptable level of service degradation.

##  Options 07

Each environment type, such as development, test, and production, uses at least one dedicated subscription.
This practice ensures that lower environments don't contribute toward scale limits, and it reduces the risk of lower-environment updates polluting production, by providing a clear management and identity boundary.

##  Options 08

The application is designed to use multiple Azure production subscriptions, with a subscription serving as a scale-unit.
For high-scale application scenarios with significant volumes of traffic, design the solution to scale across multiple Azure subscriptions to ensure the inherit scale-limits within a single subscription don't constrain the scalability.

##  Options 09

One or more tenants are segregated as a scale-unit that can be scaled independently.
For multi-tenant application scenarios, the ability to indignantly scale a single tenant or group of tenants is often critical. This granular tenant-level scalability can be achieved through deployment stamp tenant pinning, which has the added benefit of streamlining tenant-specific capability allowlisting.

##  Options 10

None of the above.

---