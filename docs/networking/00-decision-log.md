# Networking Decision Log

## DL-001: Choose Hub-Spoke Topology
**Decision:** Use Hub-Spoke architecture  
**Reason:** Centralized security, scalable growth, consistent routing  
**Alternatives:** Flat VNet, fully-meshed VNets  
**Risks:** Complexity in routing, peering limits, troubleshooting  
**Mitigations:** Standardized IP plan, naming convention, UDR templates, documentation

## DL-002: Separate /16 per Environment
**Decision:** Allocate /16 per Dev/Test/Prod  
**Reason:** Avoid overlap, simplify future expansion and multi-region  
**Alternatives:** Smaller CIDRs per environment  
**Risks:** IP waste  
**Mitigations:** Use RFC1918 with capacity planning; adjust per org size

## DL-003: Centralized Egress via Firewall
**Decision:** Force spoke outbound traffic through Hub Firewall  
**Reason:** Inspection, logging, policy enforcement, consistent egress IP  
**Alternatives:** NAT Gateway per spoke  
**Risks:** Single point of failure / bottleneck  
**Mitigations:** Zone-redundant firewall, scale-out, monitor throughput, fallback design
