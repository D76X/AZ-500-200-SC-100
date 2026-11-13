[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q06

A healthcare company deploys `Azure Firewall Standard` in its `hub virtual network` to inspect traffic between 
its Azure workloads and the internet. A new compliance requirement mandates that the firewall be able to detect 
and `block network intrusion attempts`, including `signature-based detection of known attack patterns`, and that 
it be able to inspect the contents of encrypted HTTPS traffic for malicious payloads rather than only filtering based 
on FQDN and IP address information. The company wants to meet this requirement using their existing Azure Firewall 
deployment rather than introducing a separate third-party network virtual appliance.

What should the company do?
Select one answer option below.

### OPTION 01
Deploy `Azure Web Application Firewall` in front of the existing `Azure Firewall Standard` deployment to provide TLS inspection and intrusion detection for all outbound traffic.

### OPTION 02
Configure additional application rules on the existing Azure Firewall Standard deployment using FQDN filtering for all known malicious domains.

### OPTION 03
Enable Azure Firewall's threat intelligence-based filtering in alert-and-deny mode on the existing Standard SKU deployment.

### OPTION 04
Upgrade the Azure Firewall deployment to the `Premium SKU`, and configure both the `intrusion detection` and `prevention system (IDPS)` and `TLS inspection` features.

---

## Answer and rationale

**Correct answer: OPTION 04.**

Upgrade Azure Firewall Standard to Premium, then `configure IDPS and TLS inspection`. 

Azure Firewall Premium provides managed, signature-based IDPS, which can alert on and block matching malicious traffic. 
Its `TLS inspection feature` decrypts supported outbound and `east-west TLS connections` for inspection, then re-encrypts the traffic. Together, these features meet the requirement to detect and block known attack patterns and inspect encrypted HTTPS payloads using the 
existing Azure Firewall service. [1][2]

TLS inspection requires configuration, including a trusted customer-provided CA certificate and appropriate firewall policy rules. 
Without TLS inspection, the firewall cannot see the contents inside encrypted TLS traffic. [1]

---

### Why the other options are not correct

### OPTION 01
Deploy `Azure Web Application Firewall` in front of the existing `Azure Firewall Standard` deployment 
to provide TLS inspection and intrusion detection for all outbound traffic.

- **OPTION 01:** Azure Web Application Firewall protects supported web applications from common web exploits, 
such as SQL injection and cross-site scripting. It is not a general-purpose control for inspecting all outbound 
network traffic, and it does not add Azure Firewall Premium's managed IDPS and outbound TLS inspection capabilities 
to the Standard firewall. [1][3]

---

### OPTION 02
Configure additional application rules on the existing Azure Firewall Standard deployment 
using FQDN filtering for all known malicious domains.

- **OPTION 02:** FQDN filtering controls traffic based on destination host names; 
it does not inspect the encrypted HTTPS payload or identify attack signatures within it. 
A malicious request can also use an otherwise permitted host name, so a domain blocklist 
does not satisfy the signature-based IDPS requirement. [1][2]

---

### OPTION 03
Enable Azure Firewall's threat intelligence-based filtering in alert-and-deny mode on the existing Standard SKU deployment.

- **OPTION 03:** Standard supports threat intelligence filtering in alert-and-deny mode, but this feature matches traffic against known malicious IP addresses and domains from Microsoft's threat intelligence feed. It is not signature-based IDPS and does not decrypt HTTPS to inspect payloads. [1][4]

You can enable Threat intelligence-based filtering for your firewall to alert and deny traffic 
from/to known malicious IP addresses, FQDNs, and URLs. The IP addresses, domains and URLs are 
sourced from the Microsoft Threat Intelligence feed, which includes multiple sources including 
the Microsoft Cyber Security team.

---

### References

1. [Azure Firewall Premium features implementation guide](https://learn.microsoft.com/en-us/azure/firewall/premium-features) — Premium IDPS and TLS inspection capabilities, traffic coverage, and TLS inspection requirements.

2. [Azure Firewall features by SKU](https://learn.microsoft.com/en-us/azure/firewall/features-by-sku) — SKU comparison showing that fully managed IDPS and outbound TLS termination are Premium features, while Standard includes FQDN filtering.

3. [Introduction to Azure Web Application Firewall](https://learn.microsoft.com/en-us/azure/web-application-firewall/overview) — WAF's role in protecting supported web applications from common exploits and its supported Azure services.

4. [Azure Firewall threat intelligence-based filtering](https://learn.microsoft.com/en-us/azure/firewall/threat-intel) — Threat intelligence filtering against known malicious IP addresses, FQDNs, and URLs, including alert-and-deny mode.

# Notes

# Azure Firewall Standard

Azure Firewall Standard is a cloud-native, stateful firewall-as-a-service (FWaaS) that 
protects Azure virtual network resources with built-in high availability and auto-scaling up to 30 Gbps. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/overview)

## Key Features

- Layer 3–Layer 7 Filtering: 
Supports application-level FQDN (Fully Qualified Domain Name) filtering for HTTPS and SQL, 
plus network-level FQDN filtering across all TCP/UDP protocols. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku)

- Threat Intelligence: 
Integrated with `Microsoft Threat Intelligence` to automatically alert and deny traffic to and from 
known malicious IP addresses and domains. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- Web Categories: 
Allows you to filter or block access to specific web content categories (such as social media, search engines, or gambling). 

[1] (https://docs.azure.cn/en-us/firewall/features), [2] (https://www.youtube.com/watch?v=PoyYshLsGag)

- Network Address Translation (NAT): 
Supports both `inbound DNAT (Destination NAT) and outbound SNAT (Source NAT)` with up to 250 associated public IP addresses. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- DNS Capabilities: 
Built-in DNS proxy and custom DNS server configuration support. 
[1] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku)

- Scalability & Availability: 
Automatically scales out dynamically up to 30 Gbps based on traffic and CPU utilization, with multi-Availability Zone 
support for high availability. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/firewall-faq), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku), 
[3] (https://docs.azure.cn/en-us/firewall/features)

## Pricing & Cost Structure

Azure Firewall Standard is billed using a combination of Microsoft Azure Pricing:
- Fixed Deployment Charge: Billed hourly per firewall instance.
- Variable Data Processing Charge: Billed per gigabyte of network traffic processed. 

[1] (https://azure.microsoft.com/en-us/pricing/details/azure-firewall/), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku)

To estimate or configure a deployment, check the Azure Pricing Calculator or review the full Azure Firewall SKU Comparison on Microsoft Learn. 
[1] (https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku)

---

# [What is Azure Firewall?](https://learn.microsoft.com/en-us/azure/firewall/overview)  

Azure Firewall is a cloud-native, intelligent network firewall security service that offers 
top-tier threat protection for your Azure cloud workloads. It's a fully stateful firewall 
as a service, featuring built-in high availability and unlimited cloud scalability. 

Azure Firewall inspects both `east-west and north-south traffic`. 

[Well-Architected FrameworkPillarsSecurity > Architecture strategies for networking and connectivity](https://learn.microsoft.com/en-us/azure/well-architected/security/networking#scope-of-influence)  

---

# [Azure Firewall Premium features implementation guide](https://learn.microsoft.com/en-us/azure/firewall/premium-features)

## [IDSP (Intrusion Detection and Prevention System)](https://learn.microsoft.com/en-us/azure/firewall/premium-features#idps)

It monitors your network for malicious activity, logs information, reports it, and optionally blocks it.

`Azure Firewall Premium` offers `signature-based IDPS` to quickly detect attacks 
by identifying specific patterns, such as byte sequences in network traffic or 
known malicious instruction sequences used by malware. 
These IDPS signatures apply to both application and network-level traffic (Layers 3-7). 
They are fully managed and continuously updated. IDPS can be applied to 
`inbound, spoke-to-spoke (East-West), and outbound traffic, including traffic to/from an on-premises network`. 

You can configure your IDPS private IP address ranges using the Private IP ranges feature. 
For more information, see IDPS Private IP ranges.

The Azure Firewall signatures/rulesets include:

- Focus on identifying actual malware, Command and Control, exploit kits, and malicious activities missed by traditional methods.
Over 67,000 rules in more than 50 categories, including malware command and control, phishing, trojans, botnets, informational events, exploits, vulnerabilities, SCADA network protocols, and exploit kit activity.
20 to 40+ new rules released daily.
Low false positive rate using advanced malware detection techniques such as global sensor network feedback loop.

---

# What is the TLS inspection feature of Azure Firewall?

The TLS inspection feature is an exclusive capability of Azure Firewall Premium that 
decrypts, inspects, and re-encrypts HTTPS/TLS traffic to detect and block 
hidden malware, exploits, and policy violations. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku), 
[3] (https://learn.microsoft.com/en-us/azure/networking/design-guide/azure-firewall)

# How It Works

- Two TLS Connections: 
When enabled, Azure Firewall Premium acts as a man-in-the-middle proxy. 
It terminates the TLS connection from the client, establishes a separate TLS connection 
with the destination web server, and inspects the plaintext payload in between. 

[1] (https://medium.com/@TakuSewo/tls-inspection-through-application-gateway-azure-firewall-and-web-server-how-to-and-tips-8f95e7dc6595), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/premium-features)

- Dynamic Certificate Generation: 
It uses a customer-provided Intermediate Certificate Authority (CA) certificate 
stored securely in Azure Key Vault to dynamically generate on-the-fly server 
certificates for the URLs being accessed. 

[1] (https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/building-a-poc-for-tls-inspection-in-azure-firewall/3676723), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/premium-certificates), 
[3] (https://learn.microsoft.com/en-us/azure/networking/design-guide/azure-firewall)

- End-User Trust: 
Client devices and browsers must trust your organization's root or intermediate CA certificate 
to prevent security warnings. 

[1] (https://www.youtube.com/watch?v=dbayTZp3YkM), 
[2] (https://learn.microsoft.com/en-us/azure/networking/design-guide/azure-firewall)

## Key Capabilities Unlocked

Without TLS inspection, standard firewalls can only see the basic `Fully Qualified Domain Name (FQDN)` 
or `Server Name Indication (SNI)`. 

Enabling TLS inspection allows Azure Firewall Premium to support: 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku), [3] (https://www.youtube.com/watch?v=16zOMymuFns)

- Full URL Filtering: 
Rules can evaluate the complete URL path (e.g., ://example.com) rather than just the base domain. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- `Intrusion Detection and Prevention System (IDPS)`: 
Deep packet inspection of HTTPS payloads against over 67,000 signature rules to spot malware, 
command-and-control traffic, and exploit kits. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- Web Categories: 
Granular allow/deny controls based on deep content analysis of encrypted web sessions. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- Traffic Scope: 
Supports both 
1. Outbound TLS Inspection (internal Azure clients to the internet) and 
2. East-West TLS Inspection (traffic within Azure or to/from on-premises networks)

[1] (https://learn.microsoft.com/en-gb/answers/questions/743560/how-will-tls-inpection-affect-the-idps), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

> Note: 
Inbound TLS inspection from the internet to Azure workloads is handled separately via Azure Application Gateway, 
not Azure Firewall. 

[1] (https://journeyofthegeek.com/2021/07/05/azure-firewall-and-tls-inspection/), 
[2] (https://learn.microsoft.com/en-gb/answers/questions/743560/how-will-tls-inpection-affect-the-idps)

## Requirements & Setup

- SKU: Requires the Azure Firewall Premium SKU. 
[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- Certificate Store: 
An exportable Intermediate CA certificate (RSA 2048-bit minimum) must be placed in Azure Key Vault 
with secret read permissions granted to the firewall's managed identity. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-certificates), 
[2] (https://learn.microsoft.com/en-us/azure/networking/design-guide/azure-firewall)

- Policy Configuration: 
The feature must be explicitly toggled on within your Azure Firewall Policy settings. 
You can follow the step-by-step instructions in the Enterprise CA Deployment Guide to configure your PKI chain. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-deploy-certificates-enterprise-ca), 
[2] (https://learn.microsoft.com/en-gb/answers/questions/743560/how-will-tls-inpection-affect-the-idps), 
[3] (https://learn.microsoft.com/en-us/azure/firewall/premium-certificates)

---

# What is the difference between the managed, signature-based IDPS and the TLS inspection feature of Azure Firewall?

The following features in Azure Firewall:

1. managed signature-based Intrusion Detection and Prevention System (IDPS) and 
2. the Transport Layer Security (TLS) inspection feature  

serve two distinct yet complementary roles in network security (available in Azure Firewall Premium). 

[1] (https://learn.microsoft.com/en-us/azure/networking/design-guide/azure-firewall)

## TLS Inspection

- What it does: 
Decrypts, inspects, re-encrypts, and forwards encrypted HTTPS/TLS traffic. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- How it works: 
It acts as a `man-in-the-middle proxy`. It terminates the incoming TLS connection 
(using a custom Certificate Authority you provide), inspects the plaintext payload, 
establishes a second TLS connection with the target web server, and then re-encrypts the data. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/secure-firewall), 
[2] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

- Scope: 
Applies to `outbound and East-West (inter-VNet/on-premises) traffic`. 
It allows the firewall to look inside encrypted web traffic to enforce full URL path filtering 
(e.g., ://contoso.com rather than just the domain) and web category rules. 

[1] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku)

---

## Signature-Based IDPS

• What it does: Monitors network traffic across layers 3 through 7 to detect and optionally block known cyber threats, exploits, malware, and command-and-control activity. [1] (https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/intrusion-detection-and-prevention-system-idps-based-on-signatures/3921330), [2] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), [3] (https://intercept.cloud/en-gb/blogs/the-evolution-of-azure-firewall)
• How it works: It uses a massive, continuously updated database of over 67,000 signature rules (spanning 50+ categories) to match byte sequences or malicious instruction patterns in network packets. It can be configured in modes such as Disabled, Alert, or Alert and Deny. [1] (https://azure.microsoft.com/en-us/blog/azure-firewall-premium-now-in-preview-2/), [2] (https://learn.microsoft.com/en-us/azure/firewall/premium-features), [3] (https://learn.microsoft.com/en-us/azure/firewall/features-by-sku), [4] (https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/intrusion-detection-and-prevention-system-idps-based-on-signatures/3921330)
• Scope: Works across all ports and protocols for inbound, outbound, and East-West traffic. [1] (https://azure.microsoft.com/en-us/blog/azure-firewall-premium-now-in-preview-2/), [2] (https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/intrusion-detection-and-prevention-system-idps-based-on-signatures/3921330)

Key Differences


Feature	TLS Inspection	Signature-Based IDPS
Primary Purpose	Unlocks and visibility-checks encrypted (HTTPS/TLS) traffic by decrypting and re-encrypting it.	Detects and blocks known malicious patterns, signatures, and exploits across network packets.
Traffic Handled	Outbound and East-West traffic only (inbound HTTPS requires a service like Azure Application Gateway).	Inbound, outbound, and East-West traffic across all ports and protocols.
Data Processing	Modifies the cryptographic stream by terminating and re-issuing TLS sessions.	Inspects packet contents against a database of known attack signatures without necessarily breaking encryption unless paired with TLS inspection.
Main Benefit	Enables full URL path filtering and web category analysis on HTTPS traffic.	Protects against known vulnerabilities, malware payloads, and network intrusions.


How They Work Together

While they are separate features, they complement each other. When IDPS analyzes outbound HTTPS traffic, it can only see encrypted noise unless TLS inspection is enabled to decrypt the stream first, allowing the IDPS engine to inspect the actual application-layer payload for hidden attacks. [1] (https://azure.microsoft.com/en-us/blog/azure-firewall-premium-now-in-preview-2/)
You can review implementation steps and architecture guidelines directly in the Azure Firewall Premium Features Implementation Guide. [1] (https://learn.microsoft.com/en-us/azure/firewall/premium-features)

---