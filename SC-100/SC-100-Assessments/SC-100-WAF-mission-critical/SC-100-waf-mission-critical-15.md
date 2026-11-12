# Answer Q14-A01

## Selected Options

---

# Q15

# Mission Critical: Data Platform

[How are the relational data technologies configured and used?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=88ff03bb-acce-4054-9a79-3221712030c5&category=29cd0819-ea59-4039-bc04-f46ee79cc22d)  

# How are the relational data technologies configured and used?

For scenarios with a highly relational data model or dependencies on existing relational technologies, 
the use of Azure Cosmos DB in a multi-write configuration might not be directly applicable. 
In such cases, it's vital that used relational technologies are designed and configured to uphold 
the multi-region active-active aspirations of an application design.

##  Options 01
Database tiers that support availability zones are used.
There are various tiers and variants available for relational databases in Azure. 
Availability zone support is not always given.

##  Options 02
(Azure SQL) Business-critical tier is used when possible.
Azure SQL Database Premium or Business Critical service tier database replicas can be distributed across availability zones at no extra cost.

##  Options 03
(Azure SQL) vCore-based consumption model is used.
Azure SQL Database offers DTU-based and vCore purchasing models.

##  Options 04
Sharding was considered and implemented when appropriate.
Sharding can be applied to distribute data and processing across multiple identical structured databases, partitioning databases horizontally to navigate platform constraints. For example, sharding is often applied in multi-tenant SaaS platforms to isolate groups of tenants into distinct data platform constructs.

##  Options 05
Azure SQL Database was prioritized for relational capabilities.
Azure SQL Database provides a fully managed database engine that is always running on the latest stable version of the SQL Server database engine and underlying Operating System.

##  Options 06
(Azure SQL) Active geo-replication and auto failover groups were considered.
Azure SQL Database provides Auto Failover Groups, which replicates databases to a secondary server and allows for transparent failover if a failure.

##  Options 07
Application is configured to query local replicas to optimize performance.
With geo-replication, the database is spread across multiple regions and the application should have a 'local' replica in the same region.

##  Options 08
Database usage is evaluated to determine if sizing is correct.
For most efficiency, the right balance between capacity and utilization must be achieved.

##  Options 09
None of the above.

---