[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q19

An organization operates workloads across Azure, AWS, and GCP. 
The security team needs to identify and prioritize chains of exposures 
that an adversary could traverse across the connected cloud environments 
by correlating resource exposure, identity permissions, and access to sensitive data.

Which Defender for Cloud capability should the organization use?

Select one answer option below.

### OPTION 01
Defender for DevOps with infrastructure-as-code scanning

### OPTION 02
Defender for Servers Plan 2 with Microsoft Defender Vulnerability Management

### OPTION 03
Microsoft Sentinel with multicloud data connectors and security workbooks

### OPTION 04
Defender CSPM with attack path analysis

## Answer

**Correct answer: OPTION 04 — Defender CSPM with attack path analysis**

Defender for Cloud's attack path analysis is designed to find exploitable routes 
from an external entry point to a critical asset. It uses the cloud security graph, 
which gathers multicloud context such as resource exposure, permissions, network connections, 
and lateral-movement possibilities. The analysis can show how an exposed resource and 
an identity's permissions could lead an attacker to sensitive data, then prioritize 
the resulting risk. 

Attack path analysis is a Defender CSPM capability and supports Azure, AWS, and GCP environments.
[^attack-path][^cspm]

### Why the other options are incorrect

- **OPTION 01 — Defender for DevOps with infrastructure-as-code scanning:** 
DevOps security focuses on code-to-cloud posture, including scanning IaC templates 
to catch configuration problems before deployment. It does not provide the requested 
analysis of exploitable paths through connected cloud resources, identities, and sensitive data.[^devops]

- **OPTION 02 — Defender for Servers Plan 2 with Microsoft Defender Vulnerability Management:** Defender for Servers improves machine security posture and protects servers against threats; vulnerability assessment helps identify weaknesses on machines. These are useful server-protection capabilities, but they are not the cross-cloud graph analysis that correlates exposures, permissions, and critical targets into attack paths.[^servers][^attack-path]
- **OPTION 03 — Microsoft Sentinel with multicloud data connectors and security workbooks:** Sentinel can collect and analyze security data from multiple clouds for monitoring, detection, investigation, and response. Connectors and workbooks do not, by themselves, provide Defender for Cloud's cloud-security-graph attack path analysis and its prioritization of exploitable routes to critical assets.[^sentinel][^connectors][^attack-path]

### References

[^attack-path]: [Security explorer and attack paths in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path) — describes the cloud security graph, its multicloud context (including exposure, permissions, and lateral movement), and how attack path analysis traces routes to critical assets.
[^cspm]: [What is Cloud Security Posture Management (CSPM)?](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management) — identifies attack path analysis as a Defender CSPM feature and lists Azure, AWS, and GCP support.
[^devops]: [Microsoft Defender for Cloud DevOps security benefits](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction) — describes DevOps security, including IaC scanning and code-to-cloud posture management.
[^servers]: [Plan a Defender for Servers deployment](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers) — describes server security recommendations, threat protection, and Plan 2 deployment.
[^sentinel]: [What is Microsoft Sentinel SIEM?](https://learn.microsoft.com/en-us/azure/sentinel/overview) — describes Sentinel's multicloud data collection and SIEM capabilities for monitoring, detection, investigation, and response.
[^connectors]: [Microsoft Sentinel data connectors](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources) — explains how Sentinel connectors ingest data from Microsoft and non-Microsoft sources.

---

# What is Defender CSPM with attack path analysis?

Defender CSPM with attack path analysis is a paid capability in Microsoft Defender for Cloud 
that maps how an attacker could chain security weaknesses from an external entry point to 
high-value cloud assets. 

Instead of listing isolated misconfigurations, it uses the cloud security graph to highlight 
real, exploitable routes and the exact fixes that break them. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path), 
[3] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management)

## How It Works

- Cloud Security Graph: 
Collects context across multicloud assets, identities, permissions, network connections, and 
vulnerabilities to map relationships and lateral movement paths. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://cloudgate.ae/blog/defender-for-cloud-cspm-baseline)

- Reachability and Context Validation: 
Evaluates external exposure and active reachability so teams focus on threats an attacker 
can actually reach and exploit. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path)

- Risk Prioritization and Remediation: 
Ranks attack paths by risk level and shows specific recommendations that sever the path 
to critical targets such as sensitive databases or storage. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path)

- Broader Resource Coverage: 
Covers virtual machines, storage accounts, containers, serverless workloads, unmanaged APIs, 
repositories, and AI agents across Azure and connected clouds. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://www.conceptualise.de/en/blog/defender-cloud-vs-third-party-cspm)

## Usage Examples

- Internet-Exposed VM to Sensitive Database: 
Tracing a path from a public-facing virtual machine with a known vulnerability 
and overly broad permissions to a database holding sensitive customer or payment records. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://cloudgate.ae/blog/defender-for-cloud-cspm-baseline)

- Public Storage with Sensitive Data: 
Flagging a storage container that allows unauthorized access and holds sensitive data, 
then prioritizing fixes that block public exposure. 

[1] (https://jakubfras.substack.com/p/defender-for-cloud-under-the-hood-cab)

- Choke Point Remediation: 
Identifying `shared nodes ("choke points")` where multiple attack paths converge 
so fixing one bottleneck eliminates several breach routes at once. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path)

- Regulatory Compliance Alignment: 
Supporting security governance alongside frameworks such as `NIS2, DORA, ISO 27001, and GDPR—relevant` 
for organizations operating in Italy and across the EU. 

[1] (https://www.conceptualise.de/en/blog/defender-cloud-vs-third-party-cspm)

## Related Terms and Synonyms

- `Attack Path Analysis (APA)`: 
The core method of tracing chained vulnerabilities, misconfigurations, and permissions to critical assets.

- Cloud Security Posture Management (CSPM): 
Continuous monitoring and hardening of cloud configurations and compliance.

- Cloud Security Graph: 
The underlying relationship map of assets, identities, and exposures used to query risks and attack paths.

- Exposure Management / Attack Surface Management: 
Broader terms in Microsoft Defender for correlating attack paths, choke points, and incident context. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path), 
[3] (https://www.qualys.com/fundamentals/what-is-attack-path-analysis),  
[4] (https://egroup-us.com/news/microsoft-defender-for-cloud-security-guide/),  
[5] (https://www.cloudquery.io/blog/what-is-a-cspm),  
[6] (https://learn.microsoft.com/en-us/answers/questions/1536516/difference-between-cspm-and-cwp)  

---

# What is Defender for DevOps with infrastructure-as-code scanning?

[Scan your connected GitHub repository or Azure DevOps project](https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities)  

`Defender for DevOps with infrastructure-as-code (IaC) scanning`—`part of Microsoft Defender for Cloud—`
is a cloud security capability that detects security vulnerabilities and misconfigurations in IaC templates 
before they are deployed to production. 

It connects DevOps platforms like `GitHub, Azure DevOps, and GitLab` to `Defender for Cloud` 
to give teams centralized visibility and `"shift-left" security`. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction), 
[3] (https://livebook.manning.com/learn/concepts/microsoft-defender-for-devops--platform/azure-security-2)

## How IaC Scanning Works

• Pipeline & Action Scanning: Runs via the Microsoft Security DevOps extension in Azure DevOps or a GitHub Action. You can target IaC files specifically (using categories: 'IaC') to keep pipeline runtimes shorter. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities)
• Agentless Code Scanning: Automatically discovers repositories and scans IaC templates, source code, and open-source dependencies without changing build or deployment pipelines. Scans can run in regional geographies such as the EU to meet data residency requirements. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/agentless-code-scanning)
• Included Scanning Engines: Uses built-in tools including Template Analyzer (with PSRule) for Azure Resource Manager (ARM) and Bicep templates, as well as Checkov and Terrascan for ARM, CloudFormation, Docker, Helm, Kubernetes, Kustomize, and Terraform. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities)

Common Usage Examples

• Catching Misconfigurations in Pull Requests: Flagging overly permissive network rules, unencrypted storage, or exposed resources in Terraform or Bicep files before code merges. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities), [2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction)
• Enforcing Baseline Standards Across Teams: Scanning multi-repository organizations on GitHub or Azure DevOps to spot drifted or non-compliant IaC templates. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/agentless-code-scanning), [2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities)
• Connecting Code to Cloud Risk: Linking IaC findings to cloud posture and attack-path analysis so teams can prioritize fixes that affect live environments. [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction), [2] (https://medium.com/@craig4shaw/devops-security-with-microsoft-defender-for-cloud-aaecae244750)

Related Terms and Synonyms

• Microsoft Defender for Cloud DevOps Security (the broader DevOps security capability within Defender for Cloud)
• Microsoft Security DevOps (MsDO) (the pipeline extension/action and scanner suite)
• IaC Static Analysis / IaC Posture Management
• Shift-Left Security / DevSecOps [1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/iac-vulnerabilities), [2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-devops-introduction), [3] (https://livebook.manning.com/learn/concepts/microsoft-defender-for-devops--platform/azure-security-2), [4] (https://www.cloudthat.com/resources/blog/integrating-microsoft-defender-with-azure-devops-for-secure-ci-cd)


---