# Vulnversity Pentest Notes

**Platform:** TryHackMe
**Machine:** Vulnversity
**Environment:** AttackBox
**Assessment Type:** Authorized Training Lab

---

# Reconnaissance

## Initial Network Scan

### Tool

* Nmap

### Objective

Identify open ports, running services, and software versions.

### Result

| Port | Service    | Version       |
| ---- | ---------- | ------------- |
| 21   | FTP        | vsftpd 3.0.5  |
| 22   | SSH        | OpenSSH 8.2   |
| 139  | SMB        | Samba 4.6.2   |
| 445  | SMB        | Samba 4.6.2   |
| 3128 | HTTP Proxy | Squid 4.10    |
| 3333 | HTTP       | Apache 2.4.41 |

### Observation

The primary attack surface was the Apache web server running on port **3333**.

---

# Enumeration

## Web Application

Visited the web application hosted on port **3333**.

### Directory Enumeration

Tool Used:

* Gobuster

Goal:

* Discover hidden directories and application functionality.

### Finding

An undocumented upload page was identified.

```
/internal/
```

This page allowed users to upload files.

---

# Vulnerability Assessment

## File Upload Validation

The upload functionality performed insufficient validation of file extensions.

Testing confirmed that standard PHP uploads were blocked, while an alternative PHP-capable extension bypassed the validation.

### Security Issue

**Insufficient File Upload Validation**

### Impact

An attacker could upload executable server-side code, leading to remote code execution.

---

# Initial Access

A reverse shell payload was successfully executed after bypassing the upload restriction.

### Result

* Remote shell obtained
* Initial access established

---

# Privilege Escalation

Performed Linux privilege escalation enumeration.

Investigated privileged executables and system configuration.

Successfully escalated privileges to administrative (root) access.

---

# Evidence Collected

* Nmap scan
* Gobuster enumeration
* Upload page
* Reverse shell
* Privilege escalation
* Root access confirmation

---

# Key Findings

### High

* Insecure file upload validation leading to remote code execution.

### High

* Privilege escalation due to insecure system configuration.

---

# Remediation Recommendations

* Use allowlist-based file validation.
* Store uploaded files outside the web root.
* Disable execution permissions within upload directories.
* Apply the principle of least privilege.
* Audit privileged binaries regularly.
* Keep server software updated.

---

# Skills Demonstrated

* Network Reconnaissance
* Service Enumeration
* Web Enumeration
* File Upload Assessment
* Linux Enumeration
* Privilege Escalation
* Technical Documentation
* Security Reporting

---

# Lessons Learned

This lab demonstrated the complete penetration testing workflow from reconnaissance through privilege escalation. It reinforced the importance of systematic enumeration, secure file upload validation, and proper privilege management while improving practical reporting and documentation skills.
