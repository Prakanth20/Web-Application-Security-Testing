# Web Application Security Testing using DVWA

This repository contains hands-on demonstrations of **OWASP Top 10 Web Application Vulnerabilities** performed in a **controlled lab environment** using **DVWA (Damn Vulnerable Web Application)** on **Kali Linux**.

The project focuses on identifying, exploiting, and mitigating common web vulnerabilities, along with detailed documentation, screenshots, and secure coding fixes.

---

## 📌 Project Objective

* To understand real-world web application vulnerabilities
* To perform controlled exploitation using DVWA
* To demonstrate secure coding practices and mitigations
* To gain practical experience with security tools like **Burp Suite**

---

## 🧪 Lab Environment

* **Operating System:** Kali Linux (VMware)
* **Vulnerable Application:** DVWA
* **Web Server:** Apache + MySQL
* **Security Tool:** Burp Suite Community Edition
* **Browser:** Firefox (Proxy configured)

> ⚠️ All testing was performed **locally and legally** for educational purposes only.

---

## 🔐 Vulnerabilities Covered

### 1️⃣ SQL Injection (SQLi)

**Module:** DVWA → SQL Injection (Low)

**Description:**
SQL Injection occurs when user input is directly embedded into SQL queries without proper validation, allowing attackers to manipulate database queries.

**Attacks Performed:**

* Authentication bypass
* Data extraction using UNION-based injection

**Example Payloads:**

```
1 OR 1=1
1' UNION SELECT user, password FROM users#
```

**Impact:**

* Disclosure of usernames and password hashes
* Unauthorized database access

**Mitigation:**

* Prepared Statements
* Input validation

---

### 2️⃣ Cross-Site Scripting (XSS)

#### 🔹 Reflected XSS

* Payload injected via URL parameters
* Executed immediately in browser response

Example:

```
<script>alert('XSS')</script>
```

#### 🔹 Stored XSS

* Payload stored in application database
* Executes whenever the page is loaded

#### 🔹 DOM-Based XSS

* Vulnerability exists in client-side JavaScript
* No server-side validation involved

**Impact:**

* Session hijacking
* Credential theft
* Malicious script execution

**Mitigation:**

* Output encoding
* Input validation
* Content Security Policy (CSP)

---

### 3️⃣ Cross-Site Request Forgery (CSRF)

**Module:** DVWA → CSRF

**Description:**
CSRF forces authenticated users to perform unwanted actions without their consent.

**Attack Demonstrated:**

* Password change request captured and replayed using Burp Suite

**Observation:**

* Password changed without CSRF token validation

**Impact:**

* Account takeover
* Unauthorized state-changing actions

**Mitigation:**

* CSRF tokens
* SameSite cookies
* POST-only sensitive actions

---

### 4️⃣ File Inclusion Attacks 

**Module:** DVWA → File Inclusion

**Attack Performed:**
Remote File Inclusion (RFI)

**Payload Used:**

```
page=www.google.com
```

**Result:**

* External page successfully loaded inside DVWA

**Impact:**

* Sensitive file disclosure
* Remote code execution

**Mitigation:**

* Disable `allow_url_include`
* Whitelist allowed file paths
* Avoid dynamic file inclusion

---

### 5️⃣ Burp Suite – Advanced Usage

**Features Used:**

* Proxy interception
* Request modification
* Intruder fuzzing

**Demonstrations:**

* Intercepting login requests
* Modifying parameters
* Analyzing server responses

---

## 🛡️ Security Fixes Implemented

* Prepared SQL statements
* Input validation & sanitization
* CSRF token implementation
* Secure file inclusion logic
* HTTP security best practices

---

## 🎯 Learning Outcomes

* Practical understanding of OWASP Top 10 vulnerabilities
* Hands-on exploitation experience
* Secure coding and mitigation techniques
* Real-world usage of Burp Suite

---

## ⚠️ Disclaimer

This project is strictly for **educational purposes**. The techniques demonstrated must **not** be used on real systems without proper authorization.

---
