
[SC-100: Microsoft Cybersecurity Architect Microsoft Learn Course 27 videos Last updated on 6 Feb 2026](https://www.youtube.com/playlist?list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_)  

[Cloud Adoption Framework for Microsoft](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)   
[Azure Architecture Center](https://learn.microsoft.com/en-us/azure/architecture/)    
[Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)  
[WAF > Pillars > Security Design Principles](https://learn.microsoft.com/en-us/azure/well-architected/security/principles)   

[Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/) 
[Zero Trust Guidance Center](https://aka.ms/ztguide/)  

> With aka.ms/XXX
[Microsoft cloud security benchmark documentation (MCSB)](https://aka.ms/mcsb)
[Cloud Adoption Framework for Microsoft](https://aka.ms/caf)
[Azure Well-Architected Framework](https://aka.ms/waf)
[WAF > Pillars > Security quick links](http://aka.ms/wafsecure)

[CAF Secure](https://aka.ms/caf)

---

# Playlist

[SC-100: Microsoft Cybersecurity Architect Microsoft Learn Playlist](https://www.youtube.com/playlist?list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_)  


---

# Understand the Azure Well-Architected Framework (WAF) | SC-100 | Episode 7

[Understand the Azure Well-Architected Framework (WAF) | SC-100 | Episode 7](https://www.youtube.com/watch?v=IaIoGe2IGAA)  

[WAF > Pillars > Security quick links](http://aka.ms/wafsecure)
[WAF > Pillars > Security Design Principles](https://learn.microsoft.com/en-us/azure/well-architected/security/principles)   

---

WAF is **design framework** used to help to build software architectures 
in the cloud based on workloads that possess the following properties:

- resiliency
- recoverability
- availablility
- can deliver a sufficient Return Of Investment (ROI)
- can accomplish their purpuse within an acceptable timeframe
- be secure as they need to be
- can scale with the demand
- can be orderly ans safely developed, deployed and maintained over their lifecycle

## The Five Pillars of the WAF Framework

* Reliability: Designing systems to recover from failures and continue functioning. This involves defining RTO/RPO (Recovery Time/Point Objectives), implementing redundancy (multi-region or availability zones), and ensuring high availability. [1, 6] 

* Security: Protecting applications and data through identity management (e.g., Microsoft Entra ID), role-based access control (RBAC), encryption, and threat protection. [1, 6, 7] 

* Cost Optimization: Managing and minimizing unnecessary cloud spend. You must know how to use budgets, alerts, tagging, reservations, and savings plans to align architecture with financial constraints. [2, 6, 7] 

* Operational Excellence: Streamlining deployment and maintenance through automation, continuous monitoring, and infrastructure-as-code (IaC). [1, 6, 8] 

* Performance Efficiency: Ensuring workloads can scale dynamically (horizontally or vertically) to meet fluctuating user demand and load testing requirements. [1, 2, 6] 

The AZ-305 exam tests your ability to balance and apply these five key pillars 
in architectural scenarios. [1, 5]

Each pillar provides:
- recommended practices
- risk considerations
- tradeoffs

The design decisions must be lalance accross all 5 pillars given the business requirements. 
Workload acrhictecture is NOT the same as its implementation!

The Security architect and the Soulution architect use WAF to set up the application for 
success; by applying the principles present in WAF it is more likely that the implementation will lead to success. However, its implementation details will depend on the given specific business  requirements.

---

# Episode 6: How to Secure Cloud Adoption?

[Cloud Adoption Framework (CAF) for Azure | SC-100 | Episode 6](https://www.youtube.com/watch?v=tQDBts92dJI)  

[CAF Security teams, roles, and functions](https://aka.ms/securityroles)  

CAF is a methodology that guides organizations through the process of migrating their applications and data to the cloud.

> Learning objectives

- What is the Cloud Adoption Framework (CAF)?
- What is Cloud Adoption Framework Secure?
- What are Cloud Adoption Framework Landing Zones?

## What is the Cloud Adoption Framework (CAF) for Azure

The Microsoft Cloud Adoption Framework for Azure is a full lifecycle framework that enables cloud architects, IT professionals, and business decision makers to achieve their cloud adoption goals. It provides best practices, documentation, and tools that help you create and implement business and technology strategies for the cloud.

Following best practices for the Cloud Adoption Framework allows your organization to better align business and technical strategies and ensure success. Watch the following video to learn more.

Cloud Adoption Framework consists of nine main activities called "methodologies".
Each methodology is a process or stage that an organization will need to navigate to adopt the cloud.

## Cloud Adoption Framework methodologies

1. Strategy: Define business justification and expected adoption outcomes
2. Plan: Align actionable adoption plans to business outcomes
3. Ready: Prepare your cloud environment for planned changes

4. Migrate: Migrate and modernize existing workloads
5. Innovate: Develop new cloud-native or hybrid solutions
6. Secure: Improve security over time **

7. Manage: Manage operations for cloud and hybrid solutions
8. Govern: Govern your environment and workloads
9. Organize: Align the teams and roles supporting your organization's cloud adoption efforts

** in SC-100 the focus is on the `Security` methodologies: [CAF Secure](https://aka.ms/caf)
But in AZ-305 is on any of the others.

---

# CAF Secure methodology
[CAF Secure methodology](https://aka.ms/caf)

## Cloud Security Team
Establish a team with expertise and experience for security and cloud.
Include members of the security team, cloud Center of Excellence (cCoE), IT operations and others.

## Business Alignment
Establish  cross-org processes to scale cloud security throughout the business.

- Risk Insights: 
Integrate security insights into risk management framework and digital initiatives

- Security Integration
Integrate security insights and practices into business and IT processes, integrate security disciplines together

- Business Resilience
Ensure organization can operate during attacks and rapidly regain full operational status.
It is better to be able to even partially operate during an attack or breach than being unable to operate at all.

## Security disciplines
Implement proven security processes build on modern, cloud-based security tools.

- Access Control
Establish Zero Trust access model to modern and legacy assets using identity & network controls
Create access boundaries and segmentation to reduce the blast radius of any security breach.

- Security Operations
Monitor Security Operations to Detect, Respond, and Recover from attacks; 
Hunt for hidden threats; 
Share threat intelligence broadly
Use data to continuosly reduce the risk of security braches.

- Asset Protection
Protect sensitive data, systems, networks, applications, identities, devices, etc. 
to minimize the risk to the overall environment.
Continuously discover, classify & secure assets.

- Security Governance
Delegate decision, acellerate innovation.
Use data to drive decisions.
Continuously Identify, measure, and manage security posture to reduce risk & maintain compliance.
Use data to drive decisions.

- Innovation Security
Security must become an integral part of DevSecOps; security expertise must be integrated in 
high-frequency cycles.
Shift decision-making from centrilized teams to workload-focussed teams.
Integrate Security into DevSecOps processes. 
Align security, development, and operations practices.

---

# What is DevSecOps in the context of the SC-100 Security Architect Exam?

In the context of the Microsoft SC-100 (Cybersecurity Architect) exam, 
DevSecOps is the practice of embedding security natively into the application 
development and cloud infrastructure lifecycle rather than treating it as an 
afterthought or a final gate before production. [1, 2] 

------------------------------

## Core Concepts Tested in SC-100

* Shift-Left Security: 

Moving security testing, code scanning, and policy validation to the earliest stages 
of development (IDE, commit, and build) to catch vulnerabilities before deployment. [1, 2] 

* Shift-Right Security: 

Continuing security testing, performance evaluation, and anomaly monitoring in live, 
post-production and runtime environments. [1] 

* Policy-as-Code & Infrastructure-as-Code (IaC): 

Using automated templates and codified policies to validate cloud resources and prevent 
misconfigurations in multi-cloud environments (like Azure or GitHub) before they deploy. [3, 4] 

* Software Supply Chain Protection: 

Implementing continuous integration (CI) pipelines that run static analysis, 
software composition analysis (SCA), and artifact signing. [3] 

* Microsoft Toolchain Integration: 

Leveraging tools like Microsoft Defender for DevOps to scan code repositories, 
correlate security recommendations directly into developer toolchains 
(such as GitHub Actions and Azure DevOps), and manage posture across multicloud pipelines. [2, 3] 

------------------------------
## Key Stages in a DevSecOps Architecture

| Stage | Security Focus | Examples in SC-100 |
|---|---|---|
| Build | Secure code and dependencies | Static Application Security Testing (SAST), container image scanning, and managing open-source dependencies. |
| Test | Automated policy and vulnerability checks | Software Composition Analysis (SCA), validating infrastructure templates, and enforcing compliance gates. |
| Deploy | Preventing insecure configurations | Policy-as-code validation, least-privilege cloud permissions, and Kubernetes cluster hardening. |
| Run (Production) | Continuous runtime monitoring | Detecting configuration drift, identity misuse, runtime threats, and integrating with SIEM/XDR solutions. |


[1] [https://www.redhat.com](https://www.redhat.com/en/topics/devops/what-is-devsecops)
[2] [https://www.examlabs.com](https://www.examlabs.com/certification/achieving-success-with-microsoft-sc-100-certification-a-comprehensive-guide/)
[3] [https://www.microsoft.com](https://www.microsoft.com/en-gb/security/business/security-101/what-is-devsecops)
[4] [https://www.examcollection.com](https://www.examcollection.com/blog/mastering-sc-100-from-strategy-to-certification-in-cybersecurity-architecture/)

---

# CAF Security teams, roles, and functions 

[CAF Security teams, roles, and functions](https://aka.ms/securityroles)  

Here is a overview of the security roles and functions from the Microsoft Cloud Adoption Framework (CAF), structured specifically for the **SC-100: Microsoft Cybersecurity Architect** exam context.

| Security Role / Function | SC-100 Exam Description |
| --- | --- |
| **Policy and standards** | Establishes the organizational security rules, guidelines, and guardrails aligned with business objectives and risk tolerance. Translates compliance requirements into enforceable cloud governance policies. |
| **Security operations** | Monitors systems continuously, detects anomalies, and responds to active operational threats. Focuses on real-time triage using tools like SIEM (Microsoft Sentinel) and XDR (Microsoft Defender). |
| **Security architecture** | Translates overall security strategy and business risk into technical designs, reference architectures, and security controls across hybrid and multi-cloud environments using Zero Trust principles. |
| **Security compliance management** | Ensures the organization continuously satisfies regulatory, industry, and internal compliance mandates. Oversees audit readiness, risk reporting, and policy enforcement tracking. |
| **People security** | Manages human-centric risks through security awareness training, phishing simulations, insider threat mitigation, and establishing a strong security culture across the workforce. |
| **Application security and DevSecOps** | Integrates security tools and guardrails directly into modern software development lifecycles (SDLC) and CI/CD pipelines (shift-left security), focusing on code scanning, API security, and container safety. |
| **Data security** | Focuses on protecting sensitive data throughout its lifecycle (at rest, in transit, and in use). Involves data classification, encryption key management, and data loss prevention (DLP) controls. |
| **Infrastructure and endpoint security** | Secures foundational compute, network, container, and physical or virtual devices (endpoints). Applies hardened baselines, patch management, network segmentation, and EDR controls. |
| **Identity and key management** | Manages the primary security perimeter: authentication, authorization, privileged access management (PIM/PAM), Conditional Access, identity life cycles, and cryptographic keys/certificates. |
| **Threat intelligence** | Collects, analyzes, and applies contextual threat data regarding active adversary tactics, techniques, and procedures (TTPs) to proactively strengthen defenses and inform threat hunting. |
| **Posture management** | Continuously measures, evaluates, and improves overall security hygiene across cloud assets (e.g., via Microsoft Defender for Cloud / CSPM) by identifying misconfigurations and prioritizing vulnerability remediation. |
| **Incident preparation** | Focuses on readiness before an attack occurs—developing incident response (IR) plans, business continuity/disaster recovery (BCDR) strategies, table-top exercises, and automated response playbooks. |
---

# Episode 5

[Zero Trust | SC-100 | Episode 5 Microsoft Learn](https://www.youtube.com/watch?v=Fpgo7k91tkQ)   

[Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/)  
[Zero Trust Guidance Center](https://aka.ms/ztguide/)  
[Zero Trust Guidance Center](https://aka.ms/zerotrust/)  

- What is ZT?
    - security must not depend of implicit factors, such as network boundaries, rather on dynamic and explicit factors, such as identiy verification

- Why we need ZT?
    - to anable a busienss to operate securely and without interruptions
    - reduce the risks, i.e. of unauthorized access or data leakage, etc.

- What are the ZT principles?

    1. Assume breach: 
        - apply continuos monitoring and automatic anomalies detection, 
        - control traffic through NSGs,
        - use layers fo compartmentalization and segmentation to reduce the blast radius
    2. Verify explicitly: for example, use Conditional Access, etc.
    3. Use least-privilege access: for example, use PIM or JIT VM access with Defender for cloud. etc.

- What are the ZT (technology) pillars?

    1. Identity
    2. Endpoints
    3. Data
    4. Apps
    5. Infrastructure
    6. Network
    7. *(Visibility, Automation and Orchestration to oversee the other pillars)

# Identity Zero Trust deployment objectives

> Objectives:

## Initial deployment objectives [Primary Objectives]:

- Federate cloud identities with on-premises identity systems.
- Gate access and provide remediation with Conditional Access policies.
- Improve visibility through analytics.

## Additional deployment objectives [Secondary Objectives]:

- Manage identities and access privileges with Identity Governance.
- Analyze user, device, location, and behavior in real time to determine risk and deliver ongoing protection.
- Integrate threat signals from other security solutions to improve detection, protection, and response.

---

# Episode 4

[Use Cases | SC-100 | Episode 4 Microsoft Learn](https://www.youtube.com/watch?v=0O-CbEkZ9TY)   

- Description of the problem or goal
- Context and stakeholders involved
- The list of assumptions and contraints that affect the solution
- The set of requirements and criteria that the solution must meet
- A propose solution that reaches the goal or solve the problem and how it meets requirements and criteria
- A diagram or sketch that illustrates the solution and its components
- A discussion of strngth and weaknesses of teh solutio, and a discussion over the possible improvements

Below you find an example of interactive

[Exams Exam SC-100: Microsoft Cybersecurity Architect](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-100/)
>
[Design security operations, identity, and compliance capabilities](https://learn.microsoft.com/en-us/training/paths/sc-100-design-operations-identity-compliance-capabilities/)  
>
[Interactive case study: Modernizing identity and data security](https://learn.microsoft.com/en-us/training/modules/case-study-identity-data-security/)   
[Interactive case study: Modernizing user access control and threat resilience](https://learn.microsoft.com/en-us/training/modules/case-study-access-control-threat-resilience/)  

## SC-100 Use Cases

https://Aka.ms/sc100casex (replace x with number)

[Interactive case study: Modernizing identity and data security](aka.ms/sc100case1)  
[Interactive case study: Modernizing user access control and threat resilience](aka.ms/sc100case2)   
[Interactive case study: Securing apps and data](aka.ms/sc100case3)   
[Interactive case study: Securing endpoints and infrastructure](aka.ms/sc100case4)   

---

# Episode 3
[Security Posture Assessments | SC-100 | Episode 3 Microsoft Learn](https://www.youtube.com/watch?v=Nc-2gsBPl3Q&list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_&index=4)  

Use assesments to adopt, gradually improve and track the business security posture, over time.

1. run a general assesment 
[Welcome to Microsoft Assessments](https://learn.microsoft.com/en-my/assessments/)

    - who are the stateholders
    - who owns what
    - what are the assets. i.e. tenants, identities, apps
    - what are the risks for each party and for the business
    - are there previous security incidents?
    - what is the expected ROI in each case, what was in the case of previos incidents if any?

In this section the tutor highlights the following assesments:

##  Microsoft Defender

[Microsoft Defender for Identity's security posture assessments](https://learn.microsoft.com/en-us/defender-for-identity/security-assessment)  
[Microsoft Defender Vulnerability Management Security baselines assessment](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-baselines)  

## Microsoft Defender for Cloud
Hybrid and Multi-Cloud Deployments

[Manage security posture by using Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/training/modules/microsoft-defender-cloud-security-posture/)  
[Microsoft Defender for Cloud Regulatory Compliance](https://learn.microsoft.com/en-us/connectors/ascregulatorycomplianceassessment/)  
[Plan for cloud workload protections using Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/training/modules/what-is-azure-defender/)   

## Compliance Managment Assesments

[Microsoft Purview: Build and manage assessments in Compliance Manager](https://learn.microsoft.com/en-us/purview/compliance-manager-assessments)  

---

# Microsoft Assessments

The assesment are arranged in the following groups

- Define
- Plan
- Prepare
- Adopt
- Govern
- Manage

The purpose of each assesment is to **probe and also educate**.
You get the most out of it if the assement is carried out together as a team effort.
Each assessment produces an actionable score and actionable items to improve the score.

---

## Microsoft Assessments Cloud Adoption Security Assessment (CASA)

[Microsoft Assessments Cloud Adoption Security Assessment (CASA)](https://learn.microsoft.com/en-us/assessments/31e5d42d-49b2-4892-b7c7-78689f3518f5/)
[Azure Architecture Blog: What is a Cloud Adoption Security Review?](https://techcommunity.microsoft.com/blog/azurearchitectureblog/what-is-a-cloud-adoption-security-review/3806510)  

The assessment evaluates the organization's cloud security maturity across key domains, 
including security teams and roles, security posture modernization, incident preparedness 
and response, confidentiality, integrity, availability, and security sustainment. 
Each question is designed to assess the implementation of best practices aligned with 
the Azure Cloud Adoption Framework (CAF) Secure Methodology, emphasizing scalable and secure 
cloud environments.

---

## Microsoft Assessments Cloud Adoption Security Review

[Microsoft Assessments Cloud Adoption Security Review](https://learn.microsoft.com/en-us/assessments/93dfb79b-71af-404d-897e-3928ecfb92b1/)

Assess your Security Journey for Cloud Adoption. 
Receive actionable considerations to improve your security posture.

---

[Microsoft Assessments Azure Well-Architected Review](https://learn.microsoft.com/en-my/assessments/azure-architecture-review/)  
[Microsoft Assessments Mission Critical | Well-Architected Review](https://learn.microsoft.com/en-my/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/)  
[Microsoft Assessments Cloud Adoption Strategy Evaluator](https://learn.microsoft.com/en-my/assessments/8fefc6d5-97ac-42b3-8e97-d82701e55bab/)  
[Microsoft Assessments Cloud Journey Tracker](https://learn.microsoft.com/en-my/assessments/cloud-journey-tracker/)
[Microsoft Assessments DevOps Capability Assessment](https://learn.microsoft.com/en-my/assessments/56ec577c-acb6-4c7b-ad13-e224b0846153/)  
[Microsoft Assessments Azure Landing Zone Review](https://learn.microsoft.com/en-my/assessments/21765fea-dfe6-4bc4-8bb7-db9df5a6f6c0/)   
[Microsoft Assessments Cloud Adoption Security Assessment (CASA)](https://learn.microsoft.com/en-my/assessments/31e5d42d-49b2-4892-b7c7-78689f3518f5/)  
[Microsoft Assessments Cloud Governance](https://learn.microsoft.com/en-my/assessments/b1891add-7646-4d60-a875-32a4ab26327e/)  

[Microsoft Assessments Identity Compete | Microsoft Partner](https://learn.microsoft.com/en-my/assessments/dd10e711-c31d-46bf-aa4e-e14085f6a1ab/)  
[Microsoft Assessments Information Protection and Governance | Microsoft Partner](https://learn.microsoft.com/en-my/assessments/8399c474-6fa0-4005-978a-20088633f8f6/)  
[Microsoft Assessments Microsoft Cybersecurity Architect Learner Journey](https://learn.microsoft.com/en-my/assessments/91e16bc4-490a-4eaa-8af9-3e7510a6b146/)  
[Microsoft Assessments Unpacking Defender | Microsoft Partners](https://learn.microsoft.com/en-my/assessments/ec2529d7-ff05-426e-a0ab-9fa9c2999bf9/)  

All assesment go through the following stages:

1. Start: Choose an assessment that aligns with the business strategies you'd like to evaluate  
2. About you: Provide answers to fundamental questions, which in return will narrow your content options  
3. Get a score: Receive curated and personalized guidance that fits your specific scenarios  
4. Take action: Review recommendations at your convenience to improve your score  
5. Recheck score: Save your assessment progress through signing in and creating a milestone.  
6. Improve: Creating milestones will allow you to gradually improve your score and see your progress in real-time  

---

## Popular Microsoft Assessments

[Microsoft Assessments Browse all](https://learn.microsoft.com/en-my/assessments/browse/?searchterm=&page=1&pagesize=30)

[Microsoft Assessments Azure Machine Learning](https://learn.microsoft.com/en-my/assessments/eec33ce4-4ef0-4bd2-9f69-1956e50465d4/)   
[Microsoft Assessments AI Engineer Skill Assessment](https://learn.microsoft.com/en-my/assessments/33a8d18b-7299-4808-95eb-ec1ac1eca4d9/)  
[Microsoft Assessments AI Readiness Assessment](https://learn.microsoft.com/en-my/assessments/94f1c697-9ba7-4d47-ad83-7c6bd94b1505/)  
[Microsoft Assessments Technical Assessment for Generative AI in Azure](https://learn.microsoft.com/en-my/assessments/443670b4-11d1-4dd7-8128-b2bdb7a2bf2f/)  


---

## Skills

[Microsoft Assessments Security Engineer Skill Assessment](https://learn.microsoft.com/en-my/assessments/68bdf530-4418-42bb-867d-c631ea1986e1/)  

---

## Popular Microsoft Assessments of Interest  

[Microsoft Assessments Power Platform Adoption Assessment](https://learn.microsoft.com/en-my/assessments/3c62fd23-9d36-491c-8941-26d5553365f8/)   
[Microsoft Assessments Power Platform Well-Architected](https://learn.microsoft.com/en-my/assessments/689fd8d9-1000-4cbb-8096-a6c8f3294fc7/)  
[Microsoft Assessments Power Platform Solution Assessment](https://learn.microsoft.com/en-my/assessments/a5c3b65d-bf7e-4743-850a-0437ae692690/)  

[Microsoft Assessments Sustainability | Well-Architected Review](https://learn.microsoft.com/en-my/assessments/f236012a-0070-45db-b94c-fe8de0799f38/)  

[Microsoft Cloud for Healthcare Learner Self-Assessment (Preview)](https://learn.microsoft.com/en-my/assessments/a597e375-3ebd-4dc7-8dd9-6d8f75a7ca70/)  
[Microsoft Assessments Healthcare Industry | Microsoft Partners](https://learn.microsoft.com/en-my/assessments/6068ed96-65c1-42b5-b870-15d51a379dbf/)  

[Microsoft Assessments SAP on Azure | Well-Architected Review](https://learn.microsoft.com/en-my/assessments/b45998e4-8e92-41b1-a0bd-ab07e665db64/)  

---

# Episode 1
[Cybersecurity Architect | SC-100 | Episode 2 Microsoft Learn](https://www.youtube.com/watch?v=S1NuiEuQuBQ&list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_&index=3)   

# Episode 2
[Cybersecurity Architect | SC-100 | Episode 2 Microsoft Learn](https://www.youtube.com/watch?v=S1NuiEuQuBQ&list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_&index=4)

---

[Course Intro | SC-100 | Episode 1 Microsoft Learn](https://www.youtube.com/watch?v=3hLAnuadexg&list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_&index=3)  

# What is MCSB in the context of the SC-100 Security Architect Exam?

MCSB stands for the [Microsoft Cloud Security Benchmark](https://learn.microsoft.com/en-us/security/benchmark/azure/), 
a foundational set of **prescriptive security best practices**, compliance guidelines, and control baselines used
to secure cloud and hybrid workloads. [1, 2] 

In the context of the SC-100 (Microsoft Cybersecurity Architect) Exam, MCSB is a core framework that you are expected 
to master for designing and evaluating security posture management. [3, 4] 

## Key Aspects of MCSB for the SC-100 Exam

* Control Baseline: It provides a unified, measurable standard for security configurations across cloud resources, 
moving beyond isolated settings into structured control families. [5, 6] 

* Multi-Cloud Scope: Although formerly known as the Azure Security Benchmark, it applies broadly across Azure and multi-cloud environments (such as AWS and GCP). [4] 

* Regulatory Mapping: MCSB maps directly to established industry standards like 
    - Center for Internet Security (CIS) Controls, 
    - National Institute of Standards and Technology (NIST), 
    - Payment Card Industry Data Security Standard (PCI-DSS). [2, 4] 

* Microsoft Defender for Cloud Integration: It serves as the underlying evaluation engine for the Regulatory Compliance dashboard and directly influences an organization's Secure Score. [2, 4] 

## Core Control Domains Covered

The benchmark is structured around critical operational domains that frequently appear in SC-100 scenario-based questions: [4, 7] 

* Identity Management and Privileged Access
* Network Security and Data Protection
* Logging, Threat Detection, and Incident Response
* Posture and Vulnerability Management
* DevOps and Emerging AI Security Controls [7, 8, 9] 

On the exam, you will be tested on how to recommend and evaluate architectural designs 
that align workloads and governance models directly with MCSB requirements. [3, 4] 

[1] [https://examos.io](https://examos.io/study-plans/microsoft-certified-cybersecurity-architect-expert-sc-100?from=hub)
[2] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/security/benchmark/azure/introduction)
[3] [https://intunedin.net](https://intunedin.net/2026/06/01/sc-100-microsoft-cybersecurity-architect-exam-resource-guide-april-2026-update/)
[4] [https://www.youtube.com](https://www.youtube.com/watch?v=zNS-ldHMueI&t=4)
[5] [https://www.youtube.com](https://www.youtube.com/watch?v=Z7RZ-H1WzHs&t=66)
[6] [https://www.linkedin.com](https://www.linkedin.com/posts/vimal-singh1984_microsoft-cloud-security-benchmark-explained-activity-7332664143486885888-9vy3)
[7] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/security/benchmark/azure/)
[8] [https://www.linkedin.com](https://www.linkedin.com/pulse/sc-100-microsoft-cybersecurity-architect-masud-rana-fvpoc)
[9] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/)

---

# What are the 3 principles of Zero Trust in the context of the SC-100 Security Architect Exam?

1. Assume Breach (Assume Compromise)
2. Verify Explicitly
3. Use least-privilege access

---

# What are the 7 pillars of Zero Trust in the context of the SC-100 Security Architect Exam?

The seven technology pillars of Zero Trust tested on the [SC-100 Microsoft Cybersecurity Architect Exam](https://learn.microsoft.com/en-us/security/zero-trust/deploy/overview) are Identities, Endpoints, Data, Apps, Infrastructure, Network, and SecOps. [1, 2] 
These pillars serve as technical boundaries for enforcing the core Zero Trust principle: never trust, always verify. [1, 2] 

## 1. Identities

* Focus: Authenticates and authorizes every user, service, and smart device.
* Key controls: Multi-Factor Authentication (MFA), Conditional Access, and least-privilege access.
* Role: Acts as the primary control plane for modern security. [3, 4] 

## 2. Endpoints

* Focus: Evaluates device health and compliance before allowing access to corporate data.
* Key controls: Mobile Device Management (MDM), device posture checks, and endpoint detection software.
* Role: Ensures personal and corporate devices meet security standards. [2, 5, 6] 

## 3. Data

* Focus: Protects sensitive information wherever it travels or rests.
* Key controls: Data discovery, automated classification, labeling, and encryption.
* Role: Prevents data leaks and unauthorized viewing. [2, 6, 7] 

## 4. Apps

* Focus: Secures applications and Application Programming Interfaces (APIs) against incoming threats.
* Key controls: Application-layer controls, secure session management, and discovery of unauthorized apps.
* Role: Enforces security inside the application development and runtime layers. [2, 7, 8] 

## 5. Infrastructure

* Focus: Protects workloads and computing platforms across hybrid and multi-cloud setups.
* Key controls: Hardening servers, virtual machines, and containers.
* Role: Reduces the risk of system compromises at the host level. [2, 8] 

## 6. Network

* Focus: Controls connectivity and blocks attackers from moving sideways across the network.
* Key controls: Micro-segmentation, firewalls, and traffic monitoring.
* Role: Turns flat networks into isolated, secure zones. [2, 6, 8] 

## 7. SecOps (Security Operations)

* Focus: Collects environment signals to detect, investigate, and stop attacks quickly.
* Key controls: Centralized logging, Security Information and Event Management (SIEM), and automated responses.
* Role: Powers real-time visibility and threat analytics across all other pillars. [2, 5, 6, 9] 


[1] [https://www.youtube.com](https://www.youtube.com/watch?v=eCxCLK-TNpk)
[2] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/security/zero-trust/deploy/overview)
[3] [https://www.linkedin.com](https://www.linkedin.com/pulse/sc-100-microsoft-cybersecurity-architect-masud-rana-fvpoc)
[4] [https://certgrid.app](https://certgrid.app/study-guide/sc-100-microsoft-cybersecurity-architect)
[5] [https://netwrix.com](https://netwrix.com/en/resources/guides/7-pillars-of-zero-trust/)
[6] [https://www.trevonix.com](https://www.trevonix.com/blogs/7-pillars-of-zero-trust)
[7] [https://www.scribd.com](https://www.scribd.com/document/870648874/SC-100-Microsoft-Cybersecurity-Architect-1746437404)
[8] [https://www.linkedin.com](https://www.linkedin.com/pulse/zero-trust-foundations-three-principles-seven-pillars-stuart-mann-y9nhe)
[9] [https://nordlayer.com](https://nordlayer.com/learn/zero-trust/pillars/)


---

# Job Statement

As a Microsoft cybersecurity architect, you translate a cybersecurity strategy into capabilities that protect the assets, business, and operations of an organization. 

You design, guide the implementation of, and maintain security solutions that follow 
Zero Trust principles and best practices, including security strategies for identity, devices, data, Al, applications, network, infrastructure, and DevOps. 

Plus, you design solutions for Governance and Risk Compliance (GRC), security operations, and security posture management.

As a cybersecurity architect, you continuously collaborate with leaders and practitioners in security, privacy, engineering, and other roles across an organization to plan and implement a cybersecurity strategy that meets the business needs of an organization.

---

# SC-100 attantion areas

1. Security best practices and priorities
2. Security operations, identity, and compliance
3. Solutions for infrastructure
4. Solutions for applications and data

---

# What is MCRA in relation to the SC-100 Security Architect Exam?

MCRA stands for the [Microsoft Cybersecurity Reference Architectures](https://learn.microsoft.com/en-us/security/adoption/mcra), a comprehensive, continuously updated collection of technical reference diagrams and PowerPoint slides that illustrate how Microsoft and third-party security capabilities integrate using [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/microsoft-reference-architecture) principles. [1, 2] 
In relation to the SC-100 Microsoft Cybersecurity Architect exam, the MCRA is a core conceptual framework tested through scenario-based design questions rather than direct definitions. [3, 4] 
------------------------------
## Key Functions of MCRA in SC-100

* Target-State Blueprint: Provides visual reference models for securing hybrid environments, multi-cloud platforms (AWS, GCP), IoT/OT, and AI estates. [1, 2, 5] 
* Integration Map: Demonstrates how native security operations tools (like Microsoft Sentinel, Defender XDR, and Entra ID) interlock to cover identity, threat protection, and governance. [6, 7] 
* Gap Analysis Tool: Used by architects to compare an organization's existing security capabilities against Microsoft's recommended architecture to identify overlaps or missing coverage. [4, 5, 8] 

## Exam Context vs. Other Frameworks

* MCRA vs. MCSB: MCRA is conceptual guidance showing how capabilities fit together, whereas the Microsoft Cloud Security Benchmark (MCSB) is a prescriptive, scored technical baseline used to evaluate actual configurations. [9] 
* Exam Application: Expect questions requiring you to interpret architectural states, recognize anti-patterns (poor security designs), and align enterprise priorities with Microsoft's recommended technology integrations. [4] 


[1] [https://www.youtube.com](https://www.youtube.com/watch?v=8-ZSgTpryLA&t=22)
[2] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/security/adoption/mcra)
[3] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/training/paths/sc-100-design-solutions-best-practices-priorities/)
[4] [https://spot.eventx.io](https://spot.eventx.io/events/b3667c50-00ac-47cd-9761-6a9e4424a8d9?regForm=436a1561-8f4f-4828-9a2b-cff97d00a4f6&auto_show_reg_form=true)
[5] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/security/zero-trust/microsoft-reference-architecture)
[6] [https://www.linkedin.com](https://www.linkedin.com/pulse/sc-100-microsoft-cybersecurity-architect-masud-rana-fvpoc)
[7] [https://www.youtube.com](https://www.youtube.com/watch?v=6iYxNm3TOiI&t=3)
[8] [https://www.youtube.com](https://www.youtube.com/watch?v=hRs6VDinIJE&t=702)
[9] [https://mscertquiz.com](https://mscertquiz.com/blog/sc-100-study-guide)

---

# What are the prerequisite for the Microsoft Cybersecurity Architect Certification in 2026?

To earn the Microsoft Certified: Cybersecurity Architect Expert certification, 
you must pass exam SC-100 and earn at least one prerequisite associate-level certification. [1, 2] 
## Required Exam

* Exam SC-100: Microsoft Cybersecurity Architect (Passing score: 700, Price: $165 USD) [3] 

## Prerequisite Certifications (Earn at least one)
You must hold or earn one of the following associate-level credentials before your expert certification is granted:

* Microsoft Certified: Identity and Access Administrator Associate (Exam SC-300)
* Microsoft Certified: Security Operations Analyst Associate (Exam SC-200)
* Microsoft Certified: Azure Security Engineer Associate (Exam AZ-500)
* Microsoft Certified: Cloud and AI Security Engineer Associate [1, 4, 5, 6, 7] 

## Recommended Experience

* Practical, hands-on experience in identity and access management, platform protection, security operations, data/AI security, application security, and hybrid or multi-cloud infrastructures.
* Expert-level skills in at least one of these security domains and experience designing solutions using Microsoft security technologies. [3, 8] 


[1] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/cybersecurity-architect-expert/)
[2] [https://techcommunity.microsoft.com](https://techcommunity.microsoft.com/blog/skills-hub-blog/announcing-the-new-certification-for-cybersecurity-architects/3545160)
[3] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-100/)
[4] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/5807443/microsoft-certified-cybersecurity-architect-expert)
[5] [https://firebrand.training](https://firebrand.training/uk/courses/microsoft/microsoft-security-certifications/certified-cybersecurity-architect-expert-certification)
[6] [https://learn.microsoft.com](https://learn.microsoft.com/it-it/credentials/certifications/cybersecurity-architect-expert/)
[7] [https://www.globalknowledge.com](https://www.globalknowledge.com/us-en/training/certification-prep/brands/microsoft/section/security/microsoft-certified-cybersecurity-architect-expert/)
[8] [https://firebrand.training](https://firebrand.training/en-ch/courses/microsoft/microsoft-security-certifications/cybersecurity-architect-certification)

---

# Exam AZ-500 is retired, does it still count as a prerequisite?

Yes, an active AZ-500 certification still counts as a prerequisite, but only until your specific credential officially expires. [1] 
Because Microsoft retired Exam AZ-500 and the Azure Security Engineer Associate certification on August 31, 2026, the rules 
regarding how it impacts your Cybersecurity Architect status depend on your current certification status: [2, 3] 

## If You Already Hold the AZ-500 Certification

* 
* It remains valid as a prerequisite: If you passed the AZ-500 exam prior to its retirement, the certification remains on your transcript and stays "Active" for exactly one year from the date you earned it. [1, 4] 

* It unlocks the Expert badge: As long as your AZ-500 status is active, passing the SC-100 exam will successfully unlock your Microsoft Certified: Cybersecurity Architect Expert credential. [5] 

* The catch: Once your AZ-500 certification reaches its expiration date, it can no longer be renewed. It will move to the "Historical Certifications" section of your transcript. [1, 3, 4] 
* 

## If You Do Not Have the AZ-500 Certification Yet

* 
* You cannot take it: The AZ-500 exam is fully discontinued and no longer bookable.
* The alternative paths: To fulfill the prerequisite for the SC-100 Expert track, you must achieve one of the other active associate-level certifications, such as SC-200 (Security Operations Analyst) or SC-300 (Identity and Access Administrator).
* The SC-500 transition: Microsoft launched SC-500 (Cloud and AI Security Engineer Associate) as the official successor to AZ-500. [2, 4, 5, 6] 
* 

Are you planning to sit for the SC-100 exam soon while your AZ-500 is still active, or are you looking into the newer SC-200/SC-300 paths instead?

[1] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/5852001/question-about-retiring-microsoft-certifications)
[2] [https://trainingcamp.com](https://trainingcamp.com/articles/az-500-retires-august-31-2026-sc-500-replaces-it-2/)
[3] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/credentials/support/retired-certification-exams)
[4] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/5994404/i-need-to-renew-my-az-500-however-it-is-showing-as)
[5] [https://learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/5979471/will-sc-500-satisfy-the-prerequisite-for-sc-100-st)
[6] [https://www.youtube.com](https://www.youtube.com/watch?v=J4DJo6VrtVo)  

---

# What is the difference between SIEM and SOAR in the context of of the SC-100 Security Architect Exam?

In the context of the **Microsoft SC-100: Cybersecurity Architect** exam: 

- **SIEM (Security Information and Event Management) focuses on visibility and detection**, while 
- **SOAR (Security Orchestration, Automation, and Response) focuses on efficiency and remediation**. 

In the Microsoft ecosystem, these capabilities are deeply integrated into **Microsoft Sentinel**, 
where SIEM acts as the central brain aggregating data, and SOAR acts as the automation engine responding 
to threats.

### Core Differences

| Feature | **SIEM (Security Information and Event Management)** | **SOAR (Security Orchestration, Automation, and Response)** |
| :--- | :--- | :--- |
| **Primary Goal** | **Data aggregation, analysis, and threat detection** | **Incident response orchestration and automation** |
| **Core Function** | Collects logs and telemetry from across the enterprise, correlates events, and triggers alerts when anomalies are found. | Standardizes incident response workflows, integrates disparate security tools, and automates repetitive tasks. |
| **Microsoft Sentinel Component** | Data Connectors, Analytics Rules, Watchlists, and Log Analytics Workspaces. | Automation Rules and **Playbooks** (powered by Azure Logic Apps). |
| **Analyst Impact** | Tells the analyst *what* happened and *where* by compiling the security data. | Tells the system *how* to react automatically to reduce Mean Time to Respond (MTTR). |

### Architectural Roles in the SC-100 Exam

As a Cybersecurity Architect, you must understand how to design solutions using both capabilities to minimize human intervention:

*   **The SIEM Layer (Detection):** You design data ingestion strategies to pull logs from Azure, multi-cloud environments (AWS, GCP), and on-premises systems. You write Analytics Rules (KQL queries) to detect sophisticated, multi-stage attacks across these platforms.
*   **The SOAR Layer (Response):** You design automated responses to those detections. For example, if the SIEM detects a brute-force attack from a malicious IP address, the SOAR playbook can automatically block that IP at the firewall, disable the targeted user account in Entra ID, and open a ticket in ServiceNow without requiring an analyst to lift a finger.

---

# What are Landing Zones in the context of the SC-100 Security Architect Exam?

[CAF What is an Azure landing zone?](https://aka.ms/caflz)  

In the context of the Microsoft SC-100: Cybersecurity Architect exam, 
an Azure Landing Zone is a multi-subscription deployment that serves as the strategic blueprint for a secure, scalable cloud environment. 
It ensures that when workloads are deployed, they automatically inherit the organization's security, governance, networking, and identity controls.

For a Security Architect, a Landing Zone represents the implementation of the Microsoft Cloud Adoption Framework (CAF) 
and the practical enforcement of Zero Trust architecture at scale.

An Azure Landing Zone is the output of a multisubscription Azure environment that accounts for scale, security governance, networking, and identity.
Enables application migration, modernization, and innovation at enterprise-scale in Azure.
Is an environment for hosting your workloads, preprovisioned through code.

## The Architect's Dilemma: Enterprise-Scale Landing Zones (ESLZ)
The SC-100 exam heavily evaluates your ability to design an Enterprise-Scale Landing Zone, 
which divides the cloud environment into two major structural components:

                  ┌─────────────────────────────────────┐
                  │          Tenant Root Group          │
                  └──────────────────┬──────────────────┘
                                     │
                  ┌──────────────────┴──────────────────┐
                  │       Contoso Management Group      │
                  └──────┬───────────────────────┬──────┘
                         │                       │
      ┌──────────────────┴────────────────┐ ┌────┴─────────────────────────────┐
      │         Platform Management       │ │         Workload Management      │
      └──────┬───────────┬───────────┬────┘ └──────┬────────────────────┬──────┘
             │           │           │             │                    │
        ┌────┴───┐  ┌────┴───┐  ┌────┴────┐  ┌─────┴──────┐       ┌─────┴──────┐
        │ Identity│  │Management││ Connectivity│ │Corp Workloads│     │Online Wrklds│
        └────────┘  └────────┘  └─────────┘  └────────────┘       └────────────┘

## 1. Platform Landing Zones
These provide shared, centralized capabilities across the entire enterprise. 

As an architect, you secure these core areas:

* Identity: Dedicated subscription for centralized identity management, securing domain controllers or Microsoft Entra ID hybrid connectors.
* Management: Centralized logging via Log Analytics Workspaces, enabling SIEM (Microsoft Sentinel) auditing across the entire footprint.
* Connectivity: The network core, typically designed using a Hub-Spoke architecture or Azure Virtual WAN. It houses Azure Firewalls, ExpressRoute/VPN gateways, and Azure DDoS Protection.
 

## 2. Application/Workload Landing Zones
These are decoupled subscriptions where specific business applications or workloads live.

* They inherit policies from the higher-level management groups.
* They communicate through the platform's Connectivity hub to reach on-premises networks or the internet safely.

------------------------------
## Core Security Design Pillars for SC-100
When designing or evaluating Landing Zones on the exam, you must focus on four security control areas:

| Security Pillar | Key Architectural Requirement for SC-100 |
|---|---|
| Governance & Policy | Use Azure Policy and Management Groups to enforce guardrails globally (e.g., preventing public IP creation, enforcing encryption at rest, restricting deployment regions). |
| Network Security | Implement a Hub-and-Spoke topology with isolated virtual networks (VNets). Force all traffic through the hub firewall using User Defined Routes (UDRs) and leverage Azure Bastion for secure management. |
| Identity & Access | Apply the Principle of Least Privilege using Azure RBAC and Microsoft Entra Privileged Identity Management (PIM). Keep operational roles separated between Platform Admins and Workload Owners. |
| Security Operations | Ensure all subscriptions automatically stream diagnostics data and security logs to the central Microsoft Sentinel workspace via Azure Policy definitions. |

## SC-100 Exam Tip: "Subscription Democratic" Model
The SC-100 exam favors an architectural design where subscriptions are used as units of management and scale, rather than trying to cram multiple applications into a single large subscription using complex RBAC rules. A proper Landing Zone architecture automates subscription creation so that new business applications get a clean, isolated environment that is secure by default from day one.
If you would like, I can provide the markdown code for this Landing Zones breakdown so you can paste it into your study notes, or we can look at a sample scenario question on how this is tested. Which would you prefer?

---

## Azure landing zone types

1. Platform landing zones: 

Subscriptions deployed to provide centralized services, often operated by one or several central teams split by function, for example, 
networking, identity, which will be used by various workloads and applications.

2. Application landing zones: One or more subscriptions deployed as an environment for an application or workload.

---