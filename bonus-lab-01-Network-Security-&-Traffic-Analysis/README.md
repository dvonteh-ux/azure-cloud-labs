# Bonus Lab 01 — Network Security & Traffic Analysis

## Overview

This lab focused on deploying and validating a secure hub-and-spoke Azure network architecture using Terraform Infrastructure-as-Code. The environment centralized traffic inspection through Azure Firewall, enforced routing with User Defined Routes, validated network communication between isolated spoke networks, and used Azure Network Watcher and Log Analytics for traffic visibility.

This lab also included real-world troubleshooting around Azure platform changes, deprecated services, VM SKU availability, packet capture dependencies, and firewall rule propagation.

---

## Technologies Used

* Microsoft Azure
* Terraform
* Azure CLI
* Azure Firewall Basic
* Azure Virtual Networks
* VNet Peering
* User Defined Routes
* Network Security Groups
* Azure Network Watcher
* Log Analytics Workspace
* Kusto Query Language
* Ubuntu Linux Virtual Machines

---

## Architecture

The environment used a hub-and-spoke network design:

* **Hub VNet**

  * Hosted Azure Firewall
  * Centralized network inspection point

* **Spoke 1 VNet**

  * Hosted Ubuntu VM 1

* **Spoke 2 VNet**

  * Hosted Ubuntu VM 2

* **Route Tables**

  * Forced spoke-to-spoke traffic through Azure Firewall

* **Network Security Groups**

  * Controlled SSH and ICMP access

---

## What I Built

* Resource group for the lab environment
* Hub VNet and spoke VNets
* Azure Firewall with required management configuration
* VNet peerings between hub and spokes
* User Defined Routes to force traffic through the firewall
* Network Security Group rules for SSH and ICMP
* Ubuntu virtual machines in separate spoke networks
* Log Analytics Workspace for firewall log review
* Network Watcher packet capture session

---

## Validation Performed

I validated the deployment by:

* Running Terraform `init`, `validate`, `plan`, and `apply`
* Reviewing Terraform outputs for private IP addresses
* Connecting to the spoke VM using SSH
* Testing spoke-to-spoke traffic with `ping`
* Confirming firewall routing behavior
* Changing firewall rules from Allow to Deny to observe traffic impact
* Running packet capture through Azure Network Watcher
* Querying firewall logs using KQL in Log Analytics

---

## KQL Query Used

```kql
AzureDiagnostics
| where Category == "AzureFirewallNetworkRule"
| where TimeGenerated > ago(1h)
| project TimeGenerated, msg_s
| order by TimeGenerated desc
```

---

## Troubleshooting Notes

During the lab, I encountered and resolved several real-world issues:

### Azure Firewall Basic Management Requirement

Azure Firewall Basic required a management subnet and management public IP configuration. I updated the Terraform configuration to include:

* `AzureFirewallManagementSubnet`
* Firewall management public IP
* `management_ip_configuration`

### Existing Network Watcher Limitation

Azure only allows one Network Watcher per region per subscription. Instead of creating a new Network Watcher, I referenced the existing `NetworkWatcher_eastus` resource.

### Deprecated NSG Flow Logs

New NSG Flow Log creation was blocked due to Azure retirement changes. I removed the deprecated NSG Flow Log configuration and used Azure Firewall diagnostics and packet capture instead.

### VM SKU Availability

The original VM size was unavailable in the East US region. I updated the VM size to `Standard_DC1s_v3`.

### Packet Capture Requirements

Packet capture required a storage account and the Network Watcher VM extension. I created a storage account for packet capture output and installed the required Network Watcher agent extension.

### Firewall Rule Propagation

Changing firewall rules temporarily affected connectivity, including SSH access. This demonstrated how centralized firewall policies can immediately impact management and workload traffic.

---

## Skills Demonstrated

* Infrastructure-as-Code with Terraform
* Azure networking fundamentals
* Hub-and-spoke architecture
* Firewall rule management
* Route table configuration
* Network segmentation
* Packet capture
* KQL log analysis
* Azure troubleshooting
* Cloud security validation

---

## Outcome

Successfully deployed and validated a secure Azure hub-and-spoke network security lab using Terraform. This lab demonstrated centralized traffic inspection, routed spoke-to-spoke communication through Azure Firewall, packet capture with Network Watcher, and firewall log analysis using KQL.

---

## Screenshots

Screenshots will be added to document:

* Terraform deployment output
* Azure resource group overview
* Hub-and-spoke network resources
* Azure Firewall rule configuration
* Successful ping test
* Deny rule test
* Packet capture status
* KQL query results
