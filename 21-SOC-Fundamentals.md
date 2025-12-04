## 🧠 What I Learned Today
### **Normalization & Parsing**
Raw logs → parsed into fields → normalized into one consistent format.


### **Correlation Engine**
SIEM connects events to reveal attacker patterns.
Example scenario:
1. Haris logs in from unusual VPN IP
2. Accesses shared files
3. Runs PowerShell
4. Machine makes outbound connection
→ Correlated = possible data exfiltration


### **Real-Time Alerting**
Alerts are triggered when rules detect suspicious patterns.


### **Dashboards**
Provide insights like:
- Top alerts
- Failed logins
- Event volume
- Triggered rules


---
## 📥 Log Ingestion Methods
- **Agent / Forwarder** (Splunk Forwarder)
- **Syslog**
- **Manual Upload**
- **Port-Forwarding**


Common log locations:
- Linux HTTP logs → `/var/log/httpd`
- Cron logs → `/var/log/cron`
- Authentication logs → `/var/log/auth.log`


---
## ⚙️ Detection Rules


### **How rules work**
Rules are logical expressions that trigger alerts.
Examples:
- 5 failed logins in 10 seconds → Brute-force alert
- Outbound traffic > 25MB → Data exfiltration alert
- Event ID 104 → Log clearing detected
- Event ID 4688 + process = "whoami" → Suspicious execution


### **Example Rule Used in the Lab**

If EventID = 4688 AND Log_Source = WindowsEventLogs AND ProcessName = (miner OR crypt) Then Trigger "Potential CryptoMiner Activity"

---
## 🔍 Alert Investigation Process
Once alert is triggered, analyst must:
1. Check triggered events
2. Check the rule logic
3. Determine if **True Positive** or **False Positive**
4. Take action:
- Tune the rule (False Positive)
- Investigate deeper (True Positive)
- Isolate host
- Block IP
- Contact asset owner


---


# 🧪 What I Practiced Today (Step-by-Step)


### ✅ **Step 1 — Started the Lab and Triggered Suspicious Activity**
I pressed **Start Suspicious Activity**, which caused an alert in the SIEM dashboard.


### ✅ **Step 2 — Identified the Process Causing the Alert**
The process responsible was:

cudominer.exe



### ✅ **Step 3 — Investigated the Event**
- Event ID: **4688** (process execution)
- User who ran the process: **chris**
- Hostname: **HR_02**


### ✅ **Step 4 — Matched the Rule Condition**
The rule looked for:

ProcessName contains "miner"

The process was **cudominer.exe**, which contains **miner**, so alert triggered correctly.


### ✅ **Step 5 — Determined Alert Type**
This was a **True Positive**, because:
- HR employees should not run mining software
- The executable name is clearly suspicious
- Came from temp directory
- Contains "miner" keyword


### ✅ **Step 6 — Retrieved the Flag**
After choosing the correct action, I obtained the flag:

THM{000_SIEM_INTRO}

---
# 🎯 Final Summary
Today I learned how a SIEM works, how logs are collected and normalized, how alerts are triggered, and how to investigate them. I applied all concepts in a real scenario by analyzing a suspicious crypto-miner execution on the HR machine.


This lab significantly improved my skills in:
- SIEM fundamentals
- Log analysis
- Event correlation
- Detection rules
- True Positive vs False Positive classification
- Basic SOC investigation workflow























































