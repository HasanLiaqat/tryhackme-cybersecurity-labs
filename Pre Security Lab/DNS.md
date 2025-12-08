# 🌐 Networking Fundamentals: What is DNS?

**Date Completed:** 8 December 2025

**Room/Module:** What is DNS?

**Focus:** Understanding the Domain Name System (DNS), its hierarchy, record types, and the process of domain resolution.

---

### Objective Achieved
I gained a clear understanding of how the Domain Name System (DNS) works to translate human-readable domain names (like tryhackme.com) into numerical IP addresses, which are necessary for communication across the Internet.

### Key Concepts Covered
* **What is DNS?** DNS is essentially the "phonebook" of the Internet, used to resolve domain names to IP addresses.
* **Domain Hierarchy:** DNS uses a hierarchical structure, organized from the **Root** (.), to **TLDs** (Top-Level Domains like .com, .org), to **Second-Level Domains** (like google, tryhackme), and finally to **Subdomains** (like mail.google.com).
* **Record Types:** Learned about the different types of records stored on a DNS server, including:
    * **A Record:** Maps a domain name to an IPv4 address.
    * **AAAA Record:** Maps a domain name to an IPv6 address.
    * **CNAME Record:** Used to alias one domain name to another (e.g., mail.example.com points to a different server).
    * **MX Record:** Specifies the mail server responsible for accepting email messages for a domain.
    * **TXT Record:** Used to store human-readable text information (often used for security features like SPF/DKIM).
* **Request Process:** Studied the steps a device takes to recursively query DNS servers (Resolver $\rightarrow$ Root $\rightarrow$ TLD $\rightarrow$ Authoritative Server) to get the final IP address.

### Practical Steps Taken
1. **Tool Familiarization:** Used or learned about command-line tools like `dig` or `nslookup` to manually query DNS servers and analyze different record types (A, CNAME, MX).
2. **Hierarchy Exploration:** Practiced navigating and understanding the relationship between different parts of a Fully Qualified Domain Name (FQDN).
3. **Resolution Simulation:** Applied the knowledge of the request process to understand how a browser resolves a domain name before establishing a connection.

---

## Next Steps
* I will continue to build on my foundational networking knowledge by moving on to the learning of learning of http in detail.
