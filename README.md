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
![Focus](https://img.shields.io/badge/Focus-SOC%20%7C%20DFIR%20%7C%20VAPT-d73a4a?style=flat-square)
![Status](https://img.shields.io/badge/Status-Open%20to%20Internships-0969da?style=flat-square)

[LinkedIn](https://linkedin.com/in/raveena-sharma-csit) · [TryHackMe](https://tryhackme.com/p/raveenasharma392) · [Email](mailto:raveenasharma3921@gmail.com)

</div>

---

## `$ whoami`

Final-year B.Tech (Cyber Security) student in Pune who thinks like a defender and tests like an attacker. I triage alerts, chase evidence through logs and disk images, break things with VAPT tooling, and then build the systems that would have stopped it.

Instead of a bullet list of adjectives, here is my profile as code:

```python
from dataclasses import dataclass, field

@dataclass
class Analyst:
    name: str = "Raveena Sharma"
    base: str = "Pune, India"
    degree: str = "B.Tech CS&IT (Cyber Security), SSPU, 2027"
    cgpa: float = 9.0
    thm_rank: str = "Top 15% globally"
    toolbox: dict = field(default_factory=lambda: {
        "investigate": ["Autopsy", "FTK Imager", "Wireshark", "Windows Event Logs"],
        "assess":      ["Nessus", "Nmap", "Burp Suite", "OWASP ZAP", "Metasploit"],
        "detect":      ["Splunk", "VirusTotal", "AbuseIPDB", "MITRE ATT&CK", "IDS/IPS"],
        "build":       ["Python", "TypeScript", "Next.js", "PostgreSQL", "MongoDB"],
    })

    def triage(self, alert):
        """Enrich -> map to ATT&CK -> decide: close, escalate, or contain."""
        ioc = self.enrich(alert, sources=["VirusTotal", "AbuseIPDB"])
        return self.map_to_attack(ioc).verdict()

    def investigate(self, incident):
        """Preserve evidence first. Always. Then timeline, then conclusions."""
        image = self.acquire(incident, tool="FTK Imager")
        return self.analyze(image, tool="Autopsy").build_timeline()

    def assess(self, target):
        """Scan, validate manually, rate the risk, write it so a human can act on it."""
        findings = self.scan(target, tools=["Nmap", "Nessus"]).validate(by_hand=True)
        return findings.rank_by_risk().write_report()

    def hunt(self, hypothesis):
        """Start from a TTP, not from an alert."""
        return self.query_siem(hypothesis, platform="Splunk").pivot_on_iocs()

    def build(self, problem):
        """If the tool I need does not exist, I make a prototype."""
        return self.prototype(problem, security_by_design=True)

    def learn(self):
        while True:
            self.practice(["TryHackMe: Jr Pentester", "Cisco Ethical Hacker"])
            self.explore(["Wazuh", "ELK", "Sentinel", "Security Onion", "Suricata"])

me = Analyst()
```

---

## Case File: RS-3921

| Field | Detail |
|---|---|
| **Subject** | Raveena Sharma |
| **Role sought** | Security Operations Internship (Investigations / Vulnerability Mgmt / Threat Mgmt) |
| **Last role** | R&D Lead Intern, OffSecDiary (led 6 research projects over 7 months) |
| **Known techniques** | Alert triage, DFIR, VAPT, SIEM querying, threat hunting fundamentals |
| **Known aliases** | R&D Lead, Cloud Security & Innovation Lead, Senior Management Head |
| **Weakness** | Cannot leave a half-finished lab unsolved |
| **Status** | Active. Learning. Shipping. |

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
| **Reconnaissance** | What does the attacker see? | Nmap, Kali Linux, DNS / TCP-IP fundamentals |
| **Vulnerability discovery** | What can be exploited? | Nessus, Burp Suite, OWASP ZAP, OWASP Top 10 |
| **Exploitation** | Is it really exploitable? | Metasploit, Hydra, John the Ripper, Hashcat |
| **Detection** | Can we see it happening? | Splunk, IDS/IPS, MITRE ATT&CK, IOC/IOA/TTP analysis |
| **Investigation** | What actually happened? | Autopsy, FTK Imager, Wireshark, Windows Event Analysis |
| **Response** | How do we contain and recover? | Incident response, alert triage, evidence preservation |
| **Prevention** | How do we stop it next time? | DLP, Zero Trust, Secure SDLC, GDPR / PCI-DSS / HIPAA / DPDP |

```mermaid
mindmap
  root((Raveena))
    Investigations
      Digital Forensics
      Incident Response
      Log and Event Analysis
      Network Traffic Analysis
    Vulnerability Mgmt
      VAPT
      Risk Assessment
      Web App Security
      Ethical Hacking
    Threat Mgmt
      SIEM Splunk
      Threat Hunting
      MITRE ATTACK
      DLP
    Builder
      Python and TypeScript
      Next.js and React
      PostgreSQL and MongoDB
      GCP and Azure
    Governance
      GDPR
      HIPAA
      PCI-DSS
      DPDP Act
```

---

## Featured Builds

Security work that ships as code, not slides. Each project below is expandable.

<details>
<summary><b>Data Loss Prevention (DLP) System</b> &nbsp;|&nbsp; endpoint agent + dashboard + ML detection</summary>

<br>

An enterprise DLP prototype with a Windows endpoint agent, an admin dashboard, and Active Directory-ready policy mapping. Built during my R&D Lead internship at OffSecDiary.

**What it does**
- Per-device agent tokens so every endpoint is individually authenticated
- Real-time monitoring that flags unauthorized data movement
- ML-based malicious-behavior detection that cuts false positives in alerts

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

**Why the ML layer matters:** a rule-only DLP drowns analysts in noise. Scoring behavior before alerting is what makes the tool usable at 3 AM.

</details>

<details>
<summary><b>Symbiotic Chunk Storage (SCS)</b> &nbsp;|&nbsp; secure distributed storage</summary>

<br>

Distributed storage designed so that no single node can read your data, no single failure can lose it, and deletion is provable.

- **Confidentiality:** AES-256-GCM encryption
- **Fault tolerance:** Reed-Solomon erasure coding
- **Integrity:** Merkle proofs plus cross-chain anchoring for tamper evidence
- **Resilience:** autonomous healing of lost shards
- **Compliance:** crypto-shredding for GDPR / HIPAA-aligned deletion

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

</details>

<details>
<summary><b>SAT-SA: Supervisory Analytics Tool</b> &nbsp;|&nbsp; Final-year major project, Smart India Hackathon</summary>

<br>

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

**Design principle:** a risk score nobody can explain is a score nobody trusts. Every output ships with its reasoning.

</details>

<details>
<summary><b>AI-Driven Pre-Transaction Fraud Risk Warning System for UPI</b></summary>

<br>

Stops the user before the money moves. Analyzes payment messages, URLs, QR codes and transaction features, then gives an explainable verdict. Backed by a review of 15 research papers across ML, GNN, NLP/BERT and deep learning for financial fraud detection.

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

</details>

<details>
<summary><b>Sovereign On-Premise Agentic AI Workbench</b> &nbsp;|&nbsp; Smart India Hackathon 2026, MRPL</summary>

<br>

An air-gapped, self-hosted AI workbench for confidential industrial data. Zero external network calls, designed on zero-trust principles.

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

The router auto-selects the right model per task, so you get capability without sending a single byte outside the plant.

</details>

<details>
<summary><b>Secure Web Applications</b> &nbsp;|&nbsp; Cybersecurity Portfolio and Unified Operations Center</summary>

<br>

Two full-stack apps where security was a requirement from commit one, not a patch at the end. Stack: Next.js, React, TypeScript, PostgreSQL (Prisma) and MongoDB.

```mermaid
flowchart TB
    R["Incoming request"] --> L1["Layer 1: Rate limiting"]
    L1 --> L2["Layer 2: CSP and security headers"]
    L2 --> L3["Layer 3: Input validation"]
    L3 --> L4["Layer 4: Signed HTTP-only session cookie (JWT)"]
    L4 --> L5["Layer 5: Role-based access control"]
    L5 --> L6["Layer 6: bcrypt-hashed credentials"]
    L6 --> L7["Layer 7: Audit logging"]
    L7 --> APP["Application logic"]
    UP["File upload"] --> V1["MIME check"] --> V2["Signature check"] --> APP
```

</details>

---

## Journey So Far

```mermaid
timeline
    title Experience Timeline
    2023 : Started B.Tech in Cyber Security at SSPU
    2024 : Cloud Computing Intern at YHills using Azure
         : AI Intern at Corizo applying ML to anomaly and threat detection
    2025 : Web Developer Intern at BloggersCon Vision
         : Google Cloud Study Jams with 19 skill badges
         : Senior Management Head at 0x0 PIR4T3S Club
    2026 : R&D Lead Intern at OffSecDiary leading 6 research projects
         : X'PLOITATHON CTF Round 2 qualifier
         : Smart India Hackathon 2026
         : Cloud Security and Innovation Lead at AWS Student Builder Club
    2027 : Graduation and full-time security career
```

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

## Currently Leveling Up

```mermaid
stateDiagram-v2
    direction LR
    [*] --> Foundations
    Foundations: Foundations done
    Foundations --> InProgress
    state InProgress {
        direction TB
        THM: TryHackMe Cyber Security 101 and Jr Pentester path
        CEH: Cisco Ethical Hacker
    }
    InProgress --> NextUp
    state NextUp {
        direction TB
        W: Wazuh SIEM and XDR
        E: ELK Stack
        MS: Microsoft Sentinel
        SO: Security Onion
        SU: Suricata IDS and IPS
    }
    NextUp --> [*]
```

**Certifications:** CCSC · Introduction to Cloud Security (Simplilearn) · Google Cloud Study Jams 2025 (19 skill badges + Gen AI Arcade) · Cisco Ethical Hacker (in progress) · Udemy Ethical Hacking · TryHackMe PreSecurity

---

## Beyond the Terminal

- **Cloud Security & Innovation Lead**, AWS Student Builder Club, SSPU Core Team (2026-27): cloud-security projects, workshops and hands-on sessions
- **Senior Management Head**, 0x0 PIR4T3S Club (Oct 2025 - Apr 2026): ran operations and events for a cybersecurity community, including CTFs and workshops
- **Internship Coordinator** and **Smart India Hackathon Internal Coordinator**: connecting students with real opportunities
- **Session Anchor** for SSPU conferences, because explaining security to a room is part of the job too

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
