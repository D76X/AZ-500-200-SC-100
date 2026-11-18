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

Microsoft Defender Vulnerability Management is a risk-based security solution that continuously discovers, assesses, prioritizes, and remediates software vulnerabilities and misconfigurations across endpoints, cloud workloads, and network devices. It operates across platforms including Windows, macOS, Linux, Android, and iOS. [1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), [2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management)

Key Capabilities

• Continuous discovery and visibility: Tracks software inventories, vulnerable open-source or third-party components, browser extensions, digital certificates, and network shares in near real time. [1] (https://www.youtube.com/watch?v=QIwrpjpqrBc), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial), [3] (https://jeffreyappel.nl/microsoft-defender-for-endpoint-series-defender-vulnerability-management-part5/)
• Risk-based prioritization: Combines Microsoft threat intelligence, breach likelihood predictions, and business context to rank which flaws pose the greatest real-world risk. [1] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
• Built-in remediation and tracking: Offers remediation workflows, security baseline assessments, application blocking, and real-time progress metrics such as exposure scores and Microsoft Secure Score for Devices. [1] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)
• Flexible monitoring: Uses built-in agent capabilities, authenticated scanning, and agentless methods to detect issues even when devices are off the corporate network or in cloud workloads. [1] (https://www.microsoft.com/en-us/security/business/threat-protection/microsoft-defender-vulnerability-management), [2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), [3] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)

Common Usage Examples

• Prioritizing critical patches: Ranking hundreds of known CVEs (Common Vulnerabilities and Exposures) so IT teams fix flaws actively exploited in the wild on high-value servers first. [1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), [2] (https://www.microsoft.com/en-gb/security/business/threat-protection/microsoft-defender-vulnerability-management), [3] (https://jeffreyappel.nl/microsoft-defender-for-endpoint-series-defender-vulnerability-management-part5/)
• Auditing third-party components: Identifying risky libraries—such as older versions of OpenSSL or Apache Log4j—and unsafe device configurations that basic OS updates miss. [1] (https://www.youtube.com/watch?v=QIwrpjpqrBc), [2] (https://www.youtube.com/watch?v=CywLfSYz-iM)
• Mitigating exposed software: Blocking vulnerable applications or tracking remediation tasks in the Microsoft Defender portal (under Exposure management) until patches are deployed. [1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), [3] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-trial)

Related Terms and Context

• Threat and Vulnerability Management (TVM): An earlier name and foundational capability set associated with Microsoft Defender for Endpoint vulnerability assessment.
• Exposure Management: The broader Microsoft Defender portal area where vulnerability data and security exposure insights are consolidated. [1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)
• Extended Detection and Response (XDR) & Cloud Security Posture Management (CSPM): Adjacent security categories that pair with vulnerability management to connect weakness discovery with threat detection and cloud configuration hardening. [1] (https://www.microsoft.com/en-gb/security/business/security-101/what-is-vulnerability-management), [2] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)
For plan details and feature availability, see Microsoft Defender Vulnerability Management plans. [1] (https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)

---