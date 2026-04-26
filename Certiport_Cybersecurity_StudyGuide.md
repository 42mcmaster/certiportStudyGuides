# Certiport ITS Cybersecurity — Student Study Guide

A self-paced review for the Certiport / GMetrix Information Technology Specialist (ITS) Cybersecurity certification exam.

---

## How to Use This Guide

This guide is structured as **fourteen short modules**, building from the foundational CIA triad up through attacks, network defenses, incident response, forensics, and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

### What This Exam Tests Most Heavily

Across the practice exam (50 questions), the heaviest weight is on:

- **The CIA triad** — confidentiality, integrity, availability — and which pillar a given scenario violates.
- **Attack types** — SQL injection, XSS, CSRF, the spoofing family (ARP / MAC / IP / DNS / DHCP), DoS / DDoS, phishing.
- **Multi-factor authentication** — the three factors and which combinations qualify as true MFA.
- **Incident response lifecycle** — the NIST four phases and their order.
- **Network defenses** — firewalls, segmentation, wireless protocols, security tools (Nessus, Wireshark, Metasploit, Nmap).

Lighter but reliable: compliance frameworks, digital forensics ordering, syslog and Windows event types, command-line tools.

---

## Table of Contents

1. [The CIA Triad and Core Security Concepts](#module-1--the-cia-triad-and-core-security-concepts)
2. [Risk Management Strategies](#module-2--risk-management-strategies)
3. [Attacks: Web, Network, and Spoofing](#module-3--attacks-web-network-and-spoofing)
4. [Malware Types and Privilege Escalation](#module-4--malware-types-and-privilege-escalation)
5. [Reconnaissance, Pen Testing, and Vulnerability Frameworks](#module-5--reconnaissance-pen-testing-and-vulnerability-frameworks)
6. [Compliance Frameworks](#module-6--compliance-frameworks)
7. [Network Defenses: Segmentation, Firewalls, Wireless](#module-7--network-defenses-segmentation-firewalls-wireless)
8. [Encryption and Authentication (MFA)](#module-8--encryption-and-authentication-mfa)
9. [Incident Response and Continuity Plans](#module-9--incident-response-and-continuity-plans)
10. [SIEM, SOAR, and Security Automation](#module-10--siem-soar-and-security-automation)
11. [Digital Forensics, Logs, and Command-Line Tools](#module-11--digital-forensics-logs-and-command-line-tools)
12. [Anti-Malware, Insider Threats, and AI-Driven Threats](#module-12--anti-malware-insider-threats-and-ai-driven-threats)
13. [Mobile, QR, BYOD Hygiene, and Defense-in-Depth](#module-13--mobile-qr-byod-hygiene-and-defense-in-depth)
14. [Test-Taking Strategy and Final Review](#module-14--test-taking-strategy-and-final-review)
15. [Exam-Day Cheat Card](#exam-day-cheat-card)
16. [Master Glossary](#master-glossary)

---

## Module 1 — The CIA Triad and Core Security Concepts

### Concept

The CIA triad is the foundation of every cybersecurity decision. The exam asks again and again: *"Which pillar was violated?"* Train yourself to answer the diagnostic question — **what happened to the data: was it seen, changed, or made unreachable?**

### Anchor: The Triad

```
        CONFIDENTIALITY
        (only authorized
         people can SEE it)
              ╱╲
             ╱  ╲
            ╱    ╲
   INTEGRITY ─── AVAILABILITY
   (data is unaltered,    (authorized users CAN
    not tampered with)     access it when needed)
```

| Pillar               | Violated When…                                                  | Common Examples                              |
| -------------------- | --------------------------------------------------------------- | -------------------------------------------- |
| **Confidentiality**  | Sensitive data is **stolen or exposed**                         | Data breach, leaked credentials, eavesdropping |
| **Integrity**        | Data is **tampered with** or modified                           | Defaced website, altered records, supply-chain malware |
| **Availability**     | Data or services are **unreachable**                            | DoS / DDoS attack, ransomware lockout, outage |

### Anchor: The Diagnostic Question

```
    What happened to the data / service?
                  │
   ┌──────────────┼──────────────┐
   ▼              ▼              ▼
  SEEN          CHANGED       UNREACHABLE
   │              │              │
   ▼              ▼              ▼
CONFIDENTIALITY INTEGRITY     AVAILABILITY
```

### Self-Check

> An attacker uses a phishing email to steal employee passwords and read confidential client documents. Which pillar of the CIA triad is **most directly** violated?
> A) Confidentiality
> B) Integrity
> C) Availability
> D) Non-repudiation

**Answer:** A.
**Why the others are wrong:** B would be if the attacker *changed* the documents. C would be if the documents were made unreachable. D isn't part of the CIA triad.

> A ransomware infection encrypts a hospital's patient files until a ransom is paid. Which pillar is **most directly** violated?
> A) Confidentiality
> B) Integrity
> C) Availability
> D) Authentication

**Answer:** C. The data isn't readable until the ransom is paid — it's unavailable to authorized users.

---

## Module 2 — Risk Management Strategies

### Concept

When risk is identified, an organization picks one of four core strategies. The exam tests whether you can read a scenario and label which strategy is being used.

### Anchor: The Four Strategies

| Strategy                     | What It Means                                              | Example                                                  |
| ---------------------------- | ---------------------------------------------------------- | -------------------------------------------------------- |
| **Risk Acceptance**          | Acknowledge the risk and **do nothing** about it           | "We'll live with the chance of this minor outage."       |
| **Risk Avoidance**           | **Eliminate** the risk by removing the activity            | Move offices out of a flood zone; stop offering a feature |
| **Risk Transfer**            | **Shift** risk to a third party                            | Buy cyber-insurance; outsource processing to a vendor    |
| **Risk Control / Mitigation**| Implement controls to **reduce** likelihood or impact      | Add MFA; encrypt data; train staff                       |

### Anchor: Related Disciplines

| Discipline                  | Focus                                                                   |
| --------------------------- | ----------------------------------------------------------------------- |
| **Vulnerability management**| Proactively identify and remediate weaknesses **before** exploitation   |
| **Risk management**         | Identify and mitigate threats broadly                                   |
| **Asset management**        | Inventory and maintain hardware and software assets                     |
| **Configuration management**| Keep system configurations consistent across the environment            |

### Self-Check

> A company stops storing customer credit-card numbers locally and instead lets a payment processor handle them entirely. Which risk strategy is this?
> A) Risk Acceptance
> B) Risk Avoidance
> C) Risk Transfer
> D) Risk Control

**Answer:** C. The card-handling risk is shifted to the third-party processor.

> A company decides the chance of a particular minor incident is low and they're willing to absorb the cost if it happens. Which strategy?
> A) Risk Acceptance
> B) Risk Avoidance
> C) Risk Transfer
> D) Risk Control

**Answer:** A.

---

## Module 3 — Attacks: Web, Network, and Spoofing

### Concept

The exam expects you to recognize each attack type from a one-line scenario. Most distractor traps cluster within the **spoofing family** (ARP / MAC / IP / DNS / DHCP) — drill those carefully.

### Anchor: Web-Application Attacks

| Attack                              | What It Does                                                                       |
| ----------------------------------- | ---------------------------------------------------------------------------------- |
| **SQL Injection (SQLi)**            | Malicious SQL placed in a form field to query or exfiltrate the backend database  |
| **Cross-Site Scripting (XSS)**      | Injects **client-side scripts** into web pages viewed by other users               |
| **Cross-Site Request Forgery (CSRF)** | Forces an authenticated user to execute unwanted actions on a web app             |
| **Buffer Overflow**                 | Writes more data than allocated memory can hold; can let attackers run arbitrary code |

### Anchor: Network Floods and Recon

| Attack             | What It Does                                                                  |
| ------------------ | ----------------------------------------------------------------------------- |
| **DoS / DDoS**     | Floods a target with traffic to deny service                                  |
| **DNS Amplification** | Abuses open DNS resolvers to flood a target with responses                  |
| **Port Scanning**  | Probes for open / closed ports to find attack surface                         |
| **Phishing**       | Fraudulent email used to harvest credentials or deliver malware               |

### Anchor: The Spoofing Family

```
ARP Spoofing   →  attacker associates THEIR MAC with a LEGITIMATE IP on the LAN
                  (intercepts traffic intended for someone else)

MAC Spoofing   →  attacker sends frames with a LEGITIMATE host's MAC
                  (impersonates that host)

IP Spoofing    →  packets sent with FALSIFIED source IPs
                  (impersonate another system on the network)

DNS Spoofing   →  alters DNS records so a domain resolves to a FRAUDULENT site

DHCP Spoofing  →  fake DHCP server hands out bad IP / gateway / DNS info

DHCP Starvation → flood DHCP server with requests until address pool is EXHAUSTED
```

The two students confuse most are **ARP** and **MAC** spoofing. The trick:

- **ARP** spoofing: attacker says "**I** am that IP." (Their MAC is mapped to someone else's IP.)
- **MAC** spoofing: attacker says "I **am** that host." (They take on someone else's MAC.)

### Self-Check

> An attacker types `' OR 1=1 --` into a website's search box and the underlying database returns every row. Which attack is this?
> A) Cross-Site Scripting
> B) SQL Injection
> C) Buffer Overflow
> D) DNS Spoofing

**Answer:** B.

> An attacker on a coffee-shop Wi-Fi sends frames that map their MAC address to the gateway's IP, causing nearby laptops to send traffic through the attacker. Which attack is this?
> A) MAC Spoofing
> B) ARP Spoofing
> C) IP Spoofing
> D) DNS Spoofing

**Answer:** B. The attacker's **MAC** is being mapped to a legitimate **IP** — that's ARP poisoning.

---

## Module 4 — Malware Types and Privilege Escalation

### Concept

The exam asks you to match a description to a malware type, and to recognize the platform-specific terms for privilege escalation.

### Anchor: The Malware Family

| Type           | One-Line Definition                                                  |
| -------------- | -------------------------------------------------------------------- |
| **Virus**      | Code that **attaches to host files**; needs user action to spread     |
| **Worm**       | Self-replicating malware that propagates **across networks**          |
| **Trojan**     | Malware **disguised** as legitimate software                          |
| **Spyware**    | Secretly gathers data and sends it back to the attacker               |
| **Rootkit**    | Toolset granting **admin / root-level** remote access                 |
| **Keylogger**  | Records keystrokes                                                    |
| **Backdoor**   | Hidden access path (not necessarily admin-level)                      |
| **Ransomware** | Encrypts data and demands payment                                     |

The exam's tell for **rootkit**: the question mentions "admin-level," "root access," or "collection of tools."

### Anchor: Privilege Escalation Vocabulary

| Term            | What It Means                                              |
| --------------- | ---------------------------------------------------------- |
| **Jailbreaking**| Bypassing user-account restrictions on **iOS**             |
| **Rooting**     | Gaining root privileges on **Android**                     |
| **Cracking**    | Generic term for breaching software / systems              |
| **Trespassing** | Intentionally accessing unauthorized resources             |

### Self-Check

> Which type of malware is best described as a toolset that grants **administrator-level** remote access to a compromised system?
> A) Spyware
> B) Worm
> C) Rootkit
> D) Keylogger

**Answer:** C.

> A user installs what they think is a free game; in reality it also installs a remote-access program. The "free game" is a:
> A) Worm
> B) Trojan
> C) Virus
> D) Ransomware

**Answer:** B. Disguised as legitimate software → Trojan.

---

## Module 5 — Reconnaissance, Pen Testing, and Vulnerability Frameworks

### Concept

Before any successful attack, there's reconnaissance. Defensive teams use the same techniques to find weaknesses first. The exam tests both the *activities* (active recon, pen testing, kill chain) and the *catalogs / frameworks* (CVE, ATT&CK, CVSS, STIX).

### Anchor: Activities

| Term                        | What It Is                                                                       |
| --------------------------- | -------------------------------------------------------------------------------- |
| **Active reconnaissance**   | Scanning systems to identify exploitable vulnerabilities (precedes exploitation) |
| **Penetration testing**     | Locating potential vulnerabilities by **simulating attacks**                     |
| **Kill chain**              | Sequenced steps of a cyberattack: recon → weaponize → deliver → exploit → install → command-and-control → actions on objectives |
| **Vulnerability databases** | Repositories of known weaknesses (the *catalog*, not the act of testing)         |

### Anchor: The Big Frameworks (and Who Owns Them)

| Framework / Catalog | What It Is                                                              | Maintained By              |
| ------------------- | ----------------------------------------------------------------------- | -------------------------- |
| **CVE**             | Dictionary of publicly known vulnerabilities                            | **MITRE Corporation**      |
| **MITRE ATT&CK**    | Framework of tactics and techniques used by threat actors               | MITRE Corporation          |
| **CVSS**            | Risk-scoring system for vulnerabilities (0.0 – 10.0)                    | **FIRST**                  |
| **CybOX**           | Schema supporting cybersecurity functions                               | (Open standard)            |
| **STIX**            | Structured threat intelligence language                                 | (Open standard)            |
| **TAXII**           | Protocol that **transports STIX** data                                  | (Open standard)            |

Memorize: **MITRE owns CVE; FIRST owns CVSS.**

### Self-Check

> Who maintains the CVE list of publicly known vulnerabilities?
> A) FIRST
> B) MITRE Corporation
> C) NIST
> D) ISO

**Answer:** B.

> Which framework provides a standard **scoring system** (0.0–10.0) for the severity of a vulnerability?
> A) CVE
> B) ATT&CK
> C) CVSS
> D) STIX

**Answer:** C.

---

## Module 6 — Compliance Frameworks

### Concept

A small but reliable cluster of questions tests whether you can match a scenario to the right regulation. The diagnostic is "**what kind of data, and where are the customers?**"

### Anchor: Regulations by Data Domain

| Framework    | Domain                                                                  | Region          |
| ------------ | ----------------------------------------------------------------------- | --------------- |
| **PCI-DSS**  | Credit-card data — any merchant that processes cards                    | International   |
| **HIPAA**    | Healthcare patient data                                                 | United States   |
| **GDPR**     | Personal data of **EU citizens**                                        | European Union  |
| **SOX**      | Financial reporting controls for **publicly traded companies**          | United States   |
| **FERPA**    | Student educational records                                             | United States   |

A common trap: confusing **PCI-DSS** (credit cards) with **SOX** (financial reporting). PCI-DSS applies to *any* merchant taking cards; SOX applies to *public-company financial statements*.

### Self-Check

> A US-based hospital must protect electronic patient records. Which regulation applies most directly?
> A) PCI-DSS
> B) HIPAA
> C) GDPR
> D) FERPA

**Answer:** B.

> An e-commerce company in California sells to customers in Berlin and Madrid. Which regulation governs the personal data of those EU customers?
> A) HIPAA
> B) SOX
> C) GDPR
> D) FERPA

**Answer:** C.

---

## Module 7 — Network Defenses: Segmentation, Firewalls, Wireless

### Concept

This module groups three reliable question types: when to use **segmentation**, the differences among **firewall types**, and the **strength order** of wireless protocols.

### Anchor: Network Segmentation

Segmentation divides the network into logical groups to control which systems can reach which resources. It's **architectural**, not a monitoring tool.

- Limits **lateral movement** by attackers.
- Protects sensitive systems behind tighter access rules.
- Reduces unnecessary east-west traffic.

### Anchor: Firewall Types

| Type                              | Behavior                                                                                              | Best For                                       |
| --------------------------------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| **Stateless firewall**            | Examines each packet independently; no memory of connections                                          | Simple, fast packet filtering                  |
| **Stateful firewall**             | Remembers established connection parameters; more context-aware                                       | Standard network perimeter                     |
| **Next-Generation Firewall (NGFW)** | Adds application-level filtering and deep packet inspection                                         | Modern enterprise perimeter                    |
| **Host-based firewall**           | Installed on a single device; protects it from unwanted access / malware                              | When malware may have **already breached** the perimeter |

### Anchor: Wireless Security — Strength Order

```
WEP    <    WPA2-PSK    <    WPA2-Enterprise    <    WPA3
weak,        home              uses RADIUS              strongest
broken       pre-shared         authentication          current
             key                server                  encryption
```

| Control / Protocol     | What It Does                                                          |
| ---------------------- | --------------------------------------------------------------------- |
| **WEP**                | Legacy, broken — avoid                                                |
| **WPA2-PSK**           | Pre-shared key (typical home networks)                                |
| **WPA2-Enterprise**    | Uses a **RADIUS** server for per-user authentication                  |
| **WPA3**               | Strongest current Wi-Fi encryption                                    |
| **MAC filtering**      | Allow / deny by device MAC; doesn't encrypt traffic                   |
| **SSID cloaking**      | Disables broadcast; clients must manually configure SSID              |

Memory aid: "Strongest encryption" → **WPA3**. "Only my devices may connect" → **MAC filtering**.

### Self-Check

> A small company already has perimeter firewalls but is concerned that a phishing-delivered worm could spread laptop-to-laptop once inside. Which control most directly limits that lateral movement?
> A) Adding more antivirus updates
> B) Network segmentation
> C) Hiding the SSID
> D) Replacing WEP with WPA3

**Answer:** B.

> Which wireless control provides the **strongest current encryption** for traffic on a corporate Wi-Fi network?
> A) WEP
> B) WPA2-PSK
> C) WPA3
> D) MAC filtering

**Answer:** C.

---

## Module 8 — Encryption and Authentication (MFA)

### Concept

Two foundational defenses share this module: how data is encrypted (symmetric vs. asymmetric vs. hashing) and how identity is verified (the three MFA factors).

### Anchor: Encryption Categories

| Category         | Key Model                                                       | Examples              |
| ---------------- | --------------------------------------------------------------- | --------------------- |
| **Symmetric**    | **Same** pre-shared key for encrypt and decrypt                 | AES, DES, 3DES        |
| **Asymmetric**   | **Public / private key pair**, dynamically exchanged            | RSA, ECC              |
| **Hashing**      | One-way; **not encryption** — used for integrity, not confidentiality | SHA-256, MD5     |

A common trap: hashing is *not* encryption. You can't recover the original data from a hash.

### Anchor: The Three Authentication Factors

```
1. SOMETHING YOU KNOW   →  password, PIN, security question
2. SOMETHING YOU HAVE   →  token, badge, phone (one-time code)
3. SOMETHING YOU ARE    →  biometric (fingerprint, face, eye)
```

**True MFA = at least two *different* factor categories.**

| Combination                              | True MFA?                            |
| ---------------------------------------- | ------------------------------------ |
| Username + password                      | ❌ Both are "know"                   |
| Eye scan + fingerprint                   | ❌ Both are "are"                    |
| Username + one-time code from phone      | ✅ Know + Have                       |
| Username + fingerprint                   | ✅ Know + Are                        |
| Badge + fingerprint                      | ✅ Have + Are                        |

### Self-Check

> Which combination is **true** multi-factor authentication?
> A) Username + password
> B) Password + PIN
> C) Password + one-time code sent to your phone
> D) Fingerprint + retina scan

**Answer:** C. Password is "know"; phone code is "have" — two different categories.

> Which is **not** considered encryption?
> A) AES
> B) RSA
> C) SHA-256 hashing
> D) ECC

**Answer:** C. Hashing is one-way; it provides integrity, not confidentiality.

---

## Module 9 — Incident Response and Continuity Plans

### Concept

When something goes wrong, there's a defined sequence to follow. The exam tests **two related distinctions**: the four phases of the NIST incident-response lifecycle, and the difference between an Incident Response Plan, a Business Continuity Plan, and a Disaster Recovery Plan.

### Anchor: The NIST SP 800-86 Lifecycle (in order)

```
1. PREPARATION
   Build the IR team, gather tools, define communications.

2. DETECTION & ANALYSIS
   Determine whether an incident has occurred. Investigate IDS / IPS alerts.

3. CONTAINMENT, ERADICATION & RECOVERY
   Stop the bleeding, remove the malicious activity, restore systems.

4. POST-INCIDENT ACTIVITY
   Document what happened. Capture lessons learned. Update procedures.
```

The exam loves "what comes first?" and "which phase is this activity?" questions. **Preparation always comes first.** Updating procedures and writing a final report is **post-incident**.

### Anchor: Three Plans — Different Scopes

| Plan                                | Scope                                                        | Focus                          |
| ----------------------------------- | ------------------------------------------------------------ | ------------------------------ |
| **Incident Response Plan (IRP)**    | A single security incident                                   | How employees handle it        |
| **Business Continuity Plan (BCP)**  | The **whole business** during/after a disruption             | Keeping critical functions running |
| **Disaster Recovery Plan (DRP)**    | **IT systems and data** restoration                          | Servers, networks, backups     |

Memory aid: **IRP = one event, BCP = whole business, DRP = the IT systems.**

### Self-Check

> A company finishes responding to a phishing-related breach. The team writes a report and updates training. Which incident-response phase is this?
> A) Preparation
> B) Detection and Analysis
> C) Containment, Eradication, and Recovery
> D) Post-Incident Activity

**Answer:** D.

> Which plan most directly addresses **how a company keeps critical business functions running** during a multi-day outage?
> A) Incident Response Plan
> B) Business Continuity Plan
> C) Disaster Recovery Plan
> D) Acceptable Use Policy

**Answer:** B. BCP is broader than DRP; DRP is the IT-restoration subset.

---

## Module 10 — SIEM, SOAR, and Security Automation

### Concept

Two related but distinct technologies appear together on the exam. **SIEM** aggregates and analyzes; **SOAR** automates response.

### Anchor: SIEM vs. SOAR

| System                                                              | What It Does                                                                                  | Use When…                                                                  |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **SIEM** (Security Information and Event Management)                | **Aggregates and analyzes log data** from across the environment; generates alerts for human investigation | You need centralized visibility and correlation                            |
| **SOAR** (Security Orchestration, Automation, and Response)         | **Automates** incident response steps to reduce human intervention                            | You want to cut detection / response time automatically (e.g., a phishing surge) |

### Anchor: Other Automation Tools

| Tool             | Purpose                                                                              |
| ---------------- | ------------------------------------------------------------------------------------ |
| **SCAP**         | Open standard for automating vulnerability and policy compliance evaluation          |
| **PowerShell**   | General scripting and automation framework on Windows (not security-specific)        |

### Self-Check

> A company's SOC is overwhelmed by repetitive phishing-email investigations. Which technology most directly **automates** the triage steps to free up analysts?
> A) SIEM
> B) SOAR
> C) NGFW
> D) WPA3

**Answer:** B.

> Which technology primarily **aggregates and correlates logs** from many sources to surface alerts for human analysts?
> A) SIEM
> B) SOAR
> C) SCAP
> D) Wireshark

**Answer:** A.

---

## Module 11 — Digital Forensics, Logs, and Command-Line Tools

### Concept

The forensics module has three reliable question types: the **order of volatility** when collecting evidence, the **types of Windows event-log entries**, and the use of **command-line tools** to investigate a system.

### Anchor: Order of Volatility (Most → Least)

```
1. RAM            (most volatile — disappears on power-off)
2. Fixed Disk     (less volatile)
3. Archived Backup (least volatile)
```

Principle: **capture what disappears first.** If you reboot before grabbing RAM, you lose all process state.

### Anchor: Windows Event-Log Types

| Type                | Means…                                                              | Example                                  |
| ------------------- | ------------------------------------------------------------------- | ---------------------------------------- |
| **Information**     | Successful operation of an application, driver, or service          | "Driver loaded successfully"             |
| **Warning**         | Not necessarily significant but **may indicate a future problem**   | "Low disk space"                         |
| **Error**           | Significant problem — loss of data or function                      | "Service failed to load"                 |
| **Success Audit**   | An audited security access **succeeded**                            | "Logon successful for user X"            |
| **Failure Audit**   | An audited security access **failed**                               | "Logon failed for user X"                |

### Anchor: Syslog Message Structure

A syslog message has three parts:

```
PRI  |  HEADER  |  MSG
 │       │         │
 │       │         └── the message content
 │       └── timestamp + HOSTNAME (origin device)
 └── priority value (encodes facility + severity)
```

- **Severity** — importance of the message.
- **Facility** — application or OS component that generated it.
- **Hostname** (in HEADER) answers "Where did the event come from?"

### Anchor: Command-Line Tools

| Command           | What It Does                                                                                        |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| **`netstat -a`**  | List all active TCP connections                                                                     |
| **`netstat -o`**  | List connections **with the owning process / application** — use to track suspicious app traffic   |
| **`netstat -e`**  | Ethernet statistics                                                                                 |
| **`nslookup`**    | Query DNS; map domain names to IP addresses (used in reconnaissance)                                |
| **`ipconfig /all`** | View full local IP configuration on Windows                                                       |
| **`tracert`**     | Show router hops between source and destination                                                     |
| **`ping`**        | Test reachability and latency                                                                       |

`netstat` works for **TCP / UDP over both IPv4 and IPv6**.

### Self-Check

> A forensic analyst is about to investigate a possibly compromised laptop. In which order should the analyst collect evidence?
> A) Backup → Disk → RAM
> B) Disk → RAM → Backup
> C) RAM → Disk → Backup
> D) RAM → Backup → Disk

**Answer:** C. Most volatile first.

> Which command lists active TCP connections **along with the process that owns each one**?
> A) `netstat -a`
> B) `netstat -e`
> C) `netstat -o`
> D) `ipconfig /all`

**Answer:** C.

---

## Module 12 — Anti-Malware, Insider Threats, and AI-Driven Threats

### Concept

This module groups the human and AI side of cybersecurity: how anti-malware systems work, how insiders go bad, and how AI tools are weaponized.

### Anchor: Anti-Malware Operations

| Operation              | What It Does                                                                                  |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| **Quarantine**         | Isolate an infected file so it can't execute or spread                                        |
| **Sandboxing**         | Run a program in an isolated environment to **observe behavior** (not specifically removal)  |
| **Definition updates** | Keep antivirus signatures current to detect known threats                                     |
| **Windows Update / Recovery** | OS maintenance — **not** malware removal                                                |

### Anchor: Insider Threat Types

| Type                  | Intent                  | Example                                                          |
| --------------------- | ----------------------- | ---------------------------------------------------------------- |
| **Malicious insider** | **Intentional** harm    | Employee steals trade secrets to sell                            |
| **Negligent insider** | **Unintentional** harm  | Employee takes a drive home without permission; it's stolen      |
| **Compromised insider** | Account taken over    | Attacker phishes a manager's credentials and uses their account  |

### Anchor: Attack Vectors and Threat Actors

| Term                       | Definition                                                            |
| -------------------------- | --------------------------------------------------------------------- |
| **Attack vector**          | The **pathway / method** used to access a system illegally (email, USB, web app, supply chain) |
| **Botnet**                 | Network of compromised devices controlled by a threat actor            |
| **Cryptographic attack**   | Attempts to break encryption or compromise keys                        |

### Anchor: AI-Driven Threats (Emerging)

| Threat                  | Description                                                                                          |
| ----------------------- | ---------------------------------------------------------------------------------------------------- |
| **Bots / chatbots**     | Can be weaponized to socially engineer employees over messaging platforms using gathered info       |
| **Generative AI**       | Produces text / images from inputs; misused for convincing phishing and disinformation               |
| **Models**              | Trained pattern recognizers; can be poisoned or manipulated                                           |

The takeaway for users: any "human" on a messaging platform could be a coercive bot. Verify out-of-band before acting on unusual requests.

### Self-Check

> An employee plugs an unauthorized USB drive into a work laptop to copy files for a weekend project. The drive is later stolen from their car. Which insider type is this?
> A) Malicious insider
> B) Negligent insider
> C) Compromised insider
> D) External attacker

**Answer:** B. No malicious intent, but careless behavior caused the breach.

> Running a suspicious executable inside an isolated VM to **watch what it does** is best described as:
> A) Quarantining
> B) Sandboxing
> C) Patching
> D) Deleting

**Answer:** B.

---

## Module 13 — Mobile, QR, BYOD Hygiene, and Defense-in-Depth

### Concept

The closing concept module covers physical-meets-digital risks (mobile devices, QR codes, BYOD) and the principle of **defense-in-depth** — layering controls so a single failure doesn't sink you.

### Anchor: Mobile and Smart-Device Risks

| Risk                          | Note                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------ |
| **Hijacked QR codes**         | Malicious actors swap or overlay QR codes to redirect users to malicious sites             |
| **App permissions**           | Minimize what each app can access — apply least-privilege to mobile                        |
| **Lost-device controls**      | Encryption, remote wipe, screen locks                                                      |

The phone's camera itself isn't the threat; the **redirect** to a fake site is.

### Anchor: Visitor / BYOD Hygiene

Before letting an outside device on your network:

- Verify **up-to-date antivirus / anti-malware** definitions and a recent scan.
- Ensure your sensitive systems are on a **separate (private / segmented) network**.
- Confirm the OS is **patched** (a patched OS is safer than an unpatched one with VPN).
- Inspect for known-vulnerable software (outdated browsers = high risk).

### Anchor: Defense-in-Depth Mitigations by Threat

| Threat                    | Mitigations                                                                            |
| ------------------------- | -------------------------------------------------------------------------------------- |
| **DoS / DDoS**            | Firewall rate-limiting, IPS to block suspicious flows. (MFA and AV updates do **not** stop DoS.) |
| **Phishing**              | SOAR automation, email filtering, user training, MFA                                   |
| **SQL Injection**         | Input validation, parameterized queries                                                |
| **Malware past the perimeter** | Host-based firewall + endpoint AV on the device                                   |

### Self-Check

> A coffee shop offers free Wi-Fi. To safely host customers without exposing the back-office systems, the shop should:
> A) Hide the SSID and rely on it
> B) Put guest Wi-Fi on a separate, segmented network from staff systems
> C) Disable encryption to make guest setup easier
> D) Use WEP for backward compatibility

**Answer:** B.

> Which is the **best** mitigation for SQL injection in a custom web app?
> A) Adding MFA to user logins
> B) Input validation and parameterized queries
> C) Replacing the firewall with an NGFW
> D) Enabling Windows Defender on the server

**Answer:** B. SQLi is fixed at the application layer.

---

## Module 14 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### Reading Scenario Questions Under Time Pressure

When a long scenario appears, before reading the answer choices:

1. **Identify the topic cluster** — CIA, attack type, MFA, IR phase, compliance, forensics.
2. **Spot the keywords** — "encrypted until ransom," "EU customers," "credit cards," "tracks back to a process," "admin-level access."
3. **Translate the scenario into a vocabulary question** — most "scenario" questions are vocabulary in disguise.

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"Was data seen, changed, or made unreachable?" — that's the CIA pillar.*
- *"ARP says I am that IP; MAC says I am that host."*
- *"True MFA needs two different factor categories."*
- *"Preparation, Detection, Containment, Post-Incident — in that order."*
- *"Volatility: RAM → Disk → Backup."*
- *"MITRE owns CVE; FIRST owns CVSS."*

### Mock Quiz (12 Questions Across the Whole Exam)

Try these timed — about 75 seconds per question.

1. A ransomware attack encrypts a hospital's records until paid. Which CIA pillar is most directly violated?
2. A company buys cyber-insurance. Which risk strategy is this?
3. An attacker maps their MAC to the gateway's IP on a LAN. Which attack?
4. Which malware type is described as a "toolset granting admin-level remote access"?
5. Who maintains the CVE list?
6. A US-based hospital electronically stores patient records. Which regulation applies?
7. Which Wi-Fi protocol provides the strongest current encryption?
8. Which combination is true MFA — password + PIN, or password + one-time code from a phone?
9. Which is the **first** phase of the NIST IR lifecycle?
10. Which technology automates incident-response steps to reduce human triage time — SIEM or SOAR?
11. In what order should a forensic analyst collect evidence — RAM, Disk, Backup?
12. Which `netstat` flag shows the **owning process** for each connection?

#### Answer Key (cover until done)

1. **Availability** — Module 1.
2. **Risk transfer** — Module 2.
3. **ARP spoofing** — Module 3.
4. **Rootkit** — Module 4.
5. **MITRE Corporation** — Module 5.
6. **HIPAA** — Module 6.
7. **WPA3** — Module 7.
8. **Password + one-time code from phone** (know + have) — Module 8.
9. **Preparation** — Module 9.
10. **SOAR** — Module 10.
11. **RAM → Disk → Backup** — Module 11.
12. **`-o`** — Module 11.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> The CIA triad is **Confidentiality** (data is seen by unauthorized people = violation), **Integrity** (data is changed = violation), **Availability** (data/services are unreachable = violation). Risk strategies: **accept** (do nothing), **avoid** (eliminate the activity), **transfer** (insurance / outsourcing), **control** (mitigate with controls). Web attacks: **SQL injection** (malicious SQL in form fields), **XSS** (client-side script injection), **CSRF** (forces an authenticated user to act), **buffer overflow** (overrun memory). Network: **DoS / DDoS**, **DNS amplification**, **port scanning**, **phishing**. Spoofing family: **ARP** maps attacker's MAC to legitimate IP; **MAC** impersonates someone's host; **IP** falsifies source IP; **DNS** redirects domain to fraudulent site; **DHCP spoofing** is a fake DHCP server; **DHCP starvation** exhausts the address pool. Malware: **virus** attaches to files, **worm** propagates across networks, **trojan** disguises itself, **spyware** exfiltrates, **rootkit** = admin-level toolset, **keylogger** records keys, **backdoor** is a hidden access path, **ransomware** encrypts and demands payment. **Jailbreak** = iOS, **root** = Android. **MITRE** owns CVE and ATT&CK; **FIRST** owns CVSS; **STIX** is the language, **TAXII** is the transport. Compliance: **PCI-DSS** for credit cards, **HIPAA** for US healthcare, **GDPR** for EU citizens, **SOX** for US public-company financials, **FERPA** for US student records. **Network segmentation** limits lateral movement. Firewalls: **stateless** vs. **stateful** vs. **NGFW** (deep packet inspection) vs. **host-based** (when malware may be inside). Wi-Fi strength: **WEP < WPA2-PSK < WPA2-Enterprise (RADIUS) < WPA3**. **MAC filtering** restricts by device; **SSID cloaking** hides broadcast. Encryption: **symmetric** (AES, DES, 3DES) shares one key; **asymmetric** (RSA, ECC) uses public/private pair; **hashing** (SHA, MD5) is one-way and not encryption. MFA factors: **know** (password / PIN), **have** (token / phone code / badge), **are** (biometric). True MFA needs at least two **different** categories. NIST IR phases: **Preparation → Detection & Analysis → Containment, Eradication & Recovery → Post-Incident Activity**. **IRP** = one event; **BCP** = whole business; **DRP** = IT restoration. **SIEM** aggregates and correlates logs; **SOAR** automates response. **SCAP** standardizes compliance evaluation. Forensics order of volatility: **RAM → Fixed Disk → Archived Backup**. Windows log types: **Information**, **Warning**, **Error**, **Success Audit**, **Failure Audit**. Syslog: **PRI / HEADER (with hostname) / MSG**. Commands: `netstat -a` lists connections, `-o` adds owning process, `-e` Ethernet stats; `nslookup` queries DNS; `ipconfig /all` shows IP config; `tracert` shows hops; `ping` tests reachability. Anti-malware: **quarantine** isolates, **sandboxing** observes behavior, **definition updates** keep AV current. Insider threats: **malicious** (intent), **negligent** (carelessness), **compromised** (account takeover). AI threats: chatbots used for social engineering, generative AI for phishing, models can be poisoned. Hijacked QR codes redirect to fraud sites. BYOD hygiene: AV updated, segmented network, patched OS. Defense-in-depth: stop DoS at the firewall/IPS, stop phishing with SOAR + filtering + training + MFA, stop SQLi with input validation and parameterized queries, stop in-network malware with host firewall + endpoint AV.

---

## Master Glossary

**ARP Spoofing** — attacker associates **their MAC** with a **legitimate IP** on a LAN, intercepting traffic.

**Asset Management** — inventorying and maintaining hardware and software assets.

**Asymmetric Encryption** — uses a public/private key pair (RSA, ECC).

**Attack Vector** — pathway / method used to access a system illegally (email, USB, web, etc.).

**Availability** — CIA pillar: authorized users can access information/services when needed.

**Backdoor** — hidden access path to a system; not necessarily admin-level.

**Botnet** — network of compromised devices controlled by a threat actor.

**Buffer Overflow** — writing more data than allocated memory can hold.

**Business Continuity Plan (BCP)** — broad plan for keeping critical business functions running during/after a disruption.

**CIA Triad** — Confidentiality, Integrity, Availability — the foundation of information security.

**Compromised Insider** — internal account taken over by an external attacker.

**Confidentiality** — CIA pillar: sensitive information is available only to authorized people.

**Configuration Management** — keeping system configurations consistent across an environment.

**CVE (Common Vulnerabilities and Exposures)** — dictionary of publicly known vulnerabilities (maintained by MITRE).

**CVSS (Common Vulnerability Scoring System)** — vulnerability severity scoring (maintained by FIRST).

**CSRF (Cross-Site Request Forgery)** — forces an authenticated user to execute unwanted actions.

**Cryptographic Attack** — attempts to break encryption or compromise keys.

**DDoS / DoS** — denial-of-service attack: flood a target to make it unreachable.

**Definition Updates** — keeping antivirus signatures current.

**DHCP Spoofing** — fake DHCP server hands out bad IP / gateway / DNS info.

**DHCP Starvation** — flooding a DHCP server until its IP pool is exhausted.

**Disaster Recovery Plan (DRP)** — IT-focused plan to restore systems and data after a disaster.

**DNS Amplification** — abuses open DNS resolvers to flood a target with responses.

**DNS Spoofing** — alters DNS records so a domain resolves to a fraudulent site.

**FERPA** — US law protecting student educational records.

**FIRST** — organization that maintains CVSS.

**GDPR** — EU privacy regulation governing personal data of EU citizens.

**Hashing** — one-way transformation; provides integrity, not confidentiality.

**HIPAA** — US law protecting healthcare patient data.

**Host-Based Firewall** — firewall installed on an individual device.

**Incident Response Plan (IRP)** — narrow plan for handling individual security incidents.

**Information / Warning / Error / Audit Success / Audit Failure** — Windows event-log types.

**Integrity** — CIA pillar: data is unaltered.

**IP Spoofing** — packets sent with falsified source IPs.

**Jailbreaking** — bypassing user-account restrictions on iOS.

**Keylogger** — records keystrokes.

**Kill Chain** — sequenced steps of a cyberattack from reconnaissance through actions on objectives.

**MAC Filtering** — allow/deny network access by device MAC; doesn't encrypt traffic.

**MAC Spoofing** — attacker uses a legitimate host's MAC to impersonate that host.

**Malicious Insider** — insider intentionally causing harm.

**Metasploit** — penetration-testing / exploitation framework.

**MFA (Multi-Factor Authentication)** — authentication using two or more of: something you know, have, are.

**MITRE ATT&CK** — framework of adversary tactics and techniques.

**MITRE Corporation** — maintains CVE and ATT&CK.

**Negligent Insider** — insider unintentionally causing harm.

**Nessus** — vulnerability scanner.

**`netstat`** — Windows / Unix command listing TCP/UDP connections; `-a` all, `-o` with owning process, `-e` Ethernet stats.

**Network Segmentation** — dividing a network into logical groups to limit lateral movement.

**Next-Generation Firewall (NGFW)** — adds application-level filtering and deep packet inspection.

**Nmap** — network mapping and port scanner.

**`nslookup`** — DNS query tool.

**OpenSSL** — cryptography library / toolkit.

**Order of Volatility** — RAM → Fixed Disk → Archived Backup; collect most volatile first.

**Penetration Testing** — locating vulnerabilities by simulating attacks.

**Phishing** — fraudulent email used to harvest credentials or deliver malware.

**Port Scanning** — probing for open ports to find attack surface.

**PCI-DSS** — international standard for handling credit-card data.

**Quarantine** — isolating an infected file so it can't execute or spread.

**Ransomware** — malware that encrypts data and demands payment.

**Risk Acceptance** — knowingly tolerating a risk without action.

**Risk Avoidance** — eliminating a risk by removing the activity.

**Risk Control / Mitigation** — implementing controls to reduce likelihood or impact.

**Risk Transfer** — shifting risk to a third party (e.g., insurance).

**Rooting** — gaining root privileges on Android.

**Rootkit** — admin-level malware toolset providing remote access.

**Sandboxing** — running a program in isolation to observe its behavior.

**SCAP** — open standard for automating vulnerability and policy compliance evaluation.

**SIEM** — system that aggregates and analyzes log data, generating alerts for analysts.

**SOAR** — system that automates incident-response steps.

**SOX** — US financial-reporting controls for publicly traded companies.

**Spyware** — malware that secretly gathers data and exfiltrates it.

**SQL Injection (SQLi)** — malicious SQL placed in a form field to access the backend database.

**SSID Cloaking** — disabling Wi-Fi SSID broadcast.

**STIX** — structured threat-intelligence language.

**Symmetric Encryption** — uses one shared key (AES, DES, 3DES).

**Syslog** — log message format with PRI, HEADER (timestamp + hostname), and MSG.

**TAXII** — protocol that transports STIX data.

**Trojan** — malware disguised as legitimate software.

**Vulnerability Database** — repository of known weaknesses (e.g., CVE).

**Vulnerability Management** — proactively identifying and remediating weaknesses.

**WEP** — legacy, broken Wi-Fi encryption.

**Windows Defender** — built-in Windows antivirus / antimalware protection.

**Wireshark** — protocol analyzer / packet capture tool.

**Worm** — self-replicating malware that propagates across networks.

**WPA2-Enterprise** — Wi-Fi authentication using a RADIUS server.

**WPA2-PSK** — Wi-Fi using a pre-shared key.

**WPA3** — strongest current Wi-Fi encryption standard.

**XSS (Cross-Site Scripting)** — injecting client-side scripts into web pages viewed by other users.
