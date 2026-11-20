# CyberSecurity Fundamentals

> A complete, structured guide to cybersecurity — from the 18 career fields and core principles, through the full HTTP protocol, to hands-on references for Nmap, Curl, Linux, Bash, and OSINT reconnaissance.
>
> Built from structured study notes, organized so anyone starting in security can use it as a reference and a roadmap.

![Topic: Cybersecurity](https://img.shields.io/badge/topic-cybersecurity-red.svg)
![Level: Fundamentals](https://img.shields.io/badge/level-fundamentals-green.svg)
![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)

---

## Table of Contents

**Part I — Foundations**

1. [The 18 Cybersecurity Fields](#1-the-18-cybersecurity-fields)
2. [Types of Hackers](#2-types-of-hackers)
3. [Engagements: Scope, Rules & Methodologies](#3-engagements-scope-rules--methodologies)
4. [The CIA Triad](#4-the-cia-triad)
5. [CVE, Severity & CVSS](#5-cve-severity--cvss)
6. [Threat vs Vulnerability vs Risk](#6-threat-vs-vulnerability-vs-risk)
7. [PII & SPII](#7-pii--spii)
8. [Controls, Frameworks & Compliance](#8-controls-frameworks--compliance)

**Part II — Cryptography & Access**

9. [Encryption & Hashing](#9-encryption--hashing)
10. [Authentication vs Authorization](#10-authentication-vs-authorization)

**Part III — Web & HTTP Deep Dive**

11. [HTTP & HTTPS](#11-http--https)
12. [URL Anatomy](#12-url-anatomy)
13. [Requests & Responses](#13-requests--responses)
14. [HTTP Methods & Safe/Idempotent](#14-http-methods--safeidempotent)
15. [HTTP Headers](#15-http-headers)
16. [HTTP Status Codes](#16-http-status-codes)
17. [Cookies & Sessions](#17-cookies--sessions)
18. [HTTP Caching](#18-http-caching)
19. [CORS & Same-Origin Policy](#19-cors--same-origin-policy)
20. [HTTP Authentication](#20-http-authentication)
21. [Request Body Types](#21-request-body-types)
22. [Request Targets (Path Forms)](#22-request-targets-path-forms)

**Part IV — Offensive Security**

23. [Vulnerabilities, PoCs & Exploits](#23-vulnerabilities-pocs--exploits)
24. [What Is a Payload?](#24-what-is-a-payload)
25. [OWASP Top 10](#25-owasp-top-10)
26. [SQL, NoSQL & SQL Injection](#26-sql-nosql--sql-injection)
27. [CVSS Metrics (Calculating Severity)](#27-cvss-metrics-calculating-severity)
28. [The Penetration Testing Process](#28-the-penetration-testing-process)
29. [MITRE ATT&CK & The Cyber Kill Chain](#29-mitre-attck--the-cyber-kill-chain)
30. [Bug Bounty Reporting](#30-bug-bounty-reporting)

**Part V — Recon & OSINT**

31. [Passive Reconnaissance](#31-passive-reconnaissance)
32. [Networking Basics: OSI Model & TCP/UDP](#32-networking-basics-osi-model--tcpudp)
33. [DNS Record Types](#33-dns-record-types)
34. [OSINT & Recon Tools](#34-osint--recon-tools)
35. [Hunting Web Apps (Online Recon Tools)](#35-hunting-web-apps-online-recon-tools)
36. [Common Ports & Protocols](#36-common-ports--protocols)

**Part VI — Systems, Tooling & Mobile**

37. [Linux Commands](#37-linux-commands)
38. [Bash Scripting Basics](#38-bash-scripting-basics)
39. [Nmap Scan Techniques & Options](#39-nmap-scan-techniques--options)
40. [Curl Common Options & Flags](#40-curl-common-options--flags)
41. [JADX & Mobile Testing](#41-jadx--mobile-testing)
42. [Quick Tips](#42-quick-tips)
43. [Understanding Version Numbers (SemVer)](#43-understanding-version-numbers-semver)
44. [Free Practice Server: Segfault (THC)](#44-free-practice-server-segfault-thc)

45. [Suggested Learning Path](#45-suggested-learning-path)

---

## Part I — Foundations

### 1. The 18 Cybersecurity Fields

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

### 2. Types of Hackers

**By intent (the "hat" colors):**

| Type | Meaning |
|---|---|
| **White Hat** | Ethical hackers — the good guys who hack **with permission** |
| **Black Hat** | Criminal hackers — the bad guys |
| **Grey Hat** | Hack **without permission** but report the bug |

**By team color:**

| Team | Role |
|---|---|
| **Red Team** | Attack |
| **Blue Team** | Defend |
| **Purple Team** | Both — attackers and defenders improving each other |

### 3. Engagements: Scope, Rules & Methodologies

**Permission boundaries:**

- **Scope** — *what you are allowed to test.* Everything outside it is off-limits.
- **Rules of Engagement (RoE)** — *the rules you must follow* during testing.

**How much information you get:**

| Model | Information Provided |
|---|---|
| **Black Box** | No info — attack blind, like a real external attacker |
| **Grey Box** | Some info — partial knowledge of the target |
| **White Box** | Full info — complete access to source, architecture, configs |

**Industry methodologies** — real engagements follow established standards, never improvise: **OWASP**, **PTES**, **OSSTMM**.

### 4. The CIA Triad

The **three most important goals in cybersecurity**. Every control, tool, and policy exists to protect one of them:

| Letter | Principle | Goal |
|---|---|---|
| **C** | **Confidentiality** | Keep data secret |
| **I** | **Integrity** | Data must not be changed (by unauthorized parties) |
| **A** | **Availability** | Data and systems must be accessible when needed |

If any one breaks, you have a security incident: a data leak breaks Confidentiality, a silent modification breaks Integrity, a DDoS or outage breaks Availability.

### 5. CVE, Severity & CVSS

| Term | Meaning |
|---|---|
| **CVE** | Unique ID for every vulnerability — e.g. `CVE-2024-1234` |
| **Severity** | Qualitative rating: **Low, Medium, High, Critical** |
| **CVSS** | Quantitative score from **0 to 10** (10 is the most dangerous) |

### 6. Threat vs Vulnerability vs Risk

| Term | Definition | Example |
|---|---|---|
| **Threat** | Possible danger (hacker, virus) | A ransomware group |
| **Vulnerability** | Weakness or hole in the system | An unpatched server |
| **Risk** | Threat + Vulnerability — how bad it can be | That group exploiting that server |

**The goal of all security work: reduce risk.**

### 7. PII & SPII

**PII — Personally Identifiable Information:** any data that can be used to distinguish or infer an individual's identity.
Examples: full name, date of birth, physical address, email address, phone number, and IP address.

**SPII — Sensitive PII:** a high-risk subset of PII that requires **stricter handling and protection guidelines** because its exposure causes significantly greater harm — especially identity theft and fraud.
Examples: Social Security numbers (SSN), financial data, medical records, and biometric information (such as facial recognition data).

### 8. Controls, Frameworks & Compliance

**The vocabulary:**

| Term | Definition |
|---|---|
| **CIA Triad** | Confidentiality, Integrity, and Availability — the three foundational principles used to set appropriate controls that mitigate threats, risks, and vulnerabilities |
| **Security Controls** | Safeguards designed to reduce specific security risks |
| **Security Frameworks** | Guidelines used to build plans that mitigate risks and threats to data and privacy (define goals → develop guidelines → implement processes → monitor results) |
| **Compliance** | The process of adhering to internal standards and external regulations |

**The frameworks & regulations you must know:**

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

## Part II — Cryptography & Access

### 9. Encryption & Hashing

**Encryption & decryption:**

- **Encryption** — convert readable data (plaintext) into unreadable data (ciphertext) using an algorithm and a key
- **Decryption** — convert ciphertext back into readable plaintext using the correct key

| Type | How It Works | Examples |
|---|---|---|
| **Symmetric** | Uses the **same secret key** for encryption and decryption | AES, ChaCha20 |
| **Asymmetric** | Uses a **public key** to encrypt/verify and a **private key** to decrypt/sign | RSA, ECC |

**Hashing:**

- **Hashing** — convert data of any size into a fixed-length value called a **hash**
- **One-way function** — a hash must not be reversible to recover the original data
- **Deterministic** — the same input always produces the same hash

Common algorithms: **SHA-256, SHA-3, bcrypt, Argon2**

**Password storage done right:**

- Store passwords **as hashes, never as plain text**
- **Salt** — a unique random value added to each password before hashing, to prevent rainbow-table attacks
- Use dedicated password-hashing algorithms: **bcrypt, scrypt, or Argon2**

**Digital signatures** — prove that data **came from the real sender** and **was not modified**:

- **Private key** → creates (signs) the signature
- **Public key** → verifies the signature

**What each mechanism gives you:**

| Mechanism | Security Property Provided |
|---|---|
| **Encryption** | **Confidentiality** — only authorized people can read the data |
| **Hashing** | **Integrity** — detects whether data has changed |
| **Digital Signatures** | **Integrity + Authenticity + Non-repudiation** |

**Protocols:**

- **HTTPS / TLS** — uses encryption to protect data sent between a browser and a website
- **SSL** — an old, **deprecated** protocol; modern secure connections use **TLS**

**Common mistakes (avoid these):**

1. Using **MD5 or SHA-1** for passwords
2. Storing encryption keys **beside the encrypted data**
3. **Hardcoding keys** in source code
4. Using **weak or reused** passwords
5. **Building custom encryption** instead of using trusted, battle-tested libraries

### 10. Authentication vs Authorization

| Concept | Question | Example |
|---|---|---|
| **Authentication** | *Who are you?* (username + password) | You log in to Gmail |
| **Authorization** | *What can you do?* (your permissions) | You can only read **your** emails |

Authentication comes first — authorization decides what that verified identity is allowed to access.

---

## Part III — Web & HTTP Deep Dive

### 11. HTTP & HTTPS

**What they are:**

- **HTTP** — *HyperText Transfer Protocol*: the set of rules used for communicating with web servers to transmit webpage data (HTML, images, videos...). Developed by Tim Berners-Lee and his team between **1989–1991**.
- **HTTPS** — *HTTP Secure*: the secure version of HTTP. Data is **encrypted**, which stops people from reading what you send and receive, **and** gives you assurance that you're talking to the correct web server — not something impersonating it.

**Core nature of HTTP:**

| Property | Meaning |
|---|---|
| **Client-Server Protocol** | The client (browser / user-agent) always initiates the request. The server never starts the conversation |
| **Application Layer** | HTTP sits on top of TCP (or QUIC in HTTP/3) — it only needs a reliable transport |
| **Stateless** | Each request is independent; the server does not remember previous requests by itself |
| **Not Sessionless** | Cookies (and other mechanisms) add state — that's how you get login sessions and shopping carts |
| **Extensible** | New functionality is added through headers without breaking old clients |
| **Human-readable (HTTP/1.x)** | Messages are plain text, easy to read and debug. HTTP/2 and HTTP/3 use binary frames but keep the same meaning |

**How a page is loaded:**

1. Browser sends a request for the **HTML document**
2. Server returns the HTML
3. Browser parses the HTML and discovers more resources (CSS, JS, images, fonts...)
4. Browser sends additional requests for those resources
5. Browser combines everything and **renders the final page**

**Message structure (request or response):**

```
1. Start-line   → method + path + version   (request)
                  version + status-code + reason   (response)
2. Headers      → key: value metadata, one per line
3. Blank line   → marks the end of headers
4. Body         → optional data (HTML, JSON, form data, file...)
```

**Connection behavior across versions:**

| Version | Behavior |
|---|---|
| **HTTP/1.0** | Opens a new TCP connection for almost every request (slow) |
| **HTTP/1.1** | Persistent connections (**Keep-Alive**) + optional pipelining |
| **HTTP/2** | **Multiplexing** — many requests/responses over one connection at the same time + header compression |
| **HTTP/3** | Runs over **QUIC** (UDP-based) — faster connection setup, better on lossy networks |

**Intermediate systems** — between the browser and the server you often find, and these can change, cache, or inspect HTTP messages:

- **Proxies** (caching, filtering, authentication, load balancing)
- **CDNs** (Cloudflare, etc.)
- **Load balancers**
- **Caches** (browser cache + shared caches)

**Why HTTPS matters:**

- HTTP sends everything in **clear text** → anyone on the path can read or modify the data
- **HTTPS = HTTP + TLS** (encryption + authentication of the server)
- SSL is the old name; modern sites use TLS
- Always prefer HTTPS — browsers mark plain HTTP as **"Not Secure"**

### 12. URL Anatomy

```
https://sub.domain.com:443/dir/file.php?id=1#fun
```

| # | Component | Meaning |
|---|---|---|
| 1 | `https://` | **Protocol / Scheme** — Hypertext Transfer Protocol Secure |
| 2 | `sub` | **Subdomain** |
| 3 | `domain` | **Domain Name / Host** |
| 4 | `.com` | **Top-Level Domain (TLD)** |
| 5 | `:443` | **Port** — default 443 for HTTPS, 80 for HTTP |
| 6 | `/dir` | **Directory / Path** |
| 7 | `/file.php` | **File / Resource** — specific target resource with file extension |
| 8 | `?id=1` | **Query String / Parameter** — key-value pairs sent to the server |
| 9 | `#fun` | **Fragment / Anchor** — targets a specific page section; client-side only |

**Deeper definitions:**

- **Scheme** — instructs what protocol to use for accessing the resource: HTTP, HTTPS, FTP...
- **User** — some services require authentication; a username and password can be put into the URL to log in
- **Host** — the domain name or IP address of the server you wish to access
- **Port** — the port you connect to; usually 80 for HTTP and 443 for HTTPS, but it can be hosted on any port between 1–65535
- **Path** — the file name or location of the resource you are trying to access
- **Query String** — extra bits of information sent to the requested path. For example, `/blog?id=1` tells the blog path you wish to receive the article with the id of 1
- **Fragment** — a reference to a location on the actual page requested; commonly used for long pages so a specific part can be linked directly and is visible as soon as the page loads

### 13. Requests & Responses

**Example request (line by line):**

```http
GET / HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://site.com/
```

- **Line 1** — the `GET` method, requesting the home page with `/`, and telling the web server we are using HTTP protocol version 1.1
- **Line 2** — we tell the web server which website we want (`example.com`)
- **Line 3** — we tell the web server we are using the Firefox version 87 browser
- **Line 4** — we tell the web server the web page that referred us to this one (`https://example.com`)
- **Line 5** — HTTP requests always end with a **blank line** to inform the web server the request has finished

**Example response (line by line):**

```http
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    Welcome To example.com
  </body>
</html>
```

- **Line 1** — HTTP 1.1 is the protocol version the server is using, followed by the HTTP Status Code — here `200 OK`, telling us the request completed successfully
- **Line 2** — the web server software and version number
- **Line 3** — the current date, time and timezone of the web server
- **Line 4** — the `Content-Type` header tells the client what sort of information is being sent: HTML, images, videos, PDF, XML...
- **Line 5** — `Content-Length` tells the client how long the response is, so we can confirm no data is missing
- **Line 6** — the HTTP response contains a blank line to confirm the end of the response headers
- **Lines 7–14** — the information that was requested, in this instance the homepage

### 14. HTTP Methods & Safe/Idempotent

**The methods:**

| Method | Purpose |
|---|---|
| **GET** | Getting information from a web server |
| **POST** | Submitting data to the web server, potentially creating new records |
| **PUT** | Submitting data to a web server to update information |
| **PATCH** | Apply partial modifications to a resource |
| **DELETE** | Deleting information/records from a web server |
| **OPTIONS** | Describe communication options for the target resource |
| **HEAD** | Same as GET but returns only headers (no body) — useful to check size, type, or existence |
| **CONNECT** | Establishes a tunnel (used for HTTPS through proxies) |
| **TRACE** | Echoes the received request (mainly for debugging; often disabled for security) |

**Safe vs Idempotent:**

- **Safe** — the method does not change server state (read-only). Safe methods: `GET, HEAD, OPTIONS, TRACE`
- **Idempotent** — sending the same request multiple times has the same effect as sending it once. Idempotent methods: all safe methods + `PUT` + `DELETE`

| Method | Safe | Idempotent |
|---|---|---|
| GET | ✅ | ✅ |
| HEAD | ✅ | ✅ |
| OPTIONS | ✅ | ✅ |
| PUT | ❌ | ✅ |
| DELETE | ❌ | ✅ |
| POST | ❌ | ❌ |
| PATCH | ❌ | Usually ❌ |

**Why it matters:**

- Browsers and crawlers can safely retry or prefetch **Safe** methods
- Load balancers and proxies can automatically retry **Idempotent** methods if the connection drops
- **POST** is dangerous to retry blindly (can create duplicate orders or charges)

### 15. HTTP Headers

**Request headers (client → server):**

| Header | Purpose |
|---|---|
| `Host` | Specifies the target domain when multiple sites share one server |
| `User-Agent` | Identifies browser, OS, and version to properly render and format content |
| `Content-Length` | Size of the sent data (body) in bytes — verifies complete transmission |
| `Accept-Encoding` | Compression algorithms supported by the browser (e.g. gzip, br) |
| `Cookie` | Sends stored session identifiers and state back to the server |
| `Authorization` | Passes credentials or auth tokens (e.g. Bearer tokens) |
| `Referer` | The URL of the previous page that linked to the requested resource |

**Response headers (server → client):**

| Header | Purpose |
|---|---|
| `Set-Cookie` | Instructs the browser to store a cookie and return it in future requests |
| `Cache-Control` | Directives defining how and for how long the response should be cached |
| `Content-Type` | Specifies the MIME type of the returned resource (e.g. text/html, application/json) |
| `Content-Encoding` | The compression algorithm actually used on the response body (e.g. gzip) |
| `Location` | Target URL used for redirects (paired with 3xx status codes) |
| `Access-Control-Allow-Origin` | Defines permitted origins under CORS policies |

### 16. HTTP Status Codes

**The five classes:**

| Class | Meaning |
|---|---|
| **1xx** Informational | Request received, continuing process |
| **2xx** Success | The action was successfully received, understood, and accepted |
| **3xx** Redirection | Further action needs to be taken to complete the request |
| **4xx** Client Error | Request contains bad syntax or cannot be fulfilled |
| **5xx** Server Error | Server failed to fulfill an apparently valid request |

**The common codes:**

| Code | Name | Meaning |
|---|---|---|
| 200 | OK | Request succeeded (standard successful response) |
| 201 | Created | Request succeeded and a new resource was created (commonly after POST) |
| 204 | No Content | Request succeeded, but there is no content to return |
| 301 | Moved Permanently | Target resource assigned a new permanent URI |
| 302 | Found | Resource resides temporarily under a different URI |
| 304 | Not Modified | Resource has not changed; client can use the cached version |
| 400 | Bad Request | Server cannot process the request due to malformed syntax |
| 401 | Unauthorized | Authentication required or has failed (user identity unknown) |
| 403 | Forbidden | Server understands the request but refuses to authorize it (insufficient permissions) |
| 404 | Not Found | Server cannot find the requested resource/endpoint |
| 405 | Method Not Allowed | HTTP method used is not supported for this endpoint (e.g. POST instead of GET) |
| 429 | Too Many Requests | User has sent too many requests in a given time (rate limiting) |
| 500 | Internal Server Error | Generic server error when no specific message is suitable |
| 502 | Bad Gateway | Gateway/proxy received an invalid response from the inbound server |
| 503 | Service Unavailable | Server is temporarily unable to handle the request (overloaded or down for maintenance) |
| 504 | Gateway Timeout | Gateway/proxy did not receive a timely response from the upstream server |

### 17. Cookies & Sessions

HTTP is **stateless** → each request is independent. Cookies add state so the server can remember you across requests:

1. Server sends a `Set-Cookie` header in the response
2. Browser stores the cookie
3. Browser automatically sends a `Cookie` header in every following request
4. Server reads the cookie and knows who you are (session)

**Important cookie flags (security):**

| Flag | Protection |
|---|---|
| `HttpOnly` | JavaScript cannot read the cookie (**protects against XSS**) |
| `Secure` | Cookie is only sent over **HTTPS** |
| `SameSite` | Controls when the cookie is sent with cross-site requests (**protects against CSRF**) — `Strict` / `Lax` / `None` |

Common uses: login sessions, shopping carts, preferences, tracking.

### 18. HTTP Caching

**Caching** — storing a copy of a response so it can be reused without contacting the origin server again.

Controlled mainly by these headers:

| Header | Effect |
|---|---|
| `Cache-Control: max-age=3600` | Cache for 1 hour |
| `Cache-Control: no-store` | Do not store at all |
| `Cache-Control: no-cache` | Must revalidate with the server before use |
| `ETag` / `Last-Modified` | Server can reply `304 Not Modified` if content has not changed |

**Types of caches:** browser cache (private) and proxy/CDN cache (shared/public).

**Benefits:** faster pages, less server load, lower bandwidth.

### 19. CORS & Same-Origin Policy

**Same-Origin Policy** — browsers block a page from reading responses that come from a different origin (different scheme, domain, or port). This protects users from malicious sites stealing data.

**CORS (Cross-Origin Resource Sharing)** — the server can relax the restriction using special headers:

```
Access-Control-Allow-Origin: *        (or a specific domain)
Access-Control-Allow-Methods: GET, POST, PUT...
Access-Control-Allow-Headers: Content-Type, Authorization...
Access-Control-Allow-Credentials: true
```

**Preflight:** for complex requests, the browser first sends an `OPTIONS` request to ask permission.

### 20. HTTP Authentication

Two common ways:

1. **HTTP Basic Authentication** — the browser sends `Authorization: Basic base64(username:password)`. Simple, but must be used **only over HTTPS**.
2. **Cookie / Token based (most modern apps)** — after login the server gives a session cookie or JWT token; the client sends it in later requests (`Cookie` header or `Authorization: Bearer <token>`).

**Related headers:** `WWW-Authenticate` (server asks for authentication) and `Authorization` (client sends credentials or token).

### 21. Request Body Types

The body is only present in methods like `POST`, `PUT`, `PATCH`. Common `Content-Type` values:

| Content-Type | Used For |
|---|---|
| `application/x-www-form-urlencoded` | Classic HTML forms (`name=value&email=test%40example.com`) |
| `multipart/form-data` | Forms that include files (images, documents) |
| `application/json` | Modern APIs (JSON objects) |
| `text/plain` / `application/xml` | Less common |

The `Content-Type` header tells the server how to parse the body. `Content-Length` tells the size of the body.

### 22. Request Targets (Path Forms)

The path in the request-line can appear in different forms:

| Form | Example | Used With |
|---|---|---|
| **Origin form** (most common) | `GET /path/to/page HTTP/1.1` + `Host:` header | Normal client requests |
| **Absolute form** | `GET https://example.com/path HTTP/1.1` | Proxies |
| **Authority form** | `CONNECT example.com:443 HTTP/1.1` | Only with CONNECT |
| **Asterisk form** | `OPTIONS * HTTP/1.1` | Only with OPTIONS |

---

## Part IV — Offensive Security

### 23. Vulnerabilities, PoCs & Exploits

| Term | Definition |
|---|---|
| **Vulnerability** | A weakness or flaw in the design, implementation, or behaviour of a system or application. An attacker can exploit these weaknesses to gain access to unauthorized information or perform unauthorized actions |
| **Security Misconfiguration** | Flaws caused by failing to properly set up or maintain a system's security settings — default credentials, unnecessary ports/services left enabled, exposed sensitive error messages and debugging features |
| **Proof of Concept (PoC)** | A technique or tool that often demonstrates the exploitation of a vulnerability |
| **Exploit** | An action or behaviour that utilises a vulnerability on a system or application |

### 24. What Is a Payload?

**Payload** — malicious code that runs after you hack a system.

Examples: **reverse shell**, **ransomware**, **backdoor**. Commonly created with tools like **Metasploit**.

### 25. OWASP Top 10

The OWASP Top 10 — the most critical web application security risks:

| ID | Risk | Meaning |
|---|---|---|
| **A01** | **Broken Access Control** | Unauthorized users accessing sensitive resources or actions |
| **A02** | **Cryptographic Failures** | Exposing sensitive data through missing or weak encryption |
| **A03** | **Injection** | Untrusted user data executed as commands (SQLi, Command Injection, LDAP) |
| **A04** | **Insecure Design** | Flaws in architecture and threat modeling before writing code |
| **A05** | **Security Misconfiguration** | Default passwords, exposed debug logs, unpatched services |
| **A06** | **Vulnerable and Outdated Components** | Using libraries or frameworks with known CVEs |
| **A07** | **Identification and Authentication Failures** | Weak passwords, missing brute-force protection, broken sessions |
| **A08** | **Software and Data Integrity Failures** | Unsigned plugins, auto-updates from untrusted sources, insecure deserialization |
| **A09** | **Security Logging and Monitoring Failures** | Missing breach alerts, lack of log retention, delayed response |
| **A10** | **Server-Side Request Forgery (SSRF)** | Coercing a vulnerable server to fetch internal resources |

### 26. SQL, NoSQL & SQL Injection

Almost every web app sits on a database — understanding how it works is what makes SQL Injection (OWASP A03) possible to find and understand.

#### Relational (SQL) vs Non-Relational (NoSQL)

| | **Relational (SQL)** | **Non-Relational (NoSQL)** |
|---|---|---|
| **Data model** | Tables (rows & columns) with a **fixed schema** | Flexible structures: **documents (JSON)**, **key-value**, **wide-column**, **graphs** |
| **Query language** | Standardized **SQL** | Varies per database (e.g. MongoDB queries) |
| **Relationships** | Real relations between tables via **foreign keys** + JOINs | Usually no JOINs — data is duplicated/embedded |
| **Schema** | Defined upfront, changes are expensive | Dynamic — add fields anytime |
| **Scaling** | Traditionally vertical (bigger server) | Natively horizontal (more servers) |
| **Examples** | MySQL, PostgreSQL, MSSQL, Oracle, SQLite | MongoDB, Redis, Cassandra, CouchDB, Elasticsearch |
| **Best for** | Structured data, complex queries, strict transactions (ACID) | Fast-changing data, huge scale, speed |

#### Core SQL commands

| Command | What it does | Example |
|---|---|---|
| **SELECT** | Retrieves data | `SELECT * FROM users;` |
| **WHERE** | Filters rows by a condition | `SELECT * FROM users WHERE id = 1;` |
| **INSERT** | Adds new rows | `INSERT INTO users (name) VALUES ('ali');` |
| **UPDATE** | Modifies existing rows | `UPDATE users SET email='new@x.com' WHERE id=1;` |
| **DELETE** | Removes rows | `DELETE FROM users WHERE id=1;` |
| **UNION** | Combines the results of two SELECTs — the heart of Union-based SQLi | `SELECT name FROM users UNION SELECT password FROM admin;` |
| **ORDER BY** | Sorts results (also used in SQLi to count columns) | `SELECT * FROM users ORDER BY id DESC;` |
| **JOIN** | Combines rows from related tables | `SELECT * FROM users INNER JOIN orders ON users.id = orders.user_id;` |

**More keywords worth knowing:**

| Keyword | Purpose |
|---|---|
| `AND` / `OR` | Combine conditions inside WHERE (also the classic injection `' OR 1=1--`) |
| `LIKE` | Pattern matching (`%` wildcard) |
| `LIMIT` / `OFFSET` | Restrict and page results |
| `GROUP BY` / `HAVING` | Aggregate rows and filter groups |
| `COUNT` / `SUM` / `AVG` | Aggregate functions |
| `DISTINCT` | Remove duplicates |
| `CREATE TABLE` / `DROP TABLE` | Define / destroy structure |
| `--` and `#` | SQL comments — used in injection to cut off the rest of the query |

#### SQL Injection (SQLi)

**Definition:** injecting malicious SQL through untrusted input so the database executes it as part of the application's query.

**Classic example** — a login query built by string concatenation:

```sql
SELECT * FROM users WHERE user='INPUT' AND pass='INPUT'
```

Entering `' OR 1=1 --` as the username turns it into:

```sql
SELECT * FROM users WHERE user='' OR 1=1 --' AND pass='...'
```

→ the condition is always true and the rest is commented out → **authentication bypass**.

**The three main SQLi categories** (verified terminology):

| Type | How It Works | Sub-Types |
|---|---|---|
| **In-Band (Classic)** | The **same channel** is used to launch the attack AND read the results | **Union-based** — appends attacker's data to the real response via `UNION` · **Error-based** — extracts data from database error messages |
| **Inferential (Blind)** | No data comes back in the response — the attacker reconstructs the database by observing **behavior changes** | **Boolean-based blind** — page content differs on TRUE vs FALSE conditions (`' AND 1=1--` vs `' AND 1=2--`) · **Time-based blind** — the response is delayed by `SLEEP()` / `WAITFOR DELAY` when the condition is true |
| **Out-of-Band (OOB)** | Data is exfiltrated over a **different channel** (e.g. DNS/HTTP callbacks to the attacker's server) — used when the response channel is unavailable; depends on DB features like MSSQL `xp_dirtree` or Oracle `UTL_HTTP` | DNS exfiltration, HTTP callbacks |

**Also worth knowing:** **Second-order SQLi** — the payload is stored now (e.g. in a profile field) and executes later when another part of the app uses that data.

**Quick manual tests:**

```
'            → breaks the query and may trigger an SQL error
' OR '1'='1  → always-true condition (auth bypass)
1' ORDER BY 1--   → increase the number until it errors → counts columns (preparation for UNION)
' AND SLEEP(5)--  → 5-second delay = time-based blind confirmed
```

**Automation:** `sqlmap` (the standard), `ghauri`.

**Prevention:** parameterized queries / prepared statements · ORMs · input validation · least-privilege DB users · WAF as an extra layer (never the only one).

### 27. CVSS Metrics (Calculating Severity)

The CVSS score is built from 8 metrics:

| # | Metric | Values |
|---|---|---|
| 1 | **Attack Vector (AV)** | Network / Adjacent / Local / Physical |
| 2 | **Attack Complexity (AC)** | Low / High |
| 3 | **Privileges Required (PR)** | None / Low / High |
| 4 | **User Interaction (UI)** | None / Required |
| 5 | **Scope (S)** | Unchanged / Changed |
| 6 | **Confidentiality (C)** | None / Low / High |
| 7 | **Integrity (I)** | None / Low / High |
| 8 | **Availability (A)** | None / Low / High |

### 28. The Penetration Testing Process

1. **Reconnaissance** — gather information
2. **Scanning** — find weaknesses
3. **Gaining Access** — exploit
4. **Maintaining Access**
5. **Covering Tracks**
6. **Reporting** — write the report

### 29. MITRE ATT&CK & The Cyber Kill Chain

**MITRE ATT&CK:**

- Free database of real hacker techniques
- Shows how attackers behave in real life
- Used by all big companies and governments

**Cyber Kill Chain** — the stages of a targeted attack:

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control
7. Actions on Objectives

### 30. Bug Bounty Reporting

A professional vulnerability report contains:

```
Title:              Vuln name + impact
Severity:           Low / Medium / High / Critical
Summary:            ...
Endpoint:           ...
Steps to Reproduce: ...
POC:                ...
Impact:             ...
Remediation:        ...
```

A clear title with impact, numbered reproduction steps, and a concrete impact statement are what separate accepted reports from ignored ones.

---

## Part V — Recon & OSINT

### 31. Passive Reconnaissance

**Passive vs Active:**

| Type | Meaning |
|---|---|
| **Passive** | Gather info without touching the target (no packets to the target) |
| **Active** | Send queries/probes directly to the target (can be detected) |

**Rule: passive first — active testing only when authorized / in-scope.**

**WHOIS** (`TCP/43`, plain text) — domain registration info:

| Field | Question It Answers |
|---|---|
| Registrar | Who registered the domain? |
| Registrant | The domain owner (often hidden by WHOIS privacy protection) |
| Creation Date | When was it registered? |
| Updated Date | When was it last modified? |
| Expiration Date | When does it expire? |
| Name Servers | Who is responsible for DNS? |
| Status | Current registration/transfer state (e.g. `clientTransferProhibited`) |
| Abuse Contact | Where to report abuse to the registrar |

```bash
whois target.com
echo "target.com" | dnsx -recon -resp
# Web: https://www.whoxy.com/
```

**RDAP** — Registration Data Access Protocol: the modern WHOIS, over **HTTPS + JSON**:

```bash
curl -s https://rdap.verisign.com/com/v1/domain/example.com | jq
```

**DNS queries** — `dig` (preferred) and `nslookup` (older/compatible):

```
dig [@SERVER] DOMAIN [TYPE]
nslookup -type=TYPE DOMAIN

dig target.com A
dig target.com MX
dig target.com TXT
```

**Subdomain discovery (passive):**

- **DNSDumpster** — subdomains + DNS info
- **crt.sh** — subdomains from SSL certificates (search `%.target.com`)

**Shodan** — search engine for exposed Internet services/devices. Can show IP, ports, services, banners, technology, ASN:

```
hostname:target.com
org:"Target"
```

**Memory map:** WHOIS/RDAP → domain info · DNS → records · DNSDumpster → subdomains · crt.sh → certificate-based subdomains · Shodan → exposed services.

### 32. Networking Basics: OSI Model & TCP/UDP

**OSI (Open Systems Interconnection)** — a standardised model used to demonstrate the theory behind computer networking. It consists of **seven layers**:

| # | Layer | Role |
|---|---|---|
| 7 | **Application** | Where applications and users interact — HTTP, DNS, SMTP... |
| 6 | **Presentation** | Data formatting, translation, and encryption |
| 5 | **Session** | Establishes, manages, and terminates connections/sessions |
| 4 | **Transport** | End-to-end delivery between hosts — TCP and UDP live here |
| 3 | **Network** | Logical addressing and routing — IP |
| 2 | **Data Link** | Node-to-node delivery — MAC addressing, frames, switches |
| 1 | **Physical** | Raw bits on the wire — cables, signals, connectors |

**The two transport protocols:**

| Protocol | Meaning |
|---|---|
| **TCP** — Transmission Control Protocol | Reliable, connection-oriented delivery — establishes a connection (3-way handshake), guarantees ordered, error-checked delivery |
| **UDP** — User Datagram Protocol | Fast, connectionless delivery — no guarantee of arrival or order; used when speed beats reliability (DNS, streaming, gaming) |

### 33. DNS Record Types

| Record | Meaning |
|---|---|
| **A** | IPv4 address(es) for the domain |
| **AAAA** | IPv6 address(es) for the domain |
| **CNAME** | Canonical Name — an alias pointing one domain name to another |
| **MX** | Mail Servers — the servers responsible for handling email for the domain |
| **SOA** | Start of Authority — the primary name server, admin email, and zone serial number |
| **TXT** | Text Records — arbitrary text, commonly used for SPF, DKIM, DMARC, and domain verification |

### 34. OSINT & Recon Tools

**Recommended workflow:**

```bash
# 1. Passive subdomain enumeration
subfinder -d target.com -all -silent -o subs.txt
assetfinder --subs-only target.com >> subs.txt
amass enum -passive -d target.com -o amass.txt
cat *.txt | sort -u > all_subs.txt

# 2. Resolve live hosts
cat all_subs.txt | dnsx -silent -o resolved.txt
cat resolved.txt | httpx -title -status-code -tech-detect -o live.txt

# 3. Enrich
#    - crt.sh + Shodan + Censys
#    - theHarvester
#    - Wayback / gau / waybackurls
#    - GitHub dorks

# 4. Active (only when authorized / in-scope)
#    - puredns bruteforce
#    - naabu / nmap
#    - katana / ffuf / nuclei
```

**The toolbox:**

| Tool | Purpose |
|---|---|
| `subfinder` | Fast passive subdomain enumeration |
| `assetfinder` | Find domains and subdomains related to a target |
| `amass` | In-depth attack surface mapping and asset discovery |
| `httpx` | Fast, multi-purpose HTTP toolkit for probing live hosts |
| `naabu` | Fast port scanner written in Go |
| `dnsx` | Fast, multi-purpose DNS toolkit for running DNS queries |
| `waybackurls` | Fetch known URLs from the Wayback Machine for a domain |
| `gau` | Fetch known URLs from AlienVault, Wayback Machine, and Common Crawl |
| `katana` | Next-generation crawling and spidering framework |
| `ffuf` | Fast web fuzzer for discovering hidden paths and files |
| `gobuster` | Brute-force URIs, DNS subdomains, and vhost names |
| `nuclei` | Fast, customizable vulnerability scanner based on YAML templates |
| `dirsearch` | Command-line web path scanner and brute-forcer |
| `wpscan` | Black-box WordPress vulnerability scanner |
| `arjun` | HTTP parameter discovery — finds hidden GET/POST parameters |
| `puredns` | Fast DNS resolution + bruteforce with resolvers |
| `alterx` | Subdomain permutation generator |
| `chaos` (ProjectDiscovery) | Public dataset of subdomains |
| `recon-ng` | Modular recon framework (Metasploit-style) |
| `spiderfoot` | Automated OSINT with 200+ modules |
| `theHarvester` | Collect emails, subdomains, hosts from public sources |
| `findomain` | Fast subdomain discovery using Certificate Transparency |
| `gitleaks` | Scan git repos for secrets and API keys |

**Google Dorks:**

```
site:*.target.com -www
site:target.com filetype:pdf OR filetype:env
site:target.com inurl:admin OR inurl:login
site:github.com "target.com" password OR api_key
```

**Shodan queries:**

```
hostname:target.com
org:"Target Company"
port:3389 org:"Target"
ssl.cert.subject.cn:target.com
```

**Quick commands:**

```bash
theHarvester -d target.com -b all
subfinder -d target.com -all -silent
amass enum -passive -d target.com
cat subs.txt | httpx -title -status-code -tech-detect
```

### 35. Hunting Web Apps (Online Recon Tools)

No-install browser tools that help at every stage of hunting — from domain intel to SSL testing. **Use them only against targets you are authorized to test.**

**WHOIS & Domain Information**

| Site | Purpose |
|---|---|
| [who.is](https://who.is/) | WHOIS lookup |
| [whois.domaintools.com](https://whois.domaintools.com/) | WHOIS lookup |
| [networking.ringofsaturn.com](https://networking.ringofsaturn.com/Tools/whois.php) | WHOIS lookup |
| [betterwhois.com](https://www.betterwhois.com/whois) | WHOIS lookup |

**DNS & Network Reconnaissance**

| Site | Purpose |
|---|---|
| [viewdns.info](https://viewdns.info/) | DNS & IP tools |
| [dnsdumpster.com](https://dnsdumpster.com/) | DNS enumeration |
| [crt.sh](https://crt.sh/) | Certificate search (subdomains) |
| [bgp.he.net](https://bgp.he.net/) | BGP & ASN toolkit |
| [securitytrails.com](https://securitytrails.com/) | DNS & domain recon |
| [digwebinterface.com](https://digwebinterface.com/) | DNS query interface |
| [mxtoolbox.com](https://mxtoolbox.com/) | Mail & DNS diagnostics (MX, SPF, blacklists) |

**Attack Surface & Specialized Search Engines**

| Site | Purpose |
|---|---|
| [netlas.io](https://netlas.io/) | Attack surface search |
| [search.censys.io](https://search.censys.io/) | Attack surface search |
| [shodan.io](https://www.shodan.io/) | IoT / exposed services search engine |
| [leakix.net](https://leakix.net/) | Leak & threat search |
| [criminalip.io](https://www.criminalip.io/) | Cyber threat search |
| [binaryedge.io](https://www.binaryedge.io/) | Attack surface search |
| [fullhunt.io](https://fullhunt.io/) | Attack surface search |

**OSINT & Target Profiling**

| Site | Purpose |
|---|---|
| [web.archive.org](https://web.archive.org/) | Historical archiving — old pages & endpoints |
| [crunchbase.com](https://www.crunchbase.com/) | Company OSINT |
| [peoplefinders.com](https://www.peoplefinders.com/) | People OSINT |
| [builtwith.com](https://builtwith.com/) | Technology profiling |
| [searchdns.netcraft.com](https://searchdns.netcraft.com/) | Site profiling |
| [osintframework.com](https://osintframework.com) | The master index — OSINT tools organized by category |

**Vulnerability Scanners & Pentesting Platforms**

| Site | Purpose |
|---|---|
| [pentest-tools.com](https://pentest-tools.com/) | Pentest platform |
| [cloud.projectdiscovery.io](https://cloud.projectdiscovery.io/) | Attack surface management |
| [detectify.com](https://detectify.com/) | DAST / vulnerability scanner |
| [intruder.io](https://www.intruder.io/) | Vulnerability scanner |
| [probely.com](https://probely.com/) | Web vulnerability scanner |
| [hostedscan.com](https://hostedscan.com/) | Hosted vulnerability scanner |
| [assetnote.io](https://assetnote.io/) | Attack surface management |

**Threat Intelligence & Reputation**

| Site | Purpose |
|---|---|
| [urlscan.io](https://urlscan.io/) | Sandbox & URL scanner |
| [virustotal.com](https://www.virustotal.com) | Malware & threat analysis |
| [urlvoid.com](https://www.urlvoid.com/) | Domain reputation |
| [abuseipdb.com](https://abuseipdb.com/) | IP reputation |

**Web Configuration & SSL Testing**

| Site | Purpose |
|---|---|
| [observatory.mozilla.org](https://observatory.mozilla.org/) | Web configuration scanner |
| [securityheaders.com](https://securityheaders.com/) | Security headers scanner |
| [ssllabs.com/ssltest](https://www.ssllabs.com/ssltest/) | SSL/TLS scanner |
| [hardenize.com](https://www.hardenize.com/) | Security posture scanner |

**API & Payload Testing**

| Site | Purpose |
|---|---|
| [payloadplayground.com](https://payloadplayground.com/) | Payload generation |
| [42crunch.com](https://42crunch.com/) | API security |

**General Utilities**

| Site | Purpose |
|---|---|
| [dropbox.com](https://www.dropbox.com/) | Cloud storage (exfil staging / payload hosting in tests) |
| [mail.tm](https://mail.tm) | Disposable email — useful for testing sign-up flows |

### 36. Common Ports & Protocols

| Port | Protocol | Purpose |
|---|---|---|
| 21 | **FTP** | File Transfer Protocol (unencrypted) |
| 22 | **SSH** | Secure Shell for remote encrypted access |
| 23 | **Telnet** | Unencrypted remote text communication |
| 25 | **SMTP** | Simple Mail Transfer Protocol (sending mail) |
| 53 | **DNS** | Domain Name System (maps names to IPs) |
| 80 | **HTTP** | Hypertext Transfer Protocol (unencrypted web) |
| 443 | **HTTPS** | HTTP Secure over TLS/SSL (encrypted web) |
| 445 | **SMB** | Server Message Block (file sharing and network access) |
| 3306 | **MySQL** | Standard default port for MySQL databases |
| 3389 | **RDP** | Remote Desktop Protocol (Windows remote desktop) |
| 69 | **TFTP** | Trivial File Transfer Protocol (UDP-based, simple transfer without auth) |
| 88 | **Kerberos** | Authentication protocol used widely in Windows Active Directory networks |
| 110 | **POP3** | Post Office Protocol v3 (email clients retrieve messages) |
| 123 | **NTP** | Network Time Protocol (clock synchronization) |
| 139 | **NetBIOS** | Older Windows session management |
| 143 | **IMAP** | Internet Message Access Protocol (email on a remote server) |
| 161 | **SNMP** | Simple Network Management Protocol (monitoring network devices) |
| 389 | **LDAP** | Lightweight Directory Access Protocol (directory lookup) |
| 636 | **LDAPS** | LDAP over TLS/SSL (secure directory access) |
| 1433 | **MSSQL** | Microsoft SQL Server database default port |
| 1521 | **Oracle DB** | Default listening port for Oracle Database |
| 5432 | **PostgreSQL** | Default listening port for PostgreSQL |
| 6379 | **Redis** | In-memory data store used as database, cache, and message broker |
| 8080 | **HTTP-Proxy / Alt-HTTP** | Common alternative port for web servers and proxies (e.g. Tomcat) |
| 8443 | **HTTPS-Alt** | Common secondary port for secure web servers and management interfaces |

---

## Part VI — Systems, Tooling & Mobile

### 37. Linux Commands

| Command | Purpose |
|---|---|
| `ls` | List directory contents |
| `ls -la` | List all files including hidden ones, with detailed permissions |
| `pwd` | Print current working directory |
| `cd` | Change current directory |
| `mkdir` | Create a new directory |
| `rmdir` | Remove an empty directory |
| `touch` | Create a new empty file or update file timestamps |
| `cp` | Copy files or directories |
| `mv` | Move or rename files or directories |
| `rm` | Remove files |
| `rm -rf` | Forcefully remove files and directories recursively |
| `cat` | Concatenate and display file content |
| `less` | View file content page by page |
| `head` | Display the first few lines of a file |
| `tail` | Display the last few lines of a file |
| `tail -f` | Follow file updates in real time |
| `nano` | Simple command-line text editor |
| `grep` | Search for patterns and text inside files |
| `find` | Search for files and directories matching specific criteria |
| `chmod` | Change file or directory permissions |
| `chown` | Change file or directory owner and group |
| `ps aux` | List all currently running processes |
| `top` | Display real-time system process and resource usage |
| `kill` | Terminate a process by its PID |
| `df -h` | Show disk space usage in human-readable format |
| `du -sh` | Show total disk usage of a specific file or directory |
| `tar` | Archive and compress or extract files |
| `curl` | Transfer data to or from a server using various protocols |
| `wget` | Download files from the web via command line |
| `sudo` | Execute a command with superuser (root) privileges |
| `clear` | Clear the terminal screen |

### 38. Bash Scripting Basics

**Getting started:**

- `chmod +x file.sh` — make the script executable
- `#!/bin/bash` — shebang (specifies the interpreter)

**Variables & arguments:**

| Syntax | Meaning |
|---|---|
| `variable_name=value` | Define a variable (no spaces around `=`) |
| `unset v_name` | Delete or unset a variable |
| `v_name=$(date)` | Command substitution — save command output to a variable |
| `$0` | Script name |
| `$1`, `$2` | Positional arguments passed to the script |
| `$#` | Number of arguments passed |
| `$@` | List of all arguments |
| `echo $?` | Exit status of the last command (0 = success) |

**Conditional operators:**

| Operator | Meaning |
|---|---|
| `-eq` / `==` | Equal to |
| `-ne` / `!=` | Not equal to |
| `-gt` | Greater than |
| `-ge` | Greater than or equal to |
| `-lt` | Less than |
| `-le` | Less than or equal to |
| `&&` / `-a` | Logical AND |
| `\|\|` / `-o` | Logical OR |

**If statement:**

```bash
if [ <test> ]; then
    <commands>
elif [ <test> ]; then
    <commands>
else
    <commands>
fi
```

**For loop:**

```bash
for i in 1 2 3; do echo "$i"; done
for i in $(seq 1 10); do echo "$i"; done
for i in {1..10}; do echo "$i"; done
```

**While loop:**

```bash
n=1
while [ $n -lt 10 ]; do
    echo "Hello $n"
    ((n++))
done
```

**Functions, arrays & redirection:**

```bash
# Functions
function_name() { <commands>; }
function_name    # call it

# Arrays
arr=("a" "b" "c")
echo ${arr[0]}      # first element
echo ${#arr[@]}     # number of elements

# Redirection
echo "Hello" > file.txt   # overwrite output to file
echo "Hello" >> file.txt  # append output to file
cat < file.txt            # read file as input
```

### 39. Nmap Scan Techniques & Options

**Scan types:**

| Flag | Meaning |
|---|---|
| `-sS` | TCP SYN Scan — stealth scan, does not complete the 3-way handshake |
| `-sU` | UDP Scan — scans UDP ports like DNS and DHCP |
| `-sT` | TCP Connect Scan — completes the full connection, used without root privileges |
| `-F` | Fast Scan — scans the top 100 ports |
| `-sV` | Version Detection — detects service/software name and version on open ports |
| `-O` | OS Detection — attempts to identify the operating system |
| `-sO` | IP Protocol Scan — scans IP protocols instead of ports |

**Output & behavior:**

| Flag | Meaning |
|---|---|
| `-oN` | Normal output — saves results to a plain text file |
| `-oX` | XML output |
| `-oA` | Output all formats (normal, XML, grepable) at once |
| `-v` | Verbose — shows real-time results during the scan |
| `-A` | Aggressive scan — OS detection + version detection + script scanning + traceroute |
| `-T0` to `-T5` | Timing templates — adjusts scan speed (default/recommended is `-T4`) |

**Targets & general options:**

| Flag | Meaning |
|---|---|
| `-iL targets.txt` | Input list of targets from a file |
| `-iR 100` | Random targets scan |
| `--exclude 1.1.1.1` | Excludes specific hosts/IPs from the scan |
| `-sL` | List scan — lists target IPs without sending packets to ports |
| `-sn 192.168.1.0/24` | Ping scan — checks which hosts are online without scanning ports |
| `-Pn` | Treat all hosts as online / skip host discovery (useful when firewalls block ping) |
| `--traceroute` | Traces the network path to the target |
| `-p` | Specify port(s) to scan |
| `-p-` | Scan all ports (1 to 65535) |
| `--script vuln` | Scans the target for known vulnerabilities using NSE scripts |

### 40. Curl Common Options & Flags

| Flag | Meaning |
|---|---|
| `-I` / `--head` | Fetch headers only (does not download the body) |
| `-i` / `--include` | Include response headers along with the response body |
| `-v` / `--verbose` | Verbose mode — shows full request, response, and handshake details |
| `-L` / `--location` | Follow HTTP redirects automatically |
| `-X` / `--request` | Specify a custom HTTP method (GET, POST, PUT, DELETE) |
| `-d` / `--data` | Send data in a POST request (e.g. `-d "param=value"`) |
| `-H` / `--header` | Pass custom headers (e.g. `-H "Authorization: Bearer <token>"`) |
| `-u` / `--user` | User credentials for Basic Authentication (`user:password`) |
| `-b` / `--cookie` | Send cookies as a string or load them from a file |
| `-c` / `--cookie-jar` | Save received cookies to a file |
| `-o` / `--output` | Write output to a specific file instead of stdout |
| `-O` / `--remote-name` | Save the file using its remote name from the URL |
| `-k` / `--insecure` | Allow insecure SSL/TLS connections (bypasses certificate checks) |
| `-s` / `--silent` | Silent mode — no progress meter or error messages |
| `-x` / `--proxy` | Route traffic through an HTTP/SOCKS proxy (e.g. `-x 127.0.0.1:8080`) |

### 41. JADX & Mobile Testing

**How to use:** open the decompiled APK in JADX, press `Ctrl + Shift + F` (global search), then search the keyword groups below one category at a time. Each group surfaces a different type of sensitive information.

**What to search for, by category:**

| Category | Keywords | What You'll Find |
|---|---|---|
| **Endpoints & API paths** | `https://` · `http://` · `/api/` · `/v1/` `/v2/` `/v3/` `/v4/` · `/graphql` | Backend URLs and API routes the app talks to |
| **API config constants** | `BASE_URL` · `API_URL` · `ENDPOINT` · `BuildConfig` | Hardcoded server addresses baked in at build time |
| **Cloud storage & BaaS** | `s3.amazonaws.com` · `s3://` · `amazonaws` · `Bucket` · `putObject` · `Presigned` · `storage.googleapis.com` · `blob.core.windows.net` · `firebaseio.com` · `supabase.co` · `execute-api.cloudfront.net` | S3/GCS/Azure storage usage, pre-signed URLs, Firebase/Supabase backends |
| **Auth tokens & secrets** | `Authorization` · `Bearer` · `X-Api-Key` · `apiKey` · `secret` | Where the app carries credentials and secrets |
| **Real-time & messaging** | `wss://` · `ws://` · `socket.io` · `Socket` · `WebSocket` · `mqtt://` · `mqtts://` · `MQTT` | WebSocket and MQTT connections (often unauthenticated) |
| **GraphQL** | `query {` · `mutation {` · `graphql` | Embedded GraphQL operations |
| **Webhooks & OAuth** | `webhook` · `callback` · `oauth` · `redirect_uri` | Callback URLs and OAuth flows worth probing |
| **Deep links** | `intent://` · `app://` · `scheme` | Custom URL schemes and intent handlers |
| **Hidden environments** | `staging` · `sandbox` · `dev.` · `beta` · `uat` · `internal` · `test` | Non-production servers, often with weaker security |
| **Config & sensitive files** | `.json` · `.xml` · `.env` · `.pem` · `.key` · `.sqlite` · `config` | Bundled config files, private keys, local databases |
| **Crypto usage** | `AES` · `DES` · `HMAC` · `SHA256` · `MD5` · `SecretKey` · `IvParameterSpec` | Where the app does encryption — look for weak algorithms and hardcoded keys |

**API key prefixes — identify the provider on sight:**

| Prefix(es) | Belongs To |
|---|---|
| `AIza` | Google API keys |
| `AKIA` / `ASIA` | AWS access key IDs |
| `sk_live_` / `pk_live_` / `rk_live_` | Stripe live keys (secret / publishable / restricted) |
| `rzp_live_` | Razorpay live keys |
| `SG.` | SendGrid API keys |
| `ghp_` / `gho_` | GitHub tokens (personal access / OAuth) |
| `glpat-` | GitLab personal access tokens |
| `xoxb-` / `xoxp-` | Slack tokens (bot / user) |
| `eyJ` | JWT tokens (Base64 of the `{"` header) |
| `key-` / `pk.` | Generic API key prefixes seen across mail/API services |

### 42. Quick Tips

**IP spoofing via headers** (worth testing on targets — some backends trust these):

```
X-Forwarded-For: 127.0.0.1
Client-IP: 127.0.0.1
X-Client-IP: 127.0.0.1
```

### 43. Understanding Version Numbers (SemVer)

Most software releases follow **Semantic Versioning (SemVer)** — three numbers separated by dots:

```
MAJOR . MINOR . PATCH
```

**Example: `14.22.1`**

| Number | Part | Meaning |
|---|---|---|
| **14** | **Major** | Big releases with breaking changes — new features that change how the software works, may not be compatible with older versions |
| **22** | **Minor** | New features added **without** breaking anything — backward compatible |
| **1** | **Patch** | Small fixes — bug fixes and **security patches** |

**Why it matters in security:**

- Version numbers tell you **how outdated** a product is — e.g. the `Server: nginx/1.15.8` header in an HTTP response
- **CVEs apply to specific version ranges** — knowing the exact version tells you which known vulnerabilities might work
- An old **Major** number usually means the software has missed many fixes → higher chance of known vulnerabilities

### 44. Free Practice Server: Segfault (THC)

[Segfault](https://www.thc.org/segfault) — a project by **The Hacker's Choice** — gives you a **free, disposable root server** for legal security testing and practice. A fresh VM is created for **every SSH connection**, preloaded with Kali-style tooling, with VPN-routed egress and transparent Tor support.

```bash
ssh root@segfault.net
# password: segfault
```

**How it works:**

1. Connect with the shared password: `segfault`
2. Wait ~60 seconds and press Enter — the system generates a **unique secret** for your session
3. **Keep that secret** — it's how you reconnect to *your* instance (nobody else can access it — the shared password only creates new servers)

**Good for:** a free Kali-like VPS · a SOCKS proxy (`ssh -D 30314 root@segfault.net`) · safely testing attacks and tools. Servers are **disposable** — everything is wiped when you disconnect, so treat it as a scratch environment. Legal practice only.

### 45. Suggested Learning Path

These fundamentals map to a practical progression:

1. **Linux fundamentals** — the operating system every security professional needs (TryHackMe's Linux path is a great start)
2. **Vulnerabilities** — deep-diving into vulnerability classes one by one (web, network, mobile...)
3. Pick **one field** from [section 1](#1-the-18-cybersecurity-fields) that fits your strengths and go deep

---

## License

This repository is released under the [MIT License](LICENSE) — use it, share it, and build on it freely.

## Disclaimer

This material is for **educational purposes** only. Anything you learn here must only be applied legally — with permission, within scope, on systems you own or are authorized to test.
