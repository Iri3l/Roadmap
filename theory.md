# MASTER HUB: Cybersecurity Theory and Practice (Level 1-3) - ENCYCLOPEDIA

This document is the ultimate source of knowledge, detailed and complete, for theoretical and practical preparation.

---

## 🛡️ Part 0: Cyber Security Fundamentals (NCFE Level 3 - Unit 1)

### 1. What is Cyber Security?
*   **Definition:** The application of technologies, processes, and controls to protect systems, networks, programs, devices, and data from cyber attacks.
*   **Goal:** To reduce the risk of cyber attacks and protect against unauthorized exploitation.

### 2. Brief History
*   **1947:** The first software "bug" – an actual moth caught in a computer at Harvard.
*   **70s:** *The Creeper* (first malware) and *The Reaper* (first antivirus).
*   **80s:** RSA (cryptography) and the first conviction for a computer worm (Robert Morris).
*   **Present:** Legislations such as GDPR following massive breaches (Equifax, Yahoo).

### 3. The 9 Key Concepts in Cyber Security
1.  **Security:** Protection of hardware and software systems.
2.  **Identity:** Verification of users/devices.
3.  **Threat:** Malicious attack (Malware, DDoS).
4.  **Confidentiality:** Access only for those authorized.
5.  **Integrity:** Protecting data against unauthorized changes.
6.  **Availability:** Accessibility of data when needed. (4, 5, 6 = **CIA Triad**).
7.  **Vulnerability:** A weakness that can be exploited.
8.  **Risk:** The probability and impact of an incident.
9.  **Hazard:** An element that can lead to a breach (location, behavior).

### 4. Consequences of Inadequate Security
*   **Economic Costs:** Theft of IP, financial data, loss of revenue.
*   **Reputational Damage:** Loss of customer trust.
*   **Legal Consequences:** Major fines (e.g., GDPR violations).

### 5. Cybersecurity Actors (Threat Actors vs. Security Actors)
An **actor** is any entity participating in a security event.

#### A. Threat Actors (The Attackers)
*   **Cybercriminals:** Motivated by profit (Ransomware).
*   **State-Sponsored (APT):** Government-backed groups (Espionage).
*   **Hacktivists:** Political/social causes (Anonymous).
*   **Insider Threats:** Employees with legitimate access who do harm.
*   **Script Kiddies:** Amateurs using ready-made tools.

#### B. Security Actors (The Defenders)
*   **Ethical Hackers (White Hats):** Test systems with permission.
*   **Blue Team:** Internal team (SOC) that monitors and defends.
*   **Security Researchers:** Discover new vulnerabilities (Zero-days).

#### C. Security Teams (Red, Blue, Purple)
*   **🔴 Red Team:** Ethical attackers (Offensive Mindset).
*   **🔵 Blue Team:** Defenders (Defensive Mindset).
*   **🟣 Purple Team:** Collaboration between Red and Blue to improve alerts.

---

## 🛡️ Part 1: Security and Management (ISC2 CC)

### 1. Risk Management
*   **Formula:** RISK = Threat × Vulnerability × Impact.
*   **Treatment:** Avoidance, Mitigation, Transfer, Acceptance.

### 2. Cyber Kill Chain (Lockheed Martin Model)
This model describes the 7 stages of a cyber attack. The security team's objective is to detect and interrupt the attack as early as possible in this chain.

1.  **Reconnaissance:** Research and planning stage. The attacker gathers information about the infrastructure, employees, and exposed technologies.
    *   **Types of Recon:**
        1.  **Passive Recon:** No direct interaction with the target (e.g., Google searches/OSINT, Social Media scraping, WHOIS lookups). It is undetectable.
        2.  **Active Recon:** Direct contact with the target's systems (e.g., port scanning with Nmap, **Banner Grabbing**, exploring open services). Can be detected by monitoring systems (IDS/IPS).
    *   **Email Harvesting:** The process of collecting email addresses from public sources to prepare Phishing attacks.
    *   **Key Tools:**
        *   **theHarvester:** Collects emails, subdomains, names, IPs, and URLs.
        *   **Hunter.io:** Specialized tool for finding professional email addresses associated with a domain.
        *   **OSINT Framework:** A centralized web resource that organizes OSINT tools by category.
2.  **Weaponization:** The attacker turns raw information into attack tools, creating malware and coupling exploits into a payload.
    *   **Key Definitions:**
        1.  **Malware:** Program designed to destroy or gain unauthorized access.
        2.  **Exploit:** Code that takes advantage of an error (bug) in an application or system.
        3.  **Payload:** The actual malicious code the attacker wants to run on the target.
    *   **Weaponization Tactics:**
        *   **Malicious Macros / VBA:** Automatic scripts hidden in Microsoft Office documents.
        *   **USB Worms:** Creating payloads that spread automatically through USB sticks.
        *   **Backdoor:** Installing a program that allows later access bypassing security.
        *   **Phishing Templates:** Customizing pages and emails to appear legitimate.
3.  **Delivery:** Choosing the method of transmitting the payload to the victim.
    *   **Methods:**
        1.  **Phishing Email:** Sending malicious links or attachments. **Spear Phishing** is a targeted attack on a specific person.
        2.  **USB Drops:** Physical attack by leaving infected USB sticks in public places or sending them by mail.
        3.  **Watering Hole Attack:** Attacker infects a legitimate site frequently visited by the target group.
        4.  **Drive-by Download:** Automatic and unintentional download of malware in the victim's browser.
4.  **Exploitation:** The moment the attacker's code runs on the target, taking advantage of a vulnerability.
    *   **Techniques:**
        1.  **Malicious Macros:** Executed when the victim opens an infected document.
        2.  **Zero-day Exploit:** Takes advantage of vulnerabilities unknown to the manufacturer.
        3.  **Known CVEs:** Exploiting public vulnerabilities (Common Vulnerabilities and Exposures) that haven't been patched.
    *   **🔍 Signs of Exploitation (SOC Monitoring):**
        *   Appearance of new, unexpected processes.
        *   Changes in system registries or creation of new services.
        *   Suspect command line arguments found in logs.
5.  **Installation:** The attacker ensures **Persistence** on the system, so they can return anytime without re-exploiting the initial vulnerability.
    *   **Methods and Techniques:**
        1.  **Scheduled Tasks / Cron Jobs:** Automatic execution of code at set intervals.
        2.  **Persistent Backdoors:** Using tools like **Meterpreter** (from Metasploit) to obtain a permanent interactive shell.
        3.  **Windows Services:** Creating or modifying Windows services using `sc.exe` to run malware at system startup (Masquerading).
        4.  **Registry Run Keys & Startup Folder:** Adding malware to registry keys that start with the user.
        5.  **Web Shell:** A script (PHP, ASP, JSP) uploaded to the server for access via browser.
        6.  **Timestomping:** **Anti-Forensics** technique where the attacker modifies file timestamps to make them appear old/legitimate.
6.  **Command & Control (C2):** The attacker establishes a discreet communication channel ("covert channel") to control the compromised system remotely.
    *   **C2 Beaconing:** The process by which malware on the infected host communicates regularly with the attacker's server to request instructions ("beacons").
    *   **Communication Channels:**
        1.  **IRC (Internet Relay Chat):** Traditional method, now easily detected and blocked.
        2.  **HTTP (80) / HTTPS (443):** Most used modern channels, masking among legitimate web traffic.
        3.  **DNS Tunnelling:** Malware makes constant DNS requests to a server controlled by the attacker.
    *   **Evasion Techniques:**
        1.  **DGA (Domain Generation Algorithms):** Malware generates thousands of random domains to avoid blocking.
        2.  **Fast Flux:** Rapidly changing IPs associated with a domain.
        3.  **Social Media & Cloud:** Using direct messages (X/Twitter) or legitimate services (Dropbox, Google Docs).
7.  **Actions on Objectives:** Final stage where the attacker has "hands-on keyboard" access and fulfills their initial goal.
    *   **Specific Actions:**
        1.  **Credential Harvesting:** Collecting usernames and passwords.
        2.  **Privilege Escalation:** Obtaining higher rights (e.g., from normal user to Domain Admin).
        3.  **Internal Reconnaissance:** Exploring the internal network.
        4.  **Lateral Movement:** Moving from one computer to another within the company.
        5.  **Data Exfiltration:** Theft of sensitive files.
        6.  **Destruction of Backups:** Deleting backups and **Shadow Copies** to force the victim to pay ransom.
        7.  **Data Corruption:** Modifying or deleting data to sabotage activity.

#### 🛡️ Final Countermeasures (Impact Mitigation):
*   **DLP (Data Loss Prevention):** Software that prevents sending sensitive files outside the network.
*   **Network Segmentation:** Isolating critical systems to stop **Lateral Movement**.
*   **Backup & Recovery Plan:** Essential for data recovery after Ransomware.
*   **User Activity Monitoring:** Overseeing behavior to detect anomalies.
*   **Principle of Least Privilege:** Limiting access to the minimum necessary.
*   **EDR / DNS Monitoring / Honeypots.**

#### 📉 Case Study: Target Attack (2013)
One of the largest data thefts in history (40 million cards affected).

| CKC Stage | Icon (Analogy) | Technical Action |
| :--- | :--- | :--- |
| **Weaponization** | 🐞 (Bug) | **PowerShell** (malicious script creation) |
| **Delivery** | 📦 (Sealed Box) | **Spearphishing attachment** (email to vendor) |
| **Exploitation** | 💻 (Open Laptop) | **Exploit public-facing application** (web access) |
| **Installation** | 📤 (Box with Arrow) | **Dynamic Linker Hijacking** (persistence) |
| **Command & Control** | 📢 (Megaphone) | **Fallback Channels** (backup communication) |
| **Actions on Objectives** | 🎯 (Red Target) | **Data from local system** (card theft) |

---

## 🛡️ Part 1: Security and Management (ISC2 CC)

### 3. Authentication and Access (AAA)
*   **Factors:** Something you KNOW (Password), HAVE (Token), ARE (Biometrics).
*   **Models:** DAC (Discretionary), MAC (Mandatory), RBAC (Role-Based).
*   **Principle of Least Privilege:** Minimum rights necessary.
*   **BYOD (Bring Your Own Device):** Personal devices at work (requires MDM and Containerization).

---

## 🌐 Part 2: Networking and Infrastructure (Cisco CCST)

### 1. Network Topologies
*   Star, Mesh, Bus, Ring.

### 2. OSI Model (7 Layers)
1. Physical, 2. Data Link, 3. Network, 4. Transport, 5. Session, 6. Presentation, 7. Application.

### 3. IP Addresses
*   IPv4 (32-bit) vs IPv6 (128-bit). Public vs Private. NAT (Translation).
*   Loopback: `127.0.0.1`. APIPA: `169.254.x.x`.

### 4. Transport Protocols
*   **TCP:** Secure, 3-Way Handshake (SYN, SYN-ACK, ACK).
*   **UDP:** Fast, "Best Effort".

### 5. DNS (Domain Name System) - Detailed
*   **Hierarchy:** Root -> TLD (.com) -> Authoritative (site.com).
*   **Records:** A (IPv4), AAAA (IPv6), MX (Mail), CNAME (Alias), TXT (SPF/DKIM).
*   **DNSSEC:** Digital signatures to prevent DNS Spoofing.

### 6. Network Analysis and Nmap
*   **Wireshark:** Green (HTTP), Blue (UDP), Gray (TCP), Black/Red (Errors).
*   **Nmap Demystified:** Lowercase = Category (`-sS`, `-sV`), Uppercase = Aggressive Technique (`-A`, `-O`).

---

## 🛡️ Part 3: System Security & Linux (Enterprise)

### 0. MITRE ATT&CK Framework
Global reference standard for documenting attacks.
*   **Tactics (Why?):** Final objective (e.g., Initial Access, Persistence).
*   **Techniques (How?):** Specific method (e.g., T1543 - Create new services).

### 1. Linux File Security (chmod)
*   **Octal:** 4 (Read), 2 (Write), 1 (Execute). 755 = rwxr-xr-x.

### 2. CLI Editors and Utilities
*   **Nano vs Vim:** Vim is modal (Insert Mode `i`, Command Mode `Esc`).
*   **Text Manipulation:** `grep`, `tr`, `sed`, `awk`, `sort`, `uniq`.

### 3. Case Study: Privilege Escalation
*   Identifying weaknesses via `sudo -l`.

### 4. Keylogging & Rogue USB
*   **USB Rubber Ducky:** Stick simulating a keyboard executing malicious commands.

---

## 💻 Part 4: Web Vulnerabilities (OWASP Top 10)
1. Broken Access Control, 2. Cryptographic Failures, 3. Injection (SQLi), 4. XSS, 5. SSRF.

---

## 🏭 Part 5: Industrial Control Systems (OT/ICS)
*   **OT Priority:** Availability and human safety over confidentiality.
*   **Terms:** SCADA, PLC, Air-Gapping.

---
*Last update: March 2, 2026. Consolidated for Irinel Lazarovici.*
