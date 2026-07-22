# Week 02 – SQL Injection Testing with OWASP ZAP & DVWA

<p align="center">
<img src="../owasp-zap-banner.png" width="900">
</p>

---

# Executive Summary

This laboratory demonstrates the identification and analysis of a **SQL Injection (SQLi)** vulnerability using **OWASP ZAP** against the **Damn Vulnerable Web Application (DVWA)** in a controlled penetration testing environment.

SQL Injection remains one of the most critical web application vulnerabilities because it allows attackers to manipulate backend SQL queries through unsanitized user input. Successful exploitation may lead to unauthorized disclosure of sensitive information, authentication bypass, database modification, and complete compromise of backend systems.

Using OWASP ZAP as an intercepting proxy, HTTP requests and responses were captured, analyzed, and replayed to observe how user-controlled parameters were transmitted to the application.

> **This laboratory was conducted for educational purposes only in an isolated lab environment. No production systems were targeted.**

---

# Lab Information

| Item | Value |
|------|-------|
| Lab | Week 02 – SQL Injection |
| Platform | DVWA |
| Tool | OWASP ZAP 2.17 |
| Browser | Mozilla Firefox |
| Operating System | Kali Linux |
| Deployment | Docker |
| Target URL | http://127.0.0.1:4280 |
| Security Level | Low |

---

# Objectives

The objectives of this laboratory were to:

- Understand SQL Injection fundamentals
- Configure OWASP ZAP as an intercepting proxy
- Capture HTTP requests and responses
- Analyze SQL Injection parameters
- Observe how user input reaches backend SQL queries
- Document the vulnerability using industry-standard reporting practices
- Develop penetration testing documentation suitable for a cybersecurity portfolio

---

# Tools Used

- OWASP ZAP 2.17
- Mozilla Firefox
- DVWA
- Docker
- Kali Linux
- GitHub

---

# Vulnerability Overview

## What is SQL Injection?

SQL Injection is a web application vulnerability that occurs when user input is incorporated into SQL queries without proper validation or parameterization.

An attacker may manipulate SQL statements to:

- Read confidential information
- Bypass authentication
- Enumerate database structures
- Modify database records
- Delete sensitive information
- Execute administrative database commands

---

# OWASP Top 10 Mapping

| Category | Mapping |
|-----------|----------|
| OWASP Top 10 | A03:2021 – Injection |
| CWE | CWE-89 |
| MITRE ATT&CK | T1190 – Exploit Public-Facing Application |

---

# Lab Methodology

The assessment followed the methodology below:

1. Deploy DVWA using Docker.
2. Configure Firefox to use OWASP ZAP as a proxy.
3. Browse the SQL Injection page.
4. Capture HTTP traffic.
5. Review intercepted HTTP requests.
6. Inspect HTTP responses.
7. Replay requests using the ZAP Requester.
8. Observe application behavior.
9. Document findings.
10. Recommend mitigations.

---

# Screenshots

## SQL Injection Page

![SQL Injection Page](screenshots/01-sql-page.png)

**Figure 1:** DVWA SQL Injection page configured with Security Level set to Low.

---

## Normal User Input

![Normal Input](screenshots/02-normal-query.png)

**Figure 2:** Submission of a normal User ID through the SQL Injection form.

---

## HTTP Request Captured

![HTTP Request](screenshots/03-zap-request.png)

**Figure 3:** OWASP ZAP intercepted the HTTP GET request containing the SQL Injection parameter.

---

## HTTP Response

![HTTP Response](screenshots/04-http-response.png)

**Figure 4:** HTTP 200 OK response returned by the web server. The response confirms successful processing of the request and reflects application behavior.

---

## Request Replay

![Requester](screenshots/05-requester.png)

**Figure 5:** The Requester tool was used to replay captured HTTP requests for manual inspection without interacting directly with the browser.

---

# Findings

## Finding 1

### SQL Injection Entry Point

**Severity:** High

**Observation**

The application accepts user-controlled input through the **id** parameter.

```
GET /vulnerabilities/sqli/?id=1&Submit=Submit
```

Because the parameter is incorporated into backend SQL queries without proper sanitization, it represents a potential SQL Injection entry point.

---

## Finding 2

### User Input Passed Directly

**Severity:** High

**Observation**

Captured HTTP requests demonstrate that user input is transmitted directly to the application.

This behavior indicates that malicious SQL statements may be processed if appropriate validation is absent.

---

## Finding 3

### HTTP Response Analysis

**Severity:** Informational

**Observation**

The application responded with:

```
HTTP/1.1 200 OK
```

indicating that the request was processed successfully.

---

# Risk Assessment

| Risk | Impact |
|-------|---------|
| Authentication Bypass | High |
| Unauthorized Data Access | Critical |
| Database Enumeration | High |
| Data Modification | Critical |
| Data Deletion | Critical |
| Administrative Access | High |

Overall Risk Rating:

# 🔴 HIGH

---

# Remediation Recommendations

To mitigate SQL Injection vulnerabilities:

- Use parameterized SQL queries.
- Implement prepared statements.
- Validate and sanitize all user input.
- Apply allow-list validation.
- Escape special SQL characters where appropriate.
- Use least-privilege database accounts.
- Implement centralized error handling.
- Deploy a Web Application Firewall (WAF).
- Conduct regular penetration testing.
- Integrate secure coding practices into the SDLC.

---

# Skills Demonstrated

- Web Application Security Testing
- SQL Injection Analysis
- HTTP Protocol Analysis
- OWASP ZAP
- Request Interception
- Manual Penetration Testing
- Vulnerability Documentation
- Technical Report Writing
- GitHub Documentation
- Risk Assessment

---

# Learning Outcomes

This exercise strengthened practical experience in:

- Understanding SQL Injection attacks
- Capturing HTTP requests
- Analyzing HTTP responses
- Identifying vulnerable input parameters
- Performing manual request replay
- Writing professional penetration testing reports

---

# References

OWASP SQL Injection

https://owasp.org/www-community/attacks/SQL_Injection

OWASP ZAP

https://www.zaproxy.org/

DVWA

https://github.com/digininja/DVWA

MITRE ATT&CK

https://attack.mitre.org/

---

# Disclaimer

This project was conducted inside an isolated penetration testing laboratory using the Damn Vulnerable Web Application (DVWA).

All testing was performed exclusively for educational purposes. No production environments, public systems, or third-party infrastructure were targeted.
