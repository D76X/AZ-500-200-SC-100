[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q10

A company runs an Azure Kubernetes Service (AKS) cluster hosting sensitive workloads. 
The security team has two requirements:

1. The Kubernetes API server must not be reachable from the public internet and must be accessible only through the company's connected internal networks.

2. Authorization for administrators performing `kubectl` operations must be managed centrally through Azure against the organization's existing Microsoft Entra users and groups, without maintaining Kubernetes-native RoleBinding and `ClusterRoleBinding` objects for those users.

Which two configurations should the team apply?

Select two options below.

### OPTION 01
Deploy AKS as a private cluster, so the API server has only a private endpoint reachable from within the virtual network

### OPTION 02
Enable Microsoft Entra ID integration for AKS user authentication, but leave Azure RBAC for Kubernetes authorization disabled on the cluster configuration

### OPTION 03
Configure network security group rules on the AKS node pool subnet to block inbound traffic on port 443 from the internet

### OPTION 04
`Enable Azure RBAC for Kubernetes authorization on the cluster`, so permissions are managed using Azure role assignments instead of native Kubernetes RBAC role bindings

## Answer and rationale

**Select options 01 and 04.**

Option 01 makes the AKS API server private, so it isn't reachable through a public endpoint. The company's connected networks must have private connectivity to the cluster virtual network and be able to resolve the private API server name through the appropriate private DNS configuration. [1]

Option 04 uses Azure RBAC role assignments to authorize access to Kubernetes resources. This lets administrators grant permissions to the organization's Microsoft Entra users and groups centrally without creating Kubernetes-native RoleBinding or `ClusterRoleBinding` objects for those identities. Azure RBAC for Kubernetes authorization requires managed Microsoft Entra integration for authentication; configure that integration as part of enabling this authorization model. [2][3]

---

### Why the other options are not correct

- **Option 02:** Microsoft Entra ID integration provides authentication, but by itself it doesn't replace Kubernetes RBAC authorization. `With Azure RBAC for Kubernetes authorization disabled`, access still has to be authorized using Kubernetes RBAC bindings, so this doesn't meet the requirement to manage authorization through Azure. [2][3]

- **Option 03:** The public AKS API server is a managed control-plane endpoint, not a service exposed by the node pool. An inbound NSG rule on the node pool subnet doesn't disable that public endpoint or make the API server private. A private cluster is the configuration that restricts API server access to its private endpoint. [1]

### References

1. [Create a Private Azure Kubernetes Service (AKS) Cluster](https://learn.microsoft.com/en-us/azure/aks/private-clusters) — Describes the private API server endpoint, private DNS, and the network connectivity required to reach it.

2. [Use Microsoft Entra ID Authorization for the Kubernetes API in AKS](https://learn.microsoft.com/en-us/azure/aks/entra-id-authorization) — Explains Azure RBAC role assignments for Kubernetes authorization and that managed Microsoft Entra integration is required.

3. [Enable Microsoft Entra ID Authentication for the AKS Control Plane](https://learn.microsoft.com/en-us/azure/aks/entra-id-control-plane-authentication) — Describes Entra ID authentication and how Kubernetes RBAC can otherwise use users' identities and group membership.

---