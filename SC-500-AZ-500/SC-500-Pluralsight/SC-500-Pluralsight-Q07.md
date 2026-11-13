[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q07

A healthcare company runs a workload processing highly sensitive patient records on an Azure virtual machine. 
The workload already relies on `Secure Boot` and `vTPM` to protect against `boot-level rootkits`. 
A new `compliance requirement states that the VM's memory contents must be encrypted using hardware-based technology`, 
so that even someone with privileged access to the underlying host cannot inspect the VM's memory while the workload 
is running.

Which VM security type should the engineer select when creating the VM to meet both the existing and the new requirement?

What should the company do?
Select one answer option below.

### OPTION 01
Trusted launch

### OPTION 02
Confidential VM

### OPTION 03
Standard

### OPTION 04
Trusted launch with Azure Disk Encryption enabled on the OS and data disks

---

## Answer and rationale

**Correct answer: OPTION 02 — Confidential VM.**

Select the `Confidential VM` security type and use a supported confidential VM size and image. 
Azure Confidential VMs use hardware-based isolation to protect data while it is being processed, 
including protection from access by the hypervisor and host operating system. 
They also provide a dedicated vTPM and support Secure Boot, meeting the existing boot-integrity 
requirements as well as the new requirement to protect memory contents at runtime. [1][2]

Configure Secure Boot and vTPM for the selected VM, as required by the image and deployment. 
Confidential VM features and supported sizes/images vary, so verify compatibility before deployment. [2]

---

### Why the other options are not correct

### OPTION 01
Trusted launch

- **OPTION 01:** Trusted Launch protects the boot chain with Secure Boot and vTPM, 
helping defend against `bootkits` and `rootkits`. It does not provide the hardware-based 
protection for data in use that the question requires. [2][3]

---

### OPTION 03
Standard

- **OPTION 03:** A Standard VM does not provide the confidential-computing hardware boundary 
needed to prevent privileged host access to data while it is being processed. It therefore 
fails the new memory-protection requirement. [1]

---

### OPTION 04
Trusted launch with Azure Disk Encryption enabled on the OS and data disks

- **OPTION 04:** Trusted Launch provides boot protections, and Azure Disk Encryption encrypts the OS and data disks. Disk encryption protects data on disk, not the VM's memory while the workload is running, so this combination does 
not meet the in-use data requirement. [2][4]

---

### References

1. [Azure Confidential Computing overview](https://learn.microsoft.com/en-us/azure/confidential-computing/overview) — Defines confidential computing as hardware-based protection for data in use and describes protection against access by cloud operators.

2. [About Azure confidential VMs](https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-overview) — Describes the hardware-enforced isolation, dedicated vTPM, Secure Boot support, and compatibility requirements of Confidential VMs.

3. [Trusted Launch for Azure VMs](https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch) — Describes Trusted Launch's protection for the VM boot chain, including Secure Boot and vTPM.

4. [Overview of managed disk encryption options](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-overview) — Describes Azure Disk Encryption as protection for OS and data disks.

---

# What is Microsoft Confidential VM?

A Microsoft Confidential VM (CVM) is a specialized Azure virtual machine that protects 
your data while it is actively being processed (data in use) using: 

1. `hardware-based memory encryption` and 
2. `trusted execution environments (TEEs)`. 

[1] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-faq), 
[2] (https://learn.microsoft.com/en-us/azure/azure-sovereign-clouds/public/confidential-computing)

## Key Features and Security Mechanisms

- Memory Encryption: 
Encrypts the entire virtual machine's memory and processor state via hardware technologies 
like `AMD SEV-SNP` or `Intel TDX`. 

[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/general-purpose/dcesv6-series), 
[2] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-faq)

- Exclusion of Cloud Operators: 
Prevents the underlying hypervisor, host operating system, and cloud administrators from 
reading or tampering with data inside the VM's memory. 

[1] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-overview), 
[2] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-faq), 
[3] (https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/general-purpose/dcesv6-series)

- Guest Attestation & `vTPM`: 
Features a dedicated `virtual Trusted Platform Module (vTPM 2.0)` and cryptographic attestation 
reports that verify the health and firmware integrity of the platform before the VM is allowed to boot. 

[1] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-faq)

- Disk and State Encryption: 
Protects operating system disks, temporary disks, and `guest state files (VMGS)`, with options 
for guest-side confidential data disk encryption. 

[1] (https://techcommunity.microsoft.com/blog/azureconfidentialcomputingblog/extending-confidential-computing-protection-to-your-data-disks/4572620)

- Lift-and-Shift Compatibility: 
Designed to run existing applications and enterprise workloads seamlessly without requiring 
code changes or software re-architecting. 

[1] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-faq), 
[2] (https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/general-purpose/dcesv6-series)

## Common Use Cases

• Regulated Industries: Protecting sensitive data in finance, healthcare, and government sectors. [1] (https://azure.microsoft.com/en-gb/solutions/confidential-compute)
• Multiparty Analytics: Allowing multiple organizations to run AI or machine learning models and analyze shared datasets without exposing the raw data to each other. [1] (https://azure.microsoft.com/en-gb/solutions/confidential-compute)
• Sensitive Databases & Apps: Running secure workloads such as SQL Server with always-encrypted enclaves, Azure Databricks, or confidential container pools on Azure Kubernetes Service (AKS). [1] (https://learn.microsoft.com/en-us/azure/confidential-computing/overview-azure-products)
For more technical details and hardware specifications, check the About Azure confidential VMs Guide. [1] (https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-overview)

---

# What is Microsoft Trusted launch?

Microsoft Trusted Launch is a security feature for Generation 2 virtual machines (VMs) 
that protects against advanced and persistent threats like: 

- bootkits 
- rootkits 
- kernel-level malware 

It is enabled by default for new Generation 2 VMs and scale sets on Azure. 

[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch), 
[2] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch-faq), 
[3] (https://learn.microsoft.com/en-us/azure/aks/use-trusted-launch)

## Key Components

- Secure Boot: 
Ensures that only properly signed operating systems, bootloaders, and drivers can load during the startup sequence. 

[1] (https://www.youtube.com/watch?v=CQqu_rTSi0Q)

- Virtual Trusted Platform Module (vTPM): 
Provides a dedicated, isolated `TPM 2.0-compliant secure vault inside the VM` to store keys and measurements. 

[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch)

- Measured Boot & Remote Attestation: 
Measures the entire boot chain (UEFI, OS, system, and drivers) and allows cloud-based attestation to 
cryptographically verify that the VM booted safely. If a check fails, `Microsoft Defender for Cloud` 
can issue integrity alerts. 

[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch)

## Core Benefits

- No Extra Cost: 
Trusted Launch does not increase the pricing of underlying Azure VMs. 

[1] (https://docs.azure.cn/en-us/virtual-machines/trusted-launch)

- Wide Support: 
It `works across x64 and Arm64 architectures`, supporting major Linux distributions 
such as `Ubuntu, Debian, Red Hat/AlmaLinux, and Azure Linux)` as well as `Windows and Windows Server`. 

[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch), 
[2] (https://docs.azure.cn/en-us/virtual-machines/trusted-launch)

- Expansion to On-Premises: 
Similar capabilities are also available for hybrid environments through 
`Trusted Launch for Azure Local VMs enabled by Azure Arc and Windows Server`. 

[1] (https://techcommunity.microsoft.com/blog/windowsservernewsandbestpractices/announcing-trusted-launch-for-virtual-machines-for-windows-server-insiders/4537082), 

[2] (https://learn.microsoft.com/en-us/azure/azure-local/manage/trusted-launch-vm-overview?view=azloc-2610)

For deployment steps and detailed compatibility matrices, check the official Microsoft Learn Trusted Launch Guide. 
[1] (https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch)

---

# What is Microsoft Trusted launch?

---