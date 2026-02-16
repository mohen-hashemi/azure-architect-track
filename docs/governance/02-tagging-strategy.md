# Azure Tagging Strategy

## Mandatory Tags

| Tag Key        | Example     | Purpose |
|---------------|------------|---------|
| Environment   | Prod       | Environment isolation |
| Owner         | NetTeam    | Accountability |
| CostCenter    | CC-1001    | Billing alignment |
| Criticality   | High       | Incident prioritization |
| DataClass     | Confidential | Security classification |

## Governance Rules

- All production resources must have mandatory tags
- Tag enforcement via Azure Policy
- No resource without Environment and Owner tag
