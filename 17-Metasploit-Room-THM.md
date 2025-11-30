
# TryHackMe Daily Progress: Learning Metasploit Framework

**Author:** Firas Belarbi  
**Source:** TryHackMe room (AttackBox and Metasploit modules)  
**Date:** (Add publish date)

---

## Summary
Today, I worked on the TryHackMe Metasploit room. I learned what Metasploit is, the difference between its versions, how to navigate msfconsole, set variables, find modules, launch exploits, and manage sessions. The focus was on practical examples within the AttackBox environment as guided in the room.

---

## Step-by-step learning and practical experience

1. **Introduction to Metasploit**  
   - Metasploit comes in two editions: **Pro (GUI commercial version)** and **Framework (open-source CLI version)**. This room focused on the open-source Framework available on AttackBox.  
   - Key components include `msfconsole`, various modules (exploit, auxiliary, post, payloads, encoders, nops, evasion), and standalone tools like `msfvenom`.

2. **Launching msfconsole and initial interaction**  
   - Started `msfconsole` on the AttackBox as demonstrated. The prompt changes to `msf6 >`.  
   - Inside msfconsole, Linux commands can be run using `exec`. For example, `exec ls` lists files, and `exec ping -c 1 8.8.8.8` checks connectivity.

3. **Context and modules usage**  
   - Used the command `use exploit/windows/smb/ms17_010_eternalblue` to select an exploit module (based on MS17-010 example from the room).  
   - The prompt changes to `msf6 exploit(windows/smb/ms17_010_eternalblue) >`, indicating the current context.

4. **Viewing and setting options**  
   - `show options` displays configurable variables like `RHOSTS`, `RPORT`, and payload-related variables like `LHOST`, `LPORT`.  
   - Examples of setting options from the room:  
     - `set LPORT 6666` sets the local port.  
     - `set RHOSTS 10.10.165.39` sets the target IP address for the module.  
     - `setg RHOSTS 10.10.165.39` sets a global variable for all modules.  
     - `unset PAYLOAD` clears the set payload.

5. **Exploitation and payloads**  
   - After configuring options, used `exploit` to launch the attack.  
   - Explains session handling, where Meterpreter sessions can be interacted with or backgrounded.

6. **Other important commands and concepts**  
   - `search` command to find modules related to a keyword.  
   - `info` to get detailed info on a module.  
   - `sessions -i` to interact with active sessions.

---

## Questions and answers encountered during the TryHackMe room

- **How to set a global RHOSTS value?**  
  `setg RHOSTS 10.10.19.23`

- **How to clear a set payload?**  
  `unset PAYLOAD`

- **How to proceed with exploitation?**  
  `exploit`

---

## Practical notes

- Practical use of Metasploit on AttackBox was essential to understand the flow of module selection, setting options, payload configuration, and launching exploits.  
- Running auxiliary modules like scanners was also practiced.  
- Managing sessions and understanding Meterpreter basics helped solidify the practical knowledge.

---
