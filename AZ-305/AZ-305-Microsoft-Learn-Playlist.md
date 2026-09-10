[AZ-305: Designing Microsoft Azure Infrastructure Solutions Microsoft Learn Course 17 videos Last updated on 30 Mar 2026](https://www.youtube.com/playlist?list=PLahhVEj9XNTejs0fgXT6HXaj_a_qsUoKa)  

[Course videos on Microsoft Learn - AZ-305](https://learn.microsoft.com/en-us/training/course-videos-on-shows?wt.mc_id=esi_coursevideos_video_wwl&tabs=copilotadministrator%2Cazureaiengineer%2Cdevopsengineer%2Cadministrator%2Cazureinfrasolutionsarchitect%2Cazureappdeveloper)  

[Cloud Adoption Framework for Microsoft](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)   
[Microsoft cloud security benchmark documentation (MCSB)](https://aka.ms/mcsbhttps://learn.microsoft.com/en-us/security/benchmark/azure/)
[Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)  

> With aka.ms/XXX
[Cloud Adoption Framework for Microsoft](https://aka.ms/caf)
[Microsoft cloud security benchmark documentation (MCSB)](https://aka.ms/mcsb)
[Azure Well-Architected Framework](https://aka.ms/waf)

> Specific to AZ-305
[Azure Architecture Center](https://learn.microsoft.com/en-us/azure/architecture/)    

---

# Episode 2: 
[Design a governance solution | AZ-305 | Episode 2 Microsoft Learn](https://www.youtube.com/watch?v=AnWVFNw-Vik)  

How to design for:

- Governance: maintain control over apps and resources in Azure through well defined processes
- Management Groups: help manage Policies, Access, Compliance and Budgeting accross multiple subscriptions
- Azure Subscriptions: unit of billing, scale and isolation
- Resource Groups: lifecycle resources containers, where resources are deployed and managed 
- Resources
- Resource Tagging
- Azure Policy
- RBAC
- Azure Landing Zones

## Design for Management Groups

Management Groups are used to manage groups of subscriptions under the same guardrails and 
to isolate workloads; they allow to apply Policies, and manage Access, Compliance and Budgeting
accross multiple subscriptions.

An Microsoft Entra ID group representing the IT management will be assigned to the top-level MG
through RBAC. Nested MGs are then use to represent the different sections of the organization,
such as departments, branches, operation teams, geographical areas, etc.

A practical example of the use of MGs in a Microsoft Entra ID tenant could be the following:

- Contoso the top-level MG to which the IT management team is assigned with Contributor or Owner role
  - Sales to which the Sales group is assigned with RBAC with approriate roles assignments
  - Corporate..
  - IT..
    - Development: by splitting the MGs with subgroups for DEV and PRD changes can be safely tested by the IT team before rolling out to PRD
    - Production
      - Subscription01: different subs are used for scale or isolation
      - Subscription02
  - HR..
  - US..
  - Pacific..
  - Europe..

> Notes

- There can be up to 6 layers of nested MGs
- Azure Subscriptions can be moved from one MG to another

> Recommendations

- Keep the management group hierarchy reasonably flat because layers make it hard to reason about them and are messy to maintain and debug
- Consider a top-level management group
- Consider an organizational or departmental structure
- Consider a geographical structure
- Consider a production management group
- Consider a sandbox management group
- Consider isolating sensitive information in a separate management group

---

## If the IT team only needs to configure access using Azure RBAC role assignments at the Management Group level.

For this scenario, assign the foillowing Azure RBAC roles at the root Management Group scope:

- the `Resource Policy Contributor` role AND the `Cost Management Contributor` 
- OR simply the broader `Management Group Contributor` or `Owner` role 

| Role | Permitted Actions | Ideal Use Case |
| :--- | :--- | :--- |
| **Management Group Contributor** | Full management of management groups, policy assignments, budget configurations, and compliance rules (excluding RBAC role delegation). | Best practice for the IT team if they do not need to grant access permissions to other users. |
| **Owner** | Full management of all resources, policies, budgets, plus the ability to grant or revoke RBAC access to others. | Required if the IT team must also manage user/group access permissions at the top-level Management Group. |
| **Resource Policy Contributor** & **Cost Management Contributor** | Fine-grained privileges dedicated strictly to defining Azure Policies, compliance rules, and managing budgets. | Best applied if enforcing strict Principle of Least Privilege (PoLP). |

---

# Which Microsoft Entra ID role should be assigned to a Microsoft Entra group that represents the IT team in charge of maintaining the top-level Management Group in a tenant? They will set the policies, budgets and define compliance at the top-level Management Group.

To provide the exact Microsoft Entra ID (Azure AD) role, it helps to distinguish between 
**Microsoft Entra ID roles** (identity management) and **Azure RBAC roles** (resource management):

1. **Azure RBAC Role (Recommended for Management Groups):**
* **Management Group Contributor** or **Owner**: Assigning this Azure RBAC role at the root/top-level
Management Group scope allows the IT team to 

- define policies (via Azure Policy), 
- set budgets (via Azure Cost Management), and 
- enforce compliance 

across all subscriptions inheriting from that management group.

2. **Microsoft Entra ID Role (Identity/Directory Scoped):**

* If strictly looking for a directory-level role with global scope over tenant configurations, 
**Global Administrator** provides unrestricted access, though **Privileged Role Administrator** 
is used to manage role assignments themselves. However, Entra ID roles do not natively grant 
permission to manage Azure resource policies/budgets without Azure RBAC assignments or elevated 
access ("Access management for Azure resources" toggle enabled).

Are you looking to configure access purely using **Azure RBAC role assignments** at 
the Management Group level, or do you need to grant directory-level administrative privileges 
via **Microsoft Entra ID roles**?

---

# Episode 1

[Course introduction | Design Microsoft Azure Infrastructure Solutions | AZ-305 | Episode 1](https://www.youtube.com/watch?v=5h_pbmMb7T4&list=PLahhVEj9XNTejs0fgXT6HXaj_a_qsUoKa&index=3)  

---

# Comparing best practice frameworks (https://aka.ms/xxx)

---

## MCSB

Includes **a collection of high-impact security recommendations** 
you can use to help secure cloud services in a single or multicloud environment.

---

## CAF

- Full life cycle framework
- Provides best practices, documentation, and tools that help you create and implement business and technology strategies

---

# WAF

- A set multiload of guiding tenets that can be used to improve the quality of a workload
- The framework consists of five pillars of architectural excellence
- The framework always targets a specific workload

## When should an architect use the Well-Architected Framework use in the context of the AZ-305 Solution Architect Exam?

1. Every time a new workload needs to be designed 
2. Every time an existing workload needs to be modernized
3. Every time an existing workload needs to be troubleshooted because it underperforms, such as it is too expensive, unstable, slow or risky

An architect should use the Microsoft Azure Well-Architected Framework (WAF) throughout the entire lifecycle of 
designing, evaluating, and evolving cloud solutions when answering scenario-based questions and making design decisions 
for the AZ-305 exam. [1, 2] 

------------------------------
## When to Apply the Framework in AZ-305

* Translating Business Requirements: Use WAF when converting client needs—like uptime targets, budget constraints, or compliance rules—into concrete Azure services and structural designs. [3, 4] 
* Evaluating Trade-offs: Apply the framework when balancing conflicting priorities, such as increasing Reliability (adding redundancy) which impacts Cost Optimization (raising expenses). [1, 2] 
* Designing Workload Categories: Reference WAF when deciding how to structure specific domains tested in the exam:
* Infrastructure & Performance Efficiency: Choosing between IaaS, PaaS, or serverless scaling.
   * Business Continuity & Reliability: Setting Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO) using multi-region or active-passive patterns.
   * Security & Governance: Implementing identity perimeters, role-based access control (RBAC), and policy guardrails.
   * Operational Excellence: Incorporating monitoring, automation, and DevOps practices into the deployment lifecycle. [3, 5, 6, 7, 8, 9] 
* Answering Case Studies: Use the five pillars (Reliability, Security, Cost Optimization, Operational Excellence, Performance Efficiency) as a mental checklist during exam case studies to filter out incorrect multiple-choice options that violate core cloud design principles. [1, 6] 

[1] [https://www.certlibrary.com](https://www.certlibrary.com/info/AZ-305)
[2] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/what-is-well-architected-framework)
[3] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/)
[4] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/architect-role/fundamentals)
[5] [https://medium.com](https://medium.com/@christian.dussol/beyond-memorization-how-architectural-thinking-skills-transform-az-305-exam-success-9ed69c14150f)
[6] [https://techmandan.blog](https://techmandan.blog/posts/my-step-by-step-study-plan-for-passing-the-azure-solutions-architect-expert-az-305-exam/)
[7] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/)
[8] [https://medium.com](https://medium.com/all-about-microsoft-azure/az-305-learning-series-microsoft-azure-well-architected-framework-reliability-f569a0558479)
[9] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/pillars)

---

# CAF Govern, CAF Secure and CAF mANAGE in the context of the AZ-305 Solution Architect Exam?

In the context of Microsoft Azure and the AZ-305 Architecting Microsoft Azure Infrastructure Solutions exam, 
**CAF** refers to the **Microsoft Cloud Adoption Framework for Azure**. 

The Cloud Adoption Framework guides organizations through cloud alignment, strategy, and operations. 
Within the framework's **Govern** and **Manage** methodologies, as well as the overarching security guidance (**Secure**), 
Azure structures key operational disciplines for enterprise scale.

---

### 1. CAF Govern (Governance Methodology)

CAF Govern focuses on maintaining control, compliance, and risk management without blocking developer velocity.

* **AZ-305 Core Focus:** Designing landing zones, governance hierarchies, and subscription strategies using Azure tools.
* **Key Principles & Tools:**
  * **Five Disciplines of Governance:** Cost Management, Security Baseline, Identity Baseline, Resource Consistency, and Deployment Acceleration.
  * **Azure Management Groups:** Organizing subscriptions hierarchically to apply policies efficiently across the enterprise.
  * **Azure Policy & Blueprints:** Enforcing compliance rules (e.g., restricting locations, requiring tags, enforcing secure endpoints) and automated provisioning.
  * **Cost Management & Billing:** Setting budgets, scopes, and cost allocation tags.

---

### 2. CAF Secure (Security Methodology)
CAF Secure integrates security into every phase of cloud adoption, drawing heavily from the **Microsoft Cybersecurity Reference Architectures (MCRA)** and the **Zero Trust Model**.

* **AZ-305 Core Focus:** Designing end-to-end secure architecture, identity controls, data protection, and threat monitoring.
* **Key Principles & Tools:**
  * **Zero Trust Architecture:** Assume breach, verify explicitly, and grant least privilege access.
  * **Microsoft Defender for Cloud:** Monitoring security posture management (CPSM) and workload protection across hybrid/multicloud environments.
  * **Microsoft Sentinel:** Cloud-native SIEM/SOAR for centralized log analytics and threat response.
  * **Identity & Access Management:** Azure Active Directory (Entra ID), Privileged Identity Management (PIM), Conditional Access, and RBAC design.
  * **Data & Network Security:** Encryption at rest/in transit, Key Vault, Private Endpoints, Firewall, and NSGs.

---

### 3. CAF Manage (Management Methodology)
CAF Manage addresses business continuity, operational baseline creation, and daily workload management once workloads are live in Azure.

* **AZ-305 Core Focus:** Designing reliable, resilient architectures with appropriate operational monitoring and disaster recovery strategies.
* **Key Principles & Tools:**
  * **Operations Baseline:** Defining standard operating procedures for patch management, backup, and monitoring across all resources.
  * **Azure Monitor & Log Analytics:** Aggregating metrics, traces, and logs across subscriptions for continuous observability.
  * **Business Continuity & Disaster Recovery (BCDR):** Designing architectures using Azure Backup and Azure Site Recovery (ASR) to meet business RTO (Recovery Time Objective) and RPO (Recovery Point Objective) requirements.
  * **High Availability (HA) Design:** Utilizing Availability Sets, Availability Zones, and regional pairs.

---

### How They Compare for AZ-305

| Domain | Primary Goal | Key Azure Services Tested |
| :--- | :--- | :--- |
| **CAF Govern** | Compliance, cost control, organizational hierarchy | Management Groups, Azure Policy, Azure Resource Manager (ARM), Tagging |
| **CAF Secure** | Risk mitigation, access control, threat defense | Entra ID, Microsoft Defender for Cloud, Key Vault, Private Link, Sentinel |
| **CAF Manage** | Operations, uptime, monitoring, backup/DR | Azure Monitor, Azure Site Recovery (ASR), Azure Backup, Log Analytics |

---

# What is the Azure Well-Architected Framework in the context of the AZ-305 Solution Architect Exam?

The Azure Well-Architected Framework is a set of guiding principles, best practices, 
and design tools used to build secure, high-performing, resilient, and efficient workloads on Azure. [1, 2] 

For the [Exam AZ-305: Designing Microsoft Azure Infrastructure Solutions](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/), the framework serves as the core evaluation standard for how a solutions architect 
translates complex business requirements into robust technical infrastructure designs. [3, 4] 

------------------------------

## The Five Pillars of the Framework

The AZ-305 exam tests your ability to balance and apply these five key pillars in architectural scenarios: [1, 5] 

* Reliability: Designing systems to recover from failures and continue functioning. This involves defining RTO/RPO (Recovery Time/Point Objectives), implementing redundancy (multi-region or availability zones), and ensuring high availability. [1, 6] 

* Security: Protecting applications and data through identity management (e.g., Microsoft Entra ID), role-based access control (RBAC), encryption, and threat protection. [1, 6, 7] 

* Cost Optimization: Managing and minimizing unnecessary cloud spend. You must know how to use budgets, alerts, tagging, reservations, and savings plans to align architecture with financial constraints. [2, 6, 7] 

* Operational Excellence: Streamlining deployment and maintenance through automation, continuous monitoring, and infrastructure-as-code (IaC). [1, 6, 8] 

* Performance Efficiency: Ensuring workloads can scale dynamically (horizontally or vertically) to meet fluctuating user demand and load testing requirements. [1, 2, 6] 

------------------------------

## Why It Matters for the AZ-305 Exam

* Design Trade-offs: The exam frequently presents scenarios where optimizing for one pillar impacts another (e.g., increasing Reliability via multi-region replication increases Cost). You must choose the optimal compromise based on business priorities. [2, 9] 

* Service Selection: Questions test your ability to select specific Azure services (like Azure Front Door, AKS, or Azure SQL) that natively satisfy the architectural standards defined by the framework. [5, 10] 

* Evaluation & Governance: You are expected to know assessment tools like Azure Advisor and the [Azure Well-Architected Review](https://learn.microsoft.com/en-us/azure/well-architected/design-guides/implementing-recommendations) to continuously evaluate and improve cloud architectures. [6, 11] 


[1] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/)
[2] [https://azure.microsoft.com](https://azure.microsoft.com/en-us/solutions/well-architected)
[3] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/)
[4] [https://www.mindmeshacademy.com](https://www.mindmeshacademy.com/certifications/azure/az-305-designing-microsoft-azure-infrastructure-solutions/study-guide/1-2-understanding-the-az-305-exam-purpose-audience)
[5] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/training/paths/azure-well-architected-framework/)
[6] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/pillars)
[7] [https://sailor.sh](https://sailor.sh/blog/az-305-exam-guide-2026/)
[8] [https://k21academy.com](https://k21academy.com/azure-cloud/az-305-certification/)
[9] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/what-is-well-architected-framework)
[10] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/service-guides/)
[11] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/well-architected/design-guides/implementing-recommendations)

---

# What is the role of Azure Advisor in the context of the AZ-305 Solution Architect Exam?

Azure Advisor acts as a built-in cloud consultant that evaluates your resource configurations and usage telemetry 
to provide proactive best-practice recommendations. [1] 

In the context of the AZ-305 (Designing Microsoft Azure Infrastructure Solutions) exam, Azure Advisor maps directly to 
the Azure Well-Architected Framework, serving as a practical tool for governance, optimization, and continuous improvement. [2, 3] 

------------------------------
## Core Pillars and Exam Relevance

* Cost Optimization: Identifies idle resources, underutilized virtual machines, and recommends reserved instances to lower overall spending. AZ-305 tests your ability to design cost-effective solutions. [1, 4, 5] 

* Security: Detects vulnerabilities, flags missing security baselines, and integrates recommendations from Microsoft Defender for Cloud. Security design is a core component of the exam. [2, 6] 

* Reliability (Resiliency): Highlights single points of failure, unbacked-up disks, or missing high-availability configurations. The exam heavily emphasizes business continuity and reliable infrastructure design. [1, 4, 6, 7] 

* Performance Efficiency: Suggests scaling options or hardware upgrades for sluggish or over-taxed compute and storage resources. [1, 4] 

* Operational Excellence: Advises on deployment visibility, tagging strategies, and resource management best practices. [4] 

------------------------------
## Key Takeaways for AZ-305 Candidates

* Alignment with Frameworks: Understand that Azure Advisor is the operational manifestation of the Azure Well-Architected Framework (Cost, Security, Reliability, Performance Efficiency, and Operational Excellence). [3, 4] 

* Proactive vs. Reactive: Know that Azure Advisor provides proactive configuration advice, whereas Azure Monitor provides reactive/real-time telemetry, logs, and metrics. [1, 8] 

* Exam Scenarios: Questions may present a scenario where an existing deployment suffers from high costs, poor availability, or security gaps, and Azure Advisor is the correct tool to recommend for assessment and remediation planning.


[1] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/advisor/advisor-overview)
[2] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-305/)
[3] [https://flashgenius.net](https://flashgenius.net/blog-article/how-to-become-an-azure-solutions-architect-expert-az-305-full-step-by-step-guide-2025)
[4] [https://tutorialsdojo.com](https://tutorialsdojo.com/azure-advisor/)
[5] [https://crackcerts.com](https://crackcerts.com/exam-guide/az-305)
[6] [https://k21academy.com](https://k21academy.com/azure-cloud/az-305-certification/)
[7] [https://www.readynez.com](https://www.readynez.com/en/training/courses/vendors/microsoft/certified-azure-solutions-architect-course-az305/)
[8] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/azure/mysql/flexible-server/concepts-business-continuity-advisor-monitor)

---

# What is the MCAF in the context of the AZ-305 Solution Architect Exam?

In the context of the Microsoft Azure Solutions Architect Expert certification and the AZ-305 exam, 
MCAF stands for the `Microsoft Cloud Adoption Framework` for Azure (frequently abbreviated as just CAF). 
It is a (playbook) complete set of guides, best practices, and tools from Microsoft that help organizations 
plan, build, and govern their cloud environments. [1, 2, 3] 

The AZ-305 exam tests your ability to align technical designs with this framework. [4] 

## Core Phases of MCAF

The framework breaks the cloud journey into distinct, logical phases:

* Strategy: Define business outcomes and motivations for moving to the cloud.
* Plan: Align people, processes, and the digital estate into a concrete migration or adoption plan.
* Ready: Prepare the cloud environment using Landing Zones for operational readiness.
* Adopt: Migrate, modernize, and innovate applications and workloads in Azure.
* Govern: Establish corporate policies, security baselines, and cost management controls.
* Manage: Monitor health, operations, and performance of cloud resources. [1, 5] 

## Importance for the AZ-305 Exam

* Design Alignment: Exam scenarios expect you to recommend solutions that respect organizational governance and landing zone best practices outlined in MCAF. [3, 6] 
* Trade-off Decisions: You must balance speed of adoption with proper management and governance. [6] 
* Complementary Framework: MCAF works alongside the Microsoft Azure Well-Architected Framework (WAF), which focuses on specific workload quality pillars like reliability, security, and cost optimization. [7, 8] 


[1] [https://ifgeekthen.nttdata.com](https://ifgeekthen.nttdata.com/s/post/stairway-azure-mcaf-el-framework-de-adopcion-de-la-nube-de-microsoft-MCXOGZVM4KMBHURCM3PO2AF62UOY?language=en_US)
[2] [https://cybera.services](https://cybera.services/Optimizing-cloud-transitions.html)
[3] [https://flashgenius.net](https://flashgenius.net/blog-article/how-to-become-an-azure-solutions-architect-expert-az-305-full-step-by-step-guide-2025)
[4] [https://azurecertprep.github.io](https://azurecertprep.github.io/docs/az-305/overview)
[5] [https://techcommunity.microsoft.com](https://techcommunity.microsoft.com/discussions/azuremigration/cloud-center-of-excellence-ccoe-en-microsoft-cloud-adoption-framework-mcaf/2075305)
[6] [https://powerkram.com](https://powerkram.com/exams/microsoft/az-305-azure-architect-expert/)
[7] [https://www.youtube.com](https://www.youtube.com/watch?v=5h_pbmMb7T4&t=64)
[8] [https://www.certlibrary.com](https://www.certlibrary.com/info/AZ-305)


---