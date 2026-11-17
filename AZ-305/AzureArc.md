
# Azure Arc

[Describe the Purpose of Azure Arc - AZ-900 Certification Course - May 2022 New John Savill's Technical Training](https://www.youtube.com/watch?v=cW6_rvDYSHg)  

[Azure Arc-Enabled Servers Walkthrough John Savill's Technical Training](https://www.youtube.com/watch?v=OHs1txVKPHw)  

---

# What asre the "Azure Hybrid Instance Metadata Service", the "Guest Configuration Arc Service" and the "Guest Configuration Extension Service"? What dio they do?

1. Azure Hybrid Instance Metadata Service 
2. Guest Configuration Arc Service
3. Guest Configuration Extension Service

These three services are the core background components of the `Azure Connected Machine agent (AMA)`. 
They work together to connect on-premises, edge, or multi-cloud Windows and Linux servers to Azure Arc, allowing them to be managed alongside native Azure resources. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview), 
[2] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent), 
[3] (https://blog.cellenza.com/en/cloud/azure-arc-enabled-servers-a-practical-approach/)

1. Azure Hybrid Instance Metadata Service (himds)

This is the primary connection and identity service for the agent. 

[1] (https://docs.azure.cn/en-us/azure-arc/servers/security-overview), 
[2] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent)

- Connection and Heartbeats. 
It establishes and maintains the connection between your server and Azure, 
sending a heartbeat every five minutes to report that the machine is online. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview), 
[2] (https://docs.azure.cn/en-us/azure-arc/servers/security-overview)

- Metadata Synchronisation. 
It collects and synchronises system details—such as operating system version, 
hardware specs, and network configurations—with Azure. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview), 
[2] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent)

- Identity and Local API. 
It manages the server's Microsoft Entra managed identity and hosts a local REST API. 
Local applications and extensions query this API to retrieve instance metadata or 
request authentication tokens for Azure services. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent), 
[2] (https://docs.azure.cn/en-us/azure-arc/servers/security-overview)

---

2. Guest Configuration Arc Service (GCArcService)

This service handles policy auditing and compliance inside the operating system 
(a feature now officially referred to by Microsoft as Azure Machine Configuration). 

[1] (https://wmatthyssen.com/2025/03/03/azure-arc-managing-azure-arc-enabled-servers-with-machine-configuration/), 
[2] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent)

- Policy Auditing. 
It evaluates the server against assigned Azure Policy rules to check if the OS settings, 
installed applications, and security baselines meet your organisation's standards. 

[1] (https://wmatthyssen.com/2025/03/03/azure-arc-managing-azure-arc-enabled-servers-with-machine-configuration/)

- Configuration Enforcement. 
Depending on how the policy is configured, it can also apply and enforce required 
configuration changes directly on the machine. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/vmware-vsphere/azure-arc-agent), 
[2] (https://wmatthyssen.com/2025/03/03/azure-arc-managing-azure-arc-enabled-servers-with-machine-configuration/)

---

3. Guest Configuration Extension Service (ExtensionService)

This service acts as the local deployment manager for add-on tools. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview)

- Extension Lifecycle. 
It handles installing, updating, and uninstalling Azure VM extensions on the non-Azure server.

- Tool Integration. 
Through this service, you can remotely deploy capabilities such as: 

    - the Azure Monitor Agent, 
    - Microsoft Defender for Endpoint, or 
    - Custom Script Extensions 

directly from the Azure portal. 

[1] (https://blog.cellenza.com/en/cloud/azure-arc-enabled-servers-a-practical-approach/), 
[2] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview), 
[3] (https://www.linkedin.com/pulse/unlocking-power-hybrid-cloud-management-azure-arc-divya-javangula)

For full architectural details and resource limits, see the Microsoft Learn Azure Connected Machine agent overview. 

[1] (https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview)

---

# [Azure Arc-Enabled Servers: Comprehensive Technical Architecture & Operational Guide](https://notebooklm.link.google/SwDRN2WUxECk)  

## NotebookLM Summary
[Azure Arc-Enabled Servers Walkthrough John Savill's Technical Training](https://www.youtube.com/watch?v=OHs1txVKPHw)  

The management of enterprise computing environments has grown increasingly complex as workloads expand across on-premises data centers, 
edge locations, and multiple public cloud providers. Organizations frequently face operational fragmentation when managing infrastructure 
outside native cloud environments, resulting in disparate management portals, inconsistent governance models, and fractured security visibility. Azure Arc-enabled servers addresses this challenge by extending the Azure Resource Manager control plane directly into operating systems running anywhere outside native Azure regions. As detailed in John Savill's technical walkthrough, this architecture allows enterprise IT organizations to project external physical and virtual servers into Azure as native resources, establishing a unified operational plane without requiring hypervisor-level integration or infrastructure migration.

1. Architectural Foundation & Control Plane Extension

In native Azure deployments, Azure Resource Manager serves as the centralized, RESTful control plane through which all resource creation, management, monitoring, and governance occur. Whether interaction happens via the Azure Portal, Azure CLI, Azure PowerShell, ARM templates (JSON or Bicep), or third-party infrastructure-as-code tools such as Terraform, every operation passes through Azure Resource Manager. This unified control plane delivers essential operational capabilities out of the box, including central inventory registration, resource graph querying, key-value metadata tagging, role-based access control (RBAC), and baseline governance through Azure Policy.

When servers reside outside native Azure regions—whether on-premises or hosted in secondary public clouds like AWS or Google Cloud Platform—they traditionally operate outside this management plane. This isolation forces administrators to maintain separate tools and processes for policy enforcement, patch management, and monitoring. Azure Arc bridges this gap by installing an agent directly inside the host operating system, projecting the external server into Azure Resource Manager as a hybrid compute object.

Control Plane Extension Model: Azure Resource Manager acts as the unifying restful API layer. Native Azure resources (Virtual Machines, Azure Kubernetes Service, Databases) and Azure Arc hybrid compute resources (on-premises physical servers, multicloud VMs) project into the same ARM control plane, enabling unified policy enforcement, RBAC, and inventory management.

By bringing external operating systems under the Azure Resource Manager umbrella, organizations eliminate management siloes. Hybrid compute objects immediately inherit control plane governance benefits, allowing enterprise operations teams to apply consistent tagging for billing and organization, query inventory across all environments via Azure Resource Graph, enforce structural control plane policies, and manage extension deployments from a single pane of glass.

2. Platform Support, OS Scope & System Prerequisites

Azure Arc-enabled servers is engineered to support a broad spectrum of enterprise server operating systems across physical hardware and virtualized environments. Because communication is driven entirely by agents running within the operating system rather than hypervisor integrations, Azure Arc remains agnostic to the underlying hardware or virtualization stack.

The platform provides extensive coverage across both Windows and Linux distributions, focusing specifically on server-class operating systems:

* Windows Server Operating Systems: Supports Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019, and Windows Server 2022.
* Specialized Windows Client Usage: While Windows 10 and Windows 11 are listed as supported operating systems, they are evaluated strictly as server-like instances dedicated to specialized application hosting or monitoring scenarios rather than end-user desktop environments.
* Linux Operating Systems: Broad support across major enterprise distributions, including Red Hat Enterprise Linux (RHEL), SUSE Linux Enterprise Server (SLES), Ubuntu, Debian, CentOS, Rocky Linux, Azure Linux (formerly code-named Mariner), Oracle Linux, and Amazon Linux.
* Hardware and Virtualization Support: Functions across physical bare-metal servers, hypervisor virtual machines (such as VMware vSphere or Microsoft Hyper-V), and virtual instances running in alternative public clouds.

Before deploying the Azure Connected Machine Agent, target operating systems must meet baseline software prerequisites. On Windows systems, the agent requires the .NET Framework to be present. On Linux distributions, PowerShell 4.0 or higher is required to facilitate agent operations and script execution.

3. Network Connectivity & Security Topologies

Azure Arc-enabled servers is not designed as an air-gapped solution; it fundamentally requires continuous line-of-sight connectivity to the Azure control plane. All communication between the host agent and Azure services is outbound-initiated over HTTPS using TCP Port 443. The architecture never requires inbound firewall ports to be opened from the internet to the local machine, preserving host network security boundaries.

Organizations can implement one of several network topologies to establish outbound connectivity to Azure Resource Manager and associated platform services:

Network Topology	Communication Path	Architecture Requirements	Operational Considerations
Public Endpoint Direct	Standard outbound internet route	Line-of-sight to Azure Service Tags over TCP 443	Simplest setup; requires direct or routed outbound internet access.
HTTP/HTTPS Proxy	Routed outbound via DMZ Proxy	Proxy configuration passed to Connected Machine Agent	Suitable for enterprise DMZs; inspects or restricts outbound web traffic.
Azure Private Link	Encrypted private IP routing	Azure Private Link Scope (AMPOLS), ExpressRoute / VPN, Private DNS	Eliminates public IP traffic; routes agent traffic privately into Azure VNets.

When deploying Azure Private Link, private endpoints are instantiated within an Azure Virtual Network, assigning dedicated private IP addresses for Azure Arc endpoints. On-premises networks route traffic over ExpressRoute private peering or Site-to-Site VPN connections, utilizing custom DNS configurations to resolve Azure Arc endpoints to private IP space. If telemetry collection via Azure Monitor is enabled, a dedicated Azure Monitor Private Link Scope (AMPLS) must be configured alongside the Azure Arc Private Link Scope.

For security-conscious environments, outgoing traffic can be filtered using Azure Service Tags or explicit Fully Qualified Domain Name (FQDN) allow-lists. Azure Arc operates across standard Azure Commercial regions, Azure Government (Azure Gov), and Azure operated by 21Vianet in China.

An optional architectural component is the Azure Relay service (utilizing Azure Service Bus). Azure Relay enables proactive bi-directional administrative actions—such as interactive OpenSSH sessions, Windows Admin Center integration, and instant notification polling—without requiring public inbound firewall rules. If an organization chooses to prohibit remote management or proactive push notifications, the specific Service Bus and Relay FQDNs can be restricted without compromising standard outbound agent telemetry and policy evaluation.

4. Enterprise Onboarding & Automation Framework

Deploying the Connected Machine Agent at enterprise scale requires structured onboarding strategies tailored to organizational security and infrastructure automation standards. The Azure Portal provides built-in script generation tools supporting both individual and automated mass deployments.

Onboarding methods fall into two primary operational patterns:

1. Single Server Interactive Onboarding: Designed for ad-hoc machine registration or evaluation environments. The generated deployment script initiates an interactive OAuth authentication prompt in a local web browser, requiring the deploying administrator to authenticate directly against Azure Entra ID. This eliminates the need to store secrets or certificates on target servers.
2. Multi-Server Automated Onboarding: Engineered for large-scale enterprise rollouts across hundreds or thousands of servers. The deployment script uses a Microsoft Entra ID Service Principal authenticated via a client secret or certificate. The script assigns target machines to a pre-defined Azure Subscription and Resource Group.

Enterprise operations teams can integrate agent deployment into existing configuration management and orchestration pipelines. The Connected Machine Agent can be distributed via documented Ansible playbooks, Chef cookbooks, Puppet modules, Microsoft Endpoint Configuration Manager (MECM/SCCM), PowerShell Desired State Configuration (DSC), Active Directory Group Policy Objects (GPO), or remote PowerShell scripts.

When implementing automated multi-server scripts, security best practices dictate that Service Principal credentials must never be committed to plain-text files or public code repositories such as GitHub. Organizations should store authentication secrets within enterprise key vaults or encrypted configuration stores, injecting them securely during pipeline execution.

5. Connected Machine Agent Architecture & System Daemons

The Connected Machine Agent operates as a lightweight system service on Windows or daemon on Linux, establishing the local execution environment for hybrid control plane capabilities. Operating overhead is minimal, consuming approximately 0.07% of a normalized CPU core on Windows (0.02% on Linux) and utilizing approximately 57 MB of RAM on Windows (42 MB on Linux). Resource consumption scales upward only when heavy extensions—such as Azure Monitor Agent collecting high-frequency diagnostic logs—are enabled and active.

The agent consists of three underlying system services, outlined below:

System Daemon / Service Name	Service Identifier	Primary Operational Responsibility	System Interactions
Azure Hybrid Instance Metadata Service	himds	Replicates Azure IMDS functionality for non-Azure hosts	Issues Microsoft Entra ID OAuth tokens for System-Assigned Managed Identity; exposes machine metadata locally
Guest Configuration Arc Service	gcarc	Drives in-guest policy auditing and OS compliance	Executes guest OS configuration audits, Desired State Configuration (DSC), and Change Tracking assessments
Extension Manager Service	extmd	Lifecycle management of Azure Arc VM extensions	Provisions, updates, and uninstalls extensions (AMA, Custom Script Extension, OpenSSH, Windows Admin Center)

Agent software does not feature an autonomous self-update mechanism. Instead, agent maintenance aligns with standard OS update workflows: Windows Update automatically updates the agent on Windows hosts, while native package managers (apt, yum, zypper) handle updates on Linux systems. Enterprise IT teams can also push agent updates using central server management tools, while Azure Advisor continuously monitors environment health and alerts administrators when outdated agent versions are detected.

6. Identity Integration & Azure Resource Model

When the Connected Machine Agent registers a server, Azure Resource Manager creates a hybrid compute object represented by the resource type Microsoft.HybridCompute/machines. This resource resides within the designated Azure Subscription and Resource Group, transforming the external machine into a manageable entity inside Azure.

Administrators can inspect, query, and organize these hybrid assets using standard Azure tools. For instance, querying Azure Resource Graph Explorer provides instant visibility into all connected servers across multicloud and on-premises environments:

Resources
| where type == 'microsoft.hybridcompute/machines'
| project name, resourceGroup, location, properties.osProfile.computerName, properties.status


Simultaneously, the registration process provisions a System-Assigned Managed Identity in Microsoft Entra ID tied directly to the hybrid compute resource. This identity establishes a secure, credential-free authentication mechanism for the host server.

By leveraging the local Hybrid Instance Metadata Service, applications or scripts running on the external server can request Microsoft Entra ID tokens under the authority of the System-Assigned Managed Identity. This identity can be granted granular role-based access control (RBAC) permissions to Azure resources—such as Azure Key Vaults, Storage Accounts, or databases—allowing on-premises applications to securely access cloud services without hardcoding static credentials.

7. Operational Capabilities: Free vs. Paid Feature Matrix

Azure Arc-enabled servers adopts a clear functional boundary separating free control plane capabilities from value-added paid services. Organizations can onboard unlimited servers to access core control plane governance, inventory tracking, and remote management tools without incurring Azure licensing charges.

The operational capabilities are categorized across free and paid feature tiers:

Capability Tier	Operational Feature	Technical Description	Financial Model
Control Plane (Free)	Resource Inventory & Search	Registration as Microsoft.HybridCompute/machines and Azure Resource Graph visibility	Included at no cost
Control Plane (Free)	Control Plane Azure Policy	Enforces structural Azure ARM policies, location rules, and tagging standards	Included at no cost
Control Plane (Free)	Metadata Tagging & Groups	Key-value tagging for organizational alignment, filtering, and billing assignment	Included at no cost
Control Plane (Free)	Extension Management	Management lifecycle for Custom Script Extension, OpenSSH, WAC, and SQL discovery	Included at no cost
Control Plane (Free)	Remote Management Tools	Browser-based Windows Admin Center and OpenSSH connectivity via Azure Relay	Included at no cost
Guest OS Services (Paid)	Azure Policy Guest Configuration	In-guest security baselines, OS setting audits, Change Tracking, App Inventory	$6.00 per server / month
Azure Platform Services	Azure Monitor Telemetry	Ingestion and retention of performance metrics and event logs via Azure Monitor Agent	Charged per GB data ingested
Azure Platform Services	Microsoft Defender for Cloud	Advanced threat detection, vulnerability management, and security posture management	Charged per server / month
Azure Platform Services	Microsoft Sentinel	Enterprise SIEM log ingestion, threat hunting, and automated incident response	Charged per GB data ingested
Azure Platform Services	Extended Security Updates (ESU)	Pay-as-you-go critical security patches for legacy Windows Server 2008/2012 OSes	Azure consumption pricing

Secure Remote Management Architecture

Azure Arc provides zero-trust remote management capabilities without requiring public IP addresses, VPN tunnels, or open inbound firewall ports:

* OpenSSH Integration: Enables administrators to establish secure SSH command-line sessions to Windows or Linux Arc servers directly through the Azure CLI or Azure Portal. Outbound connections are brokered securely via Azure Relay. Access is enforced through Azure RBAC, requiring users to hold explicit roles such as Virtual Machine Administrator Login, Virtual Machine User Login, or Virtual Machine Local User Login.
* Windows Admin Center (WAC): Provides a web-based graphical management interface directly within the Azure Portal. The WAC extension executes WinRM, WMI, and PowerShell calls over an HTTPS-encapsulated Azure Relay connection. Administrators can manage files, inspect event logs, view performance counters, edit registry settings, and execute interactive PowerShell sessions without local network access.
* Custom Script Extension: Enables automated, out-of-band script execution on target hosts for configuration management or emergency remediation without opening remote management ports.

By combining free control plane governance with selective paid management services, Azure Arc-enabled servers delivers a scalable operational framework that extends Azure-native governance across hybrid, multicloud, and edge infrastructure.

---
