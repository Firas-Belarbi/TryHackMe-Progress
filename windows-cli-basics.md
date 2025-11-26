# Windows Command Line – Practical Notes (TryHackMe Room)

This document summarizes my practical work in a Windows Command Line room on TryHackMe.  
The goal was to control a Windows machine remotely using SSH and work only from the command line (CLI) instead of a graphical user interface (GUI).

---

## 1. Remote Access via SSH

I connected to a Windows target from the TryHackMe AttackBox using SSH:

```bash
ssh user@MACHINE_IP
```

### Steps:
- Opened the terminal in the AttackBox.
- Used `ssh user@MACHINE_IP` to connect.
- Accepted the fingerprint prompt with `yes` the first time.
- Entered the password (input is invisible for security).
- Worked entirely inside CMD on the remote Windows host.

---

## 2. Common Issues Encountered and Lessons Learned

### 2.1 Path and File Errors

At one point I ran:

```cmd
type C: \Treasure\Hunt\secret
```

This resulted in:

- "The system cannot find the path specified"
- "Access is denied"

#### What I learned:

- Paths must be written correctly without extra spaces:

```cmd
C:\Treasure\Hunt\secret
```

- `type` works on files, not directories.
- Use `cd` and `dir` to verify your location:

```cmd
cd C:\Treasure\Hunt
dir
type flag.txt
```

**Lesson:**  
Always confirm the path and whether you are dealing with a file or a directory before running commands.

---

### 2.2 Switching from GUI Thinking to CLI Thinking

Before this room I was used to:

- Clicking with the mouse  
- Using File Explorer  
- Navigating visually  

In CLI:

- GUI is easier but slower  
- CLI is faster, automatable, and better for remote work  

| Task | GUI | CLI |
|------|------|------|
| Check IP | Open Network Settings | `ipconfig` |
| List files | Open folders | `dir` |
| Navigate | Double-click folders | `cd` |

---

## 3. Core Windows Commands Practiced

### 3.1 File and Directory Operations

```cmd
cd                # change directory
dir               # list files and folders
tree              # show folder structure
mkdir folder      # create folder
rmdir folder      # remove folder
copy src dst      # copy files
move src dst      # move files
del file          # delete files
type file.txt     # show file contents
more file.txt     # view file by page
```

---

### 3.2 Networking

```cmd
ipconfig
ipconfig /all
ping host
tracert host
nslookup domain
netstat
netstat -abon
```

---

### 3.3 System Information

```cmd
ver
systeminfo
set
systeminfo | more
```

---

### 3.4 Processes

```cmd
tasklist
tasklist /FI "imagename eq X"
taskkill /PID 1234
```

---

### 3.5 Power Control

```cmd
shutdown /s     # shutdown
shutdown /r     # restart
shutdown /a     # abort shutdown
```

---

## 4. How I Handle New Commands

### 4.1 Built-in Help

```cmd
command /?
```

Examples: `ipconfig /?`, `netstat /?`, `tasklist /?`

---

### 4.2 Paging Long Output

```cmd
systeminfo | more
driverquery | more
```

---

## 5. Relevance to Cybersecurity

Command-line skills are essential in real cyber operations:

### Typical access in real attacks:

- Reverse shell  
- PowerShell or CMD session  
- SSH access  
- No GUI available  

### You must be able to:

- Navigate the file system  
- Search for sensitive files  
- Read logs and configurations  
- Inspect network connections  
- Manage processes and services  

This room gave me foundation skills needed for Windows exploitation and defensive security.

---

## 6. Personal Summary

From this room I learned:

- How to connect to a Windows machine over SSH and work entirely from CLI.
- How to fix common mistakes like path issues.
- Why CLI is critical for cybersecurity.
- Core Windows commands useful for all future labs.
- How to discover and understand any new command using `/?` and `| more`.

---
