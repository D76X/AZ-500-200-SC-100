
[AZ-700: Designing and Implementing Microsoft Azure Networking Solutions Microsoft Learn Course 11 videos Last updated on 20 May 2026](https://www.youtube.com/playlist?list=PLahhVEj9XNTdToCofwwCsHyu-PkVztyz7)  

---

# Episode 2

[Introduction to Azure Virtual Networks | AZ-700 | Episode 2  Microsoft Learn](https://www.youtube.com/watch?v=M-Uz0skhb-E)

Learning Objectives – IP Addressing for Resources

Review Virtual Network Fundamentals

- Review IP Addressing Fundamentals
- Plan for Azure IP Addressing
- Demonstration: Create Virtual Networks
- Review Examples of Public IP Addressing
- Demonstration: Create Public IP Addresses

Exam Objectives
Design and implement core networking infrastructure (25-30%)
- Design and implement IP addressing for Azure resources
- Design and implement name resolution
- Design and implement VNet connectivity and routing


## Review Virtual Network Fundamentals

- Virtual Network (VNet): The main boundary
A large private IP address space (e.g., 10.0.0.0/16) representing your isolated cloud network.

- Subnets: Smaller divisions within the VNet 
(e.g., 10.0.1.0/24, 10.0.2.0/24) for grouping resources, often public (with gateways) or private (for databases).

- IP Addresses: Individual addresses 
assigned to resources (VMs, databases) within subnets, following the subnet's 
range (e.g., 10.0.1.4, 10.0.2.5).

- CIDR Notation: /16, /24 notation showing network size and available IP addresses.

- Not all IP addresses are available for assignment.

- The first four and the last IP address in every subnet is reserved for internal platform use (network/broadcast, default gateway, Azure DNS).

- Multicast, Broadcast, Loopback, Link-Local, and Internal DNS IP address ranges are not available for assignment.

- `RFC 1918` defines specific `IPv4 address ranges for private networks`. These addresses are not routed on the public internet: `10.`, `172.`, `192.`

## Plan for Azure IP aggressing

- Ensure address spaces don't overlap  

- Use a few large virtual networks instead of multiple smaller ones  

- Decide if your IP addresses should be private or public  

- Decide if the IP addresses should be statically or dynamically allocated - consider using separate subnets  

- Subnets shouldn't cover the entire address space of the virtual network  

- Never manage IP addresses from within the virtual machine  

---

# Episode 1

[Course Introduction | AZ-700 | Episode 1 Microsoft Learn](https://www.youtube.com/watch?v=Z3gPmFw0b4E&list=PLahhVEj9XNTdToCofwwCsHyu-PkVztyz7&index=2&t=53s)  

# About this series

## Prerequisites

Successful Azure network engineers should have experience 
creating and managing compute, storage, and networking resources in Azure.

## Azure Network Engineer Role

Network engineers have subject matter expertise in planning, implementing, and 
managing Azure networking solutions. 

This includes 

- core network infrastructure, 
- hybrid connectivity, 
- application delivery services, 
- private access to Azure services, and 
- network security

As an Azure network engineer, your responsibilities include 

- optimizing performance, 
- resiliency, 
- scale, and 
- security of Azure networking solutions. 

You deploy the solutions by using the Azure portal, the command line, and templates. 
You proactively monitor network environments to identify issues and minimize risk.

## Series Overview

- Introduction to Azure Virtual Networks
- Design and Implement Hybrid Networking
- Design and Implement Express Route
- Load balance non-HTTP(S) traffic
- Load balance HTTP(S) traffic
- Design and Implement Network Security
- Design and Implement private access to Azure Services
- Design and Implement Network Monitoring

---
