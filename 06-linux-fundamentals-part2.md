# Linux Fundamentals (Part 2) – TryHackMe

## 🧩 Room Overview
This room continues building foundational Linux knowledge by introducing user management, processes, services, system monitoring, and privilege concepts.  
These skills are essential for security analysts, administrators, and penetration testers.

- Platform: **TryHackMe**
- Path: **Linux Fundamentals**
- Status: ✅ Completed
- Focus: Processes, users, groups, permissions, system monitoring, service control

---

## 🎯 Learning Objectives

- Manage users and groups  
- Understand Linux processes (foreground/background)  
- Monitor system activity and running programs  
- Control system services using `systemctl`  
- Use essential tools like `ps`, `top`, and `htop`  
- Understand privilege escalation basics  
- Strengthen terminal and administrative skills  

---

## 🔑 Key Concepts Learned

### 1. User & Group Management

Linux is a multi-user OS. Common commands:

```bash
sudo adduser alice
sudo passwd alice
sudo usermod -aG sudo alice
groups alice
id alice
```

Important files:

- `/etc/passwd` → user information  
- `/etc/shadow` → password hashes  
- `/etc/group` → group definitions  

---

### 2. Understanding Processes

Every running program is a **process**.

View running processes:

```bash
ps aux
top
htop
```

Managing processes:

```bash
kill PID
kill -9 PID        # force kill
fg                 # bring job to foreground
bg                 # send job to background
jobs               # list background jobs
```

---

### 3. Services & systemctl

Linux services = background programs.

```bash
systemctl status ssh
systemctl start ssh
systemctl stop ssh
systemctl restart ssh
systemctl enable ssh    # start on boot
```

---

### 4. File Searching Tools

```bash
find / -name file.txt
locate password
grep "error" /var/log/syslog
grep -R "keyword" /etc/
```

These are used heavily in investigations and log analysis.

---

### 5. Environment & Variables

```bash
echo $PATH
export NAME=Firas
env
```

---

### 6. Permissions (Advanced)

Change ownership:

```bash
sudo chown user:group file
```

Symbolic permissions:

```bash
chmod u+rwx file
chmod g-w file
chmod o-r file
```

---

### 7. Privilege Escalation Basics

Part of the room explains:

- What is a privileged user (root)  
- Why attackers target misconfigurations  
- How Linux enforces permission boundaries  
- How to safely use `sudo`  

---

## 🧪 Practical Skills Gained

During the room, I practiced:

- Creating users and assigning groups  
- Monitoring processes with ps/top  
- Killing, suspending, and controlling processes  
- Starting and stopping services  
- Searching system files  
- Editing system configuration files  
- Reading Linux logs  

These are **real-world SOC and sysadmin skills**.

---

## 🧠 Relevance to My Future SOC Role

SOC Analysts frequently:

- Investigate suspicious processes  
- Check active services  
- Validate running commands  
- Analyze logs in `/var/log/`  
- Detect unauthorized users  
- Review privilege changes  
- Monitor CPU/memory for anomalies  

Part 2 builds the *core operational knowledge* needed for every investigation.

---

## 📝 Summary

Linux Fundamentals Part 2 strengthened my understanding of how Linux works under the hood.  
I learned user management, processes, services, environment variables, advanced permissions, and essential administration commands — all of which are critical for security operations and penetration testing.
