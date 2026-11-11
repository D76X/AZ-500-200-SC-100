
[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q05

A company migrates a file-sharing workload from an on-premises Windows file server to Azure Files. The on-premises server used NTFS permissions tied to on-premises Active Directory Domain Services (AD DS) groups to control which specific folders each department could access. The company wants Azure Files to preserve this same folder-level, group-based access control model for its hybrid, AD DS-joined workstations, without provisioning a separate Azure AD Domain Services deployment and without distributing the storage account access key to end users.

Which configuration should the company implement?

Select one answer option below.

### OPTION 01
Enable AD DS authentication for Azure Files, assign share-level Azure RBAC permissions to the synchronized groups, and preserve granular permissions with file-system ACLs.

### OPTION 02
Configure a Shared Access Signature (SAS) token for each department granting access to its specific folder, and distribute the tokens to department members instead of the storage account key.

### OPTION 03
Assign Azure RBAC roles, such as Storage File Data SMB Share Reader and Contributor, to each department's AD DS group at the level of the entire file share, rather than per folder.

### OPTION 04
Deploy Azure AD Domain Services in the same virtual network as the storage account, domain-join the Azure Files share to it, and recreate the department groups directly in Azure AD DS.

## Answer and rationale

**Correct answer: OPTION 01.**

Enable on-premises AD DS authentication for Azure Files over SMB. Synchronize the AD DS groups used for share access to Microsoft Entra ID, assign the appropriate Azure RBAC share-level role to those groups, and use Windows ACLs (NTFS permissions) to control access to each department's directories and files. AD DS-joined workstations can then authenticate with their existing domain credentials, while the share and file permissions—not a storage account key—govern access. Azure Files requires both share-level permission and the relevant file/directory permissions; the more restrictive permission applies. [1][2][3]

### Why the other options are not correct

- **OPTION 02:** A SAS token is a delegated token, not an AD DS identity or group membership. Distributing separate tokens would replace the existing identity-based SMB and NTFS-ACL model rather than preserve it; it does not provide the requested group-based folder ACLs. Azure Files' identity-based SMB access uses Kerberos and file/directory ACLs for this model. [1][3]
- **OPTION 03:** Azure RBAC roles such as **Storage File Data SMB Share Reader** and **Storage File Data SMB Share Contributor** grant share-level access. Assigning them at the file-share scope does not create per-folder authorization. Windows ACLs are required for directory- and file-level control. [2][3]
- **OPTION 04:** Microsoft Entra Domain Services (formerly Azure AD Domain Services) is a distinct, managed-domain identity source. Azure Files supports existing on-premises AD DS directly, including AD DS-joined clients, so deploying another domain service and recreating groups is unnecessary and conflicts with the requirement not to provision it. [1][4]

### References

1. [Overview: Azure Files identity-based authentication](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-active-directory-overview) — supported identity sources, Kerberos authentication, AD DS and hybrid identity requirements.
2. [On-premises AD DS authentication for Azure Files](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-ad-ds-overview) — synchronizing AD DS identities and assigning share-level permissions to synced identities.
3. [Configure directory- and file-level permissions for Azure Files](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-configure-file-level-permissions) — Windows ACLs provide granular access; share-level RBAC and ACLs work together.
4. [Assign share-level permissions for Azure Files](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-assign-share-level-permissions) — Azure RBAC roles grant share-level permissions to users or groups.

---