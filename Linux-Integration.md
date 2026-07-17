# Linux Integration

## Overview

While Active Directory is commonly associated with Windows environments, many enterprise networks also include Linux systems that authenticate against Active Directory.

To simulate a mixed operating system environment, I joined an Ubuntu workstation to the **lab.local** domain using **Realmd**, **SSSD**, and **Kerberos**. This allows domain users to authenticate with their existing Active Directory credentials without requiring separate Linux accounts.

---

# Objectives

The objectives of this phase were to:

- Join Ubuntu to Active Directory
- Enable centralized authentication
- Configure Kerberos authentication
- Integrate SSSD with Active Directory
- Provide centralized Linux administration
- Verify cross-platform authentication

---

# Domain Join

Ubuntu was configured to communicate directly with the Domain Controller and joined to the **lab.local** domain using **realmd**.

The following components were used:

| Component | Purpose |
|-----------|---------|
| Realmd | Domain discovery and enrollment |
| SSSD | Identity and authentication services |
| Kerberos | Secure authentication |
| Active Directory | Centralized identity provider |

After joining the domain, Active Directory users were able to authenticate directly on the Linux workstation.

![alt text](<images/Screenshot 2026-07-17 035712.png>)
![alt text](<images/Screenshot 2026-07-17 035803.png>)

---

# Kerberos Authentication

Kerberos provides secure authentication between Linux clients and Active Directory.

During deployment, I came across a time synchronization issue that initially prevented me from joining the Ubuntu workstation to the domain. After correcting the system time so that the workstation date and time matched that of the Domain Controller, Kerberos authentication succeeded and I successfully joined the workstation to the domain **lab.local**.

Verifying that Kerberos is working on UBUNTU01: ![alt text](<images/Screenshot 2026-07-17 035823.png>)


---

# Linux Administrative Privileges

To maintain consistent administration across Windows and Linux systems, members of the **IT Helpdesk** Active Directory Security Group were granted administrative privileges on the Ubuntu workstation.

Rather than creating separate local administrator accounts, Ubuntu was configured to allow authorized domain users to execute administrative commands using **sudo**.

This approach provides:

- Centralized administration
- Consistent privilege management
- Simplified onboarding and offboarding
- Role-Based Administration across operating systems

Managing Linux administrative access through Active Directory mirrors common enterprise practices and eliminates the need to manage separate administrator accounts on each Linux system.

Granting sudo access to the IT Helpdesk Active Directory group on UBUNTU01: ![alt text](<images/Screenshot 2026-07-10 004859.png>)

Verifying sudo rights as an IT Helpdesk user: ![alt text](<images/Screenshot 2026-07-17 035941.png>)

---

# Authentication Validation

The Linux integration was validated by performing the following tests:

- Successfully joined Ubuntu to the **lab.local** domain.
- Logged in using Active Directory user accounts.
- Verified domain user resolution.
- Confirmed Kerberos authentication.
- Verified IT Helpdesk members could execute administrative commands using **sudo**.

These tests confirmed successful integration between Linux and Active Directory.

Verifying Linux can resolve Active Directory users and group memberships: ![alt text](<images/Screenshot 2026-07-17 040034.png>)

---

# Enterprise Benefits

Integrating Linux systems with Active Directory provides several operational benefits:

- Centralized user management
- Single Sign-On (SSO)
- Consistent authentication across operating systems
- Reduced administrative overhead
- Improved security through centralized identity management
- Simplified account lifecycle management

---

# Skills Demonstrated

- Linux Administration
- Ubuntu Server/Desktop
- Active Directory Integration
- Kerberos Authentication
- SSSD
- Realmd
- Linux Identity Management
- Sudo Configuration
- Cross-Platform Authentication