
# TryHackMe — The Boom of AI Assistants  
## Advent of Cyber – Day 4  


---

## 🎄 Introduction

In this challenge, I explored how Artificial Intelligence can be used across different areas of cyber security.  
Using the AI agent **Van SolveIT**, I interacted with a vulnerable web application and completed three showcases:

- 🔴 Red Team — generating and running an exploit script  
- 🔵 Blue Team — analysing web logs to identify an attack  
- 🟪 Software Security — reviewing source code for vulnerabilities  

This room demonstrates how AI can assist both attackers and defenders, as well as help with secure software development.

---

# 🟥 Stage 2 — Red Team: Generating & Executing an Exploit

### ✔ Objective  
Use the AI assistant to generate a Python exploit that abuses an SQL Injection vulnerability in the login page.

### ✔ What Happened  
The AI provided a Python script using the payload:



alice' OR 1=1 -- -


This payload forces the SQL query to always evaluate as TRUE, bypassing authentication.

### ✔ Steps Performed  
1. Saved the script as `script.py`  
2. Replaced the placeholder URL:


http://MACHINE_IP:5000/login.php

with the real target:


http://10.80.173.160:5000/login.php

3. Executed the script using:


python3 script.py


### ✔ Result  
The exploit successfully logged in as **admin** and returned:



FLAG: THM{SQLI_EXPLOIT}


### ✔ Red Team Answer  
**THM{SQLI_EXPLOIT}**

---

# 🟦 Stage 3 — Blue Team: Analysing Logs

### ✔ Objective  
Inspect server logs to understand how the attack was performed and where it originated.

### ✔ Log Observed



198.51.100.22 - - [03/Oct/2025:09:03:11 +0100]
"POST /login.php HTTP/1.1" 200 642 "-"
"python-requests/2.31.0"
"username=alice%27+OR+1%3D1+--+-&password=test"


### ✔ Key Observations  
- **IP Address:** The attack originated from `198.51.100.22`  
- **Endpoint:** `/login.php` is a sensitive location  
- **User-Agent:** `python-requests` indicates scripted/automated activity  
- **Payload:** Decodes to  



alice' OR 1=1 -- -

confirming SQL Injection

### ✔ What I Learned as Blue Team  
- Logs reveal clear indicators of malicious behaviour  
- SQL payloads stand out due to special characters and logical operators  
- Automated scripts are easily identified by their user agents  
- Correlating timestamps helps build an incident timeline  

After reviewing all findings, I completed the Blue Team stage successfully.

---

# 🟪 Stage 4 — Software Security: Reviewing the Source Code

### ✔ Objective  
Identify the root cause of the SQL Injection vulnerability within the PHP source code.

### ✔ Vulnerable Code

```php
$user = $_POST['username'] ?? '';
$pass = $_POST['password'] ?? '';


These variables were later inserted directly into an SQL query without validation or sanitization.

✔ Why the Code Is Vulnerable

User input is used unsafely inside SQL statements

No Prepared Statements or parameter binding

No filtering, sanitization, or escaping

Developers relied on raw input, making injection trivial

✔ How It Should Be Fixed

Use prepared statements:

$stmt = $db->prepare("SELECT * FROM users WHERE username=? AND password=?");
$stmt->execute([$user, $pass]);

✔ Final Flag Displayed
THM{AI_MANIA}

✔ Software Security Answer

THM{AI_MANIA}

🧠 What I Learned From This Room
🔴 Red Team Lessons

How AI can auto-generate exploits

How SQL Injection works in practice

How to automate offensive tasks efficiently

🔵 Blue Team Lessons

How to read and interpret access logs

How SQL Injection attempts appear in server logs

How to detect automated reconnaissance or exploit activity

🟪 Software Security Lessons

Why improper input handling leads to vulnerabilities

The importance of prepared statements

How AI can help identify insecure code patterns

🏁 Final Answers Summary
Question	Answer
AI Showcase Final Flag	THM{AI_MANIA}
SQLi Exploit Flag	THM{SQLI_EXPLOIT}
🎉 Completed Successfully!

This write-up showcases how AI can assist in cyber security across offensive, defensive, and software security domains.
It also highlights the importance of validating AI outputs and maintaining secure coding practices.


---
