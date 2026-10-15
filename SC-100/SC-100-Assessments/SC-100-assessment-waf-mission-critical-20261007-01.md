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

To achieve a highly available application design, all functional aspects of the solution must be capable of scaling to meet changes in demand. A scale-unit architecture helps achieve this by allowing related components to be scaled independently as a logical unit or function. 

A scale-unit can be 

- application code components, 
- Azure resources, or even 
- deployment stamps that encompass multiple related components. 

Typically, a scale-unit architecture will consider multiple levels of nested scale-units to ensure key functional aspects can be scaled independently or together.

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

# Q01: Analysis

## I am studying for the SC-100: Microsoft Cybersecurity Architect Microsoft.

As part of the preparation to the exam I try to go through some of the Well-Architected Review Assessments. 
I have the following question from the Mission Critical | Well-Architected Review Assessment.  

---

# Q01: Analysis Response by PICO

## What “scale-unit” means

A **scale-unit** is a part of the solution that can be increased or decreased as a logical group. 
It might be a single service, several dependent services, a complete regional deployment stamp, a subscription, or a group of tenants.

The Microsoft guidance recommends using nested scale-units—for example, independently scalable application components inside a larger regional deployment stamp. A deployment stamp is an independently deployable copy of the components needed to process business transactions. [learn.microsoft](https://learn.microsoft.com/en-us/azure/well-architected/mission-critical/mission-critical-application-design) [learn.microsoft](https://learn.microsoft.com/en-us/azure/architecture/patterns/deployment-stamp)

For the examples below, imagine a **multi-tenant SaaS order-processing platform**:

- Customers use the platform to browse products and place orders.
- The platform has frontend APIs, checkout services, background workers, queues, databases, and monitoring.
- Some customers generate much more traffic than others.

---

## Option 01 — Define non-functional requirements for critical flows

> Key non-functional requirements for performance and availability are defined for critical system/user flows.

### Short example

The team defines separate requirements for each important user flow:

| User flow | Example requirement |
|---|---|
| Browse products | 99.9% availability and response time below 500 ms |
| Place an order | 99.99% availability and response time below 300 ms |
| Process payment | No lost transactions and automatic retry |
| Generate reports | Can be delayed by several minutes |

### What this means

The platform does not treat the entire application as having one generic performance target. The **checkout flow** is more critical than report generation, so it may receive dedicated capacity and stronger availability guarantees.

This helps the architects decide what belongs in the same scale-unit and what should scale separately.

---

## Option 02 — Understand the scale limits of all components and Azure resources

> The scale limits of all application components and underlying Azure resources are understood.

### Short example

Before going live, the team documents the relevant limits for:

- Maximum API instances
- Maximum database throughput
- Queue or messaging throughput
- Maximum connections
- Storage account limits
- Regional capacity
- Subscription quotas
- Deployment and provisioning time

During a load test, they discover that the checkout database reaches its throughput limit before the API does. They therefore partition the data and prepare a second database scale-unit.

### What this means

Scaling the application servers alone is not sufficient. If the database, queue, network, or subscription reaches a limit first, the whole application can still fail to scale.

The important exam idea is:

> **Know what limits each component, Azure resource, region, and subscription before designing the scaling strategy.**

---

## Option 03 — Make every application component scalable

> All application components are able to scale independently or as part of a logical scale-unit.

### Short example

The order platform contains:

- Frontend API instances for customer requests
- Checkout service instances
- Background order-processing workers
- Notification workers
- Queue partitions
- Database partitions

During a promotion:

- Frontend APIs scale from 5 to 20 instances.
- Checkout services scale from 4 to 16 instances.
- Notification workers remain at 2 instances because email traffic has not increased.
- Order-processing workers scale independently based on queue length.

### What this means

The system does not have one indivisible application server that must be enlarged every time any function becomes busy.

Each functional area either:

1. scales independently, or  
2. is grouped with related components into a logical scale-unit.

This is the core purpose of scale-unit architecture: compartmentalizing the solution so that capacity can be added where it is needed. [learn.microsoft](https://learn.microsoft.com/en-us/azure/well-architected/mission-critical/mission-critical-application-design)

---

## Option 04 — Define relationships between scale-units using a capacity model

> The relationship between scale-units is defined according to a capacity model and non-functional requirements.

### Short example

Load testing shows that the following relationship is required:

- 1 API scale-unit handles 1,000 order requests per minute.
- Every API scale-unit produces approximately 200 queue messages per minute.
- 1 worker scale-unit can process 400 queue messages per minute.
- Therefore, 2 API scale-units require approximately 1 worker scale-unit.
- 10 API scale-units require approximately 5 worker scale-units.

The platform automatically scales the workers when the API layer grows.

### What this means

Components must scale in proportion to their dependencies. Otherwise, one layer becomes a bottleneck.

A capacity model expresses relationships such as:

> “For every 1,000 requests per minute, we need three API instances, two queue partitions, and one worker group.”

Microsoft describes the boundaries and relationships of scale-units as something that should be defined using a capacity model and expected performance. [learn.microsoft](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-mission-critical/mission-critical-app-platform)

---

## Option 05 — Deploy an entire regional stamp as one scale-unit

> An entire regional stamp can be deployed as one logical scale-unit.

### Short example

The team defines a **West Europe order-processing stamp** containing:

- Frontend APIs
- Checkout services
- Background workers
- Queues
- Regional data stores
- Key Vault resources
- Regional monitoring
- Networking components

Using infrastructure as code, the team can deploy a complete second copy of the stamp in West Europe when demand increases.

Traffic is then distributed between the two stamps.

### What this means

Instead of manually adding individual resources, the team deploys a complete, tested group of related resources.

A regional stamp can also support:

- Horizontal scaling
- Disaster recovery
- Independent updates
- Regional isolation
- Easier capacity management

A stamp normally contains the components required to complete business transactions, and a region can contain more than one stamp. [learn.microsoft](https://learn.microsoft.com/en-us/azure/well-architected/mission-critical/mission-critical-architecture-pattern) [learn.microsoft](https://learn.microsoft.com/lb-lu/azure/architecture/databases/architecture/azure-data-factory-mission-critical)

---

## Option 06 — Measure how long scale-out and scale-in take

> The time required to perform scale operations is measured across all scale-units.

### Short example

A load test produces these results:

- API scale-out: 45 seconds
- Checkout service scale-out: 90 seconds
- Worker scale-out: 4 minutes
- Database capacity increase: 8 minutes
- New regional stamp deployment: 20 minutes

The team discovers that workers scale too slowly during a sudden promotion. To compensate, they keep a minimum number of workers running and scale them proactively before expected traffic peaks.

### What this means

It is not enough to know that a component **can** scale. You must also know **how quickly** it scales.

If traffic rises faster than the system can add capacity, users may experience:

- Increased latency
- Queue buildup
- Failed requests
- Timeouts
- Reduced availability

Microsoft’s mission-critical guidance specifically notes that scale-out operations can temporarily affect user experience, so the timing needs to be understood and tested. [learn.microsoft](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-mission-critical/mission-critical-app-platform)

Scale-in should also be measured because removing capacity too quickly can cause instability during a traffic fluctuation.

---

## Option 07 — Isolate development, test, and production subscriptions

> Each environment type uses at least one dedicated subscription.

### Short example

The company uses:

- `OrderPlatform-Development`
- `OrderPlatform-Test`
- `OrderPlatform-Production`

A developer creates 50 test databases in the development subscription. Those resources do not consume the production subscription’s quotas.

A test deployment also cannot accidentally overwrite production resources because the environments have separate management and identity boundaries.

### What this means

This option is mainly about **isolation and governance**, not just performance.

Separate subscriptions help prevent:

- Lower environments consuming production capacity
- Accidental production changes
- Permission spillover
- Test resources affecting production quotas
- Confusing billing and ownership

Microsoft describes dedicated environment subscriptions as a way to prevent lower environments from contributing to scale limits and to provide a clear management and identity boundary. [learn.microsoft](https://learn.microsoft.com/en-us/azure/well-architected/mission-critical/mission-critical-deployment-testing)

---

## Option 08 — Use multiple production subscriptions as scale-units

> The application is designed to use multiple Azure production subscriptions, with a subscription serving as a scale-unit.

### Short example

The company’s production platform has:

- `OrderPlatform-Production-01`
- `OrderPlatform-Production-02`
- `OrderPlatform-Production-03`

Each subscription contains a complete, independently deployable production capacity unit. A global routing service distributes traffic across them.

When the first subscription approaches its resource or quota limits, the team deploys another identical production unit into the next subscription instead of trying to keep expanding the first one.

### What this means

A subscription can become an **outer scaling boundary**.

This is especially useful for very large workloads where a single subscription’s limits could restrict:

- Number of resources
- Number of instances
- Networking capacity
- Regional resource availability
- API or management operations
- Deployment throughput

This does not mean every application should use multiple production subscriptions. It is mainly relevant when the expected scale is high enough that one subscription could become a constraint. Microsoft identifies subscriptions as a management, billing, and scale boundary, and recommends multiple production subscriptions when the scale requirements justify them. [learn.microsoft](https://learn.microsoft.com/en-us/azure/well-architected/mission-critical/mission-critical-deployment-testing) [learn.microsoft](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/resource-org-subscriptions)

### Important distinction from Option 07

- **Option 07:** separate subscriptions for environment isolation.
- **Option 08:** multiple production subscriptions to increase the available scaling boundary.

---

## Option 09 — Make one tenant or a group of tenants a scale-unit

> One or more tenants are segregated as a scale-unit that can be scaled independently.

### Short example

The platform serves 500 customer organizations.

- Most small customers share several stamps.
- A large customer generates 40% of all traffic.
- That customer is assigned to a dedicated stamp.
- The dedicated stamp can be scaled independently without scaling every other customer’s environment.
- The customer can also receive a feature that is enabled only on that stamp.

### What this means

A **tenant** is usually a customer organization using the SaaS platform.

Tenant-level scale-units allow the platform to:

- Isolate a high-volume customer
- Scale one customer without scaling everyone
- Reduce noisy-neighbor effects
- Apply tenant-specific configuration
- Roll out features to selected customers
- Move a tenant to a larger or dedicated stamp

This is commonly implemented by assigning tenants to deployment stamps. The deployment-stamp pattern supports serving predefined groups of tenants from independent copies of the application. [learn.microsoft](https://learn.microsoft.com/en-us/azure/architecture/patterns/deployment-stamp)

The wording in the assessment appears to contain two typographical errors:

- “indignantly” should be **independently**
- “inherit scale-limits” should be **inherent scale limits**

---

## Putting all nine together

A mature design might look like this:

```text
Global platform
|
+-- Production subscription 1
|   |
|   +-- West Europe stamp
|       |
|       +-- API scale-unit
|       +-- Checkout scale-unit
|       +-- Worker scale-unit
|       +-- Tenant group A
|
+-- Production subscription 2
|   |
|   +-- West Europe stamp
|       |
|       +-- API scale-unit
|       +-- Checkout scale-unit
|       +-- Worker scale-unit
|       +-- Dedicated high-volume tenant
|
+-- Test subscription
+-- Development subscription
```

The underlying reasoning is:

1. Define requirements for each important user flow.
2. Understand the limits of every component.
3. Ensure all functional components can scale.
4. Model how components must scale together.
5. Package related components into regional stamps.
6. Measure how fast each scale-unit changes capacity.
7. Separate non-production environments.
8. Use multiple production subscriptions when necessary.
9. Isolate tenants or tenant groups when their capacity needs differ.

### Simple exam interpretation

When you see this question, think:

> **Can the solution add capacity at the right level—component, function, stamp, subscription, region, or tenant—without unnecessarily scaling unrelated parts of the system?**

If the answer is yes, the architecture is making good use of scale-units.

---