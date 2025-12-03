# What I Learned and Practiced in TryHackMe: Introduction to SOC (Security Operations Center)

Today, I completed an in-depth practical exercise on the fundamentals of a **Security Operations Center (SOC)**, focusing on the role of a **Level 1 SOC Analyst** and the three main pillars that support SOC operations: **People, Processes, and Technology**.

---

## Key Concepts and Learnings

### SOC Overview
Technology has increased efficiency but also brought more security responsibilities. Organizations now store critical data digitally, making them vulnerable to new cyber threats. A SOC is a dedicated team that monitors networks **24/7** to detect and respond to these threats proactively.

### Detection and Response
The SOC team’s primary goal is continuous detection and response to incidents. This includes identifying vulnerabilities, unauthorized activities, policy violations, and intrusions within the network.

### Three Pillars of SOC

#### People
The SOC team is composed of various roles, including **Level 1, 2, and 3 Analysts**, **Security Engineers**, **Detection Engineers**, and **SOC Managers**, each with distinct responsibilities from triaging alerts to managing incidents and security tools.

#### Processes
Key SOC processes include alert triage (analyzing alerts by answering the **5 Ws**: *What, When, Where, Who, Why*), reporting, incident response, and forensic investigation.

#### Technology
Security tools such as **SIEM (Security Information and Event Management)**, **EDR (Endpoint Detection and Response)**, and **Firewalls** are vital for automating detection and response across the organization’s network.

---

## Practical Exercise Summary

I acted as a **Level 1 SOC Analyst** tasked with investigating an alert triggered by a port scan detected inside the network.

Using the SIEM tool, I reviewed detailed logs and answered the **5 Ws** to understand the alert’s context:

- **What?** Port scan activity  
- **When?** June 12, 2024, 17:24  
- **Where?** Target IP: 10.0.0.3  
- **Who?** Source hostname: *Nessus* (a vulnerability scanning tool)  
- **Why?** Intended activity by the vulnerability assessment team, not malicious

I confirmed that responses were sent back to the scanner IP, indicating legitimate scanning behavior.

Closed the alert with confidence, gaining the flag:  
`THM{000_INTRO_TO_SOC}`

---

This hands-on lab strengthened my understanding of how SOC teams operate, the critical role of each SOC pillar, and how to effectively investigate and handle security alerts. It also highlighted the importance of collaboration between automated tools and human expertise in maintaining cybersecurity.
