# Group Policy Management

## Overview

Group Policy Objects (GPOs) provide centralized management for Windows computers and users within an Active Directory environment. Rather than configuring each workstation individually, administrators can deploy settings across the entire domain from a single management console.

Within this homelab, I used Group Policy to automate workstation configuration and demonstrate enterprise administration practices.

---

# Objectives

My objectives of this phase were to:

- Deploy centralized workstation configuration
- Eliminate manual local administration
- Demonstrate Role-Based Administration
- Verify policy deployment across multiple computers
- Prepare the environment for future enterprise security policies

---

# Group Policy Infrastructure

The Group Policy Management Console was used to create and manage domain policies.

The custom Group Policy Objects created during this project were linked to the appropriate Organizational Unit and automatically applied to users and domain-joined workstations.

This demonstrates how enterprise administrators centrally manage hundreds or thousands of users and computers without configuring each device or account individually.

Group Policy Management Console in DC01: ![alt text](<images/Screenshot 2026-07-17 021453.png>)

---

# IT Helpdesk Local Administrator Policy

A custom Group Policy Object was created to automatically add members of the **IT Helpdesk** security group to the local **Administrators** group on every managed workstation.

Rather than manually adding administrators on each computer, membership is controlled through Active Directory.

Benefits include:

- Centralized administration
- Consistent workstation configuration
- Reduced administrative effort
- Easier onboarding and offboarding
- Improved security through Role-Based Access Control (RBAC)

Adding "IT Helpdesk" group to Administrators on DC01: ![alt text](<images/Screenshot 2026-07-10 014221.png>)

IT Helpdesk Local Admin Policy: ![alt text](<images/Screenshot 2026-07-10 011755.png>)

Verifying the policy is applied and works on CLIENT01: ![alt text](<images/Screenshot 2026-07-17 020908.png>)

![alt text](<images/Screenshot 2026-07-17 021245.png>)
---

# Account Security Policy

I configured a domain-wide password policy through the Account Security Policy to enforce stronger authentication requirements across all domain users.

The policy was designed to simulate enterprise security standards by requiring complex passwords, defining password history, enforcing password expiration, as well as defining account lockout rules.

Centralizing these settings ensures that every user account within the domain follows the same security baseline without requiring manual configuration on individual systems.

![alt text](<images/Screenshot 2026-07-10 010036.png>)
![alt text](<images/Screenshot 2026-07-10 010047.png>)
![alt text](<images/Screenshot 2026-07-10 010229.png>)

Verifying policy is applied on CLIENT01: ![alt text](<images/Screenshot 2026-07-17 020908.png>)

---

# Network Drive Mapping

Group Policy Preferences were used to automatically map department file shares when users logged into domain-joined workstations.

Rather than requiring users to manually connect to network resources, I configured the appropriate drive mappings to be applied automatically based on a user's department.

This approach simplifies user onboarding while ensuring consistent access to organizational resources.

![alt text](<images/Screenshot 2026-07-14 210516.png>)
![alt text](<images/Screenshot 2026-07-14 210845.png>)
![alt text](<images/Screenshot 2026-07-14 210856.png>)
![alt text](<images/Screenshot 2026-07-14 210917.png>)

Verifying policy is applied on CLIENT01: ![alt text](<images/Screenshot 2026-07-17 020923.png>)

HR Team member viewing their respective network drive on CLIENT02: ![alt text](<images/Screenshot 2026-07-14 215533.png>)

---

# Policy Deployment

Once I configured my Group Policy Object, the following steps were performed:

1. Updated Group Policy on the client using:

```
gpupdate /force
```

2. Restarted the workstation

3. Logged in as IT Helpdesk user

4. Verified local administrator membership

5. Verified correct network drive access

6. Logged in as HR Team user and Accounting user

7. Verified correct network drive access

I was able to confirm that the policy successfully applied from the Domain Controller to the workstation.

---

# Policy Validation

Policy deployment was verified using several methods.

Validation included:

- Group Policy Management Console
- gpupdate /force
- gpresult /r
- Local Administrators group
- Administrative command execution

Successful validation confirmed that the policy was functioning as intended.

---

# Enterprise Benefits

Using Group Policy provides several advantages over manual workstation administration.

- Centralized management
- Automated workstation configuration
- Consistent security settings
- Simplified administration
- Faster deployment
- Reduced configuration drift

These advantages make Group Policy one of the most important management tools in enterprise Windows environments.

---

# Skills Demonstrated

- Group Policy Management
- Group Policy Objects (GPO)
- Centralized Windows Administration
- Active Directory Administration
- Role-Based Administration
- Enterprise Workstation Management
- Windows Security