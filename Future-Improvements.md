# Future Improvements

## Overview

I designed this homelab to be an evolving enterprise environment rather than a one-time project. While the current implementation provides centralized identity management, Group Policy administration, file services, endpoint security, and Linux integration, several additional technologies are planned to further simulate a production enterprise network.

My next steps for this lab will focus on network security, monitoring, automation, and defensive cybersecurity.

---

# pfSense Firewall

My plan for the next phase of the lab is to replace the current bridged network with a dedicated pfSense firewall.

Planned features include:

- Dedicated virtual firewall appliance
- Centralized routing
- Stateful packet inspection
- Network Address Translation (NAT)
- Firewall rule management
- Secure VPN access
- Improved network segmentation

This will introduce enterprise-grade perimeter security while allowing greater control over network traffic between systems.

---



# Wazuh SIEM

I plan on deploying a Wazuh SIEM platform to centralize log collection across Windows and Linux systems.

Planned capabilities include:

- Windows Event Log collection
- Linux log collection
- Security monitoring
- Alert generation
- File integrity monitoring
- Compliance reporting

This will provide greater visibility into activity occurring throughout the environment.

---

# Security Onion

Security Onion may be introduced as a dedicated network monitoring platform.

Capabilities include:

- Network intrusion detection
- Packet capture
- Zeek analysis
- Suricata IDS
- Network traffic investigation

Combining Security Onion with Wazuh would provide both host-based and network-based visibility.

---


# Active Directory Security Testing

To better understand enterprise security from both defensive and offensive perspectives, I plan on using the Kali Linux workstation I currently have set up to be used to perform testing against the lab environment.

Planned activities include:

- LDAP enumeration
- SMB enumeration
- Kerberos analysis
- Password auditing
- Active Directory reconnaissance
- Privilege escalation testing

All testing will be performed exclusively within the isolated lab environment.

---

# Automation

I also plan on including greater automation of administrative tasks, such as:

- PowerShell scripting
- Bash scripting
- Scheduled maintenance tasks
- Automated backups
- User provisioning automation

Automation reduces repetitive administrative work while improving consistency across the environment.

---

# Long-Term Goals

My long-term objective of this homelab is to simulate a realistic enterprise infrastructure that combines Windows administration, Linux administration, networking, cybersecurity, and automation.

As additional technologies are implemented, this documentation will continue to expand, reflecting the ongoing development of the environment.

---

# Planned Technologies

| Technology | Status |
|------------|--------|
| Active Directory | ✅ Complete |
| Organizational Units & Security Groups | ✅ Complete |
| Group Policy | ✅ Complete |
| File Server & RBAC | ✅ Complete |
| Windows Firewall Hardening | ✅ Complete |
| Linux Integration | ✅ Complete |
| pfSense Firewall | 🔄 Planned |
| Wazuh SIEM | 🔄 Planned |
| Security Onion | 🔄 Planned |
| Active Directory Security Testing | 🔄 Planned |
| Automation | 🔄 Planned |