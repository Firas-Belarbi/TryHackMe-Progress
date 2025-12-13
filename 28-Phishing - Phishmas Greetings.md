# 📧 Phishing Analysis Report – TryHackMe SOC-mas Room

## 🧑‍💻 Author

* **Name:** Firas Belarbi
* **Platform:** TryHackMe
* **Room:** SOC-mas – Spotting Phishing Emails

---

## 🎯 Objective

This document presents the **corrected and final phishing analysis** based strictly on the **actual email evidence (headers, domains, authentication results, and content)** from the TryHackMe SOC‑mas room. Each email was manually triaged, classified as **Phishing** or **Spam**, and backed by concrete technical indicators.

---

## 🧠 Methodology Used

For every email, the following were analysed:

* Sender domain vs legitimate organization domain
* SPF / DKIM / DMARC results
* Return‑Path consistency
* Domain impersonation (typosquatting / punycode)
* Presence of social engineering techniques
* Attachments or deceptive file types
* Real intent (credential theft, malware, fraud vs harmless marketing)

---

## 📩 Email‑by‑Email Analysis

---

### ✉️ Email 1 – PayPal Invoice Notification

**From:** [service@paypal.com](mailto:service@paypal.com)
**Classification:** 🚨 Phishing

**Correct Phishing Signals:**

* **Spoofing** → SPF, DKIM, and DMARC all failed
* **Fake Invoice** → Financial lure impersonating PayPal
* **Sense of Urgency** → Payment‑related pressure

**Technical Proof:**

* Authentication‑Results: `spf=fail`, `dkim=fail`, `dmarc=fail`
* Sender infrastructure does not legitimately belong to PayPal

**Flag:** `THM{yougotnumber1-keep-it-going}`

---

### ✉️ Email 2 – Missed Call / Audio Message

**From:** [calls@tbfc.com](mailto:calls@tbfc.com)
**Classification:** 🚨 Phishing

**Correct Phishing Signals:**

* **Impersonation** → Pretends to be internal TBFC system
* **Spoofing** → SPF / DKIM / DMARC failed
* **Malicious Attachment** → `.html` file disguised as `.mp3`

**Technical Proof:**

* Attachment: `Play-Now.mp3-*.html`
* Return‑Path mismatch
* Email originated from weakmail.com infrastructure

**Flag:** `THM{nmumber2-was-not-tha-thard!}`

---

### ✉️ Email 3 – URGENT: McSkidy VPN Access

**From:** [mcskiddyy202512@gmail.com](mailto:mcskiddyy202512@gmail.com)
**Classification:** 🚨 Phishing

**Correct Phishing Signals:**

* **Impersonation** → Pretending to be McSkidy
* **Social Engineering Text** → Incident response scenario
* **Sense of Urgency** → Immediate VPN access request

**Technical Proof:**

* External free Gmail domain
* Attempts to bypass normal communication channels

**Flag:** `THM{Impersonation-is-areal-thing-keepIt}`

---

### ✉️ Email 4 – Salary Raise via Dropbox

**From:** [no-reply@dropbox.com](mailto:no-reply@dropbox.com) (impersonating TBFC HR)
**Classification:** 🚨 Phishing

**Correct Phishing Signals:**

* **Impersonation** → Claims to be TBFC HR
* **External Sender Domain** → Dropbox, not tbfc.com
* **Social Engineering Text** → Attractive salary raise lure

**Technical Proof:**

* Legitimate Dropbox delivery abused
* Reply‑To points to unrelated Outlook address

**Flag:** `THM{Get-back-SOC-mas!!}`

---

### ✉️ Email 5 – Event Logistics Proposal

**From:** [lara@candycane-co.wv](mailto:lara@candycane-co.wv)
**Classification:** 🟡 Spam (Not Phishing)

**Reasoning:**

* No impersonation of TBFC staff
* No malicious links or attachments
* No urgency, no data request
* Pure marketing content

**Conclusion:**
Even if unwanted, it poses **no security threat**.

**Flag:** `THM{It-was-just-a-sp4m!!}`

---

### ✉️ Email 6 – Christmas Laptop Upgrade Agreement

**From:** tbfc-it@tbƒc.com
**Classification:** 🚨 Phishing

**Correct Phishing Signals:**

* **Impersonation** → Pretends to be TBFC‑IT
* **Typosquatting / Punycode** → `tbƒc.com` instead of `tbfc.com`
* **Social Engineering Text** → Attractive hardware upgrade

**Technical Proof:**

* Unicode character `ƒ` replacing `f`
* Return‑Path uses `xn--` encoded domain
* Embedded link: `microsoftooline.co` (fake Microsoft domain)

**Flag:** `THM{number6-is-the-last-one!-DX!}`

---

## ✅ Final Summary

| Email | Classification |
| ----- | -------------- |
| 1     | Phishing       |
| 2     | Phishing       |
| 3     | Phishing       |
| 4     | Phishing       |
| 5     | Spam           |
| 6     | Phishing       |

---

## 🧠 Key Takeaways

* **Passing SPF/DKIM does NOT guarantee legitimacy** when punycode or impersonation is used
* **Intent matters more than appearance**
* Legitimate services (Dropbox, Microsoft, Gmail) are commonly abused
* Spam ≠ Phishing

---

> 🔐 *Modern phishing is psychological, not technical. Verify intent, not just syntax.*
