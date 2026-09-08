
[SC-100: Microsoft Cybersecurity Architect Microsoft Learn Course 27 videos Last updated on 6 Feb 2026](https://www.youtube.com/playlist?list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_)  

[Cloud Adoption Framework for Microsoft](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/)   
[Azure Architecture Center](https://learn.microsoft.com/en-us/azure/architecture/)    
[Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)  

> With aka.ms/XXX
[Microsoft cloud security benchmark documentation (MCSB)](https://aka.ms/mcsb)
[Cloud Adoption Framework for Microsoft](https://aka.ms/caf)
[Azure Well-Architected Framework](https://aka.ms/waf)


---

[Cybersecurity Architect | SC-100 | Episode 2 Microsoft Learn](https://www.youtube.com/watch?v=S1NuiEuQuBQ&list=PLahhVEj9XNTfRZMathQ5fn1akTwV7R3w_&index=3)   

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