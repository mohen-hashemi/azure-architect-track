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

&nbsp; - VPN Gateway / ExpressRoute

&nbsp; - Azure Firewall

&nbsp; - Bastion

&nbsp; - Shared services



\- Spoke VNets:

&nbsp; - Application workloads

&nbsp; - Isolated environments (Prod / Dev / Test)



Benefits:

\- Centralized security

\- Simplified routing

\- Network segmentation

\- Scalability



