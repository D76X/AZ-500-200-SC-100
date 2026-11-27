[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

[Plan and implement security for storage AZ-500 Microsoft Learn](https://www.youtube.com/watch?v=oIEOhL_JqqU)  

---

# Q18

A media company has enabled `automatic malware inspection for newly uploaded blobs in Storage2`. 
One designated container receives very large video assets from a controlled internal workflow that 
the organization has decided to exempt from inspection, while uploads to every other container must 
remain covered. The team also wants any blob classified as harmful in the covered locations to become 
unavailable automatically while remaining recoverable for investigation.

Which two configurations should the team implement?

Select two options below.

### OPTION 01
Enable the Defender for Storage option that soft-deletes blobs detected as malicious.

### OPTION 02
Add an on-upload malware scanning filter that excludes the designated ingestion path.

### OPTION 03
Create a Defender for Cloud alert suppression rule that suppresses all malware-related alerts for Storage2.

### OPTION 04
Disable sensitive data threat detection for Storage2 to reduce the overall alert volume.

---

## Answer

**Correct answers: OPTION 01 — enable soft delete for malicious blobs, and OPTION 02 — configure an on-upload malware scanning exclusion for the designated ingestion path.**

### Why the selected answers are correct

- **OPTION 01 — Enable the Defender for Storage option that soft-deletes blobs detected as malicious:** Defender for Storage has a built-in malware-remediation feature that automatically soft-deletes malicious blobs detected by on-upload or on-demand scanning. Soft deletion makes the blob unavailable to normal access while retaining it for investigation and recovery during the configured retention period. If blob soft delete isn't already enabled on the storage account, enabling the malicious-blob soft-delete feature configures it automatically. [1][2]

- **OPTION 02 — Add an on-upload malware scanning filter that excludes the designated ingestion path:** Microsoft Defender for Storage supports filters for on-upload malware scanning. A filter can exclude blobs by path prefix, so the team can exclude the designated container or ingestion path while keeping on-upload scanning enabled for every other covered container in the storage account. [3][4]

### Why the unselected answers are incorrect

- **OPTION 03 — Create an alert suppression rule that suppresses all malware-related alerts for Storage2:** Alert suppression rules only change a matching alert's status to Dismissed and prevent it from generating notifications or appearing in active alert views. They do not stop malware scanning, do not keep an exempt container out of scanning, and do not automatically quarantine or soft-delete malicious blobs. Also, they apply to alerts rather than providing the required granular path exemption. [5]

- **OPTION 04 — Disable sensitive data threat detection for Storage2:** Sensitive data threat detection identifies exposure events and suspicious activities involving sensitive data. Disabling it may affect sensitive-data alerts and breach protection, but it neither configures malware scanning exclusions nor enables remediation for malicious blobs. The question is about malware scanning and malicious-blob quarantine, so this setting does not satisfy the requirements. [6]

### References

1. [Set Up Automated Remediation for Malware Detection](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-configure-malware-scan) — describes the built-in capability that soft-deletes malicious blobs, prevents access, and retains the blobs for investigation and recovery.

2. [Soft Delete for Blobs to Recover Data](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview) — explains that soft-deleted blobs remain recoverable through the retention period and can be restored.

3. [Introduction to Defender for Storage Malware Scanning](https://learn.microsoft.com/en-us/azure/defender-for-cloud/introduction-malware-scanning) — explains on-upload scanning and how it detects and mitigates malware as objects are uploaded or modified.

4. [Defender For Storage - Create REST API](https://learn.microsoft.com/en-us/rest/api/defenderforcloud/defender-for-storage/create) — documents on-upload malware-scanning `excludeBlobsWithPrefix` filters and examples that exclude containers or specific blob paths.

5. [Suppress alerts from Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-suppression-rules) — explains that suppression rules dismiss matching alerts and suppress their notifications or active views; they do not remediate threats or change scan coverage.

6. [Sensitive data threat detection in Defender for Storage](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity) — describes sensitive-data threat detection as a separate capability for protecting sensitive data and identifying exposure events or suspicious activities.

---

# What is Microsoft sensitive data threat detection for Storage?

[Sensitive data threat detection in Microsoft Defender for Storage](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity)   

Sensitive data threat detection is a feature in Microsoft Defender for Storage 
that identifies resources holding sensitive data and prioritizes security alerts 
based on that sensitivity. 

It helps security teams spot: 

- exposure events, 
- suspicious activity, and 
- potential data breaches faster. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction), 
[3] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity)  

## How It Works

- Agentless discovery: 
It uses an agentless engine with smart sampling to scan supported storage resources 
and find sensitive information. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity)

- Microsoft Purview integration: 
It connects with `Microsoft Purview sensitive information types (SITs)` 
and `sensitivity labels` to align findings with your organization's classification policies. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity)

- Scan schedule: 
Initial scan results typically appear within 24 hours of enablement, 
new storage accounts under protected subscriptions are scanned within 6 hours of creation, 
and `recurring scans run weekly`. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity)

- Alert context: 
Security alerts include sensitivity details—such as scan time, top sensitivity label, 
matched information types, and sensitive file types—to help teams prioritize incidents. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity)

## Supported Storage & Pricing

- Blob storage: 
Available for standard general-purpose v1 and v2, Azure Data Lake Storage Gen2, and premium block blobs.

- Azure Files: 
Supported over REST API and SMB for Files, Files v2, and Premium Files when Defender CSPM is enabled.

- Cost and configuration: 
Included in the `Defender for Storage plan at no extra charge and enabled by default`, 
though you can toggle it on or off. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity)

## Common Usage Scenarios

- Prioritizing exfiltration or access alerts: 
Focusing first on: 
  - unusual downloads, 
  - data extraction, or 
  - suspicious access 

involving blob containers that hold personal or regulated data. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity), 
[2] (https://techcommunity.microsoft.com/blog/microsoftdefendercloudblog/key-findings-from-product-telemetry-top-storage-security-alerts-across-industrie/4473362), 
[3] (https://learn.microsoft.com/vi-vn/azure/defender-for-cloud/defender-for-storage-threats-alerts)

- Spotting risky exposure: 
Flagging storage resources with sensitive information types that face 
  - misconfigurations, 
  - public exposure risks, or 
  - unusual authentication token activity. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/discover-sensitive-data), 
[2] (https://techcommunity.microsoft.com/blog/microsoftdefendercloudblog/key-findings-from-product-telemetry-top-storage-security-alerts-across-industrie/4473362), 
[3] (https://learn.microsoft.com/vi-vn/azure/defender-for-cloud/defender-for-storage-threats-alerts)

- Compliance and data governance: 
Aligning threat triage with regional or industry data protection rules (such as `GDPR in Europe`) 
`using Purview sensitivity labels and custom SITs`. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity)

## Related Terms

• `Sensitive Data Discovery`: 
The underlying agentless scanning engine shared with `Defender Cloud Security Posture Management (CSPM)`.

- Microsoft Purview data classification / `SITs`: 
The classification framework and sensitive information types used to define what counts as sensitive data. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity),  
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-defender-for-storage-data-sensitivity),  
[3] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/discover-sensitive-data)  

---

# Allow recommended upper limit for shared access signature

In Microsoft Azure Storage, enabling the recommended upper limit for a 
shared access signature (SAS) configures a SAS expiration policy (sasPolicy) 
on a storage account to define the maximum recommended validity interval 
(days, hours, minutes, and seconds) for SAS tokens. 

[1] (https://learn.microsoft.com/en-us/azure/storage/common/sas-expiration-policy), 
[2] (https://www.ultratranscender.net/az-104/notes/shared-access-signatures/)  

## How It Works

- Validity calculation: 
Azure calculates the validity interval by subtracting the signed start time 
from the signed expiry time. When a policy is active, signed start is required. 

[1] (https://learn.microsoft.com/en-us/azure/storage/common/sas-expiration-policy), 
[2] (https://learn.microsoft.com/en-us/answers/questions/1470252/what-is-microsofts-recommended-upper-limit-for-sas)

- Enforcement & actions: 
You can set the expiration action to Log (the default, which warns on creation and 
logs out-of-policy usage in Azure Storage diagnostic logs under SasExpiryStatus) or 
Block (which denies requests using a SAS whose validity exceeds the limit). 

[1] (https://learn.microsoft.com/en-us/answers/questions/1470252/what-is-microsofts-recommended-upper-limit-for-sas), 
[2] (https://mc.merill.net/message/AZ498759), 
[3] (https://www.ultratranscender.net/az-104/notes/shared-access-signatures/)

- Scope: 
Applies to user delegation, service, and account SAS tokens for that storage account. 

[1] (https://learn.microsoft.com/en-us/azure/storage/common/sas-expiration-policy)

## How to Configure It in the Azure Portal

1. Open your Storage account in the Azure portal.
2. Select Configuration in the left menu.
3. `Enable the SAS expiration policy` (historically labeled "Allow recommended upper limit for shared access signature (SAS) expiry interval").
4. Set the Upper limit for SAS expiry interval (for example, 7 days or less per security policies).
5. Choose the expiration action (Log or Block) and click Save. 

[1] (https://www.ahsay.com/en/support/help-centre/how-to/cbs/cloud-storage/setup-shared-access-signature-microsoft-azure-portal), 
[2] (https://www.azadvertizer.net/azpolicyadvertizer/7aa1c9d5-3d7e-4579-8117-d85e99211757.html), 
[3] (https://www.ultratranscender.net/az-104/notes/shared-access-signatures/)

For full CLI, PowerShell, and portal setup details, see Microsoft Learn. 
[1] (https://learn.microsoft.com/en-us/azure/storage/common/sas-expiration-policy)

---