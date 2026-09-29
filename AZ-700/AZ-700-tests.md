# AZ-700 Practice Tests

Original, unofficial scenario-based practice for **Exam AZ-700: Designing and Implementing Microsoft Azure Networking Solutions**. These questions are not copied from the live exam.

> **Exam alignment:** The current Microsoft Learn study guide lists five domains: core networking infrastructure (25–30%); connectivity services (20–25%); application delivery services (15–20%); private access to Azure services (10–15%); and Azure network security services (15–20%). The study guide was updated July 27, 2026. Check the [official exam page](https://learn.microsoft.com/en-us/credentials/certifications/azure-network-engineer-associate/) and [study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-700) for subsequent changes.
>
> Select the number of answers specified. Unless stated otherwise, choose the single best answer. Each question includes its rationale, explanations for the distractors, and Microsoft Learn references. This unofficial study aid does not guarantee exam coverage. Validate region, SKU, service, and feature availability before deployment.
# AZ-700 Practice Tests

Original, unofficial scenario-based practice for **Exam AZ-700: Designing and Implementing Microsoft Azure Networking Solutions**. These questions are not copied from the live exam.

> **Exam alignment:** The current Microsoft Learn study guide lists five domains: core networking infrastructure (25–30%); connectivity services (20–25%); application delivery services (15–20%); private access to Azure services (10–15%); and Azure network security services (15–20%). The guide indicates it was updated July 27, 2026. Check the [official study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-700) for subsequent changes.
>
> Select the number of answers specified. Unless stated otherwise, choose the single best answer. Each question includes its rationale, explanations for the distractors, and Microsoft Learn references. This unofficial study aid does not guarantee exam coverage. Validate region, SKU, service, and feature availability before deployment.

## Domain 1: Design and implement core networking infrastructure

### Question 1 - Plan nonoverlapping address spaces

A company connects its on-premises network to Azure and plans to peer two VNets. The on-premises ranges are `10.20.0.0/16` and `10.30.0.0/16`. Which VNet address-space plan avoids routing conflicts and allows future subnet growth?

A. Assign each VNet a nonoverlapping private CIDR range that does not overlap either on-premises range, then allocate appropriately sized subnets
B. Reuse `10.20.0.0/16` in Azure because VNet peering performs address translation automatically
C. Assign every subnet in both VNets `0.0.0.0/0`
D. Give the VNets identical prefixes and rely on NSGs to resolve duplicate routes

**Correct: A.** Connected networks need nonoverlapping address spaces for unambiguous routing. Reserve suitable space for current subnets and planned growth. Peering and VPN/ExpressRoute do not automatically translate overlapping CIDRs. [R1][R2]

**Why the others are wrong:** B overlapping address ranges prevent normal VNet peering and create ambiguous hybrid routes. [R1][R2] C `0.0.0.0/0` is a default route, not a usable private VNet address plan. [R1] D NSGs filter traffic but do not translate addresses or resolve route-prefix conflicts. [R2][R3]

**References:** [R1] [Plan virtual networks](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-vnet-plan-design-arm); [R2] [Azure VNet peering overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 2 - Resolve Azure and on-premises private DNS

Azure workloads must resolve private endpoint names using a private DNS zone. On-premises clients must resolve those same names, and Azure clients must resolve selected on-premises names. The organization wants a managed DNS forwarding service rather than DNS VMs. Which design best meets the requirement?

A. Use Azure DNS Private Resolver with inbound and outbound endpoints and appropriate forwarding rules; link the private DNS zone to the relevant VNets
B. Create a public DNS zone for private endpoint records and publish RFC1918 addresses
C. Configure Azure Traffic Manager to forward DNS queries between Azure and on-premises
D. Add static host entries to each Azure VM and on-premises client

**Correct: A.** DNS Private Resolver provides managed inbound/outbound DNS resolution between Azure VNets and external DNS environments. Private DNS zone links provide resolution for linked VNets; forwarding rulesets direct queries to the appropriate DNS servers. [R1][R2]

**Why the others are wrong:** B public DNS does not provide the required private resolution boundary and can expose internal naming information. [R2] C Traffic Manager routes DNS responses among service endpoints; it is not a conditional DNS forwarder between private DNS environments. [R3] D static host entries are difficult to maintain and do not provide managed, scalable name resolution. [R1]

**References:** [R1] [Azure DNS Private Resolver overview](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R2] [Azure Private DNS zones](https://learn.microsoft.com/en-us/azure/dns/private-dns-privatednszone); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 3 - Enable spoke-to-spoke transit through a hub

Spoke VNets are peered to a hub VNet. The hub has a VPN gateway connected to on-premises, and spokes must use that gateway to reach on-premises. Which peering configuration is required?

A. Enable gateway transit on the hub peering and use remote gateways on each spoke peering
B. Enable remote gateways on the hub and gateway transit on each spoke
C. Enable VNet peering only; peering automatically shares the hub gateway with every spoke
D. Deploy an NSG in each spoke that advertises the gateway routes

**Correct: A.** The VNet containing the gateway advertises gateway transit; the peered VNet configures use of the remote gateway. This enables spokes to use the hub gateway, subject to peering and gateway constraints. [R1]

**Why the others are wrong:** B reverses the gateway transit and remote gateway settings. [R1] C peering alone does not automatically make a gateway available to the peer; the gateway transit options must be configured. [R1] D NSGs filter traffic and do not advertise routes or share a virtual network gateway. [R1][R2]

**References:** [R1] [VNet peering gateway transit](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 4 - Force outbound traffic through a network virtual appliance

A subnet's outbound traffic must pass through a centralized network virtual appliance (NVA) before reaching the internet. The organization requires explicit, auditable route control. What should you configure?

A. Associate a route table with the subnet and add a `0.0.0.0/0` user-defined route with next-hop type Virtual appliance and the NVA private IP
B. Add an inbound NSG rule allowing the NVA's subnet
C. Create a private DNS zone pointing to the NVA
D. Add an Azure Load Balancer probe for `0.0.0.0/0`

**Correct: A.** A user-defined route on the subnet can direct the default route to a virtual appliance next hop, subject to correct NVA forwarding and return routing. [R1]

**Why the others are wrong:** B NSGs permit or deny traffic but do not set the next hop. [R1][R2] C DNS resolves names and does not steer IP packets through an NVA. [R3] D Load Balancer probes monitor backend health and do not configure subnet routing. [R4]

**References:** [R1] [Azure virtual network UDR overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview); [R2] [NSG overview](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R4] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).

### Question 5 - Provide predictable outbound public IP addresses

A subnet contains multiple virtual machines that require outbound internet access. External partners allowlist a small, stable set of public source IPs. No inbound connections are required. Which service is the best fit?

A. Azure NAT Gateway associated with the workload subnet, using a static public IP or public IP prefix
B. A public IP address on every VM
C. Azure Traffic Manager with a priority routing method
D. An internal Standard Load Balancer

**Correct: A.** NAT Gateway provides managed outbound internet connectivity for subnet resources and predictable SNAT source addresses using attached public IPs or prefixes. It is not an inbound service. [R1]

**Why the others are wrong:** B public IPs on every VM increase exposure and do not centralize the required small stable source-IP set. [R1] C Traffic Manager performs DNS-based endpoint selection and does not provide SNAT. [R2] D an internal load balancer handles private inbound distribution and does not provide internet egress. [R3]

**References:** [R1] [Azure NAT Gateway overview](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R2] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R3] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).

### Question 6 - Manage network connectivity across many VNets

A central network team must create connectivity configurations across VNets in multiple subscriptions and apply consistent network group membership and connectivity rules. Which service is designed for centralized VNet connectivity management?

A. Azure Virtual Network Manager
B. Azure DNS Private Resolver
C. Azure Traffic Manager
D. Azure Network Watcher IP flow verify

**Correct: A.** Azure Virtual Network Manager centralizes management of virtual network connectivity and security configurations across subscriptions and regions within its scope. [R1]

**Why the others are wrong:** B Private Resolver handles DNS forwarding, not VNet connectivity topology. [R2] C Traffic Manager routes DNS responses for application endpoints, not VNet-to-VNet connectivity. [R3] D IP flow verify diagnoses NSG rule decisions and does not configure enterprise connectivity. [R4]

**References:** [R1] [Azure Virtual Network Manager overview](https://learn.microsoft.com/en-us/azure/virtual-network-manager/overview); [R2] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R3] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [IP flow verify](https://learn.microsoft.com/en-us/azure/network-watcher/ip-flow-verify-overview).

### Question 7 - Exchange routes with an NVA dynamically

An NVA in a hub VNet must exchange BGP routes dynamically with Azure virtual networks, avoiding manually maintained user-defined routes for prefixes learned from the NVA. Which Azure service is intended for this integration?

A. Azure Route Server, peered with the NVA and configured with the required BGP settings
B. Azure NAT Gateway
C. Azure DNS Private Resolver
D. Azure Traffic Manager

**Correct: A.** Azure Route Server enables dynamic route exchange between network virtual appliances and Azure virtual networks using BGP. NVA and route-server configuration must satisfy the documented peering and routing requirements. [R1]

**Why the others are wrong:** B NAT Gateway provides outbound SNAT and does not exchange routes. [R2] C Private Resolver forwards DNS queries, not BGP routes. [R3] D Traffic Manager directs DNS clients to endpoints and does not participate in BGP. [R4]

**References:** [R1] [Azure Route Server overview](https://learn.microsoft.com/en-us/azure/route-server/overview); [R2] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R3] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 8 - Diagnose an unexpected network path

A VM cannot reach a destination. The operator needs to determine which effective route Azure selects and whether an NSG permits a specific five-tuple. Which pair of Network Watcher tools should be used? **Select two.**

A. Next hop to determine the selected next hop for traffic from a VM NIC
B. IP flow verify to evaluate whether an NSG rule allows or denies the specified flow
C. Connection Monitor to rewrite the VM subnet's route table automatically
D. Traffic Analytics to change the effective NSG priority
E. Packet capture to create a new route advertisement

**Correct: A, B.** Next hop identifies the route selected for a destination from a VM; IP flow verify evaluates NSG rules for a specified flow. Together they help distinguish routing from filtering problems. [R1][R2]

**Why the others are wrong:** C Connection Monitor tests connectivity and helps observe end-to-end reachability; it does not rewrite route tables. [R3] D Traffic Analytics visualizes flow data and does not change NSG priority. [R4] E packet capture collects traffic for analysis and does not advertise routes. [R1]

**References:** [R1] [Azure Network Watcher overview](https://learn.microsoft.com/en-us/azure/network-watcher/network-watcher-overview); [R2] [IP flow verify](https://learn.microsoft.com/en-us/azure/network-watcher/ip-flow-verify-overview); [R3] [Connection Monitor overview](https://learn.microsoft.com/en-us/azure/network-watcher/connection-monitor-overview); [R4] [Traffic Analytics](https://learn.microsoft.com/en-us/azure/network-watcher/traffic-analytics).

## Domain 2: Design, implement, and manage connectivity services

### Question 9 - Connect a branch office to Azure over the internet

A branch office must connect to an Azure VNet using an IPsec tunnel over the public internet. The on-premises VPN device supports route-based VPN and BGP. Which Azure design is appropriate?

A. Deploy an Azure VPN Gateway with a route-based VPN, configure the local network gateway and connection with matching IPsec/IKE settings, and enable BGP if dynamic route exchange is required
B. Deploy Azure ExpressRoute only; it uses the public internet for the IPsec tunnel
C. Configure Azure Traffic Manager with a private DNS zone
D. Use VNet peering to connect the on-premises VPN device directly to the Azure VNet

**Correct: A.** VPN Gateway provides site-to-site IPsec connectivity over the internet. A route-based gateway supports flexible routing and BGP where needed; both peers must use compatible settings. [R1][R2]

**Why the others are wrong:** B ExpressRoute provides a private connectivity path through a connectivity provider and is not itself an IPsec VPN over the public internet. [R3] C Traffic Manager and private DNS provide neither a VPN tunnel nor hybrid routing. [R4] D VNet peering connects Azure VNets; it does not terminate an on-premises VPN tunnel. [R5]

**References:** [R1] [About VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways); [R2] [Site-to-site VPN Gateway configuration](https://learn.microsoft.com/en-us/azure/vpn-gateway/tutorial-site-to-site-portal); [R3] [ExpressRoute overview](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction); [R4] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [VNet peering overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview).

### Question 10 - Provide resilient site-to-site VPN connectivity

A business-critical branch uses a site-to-site VPN to Azure. It must tolerate a failure of one VPN gateway instance, and the on-premises VPN device supports two tunnels. Which design should be selected?

A. Use a VPN Gateway configuration that supports active-active or zone-redundant high availability, and configure the corresponding redundant tunnels on the on-premises device
B. Deploy one nonredundant VPN gateway and rely on a DNS alias
C. Configure a single user-defined route to a VM acting as a VPN gateway
D. Use a point-to-site VPN profile on a single administrator laptop

**Correct: A.** VPN Gateway supports high-availability options, including active-active and zone-redundant configurations for eligible SKUs/regions. The customer-side device must establish the matching redundant tunnels. [R1][R2]

**Why the others are wrong:** B DNS does not make a single gateway instance redundant. [R1] C a VM NVA could be designed as a VPN appliance, but a single VM and route do not satisfy the managed-gateway HA requirement. [R1] D P2S is for individual client connections, not redundant branch-to-VNet connectivity. [R3]

**References:** [R1] [VPN Gateway highly available configurations](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-highlyavailable); [R2] [About VPN Gateway](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways); [R3] [Point-to-site VPN overview](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about).

### Question 11 - Provide remote-user VPN access

Remote employees need to initiate encrypted connections from individual Windows clients to an Azure VNet. The organization wants to authenticate users with Microsoft Entra ID and distribute a VPN client profile. Which solution meets the requirement?

A. Point-to-site VPN on an eligible Azure VPN Gateway, using a supported tunnel and Microsoft Entra authentication configuration
B. Site-to-site VPN with a local network gateway for each employee laptop
C. ExpressRoute Global Reach
D. Azure Front Door with a private origin

**Correct: A.** P2S VPN provides client-initiated VPN connectivity from individual devices to an Azure VNet. Supported tunnel types, gateway SKUs, authentication, and client profile requirements must be verified for the tenant and client platform. [R1]

**Why the others are wrong:** B S2S connects a branch or network gateway, not individual remote-user VPN clients. [R1][R2] C Global Reach connects ExpressRoute circuits and does not provide a client VPN. [R3] D Front Door is a global application delivery service and does not establish a user network tunnel. [R4]

**References:** [R1] [Point-to-site VPN overview](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-about); [R2] [VPN Gateway overview](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways); [R3] [ExpressRoute Global Reach](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-global-reach); [R4] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview).

### Question 12 - Select an ExpressRoute connectivity model

An enterprise needs a private, dedicated connectivity path from its offices to Microsoft cloud services through a connectivity provider. It must carry private VNet traffic and also access Microsoft public services such as Microsoft 365 using the appropriate peering. Which design is appropriate?

A. Provision an ExpressRoute circuit with the required private peering and, if supported and required, Microsoft peering; choose a connectivity model and circuit SKU/tier matching topology and bandwidth
B. Create only a VPN Gateway; VPN is a private provider circuit
C. Configure VNet peering between the office router and an Azure VNet
D. Use Azure Traffic Manager to advertise Microsoft service routes

**Correct: A.** ExpressRoute provides private connectivity via an ExpressRoute partner or ExpressRoute Direct. Private peering connects to Azure VNets; Microsoft peering is for supported Microsoft public services and requires the relevant design and configuration. [R1][R2]

**Why the others are wrong:** B VPN Gateway creates IPsec tunnels over the internet and is not a dedicated ExpressRoute provider circuit. [R3] C VNet peering connects Azure VNets, not an office router. [R4] D Traffic Manager uses DNS to route endpoint requests; it does not advertise BGP routes or provide private connectivity. [R5]

**References:** [R1] [Azure ExpressRoute overview](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-introduction); [R2] [ExpressRoute connectivity models](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models); [R3] [VPN Gateway overview](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways); [R4] [VNet peering](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview); [R5] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 13 - Connect ExpressRoute circuits in different regions

A multinational company has ExpressRoute circuits in two locations. It needs private connectivity between the on-premises networks attached to those circuits through Microsoft's network, without routing the intersite traffic over the public internet. Which feature is designed for this?

A. ExpressRoute Global Reach, subject to circuit, provider, and regional availability requirements
B. ExpressRoute Microsoft peering alone
C. Azure NAT Gateway
D. Azure Traffic Manager

**Correct: A.** Global Reach links ExpressRoute circuits so on-premises networks can communicate over Microsoft's network, subject to supported circuit and connectivity requirements. [R1]

**Why the others are wrong:** B Microsoft peering provides access to supported Microsoft public services; it does not itself connect the enterprise's two on-premises circuits. [R1] C NAT Gateway provides outbound internet SNAT for Azure subnets. [R2] D Traffic Manager provides DNS-based application endpoint routing. [R3]

**References:** [R1] [ExpressRoute Global Reach](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-global-reach); [R2] [Azure NAT Gateway overview](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 14 - Design a hub-and-spoke WAN for many branches

A retailer has dozens of branches, Azure VNets in multiple regions, and both VPN and ExpressRoute connectivity. The network team wants centrally managed hubs and global transit between branches and Azure. Which service is best suited?

A. Azure Virtual WAN with virtual hubs and appropriately sized VPN/ExpressRoute gateways
B. A separate VNet peering mesh among every branch and every Azure VNet
C. Azure DNS Private Resolver
D. Azure Application Gateway

**Correct: A.** Virtual WAN provides a managed hub-and-spoke network service for branch, VPN, ExpressRoute, and VNet connectivity, including global transit through virtual hubs. [R1][R2]

**Why the others are wrong:** B full mesh peering becomes difficult to scale and does not directly onboard branch VPN devices as managed Virtual WAN connections. [R1][R3] C Private Resolver handles DNS forwarding, not WAN connectivity. [R4] D Application Gateway is a regional Layer 7 application delivery service, not a WAN hub. [R5]

**References:** [R1] [Azure Virtual WAN overview](https://learn.microsoft.com/en-us/azure/virtual-wan/virtual-wan-about); [R2] [Global transit network architecture](https://learn.microsoft.com/en-us/azure/virtual-wan/virtual-wan-global-transit-network-architecture); [R3] [VNet peering overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview); [R4] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R5] [Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview).
### Question 15 - Improve ExpressRoute data-path performance

A company has an ExpressRoute connection with private peering. Traffic between on-premises and Azure VMs must avoid unnecessary gateway processing to reduce network hops and improve throughput. Which feature should be evaluated, subject to gateway, circuit, and destination support?

A. ExpressRoute FastPath
B. ExpressRoute Global Reach
C. Azure Traffic Manager Priority routing
D. Azure NAT Gateway

**Correct: A.** FastPath allows supported ExpressRoute traffic to bypass the ExpressRoute virtual network gateway data path and connect more directly to supported VNet resources, improving performance. Its availability and limitations depend on the circuit, gateway SKU, destination, and topology. [R1]

**Why the others are wrong:** B Global Reach connects ExpressRoute circuits so on-premises networks can communicate over Microsoft's network; it is not the ExpressRoute gateway-bypass feature. [R2] C Traffic Manager directs DNS queries among endpoints and does not optimize the ExpressRoute packet path. [R3] D NAT Gateway provides outbound SNAT for Azure subnets, not ExpressRoute gateway bypass. [R4]

**References:** [R1] [ExpressRoute FastPath features and limitations](https://learn.microsoft.com/en-us/azure/expressroute/about-fastpath); [R2] [ExpressRoute Global Reach](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-global-reach); [R3] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview).

## Domain 3: Design and implement application delivery services

### Question 16 - Balance HTTP traffic globally across regions

A public web application runs in two Azure regions. The design needs a global anycast entry point, edge acceleration, health-based routing, and Web Application Firewall integration. Which service should be selected?

A. Azure Front Door with an appropriate tier and WAF policy
B. Azure Load Balancer in one region
C. Azure Traffic Manager only, because it inspects HTTP requests at the edge
D. Azure VPN Gateway

**Correct: A.** Front Door is a global Layer 7 application entry point using Microsoft's edge network; it supports acceleration, health-based origin routing, TLS, and WAF integration. Select the tier based on required features. [R1][R2]

**Why the others are wrong:** B Load Balancer is regional Layer 4 and does not provide a global HTTP edge or WAF. [R3] C Traffic Manager routes through DNS responses and does not proxy or inspect each HTTP request at the edge. [R4] D VPN Gateway connects private networks and is not an application delivery service. [R5]

**References:** [R1] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R2] [WAF on Azure Front Door](https://learn.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overview); [R3] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R4] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [VPN Gateway overview](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways).

### Question 17 - Route HTTPS by host and URL path in one region

A regional web application must route `api.contoso.com` to one backend pool and `/images/*` requests to another pool. The ingress service must terminate TLS and perform health probing. Which service is the best fit?

A. Azure Application Gateway with listeners, rules, backend pools, health probes, and path-based routing
B. Azure Load Balancer with TCP rules only
C. Azure Traffic Manager with weighted DNS routing
D. Azure NAT Gateway

**Correct: A.** Application Gateway provides regional Layer 7 HTTP(S) load balancing, host/path-based routing, TLS termination, listeners, probes, and backend settings. [R1][R2]

**Why the others are wrong:** B Load Balancer operates at Layer 4 and cannot route by hostname or URL path. [R3] C Traffic Manager chooses endpoints through DNS; it does not inspect each request or terminate TLS as an application proxy. [R4] D NAT Gateway provides outbound SNAT, not inbound application routing. [R5]

**References:** [R1] [Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview); [R2] [Application Gateway configuration](https://learn.microsoft.com/en-us/azure/application-gateway/configuration-overview); [R3] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R4] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [Azure NAT Gateway overview](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview).

### Question 18 - Distribute UDP traffic within a region

A service receives UDP traffic on a fixed port from clients and runs on multiple healthy VMs in one region. It requires Layer 4 distribution and inbound NAT rules for administrative access. Which service should be used?

A. Azure Standard Load Balancer with a load-balancing rule and required inbound NAT rules
B. Application Gateway with a path-based HTTP rule
C. Azure Front Door with URL rewrite
D. Traffic Manager with a weighted profile

**Correct: A.** Standard Load Balancer operates at Layer 4 and supports TCP/UDP load-balancing rules and inbound NAT rules for individual backend endpoints. [R1]

**Why the others are wrong:** B Application Gateway is a Layer 7 HTTP(S) proxy and is not the appropriate UDP load balancer. [R2] C Front Door provides global HTTP(S) delivery, not arbitrary UDP load balancing. [R3] D Traffic Manager uses DNS responses and does not proxy UDP connections. [R4]

**References:** [R1] [Azure Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview); [R2] [Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview); [R3] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R4] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 19 - Choose DNS-level failover for non-HTTP endpoints

A service exposes non-HTTP endpoints in two regions. Clients can use DNS-based failover and should be directed to the highest-priority healthy endpoint. The service does not need a proxy, TLS termination, or Layer 7 inspection. Which service fits?

A. Azure Traffic Manager using the Priority routing method and endpoint health monitoring
B. Azure Front Door with a WAF custom rule
C. Azure Application Gateway with path-based routing
D. Azure Firewall with an application rule

**Correct: A.** Traffic Manager is a DNS-based global traffic-routing service. Priority routing can direct DNS queries to the highest-priority endpoint considered online by health monitoring. DNS caching and client resolver behavior affect failover time. [R1]

**Why the others are wrong:** B Front Door is a global HTTP(S) proxy and introduces application delivery capabilities not required for the non-HTTP DNS-routing scenario. [R2] C Application Gateway is a regional Layer 7 HTTP(S) proxy. [R3] D Azure Firewall filters network traffic but does not provide DNS priority routing between service endpoints. [R4]

**References:** [R1] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R2] [Azure Front Door overview](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview); [R3] [Application Gateway overview](https://learn.microsoft.com/en-us/azure/application-gateway/overview); [R4] [Azure Firewall overview](https://learn.microsoft.com/en-us/azure/firewall/overview).

### Question 20 - Insert a network virtual appliance transparently

A security appliance must inspect traffic between a load balancer and backend virtual machines, while minimizing changes to the application configuration. Which Azure service is designed to chain an NVA transparently in the data path?

A. Azure Gateway Load Balancer, paired with a supported public or internal load-balancing design
B. Azure Traffic Manager
C. Azure DNS Private Resolver
D. Azure NAT Gateway

**Correct: A.** Gateway Load Balancer provides a service-chaining pattern to insert and scale NVAs transparently in the traffic path using supported load-balancer configurations. [R1]

**Why the others are wrong:** B Traffic Manager routes through DNS and does not insert appliances in a packet path. [R2] C Private Resolver handles DNS queries rather than inline inspection. [R3] D NAT Gateway provides outbound source translation and does not chain an NVA. [R4]

**References:** [R1] [Azure Gateway Load Balancer overview](https://learn.microsoft.com/en-us/azure/load-balancer/gateway-overview); [R2] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R3] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview); [R4] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview).

### Question 21 - Secure a private origin behind Front Door

A web application is published through Azure Front Door. The origin must not be reachable directly from the public internet; traffic should reach the origin over a private connection where supported. Which design is appropriate?

A. Configure Azure Front Door origin Private Link for a supported origin, approve the private endpoint connection, and restrict the origin's public access as appropriate
B. Publish the origin's public IP and rely only on an unguessable DNS name
C. Add an Azure Traffic Manager profile in front of the origin and assume it blocks direct access
D. Add an NSG to the Front Door-managed edge network

**Correct: A.** Front Door supports Private Link connectivity to supported origins, helping secure origin access without relying on public reachability. Configure the origin and connection approval per the supported service and tier. [R1][R2]

**Why the others are wrong:** B obscurity does not prevent direct origin access. [R1] C Traffic Manager provides DNS routing and does not proxy or block direct origin requests. [R3] D customers do not attach an NSG to Front Door's managed edge network; NSGs apply to supported VNet subnets and NICs. [R4]

**References:** [R1] [Azure Front Door Private Link](https://learn.microsoft.com/en-us/azure/frontdoor/private-link); [R2] [Azure Private Link overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview); [R3] [Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

## Domain 4: Design and implement private access to Azure services

### Question 22 - Privately connect a VNet to Azure Storage

A workload in an Azure VNet must access a storage account through a private IP address. The storage account's public endpoint must be disabled, and storage DNS must resolve to the private address from linked VNets. Which design meets the requirement?

A. Create a private endpoint for the required Storage subresource, link/configure the private DNS zone, and disable public network access
B. Enable a service endpoint and leave the public endpoint accessible from all networks
C. Add a public DNS A record that points to the storage account's private IP
D. Create a NAT Gateway and configure its public IP as the storage private endpoint

**Correct: A.** A private endpoint maps a supported service to a private IP in a VNet. Private DNS integration resolves the service name through the private endpoint. Disabling public network access closes the public path when supported and configured. [R1][R2]

**Why the others are wrong:** B service endpoints secure access to a service's public endpoint; they do not assign the service a private IP in the VNet, and public access is explicitly left open. [R1][R3] C public DNS should not publish internal addresses and would not create private connectivity. [R2] D NAT Gateway provides outbound SNAT and does not create Private Link connections. [R4]

**References:** [R1] [Azure Private Link overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview); [R2] [Azure Private Endpoint DNS integration](https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-dns); [R3] [Virtual network service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview); [R4] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview).

### Question 23 - Choose a service endpoint or private endpoint

A storage account must accept traffic only from selected subnets, but the team does not require a private IP address for the service or disabling its public endpoint. It wants to preserve the service's public endpoint while restricting access to selected VNets. Which feature is the closest fit?

A. A virtual network service endpoint with the storage account network rules configured for the selected subnet
B. A Private Link service
C. Azure Front Door Private Link for the storage account
D. A public IP prefix on the subnet

**Correct: A.** A service endpoint extends a VNet's identity to supported Azure services and lets the service firewall allow selected subnets while the service continues to use its public endpoint. [R1]

**Why the others are wrong:** B Private Link service is for exposing a service hosted behind a Standard Load Balancer privately to consumers, not for limiting a consumer's access to a storage account. [R2] C Front Door Private Link secures supported Front Door origins, not general VNet-to-Storage access. [R3] D a public IP prefix allocates public addresses and does not provide service-endpoint access control. [R4]

**References:** [R1] [Virtual network service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview); [R2] [Azure Private Link service overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-service-overview); [R3] [Front Door Private Link](https://learn.microsoft.com/en-us/azure/frontdoor/private-link); [R4] [Public IP address prefixes](https://learn.microsoft.com/en-us/azure/virtual-network/ip-services/public-ip-address-prefix).

### Question 24 - Publish a privately consumable service to customers

A company hosts a service behind a Standard Load Balancer in its VNet. Customers in their own VNets must connect privately using their own private endpoint; the provider must approve each consumer connection. Which design is appropriate?

A. Publish an Azure Private Link service associated with the supported load balancer frontend, then allow consumers to create and request private endpoint connections
B. Create a service endpoint in each customer's VNet and add it to the provider's subnet NSG
C. Configure a public Traffic Manager endpoint for the service
D. Peer the provider VNet with every customer VNet and expose all provider subnets

**Correct: A.** Private Link service exposes a provider-hosted service behind a supported Standard Load Balancer to consumers, who connect using private endpoints and can require connection approval. [R1]

**Why the others are wrong:** B service endpoints let a consumer VNet access supported Azure PaaS services; they do not publish a customer's VNet service through a private endpoint. [R1][R2] C provides public DNS routing, not private consumer connectivity. [R3] D peering exposes broader network connectivity and scales poorly compared with a service-specific private endpoint. [R1][R4]

**References:** [R1] [Azure Private Link service overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-service-overview); [R2] [Virtual network service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview); [R3] [Azure Traffic Manager overview](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [VNet peering overview](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview).

### Question 25 - Control Storage access to approved destinations

A company already uses virtual network service endpoints for Azure Storage. It must restrict traffic from a designated subnet to an approved set of storage accounts, preventing that subnet from using the endpoint to access other Storage accounts. Which feature should be configured?

A. An Azure Storage service endpoint policy associated with the subnet
B. A Private Link service on every storage account
C. An NSG rule that lists all possible Storage account resource IDs
D. Azure Traffic Manager with endpoint monitoring

**Correct: A.** A service endpoint policy allows the organization to constrain Storage access through a subnet service endpoint to specified Azure Storage resources. [R1]

**Why the others are wrong:** B Private Link service is for provider-hosted services behind a load balancer, not this consumer-side Storage endpoint policy. [R2] C NSGs filter network traffic by addresses, ports, and protocols; they are not the service-endpoint resource allowlist mechanism. [R1][R3] D Traffic Manager performs DNS endpoint selection and does not control Storage access through a subnet. [R4]

**References:** [R1] [Azure service endpoint policies](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoint-policies-overview); [R2] [Private Link service overview](https://learn.microsoft.com/en-us/azure/private-link/private-link-service-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

## Domain 5: Design and implement Azure network security services

### Question 26 - Apply reusable rules to groups of application servers

A web tier and a database tier use multiple VM network interfaces. Security rules should refer to application roles rather than hard-coded IP addresses. The database tier must accept SQL traffic only from the web tier. Which design is best?

A. Associate application security groups with the VM NICs and reference the web-tier ASG as the source in an NSG rule on the database subnet/NIC
B. Create one NSG per VM with a rule allowing SQL from `0.0.0.0/0`
C. Use a public DNS zone to represent the web-tier source address
D. Assign an Azure Traffic Manager profile to the database subnet

**Correct: A.** Application security groups let rules refer to groups of NICs by workload role. NSGs then apply the necessary port/protocol restriction between the web and database tiers. [R1][R2]

**Why the others are wrong:** B permits SQL from any source and does not meet segmentation or least-privilege requirements. [R1] C DNS names do not act as NSG application security groups. [R2] D Traffic Manager routes DNS clients and does not filter subnet traffic. [R3]

**References:** [R1] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R2] [Application security groups](https://learn.microsoft.com/en-us/azure/virtual-network/application-security-groups); [R3] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 27 - Collect and analyze network flow data

A security team needs to record IP traffic metadata for virtual networks and analyze communication patterns over time. It wants a supported network flow log source for Azure Network Watcher Traffic Analytics. Which solution should be planned?

A. Configure Virtual Network flow logs for the relevant VNets and use Traffic Analytics with its supported Log Analytics and storage configuration
B. Enable Azure DNS query logging and treat it as a complete IP flow record
C. Create an NSG rule for every connection and use the rule list as a traffic history
D. Use Azure Front Door access logs for all VNet east-west traffic

**Correct: A.** Virtual Network flow logs capture IP traffic metadata for virtual networks. Traffic Analytics can analyze supported flow-log data to help visualize traffic patterns and identify issues. Verify current region, workspace, storage, and feature support. [R1][R2]

**Why the others are wrong:** B DNS logs describe name queries, not all network flows or their byte/packet metadata. [R1] C NSG rules express policy and do not record every observed flow as historical telemetry. [R1] D Front Door logs describe requests that traverse Front Door, not general VNet east-west traffic. [R3]

**References:** [R1] [Virtual Network flow logs](https://learn.microsoft.com/en-us/azure/network-watcher/vnet-flow-logs-overview); [R2] [Traffic Analytics](https://learn.microsoft.com/en-us/azure/network-watcher/traffic-analytics); [R3] [Azure Front Door monitoring and logs](https://learn.microsoft.com/en-us/azure/frontdoor/standard-premium/how-to-logs).

### Question 28 - Select an Azure Firewall tier for TLS inspection

A hub firewall must provide intrusion detection and prevention, TLS inspection, and URL filtering for supported traffic. Which Azure Firewall SKU should the architect select?

A. Azure Firewall Premium
B. Azure Firewall Basic
C. Azure NAT Gateway
D. An NSG alone

**Correct: A.** Azure Firewall Premium includes advanced protections such as IDPS, TLS inspection, and URL filtering for supported scenarios. Confirm certificate deployment, protocol, and service limitations during design. [R1][R2]

**Why the others are wrong:** B Basic targets simpler, lower-throughput scenarios and does not provide the requested Premium inspection capabilities. [R1] C NAT Gateway provides outbound SNAT, not stateful inspection or IDPS. [R3] D NSGs provide stateful network-layer filtering and do not perform TLS inspection or IDPS. [R4]

**References:** [R1] [Choose the right Azure Firewall SKU](https://learn.microsoft.com/en-us/azure/firewall/choose-firewall-sku); [R2] [Azure Firewall Premium features](https://learn.microsoft.com/en-us/azure/firewall/premium-features); [R3] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview); [R4] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview).

### Question 29 - Deploy a secured Virtual WAN hub

A global enterprise uses Azure Virtual WAN and requires centralized inspection of traffic between branches and Azure VNets. It wants to manage firewall policies centrally across secured virtual hubs. Which architecture best meets the requirement?

A. Deploy Azure Firewall in the Virtual WAN virtual hub, secure the hub, and manage policies with Azure Firewall Manager
B. Deploy one NSG per branch and assume it inspects inter-hub traffic centrally
C. Use Traffic Manager as the firewall manager for Virtual WAN
D. Use a DNS Private Resolver inbound endpoint as the traffic-inspection appliance

**Correct: A.** Azure Firewall can be deployed in a Virtual WAN hub to create a secured virtual hub; Firewall Manager provides centralized policy management for supported firewall deployments. [R1][R2]

**Why the others are wrong:** B NSGs filter traffic at VNet subnets/NICs and do not provide the requested centralized secured-hub inspection. [R1][R3] C Traffic Manager performs DNS-based endpoint routing, not firewall policy management. [R4] D Private Resolver handles DNS queries and does not inspect arbitrary transit traffic. [R5]

**References:** [R1] [Secure virtual hubs with Azure Firewall Manager](https://learn.microsoft.com/en-us/azure/firewall-manager/secured-virtual-hub); [R2] [Azure Firewall Manager overview](https://learn.microsoft.com/en-us/azure/firewall-manager/overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R5] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview).

### Question 30 - Configure a WAF to monitor and block web attacks

A security team wants to log matched web requests and block requests that match managed WAF rules. Which WAF configuration is required?

A. Configure a WAF policy in Prevention mode with an appropriate managed rule set and associate it with the protected Application Gateway or Front Door resource
B. Configure Detection mode; it blocks matching requests automatically
C. Configure an NSG rule for SQL injection signatures
D. Use Traffic Manager Priority routing as the web application firewall

**Correct: A.** Prevention mode logs and blocks requests that match configured WAF rules; Detection mode monitors/logs but does not block. The policy must be associated with the correct supported application delivery resource. [R1][R2]

**Why the others are wrong:** B Detection mode reports matches but does not block them. [R1] C NSGs filter network flows and cannot evaluate SQL injection or managed HTTP rule sets. [R3] D Traffic Manager is DNS routing and has no WAF inspection capability. [R4]

**References:** [R1] [WAF on Application Gateway](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview); [R2] [WAF on Azure Front Door](https://learn.microsoft.com/en-us/azure/web-application-firewall/afds/afds-overview); [R3] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R4] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview).

### Question 31 - Permit administration without public VM addresses

Administrators need RDP and SSH access to Azure VMs, but the VMs must not have public IP addresses. What should you deploy?

A. Azure Bastion in the VNet, with the required subnet and supported SKU/client configuration
B. A public IP on each VM and an NSG rule allowing all internet sources
C. Azure Traffic Manager with a private DNS zone
D. Azure NAT Gateway

**Correct: A.** Azure Bastion enables RDP/SSH access to VMs over TLS through supported client experiences without requiring public IP addresses on those VMs. [R1]

**Why the others are wrong:** B exposes management endpoints directly and violates the no-public-IP requirement. [R1][R2] C Traffic Manager routes DNS queries and does not provide remote administration. [R3] D NAT Gateway provides outbound connectivity, not inbound RDP/SSH access. [R4]

**References:** [R1] [Azure Bastion overview](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Azure NAT Gateway](https://learn.microsoft.com/en-us/azure/nat-gateway/nat-overview).

### Question 32 - Protect public IP resources from volumetric attacks

A public service in an Azure VNet requires protection against large volumetric distributed denial-of-service attacks. The organization needs protection scoped to the virtual network's supported public IP resources and access to DDoS telemetry and mitigation reports. Which solution should be designed?

A. Azure DDoS Network Protection on the VNet, with the required configuration and monitoring
B. An NSG with a deny rule for all internet traffic
C. Azure Application Gateway WAF alone
D. Azure Private DNS zone

**Correct: A.** DDoS Network Protection provides network-layer DDoS mitigation for supported public IP resources associated with protected VNets and includes telemetry/mitigation capabilities. [R1]

**Why the others are wrong:** B denying all internet traffic would block legitimate service access and is not volumetric DDoS mitigation. [R2] C WAF addresses application-layer HTTP(S) attacks; it does not replace network-layer DDoS protection. [R1][R3] D private DNS resolves private names and has no DDoS mitigation function. [R4]

**References:** [R1] [Azure DDoS Protection overview](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [WAF overview](https://learn.microsoft.com/en-us/azure/web-application-firewall/overview); [R4] [Azure Private DNS zones](https://learn.microsoft.com/en-us/azure/dns/private-dns-privatednszone).

### Question 33 - Apply centrally managed network security rules

A platform team must enforce baseline security rules across selected VNets, and workload teams must not be able to override those centrally mandated rules. Which Virtual Network Manager capability is designed for this?

A. Security admin configuration with appropriately scoped network groups and rules
B. A conventional NSG rule assigned at the NIC, which always overrides every other VNet rule
C. Azure Traffic Manager with geographic routing
D. DNS Private Resolver forwarding rules

**Correct: A.** Azure Virtual Network Manager security admin rules provide centrally managed network security policy for network groups and can be configured with enforcement behavior that takes precedence over conflicting NSG rules as documented. [R1]

**Why the others are wrong:** B NSGs provide subnet/NIC filtering but alone do not provide the centrally managed Virtual Network Manager security-admin governance requested. [R1][R2] C Traffic Manager routes DNS clients to endpoints. [R3] D DNS forwarding rules govern name resolution, not packet filtering. [R4]

**References:** [R1] [Security admin rules in Azure Virtual Network Manager](https://learn.microsoft.com/en-us/azure/virtual-network-manager/concept-security-admins); [R2] [Network security groups](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview); [R3] [Azure Traffic Manager](https://learn.microsoft.com/en-us/azure/traffic-manager/traffic-manager-overview); [R4] [Azure DNS Private Resolver](https://learn.microsoft.com/en-us/azure/dns/dns-private-resolver-overview).

## Further study

Use the [AZ-700 certification page](https://learn.microsoft.com/en-us/credentials/certifications/azure-network-engineer-associate/) and [official study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-700) for current objectives. Microsoft Learn preparation resources:

- [AZ-700 course: Design and Implement Microsoft Azure Network Solutions](https://learn.microsoft.com/en-us/training/courses/az-700t00)
- [AZ-700 learning path](https://learn.microsoft.com/en-us/training/paths/design-implement-microsoft-azure-networking-solutions-az-700/)
- [Introduction to Azure Virtual Networks](https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/)
- [Design and implement hybrid networking](https://learn.microsoft.com/en-us/training/modules/design-implement-hybrid-networking/)
- [Design and implement Azure ExpressRoute](https://learn.microsoft.com/en-us/training/modules/design-implement-azure-expressroute/)
- [Load balance non-HTTP(S) traffic in Azure](https://learn.microsoft.com/en-us/training/modules/load-balancing-non-https-traffic-azure/)
- [Load balance HTTP(S) traffic in Azure](https://learn.microsoft.com/en-us/training/modules/load-balancing-https-traffic-azure/)
- [Design and implement network security](https://learn.microsoft.com/en-us/training/modules/design-implement-network-security-monitoring/)
- [Design and implement private access to Azure services](https://learn.microsoft.com/en-us/training/modules/design-implement-private-access-to-azure-services/)
- [Design and implement network monitoring](https://learn.microsoft.com/en-us/training/modules/design-implement-network-monitoring/)

Supplementary video material: [AZ-700 Microsoft Learn playlist](https://www.youtube.com/playlist?list=PLahhVEj9XNTdToCofwwCsHyu-PkVztyz7) and episode links in the repository specification. Microsoft Learn is the authority for exam scope and product behavior.