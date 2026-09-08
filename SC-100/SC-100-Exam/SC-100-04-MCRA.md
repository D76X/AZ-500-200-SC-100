# MCRA Microsoft Cybersecurity Reference Architecture

[Design solutions that align with the Microsoft Cybersecurity Reference Architecture (MCRA) and Microsoft cloud security benchmark (MCSB)](https://learn.microsoft.com/en-us/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/)  

[MCRA-Microsoft Cybersecurity Reference Architectures-**Collection**](https://learn.microsoft.com/en-us/collections/g23msnd27o06qk) 

[Microsoft Cybersecurity Reference Architectures](https://learn.microsoft.com/en-us/security/adoption/mcra)   
[**MCRA**\-Funktionen und Kontrollen mit MCRA-**Modul 2**](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/2-design-solutions-best-practices-capabilities-controls)  
[**MCRA**\-Securing privileged access](https://learn.microsoft.com/en-us/security/privileged-access-workstations/overview)   
[**MCRA**\-Privileged access: **Strategy**](https://learn.microsoft.com/en-us/security/privileged-access-workstations/privileged-access-strategy) 

---

[Securing Azure: Microsoft Cybersecurity Reference Architecture (MCRA) and Microsoft Cloud Security Benchmark (MCSB)](https://strategic-cyber.co.uk/2023/11/17/securing-azure-7-microsoft-cybersecurity-reference-architecture-mcra-and-microsoft-cloud-security-benchmark-mcsb/#:~:text=In%20conclusion%2C%20whereas%20the%20MCSB,Architecture%20to%20name%20a%20few). 

* **MCSB** provides mostly written technical control guides related to specific domains via a spreadsheet list.  
    
* **MCRA** provides technical diagrams for an Enterprise Access Model, a Security Operations Reference Architecture, and the components of a Zero Trust Architecture.

---

   
[Übersicht über MCRA](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/1-introduction-reference-architecture-benchmark)

Die **Microsoft Cybersecurity Reference Architectures (MCRA)** sind **technische Diagramme** zur Beschreibung der Cybersicherheitsfunktionen von Microsoft. In den Diagrammen wird beschrieben, **wie die Sicherheitsfunktionen von Microsoft mit folgenden Komponenten integriert** werden:

* Microsoft-Plattformen wie Microsoft 365 und Microsoft Azure  
* Anwendungen von **Drittanbietern** wie ServiceNow und Salesforce  
* Plattformen von Drittanbietern wie:   
  * Amazon Web Services (AWS)   
  * Google Cloud Platform (GCP)  
    

Die MCRA enthält **Diagramme zu** den folgenden **Themen**:

Sie finden die Diagramme auf den folgenden Links:  
[Zero Trust-**Abbildungen für IT-Architekten** und \-Implementierer](https://learn.microsoft.com/de-de/security/zero-trust/zero-trust-tech-illus)    
[Zero Trust **illustrations for IT architects** and implementers](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-tech-illus)   
[**RaMP initiatives** for Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-ramp-overview#ramp-initiatives-for-zero-trust)  
 

* Microsoft-Cybersicherheitsfunktionen  
* Zero Trust sowie einen [Zero Trust-Modernisierungsplan (RaMP)](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-ramp-overview)  
* Zero Trust-Benutzerzugriff  
* Sicherheitsvorgänge  
* Operational Technology (OT)  
* Multicloud- und plattformübergreifende Funktionen  
* Abdeckung der Angriffskette  
* Native Sicherheitskontrollen in Azure  
* Sicherheitsorganisatorische Funktionen

---

## [Schutz vor Angriffen mit MCRA](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/3-design-solutions-best-practices-attack-protection)

[Entwerfen einer Resilienzstrategie für Ransomware und andere Angriffe auf der Grundlage bewährter Sicherheitsmethoden von Microsoft](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/)   
[Häufige Cyberbedrohungen und Angriffsmuster](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/1-common-cyberthreats-attack-patterns)

**MCRA \> Erkennen \> Reagieren \> Wiederherstellen : ERW**

1. Kontinuierliche Verbesserung in Richtung vollständige Abdeckung  
2. Ausgewogene Kontrollinvestitionen über den gesamten Lebenszyklus; **Identifizierung, Schutz, Erkennung, Reaktion** und **Wiederherstellung \= IESRW**  
     
3. Von SIEM für alles zu **XDR \+ SIEM:**   
   **SIEM** (Security Information and Event Management)  
     
   [**Microsoft Defender XDR: Deine umfassende Verteidigungsstrategie für Endpunkte und Cloud-Dienste-CloudPingPong**](https://www.youtube.com/watch?v=lsjnABpRGe0)    
     
     
   **XDR:** e**X**tended \+ **D**etection \+ **R**esponse  
     
   [**Microsoft Defender XDR**](https://www.microsoft.com/en-us/security/business/siem-and-xdr/microsoft-defender-xdr)**:**   
   Elevate your security with **unified visibility, investigation, and response across the cyberattack chain** with an industry-leading extended detection and response (XDR) solution.  
     
   [What is Microsoft Defender XDR?](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)   
   Microsoft Defender XDR is a unified pre- and post-breach enterprise defence suite that natively coordinates detection, prevention, investigation, and response across endpoints, identities, email, and applications to provide integrated protection against sophisticated attacks.  
     
   Microsoft Defender XDR **takes automatic action to prevent or stop the attack and self-heal affected mailboxes, endpoints, and user identities**.  
     
   Microsoft Defender XDR helps security teams protect and detect their organisations by using information from other Microsoft security products, including:  
     
- Microsoft Defender for Endpoint  
- Microsoft Defender for Office 365  
- Microsoft Defender for Identity  
- Microsoft Defender for Cloud Apps  
- Microsoft Defender Vulnerability Management  
- Microsoft Defender for Cloud  
- Microsoft Entra ID Protection  
- Microsoft Data Loss Prevention  
- App Governance

  With the integrated Microsoft Defender XDR solution, security professionals can stitch together the threat signals that each of these products receives and determine the full scope and impact of the threat.


- how it entered the environment,   
- what it's affected  
- how it's currently impacting the organisation

 

4. **SOAR-Automatisierung und moderne Analyse:** Verringern Sie den manuellen Aufwand bei Sicherheitsvorgängen.  
      
- **SOAR** (Security Orchestration, Automation and Response)   
- **ML (Machine Learning)**  
- UEBA (User Entity Behavioral Analytics): .UEBA verbessert die Erkennung und Untersuchung, indem es ein Profil der einzelnen Benutzerkonten und Entitäten erstellt, die von Angreifern kompromittiert werden, anstatt zu versuchen, Muster in den gesamten Rohprotokolldaten zu finden.  
    
    
    
5. **Anpassen von Prozessen auf operative Technologie (OT)**

---

## [MCRA-MCSB-Häufige Cyberbedrohungen und Angriffsmuster](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/1-common-cyberthreats-attack-patterns) 

---

