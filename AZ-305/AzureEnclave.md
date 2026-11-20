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

[Azure Enclave Architecture and Operations: Technical Reference Guide](https://notebooklm.link.google/DqOiTErMoYhA)  

1. Executive Summary & Strategic Value Proposition

Organizations operating in public cloud environments frequently manage workloads requiring stringent data isolation, rigorous regulatory compliance, and zero-trust security perimeters. As highlighted in John Savill's technical walkthrough on Azure Enclaves, common examples include proprietary medical and health records, sensitive research datasets, government defense programs, regulated financial systems, and isolated artificial intelligence (AI) testing sandboxes.

Historically, building a zero-trust, compliant environment in Microsoft Azure required cloud security teams to possess deep expertise across virtual networking, firewall administration, access management, and policy enforcement. As noted in the architectural analysis, approximately 90 percent of the infrastructure created by Azure Enclaves could technically be assembled using custom Bicep templates. However, doing so manually requires plumbing Azure Virtual WANs, deploying region-specific Secured Virtual Hubs with Azure Firewall, configuring complex Virtual Network (VNet) peering, maintaining Network Security Groups (NSGs) across every subnet, and manually assigning exhaustive Azure Policy initiatives. This manual approach imposes immense operational overhead and exposes organizations to configuration drift, where a single misconfigured firewall rule or omitted policy assignment undermines the security of the entire environment.

Azure Enclave addresses this challenge by introducing a first-party Azure resource provider that abstracts complex zero-trust architecture into managed, standardized building blocks. Operating under the guiding principle of "isolated by default, connected by explicit intent," Azure Enclaves automates the orchestration of all underlying networking, firewall, policy, and perimeter infrastructure. This enables security architects to deploy fully compliant, isolated environments rapidly while guaranteeing operational visibility and centralized governance.

Architectural Dimension	Traditional Manual Implementation	Azure Enclave Managed Solution
Infrastructure Orchestration	Manual Bicep/Terraform scripts for VNets, Hubs, Firewalls, and Peering.	Automated provisioning via a dedicated first-party resource provider.
Perimeter Security	Manual configuration of Azure Firewall policy rules and subnet-level NSGs.	Automated Secured Hub deployment with default-deny network isolation.
Policy & Compliance	Manual policy initiative assignments; highly vulnerable to configuration drift.	Built-in, immutable policy enforcement backed by Azure Deny Assignments.
IP Address Management	Manual tracking of overlapping IP CIDRs across subscriptions and regions.	Built-in automated IPAM reserving dedicated ranges from a central pool.
Inter-Workload Connectivity	Complex VNet peering, custom route tables, and manual firewall inspection rules.	Declarative Enclave Endpoints and Connections decoupling targets from routing.
Operational Governance	Ad-hoc administrative changes; manual audit logging setup across services.	Centralized approval workflows (1–5 approvers) and integrated audit logging.

2. Architectural Hierarchy: Community, Enclave, and Workload Constructs

Azure Enclaves organizes cloud resources into a structured, three-tiered administrative hierarchy comprising the Community, the Enclave, and the Workload. Each construct defines explicit boundaries across Microsoft Entra ID tenants, Azure subscriptions, and geographic regions.

Hierarchy Overview:

* Community: Tenant-wide governance boundary, multi-region, multi-subscription, global Virtual WAN scope, IPAM pool (/8 to /16).
* Enclave: Subscription-bound and single-region localized network container, VNet, subnets, NSGs, flow logs, managed identity.
* Workload: Linked resource groups containing application resources (VMs, AKS, SQL, Storage) constrained to Enclave subnets.

Community Layer

The Community serves as the top-level zero-trust boundary and governance scope within Azure Enclaves. It acts as the master container for shared networking infrastructure, centralized logging, and baseline security policy initiatives. As presented in the architectural overview, key operational boundaries include:

* Tenant Scoping: A Community is strictly bound to a single Microsoft Entra ID tenant.
* Multi-Region & Multi-Subscription Extension: A Community can span across multiple Azure regions and multiple Azure subscriptions under the same Entra ID tenant.
* Global Network Substrate: Defines a central Classless Inter-Domain Routing (CIDR) block ranging from /8 to /16, managed dynamically via automated IP Address Management (IPAM).
* Centralized Telemetry: Automatically provisions a shared Log Analytics workspace to aggregate audit logs, diagnostic metrics, and firewall telemetry across all nested enclaves.

Enclave Layer

An Enclave is a localized, isolated execution boundary created inside a parent Community. It encapsulates the network perimeter and runtime environment for a specific set of application components:

* Strict Boundary Restrictions: Unlike the Community, an Enclave cannot span multiple subscriptions or multiple regions. It is strictly pinned to a single Azure subscription and a single Azure region due to underlying Virtual Network architectural limits.
* Dynamic Network Allocation: Upon creation, an Enclave requests a specific IP address capacity. The IPAM engine automatically carves out a contiguous CIDR block from the Community's master pool and assigns it to the Enclave's Virtual Network.
* Perimeter Infrastructure: Automatically provisions an Azure Virtual Network, configures requested subnets, attaches Network Security Groups (NSGs) to every subnet, and streams VNet Flow Logs to a dedicated storage account using a system-assigned managed identity.

Workload Layer

The Workload represents the functional application services and data resources running within an Enclave:

* Resource Group Binding: A Workload consists of one or more linked Azure Resource Groups (which must be empty prior to linking or created directly through the Enclave interface).
* Supported Azure Services: Accommodates standard Azure resources, including Virtual Machines, Azure Kubernetes Service (AKS) clusters, SQL databases, and storage accounts.
* Strict Subnet Binding: Resources deployed into a Workload are restricted by policy; they can only attach to subnets belonging to their specific Enclave. Attempts to expose public endpoints or connect to unauthorized external networks are automatically blocked.

Construct Tier	Multi-Region Support	Multi-Subscription Support	Primary Security & Operational Function
Community	Yes	Yes	Global zero-trust boundary, Virtual WAN hub management, baseline policy initiatives, and central log aggregation.
Enclave	No (Single Region)	No (Single Subscription)	Localized network perimeter, VNet provisioning, NSG enforcement, and managed identity assignment.
Workload	No (Bound to Enclave)	No (Bound to Enclave)	Application runtime execution within linked resource groups under mandatory policy restrictions.

3. Automated Zero-Trust Networking and Infrastructure Topology

The networking foundation of Azure Enclaves relies on Azure Virtual WAN and Secured Virtual Hubs to enforce hardware-assisted packet inspection, regional transit routing, and default-deny perimeter isolation.

Global Virtual WAN and Regional Secured Hub Integration

When a Community is established, Azure Enclaves provisions a global Azure Virtual WAN resource. As Enclaves are deployed across different geographic regions, the service orchestrates regional networking infrastructure through the following automated sequence:

1. Automated Secured Hub Provisioning: In every Azure region where an Enclave is deployed, Azure Enclaves provisions a Secured Virtual Hub integrated with Azure Firewall.
2. Regional Transit Routing: The Secured Hub acts as a regional transit router. All inbound, outbound, and inter-enclave traffic is forced through the Azure Firewall for deep packet inspection and policy enforcement.
3. Dedicated Virtual Hub Allocation: For high-throughput workloads or strict performance isolation, administrators can pre-deploy dedicated Virtual Hubs in specific regions and assign designated Enclaves to those dedicated hubs rather than sharing default regional hubs.

IP Address Management (IPAM) and Subnet Allocation

To prevent IP address collisions across large enterprise environments, Azure Enclaves embeds an automated IPAM engine:

* Master CIDR Allocation: Administrators define a non-overlapping IP address block (between /8 and /16) at the Community level during initial deployment.
* Subnet Carve-Outs: When creating an Enclave, the administrator requests the required subnet sizing. IPAM dynamically carves out the CIDR range from the Community pool and binds it to the Enclave's Virtual Network.
* Subnet Security Baselines: Every subnet created within an Enclave is automatically paired with an NSG configured with explicit default-deny rules. Subnet traffic flow logs are enabled by default and streamed to a managed storage account via system-assigned managed identities.

4. Governance, Immutable Policy Enforcement, and Compliance Baselines

Security across Azure Enclaves is governed by mandatory Azure Policy initiatives, system-assigned managed identities, and Azure Deny Assignments that prevent configuration drift or policy deletion.

Inherited Policy Initiatives and Immutable Enforcement

Governance policies established at the Community level automatically inherit down to all child Enclaves and Workload resource groups. This inheritance model operates similarly to Azure Management Group policy structures, with a critical security distinction:

* Immutability via Deny Assignments: Policy assignments set at the Community level are locked using Azure Deny Assignments. Even administrators holding Owner permissions on individual Enclaves or subscriptions cannot delete or modify inherited community policy assignments.
* Auditability of Exceptions: If an Enclave requires specific policy exemptions (and if local policy overrides are permitted by Community settings), exceptions can be configured by authorized Role-Based Access Control (RBAC) principals. However, all exceptions are logged, audited, and highlighted in compliance reporting dashboards.

Mandatory Compliance Baselines

By default, Azure Enclaves applies a strict baseline compliance initiative designed to eliminate common cloud exposure vectors. Key enforced rules include:

* Mandatory Private Endpoints: All Azure Platform-as-a-Service (PaaS) resources (such as Azure Storage, Key Vault, and SQL Database) must disable public access points and utilize Azure Private Link.
* Disabled Public Storage Access: Storage accounts are explicitly blocked from allowing public blob access or unencrypted transport.
* Strict TLS Version Thresholds: All incoming and outgoing Web/API connections must enforce TLS version 1.2 or higher.
* Managed Identity Integration: Policy evaluation, flow log streaming, and compliance auditing are executed using dedicated system-assigned managed identities, eliminating stored administrative credentials.

5. Traffic Control Mechanics: Endpoints, Connections, and Egress Abstractions

Azure Enclaves manages network communication through a declarative abstraction model composed of Community Endpoints, Enclave Endpoints, and Enclave Connections. This model decouples destination configurations from connection requests, enabling clean separation of administrative duties.

Community Endpoints (Egress Control)

Community Endpoints define explicitly permitted outbound egress destinations outside the Enclave boundary that have been approved as acceptable operational risks:

* Supported Destination Types: Destinations can be specified using explicit IP addresses, Fully Qualified Domain Names (FQDNs), FQDN tags (such as Azure Firewall system tags for Windows Update or Azure Virtual Desktop), Azure Service Tags, or specific private network CIDRs.
* Default-Deny Perimeter: By default, zero outbound internet or external network access is permitted until a Community Endpoint is explicitly configured and attached.

Enclave Endpoints and Enclave Connections (Ingress & Inter-Workload Control)

To enable communication into an Enclave or between two Enclaves, Azure Enclaves utilizes a paired endpoint-and-connection structure:

1. Enclave Endpoints: Defined by the target Enclave owner to specify what internal workloads are exposed to external callers. The endpoint is defined using a 3-tuple parameter set: Target IP Range, Destination Port, and Protocol (e.g., 10.67.1.10–10.67.1.11, Port 443, TCP).
2. Enclave Connections: Created by the source Enclave owner to establish a logical connection to an exposed Enclave Endpoint or Community Endpoint. Connections can span across different Enclaves within the same Community or across separate Communities (requiring RBAC authorization on both ends).

Operational Scenario: Dynamic Endpoint Abstraction

This decoupled model provides a significant operational advantage during infrastructure lifecycle updates:

* Active Directory Migration Example: Consider a scenario where Active Directory Domain Controllers (DCs) are hosted inside an Enclave. The target Enclave owner defines an Enclave Endpoint specifying the DC IP addresses and required Kerberos/RPC ports. Consuming Enclaves create Enclave Connections referencing that Enclave Endpoint.
* Seamless Target Redeployment: If the Domain Controllers are redeployed and assigned new IP addresses, the target administrator updates only the single Enclave Endpoint definition. All consuming Enclave Connections automatically maintain connectivity without requiring individual workload owners to update their firewall rules or routing tables.

6. Governance Operations, Multi-Approver Workflows, and Billing Architecture

Centralized Approval Workflows and RBAC

To prevent unauthorized architectural modifications in sensitive environments, Azure Enclaves incorporates a built-in approval engine:

* Configurable Approval Triggers: High-risk lifecycle actions—such as Enclave creation, endpoint modification, or policy relaxation—can be configured to require mandatory administrative approval.
* Multi-Person Quorum: Approval policies can mandate between 1 and 5 authorized approvers.
* Complete Audit Trail: When a request is submitted, designated approvers review the action within the Azure Enclaves governance portal. Upon approval, the resource provider automatically completes the deployment, recording full execution logs for audit compliance.

Three-Tier Financial Billing Model

The financial model of Azure Enclaves combines fixed service fees with underlying consumption components across three distinct tiers:

1. Tier 1: Enclave Service Fee: A fixed, per-enclave, per-hour managed resource provider fee covering Enclave management and orchestration.
2. Tier 2: Underlying Infrastructure: Consumption charges for underlying networking and security infrastructure, including Azure Virtual WAN scale units, Regional Secured Hubs, Azure Firewall processing hours, Azure Bastion hosts, Log Analytics ingestion, and VNet Flow Logs storage.
3. Tier 3: Workload Consumption: Standard Azure resource consumption charges for deployed virtual machines, AKS clusters, SQL databases, and application resources.

7. Azure Component Reference and Architectural Mapping

Azure Enclaves orchestrates a suite of native Azure infrastructure services. The following reference table maps the high-level Enclave constructs to their underlying Azure resource providers and native service documentation concepts.

Enclave Construct	Underlying Azure Native Component	Technical Purpose & Documentation Reference
Community Network Hub	Microsoft.Network/virtualWans	Global transit network backbone managing regional hub deployments and inter-region routing.
Regional Transit Router	Microsoft.Network/hubVirtualNetworkConnections	Regional Secured Virtual Hub providing centralized packet routing and Virtual WAN integration.
Perimeter Security Engine	Microsoft.Network/azureFirewalls	Deep packet inspection engine enforcing Community Endpoints, FQDN filtering, and rule policies.
Enclave VNet & Subnets	Microsoft.Network/virtualNetworks	Isolated layer-3 network container carved out via automated IPAM CIDR allocation.
Subnet Traffic Filters	Microsoft.Network/networkSecurityGroups	Stateful packet filtering attached to every Enclave subnet with automated flow logging.
Policy Engine & Deny Locks	Microsoft.Authorization/policyAssignments	Inherited policy initiatives locked via Azure Deny Assignments (Microsoft.Authorization/denyAssignments).
Administrative Identity	Microsoft.ManagedIdentity/userAssignedIdentities	Passwordless identity for policy enforcement, compliance auditing, and flow log storage streaming.
Remote Access Bastion	Microsoft.Network/bastionHosts	Optional managed jump-host service for secure, browser-based RDP/SSH access without public IPs.
Central Telemetry Store	Microsoft.OperationalInsights/workspaces	Log Analytics workspace aggregating firewall logs, NSG flow logs, policy audits, and diagnostic telemetry.

Document authoring and architectural mapping completed based on technical walkthrough context.

---