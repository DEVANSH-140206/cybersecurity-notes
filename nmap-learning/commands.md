# NMAP COMPLETE NOTES (PROJECT + REAL WORLD)
## Cybersecurity / Penetration Testing Cheat Sheet

==================================================================
WHAT IS NMAP?
==================================================================

Nmap = Network Mapper

Nmap is a network scanning and reconnaissance tool used to discover:

• Live hosts
• Open ports
• Running services
• Service versions
• Operating System
• Vulnerabilities (using NSE scripts)

Nmap DOES NOT automatically hack a machine.

It gathers information.

Information = Reconnaissance

Reconnaissance is the FIRST phase of every penetration test.

==================================================================
PENETRATION TESTING FLOW
==================================================================

Target
   ↓
Host Discovery
   ↓
Port Scanning
   ↓
Service Detection
   ↓
Version Detection
   ↓
Operating System Detection
   ↓
Vulnerability Detection
   ↓
Exploitation (Metasploit etc.)
   ↓
Post Exploitation

Nmap performs almost every step before exploitation.

==================================================================
GENERAL SYNTAX
==================================================================

nmap [OPTIONS] TARGET

Example

nmap -sV 192.168.56.102

Breakdown

nmap
↓
Run Nmap

-sV
↓
Version Detection

192.168.56.102
↓
Target Machine

==================================================================
TARGETS
==================================================================

Single Host

192.168.56.102

Multiple Hosts

192.168.56.101 192.168.56.102

Entire Network

192.168.56.0/24

Website

scanme.nmap.org

==================================================================
IMPORTANT CONCEPTS
==================================================================

Host
=
Any device connected to a network

Port
=
A communication endpoint

Example

22 = SSH

21 = FTP

80 = HTTP

443 = HTTPS

Open Port
=
Application is listening

Closed Port
=
No application is listening

Filtered
=
Firewall blocked Nmap

==================================================================
MOST IMPORTANT OPTIONS
==================================================================

-sn
Skip Port Scan
Host Discovery Only

Purpose

Find alive machines

Example

nmap -sn 192.168.56.0/24

Old tutorials use

-sP

Modern Nmap uses

-sn

==================================================================
-sS
==================================================================

TCP SYN Scan

Most commonly used scan by penetration testers.

Requires sudo/root.

Example

sudo nmap -sS 192.168.56.102

How it works

Client
↓

SYN
↓

Server
↓

SYN ACK
↓

Nmap sends RST

Connection never completes.

Advantages

• Fast
• Stealthier than full TCP connect scans
• Very reliable

==================================================================
-p
==================================================================

Choose ports to scan.

Examples

Single Port

-p 80

Multiple Ports

-p 22,80,443

Range

-p 1-1000

All Ports

-p-

Example

sudo nmap -sS -p 22,80,443 192.168.56.102

==================================================================
-sV
==================================================================

Version Detection

Finds service versions.

Without

80/tcp open http

With

80/tcp open Apache httpd 2.2.8

Example

nmap -sV 192.168.56.102

Very useful before exploiting.

==================================================================
-O
==================================================================

Operating System Detection

Requires sudo.

Example

sudo nmap -O 192.168.56.102

Detects

Linux

Windows

Cisco

Unix

etc.

Uses TCP/IP fingerprinting.

Capital O

NOT zero.

==================================================================
-A
==================================================================

Aggressive Scan

Most useful single command.

Example

sudo nmap -A 192.168.56.102

Includes

✔ OS Detection

✔ Version Detection

✔ Default NSE Scripts

✔ Traceroute

One command

Lots of information

==================================================================
--script
==================================================================

Runs NSE (Nmap Scripting Engine).

Example

sudo nmap --script vuln 192.168.56.102

Purpose

Run scripts to detect vulnerabilities.

Examples

--script vuln

Run vulnerability scripts

--script ftp-anon

Check anonymous FTP login

--script smb-enum-shares

Enumerate SMB shares

--script http-title

Find webpage titles

==================================================================
-D
==================================================================

Decoy Scan

Example

sudo nmap -sS -D RND:10 TARGET

Purpose

Adds decoy source IP addresses to make scan logs harder to interpret.

Used in advanced penetration testing.

==================================================================
OUTPUT OPTIONS
==================================================================

Save scan results.

Normal

-oN scan.txt

XML

-oX scan.xml

Grepable

-oG scan.gnmap

All Formats

-oA project_scan

Creates

project_scan.nmap

project_scan.xml

project_scan.gnmap

==================================================================
IMPORTANT PORT OPTION
==================================================================

-p-

Means

Scan ALL 65535 TCP ports.

Useful because default scan checks only the top 1000 ports.

Example

sudo nmap -p- 192.168.56.102

==================================================================
COMBINING OPTIONS
==================================================================

Nmap options can be combined.

Example

sudo nmap -sS -sV -O -p- 192.168.56.102

Meaning

Run Nmap

↓

SYN Scan

↓

Version Detection

↓

OS Detection

↓

All Ports

↓

Target

==================================================================
COMMONLY USED COMMANDS
==================================================================

1.

nmap TARGET

Purpose

Default scan

Scans top 1000 TCP ports

------------------------------------------------------

2.

nmap -sn NETWORK

Purpose

Find alive hosts

------------------------------------------------------

3.

sudo nmap -sS TARGET

Purpose

Stealthier SYN Scan

------------------------------------------------------

4.

nmap -sV TARGET

Purpose

Find service versions

------------------------------------------------------

5.

sudo nmap -O TARGET

Purpose

Find Operating System

------------------------------------------------------

6.

sudo nmap -A TARGET

Purpose

Everything in one command

------------------------------------------------------

7.

sudo nmap -p- TARGET

Purpose

Scan every TCP port

------------------------------------------------------

8.

sudo nmap -p- -sV TARGET

Purpose

Scan every TCP port and identify service versions

------------------------------------------------------

9.

sudo nmap --script vuln TARGET

Purpose

Find common known vulnerabilities

------------------------------------------------------

10.

sudo nmap -oA scan TARGET

Purpose

Save scan in all formats

==================================================================
PROJECT COMMANDS
==================================================================

Find Alive Hosts

nmap -sn 192.168.56.0/24

-----------------------------------

Scan Target

nmap 192.168.56.102

-----------------------------------

Version Detection

nmap -sV 192.168.56.102

-----------------------------------

Operating System

sudo nmap -O 192.168.56.102

-----------------------------------

Aggressive Scan

sudo nmap -A 192.168.56.102

-----------------------------------

Scan All Ports

sudo nmap -p- 192.168.56.102

-----------------------------------

All Ports + Versions

sudo nmap -p- -sV 192.168.56.102

-----------------------------------

Vulnerability Scan

sudo nmap --script vuln 192.168.56.102

-----------------------------------

Save Results

sudo nmap -A -oA metasploit_scan 192.168.56.102

==================================================================
HOW TO BUILD NMAP COMMANDS
==================================================================

Step 1

Ask yourself

"What do I want?"

↓

Need to find live hosts

↓

Add

-sn

-----------------------------------

Need service versions

↓

Add

-sV

-----------------------------------

Need OS

↓

Add

-O

-----------------------------------

Need all ports

↓

Add

-p-

-----------------------------------

Need vulnerabilities

↓

Add

--script vuln

-----------------------------------

Need aggressive information

↓

Add

-A

-----------------------------------

Need stealthier TCP SYN scan

↓

Add

-sS

-----------------------------------

Need to save output

↓

Add

-oA filename

-----------------------------------

Finally

Add target

==================================================================
EXAMPLES
==================================================================

Need

Find alive hosts

Command

nmap -sn 192.168.56.0/24

-----------------------------------

Need

Find OS

Command

sudo nmap -O 192.168.56.102

-----------------------------------

Need

Find Versions

Command

nmap -sV 192.168.56.102

-----------------------------------

Need

Everything

Command

sudo nmap -A 192.168.56.102

-----------------------------------

Need

Every Port

Command

sudo nmap -p- 192.168.56.102

-----------------------------------

Need

Find Vulnerabilities

Command

sudo nmap --script vuln 192.168.56.102

==================================================================
COMMANDS YOU'LL USE MOST OFTEN
==================================================================

★★★★★
nmap -sn NETWORK

★★★★★
nmap TARGET

★★★★★
nmap -sV TARGET

★★★★★
sudo nmap -A TARGET

★★★★★
sudo nmap -p- TARGET

★★★★★
sudo nmap -p- -sV TARGET

★★★★★
sudo nmap --script vuln TARGET

★★★★★
sudo nmap -oA scan TARGET

==================================================================
THINGS TO REMEMBER
==================================================================

✓ Nmap is a reconnaissance tool, not an exploitation tool.

✓ Default scan checks only the top 1000 TCP ports.

✓ Use -p- to scan all TCP ports.

✓ Use -sV before exploiting to identify service versions.

✓ Use -O for OS detection (capital letter O).

✓ Use -A when you want a comprehensive scan.

✓ Use --script vuln to check for common known vulnerabilities.

✓ Save important scans using -oA.

✓ Learn to build commands by asking:
  "What information do I need?" rather than memorising complete commands.

==================================================================
REAL-WORLD PENTEST WORKFLOW
==================================================================

1. Discover hosts
   nmap -sn NETWORK

2. Scan ports
   nmap TARGET

3. Detect services
   nmap -sV TARGET

4. Detect OS
   sudo nmap -O TARGET

5. Run aggressive scan
   sudo nmap -A TARGET

6. Scan all ports
   sudo nmap -p- TARGET

7. Check for vulnerabilities
   sudo nmap --script vuln TARGET

8. Analyse results

9. Search for matching exploits

10. Exploit using Metasploit or other authorised tools
