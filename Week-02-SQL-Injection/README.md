# Week 2 – SQL Injection Testing with OWASP ZAP & DVWA

![SQL Injection](https://img.shields.io/badge/Vulnerability-SQL%20Injection-red)
![OWASP Top 10](https://img.shields.io/badge/OWASP-A03%3A2021-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

# Overview

This lab demonstrates the process of identifying and analyzing SQL Injection vulnerabilities using OWASP ZAP and Damn Vulnerable Web Application (DVWA).

The objective was to understand how user-supplied input is transmitted through HTTP requests, captured by OWASP ZAP, and analyzed during a manual web application security assessment.

No unauthorized systems were tested. All testing was performed within a controlled laboratory environment.

---

# Learning Objectives

- Understand SQL Injection fundamentals
- Capture HTTP requests using OWASP ZAP
- Analyze GET parameters
- Inspect HTTP Request and Response messages
- Replay requests using the ZAP Requester
- Observe application behavior when modifying parameters
- Practice manual web application testing methodology

---

# Lab Environment

| Component | Version |
|-----------|----------|
| Kali Linux | Latest |
| OWASP ZAP | 2.17 |
| DVWA | Docker |
| Docker | Latest |
| Firefox | Latest |

---

# Target Application

**Damn Vulnerable Web Application (DVWA)**

Target URL:

http://127.0.0.1:4280

Security Level:

Low

---

# Tools Used

- OWASP ZAP
- Firefox Browser
- Docker
- DVWA
- Kali Linux

---

# Testing Methodology

## Step 1

Started DVWA Docker container.

---

## Step 2

Configured Firefox to proxy traffic through OWASP ZAP.

Proxy:

127.0.0.1:8080

---

## Step 3

Logged into DVWA.

Default credentials:

Username:

admin

Password:

password

---

## Step 4

Changed DVWA Security Level to:

Low

---

## Step 5

Navigated to:

SQL Injection

---

## Step 6

Entered several User IDs.

Examples:

1

2

5

Each request was intercepted by OWASP ZAP.

---

## Step 7

Captured the request:

GET /vulnerabilities/sqli/?id=1&Submit=Submit

---

## Step 8

Reviewed:

- HTTP Headers
- Cookies
- Parameters
- Response Body

---

## Step 9

Replayed requests using the OWASP ZAP Requester.

---

# Evidence Collected

- HTTP GET Request
- HTTP Response
- Session Cookie
- PHPSESSID
- Security Level Cookie
- Request Headers
- Response Headers

---

# Sample Request

```http
GET /vulnerabilities/sqli/?id=1&Submit=Submit HTTP/1.1
Host: 127.0.0.1:4280
Cookie: PHPSESSID=********
```
