# SC-500 Practice Tests

Original, unofficial practice questions for **Exam SC-500: Implementing End-to-End Security Controls for Cloud and AI Workloads**, which earns the **Microsoft Certified: Cloud and AI Security Engineer Associate** credential. These questions are not copied from the live exam.

> **Exam alignment:** The current Microsoft Learn study guide groups skills into four domains: manage identity, access, and governance (20–25%); secure storage, databases, and networking (25–30%); secure compute (20–25%); and manage and monitor security posture (20–25%). The guide includes AI security within Secure compute. Check the official study guide for future changes. Product availability, feature support, and licensing vary by configuration and can change.
>
> **How to use:** Select the number of answers specified. Unless stated otherwise, choose the single best answer. Each answer includes why it is right, why the distractors are wrong, and Microsoft Learn references. This study aid does not guarantee exam coverage.

## Domain 1: Manage identity, access, and governance

### Question 1 - Just-in-time directory roles

A tenant administrator needs the User Administrator role only when performing approved maintenance. The organization requires eligible rather than permanent assignment and time-limited activation with approval. What should you configure?

A. An eligible Microsoft Entra role assignment in Privileged Identity Management (PIM), with activation duration and approval requirements
B. A Conditional Access policy that permanently assigns the role after MFA
C. An authentication methods policy that grants the role to FIDO2 users
D. A Sentinel analytics rule that adds the user to the role when an incident opens

**Correct: A.** PIM provides eligible role assignments and controlled, time-bound activation with configurable approval and authentication requirements. [R1]

**Why the others are wrong:** B Conditional Access evaluates sign-in conditions; it does not assign or activate directory roles. [R1][R2] C authentication methods control how users authenticate, not role assignment. [R3] D Sentinel detects and responds to incidents; it is not the directory role governance service. [R4]

**References:** [R1] [Configure Microsoft Entra PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure); [R2] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R3] [Manage authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods); [R4] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview).

### Question 2 - Require phishing-resistant authentication for administrators

An organization requires privileged users to use phishing-resistant authentication when accessing administrative cloud apps. The policy should apply based on user and app context, not just a trusted network location. Which control best meets the requirement?

A. A Conditional Access policy targeting privileged users and administrative apps that requires a phishing-resistant authentication strength
B. A named location marking every corporate IP as trusted, with no MFA requirement
C. A password protection policy that blocks common passwords
D. A PIM approval workflow without a sign-in authentication condition

**Correct: A.** Conditional Access can apply authentication-strength requirements to targeted users and cloud apps, including phishing-resistant methods when appropriately configured. [R1][R2]

**Why the others are wrong:** B trusts network location and removes the requested authentication control; location alone does not prove identity. [R1] C password protection helps prevent weak or known-compromised passwords but does not enforce phishing-resistant authentication. [R3] D PIM governs privileged activation; approval alone does not impose the specified sign-in authentication strength. [R1][R4]

**References:** [R1] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R2] [Authentication strengths in Conditional Access](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths); [R3] [Microsoft Entra password protection](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad); [R4] [Configure PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).

### Question 3 - Authenticate an Azure-hosted workload to Azure resources

A workload running on an Azure virtual machine must read a secret from Key Vault. The team must not store a client secret in application settings and must grant only the required access. What should you configure?

A. A managed identity for the VM and a least-privilege Key Vault data-plane role for that identity
B. A client secret embedded in the VM image and subscription Owner for its service principal
C. A user-delegation SAS for the Key Vault secret
D. A Conditional Access named location using the VM's subnet

**Correct: A.** A managed identity obtains Entra tokens without the application storing credentials. Assigning only the required Key Vault data-plane permission follows least privilege. [R1][R2]

**Why the others are wrong:** B creates a reusable secret and grants excessive control. [R1][R2] C SAS is an Azure Storage authorization mechanism, not a Key Vault secret credential. [R3] D named locations inform sign-in policies; they do not authenticate a workload or grant Key Vault data access. [R4]

**References:** [R1] [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview); [R2] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault); [R3] [Azure Storage SAS overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview); [R4] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).

### Question 4 - Restrict Key Vault network access

An application in a virtual network needs Key Vault access. Security policy requires a private IP path, no public network access, and a managed identity with only secret-read permission. Which design meets the requirements?

A. Create a Key Vault private endpoint, configure private DNS, disable public network access, and grant the app identity the minimum data-plane role
B. Add the application's public IP to the vault firewall and grant subscription Contributor
C. Use a service endpoint, leave Key Vault open to all networks, and grant the VM Owner
D. Put the secret in an NSG rule and use the VM's system-assigned identity as a network route

**Correct: A.** Private Link supplies private connectivity to Key Vault; private DNS resolves the vault name to the endpoint. Disabling public access and assigning a narrow data-plane role addresses the network and identity requirements. [R1][R2]

**Why the others are wrong:** B allows public connectivity and grants excessive management permissions. [R1][R2] C leaves the public service path available and over-privileges the VM. [R1][R2] D NSGs do not store secrets or route managed identities; identity and network controls are separate. [R1][R3]

**References:** [R1] [Key Vault network security](https://learn.microsoft.com/en-us/azure/key-vault/general/network-security); [R2] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 5 - Enforce a resource configuration baseline

A governance team must prevent new storage accounts from allowing public blob access, continuously assess existing resources against the same requirement, and remediate noncompliant deployments. Which Azure capability should be used?

A. An Azure Policy definition or initiative with an appropriate deny effect for new resources and audit/remediation controls for existing resources
B. A Microsoft Sentinel analytics rule that blocks ARM deployments
C. An Azure RBAC role assignment that automatically changes storage account properties
D. A Microsoft Purview retention label applied to storage accounts

**Correct: A.** Azure Policy evaluates resource properties against definitions and can deny noncompliant requests or identify and remediate noncompliant resources, depending on the policy effect and configuration. [R1]

**Why the others are wrong:** B Sentinel analyzes security events and does not enforce ARM resource configuration at deployment. [R2] C RBAC controls who can perform actions; it does not itself enforce a property value across deployments. [R3] D retention labels govern information lifecycle, not Azure resource configuration. [R4]

**References:** [R1] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R2] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R3] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R4] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 6 - Protect backup operations from a compromised administrator

A ransomware response plan requires immutable Azure Backup recovery points and independent approval before a privileged user can disable protection or delete backup data. Which two controls should you combine? **Select two.**

A. Configure vault immutability to protect recovery points during the required retention period
B. Use Resource Guard multi-user authorization (MUA) with an independently controlled approver for protected operations
C. Give the backup administrator Owner on both the vault and its Resource Guard
D. Disable soft delete and allow the backup administrator to purge recovery points
E. Use an Azure Firewall policy as the approval workflow for vault operations

**Correct: A, B.** Immutable vault settings protect backup data against modification or deletion during the configured period. Resource Guard MUA adds an independent authorization boundary for protected operations. [R1][R2]

**Why the others are wrong:** C defeats separation of duties by giving one administrator control of both the protected resource and authorization boundary. [R2] D weakens deletion protection and conflicts with recoverability. [R1] E Azure Firewall filters network traffic; it does not approve Azure Backup operations. [R3]

**References:** [R1] [Azure Backup security features](https://learn.microsoft.com/en-us/azure/backup/backup-azure-security-feature); [R2] [Multi-user authorization using Resource Guard](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept); [R3] [Azure Firewall overview](https://learn.microsoft.com/en-us/azure/firewall/overview).
### Question 7 - Review application permission grants

A security team must identify which Microsoft Graph permissions have been granted to a multitenant application, determine whether admin consent was given, and revoke an unneeded grant. Which area is designed for reviewing and managing an enterprise application's granted permissions?

A. The enterprise application's Permissions view, with the appropriate admin-consent and revocation controls
B. The app registration's Branding settings
C. The Azure Key Vault firewall pane
D. The Azure Policy compliance dashboard

**Correct: A.** The enterprise application (service principal) exposes the application's granted permissions and consent state for review; administrators can manage grants according to tenant consent policy. [R1][R2]

**Why the others are wrong:** B branding configures presentation and publisher information, not API permission grants. [R1] C Key Vault firewall controls network access to a vault, not Entra application consent. [R3] D Azure Policy evaluates Azure resource configuration, not OAuth permission grants. [R4]

**References:** [R1] [Manage application permissions in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-application-permissions); [R2] [Application objects and service principals](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals); [R3] [Key Vault network security](https://learn.microsoft.com/en-us/azure/key-vault/general/network-security); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 8 - Find exposed secrets and protect Key Vault

The security team needs (1) to discover exposed secrets in connected code repositories and (2) to detect suspicious activity against Azure Key Vaults. Which two Defender for Cloud capabilities should it use? **Select two.**

A. Defender CSPM secret scanning for supported repositories and DevOps resources
B. Defender for Key Vault threat protection for supported vault activity
C. Defender for Storage as the code-repository secret scanner and Key Vault threat detector
D. Azure Bastion as the vault audit and repository-scanning engine
E. Azure Policy deny assignments as real-time Key Vault threat detection

**Correct: A, B.** Defender CSPM secret scanning can help identify exposed secrets in supported DevOps environments; Defender for Key Vault detects threats involving supported Key Vault resources. [R1][R2][R3]

**Why the others are wrong:** C Defender for Storage protects storage resources and does not replace secret scanning or Defender for Key Vault. [R1][R2][R4] D Bastion provides VM connectivity, not repository scanning or vault threat analytics. [R5] E Azure Policy evaluates resource configuration; it is not a runtime Key Vault threat-detection service. [R2][R6]

**References:** [R1] [Scan for secrets with Defender CSPM](https://learn.microsoft.com/en-us/azure/defender-for-cloud/secret-scanning); [R2] [Defender for Key Vault](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-key-vault-introduction); [R3] [SC-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500); [R4] [Defender for Storage](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction); [R5] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R6] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

## Domain 2: Secure storage, databases, and networking

### Question 9 - Remove public access to a storage account

A business-critical blob container must be reachable by an application in one VNet through a private IP. Internet access to the storage account must be disabled. Which design best meets the requirement?

A. Configure a private endpoint for the required storage subresource, private DNS, and disable public network access
B. Enable a service endpoint and allow the storage account's public endpoint from all networks
C. Add an NSG to the storage account and assume it disables its public endpoint
D. Create a public SAS URL and restrict access only by obscurity

**Correct: A.** A private endpoint maps the supported storage service to a private IP in the VNet; private DNS provides the expected name resolution. Disabling public network access removes the public path where supported. [R1][R2]

**Why the others are wrong:** B uses the public service endpoint and explicitly permits all networks, contrary to the requirement. [R1] C NSGs apply to supported subnet/NIC traffic; they do not attach to the storage account or disable its public endpoint. [R3] D uses an internet-reachable bearer token and does not establish private connectivity. [R4]

**References:** [R1] [Azure Storage network security](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security); [R2] [Azure Private Link overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Storage SAS overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview).

### Question 10 - Authorize blob access without account keys

An application must read blobs but must not be able to change storage account configuration or retrieve account keys. Which authorization design is best?

A. Assign the application's managed identity the Storage Blob Data Reader role at the required container or account scope
B. Assign the application Contributor on the subscription
C. Store the storage account key in application settings and grant the identity Owner
D. Assign the Reader management-plane role and assume it grants blob data reads

**Correct: A.** A scoped Storage Blob Data Reader data-plane role authorizes read operations on blob content without granting account-management permissions; a managed identity avoids stored credentials. [R1][R2]

**Why the others are wrong:** B subscription Contributor grants broad management-plane permissions and exceeds the requested access. [R2] C exposes an account key and grants excessive privilege. [R1][R2] D Azure management-plane Reader does not by itself grant access to blob data. [R1][R2]

**References:** [R1] [Authorize access to blobs using Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/storage/blobs/authorize-access-azure-active-directory); [R2] [Azure built-in roles for storage](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/storage).

### Question 11 - Issue constrained delegated access to blobs

A partner needs temporary read access to a specific blob. The organization requires Entra-backed delegation, least privilege, and no account key in the sharing workflow. Which credential should be issued?

A. A user delegation SAS scoped to the blob with read-only permission and a short expiry
B. A long-lived account SAS with broad service and resource permissions
C. The storage account access key in an email
D. A subscription Contributor assignment to the partner

**Correct: A.** A user delegation SAS is signed using a user delegation key obtained through Microsoft Entra credentials and can be narrowly scoped and time-bounded. [R1][R2]

**Why the others are wrong:** B grants broader, longer-lived access and is not the requested Entra-backed delegation approach. [R1] C exposes a powerful shared credential rather than a constrained delegated token. [R1] D grants broad Azure management access unrelated to read access to one blob. [R2]

**References:** [R1] [Create a user delegation SAS](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-user-delegation-sas-create-cli); [R2] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview).

### Question 12 - Detect threats to Azure Storage

An organization needs alerts for suspicious activities targeting its storage accounts and wants Microsoft Defender to analyze storage-related threat signals. Which capability is designed for this?

A. Microsoft Defender for Storage, enabled for the relevant subscriptions or storage accounts and configured for the required protection
B. Defender for Key Vault, used to scan blob contents and storage transactions
C. Azure Policy alone, used as a real-time threat-detection analytics engine
D. Microsoft Purview retention, used to block all storage-account network connections

**Correct: A.** Defender for Storage provides threat-protection capabilities for supported storage resources, including detection based on storage activity and configured protections. [R1]

**Why the others are wrong:** B Defender for Key Vault focuses on Key Vault threats, not storage-account threat protection. [R2] C Azure Policy evaluates resource configuration and compliance; it is not the storage threat analytics service. [R3] D retention governs data lifecycle and does not block storage network connections. [R4]

**References:** [R1] [Microsoft Defender for Storage](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction); [R2] [Microsoft Defender for Key Vault](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-key-vault-introduction); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 13 - Audit Azure SQL Database activity

A security team needs a tamper-resistant history of database events for investigations and wants to detect database threat patterns. Which two controls should the architect configure? **Select two.**

A. Azure SQL Auditing, sending audit events to an appropriately protected destination with retention suited to policy
B. Defender for SQL/Defender for Databases protection for supported database threat detection
C. An NSG flow log as the only record of SQL statements and database identities
D. A storage account SAS as the SQL database auditing policy
E. A SQL firewall rule as a substitute for auditing and threat detection

**Correct: A, B.** Azure SQL Auditing records configured database events to a selected destination. Defender for Databases provides additional threat-protection capabilities; auditing and threat detection serve complementary purposes. [R1][R2]

**Why the others are wrong:** C network flow logs do not record SQL statements or provide a complete database audit trail. [R1] D a storage SAS is a storage authorization token, not an SQL auditing configuration. [R1] E firewall rules control connectivity but do not record database activity or detect database threats. [R1][R2]

**References:** [R1] [Azure SQL auditing overview](https://learn.microsoft.com/en-us/azure/azure-sql/database/auditing-overview); [R2] [Microsoft Defender for Databases](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-databases-introduction).

### Question 14 - Centralize network security rules across VNets

A company manages many Azure virtual networks. Network security teams need centrally applied security-admin rules while workload teams retain their subnet NSGs. Which design best fits?

A. Use Azure Virtual Network Manager network groups and a security admin configuration, alongside NSGs for workload-level filtering
B. Replace all NSGs with Microsoft Sentinel analytics rules
C. Use Azure Policy alone as a stateful inline network firewall
D. Assign Azure RBAC Reader to the network team and expect it to filter packets

**Correct: A.** Azure Virtual Network Manager can group VNets and deploy centrally managed security admin rules; NSGs continue to provide subnet/NIC-level network security rules. [R1][R2]

**Why the others are wrong:** B Sentinel is a SIEM/SOAR service, not an inline network filter or NSG replacement. [R3] C Azure Policy governs resource configuration; it is not a stateful packet-filtering service. [R4] D Reader grants visibility, not the ability to enforce packet filtering. [R2]

**References:** [R1] [Azure Virtual Network Manager overview](https://learn.microsoft.com/en-us/azure/virtual-network-manager/overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

## Domain 3: Secure compute

### Question 15 - Assess AI-related data exposure before rollout

Before enabling Microsoft 365 Copilot broadly, a company wants to identify sensitive SharePoint content and excessive sharing that could expose information through AI-assisted discovery. Which capability is designed to assess and help manage this data risk?

A. Microsoft Purview Data Security Posture Management (DSPM) for AI
B. Azure DDoS Protection
C. Entra Privileged Identity Management, used as the SharePoint content scanner
D. Azure Bastion

**Correct: A.** Purview DSPM for AI helps organizations understand and manage data security risks associated with AI use, including sensitive data and oversharing risks relevant to Copilot. [R1]

**Why the others are wrong:** B DDoS Protection mitigates network denial-of-service attacks, not content exposure to AI. [R2] C PIM governs privileged access; it does not scan or assess SharePoint content exposure. [R3] D Bastion provides secure VM administration, not data security posture assessment. [R4]

**References:** [R1] [Microsoft Purview and AI](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview); [R2] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R3] [Configure Microsoft Entra PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure); [R4] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview).

### Question 16 - Apply access policy to AI agent identities

An organization uses Microsoft Entra Agent ID for AI agents. A security architect must enforce contextual access requirements for an agent identity and investigate how that identity's access could affect other resources. Which pair of controls aligns with the SC-500 objectives?

A. Apply Conditional Access to the agent identity and use Defender XDR to analyze the identity's potential blast radius
B. Use a storage account firewall for Conditional Access and Purview retention to calculate identity blast radius
C. Use a Sentinel workspace as the agent's identity provider and an NSG as its role assignment system
D. Assign every agent permanent Global Administrator and use Azure Policy to detect sign-ins

**Correct: A.** The SC-500 study guide explicitly includes Conditional Access for Microsoft Entra Agent ID and blast-radius analysis for Entra Agent ID risks using Defender XDR. [R1][R2][R3]

**Why the others are wrong:** B storage firewalls control storage network access, while retention does not evaluate identity relationships or blast radius. [R4][R5] C Sentinel is a SIEM, not an identity provider, and NSGs do not assign Entra roles. [R2][R6] D permanent Global Administrator violates least privilege; Azure Policy governs Azure resources and is not a sign-in analytics service. [R7][R8]

**References:** [R1] [SC-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500); [R2] [Microsoft Entra Agent ID overview](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/what-is-agent-id); [R3] [Microsoft Defender XDR overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender); [R4] [Azure Storage network security](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security); [R5] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention); [R6] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R7] [Microsoft Entra PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure); [R8] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 17 - Govern AI model access through an AI gateway

A company deploys Microsoft Foundry models and wants a centralized gateway for API access, model endpoint routing, usage controls, and policy enforcement. Which design best meets the requirement?

A. Configure the Azure API Management AI Gateway for the Foundry APIs, applying suitable authentication and rate/token-consumption policies
B. Publish model endpoints directly to the internet and use an NSG as the model-aware token quota system
C. Use Azure Backup as the API gateway and model router
D. Use a Key Vault access policy to throttle prompts and route requests between models

**Correct: A.** Azure API Management's AI Gateway capabilities support centralized management and governance of AI API traffic, including policies for authentication, usage, and routing when configured for the supported Foundry integration. [R1][R2]

**Why the others are wrong:** B NSGs filter network traffic; they do not inspect model API usage or enforce model-aware quotas. [R1][R3] C Azure Backup protects data for recovery, not API traffic. [R4] D Key Vault protects secrets and keys; it does not function as an AI API gateway or token-throttling service. [R5]

**References:** [R1] [AI gateway capabilities in Azure API Management](https://learn.microsoft.com/en-us/azure/api-management/genai-gateway-capabilities); [R2] [Configure AI Gateway for Foundry resources](https://learn.microsoft.com/en-us/azure/foundry/configuration/enable-ai-api-management-gateway-portal); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Backup overview](https://learn.microsoft.com/en-us/azure/backup/backup-overview); [R5] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault).

### Question 18 - Administer VMs without public IPs

Administrators must connect to Azure VMs using RDP or SSH, but the VM NICs must not have public IP addresses. The organization wants a managed browser-based access path over TLS. What should you deploy?

A. Azure Bastion in the VNet containing or peered to the target VMs
B. Azure DDoS Protection on each VM
C. Microsoft Sentinel as an RDP proxy
D. An NSG rule that exposes RDP and SSH to all internet addresses

**Correct: A.** Azure Bastion provides RDP/SSH connectivity over TLS through supported client experiences without requiring public IPs on target VMs. [R1]

**Why the others are wrong:** B DDoS Protection helps mitigate denial-of-service attacks and does not provide administrative connectivity. [R2] C Sentinel is a security analytics platform, not an RDP proxy. [R3] D exposes management ports broadly and violates the no-public-access requirement. [R1][R4]

**References:** [R1] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R2] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R3] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 19 - Limit VM management port exposure

Security operations requires just-in-time access to supported Azure VMs: close management ports by default, open them only for an approved request, and restrict the permitted source and duration. Which capability should be configured?

A. Just-in-time VM access in Microsoft Defender for Cloud
B. Azure Bastion host scaling as a substitute for port authorization
C. A permanent NSG allow rule for RDP and SSH from any source
D. Entra access reviews for VM network ports

**Correct: A.** Defender for Cloud JIT access reduces exposure by opening selected management ports for a limited period in response to authorized requests, subject to supported resources and configuration. [R1]

**Why the others are wrong:** B Bastion provides a secure connection path but does not itself satisfy the requested JIT port-opening workflow. [R1][R2] C permits permanent, unrestricted exposure rather than just-in-time access. [R1][R3] D access reviews govern user/group/role access, not network port rules. [R4]

**References:** [R1] [JIT VM access in Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/just-in-time-access-usage); [R2] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview).

### Question 20 - Extend server protection to hybrid and multicloud

An organization needs to manage servers in Azure, on-premises, and AWS through a consistent Azure control plane and apply Defender for Servers protections. What is the appropriate approach?

A. Connect supported non-Azure servers with Azure Arc, then onboard them to Defender for Cloud and configure Defender for Servers
B. Install Microsoft Sentinel on each server and treat the agent as its Azure resource manager
C. Assign an Azure NSG to each on-premises host without Arc onboarding
D. Use Purview retention labels to register server operating systems

**Correct: A.** Azure Arc-enabled servers brings supported machines outside Azure into Azure management. Defender for Cloud can then apply supported security posture and Defender for Servers capabilities when appropriately configured and licensed. [R1][R2]

**Why the others are wrong:** B Sentinel collects and analyzes security data; it is not the Azure Arc management plane. [R1][R3] C an NSG does not onboard or manage on-premises hosts. [R4] D retention labels classify and govern data, not server inventory or protection. [R5]

**References:** [R1] [Azure Arc-enabled servers overview](https://learn.microsoft.com/en-us/azure/azure-arc/servers/overview); [R2] [Defender for Servers](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-introduction); [R3] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R5] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 21 - Detect container workload risks

A platform team runs Kubernetes workloads on Azure Kubernetes Service (AKS). It needs security posture findings for clusters and container images, plus workload threat protection. Which approach best fits?

A. Configure Defender for Containers in Defender for Cloud and apply the relevant AKS security controls
B. Use Defender for Storage as the only container image and Kubernetes threat-protection service
C. Use Azure SQL Auditing to scan container images
D. Rely only on an NSG; network rules provide image vulnerability assessment and cluster posture management

**Correct: A.** Defender for Containers provides supported container security capabilities, while AKS security controls address cluster and workload configuration. Coverage depends on plan, configuration, and supported features. [R1][R2]

**Why the others are wrong:** B Defender for Storage protects storage resources, not container clusters and images. [R1][R3] C SQL auditing records database events and does not inspect container images. [R4] D NSGs filter network traffic; they do not provide image vulnerability or cluster posture assessment. [R2][R5]

**References:** [R1] [Defender for Containers](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-containers-introduction); [R2] [AKS security concepts](https://learn.microsoft.com/en-us/azure/aks/concepts-security); [R3] [Defender for Storage](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction); [R4] [Azure SQL auditing](https://learn.microsoft.com/en-us/azure/azure-sql/database/auditing-overview); [R5] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 22 - Protect a public App Service application

A public web application runs on Azure App Service. Security requires inspection for common web exploits and that the application receive requests through a protected application delivery tier. Which design best meets the requirement?

A. Place a supported Web Application Firewall (WAF) in front of the app and configure the App Service access restrictions/networking to accept only the intended ingress path
B. Use an NSG alone to inspect HTTP payloads for SQL injection
C. Use Azure DDoS Protection as the only web application firewall
D. Enable Purview retention labels on the App Service plan

**Correct: A.** A WAF can inspect HTTP(S) requests for common web exploits; restricting App Service ingress to the intended protected path prevents clients from bypassing that layer, subject to the chosen architecture and supported configuration. [R1][R2]

**Why the others are wrong:** B NSGs filter network flows and do not inspect HTTP payloads for application-layer exploits. [R1][R3] C DDoS Protection mitigates network-layer DDoS attacks, not common application-layer web attacks. [R1][R4] D retention labels govern content lifecycle, not app ingress or request inspection. [R5]

**References:** [R1] [Azure Web Application Firewall overview](https://learn.microsoft.com/en-us/azure/web-application-firewall/overview); [R2] [App Service security overview](https://learn.microsoft.com/en-us/azure/app-service/overview-security); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R5] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention).

## Domain 4: Manage and monitor security posture

### Question 23 - Assess multicloud security posture

A company connects Azure subscriptions, AWS accounts, and Google Cloud projects. The security team needs prioritized posture recommendations and attack-risk visibility across the connected cloud estate. Which service is the best fit?

A. Microsoft Defender for Cloud, using its cloud security posture management (CSPM) capabilities and supported multicloud connectors
B. Microsoft Sentinel as the only resource configuration benchmark
C. Azure Bastion for AWS and Google Cloud posture assessment
D. Microsoft Purview retention labels for cloud-resource attack paths

**Correct: A.** Defender for Cloud CSPM provides security posture recommendations and supported multicloud visibility when the environments are connected and configured. [R1][R2][R3]

**Why the others are wrong:** B Sentinel is a SIEM/SOAR platform for security data and incident response, not a substitute for CSPM. [R1][R4] C Bastion provides VM administrative connectivity; it does not assess cloud posture. [R5] D retention labels govern content, not cloud-resource configuration or attack paths. [R6]

**References:** [R1] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R2] [Onboard AWS to Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-aws); [R3] [Onboard GCP to Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-gcp); [R4] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R5] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R6] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 24 - Evaluate regulatory compliance

An auditor wants to assess cloud resources against supported regulatory standards, review failed controls, and track recommendations to improve compliance. Which capability should be used?

A. The regulatory compliance dashboard in Microsoft Defender for Cloud
B. Defender XDR advanced hunting as a replacement for resource compliance assessments
C. Entra access reviews as the source of Azure configuration-control results
D. Azure Bastion to run compliance assessments on every cloud resource

**Correct: A.** Defender for Cloud maps supported assessments to regulatory standards and presents failed controls and related recommendations. Coverage depends on connected environments and enabled plans. [R1][R2]

**Why the others are wrong:** B advanced hunting queries security data; it is not the Defender for Cloud regulatory compliance assessment experience. [R1][R3] C access reviews recertify user access, not resource configuration compliance. [R4] D Bastion supplies administrative connectivity and does not assess regulatory controls. [R5]

**References:** [R1] [Defender for Cloud regulatory compliance dashboard](https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard); [R2] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R3] [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview); [R4] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview); [R5] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview).

### Question 25 - Ingest Linux security and network appliance events

A company needs Linux host and network-appliance Syslog/CEF events in Microsoft Sentinel, collected through Azure Monitor Agent (AMA) with centrally managed collection configuration. Which design is appropriate?

A. Deploy AMA to supported hosts, configure the Syslog/CEF connector and data collection rules (DCRs), then send data to the intended Sentinel workspace
B. Install a Sentinel analytics rule on each appliance and send no events to a workspace
C. Use a storage-account SAS as the log collector and disable the Sentinel data connector
D. Configure Azure Policy to transform each Syslog event into a Sentinel incident

**Correct: A.** The Syslog via AMA connector and DCRs configure collection from supported Linux machines and forward the selected facility/severity data into the connected Log Analytics/Sentinel workspace. [R1][R2]

**Why the others are wrong:** B analytics rules run over ingested workspace data; they are not host agents or event-forwarding configuration. [R1][R3] C SAS authorizes storage access and does not collect Syslog into Sentinel. [R1] D Azure Policy governs Azure resource configuration; it does not parse and ingest event streams. [R4]

**References:** [R1] [Collect Syslog data with Azure Monitor Agent](https://learn.microsoft.com/en-us/azure/sentinel/data-connectors/syslog-via-ama); [R2] [Connect data sources to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources); [R3] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 26 - Collect Windows Security events

A security operations team needs Windows Security events from a fleet of Windows servers in Sentinel. It wants centrally managed event selection using supported Azure Monitor collection components. Which approach best fits?

A. Configure the Windows Security Events via AMA connector with DCRs, and use Windows Event Forwarding where the collection architecture requires it
B. Enable the Syslog connector on every Windows host and send all events to an NSG
C. Use a Purview retention label as the Windows event forwarder
D. Query each host locally with Defender XDR advanced hunting and do not connect events to Sentinel

**Correct: A.** The Windows Security Events via AMA connector uses Azure Monitor Agent and DCRs to select and collect supported Windows Security events; Windows Event Forwarding is supported for applicable collection designs. [R1][R2]

**Why the others are wrong:** B Syslog/NSGs are not the Windows Security Events via AMA pipeline; an NSG is not a log destination. [R1][R3] C retention labels govern content, not event collection. [R4] D local queries do not centrally ingest the events into Sentinel as required. [R1][R5]

**References:** [R1] [Collect Windows Security events with AMA](https://learn.microsoft.com/en-us/azure/sentinel/data-connectors/windows-security-events-via-ama); [R2] [Connect data sources to Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Microsoft Purview retention](https://learn.microsoft.com/en-us/purview/retention); [R5] [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview).

### Question 27 - Grant Sentinel incident triage permissions

A user must investigate and update Sentinel incidents but must not administer data connectors or change analytics rules. Which role should be assigned at the appropriate Sentinel workspace scope?

A. Microsoft Sentinel Responder
B. Microsoft Sentinel Reader
C. Microsoft Sentinel Contributor
D. Azure subscription Owner

**Correct: A.** Sentinel Responder can investigate and manage incidents without the broader configuration permissions of Contributor or Owner. Assign it at the narrowest suitable scope. [R1]

**Why the others are wrong:** B Reader provides read-only access and cannot perform the required incident updates. [R1] C Contributor grants broader management capabilities, including configuration actions beyond incident triage. [R1] D subscription Owner grants excessive control over all subscription resources. [R2]

**References:** [R1] [Microsoft Sentinel roles and permissions](https://learn.microsoft.com/en-us/azure/sentinel/roles); [R2] [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles).

### Question 28 - Automate incident response

When a high-severity Sentinel incident is created, the operations team wants an automatic workflow to enrich the incident and notify the on-call team, while retaining the ability to use the playbook for other supported response actions. What should you configure?

A. A Sentinel automation rule that invokes an Azure Logic Apps playbook under the appropriate managed identity and permissions
B. An Azure Policy deny assignment that sends email when an analytics rule matches
C. A Conditional Access policy that runs a Logic Apps workflow after every sign-in
D. A Key Vault firewall rule that enriches Sentinel incidents

**Correct: A.** Sentinel automation rules can orchestrate incident handling and invoke playbooks; playbooks are Logic Apps workflows that perform configured response actions. [R1][R2]

**Why the others are wrong:** B Azure Policy evaluates resource configuration and is not the incident automation engine. [R3] C Conditional Access controls access decisions, not Sentinel incident workflows. [R4] D Key Vault firewall rules restrict network access and do not automate security operations. [R5]

**References:** [R1] [Automate responses with Microsoft Sentinel playbooks](https://learn.microsoft.com/en-us/azure/sentinel/automation/automate-responses-with-playbooks); [R2] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R5] [Key Vault network security](https://learn.microsoft.com/en-us/azure/key-vault/general/network-security).

### Question 29 - Discover an organization's external attack surface

A company wants to discover internet-facing assets associated with its organization, including assets unknown to its internal inventory, and prioritize external exposure for investigation. Which capability is designed for this purpose?

A. Microsoft Defender External Attack Surface Management (EASM)
B. Azure Bastion
C. Microsoft Purview Data Loss Prevention
D. Microsoft Entra access reviews

**Correct: A.** Defender EASM discovers and maps an organization's external, internet-facing attack surface to help identify and prioritize exposed assets. [R1][R2]

**Why the others are wrong:** B Bastion provides secure VM administration, not external asset discovery. [R3] C DLP detects and helps control sensitive data movement, not public asset exposure. [R4] D access reviews recertify identities' access, not discover internet-facing infrastructure. [R5]

**References:** [R1] [Microsoft Defender External Attack Surface Management overview](https://learn.microsoft.com/en-us/azure/external-attack-surface-management/overview); [R2] [SC-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500); [R3] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R4] [Purview DLP](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp); [R5] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview).

### Question 30 - Investigate Microsoft Purview audit activity from Defender XDR

An investigator needs to search for Microsoft Purview audit activities using Defender XDR's hunting experience. Which approach best matches the requirement?

A. Use the supported Purview Audit data in Defender XDR advanced hunting, and use Purview Audit search when a broader audit-search workflow is required
B. Use Azure NSG flow logs as the authoritative record of Microsoft 365 user audit events
C. Use Azure Policy compliance results as the audit-event query language
D. Use an Azure Storage SAS to query the Purview audit portal

**Correct: A.** The SC-500 guide specifically includes querying Microsoft Purview Audit in Defender XDR. Advanced hunting queries supported Defender XDR data; Purview Audit search remains the audit-search experience for its supported workloads and retention. [R1][R2][R3]

**Why the others are wrong:** B NSG flow logs record network flows, not Microsoft 365 audit activities. [R1] C Azure Policy evaluates resource configuration; it is not an audit-event query system. [R4] D a storage SAS does not authenticate to Defender XDR or Purview Audit. [R2][R3]

**References:** [R1] [SC-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500); [R2] [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview); [R3] [Search the audit log](https://learn.microsoft.com/en-us/purview/audit-search); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 31 - Scope Microsoft Security Copilot access and plugins

A security team is enabling Microsoft Security Copilot. Analysts should use only the capabilities approved for their role, and integrations should be deliberately enabled rather than exposing every connected service to all users. Which approach is best?

A. Configure the Security Copilot access roles and workspace permissions, then enable and govern only the required plugins for the intended users
B. Give every analyst Global Administrator and enable all plugins without review
C. Share one administrator's credentials with all analysts and disable auditing
D. Use an Azure NSG to assign Security Copilot roles and filter prompts by user identity

**Correct: A.** Security Copilot has role and access configuration and uses plugins to connect supported services. Least-privilege access and deliberate plugin configuration limit who can use which integrations. [R1][R2]

**Why the others are wrong:** B grants excessive privilege and makes integrations available without governance. [R1][R2] C shared credentials undermine accountability and secure access. [R1] D NSGs filter network traffic; they do not grant application roles or govern Security Copilot plugins. [R3]

**References:** [R1] [Get started with Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot); [R2] [Manage Security Copilot plugins](https://learn.microsoft.com/en-us/security-copilot/manage-plugins); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

## Further study

Use the [SC-500 certification page](https://learn.microsoft.com/en-us/credentials/certifications/cloud-and-ai-security-engineer-associate/) and the [official SC-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500) for the current exam scope and skills measured. The following Microsoft Learn resources and [CertCrush video playlist](https://www.youtube.com/playlist?list=PLUYir_dGcUeA) are supplementary: [SC-500T00 course](https://learn.microsoft.com/en-us/training/courses/sc-500t00), [Secure access with Microsoft Entra](https://learn.microsoft.com/en-us/training/paths/secure-access-resources-entra/), [Secure Azure Key Vault](https://learn.microsoft.com/en-us/training/paths/configure-key-vault-security/), [Security governance and regulatory compliance](https://learn.microsoft.com/en-us/training/paths/security-governance-compliance/), [Azure Storage security](https://learn.microsoft.com/en-us/training/paths/implement-azure-storage-security/), and [Azure SQL Database security](https://learn.microsoft.com/en-us/training/paths/implement-azure-sql-database-security/). Microsoft Learn is the authority for exam scope and product behavior.