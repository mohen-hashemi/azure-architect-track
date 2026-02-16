# Azure Virtual Network (VNet)

## What is VNet?

Azure Virtual Network is the fundamental building block for private networking in Azure.

## Key Components

* Address space (CIDR)
* Subnets
* Network Security Groups
* Route Tables
* Peering
* NAT Gateway
* VPN Gateway
* ExpressRoute

## Architectural Role

VNet provides isolation, segmentation, and secure connectivity between:

* Azure resources
* On-premises infrastructure
* Other VNets



\## Enterprise Design Scenario



\### Requirements



\- Separate environments: Dev, Test, Prod

\- On-premises connectivity

\- Internet access control

\- Network segmentation

\- High availability



\### Proposed Architecture



\- Hub-Spoke topology

\- Dedicated VNet per environment

\- Centralized Firewall in Hub

\- VPN Gateway in Hub

\- Peering between Hub and Spokes



\### Addressing Strategy



Hub: 10.0.0.0/16

Dev: 10.1.0.0/16

Test: 10.2.0.0/16

Prod: 10.3.0.0/16



\### Design Decisions



\- Hub-Spoke chosen for centralized control

\- Separate address spaces to prevent overlap

\- NSG per subnet for segmentation

\- UDR to force traffic through firewall



\## Enterprise Hub-Spoke Design Scenario



In large enterprise environments, Azure Virtual Network architecture is typically implemented using a Hub-Spoke model.



\- Hub VNet:

  - VPN Gateway / ExpressRoute

  - Azure Firewall

  - Bastion

  - Shared services



\- Spoke VNets:

  - Application workloads

  - Isolated environments (Prod / Dev / Test)



Benefits:

\- Centralized security

\- Simplified routing

\- Network segmentation

\- Scalability



\## Enterprise Hub-Spoke Design Scenario



\### Requirements

\- Separate environments: Dev / Test / Prod

\- Centralized security and egress control

\- On-premises connectivity (VPN now, ExpressRoute later)

\- Clear segmentation (no flat network)

\- Scalable IP plan (future growth, mergers, multi-region)



\### Proposed Topology

\- Hub-Spoke network model

\- Hub hosts shared services:

&nbsp; - Azure Firewall (or NVA)

&nbsp; - VPN Gateway / ExpressRoute Gateway

&nbsp; - Bastion (optional)

&nbsp; - Shared DNS (optional)

\- Spokes host workloads per environment:

&nbsp; - Dev Spoke

&nbsp; - Test Spoke

&nbsp; - Prod Spoke



\### Addressing Strategy (Example)

\- Hub:  10.0.0.0/16

\- Dev:  10.1.0.0/16

\- Test: 10.2.0.0/16

\- Prod: 10.3.0.0/16



\### Subnet Layout (Hub)

\- AzureFirewallSubnet: 10.0.0.0/26

\- GatewaySubnet:       10.0.0.64/27

\- AzureBastionSubnet:  10.0.0.96/27 (optional)

\- SharedServices:      10.0.1.0/24 (optional)



\### Subnet Layout (Spoke Example - Prod)

\- Web:   10.3.1.0/24

\- App:   10.3.2.0/24

\- Data:  10.3.3.0/24

\- Mgmt:  10.3.10.0/24 (optional)



\### Routing \& Security Controls

\- Use UDRs in spokes to force egress via Hub Firewall

\- NSG per subnet for east-west segmentation

\- Deny-by-default for inbound, allow only required ports

\- Private endpoints for PaaS where possible (reduce public exposure)



\### Design Decisions (Why)

\- Hub-Spoke chosen for centralized control and consistent security

\- Separate /16 per environment prevents overlap and simplifies governance

\- UDR + Firewall centralizes outbound and inspection

\- NSG + subnet segmentation prevents lateral movement



