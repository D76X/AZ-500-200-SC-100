# SC-100-BCDR

# SC-100-06-BCDR

Business Continuity and Disaster Recovery

[SC-100-BCDR-Business Continuity & Distaster Recovery-Collection](https://learn.microsoft.com/en-us/collections/ypzkt3jwn7kr7n)

Learning Path:  
[Architect migration, business continuity, and disaster recovery in Azure-**Microsoft Learn-Path**](https://learn.microsoft.com/en-us/training/paths/architect-migration-bcdr/)  
[AZ-104: Deploy and manage Azure compute resources \- **Learning Path**](https://learn.microsoft.com/en-us/training/paths/az-104-manage-compute-resources/)   
[AZ-104: Monitor and back up Azure resources-**Learning Path**](https://learn.microsoft.com/en-us/training/paths/az-104-monitor-backup-resources/)

Modules:

[AZ-104: Deploy and manage Azure compute resources \- **Learning Path**](https://learn.microsoft.com/en-us/training/paths/az-104-manage-compute-resources/)   
[Schützen Ihrer virtuellen Computer mithilfe von **Azure Backup**\-MLM](https://learn.microsoft.com/de-de/training/modules/protect-virtual-machines-with-azure-backup/)   
[Implementing Microsoft Azure Backup by Gary Grudzinskas \- PluralSight](https://app.pluralsight.com/library/courses/microsoft-azure-backup-implementing/table-of-contents) 

[AZ-104: Monitor and back up Azure resources-**Learning Path**](https://learn.microsoft.com/en-us/training/paths/az-104-monitor-backup-resources/)  
[Protect your virtual machines by using Azure Backup \- **Module**](https://learn.microsoft.com/en-us/training/modules/protect-virtual-machines-with-azure-backup/) 

[Implement DR in Windows Server on-premises and hybrid environments- **Microsoft Learn \- Module**](https://learn.microsoft.com/en-us/training/paths/implement-disaster-recovery-windows-server-premises/) 

Courses:

[Disaster Recovery **Channel Pluralsight**](https://app.pluralsight.com/channels)  
[Microsoft Azure Solutions Architect: Design for Backup and Recovery-**John Savill \- Pluralsight**](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-design-backup-recovery/table-of-contents)  
[**Pluralsight: Implementing Azure Backup for VMs \+ Implementing DR \+ Implementing Azure Update Manager \- Pluralsight \- Matt Allford**](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-implement-workload-management-strategy/table-of-contents)  
[Using Azure for Disaster Recovery Quick Start By A **Cloud Guru Pluralsight**](https://app.pluralsight.com/ilx/using-azure-for-disaster-recovery-quick-start/table-of-content)

Other

[AZ-104-High Availability](https://docs.google.com/document/d/1IUzDFsCkL5IYghgtYxKFYm71cAFQyIhkZ74vVY9Mgvk/edit?tab=t.t4t38v9lkzxk)    
[Azure SQL High Availability and Disaster Recovery \- John Savill](https://www.youtube.com/watch?v=-HTYxfXW3Fo) 

---

# Definitions

[**BCDR-John Savill-Pluralsight-Key Concepts**](https://app.pluralsight.com/ilx/video-courses/clips/c19adaa0-6162-46dd-a8a9-d233ca885bbc)   
[What does **Azure Site Recovery** provide? \- Microsoft Learn](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview#what-does-site-recovery-provide)   
[Azure Traffic Manager (with Azure Site Recovery) \- Microsoft Learn](https://learn.microsoft.com/en-us/azure/site-recovery/concepts-traffic-manager-with-site-recovery)  
[Microsoft Azure Solutions Architect: Design for Backup and Recovery-**John Savill \- Pluralsight**](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-design-backup-recovery/table-of-contents)   
[Design a solution for backup and disaster recovery \- Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/design-solution-for-backup-disaster-recovery/) 

\> Networking Considerations during DR Failover:  
[Failover Networking-**John Savill-Pluralsight**](https://app.pluralsight.com/ilx/video-courses/cbe68a68-7799-4e69-9d7e-3552b1efceea/0e57dc20-a360-4ebb-a374-1181fb3809db/df04f9a7-5970-4db0-8965-a5729556d8cf)   
[About networking in Azure virtual machine disaster recovery](https://learn.microsoft.com/en-us/azure/site-recovery/azure-to-azure-about-networking)   
[Customize networking configurations of the target Azure VM-Microsoft](https://learn.microsoft.com/en-us/azure/site-recovery/azure-to-azure-customize-networking) 

\> Recovery Plans:  
[Recovery Plans-**John Savill-Pluralsight**](https://app.pluralsight.com/ilx/video-courses/cbe68a68-7799-4e69-9d7e-3552b1efceea/0e57dc20-a360-4ebb-a374-1181fb3809db/bd7ea43b-502f-493d-b08d-7667965544f9)   
[About Recovery Plans-Microsoft](https://learn.microsoft.com/en-us/azure/site-recovery/recovery-plan-overview)   
[Create and customise recovery plans](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-create-recovery-plans) 

**RTO: These are the Recovery Time Objective** 

RTO is the goal your organisation sets for the maximum length of time it should take to restore normal operations following an outage or data loss.

**RPO: Recovery Point Objective** 

RPO is your goal for the maximum amount of data the organisation can tolerate losing.

**RLO: Recovery level objective** 

RLO is the objective that defines the **granularity** with which you must be able to recover data — whether you must be able to recover the whole farm, Web application, site collection, site, list or library, or item, databases, etc.

Examples:

\> Example 1:

[What is the commitment of blob storage RTO, RLO and RPO?](https://learn.microsoft.com/en-us/answers/questions/440593/what-is-the-commitment-of-blob-storage-rto-rlo-and)  
[Understanding Azure storage redundancy offerings](https://techcommunity.microsoft.com/blog/azurestorageblog/understanding-azure-storage-redundancy-offerings/1431700) 

- Typically, RTO \< 1 hour with no SLA  
- Typically, RPO \< 15 min with no SLA

\> Example 2:

[What does **Azure Site Recovery** provide? \- Microsoft Learn](https://learn.microsoft.com/en-us/azure/site-recovery/site-recovery-overview#what-does-site-recovery-provide) 

ASR RTO and RPO targets: 	

ASR keeps recovery time objectives (RTO) and recovery point objectives (RPO) within organizational limits. It provides continuous replication for Azure VMs and VMware VMs, and replication frequency as low as 30 seconds for Hyper-V. 

**You can reduce RTO further by integrating with [Azure Traffic Manager (with Azure Site Recovery)](https://learn.microsoft.com/en-us/azure/site-recovery/concepts-traffic-manager-with-site-recovery)**.

---

# [Vergleich von Azure Backup und Azure Site Recovery](https://learn.microsoft.com/de-de/training/modules/protect-virtual-machines-with-azure-backup/2-azure-backup-features-scenarios)

Sowohl **Azure Backup** als auch **Azure Site Recovery** zielen darauf ab, das System stabiler gegenüber Fehlern und Fehlern zu machen, **aber sie verwenden zwei verschiedene Ansätze**. 

**Das Hauptziel von AB** ist das Verwalten von Kopien **zustandsbehaftet**er Daten ist, mit denen Sie in der Zeit zurückgehen können. Sicherungen werden im Fall von **versehentlichen Datenverlusten**, **Datenbeschädigungen** oder **Angriffen über [Ransomware](https://learn.microsoft.com/en-us/collections/rjrqh2t0e7dy2)** verwendet.

**Azure Site Recovery** repliziert die Daten jedoch nahezu in Echtzeit und **ermöglicht ein Failover**.  
Insofern können Sie Verfügbarkeitszonen nutzen, wenn Probleme wie **Netzwerk- oder Stromausfälle** auftreten. Bei **Notfällen, die eine ganze Region** betreffen, beispielsweise Natur**katastrophen**, wird Site Recovery verwendet. 

Darüber hinaus hängt die Wahl eines Wiederherstellungsansatzes von der [**Kritikalität**](https://www.dwds.de/wb/Kritikalit%C3%A4t) der Anwendung, den Anforderungen an den **Wiederherstellungspunkt (RPO)** und die **Wiederherstellungszeit (RTO)** **sowie von den Kosten** ab.

---

# Azure Backup

[**Übung**: Sichern eines virtuellen Azure-Computers-**Microsoft Learn**](https://learn.microsoft.com/de-de/training/modules/protect-virtual-machines-with-azure-backup/4-exercise-back-up-azure-virtual-machine)  
[Schützen Ihrer virtuellen Computer mithilfe von **Azure Backup**\-MLM](https://learn.microsoft.com/de-de/training/modules/protect-virtual-machines-with-azure-backup/)   
[An overview of Azure VM backup](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction) 

## MARS vs MABS

[Azure stack HCI Backup MABS or MARS](https://techcommunity.microsoft.com/discussions/azurestack/azure-stack-hci-backup-mabs-or-mars/3248883)   
[**Azure Backup architecture and components**](https://learn.microsoft.com/en-us/azure/backup/backup-architecturev)

MARS agent backs up data **directly** to Azure, that is to recovery services vault. However, MABS backs up the data to the local storage first and then the MARS agent installed on the MABS server backups the local storage to the vault.

**MARS agent is easy to install and manage**. Whereas, **MABS is a little more complex** and used to set up backups for environments that run multiple workloads, for example: VMware & Hyper-V, SQL Serve, etc.

[MARS and MABS backup methods use the same backup process?](https://learn.microsoft.com/en-us/answers/questions/820006/mars-and-mabs-backup-method-use-the-same-backup-pr)

Microsoft Azure offers **Azure Backup services for different types of workloads**. For example, If you want to backup **only Azure VMs**, you can leverage **Azure Backup for VMs**. Likewise, there are **other Azure backup solutions** for backing up your **on-premise Windows machines**; you can use **Azure backup agent**. 

However, if you have an environment with multiple types of workloads, SQL, Windows Machines, Linux VMs, VMware VMs, you can opt for **Microsoft Azure Backup Server (MABS)**.

[Install and upgrade Azure Backup Server-(**MABS**)](https://learn.microsoft.com/en-us/azure/backup/backup-azure-microsoft-azure-backup) 

With Azure Backup Server, you can protect application workloads, such as Hyper-V VMs, VMware VMs, Azure Local VMs, Microsoft SQL Server, SharePoint Server, Microsoft Exchange, and Windows clients from a single console.

[Microsoft Azure Recovery Services (**MARS**) agent for Azure Backup](https://learn.microsoft.com/en-us/azure/backup/backup-azure-about-mars) 

Azure Backup uses MARS agent to back up and recover files, folders, and the volume or system state from an on-premises computer to Azure.

---

## [Backup Best Practices & Maintenance](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction#best-practices)

If you're restoring VMs from a single vault, we highly recommend **using different general-purpose v2 storage accounts** **to avoid throttling**. For example, **each VM must have a different storage account**.

For example, if 10 VMs are restored, use 10 different storage accounts.

[Implementing Microsoft Azure Backup by Gary Grudzinskas-PluralSight-Maintaining Azure Backup](https://app.pluralsight.com/ilx/video-courses/0e909a92-fd9e-47c8-b94a-82ecb84d7fdf/edabeedb-e8d7-4566-aa92-0ea60830274a/826a5b6c-ae47-4693-a1ed-44de5b22ec89)

* Enable CRR   
* Enable MFA  
* Enable Soft Delete  
* Enable Security PIN  
* Download an updated version of the Azure Back Agent

---

### Deleting a Recovery Service Vault

[Implementing Microsoft Azure Backup by Gary Grudzinskas-PluralSight-Deleting a Recovery Service Vault](https://app.pluralsight.com/ilx/video-courses/0e909a92-fd9e-47c8-b94a-82ecb84d7fdf/edabeedb-e8d7-4566-aa92-0ea60830274a/d6f7f32f-e288-4662-9c4e-593e147940e4) 

---

## Backup Cost Optimisation

Optimise [your data protection costs with Azure Backup-Microsoft Azure](https://www.youtube.com/watch?v=4ocUnsRHrC4)   
[Azure Backup Pricing-Gary Grundzinskan-**Pluralsight**](https://app.pluralsight.com/ilx/video-courses/0e909a92-fd9e-47c8-b94a-82ecb84d7fdf/edabeedb-e8d7-4566-aa92-0ea60830274a/3776363f-19d4-4666-a8ab-13d15234b765) 

---

## DPM: System Centre Data Protection Manager (DPM)

[Support matrix for backup with Microsoft Azure Backup Server or System Center DPM](https://learn.microsoft.com/en-us/azure/backup/backup-support-matrix-mabs-dpm)  
[Microsoft System Centre documentation](https://learn.microsoft.com/en-us/system-center/)   
[System](https://www.microsoft.com/en-us/system-center) Centre   
[System Centre 2025](https://techcommunity.microsoft.com/blog/systemcenterblog/announcement-system-center-2025-is-here/4138510)   
[A Guide to Different Microsoft Azure Backup Options](https://petri.com/guide-different-microsoft-azure-backup-options/) 

System Centre DPM is an enterprise solution that configures, facilitates, and manages backup and recovery of enterprise machines and data. It's part of the System Centre suite of products.

* MARS: The Microsoft Azure Recovery Services agent that is deployed onto a machine that you want to back up directly to Azure.  
    
* DPM: Microsoft System Centre Data Protection Manager is an on-premises backup server that will perform disk-to-disk-to-cloud backup.  
    
* MABS: The Microsoft Azure Backup Server is also an on-premises backup server that you can get from Microsoft to perform disk-to-disk-to-cloud backup.

---

# [MUA: Multi-user authorization using Resource Guard](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept?tabs=recovery-services-vault) 

[Configure Multi-user authorization using Resource Guard in Azure Backup](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization?tabs=azure-portal&pivots=vaults-recovery-services-vault) 

[**Case study 01**: Design solutions that align with **security best practices** and priorities-**LP-1**](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/) 

Implementieren Sie die [Mehrbenutzerautorisierung (Multi-User Authorization, MUA)](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept?tabs=recovery-services-vault) für kritische Vorgänge in Recovery Services- und Backup-Tresoren. **MUA für Azure Backup stellt mithilfe von Resource Guard** sicher, dass kritische Vorgänge wie: 

* das Deaktivieren des **vorläufigen Löschens**  
* das Beenden und Löschen von Sicherungen   
* eine Verkürzung der Aufbewahrung von Sicherungsrichtlinien 

nur ausgeführt werden, wenn sie durch mehrere Benutzer autorisiert wurden.

---

# Network Connection between Backups and Workloads

[**Case study 01**: Design solutions that align with **security best practices** and priorities-**LP-1**](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/) 

Stellen Sie sicher, dass die Netzwerkverbindung zwischen Sicherungsdiensten und Workloads sicher ist. 

1. Im Falle einer Azure-VM passieren die Daten während der Übertragung das Azure-Backbonenetzwerk.   
     
2. Für **Azure Storage müssen** Sie den Zugriff auf Azure-Dienste in der Liste der vertrauenswürdigen Dienste explizit zulassen.   
     
3. **Für lokale Workloads**, die durch den Microsoft Azure Recovery Services-Agent (MARS) oder Microsoft Azure Backup Server (MABS) geschützt sind, können Sie **das Microsoft-Peering für ExpressRoute oder Virtual Private Network (VPN) verwenden**, um sich mit Azure zu verbinden. **Das private Peering unterstützt private Endpunkte**.

---

# [Backup Explorer: Monitor your backups](https://learn.microsoft.com/en-us/azure/backup/monitor-azure-backup-with-backup-explorer)

[**Case study 01**: Design solutions that align with **security best practices** and priorities-**LP-1**](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/) 

Regularly monitoring backups. Monitoring solutions, such as Backup Explorer, help identify systems that aren't protected by Azure Backup. They also facilitate monitoring backup items, backup jobs, and policies.

---

# [CMKs: Encrypt backup data by using customer-managed keys](https://learn.microsoft.com/en-us/azure/backup/encryption-at-rest-with-cmk?tabs=portal#configuring-a-vault-to-encrypt-using-customer-managed-keys?azure-portal=true) 

The encryption key that you use for encrypting backups **might be different** from the one that you use for the source. An AES 256-based **data encryption key (DEK)** helps protect the data. Your **key encryption keys (KEKs)**, in turn, help **protect the DEK**. 

You have full control over the data and the keys.

---

# [Restore virtual machine data](https://learn.microsoft.com/en-us/training/modules/protect-virtual-machines-with-azure-backup/5-restore-virtual-machine-data)

Restore options:

1. Create a new VM from a restore point with the same setup as the original VM.  
     
2. **Restore** a disk and use it to create a new VM with **new settings**.  
     
3. **Replace** the disk of an existing VM (and take a snapshot of the VM.)  
     
4. **CRR** ([**Cross Region Restore**](https://azure.microsoft.com/en-us/blog/cross-region-restore-crr-for-azure-virtual-machines-using-azure-backup/)) creates a **new identical VM** or **restores** to a **new** VM in the secondary paired region from a vault with the Cross Subscription Restore property enabled.   
     
5. **CZR** ([**Cross Zonal Restore**](https://jpigott.com/2022/12/azure-cross-zonal-restore-for-azure-virtual-machines/)) to restore a VM or zone-pinned disks to different available zones from a vault with Zonal-redundant storage (ZRS) enabled.  
     
6. [**Selective disk backup**](https://learn.microsoft.com/en-us/azure/backup/selective-disk-backup-restore) (**SDB**) to selectively back up a subset of the data disks that are attached to your VM. This is supported both for **Enhanced Policy** as well as **Standard Policy**.   
   

---

## Zone pinned Azure VM Disaster Recovery

[Disaster recovery of zone-pinned Azure Virtual Machines to another region](https://azure.microsoft.com/en-us/blog/disaster-recovery-of-zone-pinned-azure-virtual-machines-to-another-region/)  
[Protect your virtual machines by using Azure Backup-Restore virtual machine data](https://learn.microsoft.com/en-us/training/modules/protect-virtual-machines-with-azure-backup/5-restore-virtual-machine-data)   
[What are availability zones?](https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview?tabs=azure-cli) 

You can now replicate and failover zone pinned virtual machines to other regions within a geographic cluster using Azure Site Recovery. 

Configuring DR for your zone-pinned VMs is very simple. Browse to your VM, select Disaster Recovery, select the target region of your choice, review settings, and click Enable replication.

If the target region supports availability zones, you can configure your target VM to be deployed as a zone-pinned VM. If not, you can configure the target VM to be deployed as a single instance or in an availability set. 

---

## [CRR:](https://azure.microsoft.com/en-us/blog/cross-region-restore-crr-for-azure-virtual-machines-using-azure-backup/) Cross-Region [Restore for Azure Virtual Machines using Azure Backup](https://azure.microsoft.com/en-us/blog/cross-region-restore-crr-for-azure-virtual-machines-using-azure-backup/)

Azure Backup uses Recovery Services Vault to hold customers’ backup data and offers local and geo-redundancy. To ensure the durability of backed-up data, Azure Backup defaults storage settings to geo-redundancy, and the backed-up data in the primary region is geo-replicated to an Azure-paired secondary region. However, the data replicated to the secondary region is available to restore in the secondary region only if Azure declares a disaster in the primary region. With the introduction of this new feature, the customers who opt-in for this feature can initiate restores in the secondary region at any time.

[Implementing Microsoft Azure Backup by Gary Grudzinskas-PluralSight-Enable-CRR-MFA-SoftDelete-PIN-DownloadAgentUpdates](https://app.pluralsight.com/ilx/video-courses/0e909a92-fd9e-47c8-b94a-82ecb84d7fdf/edabeedb-e8d7-4566-aa92-0ea60830274a/826a5b6c-ae47-4693-a1ed-44de5b22ec89)

---

## [CZR: Azure  Cross Zonal Restore for Azure Virtual Machines](https://jpigott.com/2022/12/azure-cross-zonal-restore-for-azure-virtual-machines/)

[Azure Cross Zonal Restore for Azure Virtual Machines](https://jpigott.com/2022/12/azure-cross-zonal-restore-for-azure-virtual-machines/)

If your design requires the ability to restore virtual machines to a specific Azure Availability Zone, you will need the new feature that has become generally available called “Azure Cross Zonal Restore”. This feature requires that the Azure recovery services vault is configured to use zonal-redundant storage (ZRS). 

The default on a new recovery services vault is to use geo-redundant storage (GRS).

[Can I restore an Azure **zone-pinned** Virtual Machine in a different zone?](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vm-backup-faq#can-i-restore-an-azure-zone-pinned-virtual-machine-in-a-different-zone)

Yes, Cross Zonal Restore now allows you to restore Azure zone pinned VMs to a different available zone using a recovery point in a vault with Zonal-redundant storage (ZRS) enabled as per Azure role-based access control (Azure RBAC) rules. 

It's also supported by vaults with Cross Region Restore (CRR).

[Can I restore an Azure **non-zone pinned** Virtual Machine in a different zone?](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vm-backup-faq#can-i-restore-an-azure-non-zone-pinned-virtual-machine-in-a-different-zone)

Yes, Cross Zonal Restore now allows you to restore Azure non-zone pinned VMs to any available zones using a recovery point in a vault with Zonal-redundant storage (ZRS) enabled as per Azure role-based access control (Azure RBAC) rules.

[Does Cross Zonal Restore support all Azure VM?](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vm-backup-faq#does-cross-zonal-restore-support-all-azure-vm) \> No, it's unsupported for Encrypted Azure VMs.

[Can I use Azure VM snapshots to restore in another zone?](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vm-backup-faq#can-i-use-azure-vm-snapshots-to-restore-in-another-zone) \> No, CZR is unsupported from snapshot restore.

---

## [SDB: Selective disk backup](https://learn.microsoft.com/en-us/azure/backup/selective-disk-backup-restore)

[Azure Selective Disk Backup & Restore Step-by-Step](https://www.youtube.com/watch?v=75LZCe7VgIo)

Azure Backup supports backing up all the disks (operating system and data) in a VM together using the virtual machine backup solution. **SDB** backup and restore functionality, allows to back up a subset of the data disks in a VM.

This is supported by **Enhanced Policy** as well as **Standard Policy**. 

---

## [Restore an encrypted virtual machine](https://learn.microsoft.com/en-us/training/modules/protect-virtual-machines-with-azure-backup/5-restore-virtual-machine-data)

[Encryption of Azure VM backups](https://learn.microsoft.com/en-us/azure/backup/backup-azure-vms-introduction#encryption-of-azure-vm-backups) 

1. Azure VMs with Azure Backup are encrypted at rest with **Storage Service Encryption (SSE)**.   
2. **Azure Backup can also back up Azure VMs encrypted using Azure Disk Encryption (ADE)**.

**Storage Service Encryption (SSE):**

With SSE, Azure Storage provides encryption at rest by automatically encrypting data before storing it and Azure Storage also decrypts data before retrieving it.  

Azure Storage supports two types of Encryption:

1. SSE with platform-managed keys.  
2. SSE with customer-managed (**RSA**) keys ([**CMK**](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption#customer-managed-keys)) requires the use of **Azure Key Vault** or [Azure Key Vault Managed HSM](https://learn.microsoft.com/en-us/azure/key-vault/managed-hsm/overview).

[Restore encrypted Azure virtual machines](https://learn.microsoft.com/en-us/azure/backup/restore-azure-encrypted-virtual-machines) 

---

# Azure Business Continuity Center

# Azure Business Continuity Center

[What is Azure Business Continuity Centre? \- Microsoft  Azure](https://www.youtube.com/watch?v=t7RDJ0MYtAc) 

[Was ist Azure Business Continuity Center?](https://learn.microsoft.com/de-de/azure/business-continuity-center/business-continuity-center-overview) 

ABC bietet eine einheitliche Erfahrung mit konsistenten Ansichten, nahtloser Navigation und unterstützenden Informationen, um einen ganzheitlichen Überblick über den Bestand zu erhalten, der für Ihre Geschäftskontinuität erforderlich ist. Außerdem sorgt ABC für eine bessere Auffindbarkeit, um Kernaktivitäten zu erledigen.

Die Integration in das Azure Business Continuity Center ermöglicht es Ihnen, **Sicherungen** im großen Stil zu **steuern, zu überwachen, zu betreiben und zu analysieren**.

# Storage Account BCDR

# Storage Account Disaster Recovery

[Azure storage disaster recovery planning and failover](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#plan-for-failover)  
[How **customer-managed planned failover** (preview) works](https://learn.microsoft.com/en-us/azure/storage/common/storage-failover-customer-managed-planned?tabs=grs-ra-grs)   
[How **customer-managed (unplanned) failover** works](https://learn.microsoft.com/en-us/azure/storage/common/storage-failover-customer-managed-unplanned?tabs=grs-ra-grs)   
[**Microsoft-managed** failover](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#microsoft-managed-failover)

[Data Loss & Inconsistencies after failover](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#anticipate-data-loss-and-inconsistencies)  
[Check the **Last Sync Time (LST) property** for a storage account](https://learn.microsoft.com/en-us/azure/storage/common/last-sync-time-get?tabs=azure-powershell)   
[File consistency for **Azure Data Lake Storage \- Hierarchical Namespace Enabled Storage**](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#file-consistency-for-azure-data-lake-storage) 

[**Azure Storage Actions**:  Cross-region disaster recovery and business continuity](https://learn.microsoft.com/en-us/azure/reliability/reliability-storage-actions#cross-region-disaster-recovery-and-business-continuity) 

Azure Account BCDR vs Azure Storage Migration  
[Azure Storage migration overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-migration-overview) 

[Failover IS NOT account migration\!](http://v)  
Storage account failovers are a temporary solution used to develop and test your disaster recovery (DR) plans, or to recover from a service outage. Failover shouldn't be used as part of your data migration strategy. For information about how to migrate your storage accounts, see Azure Storage migration overview.

[Copy Data as a Failover Alternative](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#copying-data-as-a-failover-alternative)

You can maintain high availability by configuring applications to **use a storage account configured for read access to a secondary region**. However, if you prefer not to fail over during an outage within the primary region, **you can manually copy your data as an alternative**. Tools such as **AzCopy** and **Azure PowerShell** enable you to copy data from your storage account in the affected region to another storage account in an unaffected region. 

After the copy operation is complete, you can reconfigure your applications to use the storage account in the unaffected region for both read and write availability.

---

[Design for high availability of Azure Storage Accounts](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#design-for-high-availability)

---

 

## Azure Blob Storage

[Store business-critical blob data with immutable storage in a write once, read many (WORM) state](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview).

[Overview of Azure Blob backup](https://learn.microsoft.com/en-us/azure/backup/blob-backup-overview?tabs=operational-backup)  
[Übersicht über die Sicherung von Azure-Blobs](https://learn.microsoft.com/de-de/azure/backup/blob-backup-overview?tabs=operational-backup) 

\> **Operative Sicherung (Operational Backup):**

Es verwendet Blobplattformfunktionen, um Ihre Daten zu schützen und eine Wiederherstellung nach Bedarf zu ermöglichen. Die operative Sicherung wird auf Ebene des Speicherkontos konfiguriert und verwaltet und gilt für alle Blockblobs im Speicherkonto. In der **Sicherungsrichtlinie** kann eine **maximale** Aufbewahrungsdauer von **360 Tagen** bzw. der entsprechenden Anzahl von ganzen **Wochen (51)** oder **Monaten (11)** definiert werden.

* [Point-in-Time-Wiederherstellung für Blockblobs](https://learn.microsoft.com/de-de/azure/storage/blobs/point-in-time-restore-overview) (Zeitpunktwiederherstellung)


Dafür werden die Features **vorläufiges Löschen**, **Änderungsfeed** und **Blobversionsverwaltung** verwendet, um Daten für den angegebenen Zeitraum aufzubewahren.  
 

* Löschsperre

Eine Löschsperre verhindert, dass das Speicherkonto versehentlich durch nicht autorisierte Benutzer gelöscht wird.

\> **Tresorsicherung (Vaulted backup):**

Es wird die Plattformfunktion auf Containerebene der **Objektreplikation** verwendet, um Daten in den Sicherungstresor zu kopieren. Die Blockblobs alle dem Blob zugeordneten Versionen sowie die Metadaten und Eigenschaften werden **asynchron** zwischen einem Quellspeicherkonto und einem Zielspeicherkonto **kopiert**.

---

## Azure Files

[How Azure Files protects against ransomware and accidental data loss \- Microsoft Azure](https://www.youtube.com/watch?v=TOHaNJpAOfc&t=4s)   
[About Azure Files backup](https://learn.microsoft.com/en-us/azure/backup/azure-file-share-backup-overview?tabs=snapshot)   
[Azure File Document Retention](https://learn.microsoft.com/en-us/answers/questions/1426331/azure-file-document-retention) 

---

# Azure SQL Server Disaster Recovery

Azure SQL Server Disaster Recovery

[Azure SQL High Availability and Disaster Recovery \- **John Savill**](https://www.youtube.com/watch?v=-HTYxfXW3Fo)  
[Disaster recovery guidance \- Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/disaster-recovery-guidance?view=azuresql)  

---

[Microsoft Azure Solutions Architect: Implement a Workload Management Strategy \- AZ303 \- Pluralsight](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-implement-workload-management-strategy/table-of-contents)  
[by Matt Allford](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-implement-workload-management-strategy/table-of-contents)

- [Implementing Azure Backup for VMs](https://app.pluralsight.com/ilx/video-courses/clips/4be8d6d6-0dbf-4665-b121-f791c48268df)  
- [Implementing Disaster Recovery](https://app.pluralsight.com/ilx/video-courses/clips/381189d1-1ee6-46fe-8dbb-8aa665720829)  

---

# Azure File Sync BCDR

# Azure File Sync

[Disaster recovery best practices with Azure File Sync](https://learn.microsoft.com/en-us/azure/storage/file-sync/file-sync-disaster-recovery-best-practices#geo-redundancy)   
[How Azure Files can help protect against ransomware and accidental data loss \- Microsoft Azure](https://www.youtube.com/watch?v=TOHaNJpAOfc&t=615s) 

[Azure Files Provisioned v2 Overview \- **John Savill**](https://www.youtube.com/watch?v=dyqQkheaHYg)   
[Azure Files AD Authentication Integration \- **John Savill**](https://www.youtube.com/watch?v=LWKkva4ksdg&t=1s) 

---

[What is Azure File Sync?](https://learn.microsoft.com/en-us/azure/storage/file-sync/file-sync-introduction)

Azure File Sync enables you to centralise your organization's file shares in Azure Files, while keeping the flexibility, performance, and compatibility of a Windows file server. While some users might opt to keep a full copy of their data locally, Azure File Sync additionally has the ability to transform Windows Server into a quick cache of your Azure file share. You can use any protocol that's available on Windows Server to access your data locally, including SMB, NFS, and FTPS. You can have as many caches as you need across the world.

[Azure Files Sync \- BCDR](https://learn.microsoft.com/en-us/azure/storage/file-sync/file-sync-introduction#business-continuity-and-disaster-recovery)

Azure File Sync is backed by Azure Files, which offers several redundancy options for highly available storage. Because Azure contains resilient copies of your data, your local server becomes a disposable caching device. You can recover from a failed server by adding a new server to your Azure File Sync deployment. Rather than restoring from a local backup, you provision another Windows Server, install the Azure File Sync agent on it, and then add it to your Azure File Sync deployment. Azure File Sync downloads your file namespace before downloading data, so that your server can be up and running as soon as possible. For even faster recovery, you can have a warm standby server as part of your deployment, or you can use Azure File Sync with Windows Clustering.

---

# VM BCDR

# Virtual Machine BCDR and High Availability

[Microsoft Azure Solutions Architect: Implement a Workload Management Strategy by **Matt Allford** \-](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-implement-workload-management-strategy/table-of-contents) 

[**Pluralsight: Implementing Azure Backup for VMs \+ Implementing DR \+ Implementing Azure Update Manager**](https://app.pluralsight.com/library/courses/microsoft-azure-solutions-architect-implement-workload-management-strategy/table-of-contents)

[Backup and restore options for virtual machines in Azure](https://learn.microsoft.com/en-us/azure/virtual-machines/backup-recovery)   
[Availability options for Azure Virtual Machines](https://learn.microsoft.com/en-us/azure/virtual-machines/availability) 

# The 3-2-1 rule

# The 3-2-1 Rule

[How Azure Files can help protect against ransomware and accidental data loss \- Microsoft Azure](https://www.youtube.com/watch?v=TOHaNJpAOfc&t=615s) 

The "3-2-1" backup rule is a best practice for data protection, o **minimise the risk of data loss due to various failures**, including hardware issues, theft, or natural disasters: 

1. **maintaining 3 copies of your data**,   
2. storing them on 2 different media,   
3. keeping 1 copy offsite. 

---

