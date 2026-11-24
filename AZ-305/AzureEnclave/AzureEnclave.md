# What is Azure Enclave?

[Azure Enclave - Isolated, Secure and Compliant by Default John Savill's Technical Training](https://www.youtube.com/watch?v=pVlM5ScV5OA)  

---

# What is Azure Enclave?

[Azure Enclave - Isolated, Secure and Compliant by Default John Savill's Technical Training](https://www.youtube.com/watch?v=pVlM5ScV5OA)   

Azure Enclave is a managed Microsoft Azure service that accelerates and streamlines 
the deployment and management of isolated, zero-trust, and compliant cloud environments 
for sensitive workloads. 

[1] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave), 
[2] (https://www.microsoft.com/en-us/microsoft-cloud/blog/us-government/2026/10/13/azure-enclave-is-now-generally-available-managed-workload-isolation-for-government-and-regulated-industries/)

## How It Works: The Community-and-Enclave Model

Azure Enclave uses a hierarchical architecture to protect and organize virtual boundaries: 

[1] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

- Communities: 
A community acts as a central hub for networking, governance, and monitoring. 
It is managed via `Azure Virtual WAN` and protected using 
`Azure Firewall, policy guardrails, and role-based access control (RBAC)`. 

[1] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

- Enclaves:
An enclave is an isolated, zero-trust software-defined Azure Virtual Network connected to the community hub. 
It is restricted from the outside by default and protected through Network Security Groups (NSGs) and Private Links. 

[1] (https://learn.microsoft.com/da-dk/Azure/enclave/what-enclave), 
[2] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

- Workloads: 
These are logical groups that link your customer-managed Azure resources to an enclave, 
allowing them to inherit the enclave's security posture and policies. 

[1] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

## Key Capabilities & Benefits

- Network Isolation: Traffic is locked down by default and restricted to authorized Microsoft services or explicitly approved enclave endpoints.
- Policy Governance: Uses Azure Policy guardrails and RBAC deny assignments to enforce compliance and prevent unauthorized changes.
- Built-in Monitoring: Automatically integrates with a Log Analytics Workspace for centralized or isolated diagnostic logging.
- Accelerated Setup: Removes the need to manually rebuild complex, air-gapped, or regulated cloud foundations from scratch. 

[1] (https://learn.microsoft.com/en-us/azure/enclave/why-azure-enclave), 
[2] (https://learn.microsoft.com/en-us/azure/enclave/access-controls-enclaves), 
[3] (https://learn.microsoft.com/da-dk/Azure/enclave/what-enclave), 
[4] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

## Common Use Cases

- Regulated Collaboration: 
Safely bringing together multiple internal teams, government agencies, defense contractors, or external partners under strict access controls. 

[1] (https://www.microsoft.com/en-us/microsoft-cloud/blog/us-government/2026/10/13/azure-enclave-is-now-generally-available-managed-workload-isolation-for-government-and-regulated-industries/), 
[2] (https://learn.microsoft.com/en-us/azure/enclave/why-azure-enclave)

- Sensitive R&D: Running isolated research projects that require strict data protection and auditability. 

[1] (https://learn.microsoft.com/en-us/azure/enclave/why-azure-enclave)

- Compliance-Driven Workloads: 
Meeting strict organizational or governmental security standards with pre-configured architectural patterns. 

[1] (https://azure.microsoft.com/en-gb/products/enclave), 
[2] (https://learn.microsoft.com/en-us/azure/enclave/why-azure-enclave)

You can read more about the architecture on the Microsoft Learn Azure Enclave Documentation or 
review pricing details on the Azure Enclave Pricing Page. 

[1] (https://azure.microsoft.com/en-gb/products/enclave), 
[2] (https://learn.microsoft.com/en-us/azure/enclave/what-azure-enclave)

---
