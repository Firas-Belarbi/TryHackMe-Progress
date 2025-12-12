# XSS - Merry XSSMas

## Room Summary
This TryHackMe room focused on identifying and exploiting Cross-Site Scripting (XSS) vulnerabilities in McSkidy’s secure message portal. System logs showed unusual activity (odd messages and suspicious search terms), suggesting XSS attempts. The objective was to validate XSS behavior (Reflected and Stored) and capture the associated flags.

---

## Environment Setup
- Started the AttackBox
- Started the Target Machine
- Opened the web app at: `http://MACHINE_IP`

---

## What I Learned

### What is Cross-Site Scripting (XSS)?
XSS is a web vulnerability where an attacker injects (JavaScript) code into a page that other users view. If the application does not properly validate, sanitize, or encode input/output, the browser may execute attacker-controlled code instead of displaying it as plain text. This can lead to session hijacking, user impersonation, page defacement, or malicious actions performed as the victim.

---

## XSS Types Practiced in This Room

### 1) Reflected XSS
- The payload is NOT stored on the server
- It is reflected immediately in the response (e.g., search results)
- Often delivered via phishing links or crafted URLs

Payload used:
`<script>alert('Reflected Meow Meow')</script>`

What I observed:
- The alert box appeared immediately after submitting the search
- This confirmed the application reflected input without proper output encoding

---

### 2) Stored XSS
- The payload IS stored/persisted on the backend
- Every user who loads the affected page executes the payload
- More dangerous because it becomes “set-and-forget”

Payload used:
`<script>alert('Stored Meow Meow')</script>`

What I observed:
- The payload was saved via the message submission form
- The alert executed automatically on page reload / revisit

---

## How the Flags Were Obtained

### Reflected XSS Flag
Method:
- Injected the reflected test payload into the search input
- Confirmed execution via the alert popup
- Retrieved the reflected XSS flag shown by the room

Flag:
`THM{Evil_Bunny}`

---

### Stored XSS Flag
Method:
- Submitted the stored payload through the message form
- Reloaded the page to confirm persistence and execution
- Retrieved the stored XSS flag shown by the room

Flag:
`THM{Evil_Stored_Egg}`

---

## Security Takeaways
- Never trust user input
- Avoid dangerous rendering like `innerHTML`; prefer `textContent`
- Sanitize and encode user-controlled data (input AND output)
- Protect session cookies using HttpOnly, Secure, and SameSite attributes
- Use Content Security Policy (CSP) to reduce XSS impact

---

## Conclusion
This room provided hands-on experience confirming both Reflected and Stored XSS in a realistic portal. By testing injection points (search for reflected, messaging for stored) and validating execution through browser behavior and logs, I strengthened my understanding of how XSS works and how to mitigate it.
