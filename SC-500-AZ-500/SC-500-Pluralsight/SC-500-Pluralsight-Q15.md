[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q15

A security team wants to reduce the exposure of VM management ports by ensuring that RDP and SSH are only accessible for a limited time window after an administrator submits an approved request. Which Defender for Servers feature provides this capability?

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

JIT VM access is a Defender for Servers feature in Microsoft Defender for Cloud. It keeps selected management ports—such as SSH (22) and RDP (3389)—closed to inbound traffic by default, then permits access when an authorized user requests it. The request specifies the ports, source IP address, and access duration; the JIT policy limits when and from where those ports are open. This directly meets the requirement to allow management access only for a limited time after a request. [1]

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

---