# Networking Fundamentals & Telnet Lab Notes

These notes summarise what I learned from the TryHackMe **Networking Concepts** room and related labs.  
They connect networking theory (OSI, TCP/IP, IP, TCP/UDP, encapsulation) with hands-on work using Telnet.

---

## 1. OSI Model – Conceptual View of Networking

The **OSI (Open Systems Interconnection) model** is a conceptual 7-layer model used to understand how data moves across a network.

| Layer | Name             | Main Function                                           | Examples                         |
|------:|------------------|---------------------------------------------------------|----------------------------------|
| 7     | Application      | Services for user applications                         | HTTP, FTP, DNS, SMTP, IMAP      |
| 6     | Presentation     | Encoding, encryption, compression                      | Unicode, JPEG, PNG, MIME        |
| 5     | Session          | Managing sessions between hosts                        | RPC, NFS                         |
| 4     | Transport        | End-to-end transport, segmentation, reliability        | TCP, UDP                         |
| 3     | Network          | Logical addressing and routing                         | IP, ICMP, IPSec                  |
| 2     | Data Link        | Reliable link between directly connected nodes         | Ethernet, Wi-Fi                 |
| 1     | Physical         | Transmission medium and signals                        | Copper, fibre, radio             |

Key points:
- Layer 2: MAC addresses + frames.
- Layer 3: IP packets + routing.
- Layer 4: TCP/UDP with ports.
- Layer 7: protocols like HTTP/DNS.

---

## 2. TCP/IP Model – Practical Internet Stack

Mapping between OSI and TCP/IP:

| TCP/IP Layer   | OSI Layers Covered                     | Examples                      |
|----------------|----------------------------------------|-------------------------------|
| Application    | OSI 5, 6, 7                            | HTTP, HTTPS, FTP, DNS, SMTP  |
| Transport      | OSI 4                                   | TCP, UDP                      |
| Internet       | OSI 3                                   | IP, ICMP, IPSec               |
| Link           | OSI 1 + 2                               | Ethernet, Wi-Fi              |

---

## 3. Data Units Across the Layers

| Layer        | Name of Data Unit                   |
|--------------|-------------------------------------|
| Application  | Data                                |
| Transport    | TCP Segment / UDP Datagram          |
| Network      | IP Packet                           |
| Data Link    | Frame                               |
| Physical     | Bits                                |

Definitions:
- TCP Segment = header + data.
- UDP Datagram = header + data.
- IP Packet = IP header + transport data.
- Frame = MAC header + packet + trailer.

---

## 4. IPv4 Addresses, Subnets, and Routing

### 4.1 IPv4 Structure
- 32-bit address (4 octets).
- Example: `192.168.66.89`.

Special addresses:
- `.0` = network address
- `.255` = broadcast (in /24)

### 4.2 Subnet Mask and CIDR
Example:
- IP: `192.168.66.89`
- Netmask: `255.255.255.0` = `/24`

`/24` → first 24 bits = network  
Hosts: `.1` to `.254`.

### 4.3 Private vs Public IP

Private ranges:
- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

Private = not routable on Internet.  
Public = routable globally.

### 4.4 Routing
Routers operate at Layer 3 and forward packets based on destination IP.

---

## 5. TCP vs UDP – Transport Layer

### 5.1 TCP
- Connection-oriented.
- Reliable delivery.
- Uses 3-way handshake.
- Suitable for: HTTPS, SSH, FTP.

### 5.2 UDP
- Connectionless.
- No reliability.
- Very fast.
- Used by DNS, DHCP, NTP, VoIP.

---

## 6. Encapsulation and the Life of a Packet

### 6.1 Encapsulation
Each layer adds its own header:

Application → Transport → Network → Data Link → Physical.

Receiving host reverses the process.

### 6.2 Packet Example (HTTP request)
1. Browser creates HTTP request.
2. TCP wraps it as segments.
3. IP adds source/destination IP.
4. Ethernet adds MAC addresses.
5. Routers forward based on IP.
6. Destination server removes all headers.

---

## 7. Telnet Lab – Working with TCP Ports Manually

### 7.1 Telnet Basics
Use Telnet as a **generic TCP client**.

```
telnet MACHINE_IP PORT
```

Exit:
```
CTRL + ] 
quit
```

Telnet is unencrypted → for labs only.

---

### 7.2 Echo Server (TCP Port 7)

```
telnet MACHINE_IP 7
```

Whatever I type, the server sends back.

---

### 7.3 Daytime Server (TCP Port 13)

```
telnet MACHINE_IP 13
```

Returns:
```
Thu Jun 20 12:36:32 PM UTC 2024
Connection closed by foreign host.
```

---

### 7.4 HTTP Server (TCP Port 80)

```
telnet MACHINE_IP 80
GET / HTTP/1.1
Host: telnet.thm

```

(Blank line required.)

Example server reply:

```
HTTP/1.1 200 OK
Server: Apache/2.4.41 (Ubuntu)
Content-Type: text/html
...
```

From this I learned:
- How to craft HTTP requests manually.
- How to read status line + headers.
- How to identify the **HTTP server version**.

---

## 8. Security and Troubleshooting Perspective

These labs help develop a cybersecurity mindset:

- Checking if ports are open.
- Identifying running services.
- Understanding protocol behaviour.
- Recognising insecure services:
  - Telnet
  - Echo port 7
  - Daytime port 13
- Preparing for Wireshark, Nmap, and SOC work.

This combines theory (OSI, TCP/IP, IP, TCP/UDP) with hands-on practice (Telnet & ports).
