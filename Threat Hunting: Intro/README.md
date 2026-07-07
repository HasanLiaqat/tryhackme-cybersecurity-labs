# TryHackMe — Threat Hunting: Introduction

**Room link:** https://tryhackme.com/room/threathuntingintro
**Category:** Blue Team / Threat Hunting
**Difficulty:** Easy/Info

## Overview

This room introduces the fundamentals of threat hunting — proactively searching for threats that evade automated detection, rather than waiting for alerts. It covers hunting approaches, hunting targets, hunting techniques, and a practical scenario applying these concepts.

## Task Breakdown

### Task 1 — Introduction
Sets the scene for why threat hunting matters as a proactive complement to reactive incident response.

### Task 2 — What Is Threat Hunting
Defines threat hunting as the proactive, analyst-driven search for signs of compromise that automated tools (SIEM/EDR alerts) may have missed. Distinguishes it from reactive security operations.

### Task 3 — Hunting Approaches
Covers the three main methodologies:
- **Hypothesis-driven hunting** — starting from an assumption (e.g., "an attacker may be using PowerShell for lateral movement") and searching for evidence to prove/disprove it.
- **Intelligence-driven hunting** — using threat intel reports, IOCs, and TTPs from known threat actors to guide the hunt.
- **Indicator-driven hunting** — searching directly for known indicators of compromise (hashes, IPs, domains).

### Task 4 — Hunting Targets
Covers what hunters are actually looking for:
- **Malware** — files, processes, and payloads.
- **Attack residues** — artifacts left behind after activity (logs, registry changes, temp files).
- **Vulnerabilities** — exploitable weaknesses an attacker could leverage.

### Task 5 — Hunting Techniques
Covers the practical, tool-level techniques used to hunt:

| Technique | Description | Example |
|---|---|---|
| **Attack Signatures** | Specific patterns (hashes, command-line params, behavior sequences) | `powershell.exe -EncodedCommand` |
| **Indicators of Compromise (IOCs)** | Exact-match artifacts from threat intel (hashes, IPs, domains, emails, URLs) | C2 IP address match in firewall logs |
| **Behavioral Pattern Analysis** | Sequences of events that together indicate malicious activity | `winword.exe → cmd.exe → powershell.exe → external IP` |
| **Logical Queries & Anomaly Detection** | Conditional queries for deviations from normal baseline activity | Admin commands run at 3 AM |

All techniques map back to **MITRE ATT&CK** technique IDs for context (e.g., T1059.001, T1547, T1071).

### Task 6 — Practical
Applied the above concepts to a fictional threat intelligence report on **APT-Serpent**, a simulated financially-motivated, state-aligned APT group.

**Key findings from the APT-Serpent report:**
- **Initial Access:** Spear-phishing emails with weaponized Office documents exploiting `CVE-2023-21716` macros.
- **Persistence:** `CustomBackdoor` implant + `PersistenceToolkit` — scheduled tasks, WMI event subscriptions, registry Run keys, DLL search-order hijacking.
- **Lateral Movement:** Pass-the-hash (stolen NTLM credentials), RDP pivoting through jump hosts.
- **Exfiltration:** Data staged, compressed with 7z, encrypted, and exfiltrated over HTTPS.
- **C2 Beacon Interval:** CustomBackdoor beacons to its C2 every **300 seconds**.

### Task 7
Wrap-up / room completion.

## Key Takeaways
- Threat hunting is proactive and hypothesis/intel-driven, not alert-reactive.
- No single data source tells the full story — correlate EDR, SIEM, network, and DNS logs together.
- IOCs are useful but perishable (attackers rotate infrastructure); behavioral and logical-query techniques catch what static IOCs miss.
- Real-world hunts blend multiple techniques: IOC sweep → behavioral pattern search → custom logical queries.
- MITRE ATT&CK is the common language connecting hunting techniques to known adversary behavior.

---
*Part of my TryHackMe write-ups repo.*
