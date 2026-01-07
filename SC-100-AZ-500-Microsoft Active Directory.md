# Microsoft Active Directory-SC-100-AZ-500

---

# [Best practices for securing Active Directory](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory) 

The most common vulnerabilities are:

* Gaps in antivirus and anti-malware deployments  
* Incomplete patching  
* Outdated applications and operating systems  
* Misconfiguration  
* Lack of secure application development practices

* ### [Credential theft](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory#credential-theft):

  Credential theft attacks occur when an **attacker gains privileged access to a computer on a network** by using **tools to extract credentials from active sessions of signed-in accounts and mimics their identity**.  
    
- Permanently privileged accounts  
- VIP accounts  
- Privilege-attached Active Directory accounts  
- Domain controllers  
- Other infrastructure services that affect identity, access, and configuration management, such as public key infrastructure (PKI) servers or systems management servers

Users with highly privileged accounts raise the risk of having their credentials stolen by engaging in the following behaviour:

- Signing into their privileged accounts on unsecured computers  
- Browsing the internet while signed in to a privileged account

* ### [Use secure administrative hosts](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory#use-secure-administrative-hosts):

Secure administrative hosts are computers configured to support administration for Active Directories and other connected systems. These hosts don't run non-administrative software like email applications, web browsers, or productivity software like Microsoft Office.

- Never administer a trusted system from a less-trusted host.  
- Require MFA for privileged accounts or administrative tasks.  
- Guarantee physical and network security for your admin hosts.

---

# [Microsoft Active Directory-Playlist-Tom Wechsler](https://www.youtube.com/playlist?list=PLi0MTIjZai_y1Y9Wc-1qt-QB9uY_9-wZq)

Alles Rund um das Microsoft Active Directory

##### Ressourcen

[Microsoft Active Directory-Playlist-Tom Wechsler](https://www.youtube.com/playlist?list=PLi0MTIjZai_y1Y9Wc-1qt-QB9uY_9-wZq)  
[Active Directory and Entra ID Administration-Path-Pluralsight](https://app.pluralsight.com/paths/skill/active-directory-and-entra-id-administration)  

##### Zusätzliche Ressourcen

---

# [Folge 4 \- Azure AD Connect mit Intune Infrastruktur](https://www.youtube.com/watch?v=uO2XpJGhwW0)

##### Ressourcen

[Azure-Tips](https://www.youtube.com/playlist?list=PLi0MTIjZai_yIjbrPZZYJBeygL4W__wqF)  
[Azure Tip: Azure AD Connect \- Schritt 1 \- Vorbereitung und Installation von Azure AD Connect](https://www.youtube.com/watch?v=Q-5IQaTbPTE&list=PLi0MTIjZai_yIjbrPZZYJBeygL4W__wqF&index=97)    
[Azure Tip: Azure AD Connect \- Schritt 2 \- Konfiguration von Azure AD Connect](https://www.youtube.com/watch?v=8Gy-qFJZ_XE&list=PLi0MTIjZai_yIjbrPZZYJBeygL4W__wqF&index=98)  
[Azure Tip: Azure AD Connect \- Schritt 3 \- Ueberpruefen und testen von Azure AD Connect](https://www.youtube.com/watch?v=svaFnVvJFUY&list=PLi0MTIjZai_yIjbrPZZYJBeygL4W__wqF&index=99) 

[Plan your Microsoft Entra hybrid join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan)   
[Configure Microsoft Entra hybrid join](https://learn.microsoft.com/en-us/entra/identity/devices/how-to-hybrid-join)   
 

In dieser Folge geht es darum, dass wir das Werkzeug Azure AD Connect (AzADC) [eingerichten](https://www.collinsdictionary.com/dictionary/german-english/einrichten), **damit** wir ein **lokales** Active Directory (**ALD**) [**synchronizieren**](https://www.collinsdictionary.com/dictionary/german-english/synchronisieren) können **mit/ins Azure Active Directory (AAD)**.

\> [**einrichten**](https://www.collinsdictionary.com/dictionary/german-english/einrichten) (**vorbereiten**, **im [Einsatz](https://www.collinsdictionary.com/dictionary/german-english/einsatz) setzen**): die [Einrichtung](https://www.collinsdictionary.com/dictionary/german-english/einrichtung) eines Werkzeugs

---

