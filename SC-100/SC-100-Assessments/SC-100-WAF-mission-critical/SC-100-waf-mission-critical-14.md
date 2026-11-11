# Answer Q14-A01

## Selected Options

---


# Q14

# Mission Critical: Data Platform

[How is the global distributed data store configured and used?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=f79863b7-fcd3-4147-8981-0607d31437c2&category=29cd0819-ea59-4039-bc04-f46ee79cc22d)  

# How is the global distributed data store configured and used?

To fully accommodate the globally distributed active-active aspirations of an application design, a distributed multi-write data platform is used, where changes to separate writeable replicas are synchronized and merged between all replicas, with conflict resolution where required.


##  Options 01
Native APIs are preferred, such as SQL API for Cosmos DB.
Some databases, such as Cosmos DB, support different APIs so that developers can pick the most suitable one for their use case.

##  Options 02
Direct connection mode is used without additional network overhead.
Data stores such as Cosmos DB can offer multiple connection modes. Some access data directly with persistent TCP connection, while others may utilize HTTP proxy.

##  Options 03
Partitioning strategy is designed for optimal use of logical and physical partitions.
High-scale globally distributed platforms utilize partitioning to achieve better performance and scale. Picking the right partitioning strategy is in the hands of the developer.

##  Options 04
Indexing is configured properly.
Data indexing is crucial for performance, and applications often don't need to index every field present in data.

##  Options 05
Retry logic is implemented on the client side.
Native SDKs provide default error handling and automated retries for selected database errors, but the application should handle additional edge cases with custom code.

##  Options 06
Provisioned throughput is based on application traffic patterns.
Provisioned throughput can be configured as a static number, or auto-scale can be utilized to automatically adjust to demand.

##  Options 07
Data recovery procedures are tested regularly.
Backups are important, but recovery also should be periodically tested on non-production environments.

##  Options 08
None of the above.

---