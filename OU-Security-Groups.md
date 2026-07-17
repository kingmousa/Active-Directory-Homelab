# Organizational Units & Security Groups

## Overview

To simulate an enterprise Active Directory environment, Organizational Units (OUs) and Security Groups were created to organize users, simplify administration, and implement Role-Based Access Control (RBAC).

Rather than placing every user directly inside the default **Users** container, I created a separate "Users (OU)" Organizational Unit to separate administrative responsibilities and be able to apply Group Policies to them later on.

---

## Organizational Unit Structure

The following Organizational Units were created inside the **lab.local** domain.

| Organizational Unit | Purpose |
|---------------------|----------|
| Users (OU) | Stores departmental user accounts |
| Groups | Stores Active Directory security groups |
| Workstations | Stores the workstations joined to the domain |
| Service Accounts | Stores the service accounts |

This structure provides a clean hierarchy that can easily scale as additional users, computers, and policies are introduced.

![alt text](<images/Screenshot 2026-07-17 011706.png>)

While I only created four OUs as part of this lab, there are some OUs that were already configured by default when the domain was created.

---

## Departmental Security Groups

Security Groups were created to represent business departments within the organization.

| Group | Department |
|--------|------------|
| IT Helpdesk | Information Technology |
| HR Team | Human Resources |
| Accounting | Accounting |

Instead of assigning permissions directly to individual users, permissions are assigned to Security Groups.

Users inherit access by becoming members of the appropriate group, following Microsoft's recommended Active Directory administration practices.

![alt text](<images/Screenshot 2026-07-17 011435.png>)
---

## User Organization

Each employee account was placed into the appropriate Organizational Unit and assigned to the corresponding Security Group.

This provides several administrative advantages:

- Simplifies user management
- Enables Role-Based Access Control (RBAC)
- Makes Group Policy deployment easier
- Reduces permission management overhead
- Supports enterprise scalability

![alt text](<images/Screenshot 2026-07-17 011450.png>)

---

## Group Membership

Security Group membership determines which network resources users are allowed to access.

For example:

- Members of **IT Helpdesk** can access the IT department file share.
- Members of **HR Team** can access HR resources.
- Members of **Accounting** can access Accounting documents.

This model follows the principle of assigning permissions to groups rather than directly to user accounts.


Members of the IT Helpdesk group: ![alt text](<images/Screenshot 2026-07-09 223351.png>)

---

## Role-Based Access Control (RBAC)

Role-Based Access Control was implemented by combining:

- Organizational Units
- Security Groups
- NTFS Permissions
- SMB Share Permissions

This ensures users only receive access to the resources required for their job role.

The RBAC model was later validated by logging into separate user accounts and verifying that only authorized network shares were accessible.

IT Helpdesk user receiving the mapped IT Helpdesk network drive: ![alt text](<images/Screenshot 2026-07-15 023827.png>)

IT User successfully accessing respective network drive: ![alt text](<images/Screenshot 2026-07-15 023846.png>)

IT User being denied access to HR drive: ![alt text](<images/Screenshot 2026-07-15 023811.png>)

---

## Enterprise Benefits

Using Organizational Units and Security Groups provides several enterprise advantages:

- Centralized administration
- Simplified permission management
- Easier Group Policy deployment
- Improved security
- Reduced administrative effort
- Better scalability for larger environments