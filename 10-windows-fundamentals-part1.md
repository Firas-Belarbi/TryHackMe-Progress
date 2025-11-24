# Windows Fundamentals Part 1 – TryHackMe

## Overview
This room introduces the core components of the Windows operating system.  
It covers the graphical interface, essential system tools, file system structure, and basic configuration utilities.  
Understanding these fundamentals is important for SOC analysts who handle alerts originating from Windows endpoints.

---

## Key Concepts

### 1. Windows Interface Components
- **Desktop**: Main workspace.
- **Taskbar**: Running applications and system tray.
- **Start Menu**: Access to programs and settings.
- **File Explorer**: Navigation of the file system.

### 2. File System Structure
Windows uses **NTFS**. Important locations:
- `C:\Users\<User>` – User profile data  
- `C:\Windows` – System files  
- `C:\Program Files` – Installed applications (64-bit)  
- `C:\Program Files (x86)` – Installed applications (32-bit)

Common file extensions:
- `.exe` (executables)  
- `.dll` (libraries)  
- `.bat/.cmd` (batch scripts)  
- `.ps1` (PowerShell scripts)

### 3. System Settings
Tools presented in the room:
- **Control Panel** – Traditional configuration interface.
- **Settings App** – Modern configuration interface.
- **System Information (msinfo32)** – Hardware, drivers, OS details.
- **Task Manager** – Processes, performance, services, startup items.

### 4. User Account Control (UAC)
Windows uses UAC to prevent unauthorized changes.  
It distinguishes between:
- Standard user
- Administrator user

UAC prompts occur when elevated privileges are required.

### 5. Command-Line Basics
Two command-line environments were introduced:
- **Command Prompt (cmd.exe)**
- **PowerShell**

Examples:
```
dir
cd C:\Windows
ipconfig
```

PowerShell provides advanced management capabilities through cmdlets:
```
Get-Process
Get-Service
Get-EventLog
```

### 6. System Tools
Tools highlighted:
- **Run (Win + R)** – Quick access to utilities  
- **Registry Editor (regedit)** – Windows configuration database  
- **Event Viewer** – Critical for SOC analysis  
- **Task Scheduler** – Automates tasks (can be abused by attackers)

---

## Windows Logs (High-Level Intro)
The room introduces logging at a basic level:
- **Application Logs**
- **Security Logs**
- **System Logs**

Typical event categories:
- Logon events  
- Policy changes  
- Application behavior  
- System warnings/errors  

Logs are stored in:
`C:\Windows\System32\winevt\Logs`

Understanding log types is essential for alert triage.

---

## Practical Notes from the Room
- Navigating the interface is necessary for validating incidents.  
- Tools like Task Manager and Event Viewer are frequently used by analysts.  
- Windows stores large amounts of forensic information in logs and the registry.  
- Knowing where files and programs are located helps identify suspicious activity.

---

## Relevance to SOC Work
SOC analysts often investigate:
- Suspicious processes  
- Startup persistence  
- Failed logons  
- Privilege escalation attempts  
- Unknown executables in user directories  

This room provides the baseline knowledge required to understand Windows alerts in SIEM platforms.

---

## Summary
Windows Fundamentals Part 1 introduces the Windows environment, file system structure, administrative tools, UAC behavior, and essential command-line usage.  
This knowledge is foundational for detecting malicious activity on Windows systems and for progressing to deeper Windows security analysis.
