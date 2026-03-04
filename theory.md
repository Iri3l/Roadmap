# MASTER HUB: Cybersecurity Theory and Practice (Level 1-3) - ENCYCLOPEDIA

This document is the ultimate source of knowledge, detailed and complete, for theoretical and practical preparation.

---

## 🛡️ Part 0: Cyber Security Fundamentals (NCFE Level 3 - Unit 1)

### 1. What is Cyber Security?
*   **Definition:** The application of technologies, processes, and controls to protect systems, networks, programs, devices, and data from cyber attacks.
*   **Goal:** To reduce the risk of cyber attacks and protect against unauthorized exploitation.

### 2. Brief History
*   **1947:** The first software "bug" – a real moth caught in a computer at Harvard.
*   **1970s:** *The Creeper* (first malware) and *The Reaper* (first antivirus).
*   **1980s:** RSA (cryptography) and the first conviction for a computer worm (Robert Morris).
*   **Present:** Regulations like GDPR following massive breaches (Equifax, Yahoo).

### 3. The 9 Key Concepts in Cyber Security
1.  **Security:** Protecting hardware and software systems.
2.  **Identity:** Verification of users/devices.
3.  **Threat:** Malicious attack (Malware, DDoS).
4.  **Confidentiality:** Access only for authorized parties.
5.  **Integrity:** Protecting data from unauthorized modification.
6.  **Availability:** Data accessibility when needed. (4, 5, 6 = **CIA Triad**).
7.  **Vulnerability:** A weakness that can be exploited.
8.  **Risk:** The probability and impact of an incident.
9.  **Hazard:** An element that could lead to a breach (location, behavior).

### 4. Consequences of Inadequate Security
*   **Economic Costs:** Theft of IP, financial data, loss of revenue.
*   **Reputational Damage:** Loss of customer trust.
*   **Legal Consequences:** Major fines (e.g., GDPR violations).

### 5. Cyber Security in the UK (NCSC & GCHQ)
As you prepare for the UK job market, it is vital to know the authorities that define the standards:
*   **GCHQ (Government Communications Headquarters):** The UK intelligence agency specializing in signals and communications (SIGINT).
*   **NCSC (National Cyber Security Centre):** Part of GCHQ but with a **public** role.
    *   *Role:* Provides support for citizens, companies, and critical infrastructure.
    *   *Key Resource:* **"10 Steps to Cyber Security"** - The standard NCSC guide for protecting organizations.

### 6. Actors in Cybersecurity (Threat Actors vs. Security Actors)
An **actor** is any entity participating in a security event.

#### A. Threat Actors (The Attackers)
*   **Cybercriminals:** Motivated by profit (Ransomware).
*   **State-Sponsored (APT):** Groups backed by governments (Espionage).
*   **Hacktivists:** Political/social causes (Anonymous).
*   **Insider Threats:** Employees with legitimate access who cause harm.
*   **Script Kiddies:** Amateurs using ready-made tools.

#### B. Security Actors (The Defenders)
*   **Ethical Hackers (White Hats):** Testing systems with permission.
*   **Blue Team:** Internal team (SOC) that monitors and defends.
*   **Security Researchers:** Discovering new vulnerabilities (Zero-days).

#### C. Security Teams (Red, Blue, Purple)
*   **🔴 Red Team:** Ethical attackers (Offensive Mindset).
*   **🔵 Blue Team:** Defenders (Defensive Mindset).
*   **🟣 Purple Team:** Collaboration between Red and Blue to improve alerts.

---

## 🛡️ Part 1: Security and Management (ISC2 CC)

### 1. Risk Management
*   **Formula:** RISK = Threat × Vulnerability × Impact.
*   **Treatment:** Avoidance, Mitigation, Transfer, Acceptance.

### 1.1 Security by Design
Integrating security from day one of system development, not at the end ("bolted-on").
*   **The 5 NCSC Pillars:**
    1.  **Establish the Context:** Understand the data value through *Threat Modeling*.
    2.  **Make Compromise Difficult:** Reduce the attack surface (Secure-by-Default).
    3.  **Make Disruption Difficult:** Ensure resilience through *Redundancy*.
    4.  **Make Detection Easier:** Prepare detection through *Detailed Logging*.
    5.  **Reduce Impact:** Limit damage through *Segmentation and Least Privilege*.

#### 🛡️ Secure by Default (NCSC UK Approach)
*   **Principle:** Security should not be a separate purchase or a complicated configuration. The device must be secure "out of the box."

### 1.2 Cyber Threat Intelligence (CTI)
CTI transforms raw data into actionable knowledge to prevent attacks.

#### A. The 4 Levels of Intelligence
1.  **Strategic:** (Executive Level). Motivations, global trends, and long-term risks.
2.  **Tactical:** (Architectural Level). Focuses on **TTPs** (Tactics, Techniques, and Procedures).
3.  **Operational:** (SOC Level). Details about specific ongoing attack campaigns.
4.  **Technical:** (Automated Level). Tiny details (IoCs - IP addresses, hashes).

### 1.3 Cyber Threat Categories
1.  **Malware:** Ransomware, Trojans, Spyware, Worms.
2.  **Social Engineering:** Phishing, Vishing, Pretexting.
3.  **Network-based:** DDoS, Man-in-the-Middle, DNS Spoofing.
4.  **Web Application:** SQLi, XSS, Broken Access Control.
5.  **Insider Threats:** Malicious or negligent employees.

### 2. Cyber Kill Chain (Lockheed Martin Model)
1. Recon -> 2. Weaponization -> 3. Delivery -> 4. Exploitation (Zero-day) -> 5. Installation (Persistence) -> 6. Command & Control (Beaconing) -> 7. Actions on Objectives.

### 3. Authentication and Access (AAA)
*   **Factors:** Something you KNOW, HAVE, ARE.
*   **Models:** DAC, MAC, RBAC.
*   **Principle of Least Privilege:** Minimum rights necessary.

---

## 🌐 Part 2: Networking and Infrastructure (Cisco CCST)

### 1. Network Topologies
*   Star, Mesh, Bus, Ring.

### 2. OSI Model (7 Layers)
1. Physical, 2. Data Link, 3. Network, 4. Transport, 5. Session, 6. Presentation, 7. Application.

### 3. IP Addresses
*   IPv4 vs IPv6. Public vs Private. NAT.
*   Loopback: `127.0.0.1`. APIPA: `169.254.x.x`.

### 4. Nmap Logic
*   Small letters = Category (`-sS`, `-sV`).
*   Capital letters = Aggressive techniques (`-A`, `-O`).

---

## 🛡️ Part 3: Systems Security & Linux (Enterprise)

### 1. Linux File Security (chmod)
*   **Octal:** 4 (Read), 2 (Write), 1 (Execute). 755 = rwxr-xr-x.
*   **Special:** `s` (SUID), `t` (Sticky Bit).

### 2. CLI Text Manipulation
*   `grep`, `tr`, `sed`, `awk`, `sort`, `uniq`.

### 3. Privilege Escalation (Case Study)
*   Identifying weaknesses via `sudo -l`. Lesson: Attention to detail is vital!

---

## 💻 Part 4: Web Vulnerabilities (OWASP Top 10)

### 1. What is OWASP?
*   A world-recognized list explaining the **10 most common security problems** found in web applications.

### 2. Official Ranking (2021 Version)
1. Broken Access Control, 2. Cryptographic Failures, 3. Injection, 4. Insecure Design, 5. Security Misconfiguration, 6. Vulnerable and Outdated Components, 7. Identification and Authentication Failures, 8. Software and Data Integrity Failures, 9. Security Logging and Monitoring Failures, 10. SSRF.

---

## 🏭 Part 5: Industrial Control Systems (OT/ICS)
*   **IT vs. OT:** IT prioritizes **Confidentiality** (C), while OT prioritizes **Availability** (A) and Physical Safety.
*   **Architecture:** PLC (Controllers), SCADA (Monitoring), HMI (Screens).
*   **Concepts:** Purdue Model (Segmentation), Air-Gapping.

---
*Last update: February 26, 2026. Consolidated document for Irinel Lazarovici.*
