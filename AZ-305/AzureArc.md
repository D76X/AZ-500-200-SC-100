
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
