[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q14

Fabrikam Financial recently completed the acquisition of a smaller firm, Northwind Trading, and inherited 
an unknown number of internet-facing web applications and subdomains that Northwind's IT team provisioned 
outside of any centrally managed Azure subscription or Microsoft Entra tenant. Fabrikam's own Azure subscription, 
Sub-Fabrikam, has `full Defender for Cloud coverage`, including `Defender CSPM` with `attack path analysis enabled`, 
and `Microsoft Defender Vulnerability Management` is configured on all known virtual machines.

The security team needs to identify any Northwind-owned domains, subdomains, and externally reachable services that 
were never registered in Fabrikam's Azure environment, so each discovered asset can be evaluated for exposure and 
brought under centralized management where appropriate. 

The solution must:

- Surface internet-facing assets that exist outside of Sub-Fabrikam and outside Microsoft Entra ID, 
based only on their public-facing footprint (domains, DNS records, certificates, IP ranges).

- Require no prior registration of the asset in Azure or Entra ID before it can be discovered.

Which capability should the security team use?

Select one answer option below.

### OPTION 01
Microsoft Entra ID Identity Protection, configured with a custom risk detection for the Northwind domains

### OPTION 02
Defender CSPM's attack path analysis, expanded to include the Northwind acquisition's resources

### OPTION 03
Microsoft Defender Vulnerability Management, extended to scan Northwind's IP address range

### OPTION 04
Microsoft Defender External Attack Surface Management (EASM), configured to scan Northwind's known seed domains

---

## Answer

**Correct answer: OPTION 04 — Microsoft Defender External Attack Surface Management (EASM), configured with Northwind's known seed domains.**

Defender EASM is designed to discover and continuously map an organization's internet-exposed attack surface. Starting from known seed assets such as domains, it recursively follows public infrastructure relationships—including DNS, certificates, hosts, and IP address blocks—to find previously unknown and unmonitored assets. This external discovery does not require the discovered assets to have been registered in Fabrikam's Azure subscription or Microsoft Entra tenant. The team can review discovered assets in EASM's inventory and determine which belong under centralized management. [1][2]

### Why the other options are incorrect

- **OPTION 01 — Microsoft Entra ID Identity Protection:** Identity Protection detects risk associated with user and sign-in activity in Microsoft Entra ID. It does not enumerate public domains, subdomains, DNS records, certificates, or services outside the tenant. A custom identity-risk detection therefore does not meet the external asset-discovery requirement. [3]
> What does Microsoft Entra ID Identity Protection, configured with a custom risk detection for specific domains accomplish?

- **OPTION 02 — Defender CSPM attack path analysis:** Attack path analysis uses Defender for Cloud's security graph to find exploitable paths through cloud assets and their relationships. Its external entry points are used to assess routes into an environment; the capability is not a general-purpose discovery engine for unknown internet assets outside Fabrikam's cloud environment. [4]

- **OPTION 03 — Microsoft Defender Vulnerability Management:** Vulnerability Management assesses vulnerabilities and security configuration on endpoints and supported network devices. Defender for Endpoint's device discovery uses onboarded endpoints to observe or probe devices in monitored corporate networks; this is not internet-wide discovery of an acquired company's domains, DNS infrastructure, certificates, and externally reachable services. [5][6]

### References

1. [Microsoft Defender EASM overview](https://learn.microsoft.com/en-us/azure/external-attack-surface-management/overview) — describes continuous external attack-surface discovery and the asset types inventoried.
2. [What is discovery in Defender EASM?](https://learn.microsoft.com/en-us/azure/external-attack-surface-management/what-is-discovery) — explains seed-based recursive discovery and the use of DNS, SSL certificates, and IP/ASN relationships.
3. [What are risk detections? — Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks) — documents sign-in and user risk detections.
4. [Security explorer and attack paths in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path) — explains the cloud security graph and attack path analysis across cloud environments.
5. [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) — describes endpoint and network-device vulnerability and configuration assessment.
6. [Microsoft Defender for Endpoint device discovery overview](https://learn.microsoft.com/en-us/defender-endpoint/device-discovery) — explains discovery of unmanaged devices on monitored corporate networks using onboarded endpoints.

---

# What is Microsoft Defender EASM and how does it work?

**Microsoft Defender External Attack Surface Management (EASM)** is 
a cloud security solution that continuously discovers, maps, and monitors 
an organization’s internet-facing infrastructure from an outside-in perspective. 

Rather than relying on internal asset lists or agents installed on servers, 
it scans and correlates public internet data to show what attackers can see 
and reach before they ever get inside your network.

---

### How It Works

Defender EASM operates through a continuous discovery-to-remediation loop 
built on Microsoft's global internet scanning and threat intelligence infrastructure:

1. **Seed-Based Recursive Discovery**
You start by providing a small set of known, trusted **discovery seeds**—such as primary domains, public IP address blocks, autonomous system numbers (ASNs), email contacts, or Whois organization records. `Defender EASM looks for strong public relationships` around those seeds and **recursively** `follows links, DNS records, certificates, and infrastructure connections` 
to `uncover forgotten subdomains, shadow IT, cloud resources, and third-party dependencies`.

2. **Continuous Scanning & Probing**
Once infrastructure links are inferred, Defender EASM probes exposed endpoints from outside the perimeter to gather telemetry on active services, web pages, SSL/TLS certificates, open ports/technologies, and known vulnerabilities. Because external infrastructure changes constantly, discovery groups can run on recurring schedules (such as weekly).

3. **Inventory Classification & Triage**
Discovered assets are indexed in a centralized inventory where teams review ownership, 
confirm whether an asset legitimately belongs to the organization, and move confirmed 
items into **Approved** status (with options to exclude unrelated or subsidiary assets). 
Assets are tracked across states (such as active/recent vs. historic) and can be tagged 
with custom labels for ownership or workflow tracking.

4. **Risk Insights & Workflow Integration**
Dashboards group findings into actionable risk themes—such as vulnerabilities, 
expiring or misconfigured certificates, compliance gaps, and security hygiene issues. 
Teams can filter the inventory, export asset data or attack surface insights 
(for example, to Log Analytics), and connect findings into SIEM, SOAR, or ticketing workflows.

---

### Key Asset Types & Role in Security Posture

* **Discovered asset types:** Domains, hosts/subdomains, IP addresses and IP blocks, 
autonomous system numbers (ASNs), SSL certificates, web pages, email contacts, and Whois organizations.

* **Outside-in vs. inside-out visibility:** Solutions like Defender for Cloud or 
endpoint/identity tools focus heavily on internal workloads, configurations, and 
identities once inside or managed. Defender EASM complements them by answering a 
foundational question: 

`what is exposed on the public internet right now, including assets spin-up or third-party links that internal teams did not track?`

---

### Operational & Governance Notes

* **Deployment & Access:** Deployed as an Azure resource within a tenant, 
with role-based access (`Owner`, `Contributor`, `Reader`) and direct authentication 
to the resource's tenant (it does not support cross-tenant access via Azure Lighthouse).

* **Data Residency & Retention:** Customer-specific metadata (such as applied labels) 
is stored in the selected Azure region alongside Microsoft's global internet dataset, 
with defined retention and deletion windows when resources or subscriptions are removed.

---

# What is Microsoft Defender CSPM?

`Microsoft Defender CSPM (Cloud Security Posture Management)` is a core feature of Microsoft Defender for Cloud 
that continuously assesses, visualizes, and helps improve the security of your cloud infrastructure. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management)

It is not an antivirus tool; instead, it acts as a proactive command center to find 

- misconfigurations, 
- track compliance, and 
- prioritize critical risks across multi-cloud and hybrid environments (including Azure, AWS, GCP, and on-premises resources via Azure Arc). 

[1] (https://www.microsoft.com/en-gb/security/business/cloud-security/microsoft-defender-cloud-security-posture-management), 
[2] (https://www.youtube.com/watch?v=HyLLI4dM7Pg), [3] (https://www.youtube.com/watch?v=SZx4ztnt8RE&t=696), 
[4] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management)

## Core Plans: Foundational vs. Defender CSPM

Microsoft splits its posture management into two tiers: [1] (https://cloudgate.ae/blog/defender-for-cloud-cspm-baseline)

1. Foundational CSPM (Free): 
Enabled by default at no cost. It provides basic asset inventory, continuous security assessments mapped to 
the `Microsoft Cloud Security Benchmark (MCSB)`, standard security recommendations, and an aggregate Secure Score. 

[1] (https://intouchajay.medium.com/microsoft-defender-cloud-security-posture-management-cspm-a-pillar-for-multi-cloud-security-f0f7809247), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management), 
[3] (https://cloudgate.ae/blog/defender-for-cloud-cspm-baseline)

2. Defender CSPM (Paid): 
A paid, resource-billed plan that `unlocks advanced cloud-native application protection platform (CNAPP) capabilities`, 
deep contextual visibility, and intelligent risk-prioritization tools. 

[1] (https://www.azadvertizer.net/azpolicyadvertizer/689f7782-ef2c-4270-a6d0-7664869076bd.html), 
[2] (https://cloudgate.ae/blog/defender-for-cloud-cspm-baseline), 
[3] (https://www.youtube.com/watch?v=SZx4ztnt8RE&t=696), 
[4] (https://www.microsoft.com/en-gb/security/business/cloud-security/microsoft-defender-cloud-security-posture-management)

## Key Capabilities of Defender CSPM (Cloud Security Posture Management)

- Attack Path Analysis: 
Maps out potential paths an attacker could take by connecting misconfigurations, network exposure, and identity flaws, 
helping you fix the root entry points before a breach occurs. 

[1] (https://www.youtube.com/watch?v=twFUk_rmueg&t=11), 
[2] (https://www.youtube.com/watch?v=nE6tFjP7Juc&t=9)

- Cloud Security Explorer: 
A graph-based query tool that lets security teams proactively search and hunt for specific risks, 
exposed assets, or misconfigured resources across the cloud and DevOps pipelines. 

[1] (https://www.youtube.com/watch?v=nE6tFjP7Juc&t=9)

- Agentless Vulnerability & Secrets Scanning: 
Scans virtual machines, serverless workloads, and containers for software vulnerabilities 
and hardcoded secrets without needing an agent installed on every machine. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-cspm-plan), 
[2] (https://www.microsoft.com/en-gb/security/business/cloud-security/microsoft-defender-cloud-security-posture-management)

- Cloud Infrastructure Entitlement Management (CIEM): 
Analyzes and visualizes identity permissions and excess access rights to enforce least-privilege security. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-cspm-plan)

- Multicloud & Regulatory Compliance: 
Assesses your environment against hundreds of built-in industry standards and benchmarks—such as 
`CIS, ISO, NIST, and PCI-DSS`. 

[1] (https://www.microsoft.com/en-gb/security/business/cloud-security/microsoft-defender-cloud-security-posture-management)

- AI & API Security Posture: 
Extends posture monitoring to cover modern cloud workloads, AI models/agents, and API endpoints. 

[1] (https://www.youtube.com/watch?v=SZx4ztnt8RE&t=696), 
[2] (https://www.microsoft.com/en-gb/security/business/cloud-security/microsoft-defender-cloud-security-posture-management)

You can learn more about enabling and configuring the service via the Microsoft Defender CSPM Guide. 
[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-cspm-plan)


---

# What is Microsoft Defender Vulnerability Management

Microsoft Defender Vulnerability Management is a risk-based security solution that continuously 
discovers, assesses, prioritizes, and remediates software vulnerabilities and misconfigurations across 
endpoints, cloud workloads, and network devices. 

It operates across platforms including Windows, macOS, Linux, Android, and iOS. 

[1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), 
[2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management)

# Key Capabilities

- Continuous discovery and visibility: 
Tracks software inventories, vulnerable open-source or third-party components, browser extensions, digital certificates, 
and network shares in near real time. 

[1] (https://www.youtube.com/watch?v=QIwrpjpqrBc), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial), 
[3] (https://jeffreyappel.nl/microsoft-defender-for-endpoint-series-defender-vulnerability-management-part5/)

- Risk-based prioritization: 
Combines Microsoft threat intelligence, breach likelihood predictions, and business context to rank which flaws pose the greatest real-world risk. 

[1] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)

- Built-in remediation and tracking: 
Offers remediation workflows, security baseline assessments, application blocking, and real-time progress metrics 
such as exposure scores and `Microsoft Secure Score for Devices`. 

[1] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)

- Flexible monitoring: 
Uses built-in agent capabilities, authenticated scanning, and agentless methods to detect issues even when devices 
are off the corporate network or in cloud workloads. 

[1] (https://www.microsoft.com/en-us/security/business/threat-protection/microsoft-defender-vulnerability-management), 
[2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), 
[3] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)

## Common Usage Examples

- Prioritizing critical patches: 
Ranking hundreds of known `CVEs (Common Vulnerabilities and Exposures)` so IT teams fix flaws 
actively exploited in the wild on high-value servers first. 

[1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), 
[2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), 
[3] (https://jeffreyappel.nl/microsoft-defender-for-endpoint-series-defender-vulnerability-management-part5/)

- Auditing third-party components: 
Identifying risky libraries—such as older versions of OpenSSL or Apache Log4j—and 
unsafe device configurations that basic OS updates miss. 

[1] (https://www.youtube.com/watch?v=QIwrpjpqrBc), 
[2] (https://www.youtube.com/watch?v=CywLfSYz-iM)

- Mitigating exposed software: 
Blocking vulnerable applications or tracking remediation tasks in the Microsoft Defender portal 
(under Exposure management) until patches are deployed. 

[1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), 
[3] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)

## Related Terms and Context

- Threat and Vulnerability Management (TVM): 
An earlier name and foundational capability set associated with Microsoft Defender for Endpoint vulnerability assessment.

- Exposure Management: 
The broader Microsoft Defender portal area where vulnerability data and security exposure insights are consolidated. 

[1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)

- Extended Detection and Response (XDR) & Cloud Security Posture Management (CSPM): 

Adjacent security categories that pair with vulnerability management to connect weakness discovery 
with threat detection and cloud configuration hardening. 

[1] (https://www.microsoft.com/en-gb/security/business/security-101/what-is-vulnerability-management), 
[2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)

For plan details and feature availability, see Microsoft Defender Vulnerability Management plans. 
[1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)

---

# [What does Microsoft Entra ID Identity Protection, configured with a custom risk detection for specific domains accomplish?](https://share.gemini.google/Xaoi3MYfeWwf)

### OPTION 01
Microsoft Entra ID Identity Protection, configured with a custom risk detection for the Northwind domains

Microsoft Entra ID Identity Protection does **not** have a built-in feature to create a `custom risk detection for specific domains`. 

Its risk detections are fixed, rather than user-defined, domain-scoped rules.

The main risk detections are: 

1. machine-learning and 
2. heuristic signals managed by Microsoft (such as leaked credentials, atypical travel, anonymous IP addresses, and password spray)

Depending on the goal you are trying to achieve, the actual 
Microsoft Entra capability typically maps to one of the following:

### 1. Enforcing Risk Policies on Specific User Domains (Conditional Access)

While you cannot create custom domain-based risk *detections*, 
you can scope **risk-based Conditional Access policies** to users 
belonging to specific verified domains:

* **How it works:** Create a dynamic security group filtering on `userPrincipalName` (e.g., `user.userPrincipalName -endsWith "@subsidiary.com"`), then target that group in a Conditional Access policy with **Sign-in risk** or **User risk** conditions.

* **What it accomplishes:** Applies tailored remediation—such as requiring multifactor authentication (MFA), forcing a secure password reset, or blocking access—strictly to users on those domains when Microsoft detects an elevated risk level.

### 2. Custom Domain-Based Detections via Microsoft Sentinel / Defender XDR

If you want to generate custom alerts or risk signals based on specific domains 
(e.g., sign-ins from unapproved federated domains, B2B guest domains, or suspicious lookalike domains):

* **How it works:** Stream Entra ID sign-in logs and Identity Protection events 
to **Microsoft Sentinel** or **Microsoft Defender XDR**, and write a custom KQL analytics/detection rule filtering on `UserPrincipalName`, `HomeTenantId`, or `CrossTenantAccessType`.

* **What it accomplishes:** Alerts your `SOC team` to domain-specific anomalies 
and can trigger automated playbooks (Logic Apps) to call the Microsoft Graph `confirmCompromised` API, which injects a high user-risk state back into Entra ID Protection.

### 3. Restricting or Allowing External Domains (Cross-Tenant Access & External Collaboration)

If the objective is controlling which external domains can interact with your 
tenant rather than detecting compromised credentials:

* **External Collaboration Settings:** Allow or block B2B guest invitations for specific email domains.

* **Cross-Tenant Access Settings / Tenant Restrictions:** Control inbound and outbound access with specific external Entra tenants/domains.

---

# [What are autonomous system numbers (ASNs) and what are they used for?](https://share.gemini.google/IyUqqVQ4r7sf)  

An **Autonomous System Number (ASN)** is a unique numeric identifier 
assigned to an **Autonomous System (AS)**—a collection of IP networks 
and routers under the control of a single administrative entity 
(such as an Internet Service Provider, large enterprise, cloud provider, 
or university) that presents a unified routing policy to the broader Internet.

### How ASNs Work

* **Allocation:** Regional Internet Registries (RIRs)—such as `RIPE NCC, ARIN, APNIC, LACNIC, and AFRINIC`—assign ASNs to organizations and coordinate global numbering through `IANA`.

* **Size:** Originally 16-bit integers (1–65,534), ASNs expanded to 32-bit integers 
(up to 4,294,967,295) as the Internet grew. Ranges are split into **public ASNs** 
(globally routed) and **private ASNs** (such as 64512–65534 and 4200000000–4294967294, used internally or with single-homed/edge setups and stripped before announcing to the public Internet).

### What ASNs Are Used For

* **Border Gateway Protocol (BGP) Routing:** BGP is the routing protocol that connects different networks across the Internet. Routers use ASNs to identify neighboring networks, exchange reachability information, and prevent routing loops by checking the **AS_PATH** attribute (the list of ASNs a route has traversed).

* **Enforcing Routing Policies:** An organization uses its ASN to control how traffic enters and leaves its network—deciding which neighbors to accept routes from, which prefixes to advertise, and which paths to prefer based on business agreements (transit, peering, or customer relationships) or traffic engineering.

* **Peering and Interconnection:** Networks peering at Internet Exchange Points (IXPs) or via private interconnects reference ASNs to establish BGP sessions and exchange traffic directly without paying a third-party transit provider.

* **Network Security, Filtering, and Attribution:** Operators and security teams use ASNs to apply **RPKI** (Resource Public Key Infrastructure) route origin validation, filter bogon or unauthorized route announcements, trace the origin of network traffic or DDoS activity, and map IP blocks to specific organizations for capacity planning and troubleshooting.

---