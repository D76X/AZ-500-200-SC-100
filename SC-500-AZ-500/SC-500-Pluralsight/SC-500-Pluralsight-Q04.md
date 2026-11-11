
[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q04

A security engineer needs to forward syslog events from a Linux-based network appliance 
that does not support the required collection agent locally to Microsoft Sentinel. 
Which architecture should the engineer implement?

Which two configurations should the security architect implement?
Select one answer option below.

## OPTION 01
Deploy Azure Event Hubs and configure the appliance to stream syslog events to the Event Hub namespace

## OPTION 02
Configure the network appliance to send syslog events directly to the Log Analytics workspace HTTP Data Collector API

## OPTION 03
Install the Log Analytics agent (MMA) on the network appliance and configure it to collect syslog events directly

## OPTION 04
Deploy a Linux VM as a log forwarder, install Azure Monitor Agent on it, point the appliance to the forwarder, and use the Syslog via AMA connector with a DCR

---

# GPT-6 Luna

## Correct Answer

### OPTION 04
Deploy a Linux VM as a log forwarder, install Azure Monitor Agent (AMA) on it, 
configure the appliance to send Syslog to the forwarder, and use the Syslog 
via AMA connector with a data collection rule (DCR).

## Why OPTION 04 Is Correct

The appliance cannot run the required collection agent, so it must send its Syslog messages 
to a separate Linux machine that can receive them. Install AMA on that Linux forwarder, configure 
its Syslog daemon to listen for the appliance, and associate the forwarder with a DCR that collects 
the required facilities and severity levels and sends them to the Log Analytics workspace used by 
Microsoft Sentinel. 

Sentinel can then query and analyze the ingested events from the workspace's `Syslog` table.

This is Microsoft's documented architecture for devices that don't allow local installation of AMA: 
- the device sends logs to a dedicated Linux forwarder, and AMA forwards them to the workspace. 
- The DCR configures the Syslog data source and workspace destination.

The two key configurations are therefore:

1. Configure the appliance and Linux forwarder so the appliance sends Syslog to the forwarder's listener.
2. Configure AMA and its DCR to collect the received Syslog and route it to the Log Analytics workspace.

## Why the Other Options Are Not Correct

> **OPTION 01**: Deploy Azure Event Hubs and configure the appliance to stream Syslog events to the Event Hub namespace.

Event Hubs is an event-streaming service, not a Syslog listener. 

Its documented producer protocols are `Kafka, AMQP, and HTTPS`; a Syslog appliance cannot send 
the Syslog protocol directly to an Event Hubs namespace. A separate component would be needed to 
receive/translate the Syslog stream, and an additional consumer or ingestion path would be needed to 
get it into Sentinel. 

The Linux AMA forwarder is the direct, documented design for this requirement.

---

> **OPTION 02**: Configure the network appliance to send Syslog events directly to the Log Analytics workspace HTTP Data Collector API.

The `legacy HTTP Data Collector API` accepts `authenticated HTTP POST requests containing JSON records`; 
it is not a Syslog receiver. Using it would require the appliance to transform the Syslog messages into 
the API's request format rather than use the standard Syslog collection path. In addition, the API is 
deprecated and support ended on `September 14, 2026`. 

The supported Syslog connector uses AMA and a DCR.

---

> **OPTION 03**: Install the Log Analytics agent (MMA) on the network appliance and configure it to collect Syslog events directly.

This contradicts the premise that the appliance cannot support the required local collection agent. 
Also, the `Log Analytics agent (MMA/OMS) was retired on August 31, 2024`; Microsoft no longer supports it, 
and its cloud data-upload service can stop at any time. 

AMA on a separate Linux forwarder avoids both problems.

---

## Question Wording Note

The prompt asks for “Which two configurations” but then says “Select one answer option below.” 

The answer choices are also inconsistently numbered in the source: the fourth choice was labeled OPTION 03 a second time. OPTION 04 above corrects that duplicate label. The intended selection is the single forwarder architecture, which requires configuring both the appliance-to-forwarder path and the AMA/DCR collection path described above.

## References

- [Forward Syslog data to Microsoft Sentinel and Azure Monitor by using Azure Monitor Agent](https://learn.microsoft.com/en-us/azure/sentinel/forward-syslog-monitor-agent) — Microsoft’s documented Linux forwarder architecture for devices that cannot run an agent locally; includes Syslog listener and data forwarding setup.

- [Collect Syslog events with Azure Monitor Agent](https://learn.microsoft.com/en-us/azure/azure-monitor/vm/data-collection-syslog) — configuring the Linux Syslog data source, facilities/severity, DCR destination, and `Syslog` table.

- [Log Analytics Agent migration](https://learn.microsoft.com/en-us/azure/azure-monitor/agents/azure-monitor-agent-migration) — MMA retirement status and migration to AMA/DCR.

- [Migrate from the HTTP Data Collector API to the Logs Ingestion API](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/custom-logs-migrate) — legacy API deprecation and end of support.

- [What is Azure Event Hubs?](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about) — Event Hubs streaming purpose and supported protocols.

---
