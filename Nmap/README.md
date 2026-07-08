# TryHackMe — Further Nmap

**Room link:** https://tryhackme.com/room/furthernmap
**Category:** Network Security / Reconnaissance
**Difficulty:** Easy/Medium

## Overview

This room builds on basic Nmap usage and dives into scan types, the Nmap Scripting Engine (NSE), and firewall evasion techniques. It's a natural follow-up to any intro-level networking/Nmap room and lays the groundwork for effective reconnaissance in later pentesting rooms.

## Task Breakdown

### Task 1 — Deploy
Deploys the target machine for the room.

### Task 2 — Introduction
Sets the scope: going beyond basic port scanning into scan types, NSE, and evasion.

### Task 3 — Nmap Switches
Core Nmap flags:

| Switch | Purpose |
|---|---|
| `-sS` | SYN scan |
| `-sU` | UDP scan |
| `-O` | OS detection |
| `-sV` | Service/version detection |
| `-v` / `-vv` | Verbosity levels 1 / 2 |
| `-oN` | Save output — normal format |
| `-oG` | Save output — grepable format |
| `-oA` | Save output — all three formats (normal, XML, grepable) |
| `-A` | Aggressive mode (OS detection + version detection + script scan + traceroute) |
| `-T5` | Timing template level 5 (fastest, noisiest) |
| `-p 80` | Scan a single port |
| `-p 1000-1500` | Scan a port range |
| `-p-` | Scan all 65535 ports |
| `--script=<name>` | Run a specific NSE script |
| `--script=vuln` | Run all scripts in the "vuln" category |

### Task 4 — Scan Types Overview
Introduces the different scan types Nmap supports and why choosing the right one matters (stealth, accuracy, speed, firewall/IDS evasion).

### Task 5 — Scan Types: TCP Connect Scans
`-sT` — completes the full TCP three-way handshake. Reliable but noisy and easily logged (no raw socket privileges needed).

### Task 6 — Scan Types: SYN Scans
`-sS` — the default and most popular scan type. Sends a SYN, doesn't complete the handshake ("half-open" scan), making it faster and stealthier than a full connect scan. Requires root/raw socket access.

### Task 7 — Scan Types: UDP Scans
`-sU` — scans UDP ports. Much slower and less reliable than TCP scanning because UDP is connectionless; relies on ICMP "port unreachable" responses to infer closed ports.

### Task 8 — Scan Types: NULL, FIN, and Xmas
Stealth scan variants that manipulate TCP flags to slip past simple firewalls/IDS:
- **NULL scan** (`-sN`) — no flags set
- **FIN scan** (`-sF`) — only the FIN flag set
- **Xmas scan** (`-sX`) — FIN, PSH, and URG flags set ("lit up like a Christmas tree")

These rely on RFC 793 behavior: closed ports should respond with RST, open/filtered ports stay silent. Only works reliably against Unix-like TCP/IP stacks — Windows doesn't follow this behavior.

### Task 9 — Scan Types: ICMP Network Scanning
Host discovery using ICMP (ping sweeps) — `-sn` to skip port scanning and just determine which hosts are alive.

### Task 10 — NSE Scripts Overview
Introduces the Nmap Scripting Engine — Lua-based scripts stored in `/usr/share/nmap/scripts/` that extend Nmap's functionality (vulnerability detection, brute-forcing, enumeration, etc.), categorized into groups like `auth`, `brute`, `default`, `discovery`, `vuln`, etc.

### Task 11 — NSE Scripts: Working with the NSE
Covers running scripts and passing arguments:
```
nmap --script <script-name> --script-args <script>.<arg>=<value> <target>
```
Example: `ftp-anon.nse` takes the optional `maxlist` argument to cap directory listing output length.

### Task 12 — NSE Scripts: Searching for Scripts
Covers finding relevant scripts by browsing `/usr/share/nmap/scripts/` or using `grep`, e.g.:
```
ls /usr/share/nmap/scripts/ | grep smb
```
Found `smb-os-discovery.nse` — determines the underlying OS of an SMB server. Inspecting the script header shows it depends on `smb-brute.nse` (uses discovered/valid credentials to pull richer OS/version/domain info via authenticated queries).

### Task 13 — Firewall Evasion
Techniques for evading firewalls and IDS/IPS during scans — e.g., fragmenting packets (`-f`), spoofing source IP/port, using decoys (`-D`), and adjusting timing to avoid detection thresholds.

### Task 14 — Practical
Applies everything learned to a live target — combining scan types, timing, NSE scripts, and evasion techniques for a real-world style reconnaissance exercise.

### Task 15 — Conclusion
Wrap-up of key takeaways and next steps.

## Key Takeaways
- **SYN scans (`-sS`)** are the default sweet spot: fast, relatively stealthy, requires root.
- **UDP scanning** is slow and unreliable but necessary — many services (DNS, SNMP, DHCP) only run on UDP.
- **NULL/FIN/Xmas scans** are useful for evading basic stateless firewalls, but unreliable against Windows targets.
- **NSE turns Nmap into a lightweight vulnerability scanner** — always check the `vuln` and `default` categories for a target.
- **Always save your scan output** (`-oA`) — avoids re-scanning (less noise, less detection risk) and gives you data for reporting.
- **Firewall evasion techniques exist but are situational** — use them deliberately, not by default, since they trade reliability/speed for stealth.
