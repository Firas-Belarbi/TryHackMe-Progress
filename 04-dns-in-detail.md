# DNS in Detail – TryHackMe

## 🧩 Room Overview
This room provides a deep look into **DNS (Domain Name System)** — one of the most essential components of networking and cybersecurity.  
Understanding DNS is critical for SOC Analysts, penetration testers, and network engineers because DNS is involved in almost every attack chain.

- Platform: **TryHackMe**
- Path: **Introduction / Networking Basics**
- Status: ✅ Completed
- Focus: DNS concepts, record types, resolving domains, and common attack techniques

---

## 🎯 Learning Objectives

- Understand how DNS works and why it is essential  
- Learn the different DNS record types (A, AAAA, CNAME, MX, TXT…)  
- Explore how domain resolution happens step-by-step  
- Understand DNS zones, authoritative servers, and recursive resolvers  
- Learn how attackers abuse DNS for malicious purposes  
- Get ready for SOC tasks involving DNS log analysis  

---

## 🔑 Key Concepts Learned

### 1. What is DNS?
DNS translates **domain names → IP addresses**.  
Example:  
`www.google.com` → `142.250.80.78`

Without DNS, the internet would not be usable.

---

### 2. DNS Hierarchy
- **Root Servers** – “.” at the top of the hierarchy  
- **TLD Servers** – (.com, .net, .org, .edu)  
- **Authoritative Name Servers** – store actual records for a domain  
- **Recursive Resolvers** – your ISP or local DNS server  

---

### 3. DNS Record Types

| Record | Purpose |
|--------|---------|
| **A** | IPv4 address |
| **AAAA** | IPv6 address |
| **CNAME** | Alias to another domain |
| **MX** | Mail server information |
| **NS** | Nameserver for the domain |
| **TXT** | Text information (SPF, DKIM, verification) |
| **SOA** | Start of Authority (zone info) |

These appear often in SOC incidents and log analysis.

---

### 4. How DNS Resolution Works  
The room explained the full path:

1. User types a domain → Browser checks cache  
2. If not found → Ask local DNS resolver  
3. Resolver queries **Root Server**  
4. Root tells which **TLD** server to ask  
5. TLD points to the **Authoritative Name Server**  
6. Authoritative server returns the final IP  
7. Browser connects to that IP

Understanding this is essential for debugging and security monitoring.

---

### 5. DNS Tools Learned

- `nslookup` – Basic DNS queries  
- `dig` – Advanced DNS lookups  
- `host` – Simple resolver tool  
- Online DNS lookup services  

Examples:

nslookup google.com
dig A google.com
dig MX example.com
host tryhackme.com


---

## 😈 How Attackers Abuse DNS

DNS can be used in many cyberattacks:

- **DNS Spoofing / Poisoning**  
  Attackers inject false DNS information to redirect traffic.

- **DNS Tunneling**  
  Using DNS to hide data exfiltration.

- **Malicious C2 domains**  
  Malware contacts command-and-control servers via DNS.

- **Typosquatting**  
  Fake look-alike domains to steal credentials.

A SOC Analyst MUST be able to spot these patterns in logs.

---

## 🧠 Relevance to My Future SOC Role

This room is directly relevant to SOC work:

- DNS logs are part of every SIEM  
- SOC alerts often involve suspicious DNS queries  
- Understanding DNS helps detect malware communication  
- DNS anomalies can indicate phishing, tunneling, or C2 traffic  
- Many investigations start with:  
  **“Why is this host resolving this domain?”**

---

## 📝 Summary

This room strengthened my understanding of DNS, record types, and how domain resolution works.  
I also learned how attackers abuse DNS and why SOC analysts must monitor DNS logs closely.
