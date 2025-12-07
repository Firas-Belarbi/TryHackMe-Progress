# Advent of Cyber 2025 – Day 3
# Splunk Practical Investigation Writeup
# Hands-On SIEM Analysis (No Theory, Only Practical Steps)

This writeup documents every practical step I performed inside Splunk to solve the TryHackMe Advent of Cyber Day 3 challenge. 
The focus of this file is demonstrating real SIEM investigation skills: 
each question → the query I used → what appeared in Splunk → how I derived the final answer.

No guessing. No theory. Only real log analysis.

------------------------------------------------------------
1) QUESTION: What is the attacker IP found attacking and compromising the web server?
------------------------------------------------------------

STEP 1 — I began by removing all normal browser traffic so only suspicious tools remained.
I used the following SPL query:

index=main sourcetype=web_traffic user_agent!=*Mozilla* user_agent!=*Chrome* user_agent!=*Safari* user_agent!=*Firefox*

STEP 2 — After running the query, I clicked on the field "client_ip".
I observed that one single IP accounted for **all suspicious user agents** such as:
wget, curl, sqlmap, Havij, zgrab, Go-http-client, Ruby Webshell Runner.

This was a clear indicator of attacker activity.

FINAL ANSWER:
198.51.100.55

------------------------------------------------------------
2) QUESTION: Which day was the peak traffic in the logs? (Format: YYYY-MM-DD)
------------------------------------------------------------

STEP 1 — To see daily traffic distribution, I ran:

index=main sourcetype=web_traffic | timechart span=1d count

STEP 2 — I checked the results and switched between Statistics and Visualization tabs.
I located the day with the highest spike in log activity.

STEP 3 — To make sure, I sorted the values from highest to lowest:

index=main sourcetype=web_traffic | timechart span=1d count | sort by count | reverse

The highest count appeared on October 12, 2025.

FINAL ANSWER:
2025-10-12

------------------------------------------------------------
3) QUESTION: What is the count of Havij user_agent events found in the logs?
------------------------------------------------------------

STEP 1 — I clicked the field "user_agent" inside Splunk.
STEP 2 — In the Top Values section, I looked specifically for:

Havij/1.17 (Automated SQL Injection)

STEP 3 — I noted the count shown next to it.

It showed exactly 993 events attributed to Havij.

FINAL ANSWER:
993

------------------------------------------------------------
4) QUESTION: How many path traversal attempts to access sensitive files were observed?
------------------------------------------------------------

STEP 1 — Path traversal attempts often use “../” patterns.
I filtered traffic from the attacker using:

sourcetype=web_traffic client_ip="198.51.100.55" AND path="*..*" OR path="*redirect*"

STEP 2 — To count attempts accurately, I used:

sourcetype=web_traffic client_ip="198.51.100.55" AND path="*..\/..\/*" OR path="*redirect*" | stats count by path

STEP 3 — I summed up the results representing directory traversal access attempts.

I observed a total of 658 traversal-related requests.

FINAL ANSWER:
658

------------------------------------------------------------
5) QUESTION: How many bytes were transferred to the C2 server IP from the compromised web server?
------------------------------------------------------------

STEP 1 — The compromised server IP is 10.10.1.5.
I checked firewall logs for outbound connections from this server to the attacker:

sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="198.51.100.55" AND action="ALLOWED"

STEP 2 — To compute total data exfiltration:

sourcetype=firewall_logs src_ip="10.10.1.5" AND dest_ip="198.51.100.55" AND action="ALLOWED" | stats sum(bytes_transferred) by src_ip

STEP 3 — Splunk returned the total bytes exfiltrated.

The final value was exactly 126167 bytes.

FINAL ANSWER:
126167

------------------------------------------------------------
SUMMARY — What I Learned from This Practical SIEM Investigation
------------------------------------------------------------

This room was fully hands-on and taught me how to perform real log analysis in Splunk using SPL queries. 
Key practical takeaways:

• How to isolate malicious traffic by filtering out legitimate user agents.
• How to analyze attacker behavior chronologically using logs.
• How to identify anomalies visually with timecharts.
• How to pivot from web logs to firewall logs to confirm C2 communication.
• How to trace an entire attack chain: reconnaissance → enumeration → exploitation → exfiltration → C2 contact.
• How to extract IOCs such as IP addresses, malicious tools, payload paths, and data transfer amounts.

This exercise strengthened my SIEM investigation workflow and showed how Splunk can be used to respond to real-world cyber incidents effectively.
