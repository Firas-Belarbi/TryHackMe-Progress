# Linux Fundamentals (Part 1) – TryHackMe

## 🧩 Room Overview
This room introduces the essentials of the Linux operating system.  
Linux is widely used in cybersecurity, servers, cloud computing, networking, and penetration testing.  
Mastering Linux is mandatory for SOC Analysts and ethical hackers.

- Platform: **TryHackMe**
- Path: **Introduction / Linux Basics**
- Status: ✅ Completed
- Focus: Commands, filesystem navigation, permissions, and terminal skills

---

## 🎯 Learning Objectives

- Understand how the Linux terminal works  
- Learn basic and essential Linux commands  
- Navigate the Linux filesystem  
- Work with files, directories, and permissions  
- Understand the Linux structure compared to Windows  
- Build confidence using Bash commands  

---

## 🔑 Key Concepts Learned

### 1. Linux vs Windows
- Windows uses GUI by default → Linux relies heavily on **terminal (CLI)**  
- Windows filesystems: NTFS, FAT → Linux filesystems: EXT4, XFS  
- Windows uses drives (C:, D:) → Linux has a **single root `/`**  
- Linux structure:

```
/
├── home
├── etc
├── var
├── usr
├── root
└── bin
```

---

### 2. Basic Terminal Commands

```bash
pwd          # Show current directory
ls           # List items in a directory
ls -la       # List all items with details
cd /path     # Change directory
cd ..        # Move one level up
clear        # Clear the terminal
whoami       # Display current user
```

---

### 3. Working with Files & Directories

```bash
touch file.txt        # Create a file
mkdir notes           # Create a directory
cp file1 file2        # Copy files
mv file1 newname      # Move/rename
rm file.txt           # Delete file
rm -r folder          # Delete folder recursively
```

---

### 4. Reading & Editing Files

```bash
cat file.txt          # Show file content
head file.txt         # First lines
tail file.txt         # Last lines
nano file.txt         # Edit in terminal
```

---

### 5. File Permissions  
Permissions appear like this:

```
-rwxr-x--x
```

Meaning:

- **r** - read  
- **w** - write  
- **x** - execute  

Three groups:

1. **User (owner)**
2. **Group**
3. **Others**

Changing permissions:

```bash
chmod 755 file.sh
chmod u+x script.sh
```

---

### 6. Package Management Basics  
(Debian/Ubuntu systems)

```bash
sudo apt update
sudo apt install package
sudo apt remove package
```

---

## 🧪 Practical Skills Gained

During this room, I practiced:

- Navigating Linux using only the terminal  
- Creating, modifying, and deleting files  
- Understanding directory structures  
- Using permissions properly  
- Working with text editors  
- Running basic scripts  

These are essential for SOC and pentesting tasks.

---

## 🧠 Relevance to My Future SOC Role

Linux is everywhere in cybersecurity:  
- Servers run Linux  
- Security tools run on Linux  
- SIEM agents collect logs from Linux  
- Attackers often use Linux systems  
- Malware frequently targets Linux servers  

A strong Linux foundation is mandatory for SOC Analysts.

---

## 📝 Summary

Linux Fundamentals Part 1 taught me the core basics needed for all future cybersecurity labs.  
It strengthened my command-line skills, filesystem understanding, and confidence in working inside Linux environments.
