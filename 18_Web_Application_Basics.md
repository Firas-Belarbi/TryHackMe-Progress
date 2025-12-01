# 🌐 **Web Application Basics – TryHackMe**

---

## 🧩 **Room Overview**

This module covers the fundamental elements of web applications, focusing on URLs, HTTP requests, and responses.

Ideal for beginners or anyone wanting to understand how web apps work.

- **Platform:** TryHackMe  
- **Path:** Introduction / Web Applications  
- **Status:** ✅ Completed  
- **Focus:** Understanding web app components, communication, and security basics

---

## 🎯 **Learning Objectives**

- **Understand** what a web application is and how browsers interact with it  
- **Break down** the components of a URL  
- **Learn** the structure of HTTP requests and responses  
- **Get familiar** with HTTP methods and status codes  
- **Discover** important HTTP security headers

---

## 🔑 **Key Concepts Learned**

### 1. **What is a Web Application?**

A web app is a program accessed via a browser, consisting of:

- **Front End:** What users see (**HTML, CSS, JavaScript**)  
- **Back End:** Servers, databases, and APIs handling data and logic  
- **WAF (Web Application Firewall):** Protects the app from malicious attacks

---

### 2. **Anatomy of a URL**

URLs are addresses used to access online resources.

**URL Components:**

- **Scheme:** Protocol used (**http** or **https**)  
- **User Info:** Optional login credentials  
- **Host:** Domain name or IP address  
- **Port:** Connection point (usually **80** or **443**)  
- **Path:** Location of a specific resource  
- **Query String:** Extra data (search terms, form inputs)  
- **Fragment:** Points to a section within the page  

---

### 3. **HTTP Messages**

#### **HTTP Requests**

Sent by clients to servers and consist of:

- **Start Line:** Method, URL path, HTTP version  
- **Headers:** Metadata like **Host**, **User-Agent**, **Content-Type**  
- **Body:** Data sent in **POST** or **PUT** requests

**Common HTTP Methods:**

- **GET:** Retrieve data  
- **POST:** Send data  
- **PUT/DELETE:** Modify or delete resources  

#### **HTTP Responses**

Sent by servers to clients and contain:

- **Status Line:** HTTP version, status code, reason phrase  
- **Headers:** Metadata like **Content-Type**, **Set-Cookie**  
- **Body:** Actual content (**HTML, JSON, images**)  

---

### 4. **HTTP Status Codes**

**Categories:**

- **1xx:** Informational  
- **2xx:** Success (e.g., **200 OK**)  
- **3xx:** Redirection (e.g., **301 Moved Permanently**)  
- **4xx:** Client Errors (e.g., **404 Not Found**)  
- **5xx:** Server Errors (e.g., **500 Internal Server Error**)  

---

### 5. **Security Headers**

Headers that improve web app security:

- **Content-Security-Policy (CSP):** Restricts allowed content sources  
- **Strict-Transport-Security (HSTS):** Enforces HTTPS usage  
- **X-Content-Type-Options:** Prevents MIME type sniffing  
- **Referrer-Policy:** Controls referrer information sent

---

## 🛠 **Practical Tasks**

1. **GET Request**  
- Select the **GET** method  
- Set the **URL** to `/api/users` as specified  
- Click **Go**  
- The flag will appear in the **HTTP Response**:  
  `THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}`

2. **POST Request**  
- Select the **POST** method  
- Change the **URL** to `/api/user/2` as specified  
- In settings, add the key `country` with value `US`  
- Click **Go**  
- The flag will appear:  
  `THM{YOU_HAVE_MODIFIED_THE_USER_DATA}`

3. **DELETE Request**  
- Select the **DELETE** method  
- Change the **URL** to `/api/user/1`  
- Remove any previous POST settings such as the `country` key  
- Click **Go**  
- The flag will appear in the response:  
  `THM{YOU_HAVE_JUST_DELETED_A_USER}`
