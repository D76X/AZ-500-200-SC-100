# AZ-500 Practice Tests

Original, unofficial practice questions aligned to the **final published AZ-500: Microsoft Azure Security Technologies** skills. These questions are not reproduced from the live exam.

> **Retirement notice:** Microsoft's published retirement date for the AZ-500 exam, certification, and renewal assessment is **August 31, 2026**. This bank covers the published AZ-500 objectives but cannot be used to earn or renew the certification after that date. Check the [official exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-500/) and [final AZ-500 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-500) for current status. AZ-500 preparation should not be assumed to cover the different objectives of any current certification.
>
> Select the number of answers requested. Unless stated otherwise, choose the single best answer. Each question includes its rationale, explanations for incorrect choices, and Microsoft Learn references. Product availability and licensing can change.

## Domain 1: Secure identity and access (15–20%)

### Question 1 - Use just-in-time Azure role assignments

A team member needs Contributor access to a production subscription only when performing approved maintenance. The organization requires just-in-time activation, time limits, MFA, and an approval step. Which configuration best meets the requirement?

B. Assign the user as eligible for the Azure resource role in Microsoft Entra Privileged Identity Management (PIM), then configure activation controls
C. Grant permanent Owner at the tenant root and require a monthly access review
D. Add the user to a Conditional Access named location
A. Create an Azure Policy assignment that grants Contributor when the resource is compliant

**Correct: B.** PIM supports eligible Azure resource role assignments with time-bound activation and configurable approval and authentication controls. Assign the role at the narrowest required scope. [R1][R2]

**Why the others are wrong:** C grants excessive standing privilege and monthly review is not just-in-time activation. [R1][R2] D named locations provide sign-in context, not role assignment or activation. [R3] A Azure Policy evaluates resource properties and does not grant Azure RBAC roles based on compliance. [R4]

**References:** [R1] [Assign Azure resource roles in PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-assign-roles); [R2] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R3] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 2 - Require compliant devices for Azure access

All administrators must use MFA and access Azure management from compliant devices. The organization wants the requirement evaluated at sign-in. Which solution should you configure?

C. A Conditional Access policy targeting the administrative users and Azure management resource, requiring MFA and a compliant device
D. An NSG rule that permits traffic only from corporate IP ranges
A. An Azure Policy that audits VM compliance
B. A PIM role activation approval without a sign-in policy

**Correct: C.** Conditional Access evaluates user, application, and sign-in conditions and can require MFA and a compliant device for the selected cloud resource. Ensure exclusions and emergency access accounts are designed safely. [R1][R2]

**Why the others are wrong:** D an NSG filters network traffic and does not enforce device compliance or MFA in Microsoft Entra. [R1][R3] A Azure Policy audits Azure resource configuration, not administrator sign-in conditions. [R4] B PIM approval governs role activation but does not replace a Conditional Access policy for every sign-in. [R1][R5]

**References:** [R1] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R2] [Require compliant devices with Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-compliance); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R5] [Configure PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).

### Question 3 - Restrict risky OAuth consent

A tenant wants to prevent users from granting third-party applications high-impact OAuth permissions without administrator review. Security administrators must be able to inspect grants and revoke inappropriate consent. Which approach is best?

D. Configure Microsoft Entra user-consent settings to restrict or allow only low-risk verified publisher permissions, and review application permission grants using the enterprise application permissions view
A. Allow all user consent and rely on Azure Policy to inspect OAuth grants
B. Use a storage account firewall to block application consent
C. Configure an NSG rule that denies Microsoft Graph permissions

**Correct: D.** Entra consent settings govern whether users can grant application permissions; enterprise application permission views allow administrators to inspect consent and manage grants. [R1][R2]

**Why the others are wrong:** A Azure Policy governs Azure resources and does not evaluate Entra OAuth consent grants. [R1][R3] B storage firewalls control storage network access, not directory application consent. [R4] C NSGs filter network traffic and cannot govern OAuth permission grants. [R5]

**References:** [R1] [User consent settings](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/configure-user-consent); [R2] [Manage application permissions](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-application-permissions); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Azure Storage network security](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security); [R5] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 4 - Authenticate an Azure workload without stored credentials

An Azure-hosted application needs to access another Azure resource. The organization forbids client secrets in application configuration and requires least-privilege authorization. What should you use?

A. A managed identity for the workload and a narrowly scoped Azure RBAC/data-plane role on the target resource
B. A client secret embedded in the container image and subscription Owner
C. A user account password stored in an app setting
D. An Azure resource tag containing the access key

**Correct: A.** Managed identities provide an Entra identity for supported Azure resources without the application managing credentials. Assign only the permissions needed at the smallest suitable scope. [R1][R2]

**Why the others are wrong:** B and C create long-lived credentials that can be exposed in images or configuration, and Owner is excessive. [R1][R2] D tags are metadata, not a credential vault or authorization mechanism. [R3]

**References:** [R1] [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview); [R2] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R3] [Azure resource tags](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources).

### Question 5 - Configure a custom API scope

An application registration will expose a custom delegated scope for another application. Which configuration is required before defining the scope?

B. Set the application's Application ID URI, then define the scope under Expose an API
C. Add an Azure RBAC Owner assignment to the app registration
D. Create a Conditional Access named location for the API
A. Configure a storage account service endpoint

**Correct: B.** The Application ID URI identifies the API and provides the resource identifier used in its scope values. After setting it, define the delegated scope under Expose an API and configure consent as required. [R1][R2]

**Why the others are wrong:** C Azure RBAC governs Azure resource access and does not define Microsoft Entra API scopes. [R3] D named locations are inputs to Conditional Access, not API scope configuration. [R4] A service endpoints secure VNet access to supported Azure services and are unrelated to app registration scopes. [R5]

**References:** [R1] [Configure an app to expose a web API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-configure-app-expose-web-apis); [R2] [Scopes and permissions in the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/scopes-oidc); [R3] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R4] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R5] [Virtual network service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview).
## Domain 2: Secure networking (20–25%)

### Question 6 - Restrict database traffic to an application tier

A three-tier workload uses web and database VMs in one VNet. The database must accept TCP 1433 only from the web tier, even as VM addresses change. Which design is most maintainable?

C. Associate application security groups with the web and database NICs, then use an NSG rule permitting TCP 1433 from the web ASG to the database tier
D. Allow TCP 1433 from `0.0.0.0/0` in a subnet NSG
A. Use a private DNS zone as the database firewall
B. Assign an Azure Traffic Manager profile to the database subnet

**Correct: C.** ASGs let NSG rules refer to workload roles rather than hard-coded IP addresses; the NSG can narrowly allow the database port from the web ASG. [R1][R2]

**Why the others are wrong:** D exposes the database port to any source and violates least privilege. [R1] A DNS resolves names but does not filter network flows. [R3] B Traffic Manager routes DNS clients and does not enforce subnet access. [R4]

**References:** [R1] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R2] [Application security groups](https://learn.microsoft.com/en-us/azure/virtual-network/application-security-groups); [R3] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 7 - Force subnet traffic through a security appliance

A workload subnet must send all outbound traffic to a centralized network virtual appliance for inspection. Which Azure networking control should direct the traffic?

D. A route table associated with the subnet, with a default user-defined route and the appliance's private IP as the virtual appliance next hop
A. An NSG allow rule for the appliance
B. A private DNS zone record pointing to the appliance
C. A load-balancer health probe

**Correct: D.** A user-defined route controls the next hop for subnet traffic. The NVA must also be configured to forward traffic and support the required return path. [R1]

**Why the others are wrong:** A NSGs allow or deny traffic but do not select the next hop. [R1][R2] B DNS affects name resolution, not general route selection. [R3] C a health probe tests backend health and does not modify routes. [R4]

**References:** [R1] [User-defined routes](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R4] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).

### Question 8 - Centrally manage security across virtual networks

A platform team needs to apply network security administrator rules to selected VNets across multiple subscriptions. Workload teams must not override centrally mandated rules. Which service should be used?

A. Azure Virtual Network Manager security admin configurations, scoped through network groups
B. Azure Traffic Manager
C. Microsoft Entra access reviews
D. Azure DNS Private Resolver

**Correct: A.** Virtual Network Manager security admin configurations centrally apply rules to network groups and support enforcement behavior relative to conflicting NSG rules. [R1]

**Why the others are wrong:** B Traffic Manager performs DNS endpoint routing. [R2] C access reviews recertify user access and do not govern packet filtering. [R3] D Private Resolver manages DNS forwarding, not network security rules. [R4]

**References:** [R1] [Security admin rules in Azure Virtual Network Manager](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-security-admins); [R2] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R3] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview); [R4] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview).

### Question 9 - Isolate PaaS traffic with a private endpoint

An Azure SQL Database must be reachable from a VNet using a private IP, and its public network path must be disabled. Which solution meets the requirement?

B. Create a private endpoint for the SQL resource, configure private DNS, and disable public network access
C. Use a service endpoint and allow the public endpoint from all networks
D. Add an NSG to the SQL logical server
A. Create a public DNS record pointing to an RFC1918 address

**Correct: B.** A private endpoint maps a supported PaaS service to a private IP in the VNet; private DNS provides correct name resolution. Disable public network access when the service and configuration support it. [R1][R2]

**Why the others are wrong:** C service endpoints secure a path to the service's public endpoint and do not assign it a private IP; opening all networks conflicts with the requirement. [R1][R3] D NSGs are associated with supported subnets/NICs, not the SQL logical server. [R4] A public DNS publishing a private address does not create private connectivity or prevent public access. [R2]

**References:** [R1] [Azure Private Link overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview); [R2] [Private endpoint DNS integration](https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-dns); [R3] [Virtual network service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 10 - Select a firewall tier for TLS inspection

A hub firewall must provide IDPS and TLS inspection for supported traffic. Which Azure Firewall tier should you select?

C. Azure Firewall Premium
D. Azure Firewall Basic
A. Azure NAT Gateway
B. A network security group

**Correct: C.** Azure Firewall Premium includes advanced capabilities such as IDPS and TLS inspection for supported scenarios. Validate certificate, protocol, and workload requirements. [R1][R2]

**Why the others are wrong:** D Basic is intended for simpler, lower-throughput needs and lacks the required Premium inspection features. [R1] A NAT Gateway performs outbound source NAT, not stateful inspection or IDPS. [R3] B NSGs filter network flows and cannot inspect TLS payloads. [R4]

**References:** [R1] [Choose the right Azure Firewall SKU](https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku); [R2] [Azure Firewall Premium features](https://learn.microsoft.com/en-us/azure/firewall/premium-features); [R3] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 11 - Block web exploits while retaining matched-request logs

A public web application needs protection against SQL injection and other common HTTP exploits. Matching requests must be logged and blocked. Which configuration meets the requirement?

D. Associate an Azure WAF policy in Prevention mode with the supported Application Gateway or Front Door
A. Configure WAF Detection mode; it blocks requests while logging them
B. Add an NSG rule that denies SQL injection patterns
C. Use Azure Traffic Manager priority routing

**Correct: D.** WAF Prevention mode logs and blocks requests that match its configured rules. Detection mode logs matches but does not block them. [R1][R2]

**Why the others are wrong:** A Detection mode is for monitoring and does not block matched requests. [R1] B NSGs filter IP/port/protocol flows and cannot inspect HTTP request bodies for SQL injection. [R3] C Traffic Manager routes DNS queries; it is not an HTTP inspection service. [R4]

**References:** [R1] [WAF on Application Gateway](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview); [R2] [WAF on Azure Front Door](https://learn.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 12 - Administer VMs without public IP addresses

Administrators need browser-based RDP and SSH connectivity to Azure VMs. VM NICs must not have public IP addresses. Which service is designed for this access pattern?

A. Azure Bastion deployed in the VNet
B. Azure NAT Gateway
C. Azure Front Door
D. Public Load Balancer with RDP and SSH open to all sources

**Correct: A.** Azure Bastion provides RDP/SSH connectivity over TLS through supported client experiences without public IPs on the target VMs. [R1]

**Why the others are wrong:** B NAT Gateway provides outbound connectivity, not inbound remote administration. [R2] C Front Door is an HTTP(S) application delivery service. [R3] D exposes management ports publicly and violates the stated requirement. [R1][R4]

**References:** [R1] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R2] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R3] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 13 - Mitigate volumetric DDoS attacks

A public-facing application on Azure requires enhanced network-layer DDoS mitigation, telemetry, and mitigation reports for public IP resources in its VNets. Which solution should be configured?

B. Azure DDoS Network Protection on the relevant virtual networks
C. Application Gateway WAF alone
D. A deny-all NSG rule
A. Azure DNS Private Resolver

**Correct: B.** DDoS Network Protection provides enhanced protection for supported public IP resources in protected VNets, including telemetry and mitigation capabilities. [R1]

**Why the others are wrong:** C WAF addresses application-layer HTTP(S) threats and does not replace network-layer DDoS protection. [R1][R2] D deny-all blocks legitimate traffic and is not DDoS mitigation. [R3] A Private Resolver handles DNS forwarding and does not mitigate volumetric attacks. [R4]

**References:** [R1] [Azure DDoS Protection overview](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R2] [WAF overview](https://learn.microsoft.com/en-us/azure/web-application-firewall/overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview).

## Domain 3: Secure compute, storage, and databases (20–25%)

### Question 14 - Reduce public exposure of VM management ports

Administrators need occasional RDP access to Azure VMs, but management ports must be closed by default and opened only for an approved, time-limited request. Which capability should you configure?

C. Just-in-time VM access in Microsoft Defender for Cloud
D. A permanent NSG allow rule from any internet address
A. Azure Bastion autoscaling as the control that opens VM ports
B. Azure Traffic Manager

**Correct: C.** Defender for Cloud JIT access limits exposure of selected management ports and opens access for a configured limited period in response to an authorized request, for supported VMs. [R1]

**Why the others are wrong:** D exposes management ports continuously and broadly. [R1][R2] A Bastion provides a secure connection path but does not itself implement the JIT port-opening workflow. [R1][R3] B Traffic Manager provides DNS routing and does not authorize VM administration. [R4]

**References:** [R1] [Just-in-time VM access](https://learn.microsoft.com/en-us/azure/defender-for-cloud/just-in-time-access-usage); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 15 - Restrict Kubernetes control-plane access

An AKS cluster's Kubernetes API should be accessible only from approved administrative networks. The cluster workloads must also use Kubernetes-native least-privilege permissions. Which two controls address these separate needs? **Select two.**

D. Configure AKS API server authorized IP ranges or an appropriate private-cluster design
E. Use Kubernetes role-based access control (RBAC) and Microsoft Entra integration for identities and workload authorization
A. Allow the API server from all public IP addresses and rely only on pod network policies
B. Assign subscription Owner to every cluster developer
C. Use Azure Storage lifecycle policies to filter API requests

**Correct: D, E.** API server network restrictions limit where the control plane is reachable. Kubernetes RBAC and Entra integration govern authenticated users' and groups' actions in the cluster. [R1]

**Why the others are wrong:** A pod network policies govern pod traffic and do not restrict access to the Kubernetes API server. [R1] B subscription Owner is far broader than cluster-scoped access and violates least privilege. [R1][R2] C storage lifecycle policies do not secure AKS. [R3]

**References:** [R1] [Security concepts for AKS](https://learn.microsoft.com/en-us/azure/aks/concepts-security); [R2] [Azure RBAC overview](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview); [R3] [Azure Storage lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview).

### Question 16 - Limit container image push privileges

Developers should push images to Azure Container Registry but must not delete repositories or manage the registry. Which role should be assigned at the registry scope?

A. `AcrPush` (or the corresponding repository-scoped writer role when the registry uses the ABAC repository-permissions mode)
B. Subscription Owner
C. `AcrDelete`
D. Azure Policy Contributor

**Correct: A.** `AcrPush` grants image push/pull operations without granting registry ownership. Where repository-level ABAC permissions are enabled, use the corresponding repository-scoped writer role and conditions. [R1]

**Why the others are wrong:** B Owner provides broad subscription management beyond image publishing. [R2] C `AcrDelete` is not the appropriate push-only role and grants destructive permissions. [R1] D Azure Policy Contributor manages policy assignments and definitions, not registry image push operations. [R3]

**References:** [R1] [Azure Container Registry roles and permissions](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-roles); [R2] [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 17 - Encrypt VM disks at rest

A compliance requirement states that all data on a VM's host storage must be encrypted at rest without requiring guest operating-system disk-encryption extensions or changes to the VM image. Which option most directly addresses the requirement?

B. Enable encryption at host for supported VM sizes and disks
C. Enable TLS on the web application only
D. Enable Azure DDoS Protection
A. Configure an NSG to deny inbound traffic

**Correct: B.** Encryption at host encrypts data stored on the host, including temporary disks and caches, in addition to managed-disk encryption for supported VM configurations. Verify VM size, disk, and region support. [R1]

**Why the others are wrong:** C TLS protects data in transit to the application, not VM host storage at rest. [R2] D DDoS Protection mitigates network attacks and does not encrypt disks. [R3] A NSGs filter network traffic and do not encrypt stored data. [R4]

**References:** [R1] [Encryption at host overview](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-overview); [R2] [TLS configuration for App Service](https://learn.microsoft.com/en-us/azure/app-service/configure-ssl-certificate); [R3] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 18 - Authorize blob access with Microsoft Entra ID

An application hosted in Azure must read blobs without storing a storage account key. It should have no management-plane rights and only read data in a specific container. Which design is best?

C. Assign the workload's managed identity a scoped Storage Blob Data Reader data-plane role
D. Assign subscription Contributor and store the account key in app settings
A. Assign management-plane Reader and assume it grants blob reads
B. Make the container public

**Correct: C.** Managed identity avoids stored credentials; a Storage Blob Data Reader role scoped to the required data boundary grants read access to blob contents. [R1][R2]

**Why the others are wrong:** D exposes a powerful account key and grants unnecessary management permissions. [R1][R2] A management-plane Reader does not itself grant data-plane blob access. [R1][R2] B public container access bypasses identity-based authorization and exposes data to the internet. [R1]

**References:** [R1] [Authorize access to blobs using Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/storage/blobs/authorize-access-azure-active-directory); [R2] [Azure RBAC built-in roles for storage](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/storage).

### Question 19 - Protect critical blobs against deletion and modification

A records archive must be retained for a fixed period. During that period, data must not be modified or deleted, including by privileged users. Which Storage capability should be configured?

D. Immutable Blob Storage with a time-based retention policy locked after validating its settings
A. Blob soft delete only
B. An NSG rule on the storage account
C. A SAS token with write permission

**Correct: D.** Immutable storage with a locked time-based retention policy provides WORM protection for supported blob data and prevents modification or deletion for the retention period. Test and validate the policy before locking because the operation can be irreversible. [R1]

**Why the others are wrong:** A soft delete can recover deleted data during its retention window but does not prevent modification or deletion. [R2] B NSGs are not attached to storage accounts and do not implement WORM retention. [R3] C a write-enabled SAS increases write access and does not enforce immutability. [R4]

**References:** [R1] [Immutable storage for Blob Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview); [R2] [Soft delete for blobs](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview); [R3] [Azure Storage network security](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security); [R4] [Azure Storage SAS overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview).

### Question 20 - Protect sensitive SQL columns from database administrators

An application stores highly sensitive values in Azure SQL Database. The database service and administrators must not see plaintext values; encryption and decryption should occur in the client application. Which feature is the best fit?

A. Always Encrypted, with keys managed outside the database engine and a compatible client driver
B. Dynamic data masking alone
C. Transparent Data Encryption (TDE) alone
D. A SQL firewall rule

**Correct: A.** Always Encrypted encrypts selected columns in the client driver so database engines and administrators without the keys do not see plaintext. [R1]

**Why the others are wrong:** B Dynamic data masking obscures query results for selected users but does not encrypt the stored data or protect plaintext from privileged database access. [R2] C TDE encrypts database files at rest but the running database engine handles plaintext. [R3] D SQL firewall rules control network connectivity and do not encrypt sensitive columns. [R4]

**References:** [R1] [Always Encrypted](https://learn.microsoft.com/en-us/azure/azure-sql/database/always-encrypted-landing); [R2] [Dynamic data masking](https://learn.microsoft.com/en-us/azure/azure-sql/database/dynamic-data-masking-overview); [R3] [Transparent Data Encryption](https://learn.microsoft.com/en-us/azure/azure-sql/database/transparent-data-encryption-tde-overview); [R4] [Azure SQL security overview](https://learn.microsoft.com/en-us/azure/azure-sql/database/security-overview).

### Question 21 - Audit database activity for investigations

A security team must retain evidence of database access and selected database events for later investigation. The audit destination must be configurable independently of query-time masking. Which feature should be enabled?

B. Azure SQL Auditing, writing audit events to an appropriately protected destination with a suitable retention policy
C. Dynamic data masking
D. An NSG flow log as the complete SQL statement audit trail
A. TDE without auditing

**Correct: B.** Azure SQL Auditing records configured database events to supported destinations such as Azure Storage, Log Analytics, or Event Hubs. Configure event categories, destination protections, and retention to meet policy. [R1]

**Why the others are wrong:** C Dynamic data masking alters what selected users see in query results; it does not record an audit trail. [R2] D NSG flow logs record network flow metadata, not SQL statements and database actions. [R3] A TDE protects database files at rest but does not log user activity. [R1][R4]

**References:** [R1] [Azure SQL auditing overview](https://learn.microsoft.com/en-us/azure/azure-sql/database/auditing-overview); [R2] [Dynamic data masking](https://learn.microsoft.com/en-us/azure/azure-sql/database/dynamic-data-masking-overview); [R3] [Virtual Network flow logs](https://learn.microsoft.com/en-us/azure/network-watcher/vnet-flow-logs-overview); [R4] [Transparent Data Encryption](https://learn.microsoft.com/en-us/azure/azure-sql/database/transparent-data-encryption-tde-overview).

### Question 22 - Authenticate Azure SQL users through Microsoft Entra

A company wants centralized identity lifecycle, MFA, and Conditional Access for administrators connecting to Azure SQL Database. Which database authentication method should it configure?

C. Microsoft Entra authentication for the logical server/database and the required contained users or groups
D. A shared SQL login embedded in every client application
A. A storage account key
B. An NSG rule that maps user identities to database roles

**Correct: C.** Microsoft Entra authentication integrates database access with centralized identities and supports Entra groups and identity controls, subject to supported client and server configuration. [R1]

**Why the others are wrong:** D a shared SQL login prevents individual identity governance and is a long-lived secret. [R1] A storage account keys authorize Storage, not SQL Database logins. [R2] B NSGs filter traffic and do not authenticate users or assign database roles. [R3]

**References:** [R1] [Azure SQL authentication and authorization](https://learn.microsoft.com/en-us/azure/azure-sql/database/authentication-aad-overview); [R2] [Azure Storage authorization](https://learn.microsoft.com/en-us/azure/storage/common/authorize-data-access); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 23 - Authenticate Azure Files SMB users with Active Directory

Users on domain-joined Windows clients need identity-based SMB access to Azure Files using their existing Active Directory credentials and share-level authorization. Which approach should be selected?

D. Configure identity-based authentication for Azure Files with a supported AD DS, Microsoft Entra Domain Services, or Microsoft Entra Kerberos configuration, then assign share-level permissions and file/directory ACLs
A. Enable anonymous access to the file share
B. Store the storage account key in each user's Windows Credential Manager as the only authorization layer
C. Use a Blob Storage user-delegation SAS for SMB access

**Correct: D.** Azure Files supports identity-based SMB authentication with supported directory services. Share-level RBAC and Windows ACLs provide complementary authorization. Validate client, domain, and feature prerequisites. [R1][R2]

**Why the others are wrong:** A anonymous access bypasses user identity and authorization. [R1] B account keys provide broad shared access and do not provide per-user share permissions. [R1][R2] C Blob SAS authorizes Blob REST access and is not the SMB authentication mechanism for Azure Files. [R3]

**References:** [R1] [Azure Files identity-based authentication overview](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-active-directory-overview); [R2] [Assign share-level permissions to an identity](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-identity-ad-ds-assign-permissions); [R3] [Azure Storage SAS overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview).

## Domain 4: Secure Azure using Microsoft Defender for Cloud and Microsoft Sentinel (30–35%)

### Question 24 - Enforce allowed resource locations

A subscription must prevent users from deploying resources outside approved Azure regions while still reporting existing noncompliant resources. Which governance design should you use?

A. Assign an Azure Policy initiative or definition with an appropriate deny effect for disallowed locations, and use compliance results to identify existing resources
B. Assign an NSG to the subscription
C. Use Azure Monitor alerts to block ARM deployments
D. Configure a resource lock on the management group

**Correct: A.** Azure Policy can deny new or updated resources that violate an allowed-locations policy and report compliance state for existing resources. [R1]

**Why the others are wrong:** B NSGs filter network traffic and do not restrict Azure resource deployment regions. [R2] C Monitor alerts notify about signals; they do not synchronously block ARM deployments. [R3] D locks protect management-group resources from some operations but do not enforce location properties. [R4]

**References:** [R1] [Azure Policy effect basics](https://learn.microsoft.com/en-us/azure/governance/policy/concepts/effect-basics); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure Monitor alerts overview](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview); [R4] [Azure resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).

### Question 25 - Restrict Key Vault network and data-plane access

An application in a VNet must retrieve secrets from Key Vault. The vault should be reachable over a private endpoint only, and the application must not manage vault settings or other secrets. Which design meets the requirement?

B. Create a Key Vault private endpoint, configure private DNS and disable public network access, then grant the workload identity only the required secret-read data-plane role
C. Allow all public networks and grant subscription Owner
D. Use an NSG on the Key Vault resource and grant Contributor
A. Store the secret in a public DNS record

**Correct: B.** Private Link provides private connectivity; private DNS resolves the vault name to the endpoint. Disabling public access and assigning a narrow Key Vault data-plane role enforce network and authorization boundaries. [R1][R2]

**Why the others are wrong:** C exposes the vault publicly and grants excessive control. [R1][R2] D NSGs are not directly attached to Key Vault; Contributor is broader than secret retrieval. [R1][R2] A DNS records are not a secrets store and would expose the value. [R3]

**References:** [R1] [Key Vault network security](https://learn.microsoft.com/en-us/azure/key-vault/general/network-security); [R2] [Key Vault RBAC guide](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-guide); [R3] [Azure Key Vault overview](https://learn.microsoft.com/en-us/azure/key-vault/general/overview).

### Question 26 - Rotate a Key Vault key used by a workload

A compliance policy requires an Azure Key Vault key to rotate automatically according to a rotation schedule. What should you configure?

C. A Key Vault key rotation policy with the required lifetime actions and a supported rotation mechanism for the key type
D. A key expiration date only; expiration automatically creates a replacement key in every configuration
A. A storage lifecycle management policy
B. An Azure Policy audit effect that changes the key value at deployment

**Correct: C.** Key Vault rotation policies define rotation timing/actions for supported keys; ensure the key type, rotation method, and dependent workload are configured to use new versions. [R1]

**Why the others are wrong:** D expiry alone does not guarantee a new key is generated or applications adopt it. [R1] A lifecycle management applies to Blob data, not Key Vault keys. [R2] B Policy audit reports configuration and does not rotate keys. [R3]

**References:** [R1] [Configure key rotation in Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/keys/how-to-configure-key-rotation); [R2] [Blob lifecycle management](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 27 - Protect backup operations from ransomware

A privileged operator must not be able to disable backup protection or delete recovery points without independent authorization. The organization also requires deletion protection for retained recovery data. Which two controls should you combine? **Select two.**

D. Use Resource Guard with multi-user authorization (MUA) for protected operations and keep authorization under a separate administrative boundary
E. Enable the relevant Azure Backup security features, including soft delete and immutability where supported and appropriate
A. Give the backup operator Owner on both the vault and Resource Guard
B. Disable soft delete to permit faster purging
C. Use an Azure Firewall rule as the approval workflow for backup changes

**Correct: D, E.** Resource Guard MUA adds independent authorization for protected backup operations. Azure Backup security features such as soft delete and immutable vault options help protect recovery data against destructive changes. [R1][R2]

**Why the others are wrong:** A defeats separation of duties by letting the same operator control the protected operation and its guard. [R1] B weakens recovery protection. [R2] C Azure Firewall controls network traffic and is not a backup authorization workflow. [R3]

**References:** [R1] [Multi-user authorization using Resource Guard](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept); [R2] [Azure Backup security features](https://learn.microsoft.com/en-us/azure/backup/backup-azure-security-feature); [R3] [Azure Firewall overview](https://learn.microsoft.com/en-us/azure/firewall/overview).

### Question 28 - Prioritize posture remediation with Secure Score

A security team needs to review its Azure security posture, identify high-impact recommendations, and track remediation against the Microsoft cloud security benchmark. Which Defender for Cloud capability should it use?

A. Secure Score and its recommendations, scoped to the relevant subscriptions and environments
B. Sentinel automation rules as the resource-configuration compliance benchmark
C. Azure Traffic Manager health checks
D. Key Vault soft delete

**Correct: A.** Defender for Cloud Secure Score summarizes posture against assessed security controls and provides recommendations that can be prioritized and remediated. Scores depend on subscription scope, enabled plans, and assessed resources. [R1][R2]

**Why the others are wrong:** B Sentinel automation rules orchestrate incident response and do not assess cloud resource configuration against the benchmark. [R3] C Traffic Manager monitors application endpoint health for DNS routing, not cloud security posture. [R4] D soft delete protects recoverability of deleted vault objects and is not a posture assessment tool. [R5]

**References:** [R1] [Secure Score in Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/secure-score-security-controls); [R2] [Defender for Cloud regulatory compliance dashboard](https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard); [R3] [Microsoft Sentinel automation](https://learn.microsoft.com/en-us/azure/sentinel/automation/automate-responses-with-playbooks); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [Key Vault recovery overview](https://learn.microsoft.com/en-us/azure/key-vault/general/key-vault-recovery).

### Question 29 - Extend posture and workload protection to AWS and GCP

A company has Azure, AWS, and Google Cloud workloads. It needs a unified view of security recommendations and wants workload protection plans for supported compute and data resources. Which approach is appropriate?

B. Connect the AWS accounts and GCP projects to Defender for Cloud, then configure the relevant CSPM and workload protection plans
C. Send cloud audit logs to Sentinel only and assume this provides Defender for Cloud posture assessment and workload protection
D. Create an Azure VNet peering connection to each cloud and do not onboard cloud accounts
A. Use Azure Policy to directly manage all AWS and GCP resources without connectors

**Correct: B.** Defender for Cloud supports multicloud connectors and can assess supported resources; workload protections require the relevant plan, configuration, and entitlements. [R1][R2][R3]

**Why the others are wrong:** C Sentinel can analyze connected logs but does not alone provide Defender for Cloud's CSPM or workload protection plans. [R1][R4] D network connectivity does not onboard cloud resource inventory or enable posture assessments. [R1] A Azure Policy governs Azure resources and is not a substitute for connecting external cloud accounts to Defender for Cloud. [R1][R5]

**References:** [R1] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R2] [Connect AWS to Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-aws); [R3] [Connect GCP to Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-gcp); [R4] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R5] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview).

### Question 30 - Discover internet-facing assets and DevOps risks

A security team needs to identify unknown internet-facing assets associated with its organization and prioritize external exposure. It also needs findings for code, secrets, and infrastructure-as-code risks in supported repositories. Which pairing best matches these needs?

C. Microsoft Defender External Attack Surface Management (EASM) for external asset discovery; Defender for Cloud DevOps security for supported repository posture findings
D. Azure Bastion for external asset discovery; Sentinel for source-code dependency scanning
A. Azure DDoS Protection for repository scanning; Azure Policy for internet-wide asset discovery
B. Traffic Manager for exposed asset inventory; Key Vault for code scanning

**Correct: C.** Defender EASM discovers and maps external, internet-facing assets. Defender for Cloud DevOps security integrates with supported DevOps environments to surface DevOps security recommendations. [R1][R2]

**Why the others are wrong:** D Bastion provides VM administration, not asset discovery; Sentinel is SIEM/SOAR, not a source repository scanning replacement. [R1][R3] A DDoS Protection mitigates network attacks and Azure Policy governs Azure configurations; neither performs both stated tasks. [R1][R4] B Traffic Manager routes DNS requests, while Key Vault stores secrets and keys rather than scanning source code. [R5][R6]

**References:** [R1] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R2] [Defender for Cloud DevOps security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction); [R3] [Microsoft Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R5] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R6] [Azure Key Vault overview](https://learn.microsoft.com/en-us/azure/key-vault/general/overview).

### Question 31 - Collect and detect security events in Sentinel

A SOC must ingest Azure activity and Windows security events into Microsoft Sentinel, then detect suspicious patterns using scheduled queries. Which two components are required? **Select two.**

D. Configure the appropriate Sentinel data connectors to ingest the required sources into the workspace
E. Enable analytics rules that query the ingested data and create alerts/incidents
A. Create a Key Vault access policy for each event source
B. Use Azure Policy as the event query and alert engine
C. Configure an NSG to convert Windows event logs into incidents

**Correct: D, E.** Sentinel data connectors ingest security data; analytics rules evaluate the ingested data and can generate alerts/incidents. Data collection and detection are separate configuration steps. [R1][R2]

**Why the others are wrong:** A Key Vault access policies control vault data-plane access and do not collect Sentinel events. [R3] B Azure Policy evaluates resource configuration, not security-event queries. [R4] C NSGs filter network traffic and do not parse Windows events or create Sentinel incidents. [R5]

**References:** [R1] [Connect data sources to Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources); [R2] [Create custom analytics rules](https://learn.microsoft.com/en-us/azure/sentinel/create-analytics-rules); [R3] [Azure Key Vault RBAC guide](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-guide); [R4] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R5] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 32 - Automate Sentinel incident response

When a Sentinel analytics rule creates a high-severity incident, the SOC wants to enrich the incident and notify responders automatically. The same response workflow should be reusable for supported incident actions. Which design is best?

A. Use a Sentinel automation rule to invoke an Azure Logic Apps playbook with the required permissions and connectors
B. Use an Azure Policy deny assignment to send the notification
C. Use a Conditional Access policy to run a workflow when an incident is created
D. Use a Key Vault firewall rule to enrich the incident

**Correct: A.** Sentinel automation rules can trigger playbooks; playbooks are Logic Apps workflows that perform configured response actions using their connectors and permissions. [R1]

**Why the others are wrong:** B Azure Policy governs resource configuration and is not a security-incident workflow engine. [R2] C Conditional Access controls user access, not incident-triggered response. [R3] D Key Vault firewall rules control network access and do not process Sentinel incidents. [R4]

**References:** [R1] [Automate responses with Microsoft Sentinel playbooks](https://learn.microsoft.com/en-us/azure/sentinel/automation/automate-responses-with-playbooks); [R2] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R3] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R4] [Key Vault network security](https://learn.microsoft.com/en-us/azure/key-vault/general/network-security).

### Question 33 - Collect network security telemetry with Azure Monitor

A team must collect selected network security events from Azure resources using Azure Monitor's managed collection configuration, then analyze them centrally. Which Azure Monitor component should be configured for collection and routing?

B. Data collection rules (DCRs), with supported data sources and destinations configured for the target monitoring pipeline
C. Azure Policy initiatives as event stream processors
D. Azure Traffic Manager profiles
A. Azure resource locks

**Correct: B.** DCRs define collection and transformation settings for supported Azure Monitor data sources and route data to configured destinations. Validate that the specific network data source supports the chosen DCR/agent path. [R1][R2]

**Why the others are wrong:** C Azure Policy evaluates resource properties and does not collect or route telemetry. [R3] D Traffic Manager selects application endpoints through DNS and is unrelated to event collection. [R4] A resource locks prevent certain management actions and do not gather logs. [R5]

**References:** [R1] [Data collection rules overview](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/data-collection-rule-overview); [R2] [Azure Monitor overview](https://learn.microsoft.com/en-us/azure/azure-monitor/overview); [R3] [Azure Policy overview](https://learn.microsoft.com/en-us/azure/governance/policy/overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [Azure resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).

## Further study

The [official AZ-500 exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-500/) and [final study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-500) document the AZ-500 exam, its published skills, and its retirement date. Supplementary materials include the [AZ-500 Microsoft Learn playlist](https://www.youtube.com/playlist?list=PLahhVEj9XNTfrVnZaub9jEgN9tmH1T6-r) and the repository's [AZ-500 study notes](AZ-500.md). Microsoft Learn is the authority for historical exam scope and current product behavior.