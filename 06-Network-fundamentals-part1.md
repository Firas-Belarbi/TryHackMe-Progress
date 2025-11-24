# Network Fundamentals (Part 1) – TryHackMe

## 🧩 Room Overview
This room introduces the essential building blocks of computer networking.  
It explains how devices communicate, what networks are made of, and the key concepts needed for cybersecurity, SOC analysis, and penetration testing.

- Platform: **TryHackMe**
- Path: **Introduction / Networking Basics**
- Status: ✅ Completed
- Focus: Understanding basic network components and communication models

---

## 🎯 Learning Objectives

- Understand what a network is and why networking is important  
- Learn how devices communicate across local and remote networks  
- Understand the difference between LAN, WAN, and the Internet  
- Learn basic networking terminology  
- Gain foundational knowledge for SOC, Pentesting, and Systems Administration  

---

## 🔑 Key Concepts Learned

### 1. What is a Network?
A network is a group of devices connected together to share:

- Data  
- Resources  
- Services (like websites, applications, files)

Common examples:
- Home WiFi  
- University campus network  
- Internet cafés  
- Corporate enterprise networks

---

### 2. LAN vs WAN

#### **LAN (Local Area Network)**  
- Small geographical area  
- Usually your home or office  
- Consists of routers, switches, PCs, printers  
- Faster and controlled by one organization  

#### **WAN (Wide Area Network)**  
- Large geographical area  
- Internet Service Providers (ISPs)  
- Connects multiple LANs together (the internet)

---

### 3. Network Devices

#### **Router**  
- Connects networks together  
- Forwards traffic between LAN ↔ WAN  
- Gives IP addresses using DHCP  

#### **Switch**  
- Connects devices inside a LAN  
- Uses MAC addresses  
- Much faster than hubs  

#### **Access Point (AP)**  
- Provides wireless (WiFi) connectivity  
- Connects wireless devices to the LAN  

#### **Firewall**  
- Filters traffic  
- Blocks malicious connections  
- Used in SOC & enterprise environments  

---

### 4. IP Addresses (High-Level)

IP address = identifier for a device.

Example:
```
192.168.1.10
```

Two versions:
- IPv4 (most common)
- IPv6 (newer, larger address space)

---

### 5. MAC Address

A unique hardware address given to each network card.

Example:
```
A4:6C:2C:59:1F:8B
```

Used for LAN communication.

---

### 6. Packets

All data on the network (messages, browsing, emails) is broken into **packets**.

Each packet has:
- Source IP  
- Destination IP  
- Data  
- Port number  
- Protocol (TCP/UDP)

---

### 7. Ports & Protocols (Basic Intro)

Ports identify applications/services.

Examples:

| Service | Port |
|---------|------|
| HTTP | 80 |
| HTTPS | 443 |
| SSH | 22 |
| DNS | 53 |

Protocols:
- **TCP** (reliable, connection-based)  
- **UDP** (fast, no connection)

---

## 🧪 Practical Skills Gained

- Identifying network components  
- Understanding how data moves across networks  
- Recognizing the difference between LAN/WAN  
- Learning about routers, switches, APs, firewalls  
- Understanding IP, MAC, packets, and ports  

These concepts are the core foundation of every cybersecurity field.

---

## 🧠 Relevance to My Future SOC Role

SOC Analysts constantly analyze:

- Traffic  
- Packets  
- IP addresses  
- Ports  
- Protocols  
- Suspicious network behavior  

Without this fundamental networking knowledge, analyzing alerts is impossible.

This room builds the networking base required before working with SIEM tools or analyzing attacks.

---

## 📝 Summary

Network Fundamentals Part 1 taught me the basics of how networks work, including LAN/WAN, routers, switches, IP addressing, ports, and packets.  
This knowledge is essential for all future cybersecurity tasks, including SOC, pentesting, and network analysis.
