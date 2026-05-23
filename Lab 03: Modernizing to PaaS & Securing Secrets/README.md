# Lab 03 — Modernizing to PaaS & Securing Secrets

## Overview

This lab focused on modernizing an Azure infrastructure environment by replacing a self-managed database VM with Azure SQL Database Platform-as-a-Service (PaaS). The lab also introduced secure secret management using Azure Key Vault and identity-based authentication using Managed Identity and RBAC.

This exercise demonstrated:

* migration from IaaS to PaaS
* secure credential storage
* least-privilege access
* managed identities
* Azure observability and monitoring

---

## Technologies Used

* Microsoft Azure
* Azure SQL Database
* Azure Key Vault
* Azure Managed Identity
* Azure RBAC
* Azure Monitor
* Azure Log Analytics
* Ubuntu Linux VM
* Azure Networking

---

## Architecture

The architecture modernized the previous lab environment by:

### Removing

* self-managed database VM

### Replacing With

* Azure SQL Database (PaaS)

### Adding

* Azure Key Vault
* Managed Identity
* Role-Based Access Control (RBAC)
* Azure Monitor Metrics

---

## What I Built

* Azure SQL Server
* Azure SQL Database
* Azure Key Vault
* Managed Identity on Web VM
* RBAC role assignments
* Azure Monitor Metrics validation
* Secure secret storage workflow

---

## Security Improvements

### Before Modernization

* database credentials manually managed
* self-hosted database VM
* infrastructure patching responsibility
* increased attack surface

### After Modernization

* managed Azure SQL Database
* secrets stored securely in Key Vault
* password removed from application configuration
* identity-based authentication
* reduced infrastructure management overhead

---

## Validation Performed

I validated the deployment by:

* confirming Azure SQL Database deployment
* validating database status and monitoring metrics
* creating and storing secrets in Key Vault
* enabling Managed Identity on the Web VM
* assigning Key Vault Secrets User RBAC role
* confirming Azure Monitor metric visibility
* validating observability functionality

---

## Key Concepts Learned

### Platform-as-a-Service (PaaS)

This lab demonstrated how Azure SQL Database removes the need to manage:

* operating systems
* database patching
* infrastructure maintenance
* backups
* availability management

### Azure Key Vault

Used Azure Key Vault to securely store:

* SQL administrator password

This prevents:

* hardcoded credentials
* plaintext password exposure
* insecure configuration management

### Managed Identity

Enabled system-assigned Managed Identity on the VM to allow secure authentication to Azure services without storing passwords or service account credentials.

### Role-Based Access Control (RBAC)

Used RBAC to apply least-privilege access:

* Key Vault Administrator for setup
* Key Vault Secrets User for VM access

### Observability

Used Azure Monitor Metrics to validate:

* SQL Database health
* DTU utilization
* monitoring visibility

---

## Troubleshooting Notes

### SQL Tier Selection

Encountered Azure free-offer limitations preventing DTU tier visibility.

Resolved by:

* removing free-offer configuration
* selecting DTU-based Basic tier

### Global Naming Constraints

SQL Server and Key Vault names required globally unique naming conventions.

### RBAC Propagation Delay

Managed Identity role assignments required propagation time before permissions became active.

### Key Vault Authorization

Initial Key Vault access returned RBAC authorization errors until the proper role assignment was configured.

---

## Skills Demonstrated

* Azure PaaS deployment
* Azure SQL Database administration
* Key Vault secret management
* Managed Identity configuration
* RBAC role assignment
* Azure monitoring
* Secure cloud architecture
* Cloud modernization concepts
* Identity-based access patterns

---

## Outcome

Successfully modernized a traditional Azure infrastructure deployment into a more secure and scalable cloud-native architecture using Azure SQL Database, Key Vault, Managed Identity, and RBAC-based access control.

---

## Screenshots

Screenshots will be added for:

* Azure SQL Database deployment
* SQL Server configuration
* Azure Key Vault deployment
* Managed Identity configuration
* RBAC role assignment
* Azure Monitor Metrics
* Secret creation workflow

