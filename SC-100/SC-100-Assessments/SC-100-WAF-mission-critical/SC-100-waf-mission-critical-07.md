# Answer Q07-A01

## Selected Options

##  Options 02
A container orchestrator other than AKS is used to host and orchestrate containerized workloads.
Some scenarios might require specialized container orchestration engines or self-hosted Kubernetes.

---

# Q07

## Mission Critical: Application Design

[Does the application use a container orchestrator to manage and operate containers?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=d2df74bc-509d-432d-83c8-292bb8ba2560&category=3b978c5b-050a-4758-91ce-15c48a3800e1)  

# Does the application use a container orchestrator to manage and operate containers?

There are several Azure application platforms capable of effectively hosting containers, 
and each has their own advantages and disadvantages that should be analyzed in the context 
of business requirements to inform an optimal technical choice. 

Each platform serves as an optimal choice for certain scenarios.

##  Options 01
Azure Kubernetes Service (AKS) is used to orchestrate all containerized workloads.

Azure Kubernetes Service (AKS) is Microsoft Azure's native managed Kubernetes service based on the open-source Kubernetes project. It allows for rapid Kubernetes cluster provisioning without complex 
cluster administration, and enhances standard Kubernetes with a rich feature set that includes advanced networking and identity capabilities. It's also the strategic application hosting platform within internal Microsoft engineering organizations.

##  Options 02
A container orchestrator other than AKS is used to host and orchestrate containerized workloads.

Some scenarios might require specialized container orchestration engines or self-hosted Kubernetes.

##  Options 03
The use of multiple availability zones is factored into either a single cluster or multiple clusters based on the application design and architecture.

Depending on interzone communication and latency requirements, it might make sense to either spread a cluster across multiple zones or pin them to a single zone.

##  Options 04
Containers are distributed across multiple Azure availability zones.

The use of multiple availability zones requires the distribution of containers across these regions. 
This happens automatically when >1 replicas are used and the cluster is deployed across more than one availability zone.

##  Options 06
None of the above.

---
