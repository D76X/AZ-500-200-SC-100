# Eaxm Practice Cloud and AI Security Engineer Associate (SC-500)

[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q02

A financial services organization runs a hybrid environment with 
Azure VMs, on-premises servers, and AWS EC2 instances. 

The security team wants a unified vulnerability management solution that covers 
all three environments using Defender for Servers.

Which combination of technologies enables this multicloud and hybrid coverage?

Select one answer option below.

## OPTION 01
Azure Arc for on-premises servers and native AWS connector for EC2 instances, both enrolled in Defender for Servers

## OPTION 02
Defender for Cloud regulatory compliance assessments applied to all Azure subscriptions and connected AWS accounts, alongside Azure Policy for on-premises servers

## OPTION 03
Microsoft Sentinel data connectors ingesting AWS CloudTrail logs and on-premises syslog sources into a centralized Log Analytics workspace for correlation

## OPTION 04
Azure Monitor Agent deployed to Azure VMs, on-premises servers, and AWS EC2 instances, reporting to a single Log Analytics workspace

---

# Gemini Argon 4

Correct Answer

## OPTION 01:
Azure Arc for on-premises servers and native AWS connector for EC2 instances, both enrolled in Defender for Servers

## Why OPTION 01 is Correct

- **Azure VMs**: Native Azure virtual machines are automatically discovered in the Azure subscription and protected when the **Defender for Servers** plan is enabled on the subscription.
- **On-Premises Servers via Azure Arc**: Onboarding on-premises physical and virtual machines as **Azure Arc-enabled servers** projects them into Azure Resource Manager as native Azure resources. Once connected to an Azure subscription with Defender for Servers enabled, Defender for Cloud can automatically provision the Microsoft Defender for Endpoint agent (with integrated **Microsoft Defender Vulnerability Management**) to assess OS and software vulnerabilities.
- **AWS EC2 Instances via Native AWS Connector**: Connecting AWS accounts using Defender for Cloud's **native AWS multicloud connector** and enabling the **Defender for Servers** plan extends unified vulnerability management to EC2 instances through **agentless vulnerability scanning** (via AWS snapshot analysis in Plan 2) and/or **auto-provisioning Azure Arc and Defender for Endpoint** (via AWS Systems Manager).

---

## Why the Other Options Should Not Be Selected

> **OPTION 02**: Defender for Cloud regulatory compliance assessments applied to all Azure subscriptions and connected AWS accounts, alongside Azure Policy for on-premises servers

- **Why it's wrong**: 
  1. **Regulatory compliance assessments** (part of CSPM) evaluate cloud resource configurations against compliance standards (such as CIS, PCI DSS, NIST, or Microsoft Cloud Security Benchmark); they do not perform OS/software CVE vulnerability scanning on servers.
  2. **Azure Policy** cannot be applied directly to on-premises servers unless those servers are first onboarded to **Azure Arc** (and even then, Azure Machine Configuration checks OS configuration baselines rather than providing Defender for Servers CVE vulnerability management).

> **OPTION 03**: Microsoft Sentinel data connectors ingesting AWS CloudTrail logs and on-premises syslog sources into a centralized Log Analytics workspace for correlation

- **Why it's wrong**: **Microsoft Sentinel** is a cloud-native **SIEM/SOAR** solution used for log ingestion, threat detection, and security event correlation. Ingesting AWS CloudTrail (control-plane activity logs) and syslog data does not provide server vulnerability assessment (CVE scanning) or integrate with Defender for Servers vulnerability management.

> **OPTION 04**: Azure Monitor Agent deployed to Azure VMs, on-premises servers, and AWS EC2 instances, reporting to a single Log Analytics workspace

- **Why it's wrong**: 
  1. **Azure Monitor Agent (AMA)** collects performance telemetry and security event logs into a Log Analytics workspace; it is **not** a vulnerability scanner. Microsoft explicitly notes that Defender for Servers no longer uses AMA for most plan features, relying instead on **agentless machine scanning** and **Microsoft Defender for Endpoint / Defender Vulnerability Management** (AMA is only used for the 500-MB/day data ingestion benefit).
  2. Furthermore, deploying AMA to non-Azure machines (on-premises or AWS EC2) requires **Azure Arc** as a prerequisite anyway.

---

# References

- [Overview of Defender for Servers in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-overview)
- [Vulnerability scanning in the Defender for Servers plan in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/auto-deploy-vulnerability-assessment)
- [Connect your on-premises machines to Microsoft Defender for Cloud (Azure Arc)](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-machines)
- [Connect your AWS account to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-aws)
- [Understand Defender for Servers data collection in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers-agents)

---

