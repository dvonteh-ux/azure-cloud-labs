# Lab 02 — Secure 2-Tier Web Application

## Overview

This lab focused on building a secure 2-tier Infrastructure-as-a-Service (IaaS) application architecture in Microsoft Azure. The environment consisted of a public-facing Web Server subnet and a private Database Server subnet connected through a Virtual Network.

The lab emphasized:

* network segmentation
* subnet isolation
* secure VM deployment
* internal-only database communication
* Network Security Group configuration
* SSH connectivity validation

---

## Technologies Used

* Microsoft Azure
* Azure Virtual Networks (VNets)
* Azure Subnets
* Azure Network Security Groups (NSGs)
* Ubuntu Linux Virtual Machines
* Azure Public IPs
* SSH
* ICMP / Ping Testing

---

## Architecture

The environment used a classic 2-tier network design:

### Public Tier

Hosted:

* `vm-web-01`

Connected to:

* `snet-web`
* Public IP address
* Internet access

### Private Tier

Hosted:

* `vm-db-01`

Connected to:

* `snet-db`
* No public IP
* Internal-only communication

### Security Controls

* NSG rule allowing only Web subnet traffic to Database subnet
* Database VM isolated from direct internet exposure

---

## Network Layout

| Component       | Address Space |
| --------------- | ------------- |
| VNet            | 10.0.0.0/16   |
| Web Subnet      | 10.0.1.0/24   |
| Database Subnet | 10.0.2.0/24   |

---

## What I Built

* Azure Resource Group
* Virtual Network
* Public Web Subnet
* Private Database Subnet
* Ubuntu Web VM
* Ubuntu Database VM
* Public IP for Web VM
* Network Security Group rules
* Internal VM-to-VM communication validation

---

## Validation Performed

I validated the deployment by:

* SSH connecting into the Web VM
* Using the Web VM as a jump box to access internal resources
* Testing connectivity between subnets using `ping`
* Verifying the Database VM had no public IP exposure
* Confirming NSG rules allowed internal traffic appropriately

---

## Key Concepts Learned

### Infrastructure-as-a-Service (IaaS)

This lab demonstrated traditional infrastructure management where:

* VMs are fully managed manually
* networking is explicitly configured
* operating systems require administration
* segmentation and firewall rules must be implemented directly

### Public vs Private Subnets

The Web tier required internet exposure while the Database tier remained private and isolated.

This mirrors real-world enterprise application architectures where:

* front-end services are internet accessible
* back-end systems are protected internally

### Jump Box Connectivity

Because the Database VM had no public IP address, access required:

1. SSH into the Web VM
2. Connect internally to the Database VM

This reinforced secure administrative access patterns.

---

## Troubleshooting Notes

### SSH Connectivity

Validated that:

* the Web VM accepted public SSH connections
* the Database VM intentionally could not be reached directly from the internet

### Internal Connectivity

Tested subnet communication using:

```bash
ping 10.0.2.4
```

This confirmed:

* routing inside the VNet
* proper subnet deployment
* successful VM communication

### NSG Rule Validation

Configured inbound rules to explicitly allow:

* traffic from the Web subnet
* communication into the Database subnet

---

## Skills Demonstrated

* Azure networking
* Subnet segmentation
* Linux VM deployment
* SSH administration
* NSG configuration
* Internal routing validation
* Secure infrastructure design
* Basic cloud architecture principles

---

## Outcome

Successfully deployed a secure 2-tier Azure infrastructure environment with isolated networking, subnet segmentation, internal-only database communication, and validated SSH connectivity patterns.

---

## Screenshots

Screenshots will be added for:

* VNet configuration
* Subnet layout
* Web VM deployment
* Database VM deployment
* NSG rule configuration
* SSH connection
* Successful ping test

