# MODULE 1

> TryHackMe — Pre Security Path  
> Fast Revision Notes

---

# 1. Offensive Security

Offensive Security = Simulating attacks to find vulnerabilities before real attackers do.

Goal:
```text
Find weaknesses and improve security
```

Examples:
- Penetration Testing
- Red Teaming
- Exploit Development
- Bug Bounty Hunting

---

# 2. Defensive Security

Defensive Security = Protecting systems from attacks.

Goal:
```text
Detect, prevent, and respond to threats
```

Examples:
- Monitoring alerts
- Firewalls
- Incident response
- Malware analysis
- SIEM monitoring

---

# 3. SOC (Security Operations Center)

SOC = Team responsible for monitoring and defending systems.

Main tasks:
- Monitor alerts
- Investigate suspicious activity
- Detect attacks
- Respond to incidents

---

# 4. Main Areas Of Interest In SOC

---

## Threat Intelligence

Collecting information about:
- Attackers
- Malware
- Threat groups
- New attack techniques

Purpose:
```text
Understand threats before attacks happen
```

---

## DFIR (Digital Forensics & Incident Response)

### Digital Forensics
Investigating:
- Logs
- Devices
- Evidence
- Attack traces

### Incident Response
Handling security incidents:
- Detect
- Contain
- Eradicate
- Recover

---

## Malware Analysis

Studying malware to understand:
- What it does
- How it spreads
- How to detect it

---

# 5. Static vs Dynamic Malware Analysis

| Static Analysis | Dynamic Analysis |
|---|---|
| Analyze without running malware | Analyze while running malware |
| Safer | More realistic |
| Inspect code/files | Observe behavior |

---

## Static Analysis Examples
- Strings analysis
- Hash analysis
- Inspecting binaries
- Reading code

---

## Dynamic Analysis Examples
- Running malware in sandbox/VM
- Monitoring network activity
- Watching file/process behavior

---

# 6. Gobuster

Gobuster = Directory/File brute-forcing tool.

Used to discover:
- Hidden directories
- Hidden files
- Admin panels
- Backup files

---

# 7. Gobuster Command

```bash
gobuster -u http://fakebank.thm -w wordlist.txt dir
```

---

# 8. Gobuster Command Breakdown

| Part | Meaning |
|---|---|
| `gobuster` | Tool name |
| `-u` | Target URL |
| `http://fakebank.thm` | Website target |
| `-w` | Wordlist option |
| `wordlist.txt` | List of possible directories/files |
| `dir` | Directory enumeration mode |

---

# 9. How Gobuster Works

Gobuster takes words from the wordlist and tries:

```text
/admin
/login
/uploads
/images
```

on the target website.

---

# 10. Why Gobuster Matters In Cybersecurity

Used in:
- Reconnaissance
- Web enumeration
- Pentesting
- CTFs

Helps discover:
- Hidden admin panels
- Sensitive directories
- Backup files
- Misconfigured resources

---

# 11. Gobuster Results

Example:
```text
/admin (Status: 200)
/backup (Status: 403)
/test (Status: 301)
```

---

## Important Status Codes In Results

| Code | Meaning |
|---|---|
| `200` | Exists & accessible |
| `301/302` | Redirect |
| `403` | Exists but forbidden |
| `404` | Not found |

---

# 12. Important Recon Concept

```text
403 is VERY interesting
```

because:
```text
Resource exists but access is blocked
```

---

# 13. SIEM

SIEM = Security Information and Event Management.

Used to:
- Collect logs
- Monitor events
- Detect suspicious activity
- Generate alerts

---

# 14. Cybersecurity Mindset

Security is continuous:
```text
Monitor → Detect → Respond → Improve
```

Threats constantly evolve, so continuous learning is necessary.

---

# 15. MOST IMPORTANT THINGS TO REMEMBER

## Offensive Security
```text
Find vulnerabilities by attacking systems ethically
```

---

## Defensive Security
```text
Protect and monitor systems
```

---

## SOC
```text
Monitors alerts and responds to threats
```

---

## Gobuster
```text
Directory/file brute-forcing tool
```

---

## Important Gobuster Command
```bash
gobuster -u http://target.com -w wordlist.txt dir
```

---

## Static vs Dynamic Analysis
```text
Static → Without running malware
Dynamic → Run malware and observe behavior
```

---

## DFIR
```text
Investigate and respond to incidents
```

---

## Threat Intelligence
```text
Study attackers, malware, and threats
```

---

# 16. 30 Second Revision

```text
Offensive Security → Attack ethically to find weaknesses

Defensive Security → Protect systems

SOC → Monitor alerts and incidents

Gobuster → Find hidden directories/files

200 → Accessible
403 → Exists but forbidden

Threat Intelligence → Study threats

DFIR → Investigate/respond to incidents

Static Analysis → Analyze without running
Dynamic Analysis → Run and observe malware

SIEM → Collect logs and detect alerts
```