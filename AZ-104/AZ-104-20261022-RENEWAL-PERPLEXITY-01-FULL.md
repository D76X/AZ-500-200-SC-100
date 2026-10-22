# AZ-104 Practice Questions — Full Questions, Answers, and Reasoning

This document contains the complete text of the 25 practice questions from the study session, every available answer option, the selected correct answer, the reasoning behind it, and the comparison tables used to evaluate the options.

## Question 1

You plan to deploy an Azure App Service web app that will have the following settings:

| Setting | Value |
|---|---|
| Name | WebApp1 |
| Publish | Docker Container |
| Operating system | Windows |
| Region | West US |
| Windows Plan (West US) | ASP-RG1-8bcf |

You need to ensure that WebApp1 can use the ASP.NET V4.8 runtime stack.

Which setting should you modify?

### Available answers

- Operating system
- Publish
- Region
- Windows Plan

### Correct answer

**Publish**

### Reasoning

A web app published as a **Docker Container** runs the runtime supplied by its container image. Azure App Service does not provide or expose its built-in application runtime stacks—such as ASP.NET V4.8—for container-based web apps.

To use the managed **ASP.NET V4.8** runtime stack, WebApp1 must be published as **Code** on Windows. The Windows operating system is already correct, and neither the region nor the existing Windows App Service plan prevents use of that runtime stack.

### Option comparison

| Option | Modify? | Reason |
|---|---:|---|
| Operating system | No | Windows is already selected, and ASP.NET V4.8 requires Windows. |
| **Publish** | **Yes** | Change from Docker Container to Code so App Service can provide the managed ASP.NET V4.8 runtime stack. |
| Region | No | The region does not determine whether the built-in ASP.NET V4.8 stack is available. |
| Windows Plan | No | The existing Windows App Service plan can host a code-based ASP.NET web app. |

## Question 2

You have an Azure App Service web app named Contoso2025 that runs in the Standard App Service plan. Contoso2025 has five deployment slots in use.

A user named User1 has the Contributor role for Contoso2025.

You need to ensure that User1 can create additional deployment slots to Contoso2025.

What should you do?

### Available answers

- Assign User1 the Owner role for Contoso2025.
- Assign User1 the Website Contributor role for Contoso2025.
- Scale out the Contoso2025 App Service plan.
- Scale up the Contoso2025 App Service plan.

### Correct answer

**Scale up the Contoso2025 App Service plan.**

### Reasoning

The issue is not permissions: **Contributor** already includes the ability to create deployment slots. The issue is the plan quota.

The Standard App Service plan supports a maximum of **five deployment slots** per web app. Because Contoso2025 already uses five, User1 cannot create another slot until the plan is moved to a higher tier that supports more slots. Scaling **up** changes the pricing tier; scaling **out** only adds instances within the same tier and does not increase the slot quota.

### Option comparison

| Option | Correct? | Reason |
|---|---:|---|
| Assign User1 the Owner role | No | Contributor already has sufficient permissions to create deployment slots. |
| Assign User1 the Website Contributor role | No | This role can manage web apps and slots, but it cannot overcome the plan-tier slot limit. |
| Scale out the App Service plan | No | Scaling out adds VM instances but keeps the same pricing tier and slot quota. |
| **Scale up the App Service plan** | **Yes** | Moving to a higher pricing tier increases the number of supported deployment slots. |

## Question 3

You plan to deploy an Azure App Service web app that will have the following settings:

| Setting | Value |
|---|---|
| Name | WebApp1 |
| Publish | Code |
| Runtime stack | Java 21 |
| Operating system | Linux |
| Continuous deployment | Disable |

You need to ensure that you can integrate WebApp1 with GitHub Actions.

Which setting should you modify?

### Available answers

- Continuous deployment
- Operating system
- Publish
- Runtime stack

### Correct answer

**Continuous deployment**

### Reasoning

GitHub Actions integration is configured through App Service’s deployment/continuous deployment settings. During web app creation, you must set **Continuous deployment** to **Enable** to choose GitHub as the source, authorize access, select an organization/repository/branch, and allow Azure to generate a GitHub Actions workflow.

The existing settings are otherwise suitable: **Code** is correct for deploying Java source code, Linux supports Java workloads, and Java 21 is supported by GitHub Actions deployment workflows.

### Option comparison

| Option | Modify? | Reason |
|---|---:|---|
| **Continuous deployment** | **Yes** | Must be enabled to connect the web app to GitHub and use GitHub Actions for build and deployment. |
| Operating system | No | Linux supports Java and GitHub Actions deployment. |
| Publish | No | Code is the appropriate publish mode for a Java source-code deployment. |
| Runtime stack | No | Java 21 is supported and does not prevent GitHub Actions integration. |

## Question 4

You have an Azure App Service web app named WebApp1.

You discover that backup options are unavailable for WebApp1.

You need to back up WebApp1.

What should you do first?

### Available answers

- Modify the Application settings of WebApp1.
- Modify the platform settings of WebApp1.
- Scale out the app service plan.
- Scale up the app service plan.

### Correct answer

**Scale up the app service plan.**

### Reasoning

App Service’s built-in backup and restore feature requires at least the **Basic** pricing tier. If WebApp1 is on Free or Shared, the Backup option is unavailable.

Scaling **up** changes the App Service plan to a higher tier, such as Basic, Standard, Premium, or Isolated, thereby enabling backup. Scaling **out** adds instances but does not change the pricing tier, so it does not unlock backups. Application settings and platform settings configure runtime or platform behavior; they do not enable the backup feature.

### Option comparison

| Option | Correct? | Reason |
|---|---:|---|
| Modify Application settings | No | Application settings configure app runtime values, not backup availability. |
| Modify platform settings | No | Platform settings do not change the App Service pricing tier or enable backups. |
| Scale out the app service plan | No | Scaling out adds instances but retains the same pricing tier. |
| **Scale up the app service plan** | **Yes** | Basic, Standard, Premium, and Isolated tiers support App Service backup and restore. |

## Question 5

You have an Azure subscription that contains the following resources:

- A storage account named storage123
- A container instance named container1

The subscription contains a virtual network named VirtualNet4 that has the following subnets:

| Subnet | Description |
|---|---|
| SubnetA | Has a Microsoft.Storage service endpoint. |
| SubnetB | container1 is deployed to SubnetB. |
| SubnetC | No resources are connected to SubnetC. |

You plan to deploy an Azure container instance named container5 to VirtualNet4.

To which subnets can you deploy container5?

### Available answers

- SubnetA, SubnetB, and SubnetC
- SubnetB and SubnetC only
- SubnetB only
- SubnetC only

### Correct answer

**SubnetB and SubnetC only**

### Reasoning

Azure Container Instances (ACI) can be deployed only to a subnet that is delegated to `Microsoft.ContainerInstance/containerGroups`. A subnet delegated to ACI can contain only container groups; it cannot also contain other resources or service-endpoint configurations.

SubnetB already contains container1, so it is an ACI-delegated subnet and can host additional container groups. SubnetC is empty and can be delegated to ACI before deploying container5. SubnetA cannot be used because it already has a Microsoft.Storage service endpoint, which is incompatible with an ACI-only delegated subnet.

### Option comparison

| Subnet | Can deploy container5? | Reason |
|---|---:|---|
| SubnetA | No | It has a Microsoft.Storage service endpoint; ACI requires an empty subnet dedicated to container groups. |
| **SubnetB** | **Yes** | It already hosts container1, so it is delegated to ACI and can host additional container groups. |
| **SubnetC** | **Yes** | It has no connected resources and can be delegated to ACI. |

## Question 6

You have an Azure subscription that includes a virtual network with the following subnets:

| Subnet | Description |
|---|---|
| Subnet1 | Has a connected virtual machine. |
| Subnet2 | Has a connected App Service web app. |
| Subnet3 | Has a deployed container instance. |

You plan to deploy a container instance named container1.

To which subnets can you deploy container1?

### Available answers

- Subnet1 and Subnet3 only
- Subnet1, Subnet2, and Subnet3
- Subnet2 and Subnet3 only
- Subnet3 only

### Correct answer

**Subnet3 only**

### Reasoning

Azure Container Instances can be deployed only into a subnet delegated to `Microsoft.ContainerInstance/containerGroups`. Such a subnet can contain only ACI container groups; it cannot be shared with virtual machines, App Service integrations, or other Azure services.

Subnet3 already contains a container instance, so it is an ACI-delegated subnet and can host container1. Subnet1 contains a VM, and Subnet2 contains an App Service web app; neither is an ACI-only delegated subnet.

### Option comparison

| Subnet | Can deploy container1? | Reason |
|---|---:|---|
| Subnet1 | No | It contains a virtual machine, so it is not an ACI-only delegated subnet. |
| Subnet2 | No | It contains an App Service web app; App Service VNet integration cannot share an ACI subnet. |
| **Subnet3** | **Yes** | It already contains a container instance, so it is an ACI-delegated subnet. |

## Question 7

You have an Azure subscription that contains a virtual network named VNet1 in the West US region.

You plan to deploy the following container instances:

| Instance | Container image | Region |
|---|---|---|
| instance1 | Windows | West US |
| instance2 | Linux | West US |
| instance3 | Windows | East US |

Which container instances can be deployed to VNet1?

### Available answers

- instance1 and instance2 only
- instance1 and instance3 only
- instance1, instance2, and instance3
- instance1 only
- instance2 only

### Correct answer

**instance1 and instance2 only**

### Reasoning

A container instance deployed into a virtual network must be created in the **same Azure region** as that virtual network. VNet1 is in West US, so only the West US instances can use it.

Both Windows and Linux container groups are supported for VNet deployment by Azure Container Instances, so the operating system is not the limiting factor. instance3 is in East US and therefore cannot be deployed into VNet1, even though VNet peering could provide cross-region connectivity after deployment.

### Option comparison

| Instance | Region | Operating system | Can use VNet1? | Reason |
|---|---|---|---:|---|
| instance1 | West US | Windows | **Yes** | It is in the same region as VNet1. |
| instance2 | West US | Linux | **Yes** | It is in the same region as VNet1. |
| instance3 | East US | Windows | No | Its region differs from VNet1’s West US region. |

## Question 8

You have an Azure subscription that contains the following storage accounts:

| Storage account | Kind |
|---|---|
| storage1 | StorageV2 |
| storage2 | BlobStorage |
| storage3 | FileStorage |

Which storage account or storage accounts can you use lifecycle management with?

### Available answers

- storage1 and storage2 only
- storage1 and storage3 only
- storage1 only
- storage1, storage2, and storage3
- storage2 and storage3 only

### Correct answer

**storage1 and storage2 only**

### Reasoning

Azure Blob Storage lifecycle management policies are supported for **general-purpose v2 (StorageV2)** accounts and **BlobStorage** accounts. They apply to block blobs and append blobs.

FileStorage accounts are designed for Azure Files and do not contain blobs, so they do not support Blob Storage lifecycle management policies. Premium block blob accounts can use lifecycle management for deletion, but they do not support tiering; in this question, storage1 and storage2 are the supported standard blob-capable account kinds.

### Option comparison

| Storage account | Kind | Lifecycle management? | Reason |
|---|---|---:|---|
| storage1 | StorageV2 | **Yes** | General-purpose v2 accounts support lifecycle management for block and append blobs. |
| storage2 | BlobStorage | **Yes** | BlobStorage accounts support lifecycle management policies. |
| storage3 | FileStorage | No | FileStorage accounts contain Azure Files shares, not blobs. |

## Question 9

How does lifecycle management work on premium block blob accounts?

### Available answers

- Lifecycle management is not supported.
- Lifecycle management supports deletion only.
- Lifecycle management supports tiering only.
- Lifecycle management supports both deletion and tiering.

### Correct answer

**Lifecycle management supports deletion only.**

### Reasoning

Premium block blob accounts support Azure Blob Storage lifecycle management policies, but only for lifecycle actions that delete data. You can delete current blob versions, previous versions, and snapshots according to policy.

They do **not** support access-tier transitions. Therefore, rules such as `tierToCool`, `tierToCold`, and `tierToArchive` cannot move blobs from a premium block blob account to Hot, Cool, Cold, or Archive. To move data to a lower-cost tier, you must copy it to another account using a supported copy operation.

### Option comparison

| Lifecycle action | Premium block blob account |
|---|---:|
| Delete current blobs, previous versions, or snapshots | Supported |
| Tier to Cool, Cold, or Archive | Not supported |
| Rehydrate from Archive through a lifecycle policy | Not applicable / not supported |

## Question 10

You have an Azure Storage account named storage1 that is configured to use the Hot access tier.

storage1 has a container named container1 and a lifecycle management rule with the following settings:

- Move blob to cool storage: Selected  
- Days after last modification: 3  
- Move blob to archive storage: Selected  
- Days after last modification: 5  

On December 1, you create a file named File1 in container1.

On December 10, you rehydrate File1 and move the file to the Hot access tier.

When will File1 be moved to archive storage?

### Available answers

- On December 15
- On December 18
- On January 1
- Within 24 hours

### Correct answer

**On December 15**

### Reasoning

The archive rule is based on **days after last modification**, not days after the blob was moved to Hot. File1 was created on December 1, and rehydrating it or changing its access tier on December 10 does not update its last-modified time.

Therefore, the archive rule evaluates File1 as having been last modified on December 1. Five days later is December 15, so the lifecycle policy can move File1 back to Archive on that date.

To prevent this behavior, the lifecycle policy would need a condition such as `daysAfterLastTierChangeGreaterThan`, which considers when the blob’s tier last changed.

### Option comparison

| Event | Date | Effect |
|---|---|---|
| File1 created | December 1 | Last-modified time is set to December 1. |
| File1 rehydrated and moved to Hot | December 10 | Access tier changes, but last-modified time remains December 1. |
| Archive threshold reached | December 1 + 5 days | The policy can archive File1. |
| **File1 moved to Archive** | **December 15** | The archive rule applies based on last modification. |

## Question 11

You have an Azure subscription that contains a virtual network named VNET1. VNET1 uses the following address spaces:

- 10.10.1.0/24  
- 10.10.2.0/28  

VNET1 contains the following subnets:

| Subnet | Address space |
|---|---|
| Subnet1 | 10.10.1.0/24 |
| Subnet2 | 10.10.2.0/28 |

To Subnet1, you deploy a virtual machine named VM1 that runs Windows Server. VM1 has Remote Desktop enabled.

VM1 does **not** have a public IP address.

You need to be able to deploy Azure Bastion to protect VM1.

What should you do first?

### Available answers

- Add a new subnet to VNET1.
- Add a public IP address to VM1.
- Add an extension to VM1.
- Modify the address space of VNET1.

### Correct answer

**Add a new subnet to VNET1.**

### Reasoning

Azure Bastion requires a dedicated subnet named exactly **`AzureBastionSubnet`** in the same virtual network as the target VM. For current Bastion deployments, that subnet must be at least **/26** in size.

VNET1 currently has only Subnet1 and Subnet2, neither of which is named `AzureBastionSubnet`. Therefore, the first step is to add a new /26 or larger subnet with that exact name. VM1 does not need a public IP because Bastion connects to the VM through its private IP address.

### Option comparison

| Option | Correct? | Reason |
|---|---:|---|
| **Add a new subnet to VNET1** | **Yes** | Create a dedicated `AzureBastionSubnet` of at least /26 in VNET1. |
| Add a public IP address to VM1 | No | Bastion connects to VMs using their private IP addresses. |
| Add an extension to VM1 | No | No VM extension is required for Bastion connectivity. |
| Modify the address space of VNET1 | No | The existing VNet address space can accommodate a new /26 subnet. |

## Question 12

You have an Azure subscription that includes the following resources:

- VNet1, a virtual network  
- Subnet1, a subnet in VNet1  
- VM1, a virtual machine  
- NIC1, a network interface of VM1  
- LB1, a load balancer  

You create a network security group named NSG1.

To which two Azure resources can you associate NSG1?

### Available answers

- LB1
- NIC1
- Subnet1
- VM1
- VNet1

### Correct answer

**NIC1 and Subnet1**

### Reasoning

An Azure network security group (NSG) can be associated directly with a **network interface** or a **subnet**. It filters inbound and outbound traffic for the NIC or for all resources in the subnet.

It cannot be associated with a virtual machine, virtual network, or load balancer. For VM1, the NSG is associated with VM1’s network interface, NIC1—not with the VM resource itself. Microsoft recommends using either a subnet NSG or a NIC NSG, but not both, unless there is a specific reason and the interaction of rules is clearly understood.

### Option comparison

| Resource | Can associate NSG1? | Reason |
|---|---:|---|
| LB1 | No | Load balancers are not valid NSG association targets. |
| **NIC1** | **Yes** | An NSG can filter traffic for an individual VM network interface. |
| **Subnet1** | **Yes** | An NSG can filter traffic for every resource in the subnet. |
| VM1 | No | The NSG is associated with VM1’s NIC, not with the VM resource. |
| VNet1 | No | A virtual network is not a valid NSG association target. |

## Question 13

You have an Azure subscription that contains a virtual machine named VM1 and a storage account named storage1.

You need to ensure that VM1 can access storage1 by using a private IP address.

What should you use?

### Available answers

- A point-to-site (P2S) connection
- A service endpoint
- A VPN gateway
- The Azure Front Door service

### Correct answer

**A service endpoint**

### Reasoning

Among the available options, a **service endpoint** is the best choice. It enables secure connectivity from VM1’s virtual network to Azure Storage over the Azure backbone and allows storage1 to be restricted to traffic from that VNet or subnet.

However, a service endpoint does **not** assign storage1 a private IP address from the VNet. A **private endpoint** would be the ideal solution because it creates a network interface with a private VNet IP for storage1, but it is not one of the available answers.

### Option comparison

| Option | Best available? | Reason |
|---|---:|---|
| **Service endpoint** | **Yes** | Provides private, VNet-scoped access to Azure Storage over the Microsoft backbone, although storage1 retains its public endpoint rather than receiving a VNet private IP. |
| Point-to-site connection | No | It connects remote clients to Azure through a VPN; it does not provide private VNet access from VM1 to storage1. |
| VPN gateway | No | It provides site-to-site or point-to-site VPN connectivity, not a private IP endpoint for a PaaS storage account. |
| Azure Front Door | No | It is a global HTTP/HTTPS delivery and security service, not a private storage networking solution. |

## Question 14

You have an Azure subscription that contains the following virtual networks:

| Virtual network | Region | Virtual machines |
|---|---|---:|
| VNet1 | West US | 3 |
| VNet2 | West US | 4 |
| VNet3 | East US | 5 |
| VNet4 | East US | 2 |

Every virtual network is peered with all other virtual networks.

You plan to protect all of the connected virtual machines by using Azure Bastion.

What is the minimum number of Azure Bastion hosts that you must deploy?

### Available answers

- 1
- 2
- 3
- 4

### Correct answer

**1**

### Reasoning

A single Azure Bastion host can protect VMs in its own virtual network and in all virtual networks peered with it. Because all four VNets are fully peered, including across West US and East US through global VNet peering, one Bastion host can reach all 14 VMs.

You do not need one Bastion host per region or per VNet. Bastion must be deployed into a VNet that contains a dedicated `AzureBastionSubnet`, but after that it can use peering to connect to VMs in the other VNets.

### Option comparison

| Deployment approach | Minimum Bastion hosts | Reason |
|---|---:|---|
| **One Bastion host** | **1** | One host can protect VMs in its VNet and all peered VNets, including globally peered VNets. |
| One host per region | Not required | Global VNet peering allows a single Bastion host to reach VMs across regions. |
| One host per VNet | Not required | Microsoft explicitly states that a Bastion host is not required in every peered VNet. |

## Question 15

You recently created an Azure virtual machine Standard backup policy.

You need to configure a retention period for virtual machine instant recovery snapshots.

What is the maximum number of days that can be set for the retention period?

### Available answers

- 5
- 7
- 14
- 30

### Correct answer

**5**

### Reasoning

For an Azure VM **Standard** backup policy, instant recovery snapshot retention can be configured from **1 to 5 days**. The default value is 2 days.

The 30-day maximum applies to the **Enhanced** policy, not the Standard policy. Values such as 7 and 14 days are not valid maximums for Standard-policy instant recovery snapshots.

### Option comparison

| Policy type | Instant recovery snapshot retention |
|---|---|
| **Standard** | **1–5 days; maximum 5** |
| Enhanced | 1–30 days; maximum 30 |

## Question 16

You have a Recovery Services vault named Recovery1 that includes a backup policy named Policy1.

You back up several Azure virtual machines to Recovery1 by using Policy1.

You need to view the Azure Backup reports.

What should you do first?

### Available answers

- Configure the Diagnostics settings of Recovery1.
- Create an Azure Log Analytics workspace.
- Modify the Backup Configuration settings of Recovery1.

### Correct answer

**Create an Azure Log Analytics workspace.**

### Reasoning

Azure Backup reports require a Log Analytics workspace to store the reporting data emitted by the Recovery Services vault. Therefore, the first step is to create—or select—an existing Log Analytics workspace.

After the workspace exists, configure the diagnostics settings of Recovery1 to send the required resource-specific Backup event categories to that workspace. The Backup Configuration setting controls vault storage redundancy, not reporting.

### Option comparison

| Option | Correct? | Reason |
|---|---:|---|
| **Create an Azure Log Analytics workspace** | **Yes** | It is the prerequisite destination for Azure Backup report data. |
| Configure Diagnostics settings of Recovery1 | No | This is the next step, but it requires an existing Log Analytics workspace as its target. |
| Modify Backup Configuration settings | No | Backup Configuration controls vault storage redundancy, not reporting data flow. |

## Question 17

You have an Azure subscription that contains an Azure disk named Disk1.

You plan to use Azure Backup to back up Disk1.

What should you deploy first?

### Available answers

- A Backup vault
- A Storage account
- A Recovery Services vault
- An Azure Backup Server

### Correct answer

**A Backup vault**

### Reasoning

Azure Disk Backup uses a **Backup vault**, not a Recovery Services vault. The first step in configuring backup for an Azure managed disk is to create a Backup vault.

After creating the vault, you configure an Azure Disk Backup policy, select Disk1, and specify a snapshot resource group. A Recovery Services vault is used for workloads such as Azure VMs, Azure Files, SQL Server in Azure VMs, SAP HANA, and hybrid backups—not for standalone managed-disk backup.

### Option comparison

| Option | Correct? | Reason |
|---|---:|---|
| **Backup vault** | **Yes** | Required for Azure Disk Backup and manages the disk’s backup instances and snapshot resource group. |
| Storage account | No | Disk backups use incremental snapshots in a designated resource group, not a user-managed storage account. |
| Recovery Services vault | No | Recovery Services vaults are for other Azure Backup workload types, not standalone managed disks. |
| Azure Backup Server | No | It is used for hybrid/on-premises workload protection and is not required for Azure managed-disk backup. |

## Question 18

Your company has an Azure subscription.

You plan to create a virtual machine scale set named VMSS1 that has the following settings:

| Setting | Value |
|---|---|
| Resource group name | RG1 |
| Region | West US |
| Orchestration mode | Uniform |
| Security type | Standard |
| OS disk type | Standard SSD |
| Key management | Platform-managed key |

You need to add custom virtual machines to VMSS1.

What setting should you modify?

### Available answers

- Key management
- Orchestration mode
- OS disk type
- Security type

### Correct answer

**Orchestration mode**

### Reasoning

Only a virtual machine scale set that uses **Flexible** orchestration mode can have standard Azure virtual machines attached to it. Flexible mode manages standard VMs and supports mixed VM types, custom VMs, and greater control over individual instances.

Uniform mode uses a common VM profile to create and manage identical scale-set instances, so it does not support attaching custom VMs. The orchestration mode is selected when the scale set is created and cannot be changed afterward, so VMSS1 must be created with Flexible orchestration.

### Option comparison

| Setting | Modify? | Reason |
|---|---:|---|
| **Orchestration mode** | **Yes** | Change Uniform to Flexible to allow custom VMs to be attached to VMSS1. |
| Key management | No | Platform-managed keys affect disk encryption, not custom-VM support. |
| OS disk type | No | Standard SSD does not determine whether custom VMs can be attached. |
| Security type | No | Standard security type does not prevent attaching custom VMs. |

## Question 19

You have an Azure subscription.

You plan to use fault domains.

From which Azure resource can you configure the fault domains?

### Available answers

- Availability set
- Virtual machine
- Virtual machine scale set
- Virtual network

### Correct answer

**Availability set**

### Reasoning

You configure the number of fault domains when creating an **availability set**. Azure then automatically assigns each VM in that availability set to one of its fault domains and update domains.

Fault domains represent groups of underlying hardware that share common power and network infrastructure. Distributing VMs across fault domains reduces the chance that a single hardware failure affects all VMs. An availability set supports up to three fault domains.

### Option comparison

| Resource | Configure fault domains? | Reason |
|---|---:|---|
| **Availability set** | **Yes** | You specify the fault-domain count when creating the availability set. |
| Virtual machine | No | Azure assigns the VM to a fault domain when it is placed in an availability set. |
| Virtual machine scale set | No | Scale sets support fault-domain spreading, but the standard AZ-104 answer is the availability set. |
| Virtual network | No | A VNet provides networking and does not configure VM fault domains. |

## Question 20

You have an Azure virtual machine named VM1.

VM1 contains the following:

- A file named File1 that is stored on volume C:\
- A file named File2 that is stored on volume D:\
- An app named App1 that is in a running state
- A user named User1 who is connected to VM1

You plan to resize VM1.

What is preserved after the resize?

### Available answers

- File1 and File2 only
- File1 and the state of App1 only
- File1, File2, and the state of App1 only
- File1, File2, the state of App1, and the connection of User1
- File1 only

### Correct answer

**File1 only**

### Reasoning

Resizing VM1 restarts it. Therefore, App1’s running state and User1’s active connection are not preserved.

File1 is stored on `C:\`, which is on the persistent OS disk, so it remains after the resize. File2 is stored on `D:\`, which on a Windows Azure VM is typically the temporary/resource disk; data on that disk is not persistent and can be lost when the VM is resized, restarted, or moved to different hardware.

### Option comparison

| Item | Preserved after resize? | Reason |
|---|---:|---|
| **File1 (`C:\`)** | **Yes** | It is on the persistent OS disk. |
| File2 (`D:\`) | No | `D:\` is typically temporary storage and may be wiped during resize or hardware movement. |
| App1 running state | No | Resizing a running VM causes a restart. |
| User1 connection | No | The restart disconnects active user sessions. |

## Question 21

You have an Azure subscription.

You plan to deploy a virtual machine scale set named VMSS1 in the East US region. VMSS1 will have 8 instances.

What is the maximum number of availability zones that VMSS1 can use?

### Available answers

- 1
- 2
- 3
- 4

### Correct answer

**3**

### Reasoning

Azure regions that support availability zones provide at least three separate zones. A zone-spanning virtual machine scale set can distribute its instances across all selected zones.

VMSS1 can therefore use up to **three** availability zones in East US. The fact that it has only 8 instances does not limit the number of zones; Azure can distribute multiple instances across each selected zone.

### Option comparison

| Configuration | Availability zones used |
|---|---:|
| Zonal deployment | 1 |
| Zone-spanning deployment | 2 or more, up to the region’s supported maximum |
| **Maximum for VMSS1** | **3** |

## Question 22

You have a Microsoft Entra tenant that contains a user named User1.

You delete User1.

You plan to restore the User1 object.

What is the maximum number of days you have to restore User1?

### Available answers

- 7 days
- 30 days
- 90 days
- 48 hours

### Correct answer

**30 days**

### Reasoning

When a Microsoft Entra user is deleted, the object enters a soft-deleted, suspended state for **30 days**. During that period, an administrator can restore the user and its properties, group memberships, roles, licenses, and application assignments.

After 30 days, permanent deletion begins automatically, and the user object can no longer be restored.

### Option comparison

| Period | Outcome |
|---|---|
| 0–30 days after deletion | User remains soft-deleted and can be restored. |
| After 30 days | Permanent deletion begins; the user cannot be restored. |

## Question 23

You have an Azure subscription that contains a user named User1, a resource group named RG1, and a virtual machine named VM1.

You enable a system-assigned managed identity for VM1.

To which identities can you assign the Reports Reader role?

### Available answers

- User1 and RG1 only
- User1 and VM1 only
- User1 only
- User1, RG1, and VM1

### Correct answer

**User1 and VM1 only**

### Reasoning

The **Reports Reader** role is a Microsoft Entra ID role. It can be assigned to Microsoft Entra security principals, including users and service principals.

VM1’s system-assigned managed identity is a service principal in Microsoft Entra ID, so it can receive the Reports Reader role. User1 is also a valid Entra identity. RG1 is an Azure Resource Manager resource group, not a Microsoft Entra identity, so it cannot be assigned an Entra ID role; it can only serve as a scope for Azure RBAC role assignments.

### Option comparison

| Identity | Can assign Reports Reader? | Reason |
|---|---:|---|
| **User1** | **Yes** | User1 is a Microsoft Entra user and a valid Entra role principal. |
| RG1 | No | A resource group is an Azure resource/scope, not a Microsoft Entra identity. |
| **VM1** | **Yes** | VM1’s system-assigned managed identity is a Microsoft Entra service principal. |

## Question 24

You have a Microsoft Entra tenant named contoso.com that contains a user named Ben Smith.

You configure Password protection for contoso.com that includes the following Custom banned passwords settings:

- Enforce custom list: Yes  
- Custom banned password list: Contoso  

Which password can be used by Ben Smith?

### Available answers

- C0nt0s0123
- CONTOSO123
- Conto123so
- FgRs01

### Correct answer

**FgRs01**

### Reasoning

Microsoft Entra Password Protection normalizes passwords before evaluation. It treats matching as case-insensitive and recognizes common substitutions, such as `o` becoming `0`. It also applies substring and fuzzy matching to detect close variants of banned terms.

Because `Contoso` is banned, passwords containing or closely resembling `contoso` are rejected. `FgRs01` does not contain, normalize to, or resemble `contoso`, so it can be used.

### Option comparison

| Password | Allowed? | Reason |
|---|---:|---|
| C0nt0s0123 | No | Normalization converts `0` to `o`, producing a string containing `contoso`. |
| CONTOSO123 | No | Matching is case-insensitive, so `CONTOSO` is detected. |
| Conto123so | No | Fuzzy matching identifies the close variant of `contoso`. |
| **FgRs01** | **Yes** | It does not contain, normalize to, or resemble `contoso`. |

## Question 25

You have an Azure subscription named Sub1.

You plan to deploy a virtual machine scale set named VMSS1 in the East US region. VMSS1 will have 8 instances.

What is the maximum number of availability zones that VMSS1 can use?

### Available answers

- 1
- 2
- 3
- 4

### Correct answer

**3**

### Reasoning

Azure regions that support availability zones provide at least three separate availability zones. A virtual machine scale set can be configured as a zone-spanning deployment and distribute its instances across the selected zones.

Because East US supports three availability zones, VMSS1 can use a maximum of three zones. Having only 8 instances does not prevent using all three zones; Azure can place multiple instances in each zone.

### Option comparison

| Configuration | Availability zones used |
|---|---:|
| Zonal deployment | 1 |
| Zone-spanning deployment | 2 or more, up to the region’s supported maximum |
| **Maximum for VMSS1** | **3** |
