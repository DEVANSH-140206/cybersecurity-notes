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
# Cyber Security Notes: Search Skills & Tools

> TryHackMe — Quick Revision Notes

---

# 1. Shodan & Apache

## Shodan
**Shodan** = Search engine for internet-connected devices and services.

Used to discover:
- Open ports
- Servers
- Cameras
- IoT devices
- Vulnerable systems

---

## Apache
**Apache** = Popular web server software used to host websites.

Commonly found during:
- Reconnaissance
- Enumeration
- Web scanning

---

## TryScanMe
```text
TryScanMe = Safe THM simulation target
```

Used for practicing reconnaissance safely.

---

## Important Linux Command

```bash
curl http://MACHINE_IP
```

### Purpose
- Sends HTTP request to target
- Retrieves webpage/server response
- Useful for enumeration & testing

---

# 2. VirusTotal

## What Is VirusTotal?
**VirusTotal** = Multi-engine malware scanning platform.

Checks:
- Files
- URLs
- Hashes

against many antivirus engines.

---

## Hash
A **hash** is a unique fingerprint of a file.

Used to:
- Identify malware
- Verify file integrity
- Search known malicious files

Common hash types:
```text
MD5
SHA1
SHA256
```

---

## TryDetectMe
```text
TryDetectMe = Safe THM malware analysis simulation
```

---

## Important Linux Commands

### Generate SHA256 Hash
```bash
sha256sum file.txt
```

### VirusTotal CLI Scan
```bash
vt file file.txt
```

---

# 3. Vulnerability Databases

| Resource | Purpose | Important Point |
|---|---|---|
| **CVE** | Vulnerability identifier database | Standardized vulnerability IDs |
| **Exploit-DB** | Public exploit archive | Stores exploit code & PoCs |
| **GitHub** | Fast PoC/research sharing | New exploits often appear here first |

---

# 4. CVE

## What Is CVE?
**CVE (Common Vulnerabilities and Exposures)** = Standardized ID for publicly known vulnerabilities.

Example:
```text
CVE-2021-44228
```

---

# 5. Exploit-DB

## What Is Exploit-DB?
Database containing:
- Public exploits
- PoC code
- Vulnerability references

Useful during:
- Pentesting
- Research
- Lab practice

---

# 6. SearchSploit

## What Is SearchSploit?
Linux CLI tool for searching Exploit-DB locally.

---

## Basic Syntax

```bash
searchsploit apache
```

### Example
Searches for:
```text
Apache-related exploits
```

---

## Another Example

```bash
searchsploit openssh
```

---

# 7. MOST IMPORTANT THINGS TO REMEMBER

```text
Shodan → Search engine for internet-connected devices

Apache → Popular web server software

VirusTotal → Multi-engine malware scanner

Hash → Unique fingerprint of a file

CVE → Vulnerability ID system

Exploit-DB → Exploit archive

GitHub → Fast PoC/research sharing

searchsploit → Search Exploit-DB from terminal
```

---

# 8. Quick Command Revision

```bash
curl http://MACHINE_IP

sha256sum file.txt

vt file file.txt

searchsploit apache
```

# Linux Fundamentals: Core Commands & Operators

> TryHackMe — Quick Revision Notes

---

# 1. System & Navigation Commands

| Command | Purpose | Example |
|---|---|---|
| `whoami` | Shows current logged-in user | `whoami` |
| `pwd` | Shows current directory path | `pwd` |
| `cd` | Changes directory | `cd /home/user` |
| `ls` | Lists files/directories | `ls` |

---

# 2. Searching & Viewing Files

## find

Used to search for files and directories.

---

## Find File By Name

```bash
find -name notes.txt
```

### Example Output

```text
./Documents/notes.txt
```

### Purpose
Searches current directory and subdirectories for:
```text
notes.txt
```

---

## Find Files Using Wildcards

```bash
find -name "*.txt"
```

### Example Output

```text
./notes.txt
./logs/access.txt
./Documents/passwords.txt
```

### Purpose
Finds:
```text
All .txt files
```

---

## Find Files In Specific Directory

```bash
find /var/log -name "*.log"
```

### Example Output

```text
/var/log/auth.log
/var/log/apache2/access.log
```

### Cybersecurity Use
Useful for:
- Finding log files
- Searching configs
- Enumerating systems

---

## echo

Prints text/output to terminal.

### Example

```bash
echo "Hello World"
```

### Output

```text
Hello World
```

---

# 3. Text Analysis & Filtering (Log Analysis Essentials)

## wc -l

Counts:
```text
Number of lines
```

### Example

```bash
wc -l access.log
```

### Example Output

```text
250 access.log
```

Meaning:
```text
access.log contains 250 lines
```

---

## grep

Searches for specific text/patterns inside files.

---

## Search For An IP Address

```bash
grep "81.143.211.90" access.log
```

### Example Output

```text
81.143.211.90 - - [12/May/2026] "GET /login HTTP/1.1"
81.143.211.90 - - [12/May/2026] "POST /admin HTTP/1.1"
```

### Cybersecurity Use
Useful for:
- Finding suspicious IPs
- Investigating attackers
- Log analysis

---

## Recursive Search

```bash
grep -R "PRETTY_NAME" /etc/
```

### Example Output

```text
/etc/os-release:PRETTY_NAME="Ubuntu 22.04 LTS"
```

### Purpose
Recursively searches:
```text
All files inside /etc/
```

for:
```text
PRETTY_NAME
```

---

## Search For Failed Logins

```bash
grep "Failed password" auth.log
```

### Example Output

```text
Failed password for root from 192.168.1.5
```

### Cybersecurity Use
Helps detect:
- Brute-force attacks
- Unauthorized login attempts

---

# 4. Linux Operators Cheat Sheet

| Operator | Meaning | Example |
|---|---|---|
| `&` | Run process in background | `firefox &` |
| `&&` | Run second command only if first succeeds | `mkdir test && cd test` |
| `>` | Redirect output (overwrite file) | `echo hello > file.txt` |
| `>>` | Redirect output (append to file) | `echo hello >> file.txt` |

---

# 5. MOST IMPORTANT THINGS TO REMEMBER

```text
whoami → Current user
pwd → Current directory
cd → Change directory
ls → List files

find → Search files/directories
echo → Print text/output

wc -l → Count lines
grep → Search text/patterns

& → Background execution
&& → Conditional execution
> → Overwrite output
>> → Append output
```

---

# 6. Quick Command Revision

```bash
whoami
pwd
cd /home/user
ls

find -name notes.txt
find /var/log -name "*.log"

echo "Hello World"

wc -l access.log

grep "81.143.211.90" access.log
grep "Failed password" auth.log
grep -R "PRETTY_NAME" /etc/
```

# Windows Terminal Fundamentals for Cybersecurity

> TryHackMe — Quick Revision Notes

---

# 1. Navigation & File Management

| Command | Purpose | Example |
|---|---|---|
| `cd` | Change directory | `cd Desktop` |
| `cd ..` | Move one directory back | `cd ..` |
| `dir` | List files/directories | `dir` |
| `mkdir` | Create directory | `mkdir test` |
| `rmdir` | Remove directory | `rmdir test` |
| `del` / `erase` | Delete file | `del notes.txt` |
| `move` | Move file/folder | `move test.txt Desktop` |

---

# Viewing File Content

| Command | Purpose | Example |
|---|---|---|
| `type` | Display file contents | `type notes.txt` |
| `more` | View long files page-by-page | `more notes.txt` |

---

# 2. System Information & Maintenance

---

## systeminfo

Displays:
- OS details
- Hardware info
- Installed patches
- System configuration

### Example

```cmd
systeminfo
```

---

## cls

Clears terminal screen.

### Example

```cmd
cls
```

---

## driverquery

Lists installed drivers.

### Example

```cmd
driverquery
```

### Cybersecurity Use

Useful for:
- Investigating drivers
- Detecting suspicious drivers
- System analysis

---

## System File Checker

Scans and repairs corrupted system files.

### Example

```cmd
sfc /scannow
```

---

## Restart System

### Example

```cmd
shutdown /r
```

Purpose:
```text
Restart the computer
```

---

# 3. Networking & Remote Access

---

## ssh

Remote secure shell connection.

### Example

```cmd
ssh user@192.168.1.10
```

---

## ipconfig

Displays basic network configuration.

### Example

```cmd
ipconfig
```

---

## ipconfig /all

Displays detailed network information.

### Includes:
- MAC address
- DNS
- DHCP
- IP configuration

### Example

```cmd
ipconfig /all
```

---

## ping

Tests connectivity to another system.

### Example

```cmd
ping google.com
```

or

```cmd
ping 8.8.8.8
```

---

## tracert

Shows path packets take to destination.

### Example

```cmd
tracert google.com
```

---

## nslookup

Queries DNS records.

### Example

```cmd
nslookup google.com
```

---

## netstat

Displays:
- Active connections
- Open ports
- Listening services

### Example

```cmd
netstat
```

### Cybersecurity Use

Useful for:
- Detecting suspicious connections
- Investigating malware activity
- Monitoring ports

---

# 4. Process Management (Blue Team Essentials)

---

## tasklist

Lists running processes.

### Example

```cmd
tasklist
```

---

## Filter Specific Process

### Example

```cmd
tasklist /FI "imagename eq sshd.exe"
```

### Purpose

Shows only:
```text
sshd.exe process
```

---

## taskkill

Terminates processes.

### Kill By PID

```cmd
taskkill /PID 1337
```

---

## Cybersecurity Use

Useful for:
- Detecting malicious processes
- Monitoring activity
- Stopping malware

---

# 5. Pipe Operator

## `| more`

Used to:
```text
View long output page-by-page
```

---

## Example

```cmd
systeminfo | more
```

### Purpose

Instead of flooding terminal:
```text
Shows output one page at a time
```

---

# 6. MOST IMPORTANT THINGS TO REMEMBER

```text
cd → Change directory
dir → List files
mkdir → Create directory
del → Delete file

systeminfo → System details
driverquery → List drivers
sfc /scannow → Repair system files

ipconfig → Network info
ping → Test connectivity
tracert → Trace packet route
netstat → View connections/ports

tasklist → List processes
taskkill → Kill process

| more → View long output page-by-page
```

# Linux vs Windows Terminal Commands

> Quick Command Comparison Cheat Sheet

---

# 1. Navigation Commands

| Linux | Windows CMD | Purpose |
|---|---|---|
| `pwd` | `cd` | Show current directory |
| `cd` | `cd` | Change directory |
| `ls` | `dir` | List files/directories |

---

# 2. File & Directory Management

| Linux | Windows CMD | Purpose |
|---|---|---|
| `mkdir` | `mkdir` | Create directory |
| `rm file.txt` | `del file.txt` | Delete file |
| `rm -r folder` | `rmdir folder` | Delete directory |
| `mv file.txt folder/` | `move file.txt folder` | Move file |
| `cat file.txt` | `type file.txt` | View file content |

---

# 3. Searching & Filtering

| Linux | Windows CMD | Purpose |
|---|---|---|
| `find` | `dir /s` | Search files |
| `grep` | `findstr` | Search text/patterns |

---

# 4. Networking Commands

| Linux | Windows CMD | Purpose |
|---|---|---|
| `ifconfig` / `ip a` | `ipconfig` | Network configuration |
| `ping` | `ping` | Test connectivity |
| `traceroute` | `tracert` | Trace packet route |
| `netstat` | `netstat` | View network connections |
| `ssh` | `ssh` | Remote secure connection |

---

# 5. Process Management

| Linux | Windows CMD | Purpose |
|---|---|---|
| `ps` | `tasklist` | List running processes |
| `kill PID` | `taskkill /PID PID` | Kill process |

---

# 6. Important Terminal Differences

| Linux Terminal | Windows CMD |
|---|---|
| More powerful for cybersecurity | More beginner-friendly |
| Widely used in hacking/pentesting | Common in enterprise environments |
| Better scripting/automation | Easier Windows administration |
| Most cybersecurity tools built for Linux | Useful for Windows investigation |

---

# 7. Cybersecurity Reality

```text
Most cybersecurity professionals heavily use Linux.

But Windows CMD/PowerShell is critical for:
- Blue Teaming
- Active Directory
- Enterprise environments
- Malware investigations
```

---

# 8. MOST IMPORTANT THINGS TO REMEMBER

```text
Linux:
ls → List files
cat → View file
grep → Search text
ifconfig → Network info

Windows:
dir → List files
type → View file
findstr → Search text
ipconfig → Network info

Linux is dominant in offensive security.
Windows CMD is important for enterprise defense.
```