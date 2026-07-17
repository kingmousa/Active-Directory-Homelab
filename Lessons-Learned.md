# Lessons Learned

## Overview

Building this Active Directory homelab provided practical experience far beyond simply installing Windows Server. Throughout the project, I encountered several real-world configuration challenges involving authentication, networking, permissions, Group Policy, and Linux integration.

Troubleshooting these issues strengthened my understanding of enterprise system administration and reinforced the importance of methodical problem solving.

---

# Active Directory Depends on DNS

One of the first lessons learned was that Active Directory relies heavily on DNS.

During early configuration and client domain joins, proper DNS settings were essential for locating the Domain Controller, authenticating users, and applying Group Policy. I had to ensure that the DNS Server on every workstation was pointing to the Domain Controller and not the router. If it was not pointing to the DC, the workstations could not locate and join the domain.

This reinforced that Active Directory is fundamentally a directory service built around DNS rather than simply a Windows login system.

---

# Kerberos Requires Accurate Time Synchronization

While joining the Ubuntu workstation to Active Directory, Kerberos authentication initially failed because the Linux system's clock was not synchronized with the Domain Controller.

I spent a good amount of time troubleshooting trying to figure out the issue. Eventually, I realized that the date and time was off by a couple days between the Domain Controller and Ubuntu workstation. After fixing the date and time for both, I was finally able to join the Ubuntu VM to the domain.

What I learned from this one step is that you will often spend more time troubleshooting trying to fix a problem than you will actually configuring or setting things up.

---

# Group Policy Does Not Apply Instantly

Another important lesson I learned was understanding how Group Policy is processed.

Configuration changes made on the Domain Controller were not immediately reflected on client workstations until I refreshed the Group Policy on each workstation.

Using tools such as:

- gpupdate /force
- gpresult /r

made it possible to verify successful policy deployment and troubleshoot configuration issues.

I also realized that Group Policies only applied to Windows workstations and therefore Linux workstations require more configurations to actually have it set up the same as Windows. Group policies such as account security and network shares did not apply to the Ubuntu workstation, though I was able to grant IT Helpdesk users sudo privileges which is nice. Going forward, I would like to change this so that all the policies will apply to the Ubuntu workstation.

---

# Effective Permissions Are Layered

Implementing the file server showed me that access control is determined by multiple permission layers.

Successful access depended on:

- Active Directory Security Group membership
- SMB Share Permissions
- NTFS Permissions

Understanding how these layers work together was essential for correctly implementing Role-Based Access Control.


# Security Is Built in Layers

This project showed me the importance of defense-in-depth.

Security was implemented at multiple layers including:

- Active Directory authentication
- Password Policy
- Security Groups
- Role-Based Access Control (RBAC)
- Windows Defender Firewall
- Linux sudo administration

Each security control complements the others rather than replacing them.

---

# Key Takeaways

Completing this project significantly improved my understanding of enterprise infrastructure and Windows administration.

Some of the most valuable skills I gained include:

- Active Directory deployment
- DNS administration
- Group Policy management
- Windows Server administration
- Linux integration with Active Directory
- Windows Defender Firewall management
- Role-Based Access Control (RBAC)
- Enterprise troubleshooting methodologies

The experience I gained throughout this project provided practical knowledge that will help me better in understanding the day-to-day responsibilities of an IT professional.