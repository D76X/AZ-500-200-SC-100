# MCSB: Microsoft Cloud Security Benchmark

[Microsoft Cloud Security Benchmark (MCSB) \- **Collection**](https://learn.microsoft.com/en-us/collections/rjrqh8jo6r252z)   
[**MCSB**\-Funktionen und Kontrollen mit MCSB-Modul 2](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/2-design-solutions-best-practices-capabilities-controls)

[Security baselines for Azure-**MCSB**](https://learn.microsoft.com/en-us/security/benchmark/azure/security-baselines-overview) 

[Overview of Microsoft Cloud security benchmark (**v1**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview)   
[Overview of Azure security controls (**v2**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview-v2)   
[Overview of Azure security controls (**v3**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview-v3) 

[Azure Security Center webinar: Azure Security Benchmark-**Microsoft Security**](https://www.youtube.com/watch?v=6qiEgTHvvIc&t=60s)   
[Azure Security Benchmark **V3** Workbook | Microsoft Defender for Cloud Webinar-**Microsoft Security Community**](https://www.youtube.com/watch?v=WW4XI4qQSvM) 

[Design solutions that align with the Microsoft Cybersecurity Reference Architecture (MCRA) and Microsoft Cloud Security Benchmark (MCSB)](https://learn.microsoft.com/en-us/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/)  

[Microsoft Cloud security benchmark documentation](https://learn.microsoft.com/en-us/security/benchmark/azure/) 

---

[Securing Azure: Microsoft Cybersecurity Reference Architecture (MCRA) and Microsoft Cloud Security Benchmark (MCSB)](https://strategic-cyber.co.uk/2023/11/17/securing-azure-7-microsoft-cybersecurity-reference-architecture-mcra-and-microsoft-cloud-security-benchmark-mcsb/#:~:text=In%20conclusion%2C%20whereas%20the%20MCSB,Architecture%20to%20name%20a%20few). 

* **MCSB** provides mostly written technical control guides related to specific domains via a spreadsheet list.  
    
* **MCRA** provides technical diagrams for an Enterprise Access Model, a Security Operations Reference Architecture, and the components of a Zero Trust Architecture.

---

## [MCRA-MCSB-Häufige Cyberbedrohungen und Angriffsmuster](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/1-common-cyberthreats-attack-patterns) 

---

# [Übersicht über MCSB](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/1-introduction-reference-architecture-benchmark)

**Täglich** werden in Azure und auf anderen Cloudplattformen **neue Dienste und Features veröffentlicht**. Entwickler veröffentlichen **rasch** neue Cloudanwendungen, die auf diesen Diensten basieren, und Angreifer suchen ständig nach neuen Wegen, um **falsch konfigurierte Ressourcen** **auszunutzen**. Die Cloud ist von schnellem Wandel geprägt, und Entwickler legen ein hohes Tempo vor, mit dem auch die Angreifer Schritt halten. Wie halten Sie Schritt und können die Sicherheit Ihrer Cloudbereitstellungen gewährleisten? Inwiefern unterscheiden sich die Sicherheitsmethoden für Cloudsysteme von denen für lokale Systeme, und inwieweit unterscheiden sie sich zwischen verschiedenen Cloud-Dienstanbietern? **Wie überwachen Sie Ihre Workload** auf Konsistenz über mehrere Cloudplattformen hinweg?

Microsoft hat festgestellt, dass die Verwendung von **Sicherheitsvergleichstests** Ihnen helfen kann, **schnellen Schutz für Cloudbereitstellungen herzustellen**. Mithilfe eines umfassenden Framework für bewährte Sicherheitsmethoden von Clouddienstanbietern können Sie bestimmte Einstellungen für die Sicherheitskonfiguration in Ihrer Cloudumgebung für mehrere Dienstanbieter auswählen und **diese Konfigurationen über eine zentrale Verwaltungsoberfläche überwachen**.

In der MCSB werden **Kontrollen** in Familien oder Domänen gruppiert. 

---

# 

# [MCSB Controls](https://learn.microsoft.com/en-us/security/benchmark/azure/overview#controls) 

## 01\.[Netzwerksicherheit](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-network-security)

Zum Absichern und Schützen von Netzwerken, der Absicherung VNets, der Einrichtung privater Verbindungen, der Verhinderung und Eindämmung externer Angriffe und der DNS-Absicherung.

## 02\.[Identitätsverwaltung](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-identity-management)

zum Einrichten sicherer Identitäts- und Zugriffssteuerungen mithilfe von Identitäts- und Zugriffsverwaltungssystemen, z.B. einmalige Anmelden, sichere Authentifizierungen, verwaltete Identitäten (und Dienstprinzipale) für Anwendungen, bedingter Zugriff und Überwachung von Anomalien bei Konten.

## 03\.[Privilegierter Zugriff](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-privileged-access) 

zum Schutz des privilegierten Zugriffs auf Ihren Mandanten und Ihre Ressourcen, Schutz Ihres Verwaltungsmodells von administrativen Konten und von Arbeitsstationen mit privilegiertem Zugriff vor bewussten und ungewollten Risiken.0

## 04\.[Datenschutz (DP: Data Protection)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-data-protection)

Schutz von ruhender Daten, in Übertragung begriffener Daten und des Zugriffs über autorisierte Zugriffsmechanismen. Das Ermitteln, Klassifizieren, Schützen und Überwachen vertraulicher Daten mithilfe von Zugriffssteuerung, Verschlüsselung sowie Schlüssel- und Zertifikatverwaltung.

[**Module-Capabilities and controls with MCSB**](https://learn.microsoft.com/en-us/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/2-design-solutions-best-practices-capabilities-controls)

[DP-1: Discover, classify, and label sensitive data](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection)   
[DP-2: Monitor anomalies and threats targeting sensitive data](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection)   
[DP-3: Encrypt sensitive data in transit](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection)   
[DP-4: Enable data at rest encryption by default](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection)   
[DP-5: Use customer-managed key option in data at rest encryption when required](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection#dp-5-use-customer-managed-key-option-in-data-at-rest-encryption-when-required)   
[DP-6: Use a secure key management process](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection#dp-6-use-a-secure-key-management-process)   
[DP-7: Use a secure certificate management process](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection#dp-7-use-a-secure-certificate-management-process)   
[DP-8: Ensure security of key and certificate repository](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-data-protection#dp-8-ensure-security-of-key-and-certificate-repository) 

## 05 [Ressourcenverwaltung (AM: Asset Management)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-asset-management) 

Die **Sichtbarkeit** und **Governance** der Sicherheit von Ressourcen sichergestellt werden soll. Empfehlungen zu **Berechtigungen für Sicherheitspersonal**, den sicheren Zugriff auf den Ressourcenbestand und **das Verwalten von Genehmigungen** für Dienste und Ressourcen (**Bestand, Nachverfolgung** und **Richtigkeit**).

[AM-1: Track asset inventory and their risks](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-asset-management#am-1-track-asset-inventory-and-their-risks)   
[AM-2: Use only approved services](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-asset-management#am-2-use-only-approved-services)   
[AM-3: Ensure security of asset lifecycle management](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-asset-management#am-3-ensure-security-of-asset-lifecycle-management)   
[AM-4: Limit access to asset management](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-asset-management#am-4-limit-access-to-asset-management)   
[AM-5: Use only approved applications in virtual machine](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-asset-management#am-5-use-only-approved-applications-in-virtual-machine)

## 06 [Sicherheitssteuerung: Protokollierung und Bedrohungserkennung](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-logging-threat-detection) 

Kontrollmechanismen zur **Erkennung** von Bedrohungen in der Cloud sowie das **Aktivieren, Erfassen** und **Speichern** von **Überwachungsprotokollen** für Clouddienste. Dazu gehört das Aktivieren von Erkennungs-, Untersuchungs- und **Abhilfe**prozessen mit Mechanismen zur **Generierung** nützlicher **Warnungen** mithilfe der nativen Bedrohungserkennung in Clouddiensten. 

**Erfassen von Protokollen** mit einem Cloudüberwachungsdienst, die **Zentralisierung der Sicherheitsanalyse** mit einem **SIEM-System** (Security Information and Event Management), die **Zeitsynchronisierung** und die **Aufbewahrung** von Protokollen.

## 07 [Reaktion auf Vorfälle](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-incident-response)

Reaktion auf Incidents umfasst Kontrollmechanismen im Lebenszyklus der Reaktion auf Incidents. Dazu gehören **Vorbereitung, Erkennung** und **Analyse**, **Eindämmung** und [**Nachbereitung**](http://Nachbereitung) von Incidents, einschließlich der Nutzung von Azure-Diensten (z. B. Microsoft Defender for Cloud und Sentinel) und/oder Clouddiensten zur **Automatisierung des Prozesses zur Reaktion** auf Incidents.

## 08 [Status- und Sicherheitsrisikomanagement (PV)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-posture-vulnerability-management)

**Posture and Vulnerability Management (PV)**  
[Sicherheitskontrolle v3: **Haltung** und **Sicherheitsrisikomanagement**](https://learn.microsoft.com/de-de/security/benchmark/azure/security-controls-v3-posture-vulnerability-management) 

es konzentriert sich auf **Bewertung** und **Verbesserung** de**s Cloudsicherheitsstatus**,  **Überprüfung auf Sicherheitsrisiken**, 

Penetrationstests und Wartung sowie [**Nachbereitung**](http://Nachbereitung), **Berichterstellung** und **Korrektur** der **Sicherheitskonfiguration** von Cloudressourcen.

[PV-1: Define and establish secure configurations](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-1-define-and-establish-secure-configurations)   
[PV-2: Audit and enforce secure configurations](http://V)   
[PV-3: Define and establish secure configurations for compute resources](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-3-define-and-establish-secure-configurations-for-compute-resources)   
[PV-4: Audit and enforce secure configurations for compute resources](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-4-audit-and-enforce-secure-configurations-for-compute-resources)   
[PV-5: Perform vulnerability assessments](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-5-perform-vulnerability-assessments)   
[PV-6: Rapidly and automatically remediate vulnerabilities](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-6-rapidly-and-automatically-remediate-vulnerabilities)   
[PV-7: Conduct regular red team operations](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-posture-vulnerability-management#pv-7-conduct-regular-red-team-operations) 

## 09 [Endpunktsicherheit (ES)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-endpoint-security) 

Erkennung und Reaktion am Endpunkt (Endpoint Detection and Response, **EDR**) sowie die Nutzung von **EDR**\- und **Antischadsoftwaredienst**en für Endpunkte in Cloudumgebungen.

[ES-1: Use Endpoint Detection and Response (EDR)](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v2-endpoint-security#es-1-use-endpoint-detection-and-response-edr)  
[ES-2: Use modern anti-malware software](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v2-endpoint-security#es-2-use-centrally-managed-modern-anti-malware-software)  
[ES-3: Ensure anti-malware software and signatures are updated](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v2-endpoint-security#es-3-ensure-anti-malware-software-and-signatures-are-updated) 

## 10\. [Sicherung und Wiederherstellung (BR: Backup & Recovery)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-backup-recovery)

Sicherung und Wiederherstellung umfassen Kontrollmechanismen, die **sicherstellen**, dass **Daten- und Konfigurationssicherungen** auf den verschiedenen Dienstebenen **durchgeführt, überprüft** und **geschützt** werden.

[BR-1: Ensure regular automated backups](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-backup-recovery#br-1-ensure-regular-automated-backups)   
[BR-2: Protect backup and recovery data](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-backup-recovery#br-2-protect-backup-and-recovery-data)   
[BR-3: Monitor backups](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-backup-recovery#br-3-monitor-backups)   
[BR-4: Regularly test backup](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-backup-recovery#br-4-regularly-test-backup)

## 11\. [DevOps-Sicherheit](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-devops-security)

Die DevOps-Sicherheit deckt die Kontrollen im Zusammenhang mit der **Sicherheitsentwicklung** und den Vorgängen in DevOps-Prozessen ab, einschließlich der **Bereitstellung kritischer Sicherheitsüberprüfungen** z.B. **statische Anwendungssicherheitstests**, Sicherheitsrisikomanagement) vor der Bereitstellungsphase, um die **Sicherheit während des gesamten DevOps-Prozesses** zu gewährleisten. 

Zudem fallen darunter auch allgemeine Themen wie **Gefahrenmodellierung** und **Softwarebereitstellungssicherheit**.

[DS-1: Conduct threat modeling](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-1-conduct-threat-modeling)   
[DS-2: Ensure software supply chain security](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-2-ensure-software-supply-chain-security)   
[DS-3: Secure DevOps infrastructure](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-3-secure-devops-infrastructure)   
[DS-4: Integrate static application security testing into DevOps pipeline](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-4-integrate-static-application-security-testing-into-devops-pipeline)   
[DS-5: Integrate dynamic application security testing into DevOps pipeline](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-5-integrate-dynamic-application-security-testing-into-devops-pipeline)   
[DS-6: Enforce security of workload throughout DevOps lifecycle](http://v)   
[DS-7: Enable logging and monitoring in DevOps](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-devops-security#ds-7-enable-logging-and-monitoring-in-devops)

[Entwerfen einer Resilienzstrategie für Ransomware und andere Angriffe auf der Grundlage bewährter Sicherheitsmethoden von Microsoft](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/)   
[Häufige Cyberbedrohungen und Angriffsmuster](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/1-common-cyberthreats-attack-patterns)

## 12\. [Governance und Strategie (GS)](https://learn.microsoft.com/de-de/security/benchmark/azure/mcsb-governance-strategy)

Governance und Strategie bieten **Leitlinien** für die Gewährleistung einer **stimmigen Sicherheitsstrategie** und eines **dokumentierten Governanceansatzes** zur Steuerung und [**Aufrechterhaltung**](https://www.collinsdictionary.com/dictionary/german-english/aufrechterhaltung) der Sicherheitsgarantie. Dazu gehören auch die **Festlegung von Rollen** und **Verantwortlichkeiten** für die verschiedenen Cloudsicherheitsfunktionen, **eine einheitliche technische Strategie** und **die Unterstützung von Richtlinien und Standards**.

[GS-1: Align organization roles, responsibilities and accountabilities](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-1-align-organization-roles-responsibilities-and-accountabilities)  
[GS-2: Define and implement enterprise segmentation/separation of duties strategy](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-2-define-and-implement-enterprise-segmentationseparation-of-duties-strategy)   
[GS-3: Define and implement data protection strategy](http://V)   
[GS-4: Define and implement network security strategy](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-4-define-and-implement-network-security-strategy)   
[GS-5: Define and implement security posture management strategy](http://V)   
[GS-6: Define and implement identity and privileged access strategy](http://V)   
[GS-7: Define and implement logging, threat detection and incident response strategy](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-7-define-and-implement-logging-threat-detection-and-incident-response-strategy)   
[GS-8: Define and implement backup and recovery strategy](http://V)   
[GS-9: Define and implement endpoint security strategy](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-9-define-and-implement-endpoint-security-strategy)   
[GS-10: Define and implement DevOps security strategy](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-governance-strategy#gs-10-define-and-implement-devops-security-strategy)

**\> [Nachbereitung](https://www.dwds.de/wb/Nachbereitung) (=[nachträglich](https://www.collinsdictionary.com/dictionary/german-english/nachtraglich)e Beschäftigung oder Befassung mit etwas)**  
**\> [nachbearbeiten](https://www.collinsdictionary.com/dictionary/german-english/nachbearbeiten):** Dazu gehören Vorbereitung, Erkennung und Analyse, Eindämmung und [**Nachbereitung**](http://Nachbereitung) von Incidents.   
\> das Team sollt jenen [**bedeutungsvoll**](https://www.collinsdictionary.com/dictionary/german-english/bedeutungsvoll) (=[bedeutsam](https://www.collinsdictionary.com/dictionary/german-english/bedeutsam), **folgenschwer, wichtig**) Incident [**nachbearbeiten**](https://www.collinsdictionary.com/dictionary/german-english/nachbearbeiten).

---

# [Schutz vor Angriffen mit MCSB](https://learn.microsoft.com/de-de/training/modules/design-solutions-microsoft-cybersecurity-cloud-security-benchmark/3-design-solutions-best-practices-attack-protection)

## 13\. [Security Control: Incident response (IR)](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response)

[Sicherheitssteuerung v3: Reaktion auf Vorfälle](https://learn.microsoft.com/de-de/security/benchmark/azure/security-controls-v3-incident-response)

[IR-1: Preparation \- update incident response plan and handling process](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-1-preparation---update-incident-response-plan-and-handling-process)  
[IR-2: Preparation \- setup incident notification](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-2-preparation---setup-incident-notification)  
[IR-3: Detection and analysis \- create incidents based on   high-quality alerts](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-3-detection-and-analysis---create-incidents-based-on-high-quality-alerts)  
[IR-4: Detection and analysis \- investigate an incident](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-4-detection-and-analysis---investigate-an-incident)  
[IR-5: Detection and analysis \- prioritise incidents](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-5-detection-and-analysis---prioritize-incidents)  
I[R-6: Containment, eradication, and recovery \- automate the incident handling](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-6-containment-eradication-and-recovery---automate-the-incident-handling)  
[IR-7: Post-incident activity \- conduct lessons learned review and retain evidence](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-incident-response#ir-7-post-incident-activity---conduct-lesson-learned-and-retain-evidence)   

## 14\. [Security Control v3: Logging and threat detection (LT)](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection) 

[LT-1: Enable threat detection capabilities](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection#lt-1-enable-threat-detection-capabilities)   
[LT-2: Enable threat detection for identity and access management](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection#lt-2-enable-threat-detection-for--identity-and-access-management)   
[LT-3: Enable logging for security investigation](http://V)   
[LT-4: Enable network logging for security investigation](http://V)   
[LT-5: Centralize security log management and analysis](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection#lt-5-centralize-security-log-management-and-analysis)   
[LT-6: Configure log storage retention](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection#lt-6-configure-log-storage-retention)   
[LT-7: Use approved time synchronization sources](https://learn.microsoft.com/en-us/security/benchmark/azure/security-controls-v3-logging-threat-detection#lt-7-use-approved-time-synchronization-sources)  

---

[Entwerfen von Sicherheit mit Azure-Zielzonen-**Microsoft Learn**](https://learn.microsoft.com/de-de/training/modules/design-solutions-align-cloud-adoption-framework-well-architected-framework/5-design-security-with-azure-landing-zones) 

**Sicherheitskontrollen**:   
[Overview of Microsoft Cloud security benchmark (**v1**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview)   
[Overview of Azure security controls (**v2**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview-v2)   
[Overview of Azure security controls (**v3**)](https://learn.microsoft.com/en-us/security/benchmark/azure/overview-v3) 

Die Empfehlungen des Microsoft-Cloudsicherheitsbenchmarks werden nach Sicherheitskontrollelementen kategorisiert. Sicherheitskontrollen stellen **allgemeine herstellerunabhängige Sicherheitsanforderungen** dar, z. B. Netzwerksicherheit und Datenschutz. Jedes Sicherheitskontrollelement enthält eine Reihe von Sicherheitsempfehlungen und Anweisungen, mit denen Sie diese Empfehlungen implementieren können.

**Sicherheitsempfehlungen:**   
[Sicherheitsbaselines für Azure-**MCSB**](https://learn.microsoft.com/de-de/security/benchmark/azure/security-baselines-overview) 

Wenn verfügbar, enthalten die Empfehlungen des Vergleichstests für Azure-Dienste auch Empfehlungen des Microsoft-Cloudsicherheitsbenchmarks, die **speziell auf diesen Dienst zugeschnitten sind**.

\>   
\> **langfristig**e **Archivierung** von **Protokollen** (=logs)  
\> **Datenaufbewahrungszeiträume** (=data retention) : Microsoft Entra ID P1- oder P2-Berichte werden 30 Tage lang aufbewahrt.

---

