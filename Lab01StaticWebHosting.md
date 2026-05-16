# Lab 01: Hosting Your First Static Website in Azure

![Azure](https://img.shields.io/badge/Azure-Blob%20Storage-0078d4?style=flat&logo=microsoftazure&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green?style=flat)
![Time](https://img.shields.io/badge/Completed%20In-6%20Minutes-blue?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat)

## Overview

Deployed a public-facing static website on **Azure Blob Storage** using the Static Website Hosting feature — no web server, no VMs, no complex infrastructure. This lab introduces core cloud concepts including **PaaS (Platform as a Service)** and **Serverless hosting**, where the focus is on delivering content while Azure handles everything underneath.

---

## Architecture

```
User (Internet) → Public URL → Azure Storage Account ($web container) → index.html
```

---

## Services & Tools Used

| Service / Tool | Purpose |
|---|---|
| Azure Portal | Primary management interface |
| Azure Resource Group | Logical container for lab resources |
| Azure Blob Storage | Hosts the static website files |
| $web Container | Auto-generated container for static site content |
| Static Website Hosting | Enables public HTTP endpoint on the storage account |
| HTML / Text Editor | Created the index.html site file |

---

## What I Did

### Phase 1 — Created a Resource Group
Logged into the Azure Portal and created a dedicated Resource Group (`rg-lab01-dharris`) in the **East US** region to organize all lab resources in one place.

### Phase 2 — Provisioned a Storage Account
Created a Storage Account (`stlab01dharris`) with the following configuration:
- **Performance:** Standard
- **Redundancy:** Locally-Redundant Storage (LRS) — cost-effective for lab environments
- Validated and deployed in under 30 seconds

### Phase 3 — Enabled Static Website Hosting
Inside the Storage Account, navigated to **Data Management → Static Website** and:
- Switched hosting from **Disabled → Enabled**
- Set `index.html` as the index document
- Set `404.html` as the error document path (best practice)
- Captured the auto-generated **Primary Endpoint URL** — this is the live public address for the site

### Phase 4 — Created the Website File
Built a simple `index.html` file locally using a text editor with basic HTML and inline CSS, confirming the page would render correctly before uploading.

### Phase 5 — Uploaded Content to Azure
Navigated to **Containers → $web** inside the Storage Account and uploaded `index.html` directly to the auto-generated `$web` container.

### Phase 6 — Validated the Deployment
Opened the Primary Endpoint URL in a browser and confirmed the live site rendered correctly — **"Hello from the Cloud!"** was displaying as expected.

---

## Key Concepts Learned

- **PaaS vs IaaS:** No virtual machines or web servers needed — Azure abstracts all infrastructure through Blob Storage's static hosting feature
- **Serverless Hosting:** Deployed a fully public website without provisioning or managing a single server
- **Storage Account Naming Rules:** Names must be globally unique across all of Azure, all lowercase, letters and numbers only — learned to append identifiers to avoid naming conflicts
- **$web Container:** Automatically created when static website hosting is enabled; Azure only serves content from this specific container
- **Case Sensitivity:** Azure static hosting is case-sensitive — `index.html` ≠ `Index.html`

---

## Outcome

Live static website successfully deployed and publicly accessible via Azure Blob Storage endpoint in **under 6 minutes** from start to finish.

---

## Clean Up

After validation, deleted the resource group (`rg-lab01-dharris`) to avoid any residual costs — a good habit to build from day one when working in cloud environments.

---

## Part of Series

This lab is part of an ongoing cloud infrastructure learning series documenting hands-on Azure projects from beginner to advanced.

| Lab | Topic | Status |
|---|---|---|
| Lab 01 | Hosting a Static Website in Azure | ✅ Complete |
| Lab 02 | Coming Soon | 🔜 |

---

*Completed by D'Vonte Harris · [LinkedIn](https://www.linkedin.com/in/d-vonte-harris-598b4b86) · [GitHub](https://github.com/dvonteh-ux)*
