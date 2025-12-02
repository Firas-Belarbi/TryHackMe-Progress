# Hydra - TryHackMe Progress

## Introduction

Hydra is a powerful and widely used tool for password testing via brute force attacks against various protocols such as SSH, FTP, HTTP forms, and more.

---

## What I Learned

- How Hydra works and how to use it effectively for password cracking.
- The supported protocols, focusing on SSH and HTTP POST forms.
- Setting up the environment (Kali Linux / AttackBox) and utilizing password lists like **rockyou.txt**.
- The importance of analyzing web requests using **Developer Tools** to fine-tune attacks.
- Practical application on TryHackMe labs to crack SSH accounts and web login forms.

---

## Key Hydra Options

| Option   | Description                             |
|----------|---------------------------------------|
| `-l`     | Specify a single username              |
| `-L`     | Use a file containing multiple usernames |
| `-P`     | Use a file containing passwords        |
| `-t`     | Number of parallel connections (threads) |
| `-V`     | Verbose mode (show each attempt)       |
| `-s`     | Specify target port                     |
| Protocol | The protocol to attack (e.g., ssh, ftp, http-post-form) |

---

## Example Commands

### 1. SSH Brute Force Attack

hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.184.95 ssh -t 4 -V

### 2. Web Login Form (HTTP POST) Attack

hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.184.95 http-post-form "/:username=^USER^&password=^PASS^:F=Your username or password is incorrect." -t 4 -V

---

## Steps for Successful Execution

1. Use **Developer Tools** in your browser to inspect the login request details.
2. Identify the HTTP request method (GET or POST).
3. Determine the login page URL path and the names of form fields.
4. Find the exact error message returned on failed login attempts.
5. Customize Hydra command syntax accordingly.
6. Execute the attack and monitor the results closely.
7. Use SSH to connect once the correct credentials are found.

---

## Important Tips

- Always use an appropriate and updated password list.
- Watch out for target system protections such as account lockout or IP blocking.
- Use these tools only in authorized testing environments respecting legal boundaries.
- Practice precise analysis of web requests to enhance attack effectiveness.

---

## My Personal Experience

By applying these methods on the TryHackMe lab, I successfully performed two attacks:

- Accessed the SSH account for user **molly** using the command:
  
  `hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.184.95 ssh -t 4 -V`

- Cracked the password for a web login form (HTTP POST) using the command:
  
  `hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V`

As a result, I retrieved **Flag 1,2** as proof of success.

---

## Conclusion

Hydra is an extremely effective tool for password cracking when used correctly. Mastery of protocol details and request analysis is essential for success.

---

## Resources

- [THC-Hydra Official GitHub Repository](https://github.com/vanhauser-thc/thc-hydra)  
- **rockyou.txt** password list included in Kali Linux  
- Browser **Developer Tools** for inspecting HTTP requests  
