# Lab 05 - Implementing Governance & Security Hardening

## Objective

The objective of this lab was to implement foundational Azure governance controls by enforcing Role-Based Access Control (RBAC), Azure Policy, and Cost Management controls. The goal was to simulate real-world cloud administration scenarios where access must be restricted, resource deployments governed, and spending monitored.

---

## Architecture Overview

This lab focused on governance rather than infrastructure deployment.

The environment included:

* Azure Resource Group
* Microsoft Entra ID User
* RBAC Role Assignment
* Azure Policy Assignment
* Azure Cost Management Budget

The design simulated a junior developer receiving limited access while administrative controls prevented unauthorized resource creation and restricted expensive deployments.

---

## Azure Services Used

* Microsoft Entra ID
* Azure Resource Groups
* Azure RBAC
* Azure Policy
* Azure Cost Management
* Azure Budgets

---

## Skills Demonstrated

* Identity and Access Management (IAM)
* Role-Based Access Control (RBAC)
* Azure Governance
* Policy Enforcement
* Budget Creation
* Cost Monitoring
* Least Privilege Access
* Cloud Security Best Practices

---

## Deployment Steps

### Step 1 – Create Governance Resource Group

Created:

```text
rg-lab05-gov-dvonte
```

to contain governance testing resources.

---

### Step 2 – Create Test User

Created a new Microsoft Entra ID user to simulate a junior developer account.

Configuration included:

* User Principal Name
* Display Name
* Password Assignment

---

### Step 3 – Implement RBAC

Assigned the built-in:

```text
Reader
```

role to the test user at the Resource Group scope.

This allowed the user to:

* View resources
* Review configurations

While preventing:

* Resource creation
* Resource modification
* Resource deletion

---

### Step 4 – Validate Access Restrictions

Using an Incognito browser session, logged in as the junior developer account.

Attempted to create resources within the Resource Group.

Result:

✅ Access successfully restricted

The user received authorization failures when attempting resource creation.

---

### Step 5 – Configure Azure Policy

Created a policy assignment:

```text
Restrict-VM-Sizes
```

Policy Definition:

```text
Allowed virtual machine size SKUs
```

Allowed Sizes:

* Standard_B1s
* Standard_B1ms

Any larger VM deployment would be denied.

---

### Step 6 – Validate Policy Enforcement

Attempted deployment of:

```text
Standard_D2s_v3
```

Result:

✅ Policy Check Failed

Azure Policy successfully prevented deployment due to governance controls.

---

### Step 7 – Implement Cost Management Controls

Created a monthly budget:

```text
Monthly-Lab-Budget
```

Configuration:

* Budget Amount: $50
* Reset Period: Monthly
* Alert Threshold: 80%

Email notifications were configured to alert when spending approached the defined threshold.

---

## Validation & Testing

Validation included:

### RBAC Validation

* User successfully authenticated
* User could view resources
* User could not create resources

### Policy Validation

* Policy assignment applied successfully
* Unsupported VM sizes were denied
* Policy evaluation returned expected failures

### Budget Validation

* Budget created successfully
* Alert threshold configured
* Cost monitoring enabled

---

## Security Considerations

This lab implemented several security best practices:

### Least Privilege Access

Users receive only the permissions required to perform their responsibilities.

### Governance Controls

Azure Policy prevents unauthorized or non-compliant deployments.

### Cost Protection

Budgets provide financial oversight and reduce the risk of unexpected cloud spending.

### Identity Security

Administrative actions are separated from standard user activities.

---

## Troubleshooting

### Reader Role Did Not Restrict Access

Issue:

User retained unexpected permissions.

Resolution:

Verified role assignment scope and ensured testing occurred within the correct Resource Group.

---

### Azure Policy Did Not Immediately Block Resources

Issue:

Policy enforcement did not occur instantly.

Resolution:

Allowed time for policy replication and reassignment processing.

---

## Lessons Learned

Key takeaways from this lab:

* Governance is just as important as deployment.
* RBAC is essential for implementing least privilege.
* Azure Policy provides scalable compliance enforcement.
* Cost management should be implemented early in cloud environments.
* Security and governance controls help prevent both technical and financial risk.

---

## Technologies Used

* Azure Portal
* Microsoft Entra ID
* Azure RBAC
* Azure Policy
* Azure Cost Management
* Azure Budgets

---

## Professional Relevance

This lab mirrors real-world responsibilities commonly performed by Cloud Administrators, Systems Engineers, and Infrastructure Engineers.

Organizations rely heavily on governance controls to:

* Restrict access
* Enforce compliance
* Reduce risk
* Control cloud spending
* Maintain security standards

These skills directly align with enterprise cloud operations and Azure administration roles.

---

## Status

✅ Completed

Governance controls implemented, validated, documented, and tested successfully.
