[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q07

A healthcare company runs a workload processing highly sensitive patient records on an Azure virtual machine. The workload already relies on Secure Boot and vTPM to protect against boot-level rootkits. A new compliance requirement states that the VM's memory contents must be encrypted using hardware-based technology, so that even someone with privileged access to the underlying host cannot inspect the VM's memory while the workload is running.

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

## Answer and rationale

**Correct answer: OPTION 02 — Confidential VM.**

Select the `Confidential VM` security type and use a supported confidential VM size and image. Azure Confidential VMs use hardware-based isolation to protect data while it is being processed, including protection from access by the hypervisor and host operating system. They also provide a dedicated vTPM and support Secure Boot, meeting the existing boot-integrity requirements as well as the new requirement to protect memory contents at runtime. [1][2]

Configure Secure Boot and vTPM for the selected VM, as required by the image and deployment. Confidential VM features and supported sizes/images vary, so verify compatibility before deployment. [2]

### Why the other options are not correct

### OPTION 01
Trusted launch

- **OPTION 01:** Trusted Launch protects the boot chain with Secure Boot and vTPM, helping defend against bootkits and rootkits. It does not provide the hardware-based protection for data in use that the question requires. [2][3]

---

### OPTION 03
Standard

- **OPTION 03:** A Standard VM does not provide the confidential-computing hardware boundary needed to prevent privileged host access to data while it is being processed. It therefore fails the new memory-protection requirement. [1]

---

### OPTION 04
Trusted launch with Azure Disk Encryption enabled on the OS and data disks

- **OPTION 04:** Trusted Launch provides boot protections, and Azure Disk Encryption encrypts the OS and data disks. Disk encryption protects data on disk, not the VM's memory while the workload is running, so this combination does not meet the in-use data requirement. [2][4]

---

### References

1. [Azure Confidential Computing overview](https://learn.microsoft.com/en-us/azure/confidential-computing/overview) — Defines confidential computing as hardware-based protection for data in use and describes protection against access by cloud operators.
2. [About Azure confidential VMs](https://learn.microsoft.com/en-us/azure/confidential-computing/confidential-vm-overview) — Describes the hardware-enforced isolation, dedicated vTPM, Secure Boot support, and compatibility requirements of Confidential VMs.
3. [Trusted Launch for Azure VMs](https://learn.microsoft.com/en-us/azure/virtual-machines/trusted-launch) — Describes Trusted Launch's protection for the VM boot chain, including Secure Boot and vTPM.
4. [Overview of managed disk encryption options](https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-overview) — Describes Azure Disk Encryption as protection for OS and data disks.
---