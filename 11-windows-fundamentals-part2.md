# Windows Fundamentals Part 2 – TryHackMe

## Overview
This room continues the introduction to Windows internals by focusing on system configuration tools, security features, system resource management, and administrative interfaces.  
These components are important for identifying abnormal behavior and investigating security alerts.

---

## Key Concepts

### 1. System Configuration (msconfig)
The System Configuration tool provides options to manage:
- Boot settings  
- Services  
- Startup behavior  
- Diagnostic modes  

Analysts use msconfig to review suspicious startup entries or disable unsafe configurations.

---

## 2. Task Manager (Advanced Use)
Task Manager provides visibility into:
- Running processes  
- CPU, RAM, disk, and network usage  
- Startup applications  
- Services

Security relevance:
- Identifying unknown or high-usage processes  
- Detecting persistence through startup items  
- Observing unusual network activity  

---

## 3. Resource Monitor
Resource Monitor gives detailed insights into:
- CPU usage per process  
- Disk I/O  
- Network connections  
- Memory allocation

Useful for detecting:
- Malware generating unusual traffic  
- Processes accessing unexpected files  
- High disk usage caused by malicious activity  

---

## 4. Disk Management
Provides information on:
- Partitions  
- File systems  
- Mounted drives  
- System reserved partitions

Analysts check for:
- Hidden or encrypted partitions  
- Suspicious mounted volumes  
- USB device activity  

---

## 5. System Information (msinfo32)
Shows full hardware and software inventory:
- BIOS version  
- Drivers  
- Startup programs  
- Environment variables  
- Running services

Good reference point during investigations.

---

## 6. User Accounts and Permissions
Windows distinguishes between:
- Standard accounts  
- Administrator accounts  
- Built-in system accounts (SYSTEM, LOCAL SERVICE)

Privilege concepts relevant to security:
- Privilege escalation attempts  
- Misconfigured permissions  
- Accounts added without authorization  

---

## 7. Security Tools Overview
The room covers several built-in security utilities:

### Windows Defender
- Real-time protection  
- Signature-based detection  
- Quarantine management  

### Firewall
- Controls inbound and outbound traffic  
- Can be misconfigured or disabled by malware  

### UAC
- Prevents unauthorized system changes  
- Critical for stopping privilege escalation  

---

## 8. Windows Update
Important for:
- Patch management  
- Closing vulnerabilities  
- Stability and security improvements  

Attackers commonly exploit outdated systems.

---

## Relevance to SOC Work
SOC analysts frequently analyze:
- Unexpected services or processes  
- Startup persistence  
- Disabled antivirus or firewall  
- Unauthorized admin accounts  
- High-usage processes  
- Suspicious network connections  

This room strengthens the ability to validate alerts quickly and identify compromised systems.

---

## Summary
Windows Fundamentals Part 2 explains essential administrative and security tools such as msconfig, Task Manager (advanced view), Resource Monitor, Disk Management, account permissions, and built-in security features.  
These concepts are critical for detecting and investigating malicious behavior on Windows endpoints.
