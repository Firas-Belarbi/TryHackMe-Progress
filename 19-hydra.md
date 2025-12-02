# Hydra - TryHackMe Progress

## Introduction

Hydra is a powerful and popular tool for password testing using brute force attacks against many protocols such as SSH, FTP, HTTP forms, and others.

---

## What I Learned

- I understood how Hydra works and how to use it for password cracking.
- I learned about the supported protocols, especially SSH and HTTP POST forms.
- I learned how to set up the working environment (Kali Linux / AttackBox) and use password lists like rockyou.txt.
- I understood the importance of inspecting web requests (using Developer Tools) to fine-tune the attack.
- I applied the attack practically on the TryHackMe lab, using Hydra to crack an SSH account and a web login form.

---

## Important Hydra Options

| Option | Description |
|--------|--------------|
| `-l`   | Single username |
| `-L`   | File of usernames |
| `-P`   | File of passwords |
| `-t`   | Number of parallel connections (threads) |
| `-V`   | Verbose mode, show each attempt |
| `-s`   | Specify port number |
| Protocol | e.g., ssh, ftp, http-post-form, etc. |

---

## Commands Used

### 1. SSH Attack

```bash
hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.184.95 ssh -t 4 -V
2. Web Login POST Form Attack
bash
Copier le code
hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.184.95 http-post-form "/:username=^USER^&password=^PASS^:F=Your username or password is incorrect." -t 4 -V
Steps I Learned to Execute
Use Developer Tools in the browser to inspect login request details.

Identify the HTTP request type (GET or POST).

Determine the login page path and form field names.

Find the exact error message displayed on failed attempts.

Adjust Hydra commands based on these details.

Run the attack and monitor the results.

Use SSH to connect to the server after obtaining the correct password.

Important Tips
Make sure to use a proper and updated password list.

Monitor if the target system has protections like lockouts or blocking.

Respect the legal aspect and use these tools only in testing environments or with permission.

Practice analyzing web requests precisely to improve success chances.

My Personal Experience
I applied the above commands on the TryHackMe lab and succeeded in:

Accessing the SSH account of user molly.

Cracking the password of the web login form.

Extracting Flag 1 successfully.

Conclusion
Hydra is a very effective password cracking tool when used properly. Understanding the targeted protocol details and analyzing requests carefully is the key to success.

Resources
Official THC-Hydra GitHub: https://github.com/vanhauser-thc/thc-hydra

rockyou.txt password list in Kali Linux

Developer Tools in web browsers
