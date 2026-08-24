# LESSON — INITIAL ACCESS & HOW ATTACKERS GAIN ACCESS ⭐⭐⭐⭐⭐

## 1. What Is Initial Access?

Initial access means the attacker has found a way to get into or interact with a target system beyond what an ordinary unauthorized user should be able to do.

Important:

> SSH does NOT magically give someone access to a computer.

SSH is simply one possible method of remotely accessing a system.

Think of SSH as a DOOR.

The attacker still needs a valid way through that door, such as legitimate credentials or a vulnerability/misconfiguration.

---

# 2. Main Attack Paths

A target computer can expose different services and applications.

                    TARGET COMPUTER
                          │
             ┌────────────┼────────────┐
             │            │            │
          SSH/RDP       Web app      Vulnerable
          services      services      software
             │            │            │
        Authentication   Exploit    Exploit /
        / credentials    / flaw     misconfig
             │            │            │
             └────────────┼────────────┘
                          ▼
                    INITIAL ACCESS
                          │
                          ▼
                 LIMITED USER ACCESS
                          │
                          ▼
                 PRIVILEGE ESCALATION
                          │
                          ▼
                  HIGHER PRIVILEGES


There are several common ways initial access can happen:

1. Stolen or guessed credentials
2. Vulnerable network services
3. Vulnerable applications
4. Misconfiguration
5. Malware/social engineering

---

# 3. Stolen or Guessed Credentials

Suppose a target exposes SSH:

Target
  │
  └── Port 22 → SSH

If an attacker obtains legitimate credentials, they may authenticate to the SSH service.

Example:

ssh username@target

The important distinction:

This is NOT necessarily an SSH vulnerability.

The SSH service may be working exactly as designed.

The problem is that the attacker possesses valid credentials.

Think:

Valid username + valid password
              ↓
       Authentication
              ↓
         SSH access

---

# 4. Vulnerable Network Service

Suppose Nmap discovers:

80/tcp   HTTP

The service running on that port may contain a vulnerability.

An attacker may investigate the service and, in an authorized penetration test, determine whether the vulnerability can provide access.

General workflow:

Reconnaissance
      ↓
Port discovery
      ↓
Service identification
      ↓
Version/configuration investigation
      ↓
Vulnerability assessment
      ↓
Authorized exploitation
      ↓
Initial access
      ↓
Privilege escalation

IMPORTANT:

Finding an open port does NOT automatically mean the service is vulnerable.

Open port ≠ vulnerability.

It simply means something is accepting network connections on that port.

---

# 5. Vulnerable Application

A web application can also contain vulnerabilities.

Example:

Browser
   ↓
HTTP/HTTPS
   ↓
Web application
   ↓
Vulnerability
   ↓
Server-side access

The weakness may exist in the application rather than in SSH itself.

For example, a poorly designed application could allow unintended actions to be performed on the server.

This is why cybersecurity professionals investigate:

- What software is running?
- What version is it?
- What functionality does it provide?
- What vulnerabilities are known?
- Is it configured securely?

---

# 6. Misconfiguration

Sometimes the software itself is not broken.

The administrator simply configured the system insecurely.

Examples:

- Excessively permissive files
- Weak authentication
- Unnecessary services exposed
- Incorrect user/group permissions
- Insecure service configurations

This connects directly to the Linux topics you have already learned.

For example:

Linux permissions:

ls -l

User identity:

id

Groups:

groups

Ownership:

chown

Permissions:

chmod

Services:

systemctl

These commands help security professionals understand how much access a particular user or service has.

---

# 7. Malware / Social Engineering

Initial access does not always happen through a network service.

Access can also originate from a user.

For example:

User
  ↓
Malicious program
  ↓
Program executes
  ↓
System access

This is a completely different attack path from exploiting an exposed SSH or HTTP service.

Social engineering can also convince a user to perform an unsafe action.

The important concept is:

> Not every attack begins by directly attacking a network service.

---

# 8. SSH Is Only One Possible Entry Point

Do NOT think:

"Hackers use SSH to get into computers."

Instead think:

"SSH is one legitimate remote-access mechanism that may be exposed on a computer."

An attacker might abuse:

- Stolen credentials
- Weak authentication
- Vulnerabilities
- Misconfigurations

to obtain access.

SSH itself is a legitimate technology used every day by:

- System administrators
- Developers
- Security professionals
- Cloud engineers
- Server administrators

---

# 9. Initial Access vs Privilege Escalation

These are TWO DIFFERENT stages.

## Initial Access

Question:

> "How did I get onto the system?"

Example:

Attacker
   ↓
Vulnerable web application
   ↓
Initial access
   ↓
Low-privileged account

---

## Privilege Escalation

Question:

> "Now that I'm on the system, can I obtain higher privileges?"

Example:

Low-privileged user
        ↓
Permission/configuration weakness
        ↓
Higher privileges
        ↓
Root

So:

INITIAL ACCESS

↓

"How do I get in?"

Then:

PRIVILEGE ESCALATION

↓

"How do I gain more privileges?"

Never confuse these two concepts.

---

# 10. Why Linux Permissions Matter

Suppose an attacker obtains access as:

www-data

They are now inside the machine, but they do NOT automatically become root.

Linux still applies permissions.

For example:

/etc/shadow

might be owned by:

root

with restrictive permissions.

So the attacker must ask:

Who am I?

id

What groups am I in?

groups

Who owns this file?

ls -l file

What permissions does it have?

ls -l file

What services are running?

systemctl --type=service

This is where your previous Linux lessons become useful.

---

# 11. The Pentesting Mindset

When you discover a target, don't immediately think:

"How do I attack this?"

Think:

"What is exposed?"

Then:

"What software is running?"

Then:

"How is it configured?"

Then:

"Are there known weaknesses?"

Then:

"Can I safely test this in my authorized environment?"

A good workflow is:

RECONNAISSANCE
      ↓
ENUMERATION
      ↓
SERVICE IDENTIFICATION
      ↓
VULNERABILITY ASSESSMENT
      ↓
AUTHORIZED EXPLOITATION
      ↓
INITIAL ACCESS
      ↓
PRIVILEGE ESCALATION
      ↓
POST-EXPLOITATION

---

# 12. Connection With Nmap

You already learned Nmap.

Suppose Nmap reports:

22/tcp   open   ssh
80/tcp   open   http
3306/tcp open   mysql

Don't just memorize the port numbers.

Think:

                 TARGET

        ┌──────────┼──────────┐
        │          │          │
       22         80        3306
        │          │          │
       SSH        HTTP      MySQL
        │          │          │
    Remote       Web       Database
    access      service      service

Each exposed service represents an attack surface that can be investigated.

But:

OPEN PORT
    ≠
VULNERABILITY

An open port simply tells you that a service is accessible.

You still need to identify and assess the service.

---

# 13. Connection With Your Linux Lessons

Your Linux knowledge now starts connecting together.

SSH
 ↓
Remote access mechanism

Nmap
 ↓
Discovers exposed network services

systemctl
 ↓
Manages services

ps
 ↓
Shows processes

id
 ↓
Shows current identity and groups

groups
 ↓
Shows group memberships

ls -l
 ↓
Shows ownership and permissions

chmod/chown
 ↓
Manage permissions and ownership

All of these help you understand:

WHO
 ↓
CAN ACCESS WHAT
 ↓
AND WITH WHICH PRIVILEGES

That is a major part of Linux security.

---

# 14. Your Metasploitable2 Lab

Your authorized lab gives you a safe environment to learn these concepts.

Conceptually:

KALI
  │
  │ Network
  ▼
METASPLOITABLE2
  │
  ├── SSH
  ├── HTTP
  ├── FTP
  ├── Telnet
  ├── MySQL
  └── Other services

Your workflow:

Kali
 ↓
Nmap
 ↓
Discover open ports
 ↓
Identify services
 ↓
Understand what each service does
 ↓
Investigate versions/configuration
 ↓
Perform authorized security testing
 ↓
Understand initial access
 ↓
Study privilege boundaries

The goal is NOT to blindly run exploits.

The goal is to understand WHY a system is vulnerable.

---

# 15. MOST IMPORTANT DISTINCTION

Remember these three concepts:

OPEN PORT

Means:

"Something is accepting network connections here."

SERVICE

Means:

"The software/functionality accepting those connections."

VULNERABILITY

Means:

"There is a weakness that may allow unintended behavior."

Example:

22/tcp open ssh

means:

Port 22 is open and Nmap identified SSH.

It does NOT automatically mean:

"SSH is vulnerable."

---

# 16. FINAL MENTAL MODEL

                         TARGET
                           │
                           ▼
                    RECONNAISSANCE
                           │
                           ▼
                    OPEN PORTS
                           │
                           ▼
                      SERVICES
                           │
                           ▼
                  SOFTWARE / VERSION
                           │
                           ▼
             CONFIGURATION / VULNERABILITIES
                           │
                           ▼
               AUTHORIZED SECURITY TEST
                           │
                           ▼
                    INITIAL ACCESS
                           │
                           ▼
                LOW-PRIVILEGED USER
                           │
                           ▼
                PRIVILEGE ESCALATION
                           │
                           ▼
                  HIGHER PRIVILEGES
                           │
                           ▼
                         ROOT

The core questions are:

1. What is exposed?
2. What service is running?
3. What software is behind it?
4. Is it configured securely?
5. Does it have a known weakness?
6. How much access does the current user have?
7. What privileges should that user have?
8. Where are the security boundaries?

That is the foundation of understanding how real Linux attacks work.

# KEY TERMS TO REMEMBER

Initial Access
→ The stage where an attacker first gains access to a target.

Authentication
→ Proving who you are, usually with credentials, keys, etc.

SSH
→ Secure remote-access protocol, normally using TCP port 22.

Service
→ A program/function running to provide some system or network functionality.

Vulnerability
→ A weakness that can cause unintended or unauthorized behavior.

Misconfiguration
→ An insecure or incorrect configuration that creates a security weakness.

Privilege Escalation
→ Obtaining higher privileges after gaining initial access.

Attack Surface
→ The collection of exposed services, applications, interfaces, and other entry points that could potentially be attacked.

MOST IMPORTANT:

SSH ≠ automatic access.

OPEN PORT ≠ vulnerability.

INITIAL ACCESS ≠ PRIVILEGE ESCALATION.

Those three distinctions are extremely important for your pentesting foundation.