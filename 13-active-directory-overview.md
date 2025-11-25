# Active Directory – Technical Overview and Hands-On Summary

## Overview
This document summarizes the key concepts and hands-on tasks completed in the TryHackMe Active Directory room.  
The focus is understanding AD DS structure, objects, authentication protocols, Group Policy, delegation, and domain organization.  
The notes reflect practical operations performed inside a live Windows domain lab.

---

## 1. Active Directory Domain Services (AD DS)
AD DS provides centralized identity, authentication, authorization, and policy enforcement.

Key components:
- Domain Controller (DC): Hosts the AD database and authentication services.
- Objects: Users, computers, groups, OUs, printers, shares.
- Centralized management model used by enterprise environments.

---

## 2. AD Objects
### Users
Security principals that can authenticate.  
Types:
- Human users
- Service accounts (e.g., MSSQL, IIS)

### Computer Accounts
Created automatically when a machine joins the domain.  
Format: `COMPUTERNAME$`  
Uses long, automatically rotating passwords.

### Security Groups
Used for authorization.  
Groups can contain users, computers, or other groups (nested groups).

Important built-in groups:
- Domain Admins  
- Enterprise Admins  
- Backup Operators  
- Server Operators  
- Account Operators  
- Domain Users / Computers / Controllers

---

## 3. Organizational Units (OUs)
OUs provide structure and allow applying Group Policy.  
A user (or computer) belongs to exactly one OU.  
OUs represent departments or device categories: IT, Sales, HR, Marketing, Workstations, Servers.

Difference:
- OU = Policy application  
- Group = Permission management

---

## 4. Delegation of Control
Delegation allows assigning limited administrative permissions on specific OUs without granting Domain Admin rights.

Example completed in lab:
- Delegated “Reset Password” permission to user *Phillip* for the Sales OU.

Delegation procedure:
- Delegate Control → Select user → Assign specific permissions.

---

## 5. PowerShell for Active Directory
PowerShell commands used:
```
Set-ADAccountPassword
Set-ADUser
Get-ADUser
gpupdate /force
```
Used to reset passwords and apply policies when ADUC was unavailable.

---

## 6. Remote Desktop Protocol (RDP)
RDP sessions established using:
- Administrator  
- Phillip  
- Sophie  
- Mark  

Domain login pattern:
```
THM\username
```

Used to test GPO application and account permissions.

---

## 7. Computer OU Cleanup
By default, all joined machines appear under the “Computers” container.  
Performed cleanup by moving devices into appropriate OUs:
- Workstations  
- Servers  
- Domain Controllers (already assigned)

---

## 8. Group Policy Objects (GPOs)
GPOs allow centralized configuration for users and computers.

Two main categories:
- Computer Configuration  
- User Configuration

GPOs created and tested:

### Control Panel Restriction
- Blocked access for Sales, Marketing, and Management.
- IT OU excluded from restrictions.

### Auto Lock Screen
- Configured screen lock after 5 minutes of inactivity.
- Applied at domain root level.

Policy application command:
```
gpupdate /force
```

---

## 9. SYSVOL
SYSVOL is a replicated folder on all Domain Controllers.  
Stores:
- GPO files  
- Login scripts

Location:
```
C:\Windows\SYSVOL\sysvol\
```

---

## 10. Kerberos Authentication
Default authentication protocol in modern AD domains.

Key elements:
- TGT (Ticket Granting Ticket)
- TGS (Service Ticket)
- KDC (Key Distribution Center) runs on the DC
- TGT encrypted with the `krbtgt` account

Kerberos was observed during authentication events inside the lab.

---

## 11. NetNTLM
Legacy authentication protocol based on challenge–response.  
Does not send passwords across the network.  
Still present for compatibility reasons.

---

## 12. Trees and Forests
### Trees
Domains sharing a continuous namespace:
- thm.local  
- uk.thm.local  

### Forests
Collection of trees with different namespaces:
- thm.local  
- mht.local  
- example.com  

Enterprise Admins have highest privileges across the entire forest.

---

## 13. Trust Relationships
Trust allows users in Domain A to access resources in Domain B.

Types:
- One-way trust  
- Two-way trust  

Joining a forest or tree automatically creates required trusts.

---

## 14. Hands-On Tasks Completed
- Logged into multiple machines via RDP.
- Reset passwords using PowerShell.
- Created and organized OUs (IT, Sales, Marketing, etc.).
- Deleted protected OUs after disabling accidental deletion.
- Created users and groups.
- Delegated password reset permissions.
- Configured and tested multiple GPOs.
- Modified password policy (minimum password length).
- Ran `gpupdate` and verified GPO propagation.
- Tested Control Panel restrictions under different users.
- Examined Kerberos and NTLM behavior.
- Reviewed SYSVOL structure.
- Organized Workstations and Servers into proper OUs.
- Validated policy inheritance by logging in with multiple accounts.

---

## 15. Summary Statements Suitable for CV or GitHub
- Implemented domain restructuring including OUs, GPOs, delegation, and AD object management.
- Enforced enterprise policies such as password complexity, Control Panel restrictions, and inactivity lock.
- Managed AD objects using PowerShell for password resets and configuration changes.
- Organized domain computers into Workstations and Servers OUs.
- Tested Kerberos authentication flows and observed TGT/TGS operations.
- Applied GPOs through SYSVOL and validated inheritance across user accounts.
