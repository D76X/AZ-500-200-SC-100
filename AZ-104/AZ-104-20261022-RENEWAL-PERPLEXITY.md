# AZ-104 Practice Questions and Answers

Generated from the current study session.

## Questions and Answers

### 1. App Service runtime stack with Docker Container

**Answer:** Publish

**Explanation:** Change Publish from Docker Container to Code. Docker Container apps use the image’s runtime; the managed ASP.NET V4.8 stack requires Code publishing.

### 2. Create additional deployment slots when Standard plan already has five

**Answer:** Scale up the app service plan

**Explanation:** Standard supports five deployment slots per app. Scaling up to a higher tier increases the slot quota; scaling out only adds instances.

### 3. Enable GitHub Actions integration for a Code/Java/Linux web app

**Answer:** Continuous deployment

**Explanation:** Set Continuous deployment to Enable. This lets App Service connect to GitHub and create/manage the GitHub Actions workflow.

### 4. Backup options unavailable for an App Service web app

**Answer:** Scale up the app service plan

**Explanation:** App Service backup requires Basic or higher. Scale up from Free/Shared to Basic or above; scaling out does not change the tier.

### 5. Deploy container5 to VNet4 with SubnetA (Storage endpoint), SubnetB (container1), SubnetC (empty)

**Answer:** SubnetB and SubnetC only

**Explanation:** ACI requires a subnet delegated to Microsoft.ContainerInstance/containerGroups and containing only container groups. SubnetB already qualifies; SubnetC can be delegated. SubnetA has a service endpoint and cannot be used.

### 6. Deploy container1 where Subnet1 has a VM, Subnet2 has App Service, Subnet3 has a container instance

**Answer:** Subnet3 only

**Explanation:** Only Subnet3 is an ACI-delegated subnet. ACI subnets can contain only container groups.

### 7. Deploy Windows/Linux ACI instances in West US and a Windows ACI instance in East US to VNet1 in West US

**Answer:** instance1 and instance2 only

**Explanation:** A container instance using a VNet must be in the same region as the VNet. East US instance3 cannot use West US VNet1.

### 8. Lifecycle management supported storage account kinds: StorageV2, BlobStorage, FileStorage

**Answer:** storage1 and storage2 only

**Explanation:** Blob lifecycle management is supported on StorageV2 and BlobStorage accounts. FileStorage accounts contain Azure Files shares, not blobs.

### 9. Lifecycle management on premium block blob accounts

**Answer:** Supported for deletion, not tiering

**Explanation:** Premium block blob accounts support lifecycle policies for deleting blobs/versions/snapshots, but cannot tier blobs to Hot, Cool, Cold, or Archive.

### 10. File1 created Dec 1; lifecycle: Cool after 3 days, Archive after 5 days; rehydrated to Hot on Dec 10

**Answer:** On December 15

**Explanation:** Changing tier/rehydrating does not update last-modified time. Last modification remains Dec 1, so the 5-day archive rule applies on Dec 15.

### 11. Enable Azure Bastion for VM1 with no public IP

**Answer:** Add a new subnet to VNET1

**Explanation:** Create a dedicated AzureBastionSubnet of at least /26 in VNET1. VM1 does not need a public IP; Bastion connects over its private IP.

### 12. Associate NSG1 with two resources: LB1, NIC1, Subnet1, VM1, VNet1

**Answer:** NIC1 and Subnet1

**Explanation:** NSGs can be associated with network interfaces and subnets only—not VMs, VNets, or load balancers.

### 13. Ensure VM1 accesses storage1 using a private IP; private endpoint unavailable

**Answer:** A service endpoint

**Explanation:** A service endpoint is the next-best option: it secures storage access from the VNet over the Azure backbone, though it does not assign storage1 a private IP like a private endpoint does.

### 14. One Bastion host for four fully peered VNets across West US and East US

**Answer:** 1

**Explanation:** A single Bastion host can protect VMs in its VNet and all peered VNets, including globally peered VNets.

### 15. Maximum instant recovery snapshot retention for a Standard Azure VM backup policy

**Answer:** 5

**Explanation:** Standard policy supports 1–5 days for instant recovery snapshots; Enhanced policy supports up to 30 days.

### 16. View Azure Backup reports for Recovery1

**Answer:** Create an Azure Log Analytics workspace

**Explanation:** Create the Log Analytics workspace first, then configure Recovery1 diagnostics to send Backup resource-specific logs to it.

### 17. Back up Azure managed disk Disk1 with Azure Backup

**Answer:** A Backup vault

**Explanation:** Azure Disk Backup requires a Backup vault. Recovery Services vaults are for VMs, Azure Files, SQL/SAP HANA, and hybrid workloads.

### 18. Add custom VMs to VMSS1 currently using Uniform orchestration

**Answer:** Orchestration mode

**Explanation:** Change to Flexible orchestration. Only Flexible VMSS supports attaching standard/custom Azure VMs; the mode cannot be changed after creation.

### 19. From which resource can you configure fault domains?

**Answer:** Availability set

**Explanation:** You configure the number of fault domains when creating an availability set. Azure assigns each VM in the set to a fault domain.

### 20. What is preserved after resizing VM1 with File1 on C:, File2 on D:, running App1, connected User1?

**Answer:** File1 only

**Explanation:** The OS disk (C:) persists; D: is typically temporary storage and is lost. A resize restarts the VM, so App1 state and User1’s session are lost.

### 21. Maximum availability zones for VMSS1 with 8 instances in East US

**Answer:** 3

**Explanation:** Azure supports up to three availability zones per region; VMSS can span all three.

### 22. Maximum days to restore a deleted Microsoft Entra user

**Answer:** 30 days

**Explanation:** Deleted Entra users remain in a soft-deleted/suspended state for 30 days and can be restored during that window.

### 23. To which identities can Reports Reader be assigned: User1, RG1, VM1?

**Answer:** User1 and VM1 only

**Explanation:** Reports Reader is an Entra ID role and can be assigned to users and service principals, including VM1’s managed identity. Resource groups are scopes, not assignable identities.

### 24. Custom banned password list contains Contoso; which password is allowed: C0nt0s0123, CONTOSO123, Conto123so, FgRs01?

**Answer:** FgRs01

**Explanation:** Entra normalizes substitutions and performs case-insensitive, substring/fuzzy matching. The first three contain or resemble Contoso; FgRs01 does not.
