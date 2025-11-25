# Windows Fundamentals Part 3 – TryHackMe

## Overview
This room focuses on additional Windows administration tools, system utilities, user management, disk operations, and environment configurations.  
These components are frequently referenced during endpoint analysis and incident triage.

---

## Key Concepts

### 1. System Utilities Overview
The room covers several built-in utilities used for system inspection and troubleshooting.

#### System Tools
- **System Information (msinfo32)**  
  Hardware, drivers, boot configuration, environment variables.

- **Task Scheduler**  
  Automates tasks. Common persistence point for malware.

- **Disk Cleanup**  
  Maintenance utility. Not security-critical but often used by attackers to remove traces.

---

### 2. Command Line and PowerShell Review
The room expands on previous usage:

#### CMD
Basic commands used for inspection:
```
ipconfig
netstat -ano
tasklist
```

#### PowerShell
More advanced system queries:
```
Get-Service
Get-LocalUser
Get-EventLog -LogName Security -Newest 20
```

PowerShell is also an attack surface due to script execution and built-in automation capabilities.

---

### 3. Event Viewer (Detailed)
Event Viewer logs are crucial for SOC investigations.

Key log categories:
- **Application**
- **System**
- **Security**

Examples of notable security events:
- Logon attempts  
- Privilege escalation  
- Policy changes  
- Service creation  
- Process execution  

Logs provide context during triage and correlation inside SIEM systems.

---

### 4. User Accounts and Groups
Windows manages users through local accounts and built-in groups.

Important groups:
- **Administrators**  
- **Users**  
- **Guests**  
- **Remote Desktop Users**  
- **Backup Operators**

Security relevance:
- Unauthorized admin accounts  
- Privilege escalation  
- Misconfigured group permissions  

---

### 5. Disk Management
The room explains:
- Partition structure  
- Reserved system partitions  
- Disk status and volume types  
- Mounting removable media  

Analysts may check for:
- Hidden partitions  
- Suspicious encrypted containers  
- Unauthorized external storage usage  

---

### 6. Control Panel and Settings
Two management interfaces:
- **Control Panel** (legacy)
- **Settings** (modern)

Both expose configuration areas for:
- Network settings  
- User accounts  
- Privacy options  
- Installed applications  

These areas are often modified during post-compromise activity.

---

### 7. Windows Services
Services run background processes.

Key concepts:
- Automatic vs Manual vs Disabled  
- Service execution accounts  
- Service configuration paths  

Suspicious indicators:
- Unknown services  
- Services pointing to non-standard directories  
- Recently created services  
- Services running from user directories  

---

## Relevance to SOC Work
The tools and concepts in this room assist with:
- Verifying suspicious processes or services  
- Checking recent log entries  
- Investigating privilege escalation  
- Confirming integrity of system configuration  
- Detecting persistence mechanisms  
- Understanding endpoint behavior during an incident  

Mastering the Windows environment is essential for effective alert triage.

---

## Summary
Windows Fundamentals Part 3 builds on previous topics by introducing deeper administrative tools, log analysis, user/group management, disk operations, and service inspection.  
These skills form a foundation for detecting malicious behavior on Windows endpoints and for progressing into Windows security and incident response.
