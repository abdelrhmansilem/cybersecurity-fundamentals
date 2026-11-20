# CyberSecurity Fundamentals

> A complete, structured guide to the core concepts of cybersecurity — the 18 career fields, hacker classifications, engagement models, the CIA Triad, vulnerability scoring, compliance frameworks, cryptography, and how HTTP/HTTPS actually work.
>
> Built from my structured study notes, organized so anyone starting in security can use it as a reference and a roadmap.

![Topic: Cybersecurity](https://img.shields.io/badge/topic-cybersecurity-red.svg)
![Level: Fundamentals](https://img.shields.io/badge/level-fundamentals-green.svg)
![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)

---

## Table of Contents

1. [The 18 Cybersecurity Fields](#1-the-18-cybersecurity-fields)
2. [Types of Hackers](#2-types-of-hackers)
3. [Engagements: Scope, Rules & Methodologies](#3-engagements-scope-rules--methodologies)
4. [The CIA Triad](#4-the-cia-triad)
5. [CVE, Severity & CVSS](#5-cve-severity--cvss)
6. [Threat vs Vulnerability vs Risk](#6-threat-vs-vulnerability-vs-risk)
7. [PII & SPII](#7-pii--spii)
8. [Controls, Frameworks & Compliance](#8-controls-frameworks--compliance)
9. [Encryption & Hashing](#9-encryption--hashing)
10. [Authentication vs Authorization](#10-authentication-vs-authorization)
11. [HTTP & HTTPS](#11-http--https)
12. [Suggested Learning Path](#12-suggested-learning-path)

---

## 1. The 18 Cybersecurity Fields

Cybersecurity is not one job — it's an umbrella over many specializations. These are the main fields you can work in:

| # | Field | What You Do |
|---|---|---|
| 1 | **Network Security** | Protect networks, firewalls, VPNs, and intrusion detection systems |
| 2 | **Application Security (AppSec)** | Secure websites, web applications, and mobile apps by identifying software vulnerabilities |
| 3 | **Penetration Testing** | Simulate real attacks legally to find system weaknesses |
| 4 | **Red Teaming** | Perform advanced, realistic attack simulations to evaluate an organization's defenses |
| 5 | **Blue Team / Defensive Security** | Monitor systems, detect attacks, and respond to security incidents |
| 6 | **SOC Analyst / Incident Response** | Analyze alerts and logs, then monitor and stop attacks in real time |
| 7 | **Digital Forensics** | Investigate security incidents, collect digital evidence, and contain breaches |
| 8 | **Bug Bounty Hunting** | Find vulnerabilities in real companies' systems and get rewarded |
| 9 | **Cloud Security** | Protect data and services in AWS, Azure, and Google Cloud |
| 10 | **Identity and Access Management (IAM)** | Manage user identities, permissions, MFA, and Zero Trust access |
| 11 | **Malware Analysis & Reverse Engineering** | Analyze malware, viruses, and attacks to understand how they work |
| 12 | **Threat Intelligence** | Track cyber threats, threat actors, and emerging attack techniques |
| 13 | **Security Engineering** | Build security tools and integrate protection into technical infrastructure |
| 14 | **DevSecOps** | Integrate security into the software development and deployment process |
| 15 | **GRC / Compliance** | Manage governance, risk, and compliance with standards such as ISO 27001 and NIST |
| 16 | **Cryptography** | Use encryption, digital signatures, and secure protocols to protect data |
| 17 | **OT/ICS Security** | Protect industrial systems used in factories, energy, and critical infrastructure |
| 18 | **Mobile, IoT, and Embedded Security** | Secure mobile apps, smart devices, and embedded systems |

**How to choose:** offensive fields (3, 4, 8) suit people who like attacking and problem-solving; defensive fields (5, 6, 7) suit people who like monitoring, analysis, and investigations; engineering fields (13, 14, 16) suit builders; governance fields (15) suit process and documentation lovers.

---

## 2. Types of Hackers

### By intent (the "hat" colors)

| Type | Meaning |
|---|---|
| **White Hat** | Ethical hackers — the good guys who hack **with permission** |
| **Black Hat** | Criminal hackers — the bad guys |
| **Grey Hat** | Hack **without permission** but report the bug |

### By team color

| Team | Role |
|---|---|
| **Red Team** | Attack |
| **Blue Team** | Defend |
| **Purple Team** | Both — works so attackers and defenders improve each other |

---

## 3. Engagements: Scope, Rules & Methodologies

A security engagement (a legal hacking project) is defined by three things:

### Permission boundaries

- **Scope** — *what you are allowed to test.* Everything outside it is off-limits.
- **Rules of Engagement (RoE)** — *the rules you must follow* during testing (when you can test, what techniques are banned, who to contact).

### How much information you get

| Model | Information Provided |
|---|---|
| **Black Box** | No info — you attack blind, like a real external attacker |
| **Grey Box** | Some info — partial knowledge of the target |
| **White Box** | Full info — complete access to source code, architecture, and configs |

### Industry methodologies

Real engagements follow established methodologies — never improvise:

- **OWASP** — web application security testing standards
- **PTES** — Penetration Testing Execution Standard
- **OSSTMM** — Open Source Security Testing Methodology Manual

---

## 4. The CIA Triad

The **three most important goals in cybersecurity**. Every control, tool, and policy exists to protect one of them:

| Letter | Principle | Goal |
|---|---|---|
| **C** | **Confidentiality** | Keep data secret |
| **I** | **Integrity** | Data must not be changed (by unauthorized parties) |
| **A** | **Availability** | Data and systems must be accessible when needed |

If any one of the three breaks, you have a security incident: a data leak breaks Confidentiality, a silent modification breaks Integrity, a DDoS or outage breaks Availability.

---

## 5. CVE, Severity & CVSS

How the industry names and rates vulnerabilities:

| Term | Meaning |
|---|---|
| **CVE** | Unique ID for every vulnerability — e.g. `CVE-2024-1234` |
| **Severity** | Qualitative rating: **Low, Medium, High, Critical** |
| **CVSS** | Quantitative score from **0 to 10** (10 is the most dangerous) |

---

## 6. Threat vs Vulnerability vs Risk

Three terms that are constantly confused:

| Term | Definition | Example |
|---|---|---|
| **Threat** | Possible danger (hacker, virus) | A ransomware group |
| **Vulnerability** | Weakness or hole in the system | An unpatched server |
| **Risk** | Threat + Vulnerability — how bad it can be | That group exploiting that server |

**The goal of all security work: reduce risk.**

---

## 7. PII & SPII

### PII — Personally Identifiable Information

> Any data that can be used to distinguish or infer an individual's identity.

Examples: full name, date of birth, physical address, email address, phone number, and IP address.

### SPII — Sensitive PII

> A high-risk subset of PII that requires **stricter handling and protection guidelines** because its exposure causes significantly greater harm — especially identity theft and fraud.

Examples: Social Security numbers (SSN), financial data, medical records, and biometric information (such as facial recognition data).

---

## 8. Controls, Frameworks & Compliance

### The vocabulary

| Term | Definition |
|---|---|
| **Security Controls** | Safeguards designed to reduce specific security risks |
| **Security Frameworks** | Guidelines used to build plans that mitigate risks and threats to data and privacy (define goals → develop guidelines → implement processes → monitor results) |
| **Compliance** | The process of adhering to internal standards and external regulations |

### The frameworks & regulations you must know

| Framework / Regulation | What It Is |
|---|---|
| **NIST** | US-based agency developing voluntary compliance frameworks like **NIST CSF** and **NIST RMF** to manage risk |
| **FERC-NERC** | Regulation for North American energy/electricity organizations to protect the power grid and comply with **CIP** standards |
| **FedRAMP** | US Federal program standardizing security assessment and monitoring for cloud services |
| **CIS** | Non-profit providing actionable, defensive controls to protect systems and networks |
| **GDPR** | EU regulation protecting data privacy; mandates transparent data handling and **72-hour breach reporting** |
| **PCI DSS** | International standard ensuring safe storage, processing, and transmission of **credit card data** |
| **HIPAA** | US law protecting patient health information (**PHI**) via Privacy, Security, and Breach Notification rules |
| **HITRUST** | A security framework and assurance program helping organizations meet HIPAA compliance |
| **ISO** | Develops international standards for technology and management to improve processes (e.g. **ISO 27001**) |
| **SOC 1 & SOC 2** | AICPA reports evaluating user access policies, financial compliance, and risk levels to prevent fraud |

---

## 9. Encryption & Hashing

### Encryption

- **Encryption** — convert readable data (plaintext) into unreadable data (ciphertext) using an algorithm and a key
- **Decryption** — convert ciphertext back into readable plaintext using the correct key

| Type | How It Works | Examples |
|---|---|---|
| **Symmetric** | Uses the **same secret key** for encryption and decryption | AES, ChaCha20 |
| **Asymmetric** | Uses a **public key** to encrypt/verify and a **private key** to decrypt/sign | RSA, ECC |

### Hashing

- **Hashing** — convert data of any size into a fixed-length value called a **hash**
- **One-way function** — a hash must not be reversible to recover the original data
- **Deterministic** — the same input always produces the same hash

Common algorithms: **SHA-256, SHA-3, bcrypt, Argon2**

**Password storage done right:**

- Store passwords **as hashes, never as plain text**
- **Salt** — a unique random value added to each password before hashing, to prevent rainbow-table attacks
- Use dedicated password-hashing algorithms: **bcrypt, scrypt, or Argon2**

### Digital signatures

A digital signature proves that data **came from the real sender** and **was not modified**:

- **Private key** → creates (signs) the signature
- **Public key** → verifies the signature

### What each one gives you

| Mechanism | Security Property Provided |
|---|---|
| **Encryption** | **Confidentiality** — only authorized people can read the data |
| **Hashing** | **Integrity** — detects whether data has changed |
| **Digital Signatures** | **Integrity + Authenticity + Non-repudiation** |

### Protocols

- **HTTPS / TLS** — uses encryption to protect data sent between a browser and a website
- **SSL** — an old, **deprecated** protocol; modern secure connections use **TLS**

### Common mistakes (avoid these)

1. Using **MD5 or SHA-1** for passwords
2. Storing encryption keys **beside the encrypted data**
3. **Hardcoding keys** in source code
4. Using **weak or reused** passwords
5. **Building custom encryption** instead of using trusted, battle-tested libraries

---

## 10. Authentication vs Authorization

Two different questions, asked in order:

| Concept | Question | Example |
|---|---|---|
| **Authentication** | *Who are you?* (username + password) | You log in to Gmail |
| **Authorization** | *What can you do?* (your permissions) | You can only read **your** emails |

Authentication comes first — authorization decides what that verified identity is allowed to access.

---

## 11. HTTP & HTTPS

### What they are

- **HTTP** — *HyperText Transfer Protocol*: the set of rules used for communicating with web servers to transmit webpage data (HTML, images, videos...). Developed by Tim Berners-Lee and his team between **1989–1991**.
- **HTTPS** — *HTTP Secure*: the secure version of HTTP. Data is **encrypted**, which stops people from reading what you send and receive, **and** gives you assurance that you're talking to the correct web server — not something impersonating it.

### Core nature of HTTP

| Property | Meaning |
|---|---|
| **Client-Server Protocol** | The client (browser / user-agent) always initiates the request. The server never starts the conversation |
| **Application Layer** | HTTP sits on top of TCP (or QUIC in HTTP/3) — it only needs a reliable transport |
| **Stateless** | Each request is independent; the server does not remember previous requests by itself |
| **Not Sessionless** | Cookies (and other mechanisms) add state — that's how you get login sessions and shopping carts |
| **Extensible** | New functionality is added through headers without breaking old clients |
| **Human-readable (HTTP/1.x)** | Messages are plain text, easy to read and debug. HTTP/2 and HTTP/3 use binary frames but keep the same meaning |

### How a page is loaded

1. Browser sends a request for the **HTML document**
2. Server returns the HTML
3. Browser parses the HTML and discovers more resources (CSS, JS, images, fonts...)
4. Browser sends additional requests for those resources
5. Browser combines everything and **renders the final page**

### Message structure (request or response)

```
1. Start-line   → method + path + version   (request)
                  version + status-code + reason   (response)
2. Headers      → key: value metadata, one per line
3. Blank line   → marks the end of headers
4. Body         → optional data (HTML, JSON, form data, file...)
```

### Connection behavior across versions

| Version | Behavior |
|---|---|
| **HTTP/1.0** | Opens a new TCP connection for almost every request (slow) |
| **HTTP/1.1** | Persistent connections (**Keep-Alive**) + optional pipelining |
| **HTTP/2** | **Multiplexing** — many requests/responses over one connection at the same time + header compression |
| **HTTP/3** | Runs over **QUIC** (UDP-based) — faster connection setup, better on lossy networks |

### Intermediate systems

Between the browser and the server you often find — and these can change, cache, or inspect HTTP messages:

- **Proxies** (caching, filtering, authentication, load balancing)
- **CDNs** (Cloudflare, etc.)
- **Load balancers**
- **Caches** (browser cache + shared caches)

### Why HTTPS matters

- HTTP sends everything in **clear text** → anyone on the path can read or modify the data
- **HTTPS = HTTP + TLS** (encryption + authentication of the server)
- SSL is the old name; modern sites use TLS
- Always prefer HTTPS — browsers mark plain HTTP as **"Not Secure"**

---

## 12. Suggested Learning Path

These fundamentals map to a practical progression. From the original notes, the companion study areas are:

1. **Linux fundamentals** — the operating system every security professional needs (TryHackMe's Linux path is a great start)
2. **Vulnerabilities** — deep-diving into vulnerability classes one by one (web, network, mobile...)
3. Pick **one field** from [section 1](#1-the-18-cybersecurity-fields) that fits your strengths and go deep

---

## License

This repository is released under the [MIT License](LICENSE) — use it, share it, and build on it freely.

## Disclaimer

This material is for **educational purposes** only. Anything you learn here must only be applied legally — with permission, within scope, on systems you own or are authorized to test.
