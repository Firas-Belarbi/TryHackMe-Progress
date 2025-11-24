# Putting It All Together – TryHackMe

This room connects the previous web fundamentals concepts into one end-to-end view:  
what happens from the moment a user types a URL until the page is displayed, and where security fits in.

---

## From URL to Web Page: Step by Step

1. **User enters a URL**
   - Example: `https://tryhackme.com/room/webfundamentals`

2. **DNS resolution**
   - Browser/OS checks cache.
   - If not found, resolver queries DNS (recursive → TLD → authoritative).
   - Result: domain → IP address.

3. **TCP connection**
   - Client initiates a TCP three-way handshake with the server IP on port 80 (HTTP) or 443 (HTTPS).
   - After handshake, a connection is established.

4. **HTTP request**
   - Browser sends an HTTP request over the TCP connection.
   - Example:
     ```text
     GET /room/webfundamentals HTTP/1.1
     Host: tryhackme.com
     User-Agent: <browser>
     Accept: text/html
     ```

5. **Server processing**
   - Web server (e.g. Nginx/Apache) receives the request.
   - May pass it to application code (PHP, Python, Node.js, etc.).
   - Application may query a database or other services.

6. **HTTP response**
   - Server returns status line, headers, and body.
   - Example:
     ```text
     HTTP/1.1 200 OK
     Content-Type: text/html
     Content-Length: 12345

     <html>...</html>
     ```

7. **Rendering**
   - Browser parses HTML.
   - Fetches linked CSS, JS, images, fonts.
   - Executes client-side JavaScript.
   - Renders the final page to the user.

---

## Components Involved

- **Client**
  - Browser (Chrome, Firefox, etc.).
  - Responsible for sending requests and rendering responses.

- **Network**
  - Routers, switches, firewalls, proxies.
  - Moves packets between client and server.

- **DNS**
  - Resolves human-readable domains to IP addresses.

- **Web Server**
  - Listens on HTTP/HTTPS ports.
  - Serves static files and/or passes requests to application logic.

- **Application**
  - Implements business logic (login, search, profiles, etc.).
  - Often communicates with databases.

- **Database**
  - Stores users, sessions, application data.

---

## Security View: Where Things Can Go Wrong

- **DNS**
  - DNS spoofing / poisoning.
  - Malicious domains used for phishing or C2.

- **Network**
  - Unencrypted HTTP traffic visible to attackers on the path.
  - Misconfigured firewalls exposing services.

- **HTTP Layer**
  - Weak or missing authentication.
  - Insecure cookies / sessions.
  - Input not validated.

- **Application**
  - SQL injection.
  - XSS.
  - Broken access control.
  - Insecure direct object references.

- **Configuration**
  - Default credentials.
  - Debug mode enabled.
  - Sensitive files exposed (backups, configs).

---

## Logs and Monitoring

During this room, the focus also connects to how logs are generated:

- Web server logs (access and error logs).
- Application logs.
- Authentication logs.

For a SOC Analyst, these logs show:

- Source IPs and requested URLs.
- HTTP methods and status codes.
- Suspicious patterns (e.g. scanning, brute-force, repeated 404s).

---

## Key Takeaways

- A simple page load involves multiple components: DNS, TCP, HTTP, web server, application, and database.
- Each step is a potential attack surface.
- Understanding this full flow is required before analyzing web attacks or building detections in a SOC environment.
