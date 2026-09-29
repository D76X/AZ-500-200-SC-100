# SC-100 Practice Tests

Original, unofficial scenario-based practice for **Exam SC-100: Microsoft Cybersecurity Architect**. These are not reproduced exam questions.

> **Exam alignment:** The Microsoft Learn exam page lists four domains: security best practices and priorities (20-25%); security operations, identity, and compliance (25-30%); infrastructure (25-30%); applications and data (20-25%). The page states the English exam is scheduled for an update on October 21, 2026. Check the live exam page and study guide for changes. Product capabilities and licensing can change; validate against current documentation and tenant entitlements.
>
> Choose the number of options requested. Each answer includes the rationale, why every distractor is wrong, and Microsoft Learn references. This study aid does not guarantee exam coverage.

## Domain 1: Design solutions that align with security best practices and priorities

### Question 1 - Architecture and benchmark

A hybrid cloud security team needs a Microsoft reference architecture that describes how security capabilities fit together, and a control benchmark to assess cloud resource configurations. Which pair best meets the requirements?

A. MCRA for the architecture; MCSB for control recommendations
B. MCSB for the architecture; MCRA as a configuration checklist
C. WAF as the control-by-control benchmark; Sentinel as the target architecture
D. Sentinel as the benchmark; Purview as the security reference architecture

**Correct: A.** MCRA describes how Microsoft security capabilities fit into an end-to-end architecture. MCSB provides cloud security control recommendations. [R1][R2]

**Why the others are wrong:** B reverses the roles of MCRA and MCSB. [R1][R2] C confuses workload design guidance (WAF) and security operations (Sentinel) with an architecture and benchmark. [R3][R4] D assigns SIEM/SOAR and data governance products the roles of security architecture and control benchmark. [R1][R4][R5]

**References:** [R1] [MCRA and MCSB learning module](https://learn.microsoft.com/en-us/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/); [R2] [MCSB overview](https://learn.microsoft.com/en-us/security/benchmark/azure/overview); [R3] [WAF security principles](https://learn.microsoft.com/en-us/azure/well-architected/security/principles); [R4] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R5] [Microsoft Purview](https://learn.microsoft.com/en-us/purview/).

### Question 2 - Zero Trust principles

A company is replacing its trusted-corporate-network model. Which three principles should anchor its Zero Trust architecture? **Select three.**

A. Verify explicitly using available identity, device, location, and risk signals
B. Use least privilege, including just-in-time access where appropriate
C. Assume breach and limit blast radius through segmentation and ongoing validation
D. Trust requests automatically when they originate on the corporate network
E. Treat successful authentication as permanent authorization

**Correct: A, B, C.** The three Zero Trust principles are verify explicitly, use least privilege, and assume breach. [R1][R2]

**Why the others are wrong:** D relies on implicit trust based on network location, which Zero Trust rejects. [R1] E treats authentication as lasting authorization rather than making access decisions using current context and least privilege. [R1][R2]

**References:** [R1] [Zero Trust overview](https://learn.microsoft.com/en-us/security/zero-trust/); [R2] [Introduction to Zero Trust](https://learn.microsoft.com/en-us/training/modules/introduction-zero-trust-best-practice-frameworks/).

### Question 3 - Framework scope

A security architect must coordinate a company-wide cloud security transformation and guide secure design of individual Azure workloads. Which approach matches the scope of each task?

A. CAF Secure for organizational cloud-security adoption; WAF security guidance for workload design
B. WAF for assigning enterprise security-team responsibilities; CAF only for workload encryption
C. Sentinel for adoption governance; MCSB as the organizational operating model
D. CAF Secure as a threat-detection service; WAF as a compliance assessment product

**Correct: A.** CAF Secure guides organizational security practices at cloud-adoption scale; WAF provides workload architecture principles, including security. [R1][R2]

**Why the others are wrong:** B reverses the frameworks' scope: WAF is workload design guidance and CAF is broader than encryption. [R1][R2] C misstates Sentinel (security analytics/response) and MCSB (cloud security control benchmark). [R3][R4] D mistakes frameworks for operational detection and compliance products. [R1][R2]

**References:** [R1] [CAF Secure methodology](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/secure/); [R2] [WAF security principles](https://learn.microsoft.com/en-us/azure/well-architected/security/principles); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [MCSB overview](https://learn.microsoft.com/en-us/security/benchmark/azure/overview).

### Question 4 - Ransomware resilience

A ransomware incident could compromise production administrators and connected backup credentials. Which two choices most directly strengthen recovery? **Select two.**

A. Make protected recovery points immutable for the required protection period
B. Use Resource Guard with multi-user authorization (MUA) and an independently controlled approver for protected backup operations
C. Keep the only backup in the production account and allow production admins to delete it
D. Treat a successful backup-job status as proof a restore will meet recovery objectives
E. Replace restore testing with a longer password policy

**Correct: A, B.** Immutability protects recovery points from destructive changes during the configured period; Resource Guard/MUA adds an independent authorization step for protected operations. Both support, but do not replace, tested recovery procedures. [R1][R2][R3]

**Why the others are wrong:** C leaves backups exposed to the same compromised boundary. [R1][R2] D a completed backup alone does not prove restore success or achievement of RTO/RPO; test restoration. [R1][R3] E password policy is not a substitute for protected recovery points and tested recovery. [R1][R2]

**References:** [R1] [Ransomware resiliency learning module](https://learn.microsoft.com/en-us/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/); [R2] [Azure Backup immutable vault](https://learn.microsoft.com/en-us/azure/backup/backup-azure-immutable-vault-concept); [R3] [Resource Guard multi-user authorization](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept).

### Question 5 - Prioritize multicloud posture risk

A team needs ongoing visibility into Azure, AWS, and Google Cloud security posture. It must prioritize cloud misconfigurations and attack paths, not merely aggregate alert logs. Which service is the best fit?

A. Defender for Cloud CSPM capabilities and recommendations
B. Sentinel as the sole cloud configuration benchmark and remediation engine
C. Purview DLP to discover infrastructure misconfigurations
D. Entra ID Protection as the multicloud workload vulnerability-management service

**Correct: A.** Defender for Cloud provides cloud security posture management and recommendations across supported cloud environments; it is the best fit for assessing and prioritizing cloud-resource risk. [R1][R2]

**Why the others are wrong:** B Sentinel is a SIEM/SOAR for security data, analytics, and response, not a substitute for CSPM recommendations. [R1][R3] C Purview DLP protects sensitive information rather than assessing infrastructure configuration. [R4] D Entra ID Protection manages identity risks, not multicloud workload posture. [R5]

**References:** [R1] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R2] [Defender for Cloud multicloud security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-multicloud-security-get-started); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Purview DLP](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp); [R5] [Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection).

## Domain 2: Design security operations, identity, and compliance capabilities

### Question 6 - Context-aware employee access

Employees use managed and unmanaged devices. Sensitive cloud apps require MFA and a compliant managed device. Which control enforces this at sign-in?

A. Entra Conditional Access using MFA and device-compliance conditions
B. A Sentinel analytics rule that blocks every interactive sign-in
C. Purview retention labels assigned to user accounts
D. An Azure NSG attached to each user's device

**Correct: A.** Conditional Access evaluates sign-in conditions and can require MFA and a compliant device for supported cloud apps. [R1][R2]

**Why the others are wrong:** B Sentinel detects and analyzes events; it is not the access-policy enforcement point. [R3] C retention labels govern data retention, not authentication. [R4] D NSGs filter Azure network traffic, not Entra user sign-ins and device compliance. [R5]

**References:** [R1] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R2] [Require compliant devices](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-compliance); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Purview retention](https://learn.microsoft.com/en-us/purview/retention); [R5] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 7 - Reduce standing privilege

Administrators must have no permanent standing Global Administrator role. Elevation must be time-bound and subject to approval and authentication requirements. Which solution fits?

A. Entra PIM with eligible role assignments and activation controls
B. Permanent Global Administrator assignment with a long password
C. A Sentinel workbook listing administrator sign-ins
D. An access review configured to grant permanent active roles

**Correct: A.** PIM supports eligible, time-limited role activation and configurable controls such as approval and MFA. [R1]

**Why the others are wrong:** B remains standing privilege; password length does not create just-in-time activation. [R1] C visualizes activity but does not govern role activation. [R2] D access reviews periodically recertify access; they do not replace PIM activation, and permanent active roles contradict the requirement. [R1][R3]

**References:** [R1] [Configure Entra PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure); [R2] [Sentinel workbooks](https://learn.microsoft.com/en-us/azure/sentinel/monitor-your-data); [R3] [Access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview).

### Question 8 - Distinguish SIEM/SOAR from XDR

Responders need (1) to correlate Azure, firewall, and third-party events with hunting and playbook automation and (2) to investigate a unified incident correlating endpoint, identity, email, and collaboration alerts. Which pairing fits?

A. Sentinel for (1); Defender XDR for (2)
B. Defender XDR for (1); Purview for (2)
C. Purview for (1); Sentinel for (2)
D. Entra ID Protection for both

**Correct: A.** Sentinel is SIEM/SOAR for data ingestion, analytics, hunting, and response automation; Defender XDR correlates signals across Microsoft security products for unified incident investigation. [R1][R2]

**Why the others are wrong:** B Defender XDR is not the general SIEM for the stated third-party sources; Purview is not XDR incident management. [R1][R2] C Purview is data governance/protection, not general SIEM; Sentinel does not provide the specified Defender XDR incident experience. [R1][R2][R3] D Entra ID Protection focuses on identity risk, not broad SIEM and XDR functions. [R1][R2][R4]

**References:** [R1] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R2] [Defender XDR overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender); [R3] [Microsoft Purview](https://learn.microsoft.com/en-us/purview/); [R4] [Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection).

### Question 9 - Assess cloud regulatory compliance

Auditors need to assess Azure and AWS resources against regulatory standards, review failed controls, and follow recommendations to remediation. Which capability should the architect use?

A. Defender for Cloud regulatory compliance dashboard
B. Purview eDiscovery as the infrastructure configuration assessor
C. Sentinel workbooks as the source of per-resource regulatory assessments
D. Entra access reviews as the cloud configuration benchmark

**Correct: A.** Defender for Cloud maps supported cloud assessments to regulatory standards and provides recommendations. Available standards and coverage depend on the environment and configuration. [R1][R2]

**Why the others are wrong:** B eDiscovery preserves, collects, and reviews content for investigations, not cloud infrastructure controls. [R3] C workbooks visualize and monitor data but are not a substitute for Defender for Cloud compliance assessments. [R1][R4] D access reviews govern user access to groups, apps, and roles, not resource configuration. [R5]

**References:** [R1] [Defender for Cloud regulatory compliance](https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard); [R2] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R3] [Purview eDiscovery](https://learn.microsoft.com/en-us/purview/ediscovery); [R4] [Sentinel workbooks](https://learn.microsoft.com/en-us/azure/sentinel/monitor-your-data); [R5] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview).

### Question 10 - Recertify guest access

External guests belong to Entra groups. Group owners must periodically attest whether each guest still needs access; unapproved access must be removed according to policy. Which capability fits?

A. Recurring Entra access reviews with group owners as reviewers and appropriate result handling
B. PIM to rotate every guest's password
C. Sentinel to delete guests after every sign-in
D. Purview retention policies to revoke group membership

**Correct: A.** Access reviews support recurring group membership review by selected reviewers, including group owners, and configured handling of review results. [R1]

**Why the others are wrong:** B PIM governs privileged/resource access activation, not guest recertification or password rotation. [R1][R2] C deleting every guest after sign-in is not an attestation workflow and ignores continued need. [R3] D Purview retention governs content lifecycle, not Entra memberships. [R4]

**References:** [R1] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview); [R2] [Entra PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 11 - Investigate potential insider data theft

A trained team must identify and investigate potentially risky employee activities that may indicate data theft or policy violations, using defined privacy and governance controls. Which capability is designed for this?

A. Purview Insider Risk Management
B. Entra ID Protection as a complete data-loss investigation case-management system
C. Azure DDoS Protection to classify employee downloads
D. Azure Private Link to create insider-risk alerts

**Correct: A.** Insider Risk Management helps identify, investigate, and act on potentially risky insider activities with configurable policies and case workflows. [R1]

**Why the others are wrong:** B Entra ID Protection manages identity risks, not insider-risk cases about user data activities. [R2] C DDoS Protection mitigates denial-of-service attacks, not employee misuse. [R3] D Private Link provides private connectivity, not behavior analysis. [R4]

**References:** [R1] [Insider Risk Management overview](https://learn.microsoft.com/en-us/purview/insider-risk-management-solution-overview); [R2] [Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection); [R3] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R4] [Azure Private Link](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview).

## Domain 3: Design security solutions for infrastructure

### Question 12 - Extend security management to hybrid servers

A company has Azure VMs and Windows and Linux servers in datacenters. It wants to bring supported non-Azure servers into Azure management and apply Defender for Cloud protections. Which design is appropriate?

A. Connect non-Azure servers to Azure Arc-enabled servers, then configure the appropriate Defender for Cloud plan and coverage
B. Install Sentinel on each server and treat it as the Azure Arc control plane
C. Add datacenter servers to an Azure NSG without connecting them to Azure
D. Use Purview retention labels to onboard operating systems

**Correct: A.** Azure Arc-enabled servers extends Azure management to supported machines outside Azure. Defender for Cloud can provide supported posture and workload protections when appropriately configured and licensed. [R1][R2]

**Why the others are wrong:** B Sentinel is security analytics, not the Arc control plane. [R1][R3] C NSGs filter Azure virtual network traffic; they do not onboard datacenter hosts. [R4] D Purview labels apply to content, not server management. [R5]

**References:** [R1] [Azure Arc-enabled servers](https://learn.microsoft.com/en-us/azure/azure-arc/servers/overview); [R2] [Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R5] [Purview retention](https://learn.microsoft.com/en-us/purview/retention).

### Question 13 - Centralized and subnet network filtering

A landing zone has several spoke VNets. The team needs centrally managed filtering at the hub and subnet- or NIC-level allow/deny rules near workloads. Which two controls fit? **Select two.**

A. Azure Firewall for centralized stateful filtering
B. NSGs for subnet- or NIC-level traffic filtering
C. Sentinel analytics rules for inline packet filtering
D. Purview DLP for subnet port filtering
E. Key Vault firewall rules for spoke routing

**Correct: A, B.** Azure Firewall provides centralized network policy; NSGs filter traffic associated with subnets or NICs. Their scopes are complementary. [R1][R2]

**Why the others are wrong:** C Sentinel analyzes security data; it is not an inline firewall. [R3] D Purview DLP protects sensitive information, not ports. [R4] E Key Vault network rules govern vault access, not general spoke routing. [R1][R5]

**References:** [R1] [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Purview DLP](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp); [R5] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault).

### Question 14 - Protect a public web application

A public regional web app needs protection against volumetric network-layer attacks and common web exploits such as SQL injection. Which two controls address these different threats? **Select two.**

A. Azure DDoS Network Protection for supported public IP resources
B. WAF on a supported application delivery service, with an appropriate managed rule set
C. An NSG as the only SQL injection inspection control
D. Purview retention to absorb volumetric traffic
E. Key Vault soft delete as HTTP threat detection

**Correct: A, B.** DDoS Protection helps mitigate network-layer DDoS attacks; WAF inspects HTTP(S) traffic for common web exploits. They are complementary and depend on supported resources and correct configuration. [R1][R2]

**Why the others are wrong:** C NSGs filter network traffic but do not inspect HTTP for SQL injection. [R2][R3] D retention has no network mitigation role. [R4] E Key Vault recovery protects deleted vault objects, not HTTP traffic. [R5]

**References:** [R1] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R2] [Application Gateway WAF](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Purview retention](https://learn.microsoft.com/en-us/purview/retention); [R5] [Key Vault recovery](https://learn.microsoft.com/en-us/azure/key-vault/general/key-vault-recovery).

### Question 15 - Protect recovery points

A privileged admin must not be able to delete critical backup recovery points alone. Recovery points must also resist modification or deletion during a defined protection period. Which two controls meet these requirements? **Select two.**

A. Configure vault immutability for the required protection policy
B. Configure Resource Guard MUA with an independently controlled approver
C. Give the same admin unrestricted ownership of the vault and Resource Guard
D. Disable soft delete so deletions finish immediately
E. Use Azure Firewall as the backup approval workflow

**Correct: A, B.** Vault immutability protects recovery points during the configured period; Resource Guard MUA adds independent authorization for protected operations and separation of duties. [R1][R2]

**Why the others are wrong:** C gives one admin control of both sides of the separation boundary. [R2] D weakens deletion safeguards. [R1] E Azure Firewall controls network traffic; it is not a backup authorization service. [R3]

**References:** [R1] [Azure Backup immutable vault](https://learn.microsoft.com/en-us/azure/backup/backup-azure-immutable-vault-concept); [R2] [Resource Guard MUA](https://learn.microsoft.com/en-us/azure/backup/multi-user-authorization-concept); [R3] [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview).

### Question 16 - Just-in-time VM access

Admins need occasional VM maintenance access. Management ports must not be permanently exposed to the internet; approved access should be limited in duration and source. Which solution fits?

A. Defender for Cloud just-in-time VM access for supported VMs with restrictive network rules
B. Permanently open RDP and SSH to every source in an NSG
C. Purview DLP to open RDP after detecting a sensitive file
D. Give every VM a public IP and rely on password complexity

**Correct: A.** Defender for Cloud JIT access reduces exposure by opening management ports for limited periods in response to authorized requests, subject to supported resources and configuration. [R1]

**Why the others are wrong:** B creates broad standing exposure. [R1][R2] C DLP protects information and does not authorize VM network access. [R3] D does not remove internet exposure or provide JIT control. [R1][R2]

**References:** [R1] [JIT VM access in Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/just-in-time-access-usage); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Purview DLP](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp).

### Question 17 - Private VM administration

Admins need RDP/SSH to Azure VMs over TLS through a managed browser or supported native-client experience, without public IPs on the VMs. Which service is designed for this?

A. Azure Bastion
B. Azure DDoS Protection
C. Sentinel as an RDP proxy
D. Private Link as a general browser RDP gateway for arbitrary VM NICs

**Correct: A.** Azure Bastion enables RDP/SSH connectivity over TLS through supported client experiences without public IP addresses on target VMs. [R1]

**Why the others are wrong:** B mitigates denial-of-service attacks, not remote access. [R2] C Sentinel provides security analytics, not RDP proxying. [R3] D Private Link connects to supported services; it is not a general VM RDP gateway. [R4]

**References:** [R1] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R2] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R3] [Sentinel overview](https://learn.microsoft.com/en-us/azure/sentinel/overview); [R4] [Azure Private Link](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview).

## Domain 4: Design security solutions for applications and data

### Question 18 - Remove application credentials

An Azure-hosted app reads secrets from Key Vault. The team must remove stored credentials from code and deployment settings, granting only required vault permissions. Which design is best?

A. Assign the app a managed identity and grant it minimum required Key Vault data-plane permissions
B. Store a service principal secret in source control and rotate quarterly
C. Embed a storage key in the image and grant subscription Owner
D. Put the secret in an NSG rule and authenticate with the VM public IP

**Correct: A.** Managed identities let supported Azure resources obtain tokens without application-managed credentials; narrow permissions follow least privilege. [R1][R2]

**Why the others are wrong:** B leaves a reusable secret exposed. [R1] C embeds a credential and grants excessive access. [R1][R2] D NSGs filter traffic; they do not store secrets or authenticate to Key Vault. [R2][R3]

**References:** [R1] [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview); [R2] [Secure Azure Key Vault](https://learn.microsoft.com/en-us/azure/key-vault/general/secure-key-vault); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 19 - Remove public access to a PaaS database

An Azure SQL Database must be reached at a private IP in the workload VNet, and its public endpoint must be unavailable. Which design fits?

A. Create a Private Endpoint, configure private DNS, and disable public network access
B. Use a Service Endpoint and leave public access enabled for all networks
C. Put an NSG on the app subnet and assume it disables SQL's public endpoint
D. Store the connection string in Purview and allow public access from the app

**Correct: A.** A Private Endpoint maps a supported service to a private IP in a VNet. Private DNS supports correct name resolution; disabling public access closes the public path when supported and correctly configured. [R1][R2]

**Why the others are wrong:** B does not provide the requested private endpoint IP and leaves public access enabled. [R1] C an app-subnet NSG does not itself disable the SQL service's public endpoint. [R1][R3] D Purview does not store or authorize SQL connection strings and public access violates the requirement. [R4]

**References:** [R1] [Private Link overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview); [R2] [Azure SQL connectivity architecture](https://learn.microsoft.com/en-us/azure/azure-sql/database/connectivity-architecture); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Microsoft Purview](https://learn.microsoft.com/en-us/purview/).

### Question 20 - Authenticate and limit API requests

An API published through Azure API Management must reject requests without a valid Entra-issued access token and limit excessive calls by a client. What should be configured at the API gateway?

A. API Management policies to validate the JWT and apply rate-limit or quota policies
B. DDoS Protection as the only authentication and per-client rate-limiting control
C. An NSG to validate JWT claims and identify API clients
D. A Purview sensitivity label as the authentication policy

**Correct: A.** API Management policies can validate JWTs and apply request rate limits or quotas. Configure issuer, audience, and claims checks for the API's trust requirements. [R1][R2]

**Why the others are wrong:** B mitigates network-layer DDoS; it does not validate tokens or implement API authorization policies. [R3] C NSGs filter network traffic, not JWT claims. [R4] D sensitivity labels classify/protect content, not API calls. [R5]

**References:** [R1] [API Management authentication policies](https://learn.microsoft.com/en-us/azure/api-management/api-management-authentication-policies); [R2] [API Management rate limit policy](https://learn.microsoft.com/en-us/azure/api-management/rate-limit-by-key-policy); [R3] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R5] [Purview sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels).

### Question 21 - Classify data and prevent exfiltration

A company must automatically identify documents with sensitive personal information, apply a persistent classification/protection label, and block or warn when matching content is shared externally. Which two capabilities should be combined? **Select two.**

A. Purview sensitivity labels with appropriate auto-labeling and protection settings
B. Purview DLP policies scoped to relevant locations and sharing channels
C. DDoS Protection and Azure Firewall as the content-classification engine
D. Entra access reviews as document inspection
E. Azure Backup retention as outbound-sharing enforcement

**Correct: A, B.** Sensitivity labels classify content and can apply protection. DLP detects sensitive information in supported locations and can warn, restrict, or block sharing actions according to policy. [R1][R2]

**Why the others are wrong:** C network controls do not classify document content or provide Purview DLP actions. [R1][R2][R3] D access reviews recertify user access; they do not inspect documents. [R4] E backup protects data for recovery, not real-time classification or sharing enforcement. [R5]

**References:** [R1] [Sensitivity labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels); [R2] [Purview DLP](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp); [R3] [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview); [R4] [Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview); [R5] [Azure Backup overview](https://learn.microsoft.com/en-us/azure/backup/backup-overview).

### Question 22 - Restrict downloads from unmanaged devices

Employees use a sanctioned SaaS app. On unmanaged devices, browser viewing should remain available but file downloads must be blocked; compliant devices retain normal access. Which design best fits?

A. Use Conditional Access with Defender for Cloud Apps session control and a session policy restricting downloads on unmanaged devices
B. Use an Entra access review to inspect each live browser session
C. Use Azure Firewall alone as an identity-integrated SaaS session control
D. Apply Azure Backup to the unmanaged device

**Correct: A.** Conditional Access can route supported sessions through Defender for Cloud Apps for real-time session monitoring and controls such as download restrictions. The app, configuration, and licensing must support the scenario. [R1][R2]

**Why the others are wrong:** B access reviews are periodic governance, not live session controls. [R3] C Azure Firewall filters network traffic but alone does not provide the identity-integrated SaaS session controls. [R1][R4] D Azure Backup protects supported data sources for recovery, not SaaS browser sessions. [R5]

**References:** [R1] [Conditional Access app control in Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad); [R2] [Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview); [R3] [Access reviews](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview); [R4] [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/overview); [R5] [Azure Backup overview](https://learn.microsoft.com/en-us/azure/backup/backup-overview).

### Question 23 - Secure a cloud deployment pipeline

A GitHub Actions workflow deploys to Azure. The team wants to avoid long-lived Azure client secrets and detect exposed secrets, vulnerable dependencies, and infrastructure-as-code misconfigurations before deployment. Which two choices best meet these goals? **Select two.**

A. Configure workload identity federation so the workflow obtains tokens without storing a long-lived client secret
B. Integrate repository security scanning and Defender for Cloud DevOps security recommendations into development and remediation
C. Store a permanent subscription Owner secret in the repository and rotate quarterly
D. Replace code and dependency scanning with DDoS Protection
E. Use Purview retention labels as GitHub Actions authentication

**Correct: A, B.** Workload identity federation lets a supported external workload exchange a trusted identity token for an access token without maintaining a client secret. Defender for Cloud DevOps security provides recommendations across supported DevOps environments; combine with suitable repository-native scanners to catch issues early. [R1][R2]

**Why the others are wrong:** C leaves a long-lived, excessive-privilege credential exposed; rotation does not remove that risk. [R1] D DDoS Protection addresses network attacks, not code, dependencies, secrets, or IaC. [R2][R3] E Purview retention governs content lifecycle, not workload authentication. [R1][R4]

**References:** [R1] [Workload identity federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation); [R2] [Defender for Cloud DevOps security](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction); [R3] [Azure DDoS Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R4] [Purview retention](https://learn.microsoft.com/en-us/purview/retention).

## Further study

Use the [SC-100 exam page](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-100/) for the current skills measured and official study guide. The four [Microsoft Learn paths](https://learn.microsoft.com/en-us/training/paths/sc-100-design-solutions-best-practices-priorities/), [operations, identity, and compliance path](https://learn.microsoft.com/en-us/training/paths/sc-100-design-operations-identity-compliance-capabilities/), [infrastructure path](https://learn.microsoft.com/en-us/training/paths/sc-100-design-security-solutions-infrastructure/), and [applications and data path](https://learn.microsoft.com/en-us/training/paths/sc-100-design-security-solutions-applications-data/) align to these domains.

The [SC-100 Microsoft Learn video playlist](https://www.youtube.com/playlist?list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_) and episode links in the repository specification are supplementary learning materials. Microsoft Learn product and exam documentation is the authority for product behavior and exam scope.