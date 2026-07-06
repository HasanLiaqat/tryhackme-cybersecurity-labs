# Web Application Penetration Test – Vulnversity

## Overview

This project documents my penetration testing assessment of the **Vulnversity** machine on TryHackMe. The lab simulates a vulnerable Linux web server and provides hands-on experience with the complete penetration testing lifecycle, from reconnaissance to privilege escalation.

> **Platform:** TryHackMe  
> **Environment:** Authorized training lab  
> **Difficulty:** Beginner

---

## Objectives

- Perform network reconnaissance
- Enumerate exposed services
- Assess the web application
- Identify and validate a file upload vulnerability
- Obtain an initial foothold
- Perform Linux privilege escalation
- Document findings in a professional penetration testing report

---

## Methodology

The assessment followed a structured penetration testing methodology:

### 1. Reconnaissance
- Network scanning
- Service identification
- Version detection

### 2. Enumeration
- Web application analysis
- Directory enumeration
- Upload functionality assessment

### 3. Initial Access
- Validation of insecure file upload controls
- Execution of a server-side payload
- Remote shell access

### 4. Privilege Escalation
- Linux enumeration
- SUID binary analysis
- Privilege escalation to root

---

## Tools Used

- Nmap
- Gobuster
- Burp Suite
- Netcat
- Linux Terminal
- GTFOBins
- TryHackMe AttackBox

---

## Skills Demonstrated

- Network Reconnaissance
- Service Enumeration
- Web Application Testing
- Directory Enumeration
- HTTP Analysis
- File Upload Security Assessment
- Reverse Shell Fundamentals
- Linux Privilege Escalation
- Security Documentation
- Technical Report Writing

---

## Repository Structure

```
vulnversity/
│
├── README.md
├── report.pdf
├── notes.md
└── screenshots/
```

---

## Key Learning Outcomes

- Learned how reconnaissance informs the rest of a penetration test.
- Improved web application enumeration techniques.
- Gained experience identifying insecure file upload mechanisms.
- Practiced Linux privilege escalation through system misconfiguration analysis.
- Strengthened technical documentation and reporting skills.
