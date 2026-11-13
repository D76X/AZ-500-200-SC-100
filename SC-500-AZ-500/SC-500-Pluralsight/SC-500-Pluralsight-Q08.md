[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q08

A law firm stores case-related documents in Azure Blob Storage in a storage account named Storage4. 
Regulatory requirements state that once a document is uploaded, it must not be able to be modified 
or deleted by anyone, including a Global Administrator, until an active legal hold on the matter is 
released, even if the retention period itself has expired. Separately, the firm's compliance policy 
requires that the encryption key protecting this data be fully under the firm's control and immediately 
revocable if a key is suspected of being compromised.

Which combination of configurations satisfies both requirements?
Select one answer option below.

### OPTION 01
Configure a container with a time-based immutability policy in locked state, add a legal hold to the container, and 
configure the storage account's encryption to use a customer-managed key stored in Azure Key Vault.

### OPTION 02
Configure a container with an unlocked time-based immutability policy that can be shortened by an administrator if business needs change, add a legal hold to the container, and enable infrastructure encryption using a Microsoft-managed key for additional depth.

### OPTION 03
Configure a container with a locked time-based immutability policy and an active legal hold to prevent any deletion or modification of documents, and rely on the default Azure Storage Service Encryption with platform-managed keys for data at rest.

### OPTION 04
Enable soft delete for blobs and containers with a 90-day retention period so that accidentally deleted case documents can be recovered, and configure the storage account's encryption to use a customer-managed key stored in Azure Key Vault.

## Answer and rationale

**Correct answer: OPTION 01.**

Configure both a **locked time-based immutability policy** and an **active legal hold** on the container, and protect the storage account with a **customer-managed key (CMK) in Azure Key Vault**.

The locked time-based policy prevents blobs from being overwritten or deleted during the specified retention period. Once locked, its retention period can't be shortened and the policy can't be deleted. The legal hold is independent of that time period: while it remains active, blobs can't be modified or deleted, even after the time-based retention period expires. The hold must be explicitly cleared to release this protection. Blob immutability is designed to protect data from modification or deletion even by account administrators. [1]

A CMK stored in Key Vault gives the firm control over the key and its access. If the key is suspected of compromise, the firm can disable it to revoke Azure Storage's access; applicable read and write operations then fail until access is restored. Revoking the key affects data availability, not the immutability policy: it does not unlock or delete the protected blobs. [2][3]

### Why the other options are not correct

### OPTION 02
Configure a container with an unlocked time-based immutability policy that can be shortened by an administrator if business needs change, add a legal hold to the container, and enable infrastructure encryption using a Microsoft-managed key for additional depth.

- **OPTION 02:** The active legal hold would prevent modification and deletion until cleared, even if the time-based retention period expires. However, an unlocked time-based policy can be shortened or deleted, making it weaker as a separate retention control. More importantly, infrastructure encryption with Microsoft-managed keys does not give the firm control of the encryption key or the ability to revoke Azure's access to it, so this option fails the key-control requirement. [1][3]

---

### OPTION 03
Configure a container with a locked time-based immutability policy and an active legal hold to prevent any deletion or modification of documents, and rely on the default Azure Storage Service Encryption with platform-managed keys for data at rest.

- **OPTION 03:** The locked policy and legal hold meet the immutability requirement. However, the default Microsoft-managed key does not satisfy the separate requirement that the firm control and be able to revoke the encryption key. Customer-managed keys stored in Azure Key Vault provide that key control. [1][2][3]

---

### OPTION 04
Enable soft delete for blobs and containers with a 90-day retention period so that accidentally deleted case documents can be recovered, and configure the storage account's encryption to use a customer-managed key stored in Azure Key Vault.

- **OPTION 04:** Soft delete can help recover deleted blobs or containers during its retention period, but it doesn't prevent an authorized user from modifying or deleting the original data. It also provides no indefinite protection tied to an active legal hold. The CMK addresses encryption-key control, but soft delete doesn't meet the WORM and legal-hold requirements. [1][4]

---

### References

1. [Immutable storage for Blob data overview](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview) — Explains time-based retention, locked versus unlocked policies, legal holds, and protection from changes by users with account administrative privileges.
2. [Customer-managed keys for account encryption](https://learn.microsoft.com/en-us/azure/storage/common/customer-managed-keys-overview) — Describes customer control of Azure Storage encryption keys and revoking access by disabling a key in Key Vault.
3. [Azure Storage encryption for data at rest](https://learn.microsoft.com/en-us/azure/storage/common/storage-service-encryption) — Compares Microsoft-managed and customer-managed keys, including who controls the keys.
4. [Blob soft delete](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview) — Describes soft delete as recovery protection for deleted blobs, distinct from immutable storage.
---