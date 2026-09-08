# SC-100-Case Study-01

[SC-100-Case Studies-Collection](https://learn.microsoft.com/en-us/collections/86mpuztw7go2p)   
[SC-100: Design solutions that align with **security best practices** and priorities \- **Learning Path**](https://learn.microsoft.com/en-us/training/paths/sc-100-design-solutions-best-practices-priorities/) 

[**Case study 01**: Design solutions that align with **security best practices** and priorities \- **LP-1**](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/)   
[**SC-100-Case Study 01**: Konzeptionelle exemplarische Vorgehensweise \- **Introduction Summary Video**](https://learn.microsoft.com/de-de/training/modules/case-study-design-solutions-security-best-practices-priorities/4-conceptual-walkthrough)  
[SC-100-Case Study 01: Technische exemplarische Vorgehensweise \- **Video**](https://learn.microsoft.com/de-de/training/modules/case-study-design-solutions-security-best-practices-priorities/5-technical-walkthrough) 

[iSCSI Target Server Overview](https://learn.microsoft.com/en-us/windows-server/storage/iscsi/iscsi-target-server) 

[**Microsoft Purview: Create** and configure **retention policies**](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=teams-retention) 

[**Azure Blob Storage** \- Store business-critical blob data with immutable storage in a **write once, read many** **(WORM) state**](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#time-based-retention-policies)   
[Time-based retention policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#time-based-retention-policies)  
[Legal Hold Policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#legal-holds)  

[**Azure Backup**: Features und Szenarios](https://learn.microsoft.com/de-de/training/modules/protect-virtual-machines-with-azure-backup/2-azure-backup-features-scenarios) 

---

# Summary

## Current State

**The current state** of Contoso’s environment exemplifies **the traditional, on-premises architecture**, with

* **file, messaging, and backup servers** hosted within the customer's own datacenter.   
    
* **File servers** **running Windows Server 2016** store various **business data**, including **confidential** **customer records** and contracts, **frequently updated** marketing information, and **large amounts of historical content** that **must be retained for compliance purposes**.   
    
* Customer records and contracts are created using Microsoft Office products, marketing information is typically stored in the Adobe Acrobat format, and historical content is commonly compressed as ZIP-based archives.  
    
* **Local** and **Storage** **iSCSI** (Internet Small Computer Systems Interface **/aɪˈskʌzi/** ) **attached devices** are **close to reaching capacity**.  
    
* **Backups** are implemented by using several **tape libraries**, which are approaching **end-of-life**.  
    
* **Backups** are **unreliable** and **inefficient** due to frequently **failing restores** and **data corruption** issues, and to remediate these issues, they maintain multiple copies across different file servers, which requires **additional capacity**.  
    
* **Personal Devices** **for VPN connectivity to the main office** by staff is a **security concern** due to **lack of oversight of the remote devices**. (refer to **Incident-1**)

**Incident-1**

**Malware** was transmitted **from a Personal Device** and then **through** the **on-premises Microsoft Exchange** email. The malware **compromised** one **Privileged Active Directory Domain Services (AD DS) account** and **attempted to encrypt data** **on one of the file servers**. 

The attempt was detected and blocked by the **Microsoft Defender Antivirus running on all** the firm’s Windows computers. 

The incident prompted the **CIO to consider cloud-based data storage and protection**.

## Requirements

1. Minimise the footprint of on-premises **storage** infrastructure.  
2. Minimise the footprint of on-premises **backup** infrastructure.  
3. Ensure that the data protection solution addresses the need for short-term and long-term backups.  
4. Ensure that the DPS addresses and supports the seven-year retention required by compliance.  
5. Implement continuous security protection and monitoring of remote devices.  
6. Control access is based on a wide range of conditions, including the state of users' devices and dynamically evaluated risk, relying on heuristics and globally collected security-related telemetry.  
7. Protect backups against accidental or malicious deletions.

## Design Questions

1. How would you approach creating a business resiliency plan for Contoso based on the Cloud Adoption Framework?  
2. Given the identified risks from the scenario, are there any opportunities to achieve better security integration with business processes using the Cloud Adoption Framework?  
3. Which Microsoft 365 services would allow Contoso to increase its visibility into and traceability of cyberattacks affecting on-premises and cloud assets?  
4. Which Microsoft Azure services would allow Contoso to increase visibility into and traceability of cyberattacks affecting on-premises and cloud assets?  
5. What changes in the operational procedures would you recommend to Contoso to mitigate the potential impact of ransomware?  
6. What would you recommend to Contoso to implement endpoint protection?  
7. What infrastructure elements would you prioritize for system hardening to mitigate the ransomware risk for Contoso?

---

## Requirements Analysis

### Requirement 1

Minimize the footprint of on-premises storage infrastructure.  
Minimise the footprint of on-premises **storage** infrastructure.

This requirement can be fulfilled by shifting the business data to cloud storage.   
However, the specific cloud storage service depends on the type of data. 

For each type of data: 

* How will the data be accessed?  
    
  *  How frequently will the data be read, written or updated


* What are the security requirements?   
    
  * What kind of information is it?   
  * Is it confidential or not?  
      
* What retention policy should be applied to the data?  
* What level of protection against accidental or malicious attacks should be applied to the data?

**The first step** is, therefore, to **classify** the business data:

1. **Confidential** customer records and contracts in the **Microsoft Office** format  
2. **Frequently updated** marketing information in the **Adobe Acrobat** format (**non-confidential**)  
3. **Large amounts of historical content in the ZIP  format** that **must be retained** for compliance.

**The second step** is to evaluate the options of cloud storage services that may be suitable for each class and the corresponding demands:

* **SharePoint Online** and **OneDrive** for confidential customer records and contracts in the Microsoft Office format.  
    
* **Azure Files** for **frequently updated** marketing information in the Adobe Acrobat format.  
    
* **Azure Blob Storage** to **archive large amounts of historical content** in the ZIP and retain it for compliance. 

All these services offer some features to **prevent data loss**, either by accident or as a consequence of an attack such as a **ransomware attack**. 

Refs:

[**Microsoft 365-Ransomware protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection)   
[Microsoft 365-**SharePoint and OneDrive Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#sharepoint-and-onedrive-protection)

\> [Domain 1: **Tenant level controls**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#domain-1-tenant-level-controls)

The first domain is the people that make up your organisation, and the infrastructure and services owned and controlled by your organisation. The following features in Microsoft 365 **are on by default**, or can be configured, **to mitigate the risk and recover from** an attack that has compromised assets in this domain.

[**SharePoint and OneDrive (Tenant Level) Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#sharepoint-and-onedrive-protection) is a built-in feature that helps protect **against ransomware attacks**.

1. **Versioning**:   
   **If the ransomware edits and encrypts a file,** a previous version of the file can be recovered. Versioning can be configured to retain a minimum of 500 versions.  
     
2. **Recycling bin**:  
   **If the ransomware creates a new encrypted copy of the file**, **and deletes the old file**, customers have 93 days to restore it from the recycle bin.

3. **Preservation Hold Library (PHL)**:  
   **When users suspect a file may have been compromised, tampered with or edited,** they can investigate it by comparing it with the **versions copied to the PHL that exist as separate items.** The file can be restored within 30 days, subject to retention settings. 

[**Exchange Online (Tenant Level) Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#exchange-online) 

Items in a mailbox can be recovered upon inadvertent or malicious premature deletion within 14 days by default, configurable up to 30 days. It also **by default** **real-time** **scans incoming email and attachments, and those containing ransomware or other known or suspected malware are deleted.** Notifications and their setup are also available.

Additional customer configurations of retention policies allow:

- retentions of 1 year up to 10+ years  
- **copy on write protection**  
- **retention policy to be locked and become immutable.**

[**Microsoft Teams (Tenant Level) Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#teams) 

Teams chats are stored within **Exchange Online** user mailboxes and files are stored in either **SharePoint** or **OneDrive**. Microsoft Teams data is protected by the controls and recovery mechanisms available in these services.

[**\> Domain 2: Microsoft Service level control**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#domain-2-service-level-controls)

The second domain is the people that make up Microsoft, the organisation, and the corporate infrastructure owned and controlled by Microsoft to execute the organisational functions of a business. **Microsoft's approach to securing its corporate estate is [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/), implemented using our own products and services.**

[**SharePoint and OneDrive (Service Level) Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#sharepoint-and-onedrive-protection-1)

* Versioning: as described in Tenant Level Protection  
* Recycle bin: as described in Tenant Level Protection \+  **there's a 14-day window where Microsoft can still recover the data. After this window, the data is permanently deleted.**

[**Teams (Service Level) Protection**](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#teams-1) is the same as its Tenant Level Protection.

**\> [Domain 3: Developers & service infrastructure](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#domain-3-developers--service-infrastructure)**

This domain is the people who develop and operate the Microsoft 365 service, the code, and infrastructure that delivers the service, and the storage and processing of your data. 

**Microsoft 365 platform** mitigates the risks in this domain focusing on these **areas** and the corresponding applied **design principles**:

* [Continuous assessment and validation of the security posture](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#continuous-assessment-and-validation-of-the-security-posture) of the service. The design applied principles are **least privilege** with **JIT** and **JEA, RBAC.**  
* Building [tools and architecture that protect the service from compromise](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#tools-and-architecture-that-protect-the-service). The [Microsoft's Security Development Lifecycle (SDL)](https://learn.microsoft.com/en-us/compliance/assurance/assurance-security-development-and-operation) is applied.  
* Building the capability to [detect and respond to threats if an attack occurs](https://learn.microsoft.com/en-us/compliance/assurance/assurance-shared-ransomware-protection#detection-and-response-capabilities). Collecting centralised logging and automatic analysis to detect log events for activities that might indicate a security incident.

**Refs:**

[Handling **ransomware in SharePoint** Online](https://learn.microsoft.com/en-us/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)   
[**OneDrive Ransomware** detection and recovering your files](https://support.microsoft.com/en-us/office/ransomware-detection-and-recovering-your-files-0d90ec50-6bfd-40f4-acc7-b8c12c73637f)   
[Built-in virus protection in SharePoint Online, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-protection-for-spo-odfb-teams-about)

---

### Requirement 2

Minimize the footprint of on-premises backup infrastructure.  
Minimise the footprint of on-premises **backup** infrastructure.

Replace on-premises tape backups with Microsoft cloud services such as **Azure Backup** and **Azure Blob** **Storage** that support **soft delete, versioning, and immutability**.

---

### Requirement 3

Ensure that the data protection solution addresses the need for short-term backups.

Ensure that the **data protection** **solution** addresses the need for **short-term backups**.

The **short-term data retention** features of **SharePoint Online**, **OneDrive for Business**, **Exchange Online**, **Azure Blob Storage**, and **Azure Files** satisfy this requirement.

- **SharePoint Online** & **OneDrive** offer versioning, recycle bin, and Files Restore  
- **Exchange Online** offers single item recovery, mailbox retention, and retention policies.  
- **Azure Blob Storage** offers soft delete functionality as **container soft delete** and **blob versioning**.  
- **Azure Files** support **point-in-time read-only snapshots** and **configurable** **soft delete** for file shares (**not individual files\!**). 

---

### Requirement 4

Ensure that the data protection solution addresses the need for long-term backups supporting the seven-year retention required for compliance reasons.

Ensure that the **data protection solution (DPS)** supports **seven-year** **retention** of **long-term backups** required by **compliance**.

The **long-term data retention** of **Microsoft 365** content is covered by: 

* [**Microsoft Purview retention policies**](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=teams-retention)   
* [Purview **Retention Labels** with the](https://learn.microsoft.com/en-us/purview/retention?tabs=table-overriden)   
* [**Preservation Hold Library**](https://learn.microsoft.com/en-us/purview/retention?tabs=table-overriden)

The **long-term data retention** of **Exchange Online** content is covered by: 

* [Create a retention policy for Exchange Online](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy)

The **long-term data retention** of **Azure Storage** content is covered by: 

* [Store business-critical blob data with immutable storage in a write once, read many (WORM) state](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview)

WORM prevents data from being written to (modified) or deleted for a user-specified interval.  
Azure Blob Storage supports **two immutability policy types that intersect with two scopes**.

Under the immutable storage umbrella, there are two scopes, each with subtle differences, that apply to [time-based retention policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#time-based-retention-policies) and l[egal hold policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#legal-holds). 

However, in general, the two scopes are: 

1. container-level WORM: can be set at the container level **only.**    
     
2. version-level WORM:  can be set at the account, container, or version level.

The two retention policies are:

1. [Time-based retention policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#time-based-retention-policies):  
     
   A TBRP **retains data as immutable for a specified interval of time.** The data can be created and read, but not modified or deleted. After the retention period expires, objects can be deleted **but not overwritten, therefore they cannot be changed even after the expiration** of the TBRP term.  
     
   [Scope](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#scope)s:  
     
   Container-level WORM policy:   
     
   It applies to all blobs in that container and individual blobs **cannot** be configured with their own immutability policies.   
     
   Version-level WORM policy:  
     
   When configured at the account or container level, it is inherited by all blobs in the account or container.  
   **It is impossible to create a Version-level WORM policy on a container if there is already LH on it,** as the LH prevents the creation of versions**.**  
     
2. [Legal hold policies](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#legal-holds):  
     
   **Legal holds make data immutable until they are explicitly cleared,** when a legal hold is set, objects can be created and read but not modified or deleted.

* These policies can be set at the same time.  
* For a write to succeed, **versioning** must be enabled **or** have **neither** a LH **nor** TBRP on it.  
* For a delete to succeed, there must not be a LH or TBRP on it.

However, in this case study, there are two storage types within an Azure Storage Account to be considered in light of long-term backup and data retention.

* **Azure Files** for **frequently updated** marketing information in the Adobe Acrobat format.  
    
* **Azure Blob Storage** to **archive large amounts of historical content** in the ZIP and retain it for compliance. 


The timescale of retention afforded by the time-based and Legal Hold policies for blobs satisfies the compliance requirement of seven-year retention. 

* [The retention interval for a time-based policy](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#retention-interval-for-a-time-based-policy) **is up to 400 years.**  
* **A legal hold will not expire unless it is manually removed.**

WORM policies for Blobs are only one of the two mechanisms for data retention applicable to Azure Blobs, the other is a full Azure Blob backup.

[Overview of Azure Blob backup](https://learn.microsoft.com/en-us/azure/backup/blob-backup-overview?tabs=operational-backup)   
[Übersicht über die Sicherung von Azure-Blobs](https://learn.microsoft.com/de-de/azure/backup/blob-backup-overview?tabs=operational-backup)

Finally, the long-term data retention compliance for the frequently updated marketing information stored in Azure Files must be assessed. 

Azure Files offers data protection through features like **soft delete, snapshots, and Azure Backup**, allowing you to **configure retention policies** and protect **against accidental** **deletion** or ransomware attacks.

[How Azure Files protects against ransomware and accidental data loss \- Microsoft Azure](https://www.youtube.com/watch?v=TOHaNJpAOfc&t=4s)   
[About Azure Files backup](https://learn.microsoft.com/en-us/azure/backup/azure-file-share-backup-overview?tabs=snapshot)   
[Azure File Document Retention](https://learn.microsoft.com/en-us/answers/questions/1426331/azure-file-document-retention) 

---

### Requirement 5

Deliver continuous security protection and monitoring of remote devices.  
Implement continuous security protection and monitoring of remote devices.

An effective ransomware protection strategy:

1. Integrate their on-premises AD DS environment with Microsoft Entra ID  
2. Remote users join their devices to Microsoft Entra ID  
3. Enroll the devices on Microsoft Intune  
4. Onboard them to Microsoft Defender for Endpoint.  
5. Mobile Device Management (MDM) functionality of Microsoft Intune should be used to enforce organization-defined device configurations, including disk encryption, software installations, and software updates.  
   

---

### Requirement 6

Control access to the company's assets based on a wide range of conditions.

* Microsoft Entra Conditional Access policies should be applied to devices and remote devices onboarded in Intune to authenticate users.  
* The policy grants access only from Microsoft Entra-joined and fully compliant devices.  
* Microsoft Entra ID Protection can dynamically detect a risk associated with an authentication attempt.  
* Microsoft Defender for Cloud Apps and Microsoft Entra Conditional Access session policies monitor, in real time, the flow of data between users and managed applications to prevent data exfiltration attempts.

---

### Requirement 7

Protect backups against accidental or malicious deletions.

Enhance built-in ransomware protection of backups stored in Azure Recovery Services and Azure Backup vaults with the following practices:

1. Restricting access to backups with RBAC  
2. Use PIM to grant time-limited and approval-based role assignments  
3. Use soft delete is enabled to protect backups from accidental or malicious deletions.  
4. Implement [**multiuser authorization (MUA)** for critical operations on **Recovery Services and Backup vaults**](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept?tabs=recovery-services-vault) with **Resource Guard**: disabling soft delete, stopping and deleting backups, or reducing retention of backup policies, can be performed only when authorized by multiple users.  
5. Use JIT with PIM on the Resource Guard  
6. Monitor Backups using [Backup Explorer](https://learn.microsoft.com/en-us/azure/backup/monitor-azure-backup-with-backup-explorer)  
7. **Ensuring that network connectivity between backup services and workloads is secure.**  
   1. Azure VM, data in transit traverses the Azure backbone network.  
   2. For Azure Storage, you must allow access to Azure services on the trusted services list.  
   3. On-prem workloads protected by **the [MARS or MABS](https://learn.microsoft.com/en-us/answers/questions/820006/mars-and-mabs-backup-method-use-the-same-backup-pr) agent** must use Microsoft peering for ExpressRoute or Virtual Private Network (VPN)

---

## List of all Questions

1. What stakeholders should be involved in crafting a ransomware mitigation plan?  
2. Alongside technical elements of backup and recovery, what process would you use to create an incident recovery plan for a major data breach?  
3. What methods would you recommend to mitigate the potential impact of ransomware that attempts to encrypt Microsoft 365-hosted content in place?  
4. What methods would you recommend to mitigate the potential impact of ransomware that copies Microsoft 365-hosted content, encrypts it, and deletes the original?  
5. What methods would you recommend to mitigate the potential impact of ransomware that attempts to copy data outside of a Microsoft 365 tenant?  
6. Which are the data protection integration points between Microsoft 365 services and Microsoft Defender XDR products?  
7. What are the endpoint protection integration points available in a Microsoft 365 environment?  
8. How would you enhance identity protection in Microsoft 365 and Microsoft Azure environments?  
     
9. How would you approach creating a business resiliency plan for Contoso based on the Cloud Adoption Framework?

---

## Conceptual Answers and Questions

### QA 1

What stakeholders should be involved in crafting a ransomware mitigation plan?

The stakeholders:

1. Central IT Operations team or CIO  
2. Central IT infrastructure team  
3. Security Architecture team  
4. Security Compliance Management team  
5. IT Productivity team  
6. Security Policy and Standards team  
7. Users

The first three roles are at a high level, and their responsibilities are the same for each part the planning and implementation:

* **The Central IT Operations team (CIO)** is responsible for the e**xecutive sponsorship** to champion a project or initiative, providing guidance, resources, and influence to ensure its success, acting as a bridge between the project team and the executive leadership.


* **The central IT infrastructure team** is responsible for driving results and cross-team collaboration.  
    
* **The Security Architecture team** advises on configuration and standards.  
    
* **The Security Compliance Management team** oversees the process to ensure compliance.  
    
* **The Security Policy and Standards team** updates standards and policy documents.

The parts to crafting a ransomware mitigation plan:

1. Backup security design  
     
- **The IT Infrastructure & Backup team** designs the backup infrastructure.  
- **The IT Productivity team** or end **users** enable **OneDrive backup**.  
    
2. Data Protection design

- **The IT Infrastructure & Backup team** designs the backup infrastructure.  
- **The IT Productivity team** or end **users** enable **the implementation of changes to the Microsoft 365 tenant for OneDrive and Protected Folders**.

---

### QA 2

Alongside technical elements of backup and recovery, what process would you use to create an incident recovery plan for a major data breach?

1. Bring together all relevant stakeholders: from the business,  the IT, and security.  
2. Determine the value of the digital assets to these stakeholders.  
3. Categorized the digital assets based on their sensitivity and business value.  
4. The categories determine the level of assurance and the corresponding measures that should be applied to protect them from potential threats.  
5. Include backups as digital assets as these are the business fallback in case of a ransomware attack.  
   

---

### QA 3

What methods would you recommend to mitigate the potential impact of **ransomware that attempts to encrypt** Microsoft 365-hosted content in place?

1. **SharePoint and OneDrive for Business (Microsoft 365\)** protect files from malicious encryption in place by using:  
     
   \- [versioning](https://learn.microsoft.com/en-us/purview/retention-policies-sharepoint#how-retention-works-with-document-versions): by default, versioning retains a minimum of 500 major versions  
   \- File Restore  
   \- [Preservation Hold library](https://learn.microsoft.com/en-us/purview/retention-policies-sharepoint#how-retention-works-for-sharepoint-and-onedrive)

When a user changes an item that's subject to retention from a retention policy or a retention label that marks items as a record, or deletes any item subject to retention, the original content is copied to the Preservation Hold library.

SharePoint and OneDrive create a Preservation Hold library if one doesn't exist for the site. The Preservation Hold library is a hidden system location that isn't designed to be used interactively but instead, automatically stores files when this is needed for compliance reasons. It's not supported to edit, delete, or move these automatically retained files yourself. Or, change or remove retention labels and sensitivity labels for these files.

2. OneDrive [can restore files from any point in time during the last 30 days](https://support.microsoft.com/en-us/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15). Users have the ability to use versioning and file restore on their own.  
     
3. [Exchange Online emails are protected by retention policies](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy), which also allow retaining immutable copies of emails for a configurable retention period.

---

### QA 4

What methods would you recommend to mitigate the potential impact of **ransomware that copies Microsoft 365-hosted content, encrypts it, and deletes the original**?

1. **SharePoint and OneDrive for Business.** If the ransomware creates a new encrypted copy of a file and deletes the old file, customers have 93 days to restore it from the recycle bin. After 93 days, there's a 14-day window where Microsoft can still recover the data. In this case, users can also restore files from the recycle bin on their own.   
     
2. **Exchange Online** emails are protected by:   
3.   
   1. [Single item recovery](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery)   
   2. [Mailbox retention](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/apply-retention-policy)   
   3. [retention policies](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/default-retention-policy) 

Single item recovery and mailbox retention support recovering items in a mailbox. Users can roll back mail messages deleted within 14 days by default, configurable up to 30 days. 

[Exchange Online Retention policies](https://learn.microsoft.com/en-us/exchange/security-and-compliance/messaging-records-management/default-retention-policy]) allow retaining immutable copies of email for a configurable retention period.

---

### QA 5

What methods would you recommend to mitigate the potential impact of ransomware that attempts to copy data outside of a Microsoft 365 tenant?

1. Use [**Microsoft Purview Data Loss Prevention (DLP) policies**](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp)**,** which **detect, warn, and block** risky, inadvertent, or inappropriate sharing of data containing personal data and confidential organisation information **based on sensitivity labels.**

2. **Supplement** this with **Microsoft Defender for Cloud App**, which supports **session monitoring** **as part of Conditional Access App Controls.** The monitoring applies to the flow of data between users and managed applications and can be used to block transfers of business sensitive content.

---

### QA 6

Which are the data protection **integration** points between **Microsoft 365** services and **Microsoft Defender XDR** products?

**SharePoint Online, OneDrive for Business, and Exchange Online** are closely integrated with Microsoft Defender XDR.

* Microsoft Defender XDR suite of products:   
    
- Microsoft Defender for Endpoint  
- Microsoft Defender for Office 365  
- Microsoft Defender for Identity  
- Microsoft Defender for Cloud Apps.

---

### QA 7

What are the **endpoint protection** **integration** points available in a **Microsoft 365** environment?

Microsoft 365 is closely integrated with 

* Microsoft Defender for Endpoint:  
  It is an **enterprise endpoint security platform** designed to help enterprise networks **prevent, detect, investigate, and respond** (**PDIR**) to advanced threats.  
     
* Microsoft Defender for Cloud Apps:  
  It **provides control over data travel** and **sophisticated analytics** to **identify** and **combat** **cyberthreats** across Microsoft and third-party cloud services.

* Microsoft Defender for Endpoint integrates with Defender for Cloud Apps:  
  By **collecting and forwarding** all cloud app networking activities, delivering enhanced visibility into cloud app usage.


  
---

### QA 8

How would you **enhance identity protection** **in Microsoft 365 and Microsoft Azure** environments?

**To mitigate ransomware risks** by protecting identities against commonly seen password attacks, which account for **99.9% of the attacks** targeting Microsoft Entra ID

1. Microsoft Entra multifactor   
2. Passwordless authentication  
3. Microsoft Entra Authenticator App  
4. Windows Hello for Business

5. Microsoft Entra Conditional Access policies  
   These policies can be applied to authenticating users and their devices to ensure access is granted only from Microsoft Entra-joined and fully compliant devices. It can also perform dynamic risk detection, evaluated by Microsoft Entra ID Protection.  
     
6. **Microsoft Entra ID PIM** to implement JIT and JEA approval-based role activation.  
7. **Microsoft Defender for Identity is included in the Microsoft Defender XDR**  
   AD DS signals are used to **identify**, **detect**, and **investigate** advanced threats, compromised identities, and malicious insider actions directed at AD DS domain environments.

---

## Design Answers and Questions

### QA 9

How would you approach creating a business resiliency plan for Contoso based on the Cloud Adoption Framework?

1. CAF principles mandate a comprehensive approach to ransomware protection.  
     
2. CAF mandates the development of a business resiliency plan with two primary factors:  
   1. Maintaining the optimal security posture.  
   2. Being able to respond to incidents most efficiently and effectively.  
        
3. CAF divides the lifecycle of security risks in 4 stages:  
   1. Before the incident  
   2. During the incident  
   3. After the incident  
   4. Feedback loop

4. CAF implements the principle of  **Zero-Trust** and has a **starting point** for a resiliency plan (**RP**):  
   1. building an **inventory** of all the technology and business assets  
   2. **identifying the level of risk** associated with each of them  
   3. **evaluating** their **current protection status**

5. CAF resiliency plan (**RP**) must take into account the following **security provisions (the defense-in-depth cybersecurity paradigm):**  
     
   1. Authentication and Authorization  
   2. Identity management  
   3. Endpoint protection  
   4. Data storage  
   5. Applications usage  
   6. [**Network segmentation** (according to **WAF**)](https://www.youtube.com/watch?v=GMPg--vKB1Y) | [Recommendations for building a segmentation strategy](https://learn.microsoft.com/en-us/azure/well-architected/security/segmentation) | [WAF Security SE:04 Recommendations for building a segmentation strategy](https://learn.microsoft.com/en-us/azure/well-architected/security/segmentation)    
   7. Monitoring  
   8. Auditing  
   9. Governance  
        
6. On-prem Active Directory Domain Services (AD DS) integration with Microsoft Entra ID **to allow secure access to corporate resources**: [Designing and Implementing Active Directory and Entra ID by Neil Morrissey \- Pluralsight](https://app.pluralsight.com/library/courses/azure-active-directory-designing-implementing/table-of-contents)  
     
   1. [Implement passwordless authentication for its remote users in MEID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless):  
        
      1. [**Windows Hello for Business**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#windows-hello-for-business)  
      2. [**Microsoft Authenticator**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#microsoft-authenticator)  
      3. [**Passkeys (FIDO2)**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#passkeys-fido2)  
      4. [**Certificate-based authentication**](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#certificate-based-authentication)  
      5. [Platform Credential for macOS](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#platform-credential-for-macos)  
      6. [Platform single sign-on (PSSO) for macOS with smart card authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless#platform-single-sign-on-for-macos-with-smartcard)  
           
7. Endpoint protection with Intune and integration with Microsoft Defender for Endpoint.   
     
8. onboard digital assets into other Microsoft Defender XDR products   
     
   1. Defender for Identity: facilitates the detection of threats within the AD DS environment  
        
   2. Defender for Cloud Apps: provides an extra layer of security for cloud-based applications, including Office 365 services by detecting anomalous behavior, which might be indicative of a ransomware attack.  
        
   3. Defender for Office 365: implements email filtering that provides other protection against specific types of advanced threats, including malware and viruses

9. Implement Microsoft Entra Conditional Access:   
   Validate that only properly authorised users on devices configured according to centrally controlled policies are granted access to the organisation’s digital assets. **Integration between Microsoft Entra Conditional Access and Defender for Cloud Apps will allow Contoso to apply session-level controls that block data exfiltration attempts**.

### [Prevent **Exfiltration** with Conditional Access & Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad)

* **Microsoft Defender for Cloud Apps** integrates with **any** identity provider (IdP) to deliver this protection with:  
    
  * [access policies](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad):  
      
    * provides **real-time monitoring and contro**l over access to cloud apps  
    * controls access based on user, location, **any** device, and app  
    * Example: Block access to Salesforce for users of unmanaged devices.  
    * Example: Block access to Dropbox for native clients.  
    * Each policy has conditions to define the policy application parameters:  
      * **Who**: which user or group of users  
      * **What**: Which cloud apps  
      * **Where:** which locations and networks

    

     

  * [session policies](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad)  
      
    * Provide **granular visibility into cloud apps with real-time, session-level monitoring**.  
    * **In contrast to access policies, which allow or block access completely, session policies allow access while monitoring the session and limit specific session activities.**  
    * Example: allow users to access an app from unmanaged devices or from specific locations, but **limit the download of sensitive files during those sessions** or **require that specific documents are protected from downloading**, **uploading, or copying** when exiting the app.  
    * Example: Block uploads of malware files to SharePoint Online.

#### Host Apps vs Resource Apps

Difference between host app and resource app, Microsoft, in the context of Access Policies.

In the context of Microsoft Access policies: 

- The **host app** is the client application that a user interacts with.    
- The **resource app** is the service or application that the host app is interacting with or accessing.

**Policies created for a host app, like Teams, don't automatically apply to a resource app**, like OneDrive, and vice versa; separate policies are needed for each\!

#### [Browser-based and Non-browser-based Access Policies](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad#sample-create-microsoft-entra-id-conditional-access-policies-for-use-with-defender-for-cloud-apps)

Microsoft Entra ID supports both browser-based and non-browser-based access policies. We recommend that you create both types for increased security coverage.

The procedure to create them is the same, with only one difference, and therefore the same process must be repeated twice : **to create a nonbrowser based Conditional Access policy**, In the Client apps area, **toggle the Configure option to Yes**. Then, **under Modern authentication clients**, clear the Browser option. Leave all other default selections selected.

10. Microsoft Entra Privileged Identity Management (**PIM**) to ensure compliance with **the principle of least privilege**.  
    

Telemetry. Visibility and Incident Response

11. **Combining all of these features would generate comprehensive telemetry**, yielding full visibility of the entire managed environment, allowing **the SecOps team** to quickly identify and thwart any emerging threats. **Visibility could be further enhanced by implementing Microsoft Sentinel**.  
      
12. Have a **well-defined plan** to execute during and after an incident.   
      
    1. **During an incident (phase 1\)**, the primary objective is to ensure that **the business remains operational** and might require **accepting service degradation** and **limiting the service to only the essential services**.  
         
    2. **During an incident (phase 2),** the team **SecOps must** assess the extent of access gained by the attackers and evict them from the managed environment. This can be achieved through the tools provided by Microsoft Defender XDR and Microsoft Sentinel, which allow the team **SecOps** to **discover the kill chain that led to an exploit**.  
         
    3. **After an incident**, business operations should be restored to their original status. Azure Backup, Microsoft 365 Preservation Hold Library allow this.  
       

Data Protection and BCDR

13. Replace on-premises **data storage and backup technologies** with cloud-based services to **improve data protection**.  
      
14. Develop a **playbook** that **clearly defines the roles and responsibilities** to assign and **the procedures to follow** during an incident. That **playbook should be tested and updated** through routine internal drill exercises, **simulating ransomware cyberattacks**.

### QA 10

Given identified risks from the scenario, are there any opportunities to achieve better security integration with business processes using the Cloud Adoption Framework?

The Cloud Adoption Framework provides guidance regarding **integration with business processes** in **three distinct areas**: 

1. Risk insights  
2. Security integration  
3. Operational resiliency

#### Risk insights 

* #### Ensure an alignment between business initiatives and both security insights and risk signals.

* Ensure that stakeholders have awareness of and visibility into ransomware protection mechanisms applied to all business-sensitive content on-prem and in the cloud.  
* Any **assets** should be **categorised** based on their business value and marked using methods such as **Microsoft Purview sensitivity labels** or **Microsoft Azure resource tags**. The categorisation drives the choice of the storage protection methodology.  
* **The longer-term objective** would involve aligning the business strategy with the **Zero Trust principles** of **assuming a breach**.  
* All business initiatives should be subject to a **thorough security review**, with a focus on ransomware protection.

#### Security integration 

* Ensure that daily business operations take security considerations into account.  
* Negotiate with the business stakeholders to agree on a schedule for update deployments that is acceptable to both sides.  
* **Migrating data to managed cloud services in Microsoft 365 and Azure will automatically resolve this challenge on the storage side**.  
* **Intune will provide the least intrusive, automated process of deploying security updates on users’ devices.**

#### Operational resiliency

* The business must remain operational following a successful security exploit.  
* The business should remediate any potential impact from such exploits in a timely manner.

### QA 11

**Which Microsoft 365 services** would allow Contoso to increase their visibility into and traceability of cyberattacks affecting **on-premises and cloud** assets?

* Microsoft Defender for Cloud   
    
* Microsoft Sentinel  
    
* **Microsoft Defender XDR**: offers a **unified pre- and post-breach enterprise defense** **suite** of products that help coordinate detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.  
    
  It includes:  
    
  * Microsoft Defender for Endpoint  
  * Microsoft Defender for Office 365  
  * Microsoft Defender for Identity  
  * Microsoft Defender for Cloud Apps

#### Microsoft Defender for Cloud and Microsoft Defender XDR

**They serve different purposes**. 

* **Microsoft Defender for Cloud** focuses on securing cloud environments (Azure, AWS, Google Cloud). Provides tools to detect and block ransomware, advanced malware and threats **for workloads** hosted in Azure, third party clouds, and on-premises.  
    
* **Defender XDR** provides extended detection and response **across your entire digital estate**, including **endpoints**, **identities**, **emails**, and **cloud apps**. **XDR acts as a unified platform** that **integrates alerts and incidents from various Defender components**, including Defender for Cloud.

### QA 12

**Which Microsoft Azure services** would allow Contoso to increase visibility into and traceability of cyberattacks affecting **on-premises** **and cloud** assets?

1. Microsoft Defender for Cloud to protect cloud and on-prem workloads:  
     
* kill-chain analysis  
* generates a security alert with remediation steps and affected resources  
* Trigger logic apps in response

2. **Microsoft Sentinel** (**SIEM \+ SOAR**)  
     
* Takes advantage of artificial intelligence to correlate multiple low fidelity signals spanning multiple sources, and create a complete view of a ransomware kill chain.  
* **Generates prioritised alerts**, reducing the corresponding impact and the time to evict attackers.

### QA 13

What changes in the operational procedures would you recommend to Contoso to mitigate the potential impact of ransomware?

* **Azure Backups are encrypted by default**, at rest with platform-managed keys or customer-managed keys (**CMK**).  
* Customers can configure **infrastructure-level encryption and CMK encryption** to provide **double encryption**.  
* **MARS** and **MABS** use a **customer-set passphrase** to implement **end-to-end encryption** of data. The **passphrase should be securely stored in an alternate location**, other than the original data location, preferably in the **Azure Key Vault**.  
* **Monitor** backups, i.e. with **Backup Explorer** to identify assets not protected by backups, backup jobs, etc, across the digital estate.  
* **Validate** backups and the **BCDR strategy** **periodically.**  
* **Verify the expected** Recovery Point Objective **(RPO)** and Recovery Time Objective **(RTO)**

#### In case of a successful exploit

1. Identify the most recent clean recovery point created before the exploit.  
2. Restore data to an isolated and secure network.  
3. Scan the restored data to ensure it's not compromised.  
4. Restore to a production environment.  
5. **Review** the incident timeline.

### QA 14

What would you recommend to Contoso to implement endpoint protection?

Implement the following:

* [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)  
    
  **PDIR: Prevent \> Detect \> Investigate \> Respond**  
    
  A **cloud-native endpoint security solution** that provides **visibility, threat protection, and response capabilities** across various platforms, including Windows, macOS, Linux, Android, iOS, and IoT devices, **leveraging AI** and **industry-leading threat intelligence**.  
    
* Microsoft Intune:  
- Evaluate device compliance with policies  
- Integrates with Microsoft Defender for Endpoint  
-    
    
* Microsoft Defender for Cloud  
    
* [Azure Firewall Premium Features](https://learn.microsoft.com/en-us/azure/firewall/premium-features)  
  * [signature-based intrusion detection and prevention system (**IDPS**)](https://learn.microsoft.com/en-us/azure/firewall/premium-features?source=docs#idps)  
    

---

	

### QA 15

What infrastructure elements would you prioritize for system hardening in order to mitigate the ransomware risk for Contoso?

According to the CAF:

1. Focus **first on Access Control**: implementing network and identity access boundaries and segmentation.  
     
2. Enhance **security operations** to maximise the ability to detect, respond to, and recover from a breach.  
     
3. Implement **Asset Protection**, maximising security of all digital assets, including infrastructure, devices, data, applications, networks, and identities.  
     
4. Implement **governance**, helping enforce security standards across the entire managed environment.  
     
5. Implement **innovation security**, which drives the adoption of the DevOps model for changes in technology

---

# Ransomware Protection

[**Ransomware Protection-Collection**](https://learn.microsoft.com/en-us/collections/rjrqh2t0e7dy2) 

**How to recover from  a ransomware attack in Microsoft 365**

[**Ransomware Solution Library: Microsoft defense against ransomware, extortion, and intrusion \- How to recover from a ransomware attack in Microsoft 365\.**](https://learn.microsoft.com/en-us/security/ransomware/) 

The following tools are also those used by the [**Microsoft Incident Response Team**](https://learn.microsoft.com/en-us/security/ransomware/human-operated-ransomware#how-microsoft-can-help-with-an-in-progress-ransomware-attack) when an organisation decides to rely on this service. However, an organisation may implement and apply the same strategies without contacting Microsoft.

1. Leverage and deploy [Microsoft Defender for Identity](https://www.microsoft.com/EN-US/security/business/siem-and-xdr/microsoft-defender-for-identity)	

**Bringing** **identity monitoring into incident response** early supports the affected organisation's security operations team to regain control. **Microsoft Incident response** uses **Defender for Identity** to help **identify the incident scope and impacted accounts**, protect critical infrastructure, and **evict** the threat actor.

2. [Microsoft Defender for Endpoint](https://www.microsoft.com/EN-US/security/business/endpoint-security/microsoft-defender-endpoint)

MDEP is used **to trace the threat actor’s movements and disrupt their attempts to use compromised** **accounts to reenter the environment**.

Examples:

[Common **malware** used in ransomware campaigns](https://learn.microsoft.com/en-us/security/ransomware/human-operated-ransomware#common-malware-used-in-ransomware-campaigns): [Qakbot](https://www.microsoft.com/en-us/security/blog/2024/05/15/threat-actors-misusing-quick-assist-in-social-engineering-attacks-leading-to-ransomware/), [Ryuk](https://www.microsoft.com/en-us/security/blog/2024/05/15/threat-actors-misusing-quick-assist-in-social-engineering-attacks-leading-to-ransomware/), [Tricbot](https://www.microsoft.com/en-us/security/blog/2020/10/12/trickbot-disrupted/?msockid=3fd141c935036ef610d9506e34696fe7)   
[Prevalent **threat actors** associated with ransomware campaign](https://learn.microsoft.com/en-us/security/ransomware/human-operated-ransomware#prevalent-threat-actors-associated-with-ransomware-campaignsv): [**LockBit**](https://blogs.microsoft.com/on-the-issues/2023/04/06/stopping-cybercriminals-from-abusing-security-tools/), [Black Basta](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=Ransom:Win32/Basta&msockid=3fd141c935036ef610d9506e34696fe),  Storm-1674  
[**Lockbit** Ransomware attack: Stopping cybercriminals from abusing security tools](https://blogs.microsoft.com/on-the-issues/2023/04/06/stopping-cybercriminals-from-abusing-security-tools/) 

---

---

## Microsoft 365 \- Microsoft Defender XDR

What [are the data protection integration points between Microsoft 365 services and Microsoft Defender XDR products?](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/3-case-study-answers)

Microsoft 365 SharePoint Online, OneDrive for Business, and Exchange Online are closely integrated with Microsoft Defender XDR suite of products, including Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity, and Microsoft Defender for Cloud Apps.

**Microsoft Defender XDR** bietet **eine einheitliche Produktreihe für den Unternehmensschutz** vor und nach einer Sicherheitsverletzung, mit der die [**Erkennung**](https://www.collinsdictionary.com/dictionary/german-english/erkennung), [**Vorbeugung**](https://www.collinsdictionary.com/dictionary/german-english/vorbeugung), **Untersuchung** und **Reaktion** über Endgeräte, Identitäten, E-Mails und Anwendungen hinweg **koordiniert** wird, um einen integrierten Schutz vor komplexen Angriffen zu gewährleisten. 

Zu diesen Produkten gehören: 

* Microsoft Defender for Endpoint   
  [Microsoft Defender for Endpoint-Teil 1 \- Den Tenant vorbereiten und einrichten-**Tom Wecsler**](https://www.youtube.com/watch?v=B24tHBuFZ1M)   
  [Microsoft Defender for Endpoint-Teil 2 \- Die lokalen Systeme einbinden (Onboard)-**Tom Wechlser**](https://www.youtube.com/watch?v=Z-XLiT_o9D8)  
    
* Microsoft Defender for Office 365  
    
* Microsoft Defender for Identity   
    
* Microsoft Defender for Cloud Apps.


---

## Integration for Protection from Ransomware

## SharePoint, OneDrive for Business, Exchange Online, Microsoft 365

[What methods would you recommend to mitigate the potential impact of **ransomware that attempts to encrypt** Microsoft 365-hosted content inplace?](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/3-case-study-answers)

Files in **SharePoint** and **OneDrive for Business** are protected from malicious encryption in place by using versioning, File Restore, and Preservation Hold library. **Microsoft 365** retains a minimum of 500 versions of a file by default but that number can be increased. **Microsoft 365 also provides a self-service recovery solution for SharePoint and OneDrive** that allows administrators and end users to restore files from any point in time during the last 30 days. Users have the ability to use versioning and Files Restore on their own. **Exchange Online** emails are protected by retention policies. Retention policies allow retaining immutable copies of email for a configurable retention period.

---

## Microsoft 365 \- Purview+Defender for Cloud Apps

[What methods would you recommend to **mitigate the potential impact of ransomware that copies Microsoft 365-hosted content, encrypts it, and deletes the original**?](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/3-case-study-answers)

To prevent a ransomware attacker from copying files outside of the Microsoft 365 tenant, customers can use [**Microsoft Purview Data Loss Prevention (DLP) policies**](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp), which **detect**, **warn**, and **block** **risky, inadvertent, or inappropriate sharing of data containing personal data and confidential organisation information based on sensitivity labels**. 

This can be supplemented by **Microsoft Defender for Cloud Apps**, which supports session monitoring as part of [**Conditional Access App Control**](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad). The monitoring applies to the flow of data between users and managed applications and can be used to block transfers of business-sensitive content.

---

## Microsoft 365 \- Endpoint Protection 

[What are the endpoint protection integration points available in a Microsoft 365 environment?](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/3-case-study-answers)

[Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)  
[Microsoft Defender for Cloud Apps Overview](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps) 

### Defender for Endpoint 

[Secure Your Devices with Defender for Endpoint \- **Part 1-Jonathan Edwards**](https://www.youtube.com/watch?v=U4LjuB3eTYI)  
[Secure Your Devices with Defender for Endpoint \- **Part 2-Jonathan Edwards**](https://www.youtube.com/watch?v=_Fc8o28vR1Q)    
[Microsoft Defender for Endpoint-**Teil 1** \- Den Tenant vorbereiten und einrichten-**Tom Wecsler**](https://www.youtube.com/watch?v=B24tHBuFZ1M)   
[Microsoft Defender for Endpoint-**Teil 2** \- Die lokalen Systeme einbinden (Onboard)-**Tom Wechlser**](https://www.youtube.com/watch?v=Z-XLiT_o9D8)  
[Microsoft Defender for Endpoint-**Teil 3** \- Konfigurieren von erweiterten Funktionen-**Tom Wechsler**](https://www.youtube.com/watch?v=XLJn0FhHNq4) 

---

## Identity Protection in Microsoft 365

[How would you enhance identity protection in Microsoft 365 and Microsoft Azure environments?](https://learn.microsoft.com/en-us/training/modules/case-study-design-solutions-security-best-practices-priorities/3-case-study-answers)

The following help mitigate ransomware risks by protecting identities against commonly seen password attacks, which account for **99.9% of the attacks targeting Microsoft Entra ID**.

1. Microsoft Entra MFA  
2. Microsoft Entra passwordless authentication  
3. Microsoft Entra Authenticator App  
4. Windows Hello for Business

### Microsoft Hello for Business

[Unlocking Your Device: The Power of Windows Hello for Business-**Jonathan Edwards**](https://www.youtube.com/watch?v=A8faHO-bn-0) 

Additionally:

5. [Microsoft Entra Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) can be applied to authenticate users and their devices by establishing compliance with if-then-based organisation policies using identity-driven signals to make access control decisions according to the paradigm: signals, decision, enforcement.   
   

Example: 

With MEID licence **P1**, **M365 Business Premium**, or **P2** If users want to access an application or service like Microsoft 365, they may be required to perform MFA to gain access, based on any combination of the following signals: user/group membership, IP, device details, application that the user wants to access, real-time and calculated **risk** detection \[requires P2 to leverage [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)\] \+ [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps). 

6. [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection) \[requires P2\] **dynamically** identifies potential threats and adjusts the corresponding risk levels. It helps organizations **detect, investigate, and remediate** **identity-based risks**. These risks can be further fed into tools like **Conditional Access** to make access decisions or **feed this info back to** a security information and event management **(SIEM) tool** such **as Microsoft Sentinel** for further investigation and correlation.  
 


### Microsoft Defender for Cloud Apps (MDApcc)

[Microsoft Defender for Cloud Apps documentation](https://learn.microsoft.com/en-us/defender-cloud-apps/)   
[Defender for Cloud Apps \- Lock Down Your Cloud Apps & Protect Data \- **Jonathan Edwards**](https://www.youtube.com/watch?v=ooqau_7ibvA) 

7. [Microsoft Defender for Cloud Apps (**MDCApps**)](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps) **monitors Microsoft Entra Conditional Access session policies** in **real-time** and the flow of data between users and managed applications **to thwart data exfiltration attempts**.

The business case for **MDCApps**: is there a way … ?

- For a business owner, what are the apps used inside their business?  
- to selectively block certain applications?  
- to monitor cloud applications?


  
**MDCApps** monitors and protects **SaaS applications and their data flow**, in four areas:

1. [Fundamental cloud access security broker (CASB)](https://www.microsoft.com/en-us/security/business/security-101/what-is-a-cloud-access-security-broker-casb): **a security policy enforcement point** between enterprise users and cloud service providers. It can combine multiple security policies i.e. authentication, credential mapping, encryption, malware detection, etc to ensure cloud app apps security on any device.  
     
2. SaaS Security Posture Management (SSPM) features, enable security teams to improve the organisation’s security posture  
     
3. Advanced threat protection, as part of Microsoft's extended detection and response (XDR) solution, enables powerful correlation of signal and visibility across the full kill chain of advanced attacks  
     
4. App-to-app protection, extending the core threat scenarios to OAuth-enabled apps that have permissions and privileges to critical data and resources.  
   

functionality, such as Shadow IT discovery, visibility into cloud app usage, protection against app-based threats from anywhere in the cloud, and information protection and compliance assessments.

8. [Microsoft Entra Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure) provides time-based and approval-based role activation to mitigate the risks of excessive, unnecessary, or misused permissions.   
     
9. [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/what-is) included in the Microsoft Defender XDR uses AD DS signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at AD DS domain environments.

---

