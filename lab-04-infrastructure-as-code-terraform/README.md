# Lab 04 — Infrastructure as Code with Terraform

## Overview

This lab focused on deploying Azure infrastructure using Terraform Infrastructure-as-Code (IaC) principles instead of manually building resources through the Azure portal.

The objective was to:

* define infrastructure declaratively
* deploy Azure resources through code
* understand Terraform state management
* practice the Terraform workflow
* safely modify live infrastructure
* fully tear down resources using Terraform destroy

This lab reinforced how modern cloud infrastructure is managed at scale using repeatable, version-controlled configuration files.

---

## Technologies Used

* Microsoft Azure
* Terraform
* Azure Cloud Shell
* Azure Resource Groups
* Azure Virtual Networks
* Azure Subnets
* Azure Network Security Groups
* Bash
* Infrastructure-as-Code (IaC)

---

## Key Concepts Learned

### Declarative Infrastructure

Instead of manually creating Azure resources through the portal, infrastructure was described in Terraform configuration files and deployed automatically.

Terraform focuses on:

* desired state
* dependency management
* repeatable deployments
* infrastructure consistency

---

### Terraform Workflow

Practiced the standard Terraform deployment workflow:

```bash
terraform init
terraform plan
terraform apply
terraform destroy
```

Each command serves a different purpose:

* `init` downloads providers/plugins
* `plan` previews infrastructure changes
* `apply` deploys or modifies resources
* `destroy` removes tracked infrastructure cleanly

---

### Terraform State Management

Learned how Terraform uses:

```text
terraform.tfstate
```

to track:

* deployed resources
* configuration relationships
* infrastructure changes
* resource dependencies

This demonstrated why Infrastructure-as-Code environments should always be managed through Terraform instead of manually deleting resources through the Azure portal.

---

## Infrastructure Deployed

The lab deployed:

* Azure Resource Group
* Virtual Network (VNet)
* Subnet
* Network Security Group (NSG)

---

## Network Layout

| Component          | Configuration |
| ------------------ | ------------- |
| VNet Address Space | 10.0.0.0/16   |
| Subnet             | 10.0.1.0/24   |
| Location           | East US       |

---

## What I Built

### Phase 1 — Initial Deployment

Created:

* Resource Group
* Virtual Network
* Subnet

using a single Terraform configuration file.

Validated:

* Terraform initialization
* execution plan
* infrastructure deployment
* Azure resource creation

---

### Phase 2 — Live Infrastructure Modification

Updated the existing Terraform configuration by adding:

* Azure Network Security Group

Terraform correctly detected:

* only one new resource needed to be added
* no existing infrastructure required modification

This demonstrated incremental infrastructure updates without rebuilding the environment.

---

### Phase 3 — Infrastructure Teardown

Used:

```bash
terraform destroy
```

to:

* safely remove all Azure resources
* maintain Terraform state consistency
* avoid orphaned infrastructure

---

## Validation Performed

Validated the environment by:

* confirming Terraform initialization
* reviewing Terraform execution plans
* verifying Azure resources in the portal
* validating subnet configuration
* confirming NSG deployment
* observing Terraform dependency ordering
* destroying all resources successfully

---

## Troubleshooting Notes

### Terraform Syntax Errors

Encountered formatting and syntax issues while editing Terraform blocks.

Resolved by:

* correcting brackets and quotes
* validating resource block structure
* reviewing Terraform error output carefully

---

### Provider Initialization

Observed how:

```bash
terraform init
```

downloads required Azure provider plugins and creates:

* `.terraform`
* `.terraform.lock.hcl`

This reinforced provider version management concepts.

---

### State Consistency

Learned why deleting resources directly through the Azure portal can cause Terraform state drift and deployment errors.

---

## Skills Demonstrated

* Infrastructure-as-Code (IaC)
* Terraform fundamentals
* Azure networking
* Resource dependency management
* Infrastructure lifecycle management
* Declarative configuration
* State management concepts
* Cloud automation workflows
* Incremental infrastructure updates

---

## Outcome

Successfully deployed, modified, validated, and destroyed Azure infrastructure entirely through Terraform configuration files.

This lab demonstrated foundational Infrastructure-as-Code concepts used in modern cloud engineering and enterprise-scale infrastructure management.

---

## Screenshots

Screenshots will be added for:

* Terraform initialization
* Terraform execution plan
* Terraform apply output
* Azure Resource Group
* Virtual Network configuration
* Subnet validation
* NSG deployment
* Terraform destroy output
