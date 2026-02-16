# Management Group Structure

Root
 ├── Platform
 │    ├── Identity
 │    ├── Connectivity
 │    └── Security
 │
 ├── LandingZones
 │    ├── Dev
 │    ├── Test
 │    └── Prod
 │
 └── Sandbox

## Rationale

- Platform: Shared services (Hub, Firewall, DNS)
- LandingZones: Workloads
- Sandbox: Experiments and PoC
