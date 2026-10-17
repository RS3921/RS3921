<div align="center">

```text
 ____   ____   _____   ___   ____   _ 
|  _ \ / ___| |___ /  / _ \ |___ \ / |
| |_) |\___ \   |_ \ | (_) |  __) || |
|  _ <  ___) | ___) | \__, | / __/ | |
|_| \_\|____/ |____/    /_/ |_____||_|
   > security operations // investigations // detection
```

# Raveena Sharma

**Security Operations Intern · Investigations · Vulnerability Management · Threat Management**

![CGPA](https://img.shields.io/badge/CGPA-9.0%2F10-2ea44f?style=flat-square)
![TryHackMe](https://img.shields.io/badge/TryHackMe-Top%2015%25%20Global-212C42?style=flat-square&logo=tryhackme&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-19%20Skill%20Badges-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Cisco](https://img.shields.io/badge/Cisco%20Ethical%20Hacker-In%20Progress-049fd9?style=flat-square&logo=cisco&logoColor=white)
![Focus](https://img.shields.io/badge/Focus-SOC%20%7C%20DFIR%20%7C%20VAPT-d73a4a?style=flat-square)
![Status](https://img.shields.io/badge/Status-Open%20to%20Internships-0969da?style=flat-square)

[LinkedIn](https://linkedin.com/in/raveena-sharma-csit) · [TryHackMe](https://tryhackme.com/p/raveenasharma392) · [Email](mailto:raveenasharma3921@gmail.com)

</div>

---

## About Me

I'm a final-year Cyber Security student in Pune who is most interested in the moment after something has gone wrong: working out what happened, how far it spread and what should be done next. I triage alerts, follow evidence through logs and disk images, break things with VAPT tooling, and then build the systems that would have stopped it.

I'm looking for a security operations internship where I can work across investigations, vulnerability management and threat management, and keep learning from people who do this every day.

---

## Case File: RS-3921

> [!IMPORTANT]
> **CASE RS-3921 &nbsp;·&nbsp; STATUS: OPEN** &nbsp;·&nbsp; Subject is actively seeking a security operations internship.

| | |
|---|---|
| **Subject** | Raveena Sharma, B.Tech CS&IT (Cyber Security), Symbiosis Skills and Professional University, Pune (2023 to 2027) |
| **Seeking** | Security operations internship across investigations, vulnerability management and threat management |
| **Most recent assignment** | R&D Lead Intern, OffSecDiary (Jan to Jul 2026) |
| **Current assignment** | Cloud Security & Innovation Lead, AWS Student Builder Club (2026 to 27) |

**Evidence on file**

| Exhibit | Finding | Where to look |
|---|---|---|
| **A** | Designed an enterprise DLP prototype with an ML module that cuts false-positive alerts | [Featured Builds](#featured-builds) |
| **B** | Led a portfolio of 6 security research projects over 7 months | [Journey So Far](#journey-so-far) |
| **C** | Competitive record in CTFs and on TryHackMe | [CTF and Competition Record](#ctf-and-competition-record) |
| **D** | Certifications completed, in progress and being explored | [Certifications and Learning Path](#certifications-and-learning-path) |

---

## My Alert Triage Pipeline

How I work an alert, from first signal to a decision someone can act on:

```mermaid
flowchart LR
    A["Alert fires in SIEM (Splunk)"] --> B{"Is it a known false positive?"}
    B -- Yes --> C["Document and tune the rule"]
    B -- No --> D["Extract IOCs: IP, hash, domain, URL"]
    D --> E["Enrich with VirusTotal and AbuseIPDB"]
    E --> F["Check logs and Windows Event IDs for context"]
    F --> G["Map behavior to MITRE ATT&CK technique"]
    G --> H{"Confirmed malicious?"}
    H -- No --> I["Close with written reasoning"]
    H -- Yes --> J["Contain and preserve evidence"]
    J --> K["Forensic analysis: Autopsy, FTK Imager, Wireshark"]
    K --> L["Report, lessons learned, new detection rule"]
    C --> M(["Feedback loop"])
    I --> M
    L --> M
    M --> A
```

---

## Skills Mapped to the Attack Lifecycle

I organize what I know the way an adversary operates, so every skill answers a real question: *where does this stop the attacker?*

| Phase | Question I answer | What I use |
|---|---|---|
| **Reconnaissance** | What does the attacker see? | Nmap, Kali Linux, DNS, TCP/IP, HTTP/HTTPS |
| **Vulnerability discovery** | What can be exploited? | Nessus, Burp Suite, OWASP ZAP, OWASP Top 10, risk assessment |
| **Exploitation** | Is it really exploitable? | Metasploit, Hydra, John the Ripper, Hashcat |
| **Detection** | Can we see it happening? | Splunk, IDS/IPS, MITRE ATT&CK, IOC/IOA/TTP analysis, threat hunting fundamentals |
| **Investigation** | What actually happened? | Autopsy, FTK Imager, Wireshark, Windows Event and log analysis |
| **Response** | How do we contain and recover? | Incident response, alert triage, evidence preservation |
| **Prevention** | How do we stop it next time? | DLP, Zero Trust, Secure SDLC, cryptography, GDPR, PCI-DSS, HIPAA, DPDP Act |
| **Build** | How do I ship secure software? | Python, C/C++, JavaScript/TypeScript, React, Next.js, REST APIs, MongoDB, PostgreSQL, Prisma, Git/GitHub, GCP |

---

## Featured Builds

Security work that ships as code, not slides.

### Cybersecurity Portfolio

*Secure, database-backed web application*

A full-stack portfolio built with Next.js 14, React, TypeScript and PostgreSQL (Prisma), with a protected admin editor so content can be updated without touching code. Security is part of how it works, not an add-on: signed HTTP-only session cookies, bcrypt hashing, rate limiting, CSP and security headers, audit logging, and a file-upload endpoint that checks both MIME type and file signature.

```mermaid
flowchart TB
    V["Visitor"] --> RL
    AD["Admin"] --> RL

    subgraph EDGE["Applied to every request"]
        RL["Rate limiting"] --> HD["CSP and security headers"]
    end

    HD --> PG["Public pages"]
    HD --> LG["Admin login"]

    subgraph APP["Next.js 14 application"]
        PG
        LG
        S["Signed HTTP-only session cookie"]
        ED["Protected admin editor"]
        UP["File-upload endpoint"]
        LG -->|"bcrypt password check"| S
        S --> ED
        ED --> UP
    end

    UP --> C1{"MIME type allowed?"}
    C1 -- No --> X["Upload rejected"]
    C1 -- Yes --> C2{"File signature matches?"}
    C2 -- No --> X
    C2 -- Yes --> OK["Upload stored"]

    subgraph DATA["Data layer"]
        DB[("PostgreSQL via Prisma")]
        AU[("Audit log")]
    end

    PG -->|"reads content"| DB
    ED -->|"no-code content updates"| DB
    LG -.->|"records attempts"| AU
    ED -.->|"records changes"| AU

    classDef bad fill:#ffebe9,stroke:#cf222e,color:#1f2328
    classDef good fill:#dafbe1,stroke:#2ea44f,color:#1f2328
    class X bad
    class OK good
```


### Sovereign On-Premise Agentic AI Workbench

*Smart India Hackathon 2026, MRPL*

An air-gapped, self-hosted AI workbench for confidential industrial data, being built with zero external network calls and zero-trust principles. A multi-model backend auto-selects the right open-weight LLM per task, with local tool use, planning and OCR/vision.

```mermaid
flowchart TB
    subgraph AIRGAP["Air-gapped environment: zero external network calls"]
        U["Engineer"] --> GW["Gateway with authentication"]
        GW --> RT["Task router"]
        RT --> L1["Open-weight LLM A"]
        RT --> L2["Open-weight LLM B"]
        RT --> L3["Vision and OCR model"]
        L1 --> T["Local tools and planning"]
        L2 --> T
        L3 --> T
        T --> DATA[("Confidential industrial data")]
    end
    NET["Internet"] -. "blocked" .-x AIRGAP
```


### SAT-SA: Supervisory Analytics Tool

*Final-year major project, Smart India Hackathon*

An offline, explainable analytics platform that assesses case-management and process data across Critical Sector Entities and highlights execution gaps. Guided by Dr. Rudresh Shirwaikar, Director of CSIT.

```mermaid
flowchart LR
    D["Case-management and process data"] --> P["Offline preprocessing"]
    P --> R["Rule-based checks"]
    P --> ML["ML risk model"]
    R --> H["Hybrid scoring engine"]
    ML --> H
    H --> S["Entity-level risk scores"]
    S --> Q["Prioritized sample queue"]
    Q --> X["Expert review"]
    H --> W["Explanations: why this entity scored high"]
    W --> X
```

A risk score nobody can explain is a score nobody trusts, so every output ships with its reasoning.


### AI-Driven Pre-Transaction Fraud Risk Warning System for UPI

*Final-year team project*

Warns the user before the money moves. It analyzes payment messages, URLs, QR codes and transaction features, then gives an explainable Safe, Suspicious or High-Risk verdict. Backed by a review of 15 research papers across ML, GNN, NLP/BERT and deep learning for financial fraud detection. Guided by Dr. Rudresh Shirwaikar, Director of CSIT.

```mermaid
flowchart LR
    I1["Payment message"] --> NLP["NLP / BERT analysis"]
    I2["URL"] --> UR["URL risk analysis"]
    I3["QR code"] --> QR["QR decode and check"]
    I4["Transaction features"] --> GN["GNN and ML scoring"]
    NLP --> F["Fusion and explanation layer"]
    UR --> F
    QR --> F
    GN --> F
    F --> V{"Verdict"}
    V --> S["Safe"]
    V --> SU["Suspicious"]
    V --> HR["High-Risk"]
```


### Data Loss Prevention (DLP) System

*Endpoint agent, dashboard and ML detection*

An enterprise DLP prototype with a Windows endpoint agent, an admin dashboard and Active Directory-ready policy mapping, built during my R&D Lead internship at OffSecDiary.

- Per-device agent tokens so every endpoint is individually authenticated
- Real-time monitoring that flags unauthorized data movement
- An ML-based malicious-behavior detection module that cuts false positives in alerts

```mermaid
sequenceDiagram
    autonumber
    participant U as User / Process
    participant A as Windows Endpoint Agent
    participant S as Policy and Detection Server
    participant M as ML Behavior Module
    participant D as Admin Dashboard
    participant R as Security Analyst

    A->>S: Authenticate with per-device token
    U->>A: Copies file / writes to USB / uploads
    A->>S: Stream activity event
    S->>S: Match against AD-mapped policy
    S->>M: Score behavior for maliciousness
    M-->>S: Risk score
    alt High risk and policy violation
        S->>D: Raise alert with context
        D->>R: Notify for review
        R->>D: Confirm or mark false positive
    else Benign
        S->>S: Log only, no alert
    end
```

A rule-only DLP drowns analysts in noise. Scoring behavior before alerting is what keeps it usable.


### Symbiotic Chunk Storage (SCS)

*Secure distributed storage*

Distributed storage designed so no single node can read your data, no single failure can lose it, and deletion is provable.

- **Confidentiality:** AES-256-GCM encryption
- **Fault tolerance:** Reed-Solomon erasure coding
- **Integrity:** Merkle proofs plus cross-chain anchoring for tamper evidence
- **Resilience:** autonomous healing of lost shards
- **Compliance:** crypto-shredding for GDPR / HIPAA-aligned data deletion

```mermaid
flowchart TB
    F["Original file"] --> E["Encrypt with AES-256-GCM"]
    E --> C["Split into chunks"]
    C --> RS["Reed-Solomon erasure coding"]
    RS --> N1["Node 1"]
    RS --> N2["Node 2"]
    RS --> N3["Node 3"]
    RS --> N4["Node N"]
    C --> MT["Build Merkle tree"]
    MT --> AN["Anchor root across chains"]
    N2 -. "node lost" .-> H["Autonomous healing rebuilds shard"]
    H --> N2
    K["Delete the encryption key"] --> X["Crypto-shredding: data becomes unreadable everywhere"]
```


### Unified Operations Center

*Employee management system, team project*

A full-stack employee management platform built by a team using Next.js, React, TypeScript and MongoDB. I contributed to the calendar and event-tracking modules and the performance analytics dashboard, and to securing the platform with JWT in HTTP-only cookies, bcrypt hashing, role-based access control and input validation.

**How a request is guarded**

```mermaid
flowchart LR
    subgraph UI["Frontend: Next.js, React, TypeScript"]
        CAL["Calendar module"]
        EVT["Event tracking module"]
        DASH["Performance analytics dashboard"]
    end

    subgraph GUARD["API security pipeline"]
        G1{"Valid JWT in HTTP-only cookie?"}
        G2{"Role allowed for this action?"}
        G3["Input validation"]
        H["Request handler runs"]
        G1 -- Yes --> G2
        G2 -- Yes --> G3
        G3 --> H
    end

    CAL --> G1
    EVT --> G1
    DASH --> G1
    G1 -- No --> R1["401 Unauthorized"]
    G2 -- No --> R2["403 Forbidden"]
    H --> DB[("MongoDB")]

    classDef bad fill:#ffebe9,stroke:#cf222e,color:#1f2328
    class R1,R2 bad
```

**How a user gets in**

```mermaid
sequenceDiagram
    autonumber
    participant U as Employee
    participant W as Next.js app
    participant DB as MongoDB

    U->>W: Submit credentials
    W->>DB: Fetch user record
    DB-->>W: Password hash and role
    W->>W: Compare password using bcrypt
    W-->>U: Set JWT in HTTP-only cookie
    Note over U,W: Script on the page cannot read the cookie
    U->>W: Later requests carry the cookie automatically
    W->>W: Verify JWT, then check role permissions
```


---

## Journey So Far

Internships, leadership roles and everything in between, in one place:

```mermaid
timeline
    title Experience and Leadership Timeline
    2023 : B.Tech in Cyber Security begins at SSPU
         : Class Representative 2023 to 24
         : Internship Coordinator 2023 to 24 and again 2025 to 27
    2024 : Cloud Computing Intern at YHills from Jun to Jul using Microsoft Azure
         : AI Intern at Corizo from Oct to Dec applying ML to anomaly and threat detection
    2025 : Web Developer Intern at BloggersCon Vision from Jun to Jul
         : Smart India Hackathon Internal Coordinator 2025 and 2026
         : Senior Management Head at 0x0 PIR4T3S Club from Oct 2025 to Apr 2026 running CTFs and workshops
    2026 : R&D Lead Intern at OffSecDiary from Jan to Jul leading 6 research projects
         : Cloud Security and Innovation Lead at AWS Student Builder Club SSPU Core Team 2026 to 27
    2027 : Graduation
```

Off the timeline: I'm also a **Session Anchor** for SSPU conferences and events, and a volunteer on the **HICA SSPU Team**, which hosted a Low-Code/No-Code session.

### Academic Trajectory

```mermaid
xychart-beta
    title "CGPA by year (out of 10)"
    x-axis ["Year 1", "Year 2", "Year 3"]
    y-axis "CGPA" 8 --> 10
    bar [8.76, 9.06, 9.21]
    line [8.76, 9.06, 9.21]
```

Each year better than the last. That is also how I approach every skill.

---

## CTF and Competition Record

| Event | Result |
|---|---|
| **X'PLOITATHON CTF 2026** | Qualified for Round 2 (Round 1: rank 11 of 175, Round 2: rank 22 of 50) |
| **Bypass CTF** | Ranked 20th |
| **MumbaiHacks** | Qualified for Round 2 |
| **TryHackMe** | Top 15% globally |

---

## Certifications and Learning Path

What I have finished, what I am working through now, and what I am picking up next:

```mermaid
flowchart LR
    DONE["COMPLETED<br/><br/>Cybersecurity Career Starter<br/>Certification (CCSC)<br/><br/>Introduction to Cloud Security<br/>Simplilearn<br/><br/>Google Cloud Study Jams 2025<br/>19 Official Skill Badges<br/>Gen AI Arcade Certification<br/><br/>Udemy: The Complete<br/>Ethical Hacking Course<br/><br/>Udemy: Python Mega Course<br/>Build 20 Apps<br/><br/>Data Structures and Algorithms<br/>AllCSNotes<br/><br/>TryHackMe: PreSecurity"]
    ONGOING["IN PROGRESS<br/><br/>Cisco Ethical Hacker<br/><br/>TryHackMe: Cyber Security 101<br/><br/>TryHackMe: Jr Penetration<br/>Tester path"]
    LEARN["EXPLORING<br/>basic knowledge<br/><br/>Wazuh (SIEM/XDR)<br/><br/>ELK Stack<br/><br/>Microsoft Sentinel<br/><br/>Security Onion<br/>(Network Security Monitoring)<br/><br/>Suricata (IDS/IPS)"]
    DONE --> ONGOING --> LEARN

    classDef done fill:#dafbe1,stroke:#2ea44f,color:#1f2328
    classDef prog fill:#fff8c5,stroke:#bf8700,color:#1f2328
    classDef next fill:#ddf4ff,stroke:#0969da,color:#1f2328
    class DONE done
    class ONGOING prog
    class LEARN next
```

---

## `security.txt`

Because a security person's contact page should be a disclosure policy:

```text
Contact:     mailto:raveenasharma3921@gmail.com
Contact:     https://linkedin.com/in/raveena-sharma-csit
Expires:     2027-12-31T23:59:59.000Z
Preferred-Languages: en, hi
Canonical:   https://github.com/RS3921
Policy:      Internships, research collaboration, CTF teams and
             security-project ideas are all in scope.
Hiring:      Open to SOC / DFIR / VAPT internship opportunities.
```

---

<div align="center">

```text
 [ detect ]  ->  [ investigate ]  ->  [ respond ]  ->  [ build it better ]
```

*Every incident is a lesson. Every lesson becomes a detection rule.*

</div>
