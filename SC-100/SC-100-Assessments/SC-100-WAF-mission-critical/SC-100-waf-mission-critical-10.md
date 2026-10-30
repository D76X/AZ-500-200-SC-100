# Answer Q10-A01

## Selected Options

---

# Q10

## Mission Critical: Application Design

[How is the volume of data and growth factored into the application design?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=b00a3eee-44e4-4179-bcfd-d3aba71ed6a0&category=29cd0819-ea59-4039-bc04-f46ee79cc22d)   

# How is the volume of data and growth factored into the application design?

Data volume may fluctuate due to changing business circumstances or housekeeping procedures. 
Existing and expected future data volumes based on forecasted data growth rates need to be 
aligned with business objectives and plans.

##  Options 01
Data volumes are not expected to exceed data platform capabilities.

Large business-critical and mission-critical applications typically generate 
and store high volumes (GB and TB) on a daily basis. There can be significant 
cost and reliability implications associated with data expansion.

##  Options 02
Data is classified based on usage and criticality ('warm', 'cold').

Not all data needs to be accessible with the lowest latency all the time. 
Classification into 'warm' or 'cold' tiers helps decide which data store should be used. 
Cold data is typically offloaded from the main transactional system into cheaper storage.

##  Options 03
Proper data volume monitoring is in place.

Data volume may fluctuate due to changing business circumstances or 
housekeeping procedures, and it can have a profound impact on data platform 
query performance.

##  Options 04
Data volume is validated against a capacity model.

There can be a profound impact associated with reaching data platform volume limits.

##  Options 05
Housekeeping procedures are in place. For example, Time to Live or cold storage.

Features such as Time to Live (TTL) can be used to manage data growth by automatically 
deleting records after an elapsed time, using either record creation or modification. 
For example, Azure Cosmos DB provides an in-built TTL capability.

##  Options 06
Multiple data platforms are used based on requirements.

Different data technologies can be used in parallel, with optimized solutions 
for specific workload scenarios and volume requirements.

##  Options 07
None of the above.

---
