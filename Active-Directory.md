# Active Directory Domain Deployment

## Overview

Server Dashboard in Domain Controller:![Server Dashboard in Domain Controller](<images/Screenshot 2026-07-17 002353.png>)

This section documents the deployment of a Windows Server 2022 Domain Controller and the configuration of an Active Directory Domain Services (AD DS) environment.

The goal of this project was to simulate an enterprise Active Directory infrastructure by deploying a centralized authentication server capable of managing users, computers, security groups, file permissions, and Group Policy Objects.

---

## Objectives

- Deploy Windows Server 2022
- Install Active Directory Domain Services (AD DS)
- Promote the server to a Domain Controller
- Create the lab.local domain
- Configure DNS
- Verify Active Directory functionality
- Prepare the environment for enterprise administration

---

## Server Configuration

| Component | Value |
|-----------|-------|
| Operating System | Windows Server 2022 |
| Hostname | DC01 |
| Domain | lab.local |
| Server Role | Domain Controller |
| DNS | Active Directory Integrated |
| Authentication | Kerberos |

---

## Installing Active Directory Domain Services

![alt text](<images/Screenshot 2026-07-17 002430.png>)

The Active Directory Domain Services role was installed through Server Manager.

After installation, the server was promoted to a Domain Controller and a new Active Directory forest was created.

Forest Name:

lab.local

This automatically configured:

- DNS
- SYSVOL
- NETLOGON
- Kerberos Authentication
- Active Directory Database

---

## Domain Controller Promotion

After promotion, the server rebooted and became the first Domain Controller in the forest.

The following services were verified:

- Active Directory Users and Computers
- DNS Manager
- Group Policy Management
- Active Directory Administrative Center

![alt text](<images/Screenshot 2026-07-17 002517.png>)

---

## Domain Computers

The following systems were joined to the lab.local domain.

| Computer | Operating System | Purpose |
|-----------|-----------------|----------|
| DC01 | Windows Server 2022 | Domain Controller |
| CLIENT01 | Windows 11 | Domain Workstation |
| CLIENT02 | Windows 11 | Domain Workstation |
| UBUNTU01 | Ubuntu Linux | Linux Domain Member |

Each client authenticates directly against Active Directory using domain credentials.

Windows clients authenticate using Kerberos while Ubuntu authenticates through SSSD and Realmd.

![alt text](<images/Screenshot 2026-07-09 223753.png>)

CLIENT01 joining the domain: ![alt text](<images/Screenshot 2026-07-03 185337.png>)

---

## DNS Configuration

Active Directory relies heavily on DNS.

The Domain Controller was configured as the DNS server for all domain-joined systems.

This allows:

- User logon
- Domain controller discovery
- Kerberos authentication
- Group Policy processing

Forward Lookup Zones in the domain lab.local: ![alt text](<images/Screenshot 2026-07-17 002641.png>)

---
## PowerShell Verification on DC01

![alt text](<images/Screenshot 2026-07-17 002805.png>)
