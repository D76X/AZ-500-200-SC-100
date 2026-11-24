[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q15

A security team wants to reduce the exposure of VM management ports 
by ensuring that RDP and SSH are only accessible for a limited time 
window after an administrator submits an approved request. 

Which Defender for Servers feature provides this capability?

Select one answer option below.

### OPTION 01
Agentless VM scanning

### OPTION 02
Azure Bastion

### OPTION 03
Just-in-Time (JIT) VM access

### OPTION 04
Azure Network Watcher packet capture

---

## Answer

**Correct answer: OPTION 03 — Just-in-Time (JIT) VM access.**

JIT VM access is a Defender for Servers feature in Microsoft Defender for Cloud. 
It keeps selected management ports—such as `SSH (22)` and `RDP (3389)`—closed to inbound traffic by default, 
then permits access when an authorized user requests it. The request specifies the ports, source IP address, 
and access duration; the JIT policy limits when and from where those ports are open. 

This directly meets the requirement to allow management access only for a limited time after a request. [1]

> Microsoft training learning path and Applied Skills credential titled Secure Azure services and workloads with Microsoft Defender for Cloud regulatory compliance controls.
[Explore just-in-time VM access SC-5002 Microsoft Learn](https://www.youtube.com/watch?v=ZD-7eCWxD_k)   

---

### Why the other options are incorrect

- **OPTION 01 — Agentless VM scanning:** Agentless scanning analyzes VM disk snapshots for configuration issues, vulnerabilities, secrets, and malware. It assesses VM security posture; it does not open or close inbound network ports in response to an access request. [2]

- **OPTION 02 — Azure Bastion:** Bastion provides secure RDP/SSH connectivity to VMs over TLS without exposing the VMs' RDP/SSH ports externally. It is a remote-access service, not the Defender for Servers feature that temporarily changes port access according to a JIT request and time limit. [3]
- **OPTION 04 — Azure Network Watcher packet capture:** Packet capture records network traffic to and from a VM for troubleshooting and analysis. Capturing traffic does not control whether RDP or SSH is allowed, so it cannot enforce request-based, time-limited access. [4]

### References

1. [Enable Just-in-Time Access — Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-just-in-time-access) — identifies JIT as a Defender for Servers feature, documents its supported management ports, and explains requesting access with a source IP and time window.

2. [Agentless machine scanning in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection) — describes agentless scanning of VM snapshots for security assessment.

3. [What is Azure Bastion?](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview) — describes secure RDP/SSH connectivity without exposing VM management ports externally.

4. [Packet Capture Overview — Azure Network Watcher](https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview) — describes packet capture as a network troubleshooting and analysis tool.

---

# What is Microsoft Agentless VM scanning?

Microsoft agentless VM scanning, officially called `agentless machine scanning in Microsoft Defender for Cloud`
is a security feature that inspects virtual machines `out-of-band` using disk snapshots 
`without installing agents on the VM or requiring network connectivity`. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms)

`It runs once every 24 hours on a fixed schedule` across connected `Azure VMs, AWS EC2 instances, and GCP compute` instances. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

## How It Works

- Disk snapshots: 
Defender for Cloud takes copies of VM disk snapshots (root and data disks) in the same region as the VM. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

- Isolated analysis: 
It analyzes the OS configuration and file system in a secure, isolated regional environment 
with no performance impact on the running VM. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

- Cleanup and reporting: 
Metadata is sent to Defender for Cloud engines for analysis and displayed on the Security alerts page, 
while the copied snapshot is deleted right after (typically within minutes). 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

## What It Scans and Required Plans

- Software inventory: 
Lists installed software on supported disks (`Defender CSPM (Cloud Security Posture Management`) 
or `Defender for Servers Plan 2`). 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms)

- Vulnerability assessment: 
Identifies known software vulnerabilities via `Microsoft Defender Vulnerability Management` 
(`Defender CSPM` or `Defender for Servers Plan 2`). 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms)

- Secrets scanning: 
Finds plaintext secrets stored on disks (Defender CSPM or Defender for Servers Plan 2). 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms)

- `Endpoint detection and response (EDR)` checks: 
Checks whether an EDR solution is running and configured properly. 
[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

- Malware scanning: 
Scans files and folders for malware and viruses using `Microsoft Defender Antivirus` 
(`Defender for Servers Plan 2 only`). 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms)

For full configuration details, review Agentless machine scanning in Microsoft Defender for Cloud. 

[1] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection)

## Common Usage Examples

- Rapid and broad coverage: 
Quickly assessing new, temporary, or legacy VMs across Azure, AWS, and GCP without deploying agents.

- Pre-agent or gap visibility: 
Gaining baseline vulnerability, secret, and malware visibility before rolling out an agent or 
on machines without an active antivirus/EDR agent.

- Attack path and secret discovery: 
Spotting exposed credentials on disks that could enable lateral movement or cross-cloud attacks. 

[1] (https://techcommunity.microsoft.com/blog/microsoftdefendercloudblog/agentless-scanning-for-virtual-machines-in-the-cloud-%E2%80%93-technical-deep-dive/4012256), 
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection), 
[3] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms), 
[4] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/agentless-malware-scanning), 
[5] (https://learn.microsoft.com/en-us/shows/mdc-in-the-field/agentless-secret-scanning-for-virtual-machines), 
[6] (https://techcommunity.microsoft.com/blog/microsoftdefendercloudblog/defender-for-clouds-agentless-secret-scanning-for-virtual-machines-is-now-genera/3994018), 
[7] (https://www.youtube.com/watch?v=mP6-yv-nBXk)

## Related Terms and Synonyms

Microsoft primarily uses agentless machine scanning or agentless scanning for VMs/servers. 
In broader cloud security, it is also referred to as `snapshot-based scanning or out-of-band VM scanning` 
(as opposed to agent-based or host-based scanning). 

[1] (https://www.youtube.com/watch?v=zO3MoPfeTfE),  
[2] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection),   
[3] (https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-agentless-scanning-vms),   
[4] (https://www.wiz.io/academy/cloud-security/agentless-scanning-vs-agent-based-scanning),   
[5] (https://medium.com/@kapetaniosand/defender-for-endpoint-vs-agentless-differences-use-cases-and-why-both-matter-7442683ca002)  

---

# What is Microsoft Azure Network Watcher packet capture?

Microsoft Azure Network Watcher packet capture is a `remote diagnostic feature` that 
lets you create packet capture sessions to track inbound and outbound network traffic 
on `Azure virtual machines (VMs) and virtual machine scale sets` 
`without logging into the guest operating system`. 

It uses the `AzureNetworkWatcherExtension VM extension` and saves captured `.cap` files 
to an `Azure Blob Storage` account or a local path on the VM. You can review the full feature 
details in the Packet Capture Overview. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview), 
[2] (https://azure.microsoft.com/en-gb/products/network-watcher), 
[3] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-alert-triggered), 
[4] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-manage)

## Common Usage Examples

- Troubleshooting network and application issues: 
Debug client-server communication failures, latency, or connectivity drops. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-inspect), 
[2] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview), 
[3] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-alert-triggered)

- Proactive alert-triggered monitoring: 
Automatically start a capture via Azure alerts or automation (such as Azure Functions) 
when an anomaly occurs. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-alert-triggered), 
[2] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview)

- Continuous monitoring for intermittent issues: 
Run long-duration captures using a ring buffer mechanism (configurable in the Azure portal) 
to catch hard-to-reproduce or intermittent problems. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview)

- Security and traffic analysis: 
Investigate potential network intrusions or misuse, gather network statistics, 
and inspect traffic with tools like Wireshark. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview), 
[2] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-alert-triggered),  
[3] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-inspect)  

- Targeted filtering: 
Filter captures by specific ports, IP addresses, and protocols 
to focus on relevant traffic and reduce file size. 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview),   
[2] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-alert-triggered)  

## Related Terms and Synonyms

In networking and cloud contexts, packet capture is commonly referred to or associated with:

- Packet sniffing or network sniffing
- PCAP (packet capture format/concept)
- Protocol analysis or traffic capture
- Remote packet capture (when initiated via management tools rather than locally on the host) 

[1] (https://learn.microsoft.com/en-us/azure/network-watcher/packet-capture-overview),  
[2] (https://www.solarwinds.com/resources/it-glossary/pcap),  
[3] (https://azure.microsoft.com/en-gb/products/network-watcher)  

---