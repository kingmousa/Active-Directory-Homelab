# File Server & Role-Based Access Control (RBAC)

## Overview

To simulate an enterprise file server, I created departmental network shares on the Domain Controller and secured them using Active Directory Security Groups.

Rather than assigning permissions directly to individual users, access was granted through Security Groups, implementing a Role-Based Access Control model. This approach simplifies administration while ensuring users can only access the resources required for their role.

---

# File Server Configuration

A dedicated file server structure was created to organize departmental resources.

| Shared Folder | Department | Access Group |
|---------------|------------|--------------|
| IT Helpdesk | Information Technology | IT Helpdesk |
| HR Team | Human Resources | HR Team |
| Accounting | Accounting | Accounting |

Each share was configured with both SMB Share Permissions and NTFS Permissions to control access at the network and file system levels.

![alt text](<images/Screenshot 2026-07-17 024751.png>)

Each departmental share was given a sample document to test if users could access these shares: ![alt text](<images/Screenshot 2026-07-17 024806.png>)
![alt text](<images/Screenshot 2026-07-17 024813.png>)
![alt text](<images/Screenshot 2026-07-17 024822.png>)

---

# Access Control Model

Instead of assigning permissions directly to users, access was managed through Active Directory Security Groups.

The permission workflow follows this process:

1. A user is added to a departmental Security Group.
2. The Security Group is granted access to the appropriate shared folder.
3. When the user signs in, they automatically inherit the correct permissions.

This model follows Microsoft's recommended best practice for enterprise access management.

Users of each security group were given modify permissions as well as read and write permissions. Whenever a user accesses a document in their respective network drive, they will have these permissions:
![alt text](<images/Screenshot 2026-07-17 025319.png>)
![alt text](<images/Screenshot 2026-07-17 025333.png>)
![alt text](<images/Screenshot 2026-07-17 025345.png>)

---

# Network Share Validation

I created a GPO that would map network drives to users based on their security group.

Departmental users were then used to verify access to each network share.

Validation included:

- Confirming users could access their assigned department share.
- Verifying unauthorized users could not access restricted folders.
- Confirming mapped drives connected successfully after Group Policy refresh.

These tests demonstrated that file access was enforced through Active Directory group membership.

An HR User logs in and accesses their network share on CLIENT02:![alt text](<images/Screenshot 2026-07-17 030000.png>)
![alt text](<images/Screenshot 2026-07-17 030151.png>)

An HR User being denied access to the Accounting share because they do have the right permissions: ![alt text](<images/Screenshot 2026-07-17 030024.png>)

---

# Enterprise Benefits

Implementing a centralized file server provides several advantages:

- Centralized document storage
- Simplified permission management
- Easier user onboarding and offboarding
- Improved security through least privilege
- Reduced administrative overhead
- Scalable access management for future departments

---

# Skills Demonstrated

- Windows File Server Administration
- SMB Share Configuration
- NTFS Permissions
- Active Directory Security Groups
- Role-Based Access Control (RBAC)
- Enterprise File Sharing
- Windows Server Administration