# Azure Naming Convention

## Format
<org>-<env>-<region>-<service>-<instance>

Example:
crb-prod-euw-vnet-01
crb-dev-euw-vm-01
crb-prod-euw-fw-01

## Components

- org      = crb (CareerRebuild)
- env      = dev | test | prod
- region   = euw (West Europe), use short codes
- service  = vnet | vm | fw | nsg | rg | kv | st
- instance = 01, 02, ...

## Resource Group Naming

rg-<org>-<env>-<region>-<workload>

Example:
rg-crb-prod-euw-network
rg-crb-dev-euw-app1
