[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q12

You have a key vault named KV1 that currently has purge protection disabled. 
Your organization requires that once a secret, key, or certificate is deleted from KV1, 
it cannot be permanently erased until its retention period expires, even by a user with 
full administrative permissions. What should you do?

Select one answer option below.

### OPTION 01
Enable soft-delete on KV1

### OPTION 02
Restrict the Key Vault Administrator role assignment to a single user

### OPTION 03
Enable purge protection on KV1

### OPTION 04
Configure a resource lock with a CanNotDelete setting on KV1

## Answer

**Option 03: Enable purge protection on KV1.**

Purge protection prevents a soft-deleted key, secret, certificate, or vault from being permanently purged until its retention period expires. This is the required safeguard because the requirement explicitly says that even a user with full administrative permissions must not be able to permanently erase a deleted object during that period. Purge protection can only be enabled when soft-delete is enabled; soft-delete is the prerequisite, while purge protection enforces the delay.

### Why the other options are incorrect

- **Option 01 — Enable soft-delete on KV1:** Soft-delete keeps deleted objects recoverable during the retention period, but by itself it still permits a sufficiently privileged user to purge them early. It does not satisfy the requirement that permanent deletion be blocked until retention expires.

- **Option 02 — Restrict the Key Vault Administrator role assignment to a single user:** Limiting role assignments is an access-control measure, not a retention safeguard. The remaining administrator can perform data-plane operations; it does not ensure that an object cannot be purged before the retention period ends.

- **Option 04 — Configure a `CanNotDelete` resource lock on KV1:** A resource lock protects the Azure resource from control-plane deletion. It does not block data-plane operations on objects stored in the vault, such as deleting or purging a secret, key, or certificate.

### References

- [Azure Key Vault soft-delete overview — Microsoft Learn](https://learn.microsoft.com/en-us/azure/key-vault/general/soft-delete-overview): Describes the difference between soft-delete and purge protection, including that purge protection prevents purging until the retention period passes.

- [Azure Key Vault RBAC guide — Microsoft Learn](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-guide): Describes Key Vault data-plane operations and the Key Vault Administrator role's permissions.

- [Lock your Azure resources — Microsoft Learn](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources): Explains that resource locks apply to control-plane operations, not data-plane operations.

---