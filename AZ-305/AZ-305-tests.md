# AZ-305 Practice Tests

Original, unofficial architecture-design questions for **Exam AZ-305: Designing Microsoft Azure Infrastructure Solutions**. These questions are not reproduced from the live exam.

> **Exam alignment:** The current Microsoft Learn study guide lists identity, governance, and monitoring (25–30%); data storage (20–25%); business continuity (15–20%); and infrastructure solutions (30–35%). The English exam was updated on April 17, 2026. Review the [exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/) and [study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-305) for current skills and future changes.
>
> Select the number of answers requested. Unless stated otherwise, choose the single best design. Each question includes its rationale, explanations for incorrect options, and Microsoft Learn references. This study aid does not guarantee exam coverage; validate service features, regional availability, and configuration prerequisites before implementation.
# AZ-305 Practice Tests

Original, unofficial architecture-design questions for **Exam AZ-305: Designing Microsoft Azure Infrastructure Solutions**. These questions are not reproduced from the live exam.

> **Exam alignment:** The Microsoft Learn exam page currently lists identity, governance, and monitoring (25–30%); data storage (20–25%); business continuity (15–20%); and infrastructure (30–35%). The English exam was updated on April 17, 2026. Review the current [exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/) and [study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-305) for future changes.
>
> Choose the number of answers requested. Unless otherwise stated, select the single best design. Each question includes its rationale, explanations for the distractors, and Microsoft Learn references. This study aid does not guarantee exam coverage; validate service features and regional availability before implementation.

## Domain 1: Design identity, governance, and monitoring solutions

### Question 1 - Design management group and subscription hierarchy

A global organization has separate platform and application teams, with three regulatory environments that require distinct Azure Policy assignments and consolidated billing boundaries. Workloads must be delegated to application teams without giving them control over the governance hierarchy. Which design is the best starting point?

A. Create management group branches for the governance boundaries, place subscriptions under the appropriate branch, and delegate workload administration at subscription or resource-group scope
B. Put every resource in one subscription and use tags as the only access-control and policy boundary
C. Create a management group for each virtual machine and assign application teams Owner at the tenant root
D. Use resource locks to replace role assignments and management group policy inheritance

**Correct: A.** Management groups organize subscriptions and allow policy and access assignments to inherit down the hierarchy. Delegating at a lower scope preserves the separation between platform governance and workload operations. The hierarchy should reflect policy needs without unnecessary depth. [R1][R2]

**Why the others are wrong:** B tags classify resources but do not provide equivalent subscription, policy-inheritance, or billing boundaries. [R1][R3] C creates excessive hierarchy and grants overly broad tenant-level privilege. [R1][R2] D locks help prevent deletion or modification of resources; they do not replace RBAC or policy. [R4]

**References:** [R1] [Organize resources with management groups](https://learn.microsoft.com/en-us/azure/governance/management-groups/overview); [R2] [Azure RBAC scope](https://learn.microsoft.com/en-us/azure/role-based-access-control/scope-overview); [R3] [Use tags to organize Azure resources](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources); [R4] [Lock resources to protect infrastructure](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).

### Question 2 - Enforce a policy while enabling remediation

New storage accounts must not allow public blob access. Existing accounts must be identified and brought into compliance. Which Azure Policy strategy best meets both requirements?

A. Assign a built-in or custom policy with a `deny` effect for new noncompliant accounts and an audit/remediation approach for existing resources
B. Assign `audit` only and assume future deployments will be blocked
C. Use an Azure RBAC Reader assignment to change the storage configuration automatically
D. Apply a resource lock to every subscription and treat it as enforcement of the public-access property

**Correct: A.** `deny` blocks noncompliant create or update requests. Audit identifies existing noncompliant resources; remediation tasks or an appropriate `modify`/`deployIfNotExists` policy can address supported existing-resource configurations. [R1][R2]

**Why the others are wrong:** B audit reports noncompliance but does not block deployment. [R1] C Reader is read-only and RBAC controls permissions rather than enforcing a property value. [R3] D locks prevent certain write or delete operations; they do not evaluate the public-access setting or bring resources into compliance. [R4]

**References:** [R1] [Azure Policy effect basics](https://learn.microsoft.com/en-us/azure/governance/policy/concepts/effect-basics); [R2] [Remediate noncompliant resources](https://learn.microsoft.com/en-us/azure/governance/policy/how-to/remediate-resources); [R3] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R4] [Resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).

### Question 3 - Grant read-only access to a resource group

A support team must view Azure resources and their configuration in one resource group but must not create, update, or delete resources. The team must not see unrelated resource groups. Which role assignment is the least-privileged design?

A. Assign the built-in Reader role at the required resource-group scope
B. Assign Owner at the subscription scope
C. Assign Contributor at the management-group scope
D. Assign User Access Administrator at the tenant root

**Correct: A.** Reader provides read-only access at the assigned scope, and a resource-group scope limits visibility to the intended group and its resources. [R1]

**Why the others are wrong:** B Owner grants full management and access delegation at a broader scope. [R1][R2] C Contributor permits resource changes and applies to an unnecessarily broad scope. [R1] D User Access Administrator can manage access assignments and is not a read-only support role. [R2]

**References:** [R1] [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles); [R2] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview).

### Question 4 - Design privileged access for Azure administrators

A team performs occasional subscription-level maintenance. Administrators must not have permanent standing privilege, and elevation must be time-bound with approval and MFA. Which solution should be designed?

A. Eligible Azure role assignments in Microsoft Entra Privileged Identity Management, with activation controls
B. Permanent Owner assignments protected by a longer password
C. Azure Policy assignments that grant the role only when a resource is compliant
D. A resource lock on the subscription

**Correct: A.** PIM supports eligible Azure resource role assignments with just-in-time activation and configurable controls such as approval, MFA, and activation duration. [R1]

**Why the others are wrong:** B retains standing privilege and does not provide controlled activation. [R1] C Azure Policy evaluates resource configuration and does not implement privileged role activation. [R2] D locks protect resources against some changes or deletion; they do not manage identity privilege. [R3]

**References:** [R1] [Assign eligible Azure resource roles in PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-assign-roles); [R2] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R3] [Resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).

### Question 5 - Store and rotate application secrets

Several applications need database passwords and TLS certificates. Credentials must not be committed to source code; access should be controlled centrally with managed identities, and credential lifecycles must support rotation. Which design is best?

A. Store secrets, keys, and certificates in Azure Key Vault and grant each workload identity only the required data-plane access
B. Store passwords in deployment templates and grant the applications subscription Owner
C. Put secrets in Azure resource tags so all deployments can read them
D. Store a shared credential in a public blob with an obscure URL

**Correct: A.** Key Vault centralizes secrets, keys, and certificates. Managed identities avoid embedding credentials, and narrow access grants follow least privilege. Configure supported key-rotation policies and suitable certificate-renewal or secret-rotation workflows; storage in Key Vault alone does not automatically rotate every credential. [R1][R2]

**Why the others are wrong:** B exposes secrets in deployment artifacts and grants excessive permissions. [R1] C tags are not a secrets store and may be broadly visible. [R3] D an obscure URL is not access control and exposes the secret to anyone who obtains it. [R1][R4]

**References:** [R1] [Azure Key Vault overview](https://learn.microsoft.com/en-us/azure/key-vault/general/overview); [R2] [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview); [R3] [Azure resource tags](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources); [R4] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault).

### Question 6 - Choose Log Analytics workspace boundaries

A company operates in three Azure geographies. Logs must remain in the geography where they are collected to meet data-residency requirements. Within each geography, the company wants to minimize workspace count and administrative overhead. How many Log Analytics workspaces should the architect recommend at minimum?

A. One workspace per geography: three
B. One workspace for the entire tenant
C. One workspace per subscription, regardless of geography
D. One workspace per resource

**Correct: A.** A Log Analytics workspace defines a data-storage region and administrative boundary. To meet geographic residency while minimizing workspace count, use at least one workspace in each required geography. [R1][R2]

**Why the others are wrong:** B a single workspace cannot satisfy storage residency across three geographies. [R1] C may create multiple workspaces in one geography while still failing to ensure coverage in each required geography; subscription count does not define data residency. [R1] D one workspace per resource adds unnecessary cost and administration without being required by the stated constraints. [R1]

**References:** [R1] [Design a Log Analytics workspace architecture](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/workspace-design); [R2] [Azure geographies](https://azure.microsoft.com/en-us/explore/global-infrastructure/geographies/).

### Question 7 - Route platform and application logs to multiple destinations

A workload's resource logs must be retained in Log Analytics for querying and also sent to an Event Hub for a third-party SIEM. The design must collect the selected resource categories without deploying an agent to each resource. Which feature should be configured?

A. Diagnostic settings on the supported Azure resources, routing selected categories to Log Analytics and Event Hubs
B. Azure Policy assignments with an `audit` effect as the log transport
C. Resource locks on each resource and an Azure Monitor alert
D. Network security groups that export application logs to both destinations

**Correct: A.** Azure Monitor diagnostic settings route supported platform resource logs and metrics to configured destinations, including Log Analytics workspaces, Event Hubs, and Storage. [R1][R2]

**Why the others are wrong:** B Azure Policy evaluates resource configuration and is not the telemetry-routing mechanism. [R3] C a lock protects management operations and an alert evaluates signals; neither routes resource logs. [R1] D NSGs control network traffic and do not configure Azure diagnostic log destinations. [R4]

**References:** [R1] [Diagnostic settings in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/diagnostic-settings); [R2] [Azure Monitor Logs overview](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/data-platform-logs); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 8 - Monitor application performance and dependencies

A development team needs request rates, response times, failures, and dependency telemetry for a web application, plus distributed tracing across service calls. Which monitoring capability should be recommended?

A. Azure Application Insights, integrated with the application and its supported telemetry instrumentation
B. Azure Storage insights as the primary application request-tracing service
C. Azure Policy compliance evaluation as distributed tracing
D. Azure Site Recovery test failover reports

**Correct: A.** Application Insights provides application performance monitoring, distributed request telemetry, failures, and dependency insights for supported instrumented applications. [R1]

**Why the others are wrong:** B Storage insights monitors storage-account health and usage, not application request traces. [R2] C Policy evaluates Azure resource compliance; it does not collect application runtime telemetry. [R3] D Site Recovery test failover validates disaster-recovery plans, not application performance. [R4]

**References:** [R1] [Application Insights overview](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview); [R2] [Azure Monitor Storage insights](https://learn.microsoft.com/en-us/azure/storage/common/storage-insights-overview); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview).


## Domain 2: Design data storage solutions

### Question 9 - Recommend a transactional relational database tier

An order-processing database requires relational constraints and stored procedures, predictable low-latency transactions, and scaling based on its own workload. It has variable compute demand and must avoid sharing a pool with unrelated databases. Which Azure SQL Database design is the best fit?

A. A single database in the vCore-based provisioned or serverless compute model selected to match its usage pattern
B. An elastic pool shared with dozens of unrelated databases, regardless of resource contention
C. Azure Cosmos DB with eventual consistency as a replacement for relational transactions
D. Azure Blob Storage with hierarchical namespace as the transactional database

**Correct: A.** Azure SQL Database supports relational workloads and vCore-based compute choices; serverless can suit intermittent use, while provisioned compute suits predictable sustained demand. A single database avoids the explicitly unwanted shared-pool tenancy. [R1][R2]

**Why the others are wrong:** B elastic pools can be cost-effective for compatible databases with variable usage, but the scenario explicitly requires dedicated per-database scaling and no shared pool. [R2] C Cosmos DB is a globally distributed NoSQL service and does not provide the requested relational database design. [R3] D Blob Storage is object storage, not a transactional relational database. [R4]

**References:** [R1] [Azure SQL Database service tiers and compute](https://learn.microsoft.com/en-us/azure/azure-sql/database/service-tiers-sql-database-vcore); [R2] [Azure SQL elastic pools](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-pool-overview); [R3] [Azure Cosmos DB consistency levels](https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels); [R4] [Azure Blob Storage introduction](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction).

### Question 10 - Scale independent databases with variable demand

A SaaS provider runs many small customer databases. Their peaks occur at different times, and the provider wants a shared compute budget with per-database controls to reduce cost. Which Azure SQL feature is best suited?

A. An elastic pool containing the databases, sized for aggregate demand with appropriate per-database limits
B. A separate fixed-size dedicated instance for every database
C. A single Azure Storage account per customer with no database service
D. An Azure SQL failover group, because it shares compute among databases

**Correct: A.** Elastic pools share resources among multiple databases with variable usage, allowing aggregate capacity to be used more efficiently while configuring per-database limits. [R1]

**Why the others are wrong:** B fixed dedicated compute for every small, nonconcurrent workload can waste capacity and fails the shared-budget requirement. [R1] C object storage does not provide relational database functionality. [R2] D failover groups provide high availability and disaster recovery for SQL instances/databases; they are not a shared-compute scaling feature. [R3]

**References:** [R1] [Azure SQL elastic pools](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-pool-overview); [R2] [Azure Storage data services overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-introduction); [R3] [Auto-failover groups for Azure SQL Managed Instance](https://learn.microsoft.com/en-us/azure/azure-sql/managed-instance/auto-failover-group-sql-mi).

### Question 11 - Choose a Cosmos DB consistency level

A globally distributed application requires read-after-write consistency for an individual user session. It accepts that reads might not immediately reflect writes from other sessions and wants better availability and lower latency than global strong consistency. Which consistency level should be evaluated?

A. Session
B. Strong
C. Eventual, with no session token support
D. Bounded staleness, configured as synchronous global consistency

**Correct: A.** Session consistency provides read-your-writes and write ordering within a client session while avoiding the stronger global guarantees and associated trade-offs of strong consistency. [R1]

**Why the others are wrong:** B strong provides the strongest global consistency and may incur latency/availability trade-offs that are unnecessary for the stated requirement. [R1] C eventual alone does not provide the requested session read-your-writes guarantee. [R1] D bounded staleness bounds lag but is not synchronous strong consistency and is not the most direct fit for the per-session requirement. [R1]

**References:** [R1] [Consistency levels in Azure Cosmos DB](https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels).

### Question 12 - Design a partition strategy for Cosmos DB

A multitenant Cosmos DB workload stores records for millions of customers. Nearly all reads and writes include a customer identifier, and the design must distribute load while keeping customer-scoped operations efficient. Which partition-key strategy is the best starting point?

A. Evaluate a high-cardinality customer identifier as the partition key, validating that no individual tenant becomes a hot partition and considering workload distribution
B. Use one constant partition-key value for every item
C. Use a timestamp with minute precision when most operations query one customer's records
D. Use a random GUID as the partition key even though application queries always require customer-scoped records

**Correct: A.** A partition key should align with common query patterns and distribute data and throughput. A customer key can support customer-scoped operations, but the architect must assess cardinality, tenant skew, and hot-partition risks. [R1][R2]

**Why the others are wrong:** B places all items in one logical partition, creating a scaling bottleneck. [R1] C may distribute by time but makes customer-scoped queries cross partitions and may still create hot write ranges. [R1][R2] D random keys can distribute writes, but conflict with the dominant customer-scoped query pattern and require cross-partition queries. [R1][R2]

**References:** [R1] [Partitioning in Azure Cosmos DB](https://learn.microsoft.com/en-us/azure/cosmos-db/partitioning-overview); [R2] [Partitioning and horizontal scaling](https://learn.microsoft.com/en-us/azure/architecture/best-practices/data-partitioning).

### Question 13 - Select storage redundancy for regional disaster recovery

An application stores business-critical blobs. The data must survive a regional outage and be readable from the secondary region during a primary-region outage. The application accepts asynchronous replication. Which redundancy option should be selected?

A. Read-access geo-redundant storage (RA-GRS), subject to supported account and service requirements
B. Locally redundant storage (LRS)
C. Zone-redundant storage (ZRS) in the primary region only
D. Premium local disk attached to one virtual machine

**Correct: A.** RA-GRS asynchronously replicates data to a paired secondary region and permits read access to the secondary endpoint, meeting regional resilience and secondary-read requirements. [R1]

**Why the others are wrong:** B LRS replicates within one datacenter in the primary region and does not provide regional recovery. [R1] C ZRS spans availability zones in one region and does not by itself provide a secondary-region read endpoint. [R1] D a VM disk is not a regional object-storage redundancy strategy. [R1][R2]

**References:** [R1] [Azure Storage redundancy](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy); [R2] [Azure managed disks](https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview).

### Question 14 - Move infrequently accessed blobs to a lower-cost tier

A data archive contains blobs that are rarely read but must remain online for occasional retrieval. The organization wants to automate tiering based on object age and lifecycle rules. Which solution should be designed?

A. Azure Blob Storage lifecycle management policies to move eligible blobs to an appropriate access tier
B. Azure SQL elastic pools with a time-based query policy
C. Cosmos DB session consistency
D. Azure Site Recovery to move blobs between storage tiers

**Correct: A.** Blob lifecycle management applies rules to transition eligible objects between access tiers or delete them based on age and other supported conditions. Choose a tier whose retrieval latency and rehydration behavior meets the archive requirement. [R1][R2]

**Why the others are wrong:** B elastic pools manage SQL compute capacity, not blob access tiers. [R3] C consistency is a Cosmos DB data consistency option, not a storage tiering policy. [R4] D Site Recovery replicates workloads for disaster recovery and does not manage Blob access tiers. [R5]

**References:** [R1] [Azure Blob Storage lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview); [R2] [Blob access tiers](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview); [R3] [Azure SQL elastic pools](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-pool-overview); [R4] [Cosmos DB consistency levels](https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels); [R5] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview).

### Question 15 - Build a cloud analytics data store

A company needs to combine data from SQL systems, SaaS sources, and files, transform it in scheduled pipelines, and query large analytical datasets separately from transactional databases. Which architecture is the best fit?

A. Use Azure Data Factory for data integration/orchestration and an analytical store such as Azure Data Lake Storage with an appropriate analytics engine
B. Run all analytical scans directly against the production OLTP database and replace its indexes with blob lifecycle policies
C. Use Azure Service Bus queues as the only long-term analytical data store
D. Use Azure Key Vault to store and query analytical records

**Correct: A.** Data Factory supports data movement and transformation orchestration; a data lake and analytics service are designed for analytical storage and processing, separating large analytical workloads from OLTP transactions. [R1][R2][R3]

**Why the others are wrong:** B couples analytical scans to transactional systems and misuses lifecycle policies, increasing contention and failing to provide an analytical store. [R2][R3] C Service Bus is messaging, not an analytical data lake or query engine. [R4] D Key Vault stores secrets, keys, and certificates, not business analytics data. [R5]

**References:** [R1] [Azure Data Factory introduction](https://learn.microsoft.com/en-us/azure/data-factory/introduction); [R2] [Analytical data stores](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/analytical-data-stores); [R3] [Data store decision overview](https://learn.microsoft.com/en-us/azure/architecture/data-guide/technology-choices/data-store-overview); [R4] [Azure Service Bus overview](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview); [R5] [Azure Key Vault overview](https://learn.microsoft.com/en-us/azure/key-vault/general/overview).

## Domain 3: Design business continuity solutions

### Question 16 - Meet a regional VM disaster-recovery objective

A business workload runs on Azure VMs in one region. The recovery point objective is 15 minutes, and recovery must start in a secondary region if the primary region is unavailable. The design must replicate running workloads and orchestrate failover. Which service should be used?

A. Azure Site Recovery, configured for replication and a tested recovery plan
B. Azure Backup alone, with no replication or failover plan
C. A storage lifecycle policy on the VM's operating-system disk
D. Azure Advisor cost recommendations

**Correct: A.** Site Recovery replicates supported workloads to a secondary location and orchestrates failover and failback, allowing a designed and tested recovery plan to meet recovery objectives when supported by configuration and workload conditions. [R1]

**Why the others are wrong:** B Azure Backup protects recovery points and supports restore; backup alone does not continuously replicate and orchestrate VM failover to meet the stated RPO. [R1][R2] C lifecycle policies manage eligible blob data, not VM replication. [R3] D Advisor provides recommendations and does not provide disaster recovery. [R4]

**References:** [R1] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview); [R2] [Azure Backup overview](https://learn.microsoft.com/en-us/azure/backup/backup-overview); [R3] [Blob lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview); [R4] [Azure Advisor overview](https://learn.microsoft.com/en-us/azure/advisor/advisor-overview).

### Question 17 - Protect VM files from deletion and ransomware

An application requires recovery of files and folders to a selected point in time. The design needs scheduled protected copies and point-in-time restore; it does not require failover of a running server to another region. Which service is the best fit?

A. Azure Backup for the supported workload, with a Recovery Services vault and an appropriate backup policy
B. Azure Site Recovery only
C. Azure Traffic Manager
D. A zone-redundant load balancer

**Correct: A.** Azure Backup protects supported workloads and provides recovery points for restore; configure the appropriate backup solution, retention, and vault security for the workload. [R1]

**Why the others are wrong:** B Site Recovery replicates workloads for disaster recovery and orchestrated failover; it is not the file/folder backup service requested. [R1][R2] C Traffic Manager routes DNS responses between endpoints and does not back up files. [R3] D a load balancer distributes network traffic and does not create recovery points. [R4]

**References:** [R1] [Azure Backup overview](https://learn.microsoft.com/en-us/azure/backup/backup-overview); [R2] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).

### Question 18 - Provide SQL Database failover to another region

A mission-critical Azure SQL Database must have a readable secondary in another region and allow planned or unplanned failover. Application connectivity should use a stable listener endpoint where available. Which design is appropriate?

A. Configure an auto-failover group with a secondary database in the target region and use its read-write listener for application connectivity
B. Configure an elastic pool and assume pool membership replicates data to another region
C. Use a local availability zone and assume it provides regional disaster recovery
D. Use Azure Backup without a secondary or a failover process

**Correct: A.** Azure SQL failover groups provide geo-replication and group-level failover, with listener endpoints to support connectivity across failover. [R1]

**Why the others are wrong:** B elastic pools share compute among databases and do not replicate the databases to another region. [R2] C availability zones protect against zonal failures within a region, not a full regional outage. [R3] D backups support recovery but do not provide the specified online secondary and failover listener. [R1][R4]

**References:** [R1] [Auto-failover groups for Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/auto-failover-group-sql-db); [R2] [Azure SQL elastic pools](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-pool-overview); [R3] [Availability zones overview](https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview); [R4] [Azure SQL automated backups](https://learn.microsoft.com/en-us/azure/azure-sql/database/automated-backups-overview).

### Question 19 - Choose storage redundancy for zonal resilience

An application stores frequently accessed blobs and must remain available if one availability zone in its region fails. Regional failover is not required. Which redundancy option is the closest fit?

A. Zone-redundant storage (ZRS), where supported for the storage account and region
B. Locally redundant storage (LRS) in one datacenter
C. Geo-redundant storage (GRS) without read access in the secondary, because only zonal availability is needed
D. Azure Site Recovery configured for virtual machines

**Correct: A.** ZRS synchronously replicates data across availability zones in a region, addressing zonal failure without requiring a secondary region. Confirm service, region, and account-type support. [R1]

**Why the others are wrong:** B LRS keeps copies within a single datacenter and does not provide zone-level resilience. [R1] C GRS addresses regional durability asynchronously but does not provide the direct same-region zonal design requested; it also adds unrequested cross-region replication. [R1] D Site Recovery protects supported workloads for disaster recovery rather than configuring Blob Storage redundancy. [R2]

**References:** [R1] [Azure Storage redundancy](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy); [R2] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview).

### Question 20 - Distinguish availability zones from regional DR

A customer-facing service must tolerate loss of one datacenter in its Azure region with minimal interruption. It does not require recovery from a full regional outage in this requirement. Which design objective should the architect prioritize?

A. Deploy across availability zones in the region, using a supported zonal or zone-redundant architecture for each service
B. Deploy a single VM in one zone and create a resource lock
C. Deploy two VMs in the same fault domain and use a single-instance database
D. Configure a traffic manager DNS profile without deploying a healthy secondary endpoint

**Correct: A.** Availability zones are physically separate locations within an Azure region; distributing supported workload components across zones can tolerate a zonal/datacenter failure. Regional disaster recovery is a separate design requirement. [R1][R2]

**Why the others are wrong:** B a resource lock prevents some management operations but does not add redundancy. [R3] C same-domain placement and a single database retain single points of failure. [R1] D DNS routing cannot provide availability if there is no healthy alternate endpoint. [R4]

**References:** [R1] [Availability zones overview](https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview); [R2] [Cross-region replication in Azure](https://learn.microsoft.com/en-us/azure/reliability/cross-region-replication-azure); [R3] [Resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources); [R4] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

## Domain 4: Design infrastructure solutions

### Question 21 - Select compute for an event-driven workload

A service runs short, stateless code in response to messages arriving in a queue. Demand is intermittent, and the team wants managed scaling without maintaining servers. Which compute option is the best fit?

A. Azure Functions triggered by the queue, using a hosting plan that matches scaling and execution requirements
B. A permanently running VM sized for peak demand
C. Azure Kubernetes Service for a single function with no container orchestration requirement
D. Azure Storage lifecycle management

**Correct: A.** Azure Functions supports event-triggered serverless execution and can scale according to the selected hosting plan and workload requirements. [R1]

**Why the others are wrong:** B provisioning for peak demand adds ongoing operations and can waste capacity for intermittent work. [R2] C AKS is a managed Kubernetes platform; it adds orchestration overhead when the requirement is a small event-triggered function and does not need Kubernetes. [R2][R3] D lifecycle management transitions or deletes blobs and is not a compute service. [R4]

**References:** [R1] [Azure Functions overview](https://learn.microsoft.com/en-us/azure/azure-functions/functions-overview); [R2] [Azure compute decision tree](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree); [R3] [Azure Kubernetes Service overview](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes); [R4] [Blob lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview).

### Question 22 - Choose managed compute for an existing web application

A company must migrate a conventional ASP.NET web application to Azure quickly. It does not require operating-system-level access, and the team wants Microsoft to manage the web-hosting platform. Which compute service is the best fit?

A. Azure App Service
B. A set of self-managed virtual machines
C. Azure Batch
D. Azure Event Hubs

**Correct: A.** App Service is a managed platform for hosting web applications and APIs; it removes the need to manage the underlying operating system in the way required for a VM-based design. [R1]

**Why the others are wrong:** B VMs provide OS-level control but create additional patching and platform-management responsibilities that the requirement avoids. [R2] C Batch runs parallel and high-performance batch jobs, not a continuously hosted web app. [R3] D Event Hubs ingests event streams and is not a web application host. [R4]

**References:** [R1] [Azure App Service overview](https://learn.microsoft.com/en-us/azure/app-service/overview); [R2] [Azure compute decision tree](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree); [R3] [Azure Batch overview](https://learn.microsoft.com/en-us/azure/batch/batch-technical-overview); [R4] [Azure Event Hubs overview](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about).

### Question 23 - Select container orchestration for microservices

A product consists of multiple containerized microservices that require Kubernetes APIs, independent deployment, service discovery, and team-controlled deployment manifests. Which service is the most appropriate managed platform?

A. Azure Kubernetes Service (AKS)
B. Azure Functions for all long-running services, without containers
C. Azure SQL elastic pools
D. Azure Traffic Manager

**Correct: A.** AKS provides managed Kubernetes orchestration for containerized workloads and supports the Kubernetes deployment model required by the scenario. [R1][R2]

**Why the others are wrong:** B Functions is serverless event-driven compute; it does not provide Kubernetes APIs or orchestration for the described containers. [R2][R3] C elastic pools provide shared Azure SQL database compute. [R4] D Traffic Manager routes DNS responses between endpoints; it does not orchestrate containers. [R5]

**References:** [R1] [Azure Kubernetes Service overview](https://learn.microsoft.com/en-us/azure/aks/intro-kubernetes); [R2] [Azure compute decision tree](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree); [R3] [Azure Functions overview](https://learn.microsoft.com/en-us/azure/azure-functions/functions-overview); [R4] [Azure SQL elastic pools](https://learn.microsoft.com/en-us/azure/azure-sql/database/elastic-pool-overview); [R5] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 24 - Design reliable asynchronous command messaging

A set of business services must send durable commands to individual consumers. Consumers may be temporarily unavailable, and the design needs competing consumers, message settlement, and dead-letter handling. Which service is the best fit?

A. Azure Service Bus queues
B. Azure Event Hubs partitions as a command queue
C. Azure Monitor metrics
D. Azure Front Door

**Correct: A.** Service Bus queues provide brokered enterprise messaging for commands, including durable message delivery, competing consumers, settlement, and dead-letter capabilities. [R1]

**Why the others are wrong:** B Event Hubs is optimized for high-throughput event streaming and retention/replay, rather than per-message command settlement and dead-letter semantics as described. [R2] C metrics are telemetry, not command delivery. [R3] D Front Door is a global application entry point, not a messaging broker. [R4]

**References:** [R1] [Azure Service Bus messaging overview](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview); [R2] [Azure Event Hubs overview](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about); [R3] [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/overview); [R4] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview).

### Question 25 - Ingest a high-volume event stream

Millions of devices emit telemetry continuously. The application must ingest a high-throughput event stream for downstream consumers and retain events for bounded replay. Which service should be selected?

A. Azure Event Hubs
B. Azure Service Bus queue for every telemetry event
C. Azure API Management as a durable streaming log
D. Azure Key Vault

**Correct: A.** Event Hubs is a scalable event-streaming service designed for high-throughput telemetry ingestion, partitioned streams, and bounded retention for replay. [R1]

**Why the others are wrong:** B Service Bus is brokered enterprise messaging and is less appropriate for very high-volume telemetry streams with partitioned replay. [R1][R2] C API Management publishes and governs APIs; it is not a durable event-streaming platform. [R3] D Key Vault stores secrets, keys, and certificates. [R4]

**References:** [R1] [Azure Event Hubs overview](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about); [R2] [Azure Service Bus overview](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview); [R3] [Azure API Management key concepts](https://learn.microsoft.com/en-us/azure/api-management/api-management-key-concepts); [R4] [Azure Key Vault overview](https://learn.microsoft.com/en-us/azure/key-vault/general/overview).

### Question 26 - Select a global web entry point and regional routing

A public web application is deployed in multiple Azure regions. Users worldwide need a global entry point, edge acceleration, and health-based routing to the closest healthy regional origin. Which service should be used?

A. Azure Front Door
B. Azure Load Balancer in one region
C. Azure Application Gateway deployed only in one region
D. Azure ExpressRoute

**Correct: A.** Front Door is a global Layer 7 entry point that uses Microsoft's edge network and supports health-based routing to origins in multiple regions. [R1]

**Why the others are wrong:** B Load Balancer operates at Layer 4 and is regional, so it does not provide the requested global HTTP(S) edge routing. [R2] C Application Gateway is a regional Layer 7 load balancer/WAF; a single regional gateway does not supply the global entry point required. [R3] D ExpressRoute provides private connectivity from on-premises networks to Microsoft cloud; it is not a public web global load balancer. [R4]

**References:** [R1] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R2] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R3] [Azure Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview); [R4] [Azure ExpressRoute overview](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction).

### Question 27 - Connect an on-premises datacenter privately to Azure

A company needs predictable private connectivity between its on-premises datacenter and Azure, with a service-provider connection and no dependency on the public internet for the customer-to-Microsoft path. Which service should be recommended?

A. Azure ExpressRoute, with a suitable circuit and connectivity model
B. Azure Traffic Manager
C. Azure Front Door
D. A public Azure Load Balancer

**Correct: A.** ExpressRoute extends on-premises networks into Microsoft cloud over a connectivity provider's private connection; the circuit and peering design must meet the required bandwidth and resilience. [R1]

**Why the others are wrong:** B Traffic Manager performs DNS-based endpoint routing and does not provide private network connectivity. [R2] C Front Door is a global public application entry point, not private datacenter connectivity. [R3] D a public Load Balancer distributes inbound network traffic; it does not establish a private circuit from the datacenter. [R4]

**References:** [R1] [Azure ExpressRoute overview](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction); [R2] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R3] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R4] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).

### Question 28 - Route requests based on URL path and protect against web attacks

A regional web application has `/images` and `/api` backends. Requests must be routed by URL path, TLS should terminate at the entry tier, and common web attacks should be filtered. Which service is the best fit?

A. Azure Application Gateway with path-based routing and its Web Application Firewall (WAF) capability
B. Azure Load Balancer using TCP rules only
C. Azure Traffic Manager using DNS priority routing
D. Azure ExpressRoute with private peering

**Correct: A.** Application Gateway is a regional Layer 7 application delivery service that supports path-based routing and WAF protection. Verify the selected SKU and WAF policy features against requirements. [R1][R2]

**Why the others are wrong:** B Load Balancer operates at Layer 4 and cannot route by URL path or inspect HTTP attacks. [R3] C Traffic Manager returns DNS responses and cannot inspect each HTTP request or route on URL path. [R4] D ExpressRoute connects networks and does not provide application-layer path routing or WAF. [R5]

**References:** [R1] [Azure Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview); [R2] [Azure WAF on Application Gateway](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview); [R3] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R4] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [Azure ExpressRoute overview](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction).

### Question 29 - Migrate an estate and choose PaaS where practical

A company must inventory on-premises servers, assess dependencies and Azure readiness, and plan a phased migration. The target should use Azure PaaS for supported workloads but preserve IaaS for workloads requiring operating-system control. Which approach is best?

A. Use Azure Migrate discovery and assessment, then select a workload-appropriate migration path to App Service, Azure SQL, or Azure VMs
B. Use Azure Site Recovery discovery as the only assessment tool and migrate every server unchanged to VMs
C. Use Azure Front Door to assess application dependencies and move databases to a CDN
D. Rehost every workload to VMs without assessing compatibility, dependencies, or modernization options

**Correct: A.** Azure Migrate supports discovery and assessment of on-premises workloads and helps plan migration; the target can be selected per workload, balancing PaaS modernization with IaaS requirements. [R1][R2]

**Why the others are wrong:** B Site Recovery supports replication and disaster recovery; it does not replace full inventory, dependency, and migration assessment. [R1][R3] C Front Door routes application traffic and a CDN is not a database target. [R4] D skips assessment and ignores the requirement to use PaaS where appropriate. [R1][R2]

**References:** [R1] [Azure Migrate overview](https://learn.microsoft.com/en-us/azure/migrate/migrate-services-overview); [R2] [Azure Cloud Adoption Framework migration planning](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/migrate/plan-migration); [R3] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview); [R4] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview).

### Question 30 - Govern and secure API integration

Several internal services expose APIs to partners. The design requires a centralized API gateway for publishing APIs, enforcing authentication, throttling callers, and applying policies, while back-end services remain independently hosted. Which service is the best fit?

A. Azure API Management
B. Azure Load Balancer
C. Azure Traffic Manager
D. Azure Site Recovery

**Correct: A.** API Management provides an API gateway and management plane for publishing, securing, applying policies to, and observing APIs independently of their back ends. [R1]

**Why the others are wrong:** B Load Balancer distributes network flows at Layer 4 and does not provide API authentication, policy, or developer-facing API management. [R2] C Traffic Manager routes DNS responses among endpoints and does not mediate each API request. [R3] D Site Recovery replicates workloads for disaster recovery, not API integration. [R4]

**References:** [R1] [Azure API Management key concepts](https://learn.microsoft.com/en-us/azure/api-management/api-management-key-concepts); [R2] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview).

### Question 31 - Reduce repeated reads from a data store

An application repeatedly reads relatively stable reference data from a database. Database latency and read load are increasing. The application can tolerate a short period of stale data and needs a cache-aside pattern. Which design is most appropriate?

A. Add Azure Cache for Redis as a distributed cache; the application reads the cache first, loads misses from the data store, and applies an appropriate expiration/invalidation strategy
B. Use Azure Site Recovery as an in-memory read cache
C. Replace the cache with an Azure Service Bus queue for every read request
D. Use Azure Policy to cache database query results

**Correct: A.** A distributed cache and cache-aside pattern reduce repeated data-store reads and can improve latency; expiration and invalidation must account for acceptable staleness. [R1][R2]

**Why the others are wrong:** B Site Recovery replicates workloads for disaster recovery, not low-latency data caching. [R3] C Service Bus queues deliver messages asynchronously and are not a key-value cache for repeated reads. [R4] D Azure Policy does not cache application data or query results. [R5]

**References:** [R1] [Cache-aside pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside); [R2] [Azure Cache for Redis overview](https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/cache-overview); [R3] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview); [R4] [Azure Service Bus overview](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview); [R5] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 32 - Centralize runtime configuration and feature flags

A team runs the same application in several environments. It needs a centrally managed configuration store and feature flags, and it wants to avoid embedding environment-specific settings in each deployment package. Which service should be recommended?

A. Azure App Configuration, integrated with the application and secured access identity
B. Azure Site Recovery recovery plans
C. Azure Traffic Manager routing methods
D. Azure Storage lifecycle management rules

**Correct: A.** Azure App Configuration centralizes application settings and feature flags so configuration can be managed separately from application binaries and deployment packages. [R1]

**Why the others are wrong:** B Site Recovery recovery plans coordinate disaster recovery and do not manage routine application settings. [R2] C Traffic Manager routes client DNS queries and does not store application configuration. [R3] D lifecycle management transitions or deletes blob data; it is not a configuration service. [R4]

**References:** [R1] [Azure App Configuration overview](https://learn.microsoft.com/en-us/azure/azure-app-configuration/overview); [R2] [Azure Site Recovery overview](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Blob lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview).

## Further study

Use the [AZ-305 exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/) and [official study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-305) for current exam objectives. Additional Microsoft Learn preparation resources:

- [AZ-305 design prerequisites](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-architect-design-prerequisites/)
- [Design identity, governance, and monitoring solutions](https://learn.microsoft.com/en-us/training/paths/design-identity-governance-monitor-solutions/)
- [Design business continuity solutions](https://learn.microsoft.com/en-us/training/paths/design-business-continuity-solutions/)
- [Design data storage solutions](https://learn.microsoft.com/en-us/training/paths/design-data-storage-solutions/)
- [Design infrastructure solutions](https://learn.microsoft.com/en-us/training/paths/design-infranstructure-solutions/)

Supplementary video material: [AZ-305 Microsoft Learn playlist](https://www.youtube.com/playlist?list=PLahhVEj9XNTejs0fgXT6HXaj_a_qsUoKa) and episode links in the repository specification. Microsoft Learn is the authority for exam scope and product behavior.