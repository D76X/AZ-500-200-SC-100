[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q14

Fabrikam Financial recently completed the acquisition of a smaller firm, Northwind Trading, and inherited an unknown number of internet-facing web applications and subdomains that Northwind's IT team provisioned outside of any centrally managed Azure subscription or Microsoft Entra tenant. Fabrikam's own Azure subscription, Sub-Fabrikam, has full Defender for Cloud coverage, including Defender CSPM with attack path analysis enabled, and Microsoft Defender Vulnerability Management is configured on all known virtual machines.

The security team needs to identify any Northwind-owned domains, subdomains, and externally reachable services that were never registered in Fabrikam's Azure environment, so each discovered asset can be evaluated for exposure and brought under centralized management where appropriate. The solution must:

Surface internet-facing assets that exist outside of Sub-Fabrikam and outside Microsoft Entra ID, based only on their public-facing footprint (domains, DNS records, certificates, IP ranges).
Require no prior registration of the asset in Azure or Entra ID before it can be discovered.
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