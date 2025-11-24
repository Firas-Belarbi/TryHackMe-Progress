# HTTP in Detail – TryHackMe

## 🧩 Room Overview
This room provides a clear and practical introduction to **HTTP (HyperText Transfer Protocol)** —  
the core protocol that powers communication between **web browsers and web servers**.

Understanding HTTP is essential for SOC Analysts, penetration testers, and anyone working in cybersecurity,  
because most attacks (SQLi, XSS, CSRF, authentication bypass…) happen through HTTP.

- Platform: **TryHackMe**
- Path: **Introduction / Networking Basics**
- Status: ✅ Completed
- Focus: How HTTP works, request/response structure, methods, headers, and status codes

---

## 🎯 Learning Objectives

- Understand how the HTTP protocol works  
- Learn the structure of HTTP requests and responses  
- Recognize common HTTP methods (GET, POST, HEAD, PUT…)  
- Understand HTTP status codes  
- Learn how web browsers communicate with servers  
- Understand cookies, sessions, and authentication basics  
- Recognize how attackers use HTTP in web exploitation

---

## 🔑 Key Concepts Learned

### 1. What is HTTP?
HTTP is a **stateless communication protocol** used by browsers to request content from web servers.

Examples:
- Visiting a website  
- Logging in  
- Submitting a form  
- Downloading files  

All of this is done using HTTP or HTTPS.

---

### 2. HTTP Request Structure

When your browser connects to a website, it sends an **HTTP Request**.

It contains:

Method (GET / POST)
URL
HTTP Version
Headers
Body (Optional)


Example:
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html

---

### 3. HTTP Response Structure

A server replies with an **HTTP Response**, which contains:

Status Line
Headers
Body (HTML, JSON, images…)



Example:
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1024



---

### 4. Common HTTP Methods

| Method | Purpose |
|--------|---------|
| **GET** | Retrieve a resource |
| **POST** | Send data (forms, login, uploads) |
| **HEAD** | Same as GET without body |
| **PUT** | Upload or replace a file |
| **DELETE** | Delete a resource |
| **OPTIONS** | Show allowed methods |

Attackers often abuse these methods if misconfigured.

---

### 5. HTTP Status Codes

| Code | Meaning |
|------|---------|
| **200** – OK | Request succeeded |
| **301 / 302** – Redirect | Page moved |
| **400** – Bad Request | Client error |
| **401** – Unauthorized | Requires authentication |
| **403** – Forbidden | Access denied |
| **404** – Not Found | Resource missing |
| **500** – Server Error | Problem on the server |

SOC analysts see these codes often in web logs.

---

### 6. Cookies & Sessions

HTTP is stateless → it does NOT remember users.  
So websites use:

- **Cookies** ← Stored on the browser  
- **Session IDs** ← Stored on the server  

Attackers target these in:
- Session hijacking  
- Cookie tampering  
- Authentication bypass  

---

### 7. Tools Used in This Room

- Browser developer tools  
- Burp Suite (optional)  
- cURL  
- TryHackMe interactive examples  

Examples:

curl -I https://example.com # Show headers
curl -X POST -d "user=test" https://example.com/login



---

## 😈 How Attackers Abuse HTTP

HTTP is the gateway for most web attacks:

- **SQL Injection**  
- **XSS (Cross-Site Scripting)**  
- **CSRF**  
- **Cookie theft**  
- **Parameter tampering**  
- **Directory traversal**  
- Sending malicious payloads via POST/GET requests  

Understanding HTTP = understanding how web hacking works.

---

## 🧠 Relevance to My Future SOC Role

A SOC Analyst constantly analyzes:
- Proxy logs  
- Web server logs  
- Suspicious URLs  
- Malformed HTTP requests  
- Authentication failures  
- Redirect chains  
- Strange User-Agent values  

This room helped me understand:
- How normal HTTP traffic looks  
- How abnormal/malicious HTTP traffic looks  

This is essential for incident response.

---

## 📝 Summary

This room improved my understanding of how browsers and servers communicate using HTTP.  
I learned how requests and responses work, HTTP methods, status codes, cookies, and how attackers exploit the web.

This knowledge is foundational for web security, SOC analysis, and future penetration testing tasks.
