[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q11

You have a key vault named KV1 that uses the Azure role-based access control (RBAC) permission model. 
An application named App1 needs to retrieve secrets from KV1 at runtime. 
You need to grant App1 the minimum permissions required, following the principle of least privilege. 

What should you do?

Select one answer option below.

### OPTION 01
Create an access policy that grants Get and List secret permissions to App1's managed identity

### OPTION 02
Assign the Key Vault Secrets Officer role to App1's managed identity at the KV1 scope

### OPTION 03
Assign the Key Vault Administrator role to App1's managed identity at the KV1 scope

### OPTION 04
Assign the Key Vault Secrets User role to App1's managed identity at the KV1 scope

## Answer and rationale

**Select option 04.** Assign the **Key Vault Secrets User** role to App1's managed identity at the scope of KV1. 
This role allows the identity to read secret contents and is designed for applications that need to retrieve secrets. 
It grants the required data-plane access without granting permissions to create, update, or delete secrets, 
or to manage other Key Vault data such as keys and certificates. [1]

### Why the other options are not correct

- **Option 01:** Access policies are for the legacy access-policy permission model. Setting a vault to use Azure RBAC invalidates its access-policy permissions, so creating an access policy would not grant App1 access in this scenario. [1][2]

- **Option 02:** The **Key Vault Secrets Officer** can perform any action on the vault's secrets except manage permissions. That is broader than the read access App1 needs to retrieve secrets. [1]

- **Option 03:** The **Key Vault Administrator** can perform all data-plane operations on all objects in the vault, including keys, secrets, and certificates. This exceeds the required access by a wide margin. [1]

### References

1. [Grant permission to applications to access an Azure key vault using Azure RBAC](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-guide) — Describes the Key Vault data-plane roles, including the read-only Secrets User role, and states that enabling the Azure RBAC permission model invalidates access-policy permissions.

2. [Assign an Azure Key Vault access policy](https://learn.microsoft.com/en-us/azure/key-vault/general/assign-access-policy) — Identifies access policies as a legacy authorization model.

---