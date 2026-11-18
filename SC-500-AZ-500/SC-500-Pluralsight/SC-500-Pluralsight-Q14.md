[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q14

Fabrikam Financial recently completed the acquisition of a smaller firm, Northwind Trading, and inherited 
an unknown number of internet-facing web applications and subdomains that Northwind's IT team provisioned 
outside of any centrally managed Azure subscription or Microsoft Entra tenant. Fabrikam's own Azure subscription, 
Sub-Fabrikam, has `full Defender for Cloud coverage`, including `Defender CSPM` with attack path analysis enabled, 
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