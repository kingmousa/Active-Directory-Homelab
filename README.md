# 🛡️ Active Directory Enterprise Homelab

## Project Overview

This project documents the design, deployment, and administration of an enterprise-style Active Directory environment built entirely in Oracle VirtualBox. The objective of this lab is to simulate a real-world Windows domain environment while gaining hands-on experience with identity management, Group Policy, RBAC, Windows Firewall, and Linux domain integration as well as administration.

The environment consists of a Windows Server 2022 Domain Controller, two Windows 11 clients, and an Ubuntu workstation client.

---

# Lab Environment

### Virtual Machines

| Machine | Operating System | Role |
|----------|-----------------|------|
| DC01 | Windows Server 2022 | Domain Controller, DNS, File Server |
| CLIENT01 | Windows 11 | Domain-joined workstation |
| CLIENT02 | Windows 11 | Domain-joined workstation |
| UBUNTU01 | Ubuntu 26.04 | Linux domain member |

---

### Hypervisor

- Oracle VirtualBox
- Windows 11 Host Machine
- Bridged Networking

---

### Technologies Used

- Oracle VirtualBox
- Windows Server 2022
- Windows 11
- Ubuntu Linux
- Active Directory Domain Services (AD DS)
- DNS
- Kerberos Authentication
- SMB File Sharing
- NTFS Permissions
- Windows Defender Firewall
- Group Policy
- SSSD
- Realmd
- CIFS

---

# Network Topology

The diagram below illustrates the architecture of the homelab environment.

Network Diagram:![alt text](<images/Homelab diagram.drawio.png>)

---

# Virtual Environment Overview

The VirtualBox environment contains one Domain Controller, two Windows clients, one Ubuntu workstation, and one Kali Linux virtual machine reserved for future security testing. The Kali Linux machine was not joined to the domain and therefore not a part of this lab.

VirtualBox Overview: ![alt text](<images/Screenshot 2026-07-09 210952.png>)

---

# Project Features

✔ Active Directory Domain Deployment

✔ Organizational Unit (OU) Administration

✔ Security Groups

✔ Role-Based Access Control (RBAC)

✔ SMB File Shares

✔ Windows Firewall Hardening

✔ Ubuntu Domain Integration

✔ Kerberos Authentication

✔ DNS Name Resolution

✔ Group Policy Management

---

# Documentation

## Infrastructure

- [Active Directory](Active-Directory.md)
- [Organizational Units and Security Groups](OU-Security-Groups.md)

## Administration

- [Group Policy](Group-Policy.md)
- [File Server and RBAC](File-Server-RBAC.md)

## Security

- [Windows Firewall Hardening](Windows-Firewall.md)

## Linux Integration

- [Ubuntu Domain Integration](docs/linux-integration.md)

## Validation

- [Validation & Testing](docs/validation-testing.md)

## Reflection

- [Lessons Learned](docs/lessons-learned.md)
- [Future Improvements](docs/future-improvements.md)

---

# Skills Demonstrated

- Active Directory Administration
- Windows Server Management
- Domain Controller Deployment
- DNS Configuration
- Organizational Unit Design
- Security Group Administration
- RBAC
- SMB File Sharing
- NTFS Permissions
- Windows Defender Firewall
- Kerberos Authentication
- Linux Domain Integration
- Virtualization
- Enterprise Documentation
