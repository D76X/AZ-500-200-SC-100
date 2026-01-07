# [Azure Update Manager](https://learn.microsoft.com/en-us/azure/update-manager/overview) 

[SC-100-AZ-305-Azure Update Manager 2023 Edition-John Savill](https://www.youtube.com/watch?v=LVmNh5YgBOQ) 

[**Azure Update Manager Overview**](https://learn.microsoft.com/en-us/azure/update-manager/overview) 

The Azure Automation Update Management and the Log Analytics agent it uses have been retired on **31st August 2024**. 

[**Bewerten von Lösungen für Sicherheitsupdates**](https://learn.microsoft.com/de-de/training/modules/design-resiliency-strategy-common-cyberthreats-like-ransomware/5-security-updates) 

**Update Manager wurde neu gestaltet** und ist im Gegensatz zur [**Updateverwaltung in Azure Automation**](https://learn.microsoft.com/de-de/azure/automation/update-management/overview) **nicht mehr** von Azure Automation- oder Azure Monitor-Protokollen abhängig. Update Manager bietet im Vergleich zur ursprünglichen Version, die über Azure Automation verfügbar war, viele neue Features und erweiterte Funktionen.

Die Update Manager zugewiesenen Computer melden, wie aktuell sie sind, basierend auf der für sie **konfigurierten Quelle für die Synchronisierung**:

* [Windows Update Agent (WUA)](https://learn.microsoft.com/en-us/windows/win32/wua_sdk/updating-the-windows-update-agent) auf Windows-Computern  
* [Windows Server Update Services (WSUS)](https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)   
* Sie können **Linux-Computer** so konfigurieren, dass sie einem lokalen oder öffentlichen **YUM-** oder **APT-Paket-Repository** gemeldet werden.

 

---

