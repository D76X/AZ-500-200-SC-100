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

---