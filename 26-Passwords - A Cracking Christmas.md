# 🛡️ TryHackMe – Advent of Cyber 2025  
##  Password Cracking (PDF & ZIP)

Today, I completed a hands-on challenge focused on understanding and practicing offline password cracking against encrypted files. The room demonstrates how attackers recover weak passwords—not by breaking encryption, but by targeting the password that protects the file. This session helped me master both the theory and the practical steps attackers (and defenders!) use when dealing with encrypted documents.

---

## 🔥 What I Learned Today

### ✅ 1. Why attackers don’t break encryption  
Modern encryption is extremely strong, so attackers usually don’t “decrypt” files. Instead, they guess the password using methods like:
- Dictionary Attacks — testing real leaked passwords from lists such as rockyou.txt
- Brute-Force Attacks — testing every possible combination
- Mask Attacks — brute forcing with patterns like ?l?l?l?d?d (3 lowercase letters + 2 digits)

---

## 🔧 Tools I Used

### For PDF cracking:
- pdfcrack — used to perform a dictionary attack directly on encrypted PDF files.

### For ZIP cracking:
- zip2john — converts the encrypted ZIP into a readable hash  
- john (John the Ripper) — cracks the hash using a wordlist

---

## 🧪 What I Actually Did (Hands-On)

### Step 1 — Move to Desktop:
cd Desktop

### Step 2 — Identify file type:
file flag.pdf  
file flag.zip

### Step 3 — Crack the encrypted PDF:
pdfcrack -f flag.pdf -w /usr/share/wordlists/rockyou.txt

Result:  
found user-password: 'naughtylist'

Flag extracted from PDF:  
THM{Cr4ck1ng_PDFs_1s_34$y}

---

### Step 4 — Crack the encrypted ZIP:

First attempt failed because of a typo (zip2jon). After correction:

Convert ZIP → hash:
zip2john flag.zip > ziphash.txt

Crack the hash with John:
john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt

Result:  
winter4ever (flag.zip/flag.txt)

Flag extracted from ZIP:
THM{Cr4ck1n6_z1p$_1s_34$yyyy}

---

## 🧠 Key Takeaways

- Attackers rarely attack encryption directly—they attack password strength.
- Offline cracking leaves no login attempts, making detection harder.
- Dictionary attacks are extremely effective because many users choose weak passwords.
- john + zip2john is a powerful combination for cracking ZIP archives.
- GPU/CPU spikes, process names, and heavy wordlist reading are signs defenders can detect.
- Practicing these attacks improves both offensive and defensive cybersecurity skills.

---

## 🎉 Final Results

PDF Password: naughtylist  
PDF Flag: THM{Cr4ck1ng_PDFs_1s_34$y}

ZIP Password: winter4ever  
ZIP Flag: THM{Cr4ck1n6_z1p$_1s_34$yyyy}

---

## 🏁 Conclusion

Today’s room was a powerful reminder that weak passwords defeat even the strongest encryption. Hands-on cracking of both PDF and ZIP files gave me realistic and practical experience with tools used by penetration testers and adversaries. Another day, another step in mastering cybersecurity. 🔥
