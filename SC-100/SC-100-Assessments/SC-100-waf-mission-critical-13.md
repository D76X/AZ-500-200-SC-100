# Answer Q13-A01

## Selected Options

---


# Q13

# Mission Critical: Data Platform

[What measures were adopted to maintain data availability and accuracy?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=f6d969d2-7818-4881-9fe6-af97a378dab7&category=29cd0819-ea59-4039-bc04-f46ee79cc22d)  

# What measures were adopted to maintain data availability and accuracy?

Several factors must be considered to validate the accuracy of data within an application, and 
the management of these factors can have a significant bearing on the design of the data platform.

##  Options 01
A multi-region data platform design is adopted.

In any distributed application with multiple data replicas, there's a trade-off between consistency and latency, 
as expressed in the CAP and PACELC theorems.

##  Options 01
Data replicas are distributed across availability zones within a region.
Within availability zone-enabled regions, Cosmos DB offers availability zone redundancy support for high availability and resiliency to zonal failures within a region.

A multi-region write data platform design is used according to required consistency level.
While multi-region write increases overall availability, there's a tradeoff in lower consistency and the need for conflict resolution.

The application is designed to prioritize the use of local database replica.
In multi-region configurations, each deployment region should have its own "local" replica. The application can be configured to prefer it under normal circumstances to avoid cross-region queries.

Service-managed keys are used for encryption.
Azure supports various encryption models, including server-side encryption that uses service-managed keys, customer-managed keys in Azure Key Vault, or customer-managed keys on customer-controlled hardware.

Conflict resolution is properly configured.
Simultaneous writes in multiple regions can generate conflicts. A common and frequently used conflict resolution strategy is “last writer wins,” but that might not be suitable for all scenarios.

None of the above.

---

# CAP and PACELC theorems

The CAP theorem and its extension, the PACELC theorem, are core frameworks used in system design 
to describe the trade-offs distributed databases and data stores must make regarding 

- data correctness, 
- system uptime, and 
- speed. 

[1] (https://www.scylladb.com/glossary/pacelc-theorem/), 
[2] (https://www.linkedin.com/pulse/cap-theorem-vs-pacelc-consistency-availability-explained-fox4c)

1. The CAP Theorem

Formulated by computer scientist Eric Brewer, the CAP theorem states that a distributed data store 
can simultaneously provide at most two of the following three guarantees: 

[1] (https://www.ibm.com/think/topics/cap-theorem), 
[2] (https://www.scylladb.com/glossary/pacelc-theorem/)

- Consistency (C): Every read receives the most recent write or an error; all nodes see the exact same data at the same time. 

[1] (https://medium.com/@ali.gelenler/distributed-system-trade-offs-cap-vs-base-vs-pacelc-1a3bcac04a7b), 
[2] (https://www.reddit.com/r/developersIndia/comments/1svkeol/today_i_understood_cap_theorem_in_system_design/)

- Availability (A): Every non-failing node returns a non-error response to every request, without a guarantee that it contains the most recent write. 

[1] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance), 
[2] (https://medium.com/@ali.gelenler/distributed-system-trade-offs-cap-vs-base-vs-pacelc-1a3bcac04a7b)

- Partition Tolerance (P): The system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes. 

[1] (https://www.mongodb.com/resources/basics/databases/cap-theorem), 
[2] (https://www.ibm.com/think/topics/cap-theorem)

## The Reality of Distributed Systems

Because real-world networks will experience `physical partitions (P)` due to hardware or link failures, 
a distributed system cannot drop "P." Therefore, the real choice during a network failure is between 
Consistency (CP) or Availability (AP): 

[1] (https://www.linkedin.com/pulse/cap-theorem-vs-pacelc-consistency-availability-explained-fox4c), 
[2] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance)

- CP (Consistency + Partition Tolerance): The system rejects or blocks requests rather than returning potentially stale data (e.g., Apache ZooKeeper). 

[1] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance)

- AP (Availability + Partition Tolerance): The system keeps responding from local node copies, risking out-of-sync or stale data (e.g., Apache Cassandra). 

[1] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance)

---

2. The PACELC Theorem

Coined by `Daniel Abadi`, the PACELC theorem expands on CAP. 

It points out that network partitions are relatively rare; the CAP theorem says nothing about what happens during the other 99% 
of the time when the system is running normally (healthy network). 

[1] (https://www.youtube.com/watch?v=dWjiUqikRx0), 
[2] (https://www.youtube.com/watch?v=X5izO4vZBhU), 
[3] (https://www.scylladb.com/glossary/pacelc-theorem/)

PACELC is structured as: `If Partition, choose Availability or Consistency; Else (normal operation), choose Latency or Consistency.` 

[1] (https://www.geeksforgeeks.org/operating-systems/pacelc-theorem/), 
[2] (https://medium.com/@ali.gelenler/distributed-system-trade-offs-cap-vs-base-vs-pacelc-1a3bcac04a7b)

\(\text{If\ }\mathbf{P}\implies \text{\ choose\ }(\mathbf{A}\text{\ or\ }\mathbf{C}),\quad \mathbf{E}\text{lse\ }\implies \text{\ choose\ }(\mathbf{L}\text{\ or\ }\mathbf{C})\)

---

## Breakdown of PACELC Choices:

- During a Partition (P): Choose Availability vs. Consistency (same as CAP). 

[1] (https://medium.com/@ali.gelenler/distributed-system-trade-offs-cap-vs-base-vs-pacelc-1a3bcac04a7b), 
[2] (https://www.geeksforgeeks.org/operating-systems/pacelc-theorem/)

- Else / Normal Operation (E): Choose Latency vs. Consistency.

	- To get strong consistency (C) during normal operation, the system must synchronize replicas (e.g., via quorum or synchronous replication), which increases latency (L).

	- To prioritize low latency (L), the system uses asynchronous replication, meaning data might be temporarily inconsistent (sacrificing C). 
    
    [1] (https://medium.com/@ali.gelenler/distributed-system-trade-offs-cap-vs-base-vs-pacelc-1a3bcac04a7b), 
    [2] (https://www.geeksforgeeks.org/operating-systems/pacelc-theorem/), 
    [3] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance), 
    [4] (https://www.youtube.com/watch?v=dWjiUqikRx0)

---

3. Classification of Popular Databases

Databases are often categorized by how they balance these trade-offs under PACELC: [1] (https://www.linkedin.com/pulse/cap-theorem-vs-pacelc-consistency-availability-explained-fox4c)

System Category	PACELC Classification	Behavior	Examples
PA/EL	Availability / Latency	Prioritizes availability during partitions; prioritizes low latency during normal operation by using asynchronous replication.	Apache Cassandra, DynamoDB
PC/EC	Consistency / Consistency	Prioritizes consistency during partitions (blocking stale reads) and synchronizes data for consistency during normal operation (at the cost of higher latency).	Google Spanner, Apache HBase
PA/EC	Availability / Consistency	Prioritizes availability during a partition, but maintains consistency during normal operation.	MongoDB (with primary-secondary configs)

For a deeper dive into architecture comparisons, explore the technical breakdowns provided by ScyllaDB or read ByteByteGo's System Design Guide. [1] (https://blog.bytebytego.com/p/consistency-and-partition-tolerance), [2] (https://www.scylladb.com/glossary/pacelc-theorem/)

---

> Refs

[CAP & PACELC theorems explained ThatNotesGuy](https://www.youtube.com/watch?v=dWjiUqikRx0)  

---