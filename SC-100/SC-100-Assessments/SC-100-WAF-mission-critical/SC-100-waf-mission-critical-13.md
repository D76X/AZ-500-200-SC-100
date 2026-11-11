# Answer Q13-A01

## Selected Options
Options 01

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
as expressed in the `CAP` and `PACELC` theorems.

##  Options 02
Data replicas are distributed across availability zones within a region.
Within `availability zone-enabled regions`, `Cosmos DB` offers availability zone redundancy support for high availability and resiliency to zonal failures within a region.

##  Options 03
A multi-region write data platform design is used according to required consistency level.
While multi-region write increases overall availability, there's a tradeoff in lower consistency and the need for conflict resolution.

##  Options 04
The application is designed to prioritize the use of local database replica.
In multi-region configurations, each deployment region should have its own `local replica`. 
The application can be configured to prefer it under normal circumstances to `avoid cross-region queries`.

##  Options 05
Service-managed keys are used for encryption.
Azure supports various encryption models, including server-side encryption that uses service-managed keys, 
customer-managed keys in Azure Key Vault, or customer-managed keys on customer-controlled hardware.

##  Options 06
Conflict resolution is properly configured.
Simultaneous writes in multiple regions can generate conflicts. 
A common and frequently used conflict resolution strategy is “last writer wins,” but that might not be suitable for all scenarios.

##  Options 07
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

[What is CAP Theorem? IBM Technology](https://www.youtube.com/watch?v=eWMgsk7mpFc) > this extends the concept from DBs to Microservices


[CAP & PACELC theorems explained ThatNotesGuy](https://www.youtube.com/watch?v=dWjiUqikRx0)  

[CAP Theorem Simplified 2026 | System Design Fundamentals | Distributed Systems | Scaler](https://www.youtube.com/watch?v=8UryASGBiR4)   

---

# Is MongoDB a CP-type database?

Yes. Under the CAP theorem, **MongoDB is generally classified as a CP system** 
(Consistent and Partition-tolerant), as it prioritizes consistency over availability 
in the event of a network partition.

### How MongoDB Behaves in a Partition

In a standard MongoDB replica set (with one Primary node and multiple Secondary nodes):

* **Write & Read Consistency:** By default, all write operations go to the single Primary node. 
This ensures strong consistency for reads and writes directed to the Primary.

* **Network Partition Scenario:** If a network split isolates the Primary from a majority of the replica set nodes:

1. The isolated Primary steps down to a Secondary.
2. The remaining nodes attempt to elect a new Primary.
3. If a node partition cannot reach a majority ($N/2 + 1$), **no Primary can be elected**.
4. If and wghen the former primary node comes back online, it will join as a secondary node.

* **Impact on Availability:** Without an active Primary, the cluster **rejects all write operations** 
and `default strongly-consistent reads`, to preserve data integrity and prevent split-brain scenarios. 
Thus, it sacrifices availability to maintain consistency.

---

### Key Caveat: Configurable Consistency & Availability

While MongoDB's default architecture is CP, its operational behavior is highly tunable 
via **Read Preferences** and **Write Concerns**:

* **Eventual Consistency / Higher Availability:** If applications set the **Read Preference** to `secondary` 
or `nearest`, clients can continue reading data from available Secondary nodes even during a network partition 
or while no Primary is present.

* **Write Guarantees:** Using `w: "majority"` ensures that writes are acknowledged only after being committed 
to a majority of nodes, preventing dirty reads or rolled-back writes if a node failure occurs.

Under the traditional CAP theorem framework, MongoDB sacrifices write availability during a network partition 
to maintain strict data consistency, making it a **CP database**.

---

# Is Apache Cassandra an AP-type database?

Yes, Apache Cassandra is a classic example of an **AP** (Available and Partition-tolerant) 
system under the CAP theorem. It prioritizes high availability and partition tolerance over 
strict, immediate linearizable consistency.

### How Cassandra Achieves AP Behavior

Cassandra's decentralized, masterless, peer-to-peer ring architecture allows it to maintain 
high availability during network partitions:

* **No Single Point of Failure / Master Nodes:** Every node in a Cassandra cluster is functionally equivalent. There is no concept of a primary or master node that must be reachable to accept writes.

* **Network Partition Scenario:** If a network split isolates a portion of the cluster, both sides of the partition can continue to accept read and write requests from clients connected to them.

* **Prioritizing Availability:** Unlike CP databases (which reject writes if a partition causes a loss of consensus or majority), Cassandra keeps accepting data to ensure the system remains online and responsive.

---

### The Trade-off: Eventual Consistency

Because Cassandra sacrifices immediate consistency to guarantee availability, 
it relies on **eventual consistency**:

* **Data Divergence:** If different nodes accept writes for the same row during a network partition, their copies of the data will temporarily diverge.

* **Reconciliation Mechanisms:** Once the network partition heals, Cassandra uses background mechanisms like **hinted handoffs**, **read repairs**, and **anti-entropy node repair** (using Merkle trees) to reconcile conflicting data and propagate updates until all replicas converge.

---

### The Nuance: Tunable Consistency

While Cassandra's default architecture and design philosophy make it an AP database, 
its consistency is **tunable per query**.

Developers can adjust consistency levels for individual read and write operations:

* **AP Mode (Default):** Setting write and read consistency to `ONE` ensures maximum speed 
and availability, but risks returning stale data if a node is out of sync.

* **CP-leaning Behavior:** You can enforce strong consistency by setting your replication factor ($RF$) and consistency levels such that **Read Consistency + Write Consistency > Replication Factor ($R + W > RF$)**—for example, using `QUORUM` for both reads and writes in a cluster with 
a replication factor of 3.

Even with tunable consistency, Cassandra's core design under the **PACELC theorem** dictates 
that in the *absence* of partitions (the "E" in PACELC), it chooses **Latency** over Consistency, cementing its identity as an AP-first database built for massive write-throughput and uninterrupted uptime.

---

# Cosmo DB

I have the following statement: 

> "Data replicas are distributed across availability zones within a region. Within `availability zone-enabled regions`, `Cosmos DB` offers availability zone redundancy support for high availability and resiliency to zonal failures within a region."

I would like to better understand how `Cosmo DB` relates to the `CAP` and `PACELC` theorems. What kinds of features does it offer in terms of availability, consistency, and network partition?

Azure Cosmos DB takes a uniquely flexible approach to the CAP and PACELC theorems. Unlike traditional databases that are permanently locked into a single behavior (like MongoDB being strictly CP or Cassandra being AP), **Cosmos DB is a multi-model, multi-region database whose classification shifts dynamically depending on the consistency level you choose.**

---

### 1. How Azure Cosmos DB Relates to the CAP Theorem

Under the CAP theorem, partition tolerance ($\text{P}$) is a mandatory reality for any distributed cloud database. 
Therefore, the choice always comes down to balancing Consistency ($\text{C}$) and Availability ($\text{A}$) during a network partition.

Cosmos DB allows you to slide across this spectrum using **five distinct consistency levels**:

## **Strong Consistency (The CP Side):**

* **Behavior:** If a network partition splits your replicas across regions or zones, the system forces writes to wait
until a global majority acknowledges them. If consensus cannot be reached due to a partition, the database refuses 
to complete the write to prevent data divergence.

* **Classification:** Strictly **CP**.

## **Eventual, Session, Consistent Prefix, and Bounded Staleness (Leaning toward AP with Tunable Guarantees):**

* **Behavior:** During a partition, these levels allow reads and writes to continue processing locally within 
available partitions/zones, prioritizing high availability ($\text{A}$). Once the network heals, data converges asynchronously.

* **Classification:** Leans heavily toward **AP**, while offering mathematically bounded limits on *how* stale the data can get (e.g., bounded by time or number of versions).

---

### 2. How Azure Cosmos DB Relates to the PACELC Theorem

The `PACELC` theorem extends CAP by asking: **If there is a Partition ($\text{P}$), how do you trade off Availability ($\text{A}$) versus Consistency ($\text{C}$); Else ($\text{E}$), when the system is running normally without partitions, how do you trade off Latency ($\text{L}$) versus Consistency ($\text{C}$)?**

Cosmos DB’s architecture maps cleanly to PACELC because it lets you explicitly dictate the Latency vs. Consistency trade-off during normal operations:

* **When using Strong Consistency:**
* **PACELC category: PC/EC.** If there's a partition ($\text{P}$), it chooses Consistency ($\text{C}$). Even during normal execution ($\text{E}$), it prioritizes Consistency ($\text{C}$) over Latency ($\text{L}$) because writes must synchronously cross-replicate before returning.


* **When using Eventual, Session, or Bounded Staleness Consistency:**
* **PACELC category: PA/EL (or PC/EL depending on exact tuning).** During normal operations ($\text{E}$), it prioritizes low **Latency** ($\text{L}$) by serving reads locally from the nearest replica without waiting for global locks, while still letting you bound the eventual consistency window.

---

### 3. Features Enabling Availability, Resiliency, and Consistency

The statement you shared touches on how Cosmos DB achieves high availability physically, which underpins these theorem trade-offs:

* **Availability Zone (AZ) Redundancy:** As your text notes, in AZ-enabled regions, Cosmos DB automatically spreads data replicas synchronously across 3 physically separate availability zones.
* *Resiliency:* If an entire datacenter facility (zone) goes dark, Cosmos DB detects it instantly, routes traffic to surviving zones, and reallocates throughput with **zero data loss ($\text{RPO} = 0$)** and minimal interruption.

* **Multi-Region Writes & Global Distribution:** You can map your database across any number of Azure regions. If configured for multi-region writes, every region can act as both active-read and active-write, drastically lowering latency for global users.

* **Session Consistency Default:** By default, Cosmos DB uses *Session Consistency*. This gives you a "monotonic reads" guarantee for the individual user session (you never read your own past writes backward), combining high performance ($\text{L}$) with intuitive consistency ($\text{C}$) without paying the heavy latency penalty of a strict global lock.

---