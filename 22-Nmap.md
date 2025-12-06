# Nmap Study Summary  
## Part 1 — What I Learned

### 1. Basics of Nmap
- Nmap is a network scanning tool used to discover hosts, services, ports, and vulnerabilities.
- Commands use “switches” (arguments) such as -sS, -sU, -Pn, etc.

### 2. TCP Scan Types
- **TCP Connect Scan (-sT):** Performs the full TCP 3-way handshake (SYN → SYN/ACK → ACK). Reliable but not stealthy.
- **SYN “Half‑open” Scan (-sS):** Sends SYN, receives SYN/ACK, then sends RST instead of completing the handshake. Faster and stealthier; requires root privileges.
- **UDP Scan (-sU):** Sends UDP packets. No response = open|filtered, ICMP unreachable = closed. Slow due to UDP being stateless.

### 3. Stealth / Firewall‑Evasion Scan Types
- **NULL Scan (-sN):** Sends packets with no flags set.
- **FIN Scan (-sF):** Sends packets with the FIN flag.
- **Xmas Scan (-sX):** Sends packets with FIN, PSH, URG flags (looks “lit up” like a Christmas tree).
- All of them rely on RFC behavior: closed ports reply with RST; open ports remain silent. Effective for bypassing some firewalls.

### 4. Host Discovery (Ping Sweep)
- **Ping Sweep (-sn):** Scans entire subnets to discover active hosts using ICMP echo, ARP requests, and lightweight TCP probes.
- Example:  
  - `nmap -sn 192.168.0.1-254`  
  - `nmap -sn 192.168.0.0/24`

### 5. Nmap Scripting Engine (NSE)
- NSE scripts are written in **Lua** and extend Nmap with extra functionality.
- Script categories include: **safe, intrusive, vuln, exploit, auth, brute, discovery**.
- Scripts can detect vulnerabilities, brute‑force credentials, enumerate users, exploit services, or gather information.

### 6. Using NSE Scripts
- Run a category:  
  - `--script=vuln`
- Run specific scripts:  
  - `--script=smb-enum-users,smb-enum-shares`
- Scripts requiring parameters use:  
  - `--script-args <script>.<arg>=<value>`
- Script help:  
  - `nmap --script-help <script-name>`

### 7. Finding / Managing Scripts
- Scripts are stored in:  
  - `/usr/share/nmap/scripts/`
- Search scripts using:  
  - `grep "<keyword>" /usr/share/nmap/scripts/script.db`  
  - `ls /usr/share/nmap/scripts/*keyword*`
- Install missing scripts manually and update DB with:  
  - `nmap --script-updatedb`

### 8. Firewall Evasion
- **Block ICMP issue:** Windows firewall often blocks ICMP → Nmap thinks host is down.
- **Solution: -Pn** (treat all hosts as alive; skip ping).
- Extra evasion switches:
  - **-f:** Fragment packets.
  - **--mtu <number>:** Custom packet size, must be multiple of 8.
  - **--scan-delay <time>ms:** Slows scans to evade IDS rate detection.
  - **--badsum:** Sends packets with invalid checksums to detect firewalls.


## Part 2 — What I Practiced

### 1. Practiced Running Different Scan Types
- Ran -sT, -sS, -sU to compare handshake behavior.
- Tested NULL, FIN, and Xmas scans to see how targets respond silently or with RST.

### 2. Performed Host Discovery
- Used -sn to identify alive hosts on a subnet.
- Compared ICMP vs ARP behavior based on root permissions.

### 3. Used NSE Scripts
- Ran vuln scripts to detect vulnerabilities.
- Executed discovery and smb-related scripts to gather info.
- Tested scripts requiring arguments using --script-args.

### 4. Script Searching and Management
- Located scripts using grep and ls patterns.
- Read script.db to identify categories.
- Practiced installing and updating custom scripts with --script-updatedb.

### 5. Applied Firewall Evasion Techniques
- Used -Pn to bypass ICMP blocking.
- Tested packet fragmentation (-f), custom MTU (--mtu), and artificial delays (--scan-delay).
- Experimented with --badsum to detect firewall behavior.

### 6. Understood Practical Differences
- Compared speed, stealth, and reliability of all scan types.
- Saw how filtered, open|filtered, closed, and open results differ between TCP and UDP.

---

This document summarizes everything learned and practiced regarding Nmap scanning, NSE usage, script management, and firewall evasion techniques.
