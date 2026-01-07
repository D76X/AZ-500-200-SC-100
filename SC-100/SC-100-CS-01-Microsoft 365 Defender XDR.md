#  [Microsoft 365 Defender \= XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

It is a suite of **highly integrated security products**.

The main parts are the following:

1. [Microsoft 365 Defender for Endpoints](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint): [Overview Video](https://www.youtube.com/watch?v=YFPyTPDfZeY)   
2. [Microsoft 365 Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)  
3. [Microsoft 365 Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/what-is)  
4. [Microsoft 365 Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)

There are other products in the bundle:

5. [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)  
6. [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)  
7. [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)  
8. [Microsoft Data Loss Prevention](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp)  
9. [App Governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)  
10. [Microsoft Purview Insider Risk Management](https://learn.microsoft.com/en-us/purview/insider-risk-management-solution-overview)

---

## Microsoft Defender for Endpoint

[Microsoft Defender for Endpoint Overview Video](https://www.youtube.com/watch?v=YFPyTPDfZeY)

[**Microsoft Defender for Endpoint \- Microsoft Security \- Playlist**](https://www.youtube.com/playlist?list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW)   
[MDEP \- Discover (Unmanaged) Devices](https://www.youtube.com/watch?v=TCDxICrZQa8&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=32)   
[Assessing and Onboarding Unmanaged Devices | Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=Oc-ZwohbtLk&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=33) 

1. **Asset Discovery**: 

Discover devices on your network without agents or periodic scans using the information gather by other devices detected on the same network.

1. Assess the device using the information from the device, the type of data it detects, and the documented vulnerabilities.   
   2. It onboards the devices.

[Attack surface reduction in Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=AkzAafLjDfs&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=12)    
[Understand and use attack surface reduction capabilities \- Microsoft Learn](https://learn.microsoft.com/en-us/defender-endpoint/overview-attack-surface-reduction) 

[01\. Enable **hardware-based isolation for Microsoft Edge for PDF & websites**.](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/microsoft-defender-application-guard/install-md-app-guard) 

[02\. Windows **Defender Application Control \- trust none till they earn it\!**](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/use-device-guard-with-configuration-manager)  
[02\. Microsoft Defender Application Control \- Microsoft Security](https://www.youtube.com/watch?v=ko-PoDFANVY&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=10) 

[03\. **Controlled folder access: Untrusted apps cannot access protected folders NO encryption attacks**](https://learn.microsoft.com/en-us/defender-endpoint/enable-controlled-folders) 

[04\. **Network Protection (without a Web Proxy\!):** to help prevent connections from **ANY application (not just Edge)** to malicious or suspicious sites](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)   
[**Use network protection to help prevent connections to malicious or suspicious sites \- Microsoft Learn**](https://learn.microsoft.com/en-us/defender-endpoint/network-protection)   
[**Network protection in Microsoft Defender for Endpoint**](https://www.youtube.com/watch?v=ZmbFHp9Usbo&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=11) 

[05\. **Exploit Protection**](https://learn.microsoft.com/en-us/defender-endpoint/enable-exploit-protection)

[07\. **Device control** in Microsoft Defender for Endpoint: allow/block certain removable devices](https://learn.microsoft.com/en-us/defender-endpoint/device-control-overview)  

2. **Attack Surface Reduction:**  
   1. Attack surface reduction rules to restrict behaviours of apps, scripts and files.  
   2. Trusted application whitelist.  
   3. Network protection: joining a network is allowed only if its reputation is OK.

[Microsoft Defender Antivirus in Windows Overview](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) 

3. **Microsoft Defender Antivirus:**  
   It blocks malicious files or fileless threats using real-time devices, behaviour monitoring, and threat protection.   
   

[Live response in Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=88wNqR-doyw&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=15) 

[Investigate entities on devices using live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response)   
[Live response command examples](https://learn.microsoft.com/en-us/defender-endpoint/live-response-command-examples) 

4. **Endpoint detection and response:** It finds threats that want to stay hidden. A security analyst can access a compromised machine remotely through a remote shell to gather forensic information for an attack's security investigation.  
   

[Advanced hunting in Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=4W6GqD8pY4o&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=14) 

[Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)  
[Threat hunting in Threat Explorer and Real-time detections in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting)   
[Learn the advanced hunting query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language) 

5. **Threat Hunting Tools** for Security Teams with a **Sandbox** for saving the investigation of quarantined assets, with a custom query language designed to make it easy to investigate security aspects of Microsoft Defender Telemetry data. The [**Custom Detection Rules** feature of Advanced Hunting](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules]) allows you to run custom hunting queries **on a set schedule**.   
   

[Automated investigations in Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=j1rRq06sfII&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=17)   
[Overview of automated investigations](https://learn.microsoft.com/en-us/defender-endpoint/automated-investigations)   
[Automation levels in automated investigation and remediation capabilities](https://learn.microsoft.com/en-us/defender-endpoint/automation-levels) 

6. **Automation** for remediation after threat detection or alert can significantly reduce response time and volume

[Microsoft Threat Experts](https://www.youtube.com/watch?v=wHDwVWailyk&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=18)   
[Endpoint Attack Notifications](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-attack-notifications?view=o365-worldwide)   
[Microsoft Defender Experts for Hunting](https://learn.microsoft.com/en-us/defender-xdr/defender-experts-for-hunting)   
[Get started with Microsoft Defender Experts for XDR](https://learn.microsoft.com/en-us/defender-xdr/get-started-xdr)   
[Get started with onboarding | Microsoft Defender Experts for XDR](https://www.youtube.com/watch?v=eLEXPZ1mUwQ)   
[**Configure and manage threat protection by using Microsoft Defender for Cloud \-Microsoft Learn Module**](https://learn.microsoft.com/en-us/training/modules/microsoft-defender-cloud-threat-protection/) 

7. [Microsoft Threat Experts](https://www.microsoft.com/en-us/security/business/services/microsoft-defender-experts-hunting\\): access expertise on demand

[Collaborate with experts on demand \- **XDR**](https://learn.microsoft.com/en-us/defender-xdr/experts-on-demand)   
[Start using Microsoft Defender Experts for Hunting \- **XDR**](https://learn.microsoft.com/en-us/defender-xdr/onboarding-defender-experts-for-hunting)   
[Endpoint Attack Notifications](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-attack-notifications) 

8. [Microsoft Defender for Endpoints **API integration**](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

---

### Other Important Topics on Microsoft Defender for Endpoints

[**Microsoft Defender for Endpoint \- Microsoft Security \- Playlist**](https://www.youtube.com/playlist?list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW) 

---

Conditional Access Policies:

[Microsoft Entra ID **Conditional Access** **Policies** in Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=dQ2WmIqhezs&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=21) 

This feature is based on the possibility of integrating **MD4E with Intune.** This integration is bilateral, but each side must be activated separately; that is, first in **MD4E,** you activate integration with **Intune** and then in **Intune,** you activate the integration with **MD4E.**  

There are 3 steps to this process:

1. must enable **integration** between **MD4E and Intune in both products\!**  
     
2. Create an **Intune Compliance Policy** using **MDE4E Device Risk:** This policy will determine whether devices are marked as compliant or not compliant **by Intune**. The Intune Compliance Policy must be assigned to a group of devices after it is created to become active. **It is important** that you do not assign the ICP to Global Admins if you are not sure that **they may be Locked Out** by Intune should they not have devices that are non-compliant with the policy\!   
     
   It is also important to know that an **Intune Compliance Policy** does not prevent access; it merely marks the device as compliant or non-compliant. **To prevent access,** you must implement the next step\!  
     
3. Create an **MEID CAP** that requires devices to be marked compliant to gain access; you can design the **MEID CAP** the way you want. Remember that a CPA has two parts to it, **the first part is the Assignments,** where you define to whom the policy will be applied. The options here are **Users & Groups, Cloud Apps** and **Conditions**. The **second part** of the **MEID CAP** is the **Access Control,** in which it is decided whether the policy should **block access** or **grant access**. The options here are the following:   
     
   * Require MFA  
   * **Require the device to be compliant 	\<\< choose this one in this case\!**  
   * Require a Hybrid AD-joined device  
   * Require approved client app  
       
4. Enable and Create the MEID CAP

---

Mobile Threat Defence App for Android and iOS

[Mobile Threat Defence Deployment with Microsoft Security](https://www.youtube.com/watch?v=MO_6-Q4TDuI&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=36)  
[Microsoft Defender for Endpoint \- Mobile Threat](https://learn.microsoft.com/en-us/defender-endpoint/mtd) Defence 

---

RBAC in Microsoft Defender for Endpoints

[Role-based access control (RBAC) in Microsoft Defender for Endpoint \- Microsoft Security](https://www.youtube.com/watch?v=Qa39K6IvzMs&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=8)   
[**Create and manage roles for role-based access control \- MD4D**](https://learn.microsoft.com/en-us/defender-endpoint/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group)   
[Assign roles and permissions for Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment) 

---

Deep File Analysis 

[Deep file analysis | Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=_ayp8QStNXI)  
[Take response actions on a file](https://learn.microsoft.com/en-us/defender-endpoint/respond-file-alerts)   
[Deep analysis](https://learn.microsoft.com/en-us/defender-endpoint/respond-file-alerts#deep-analysis) 

---

Unified IoCs: Unified Indicators of Compromise (IoCs)

[Unified IoCs | Microsoft Defender for Endpoint](https://www.youtube.com/watch?v=Rwyca4LR308&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=2&t=1s)

Unified IoCs involve creating a central repository for IoCs and integrating it with various security tools and platforms. This can be achieved through APIs, security information and event management (SIEM) systems, or other security platforms. Security teams can then add, update, and manage IoCs within this central repository, and these changes will be reflected across all connected systems.

[Overview of indicators in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview) 

An Indicator of compromise (IoC) is a **forensic artefact observed on the network or host**. An IoC **indicates, with high confidence**, that a computer or **network intrusion has occurred**. 

IoCs are **observable**, which links them directly to measurable events. Some IoC examples include:

* hashes of known malware  
* Signatures of malicious network traffic  
* URLs or domains that are known to be malware distributors  
* Compromised Digital Certificate Signatures

---

Microsoft Defender for Endpoint APIs

[API integration in Microsoft Defender for Endpoint \- **Microsoft Security**](https://www.youtube.com/watch?v=Jb5u8n5Z6PM&list=PL3ZTgFEc7LysX3dP-2WrxCSjOfz2uymRW&index=19)   
[Access the Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)  
[Microsoft Defender for Endpoint APIs using PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-full-sample-powershell)  

---

## [Microsoft 365 Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)

[**Microsoft Defender for Office 365 \- Playlist \- Microsoft Security**](https://www.youtube.com/playlist?list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf)  
[**Microsoft Defender for Office 365 \- Collection**](https://learn.microsoft.com/en-us/collections/ewk6soty67ge4j) 

[How to Set Up Defender for Office 365: A Complete Guide \- Jonathan Edwards](https://www.youtube.com/watch?v=y7m-X8AGBlM)

This tutorial illustrates the process of creating Policies for Defender for Office 365:

* Standard Preset Security Policy  
* **Inbound** Company ASP (Anti Spam) Policy  
* **Outbound** Company ASP (Anti Spam) Policy  
* **Anti-malware** policy

[Microsoft Defender for Office 365 service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)  
[Exchange Online service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) 

[**EOP: Exchange Online Protection**](https://learn.microsoft.com/en-us/defender-office-365/eop-about)

[Migrating to Microsoft Defender for Office 365](https://www.youtube.com/watch?v=Izu8U1n54xw&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=21) 

It protects against threats in **email, links (URLs), file attachments, and collaboration tools**. 

[**Why do I need Microsoft Defender for Office 365?**](https://learn.microsoft.com/en-us/defender-office-365/mdo-about) 

Microsoft Defender for Office 365 is a seamless integration into Microsoft 365 subscriptions that protects against threats in email, links (URLs), file attachments, and collaboration tools. This article explains the protection ladder in Microsoft 365 organisations. The protection ladder starts with Exchange Online Protection (EOP) and continues through to Defender for Office 365, which includes Defender for Office 365 Plan 1 and Defender for Office 365 Plan 2\.

**All Microsoft 365 subscriptions include built-in security and protection features**.

1. **Exchange Online Protection (EOP):**   
   Included in any subscription that includes Exchange Online mailboxes. Also available as a standalone subscription to protect on-premises email environments.  
     
2. **Defender for Office 365 365 Plan 1:**   
   Included in some Microsoft 365 subscriptions with Exchange Online mailboxes that cater to small to **medium-sized businesses** (for example, Microsoft 365 Business Premium).  
     
3. **Defender for Office 365 365 Plan 2:**   
   Included in some Microsoft 365 subscriptions with Exchange Online mailboxes that cater to **enterprise organisations** (for example, Microsoft 365 E5, Microsoft 365 A5, and Microsoft 365 GCC G5).

---

## [Microsoft 365 Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/what-is) 

[Leveraging Microsoft Defender for Identity \- **John Savill**](https://www.youtube.com/watch?v=09zXZcNPLuU&t=43s)  
[Defender for Identity in the Microsoft 365 Defender Portal: Tips and Tricks \- Microsoft Security Community](https://www.youtube.com/watch?v=mlfd5TV5jFM)   
[Microsoft Defender for Identity webinar: Deployment and configuration \- Microsoft Security](https://www.youtube.com/watch?v=0FXut2osAfg)  
[Microsoft Defender for Identity | Become an Advisor to Our Product Engineering Team \- Microsoft Security Community](https://www.youtube.com/watch?v=sMZJTCtfK3Y)   

---

## [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)

[Get started with App governance \- Microsoft Defender for Cloud Apps \- Microsoft Security](https://www.youtube.com/watch?v=6GouFtEeSoY)  
[**Microsoft Defender for Cloud Apps \- US \- Microsoft Security Community \- Playlist**](https://www.youtube.com/watch?v=O69Td1BoY80&list=PLmAptfqzxVEWPdYnWAM9ZIr81jWESvPTN)    
[Defender for Cloud Apps \- Lock Down Your Cloud Apps & Protect Data \- **Jonathan Edwards**](https://youtu.be/ooqau_7ibvA?si=LU3jznlPSx7dCesM) 

* Implement **App Governance (this must be enabled on the Microsoft Defender Admin Portal: Turn On App Governance).**  
* Discover OAuth Apps.  
* Detect and prevent OAuth App's suspicious activity.  
* Visibility into OAuth Apps Metadata.  
* The **App Governance tile** in the **Microsoft Defender** portal offers a bird-eye view of the OAuth App estate on your tenant and provides metrics on the security posture in this respect.   
* It also provides charts and advice on how to improve the security posture by changing the settings of each detected OAuth App.

---

## [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) 

[Vulnerability management | Microsoft 365 Defender \- Microsoft Security](https://youtu.be/G54f7IqUFMU?si=qZ9usTTcdYMIh8fo)  
[Microsoft 365: **The Complete Guide** To Vulnerability Management \- **John Edwards**](https://youtu.be/r69wcxlLPqM?si=4dNS3Liv2-hKxwXO)    
[Microsoft Defender Vulnerability Management: New capabilities in risk mitigation & threat protection \- **Microsoft Security Community**](https://www.youtube.com/live/F_P14yoeg-A?si=Z2O6EjB5DzYfooi6)   
[Upgrade to Microsoft Defender Vulnerability Management \- Microsoft Security Community](https://youtu.be/nCEuDNfPKtk?si=HvigSHQjl31LWv2w) 

---

## [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)

[**Microsoft Defender for Cloud \- Playlist \- Microsoft Security Community**](https://www.youtube.com/playlist?list=PLmAptfqzxVEUvnWqb-AcIx7jABPTtyjdv)   
[Manage cloud security posture with Microsoft Defender for Cloud \- **in minutes** \- Microsoft Security](https://www.youtube.com/watch?v=nE6tFjP7Juc)  
[**Getting Started** with Microsoft Defender for Cloud \- Micorosft Security](https://www.youtube.com/watch?v=2y-QZK75vek) 

---

## [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)

[Microsoft Azure AD Identity Protection Deep Dive \- **John Savill**](https://www.youtube.com/watch?v=Nx2ych3xHl0&t=70s)   
[What is Microsoft Entra ID Protection? \- Microsoft Security](https://youtu.be/SFkrjA48J5E?si=3jw9smvf-Pvv-3_G)   
[How to set up Microsoft Entra ID Protection \- Microsoft Security](https://youtu.be/5mf72Vf40WU?si=ZHYAxUKu7UH1zoN0)   
[**Workload Identity Protection** with Azure AD Identity Protection \- **John Savill**](https://youtu.be/TASsrY_ilWc?si=saJyCKN-ZwPKX5UP) 

---

## [Microsoft Data Loss Prevention](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) 

[Endpoint DLP | What it is and how to set it up in Microsoft 365 \- Microsoft Mechanics](https://www.youtube.com/watch?v=XO2zMA3w1wA)   
[Everything You Need To Know About Data Loss Prevention In Microsoft 365 | Peter Rising, MVP](https://www.youtube.com/watch?v=5zQ-MOXjCcA)   
[Microsoft DLP Policies Demystified: Step-by-Step Tutorial | Peter Rising, MVP](https://youtu.be/VNk20hkIVGU?si=NyzjWhh3bgXoRWNl)  
[Data Loss Prevention in Microsoft 365 \- Stop Data Leakage \- Jonathan Edwards](https://www.youtube.com/watch?v=LHWX713SaZU)    
[Learn Microsoft 365 Data Loss Prevention Policies in Just 20 mins \- Andy Malone, MVP](https://www.youtube.com/watch?v=q3MhTFLYNAc)    
[**DLP** Microsoft **Purview for Endpoint** **Step-By-Step Guide and Demo** \- CloudInspired](https://www.youtube.com/watch?v=Ba3QCYyZdZs) 

---

## [Microsoft Purview Insider Risk Management](https://learn.microsoft.com/en-us/purview/insider-risk-management-solution-overview)

[Mastering Insider Risk In Microsoft Purview: The Ultimate Guide\! | Peter Rising, MVP](https://www.youtube.com/watch?v=_C9D-3qmHms)   
[Microsoft Purview Insider Risk Management | Admin Set-up Tutorial \- Microsoft Mechanics](https://www.youtube.com/watch?v=og90Rs8tVUA)

---

