# Windows Defender Firewall Hardening

## Overview

I used Windows Defender Firewall with Advanced Security to implement some basic host-based security controls across the Active Directory environment.

Rather than relying on the default Windows Firewall configuration, I configured custom inbound rules to limit unnecessary network exposure while allowing only authorized communication between trusted systems.

These rules simulate common enterprise firewall practices by restricting administrative protocols and disabling insecure legacy services.

---

# Objectives

The objectives of this phase were to:

- Reduce the Windows attack surface
- Restrict network access to trusted hosts
- Block insecure protocols
- Protect file sharing services
- Demonstrate host-based firewall management

---

# Firewall Rule Overview

Four custom firewall rules were implemented as part of the hardening process.

| Rule | Action | Purpose |
|------|--------|---------|
| Allow ICMP from Domain Workstations | Allow | Permit ping requests only from trusted domain clients |
| Allow SMB from Domain Workstations | Allow | Restrict Windows file sharing to authorized systems |
| Block Telnet | Block | Disable insecure remote administration |
| Block FTP | Block | Prevent use of an unencrypted file transfer protocol |

Together, these rules reduce unnecessary network exposure while allowing normal domain functionality.

Windows Firewall Inbound rule list. Only the first four were ones I configured: ![alt text](<images/Screenshot 2026-07-15 032428.png>)

---

# ICMP Restriction

I created a custom inbound rule to allow ICMP Echo Requests only from trusted domain workstations.

Restricting ICMP in this manner allows administrators to verify connectivity from managed systems while preventing unsolicited ping traffic from untrusted devices.

This approach reduces unnecessary network visibility without affecting legitimate administrative troubleshooting.

![alt text](<images/Screenshot 2026-07-15 032440.png>)

---

# SMB Restriction

Windows file sharing (SMB) was restricted so that only trusted domain workstations could communicate with the file server.

Restricting SMB access helps protect shared resources from unauthorized systems while ensuring that legitimate users retain access to departmental file shares.

This configuration complements the Role-Based Access Control (RBAC) model implemented through Active Directory Security Groups.

![alt text](<images/Screenshot 2026-07-15 032449.png>)

---

# Blocking Insecure Protocols

Legacy protocols such as Telnet and FTP transmit sensitive information without encryption and are considered insecure for enterprise environments.

I created inbound firewall rules to block these protocols, reducing the likelihood of accidental use while encouraging secure alternatives such as SSH and SFTP.

Disabling outdated protocols is a common security hardening practice and helps enforce modern security standards.

![alt text](<images/Screenshot 2026-07-17 033447.png>)
![alt text](<images/Screenshot 2026-07-17 033456.png>)

---

# Validation

Each firewall rule was tested after deployment to verify that the intended traffic was either permitted or blocked.

Validation included:

- Confirming ICMP requests succeeded only from trusted systems.
- Verifying SMB access from authorized workstations.
- Confirming Telnet connections were blocked.
- Confirming FTP connections were blocked.
- Reviewing rule status in Windows Defender Firewall with Advanced Security.

![alt text](<images/Screenshot 2026-07-17 034045.png>)

---

# Enterprise Benefits

Implementing custom firewall rules provides several advantages:

- Reduces the attack surface
- Protects administrative services
- Restricts unnecessary network traffic
- Blocks insecure legacy protocols
- Supports defense-in-depth
- Improves endpoint security

---

# Skills Demonstrated

- Windows Defender Firewall
- Windows Firewall with Advanced Security
- Host-Based Firewall Administration
- Network Security
- Windows Server Administration
- Endpoint Hardening
- Principle of Least Privilege