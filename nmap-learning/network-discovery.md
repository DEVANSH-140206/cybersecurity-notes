# Network Discovery & Host Enumeration

This document contains the fundamental networking concepts and commands used to discover devices on a network before performing security testing. These concepts form the basis of Reconnaissance and Enumeration in Ethical Hacking.

---

# What is Network Discovery?

## Definition

Network Discovery is the process of identifying devices connected to a network.

## Why is it needed?

Before attacking or testing a machine, an ethical hacker must first know:

- Which devices are connected?
- Which devices are alive?
- What IP addresses do they have?
- Which machine is the target?

Without discovering devices, there is nothing to scan or test.

## How does it work?

A scanner sends requests to devices on the network.

If a device responds, it is considered "alive."

## Advantages

- Finds active devices
- Helps map the network
- First step in penetration testing

## Example

```text
Unknown Network

↓

Discover Devices

↓

Identify Target

↓

Perform Security Testing
```

## Commands

```bash
nmap -sn <network>
```

## Notes / Best Practices

Always perform Host Discovery before scanning ports.

---

# IP Address

## Definition

An IP (Internet Protocol) Address is a unique numerical identifier assigned to every device connected to a network.

It allows devices to communicate with each other.

## Why is it needed?

Without an IP address, devices cannot send or receive network traffic.

## Structure

IPv4 consists of four numbers separated by dots.

Example

```text
192.168.56.101
```

Each number is called an **Octet**.

```text
192

168

56

101
```

Each Octet contains 8 bits.

Total

```text
8 + 8 + 8 + 8 = 32 bits
```

## Advantages

- Unique identification
- Enables communication
- Routing of packets

## Example

```text
Kali

192.168.56.101

↓

Metasploitable

192.168.56.102
```

## Commands

```bash
ip a

hostname -I
```

## Notes / Best Practices

Devices on the same local network usually share the first part of the IP address.

---

# Network ID

## Definition

The Network ID identifies the network to which a device belongs.

Every device connected to the same network has the same Network ID.

## Why is it needed?

Routers use the Network ID to determine where packets should be sent.

## Example

Suppose these devices exist.

```text
192.168.56.101

192.168.56.102

192.168.56.103
```

Notice

```text
192.168.56
```

is identical.

This is the Network ID.

## Notes

Devices with the same Network ID can usually communicate directly.

---

# Host ID

## Definition

The Host ID uniquely identifies a device inside a network.

## Example

```text
192.168.56.101
```

Network ID

```text
192.168.56
```

Host ID

```text
101
```

Another device

```text
192.168.56.102
```

Network ID remains the same.

Host ID changes.

## Notes

Every device on a network must have a unique Host ID.

---

# CIDR Notation

## Definition

CIDR (Classless Inter-Domain Routing) indicates how many bits belong to the Network ID.

Example

```text
192.168.56.101/24
```

The "/24" means

The first 24 bits belong to the Network.

The remaining 8 bits belong to the Host.

## Visualization

```text
192 .168 .56 .101

|----24 bits----|

Network

|--8 bits--|

Host
```

## Why is it needed?

CIDR determines

- Network size
- Number of hosts
- Network range

## Example

```text
192.168.56.101/24
```

Network

```text
192.168.56.0/24
```

Host

```text
101
```

## Notes

Most VirtualBox Host-only networks use /24.

---

# Network Address

## Definition

The Network Address represents the entire network.

It is not assigned to any individual device.

Example

```text
192.168.56.0
```

## Why is it needed?

It identifies the network itself.

## Example

Imagine a street.

```text
Green Street
```

The street is

```text
192.168.56.0
```

The houses are

```text
192.168.56.1

192.168.56.2

192.168.56.3

...
```

## Notes

The Network Address cannot be assigned to a computer.

---

# Broadcast Address

## Definition

The Broadcast Address is used to send a packet to every device on a network.

Example

```text
192.168.56.255
```

## Why is it needed?

Allows communication with all hosts simultaneously.

## Notes

The Broadcast Address cannot be assigned to any device.

---

# Finding Your IP Address

## Command

```bash
ip a
```

## Definition

Displays all network interfaces and their IP addresses.

## Why is it needed?

Used to identify

- Current IP Address
- Network Adapter
- Network to scan

## Example

```text
eth0

inet 10.0.2.15/24

eth1

inet 192.168.56.101/24
```

This tells us

Adapter 1

```text
10.0.2.15
```

Adapter 2

```text
192.168.56.101
```

## Notes

Running

```bash
ip a
```

inside Kali only displays Kali's interfaces.

It does **NOT** display the IP addresses of other machines.

---

# hostname -I

## Definition

Displays the IP addresses assigned to the current machine.

## Why is it needed?

A quick way to view the system's IP without displaying all network information.

## Command

```bash
hostname -I
```

Example

```text
10.0.2.15 192.168.56.101
```

## Notes

If multiple adapters are connected, multiple IP addresses will be displayed.

---

# Understanding Multiple Network Interfaces

A computer can have multiple Network Interface Cards (NICs).

Example

```text
Kali Linux

eth0

↓

NAT

↓

10.0.2.15

-------------------------

eth1

↓

Host-only

↓

192.168.56.101
```

Each adapter belongs to a different network.

Each adapter has a different IP address.

This allows Kali to communicate with multiple networks simultaneously.

---

# How Do We Know Which Network to Scan?

Suppose

```bash
ip a
```

shows

```text
inet 192.168.56.101/24
```

The Network ID is

```text
192.168.56
```

Since the subnet is

```text
/24
```

we replace the Host ID with

```text
0
```

Result

```text
192.168.56.0/24
```

This is the network we scan.

Another Example

Current IP

```text
192.168.43.25/24
```

Network

```text
192.168.43.0/24
```

Current IP

```text
10.0.2.15/24
```

Network

```text
10.0.2.0/24
```

## Important Rule

If your IP is

```text
A.B.C.D/24
```

The network to scan is

```text
A.B.C.0/24
```

---

# Common Beginner Mistakes

❌ Thinking `ip a` shows every device on the network.

Reality

It only shows the interfaces of the current machine.

---

❌ Confusing Network ID with Host ID.

Remember

```text
192.168.56.101

Network → 192.168.56

Host → 101
```

---

❌ Using the Network Address as a device IP.

Wrong

```text
192.168.56.0
```

Correct

```text
192.168.56.101
```

---

❌ Using the Broadcast Address as a device IP.

Wrong

```text
192.168.56.255
```

---

# Best Practices

- Always check your own IP before scanning.
- Understand the subnet before choosing a scan range.
- Verify the correct network adapter (NAT, Host-only, Bridged).
- Never assume another machine's IP address.
- Use Host Discovery before Port Scanning.
- Keep network diagrams for your lab to avoid confusion.


---

# Ping

## Definition

Ping is a network utility used to check whether another device on the network is reachable.

It works by sending **ICMP (Internet Control Message Protocol) Echo Request** packets to a target device. If the target is online, it replies with an **ICMP Echo Reply**.

## Why is it needed?

Ping helps determine whether:

- A device is online
- Network connectivity exists
- Two devices can communicate

It is usually the first connectivity test before scanning ports or performing penetration testing.

## How does it work?

```text
Kali
   │
ICMP Echo Request
   │
   ▼
Metasploitable
   │
ICMP Echo Reply
   │
   ▼
Kali
```

If no reply is received, the device may be:

- Offline
- Blocking ICMP
- Not connected to the same network

## Command

```bash
ping <IP_Address>
```

Example

```bash
ping 192.168.56.102
```

## Notes / Best Practices

- Always test connectivity before running Nmap scans.
- Some systems block ping even though they are online.

---

# ifconfig

## Definition

`ifconfig` (Interface Configuration) displays and configures network interfaces.

Although it is deprecated on modern Linux systems, many penetration testing labs and older Linux distributions (such as Metasploitable2) still use it.

## Why is it needed?

It allows you to view:

- IP Address
- MAC Address
- Interface Status
- Packet Statistics

## Command

```bash
ifconfig
```

Example

```text
eth0

inet addr:192.168.56.102

Mask:255.255.255.0
```

## Notes

When using Metasploitable2, `ifconfig` is commonly used to find the machine's IP address.

---

# ifconfig -a

## Definition

Displays **all** network interfaces, including disabled ones.

## Why is it needed?

Useful when an adapter exists but is currently down.

## Command

```bash
ifconfig -a
```

## Example

```text
lo

eth0

eth1
```

Even if `eth1` is inactive, it will still be displayed.

---

# Loopback Interface (lo)

## Definition

The Loopback Interface represents the computer communicating with itself.

Every Linux machine has one.

## IP Address

```text
127.0.0.1
```

This address is also called

```text
localhost
```

## Why is it needed?

Programs running on the same machine can communicate without using the physical network.

## Example

```text
Browser

↓

Web Server

↓

Same Computer

↓

127.0.0.1
```

## Notes

`lo` is not used to communicate with other devices.

---

# Ethernet Interfaces

Linux names Ethernet adapters as

```text
eth0

eth1

eth2
```

Each adapter represents a different network connection.

Example

```text
eth0

↓

NAT

↓

10.0.2.15
```

```text
eth1

↓

Host-only

↓

192.168.56.101
```

A machine can have multiple interfaces connected to different networks simultaneously.

---

# Nmap

## Definition

Nmap stands for

**Network Mapper**

It is one of the world's most popular network discovery and security auditing tools.

## Why is it needed?

Nmap can

- Discover devices
- Scan ports
- Detect services
- Detect operating systems
- Identify vulnerabilities (using NSE scripts)

It is one of the first tools used during penetration testing.

## Basic Syntax

```bash
nmap [options] target
```

Example

```bash
nmap 192.168.56.102
```

## Advantages

- Fast
- Powerful
- Flexible
- Supports hundreds of scanning techniques

---

# Host Discovery

## Definition

Host Discovery is the process of identifying which devices are currently online.

Host Discovery does **not** scan ports.

It only determines whether a host is alive.

## Workflow

```text
Unknown Network

↓

Find Live Hosts

↓

Choose Target

↓

Scan Ports

↓

Identify Services

↓

Attack (Authorized Environments Only)
```

---

# nmap -sn

## Definition

Performs Host Discovery only.

The `-sn` option tells Nmap

> "Do not scan ports. Only determine whether hosts are alive."

## Command

```bash
nmap -sn <network>
```

Example

```bash
nmap -sn 192.168.56.0/24
```

## Why do we scan 192.168.56.0/24?

Suppose

```bash
ip a
```

shows

```text
inet 192.168.56.101/24
```

The first three octets belong to the Network ID.

```text
192.168.56
```

The last octet is the Host ID.

```text
101
```

Replacing the Host ID with

```text
0
```

gives the Network Address.

```text
192.168.56.0/24
```

This tells Nmap

> Scan every possible device on this network.

---

# How Nmap Scans the Network

Suppose

```text
192.168.56.0/24
```

contains

```text
Windows Host

192.168.56.1

Kali

192.168.56.101

Metasploitable

192.168.56.102
```

Nmap checks

```text
192.168.56.1

↓

Alive

192.168.56.2

↓

No Response

192.168.56.3

↓

No Response

...

192.168.56.101

↓

Alive

192.168.56.102

↓

Alive
```

It repeats this process until every possible host has been checked.

---

# Example Output

```text
Starting Nmap...

Nmap scan report for 192.168.56.1

Host is up.

Nmap scan report for 192.168.56.101

Host is up.

Nmap scan report for 192.168.56.102

Host is up.
```

This tells us

Three devices responded.

It does **not** tell us what those devices are.

---

# Finding the Target Machine

Suppose Nmap reports

```text
192.168.56.1

192.168.56.101

192.168.56.102
```

First, determine your own IP.

```bash
hostname -I
```

Suppose

```text
192.168.56.101
```

Now we know

```text
192.168.56.101

↓

Kali
```

The remaining devices become potential targets.

---

# Common Beginner Mistake

Many beginners accidentally scan their own machine.

Example

```bash
sudo nmap 192.168.56.101
```

If Kali's Host-only IP is

```text
192.168.56.101
```

then Kali scans itself.

Wireshark will show

```text
Source IP

192.168.56.101

Destination IP

192.168.56.101
```

This means

The packets never left Kali.

The attack was performed against the local machine instead of Metasploitable.

---

# Correct Workflow

Step 1

Find your IP.

```bash
hostname -I
```

Step 2

Find live hosts.

```bash
nmap -sn 192.168.56.0/24
```

Step 3

Identify unknown hosts.

Step 4

Choose the correct target.

Step 5

Scan the target.

---

# Practical Example (Our Lab)

```text
Windows Host

192.168.56.1

↓

Kali

192.168.56.101

↓

Metasploitable

192.168.56.102
```

Commands

```bash
hostname -I
```

↓

Shows

```text
192.168.56.101
```

Next

```bash
nmap -sn 192.168.56.0/24
```

↓

Finds

```text
192.168.56.1

192.168.56.101

192.168.56.102
```

Now we know

```text
192.168.56.101

↓

Our Machine
```

Unknown

```text
192.168.56.102
```

↓

Likely Metasploitable

This host can now be scanned in greater detail.

---

# Best Practices

- Always verify your own IP before scanning.
- Use `ping` to confirm connectivity before using Nmap.
- Use `nmap -sn` before any detailed scan.
- Never assume a host's identity based only on its IP address.
- Document discovered hosts during penetration testing.
- Perform scans only on systems you own or are explicitly authorised to test.


---

# Reconnaissance

## Definition

Reconnaissance (Recon) is the first phase of penetration testing where information about the target is collected before attempting any attack.

It answers questions like:

- What systems are online?
- What operating systems are running?
- What services are available?
- What technologies are being used?
- Which machine should be targeted?

## Why is it needed?

Reconnaissance helps attackers and penetration testers understand the target environment before interacting with it further.

The more information collected, the better the testing strategy.

## Types of Reconnaissance

### Passive Reconnaissance

Information is collected **without directly interacting** with the target.

Examples

- Google Search
- Company Website
- LinkedIn
- WHOIS
- DNS Records
- Public GitHub Repositories

Advantages

- Difficult to detect
- No direct contact with the target

---

### Active Reconnaissance

Information is collected by directly communicating with the target.

Examples

- Ping
- Nmap
- Banner Grabbing
- Port Scanning

Advantages

- More accurate
- More detailed

Disadvantages

- Can be detected
- Generates network traffic

---

# Enumeration

## Definition

Enumeration is the process of extracting detailed information from discovered hosts.

Unlike Reconnaissance, Enumeration actively communicates with services to gather information.

Examples

- Open Ports
- Running Services
- Operating System
- Service Versions
- Hostname
- Shared Resources
- Users (when permitted)

## Why is it needed?

Enumeration helps identify possible attack vectors.

Example

Recon finds

```text
192.168.56.102
```

Enumeration reveals

```text
FTP

SSH

Telnet

Apache

MySQL

Samba
```

Now we know where to focus our testing.

---

# nmap -A

## Definition

The **-A** option enables aggressive scanning.

It performs

- OS Detection
- Service Version Detection
- Default NSE Scripts
- Traceroute

## Command

```bash
sudo nmap -A <IP_Address>
```

Example

```bash
sudo nmap -A 192.168.56.102
```

---

# What Information Does -A Provide?

## Open Ports

Example

```text
21/tcp

22/tcp

80/tcp
```

---

## Running Services

Example

```text
FTP

SSH

HTTP
```

---

## Service Versions

Example

```text
vsFTPd 2.3.4

Apache 2.2

OpenSSH 4.7
```

Knowing versions is important because vulnerabilities often depend on the software version.

---

## Operating System Detection

Example

```text
Linux

Ubuntu

Windows
```

Nmap estimates the operating system based on network behaviour.

---

## NSE (Nmap Scripting Engine)

NSE scripts automatically perform additional checks.

Examples

- Detect vulnerabilities
- Gather service information
- Check default configurations

---

## Traceroute

Shows the path packets take to reach the target.

Useful in larger networks.

---

# How Did We Identify Metasploitable?

Suppose Host Discovery returned

```text
192.168.56.1

192.168.56.101

192.168.56.102
```

Step 1

Check our own IP.

```bash
hostname -I
```

Output

```text
192.168.56.101
```

This is Kali.

Remaining Hosts

```text
192.168.56.1

192.168.56.102
```

Now perform Enumeration.

```bash
sudo nmap -A 192.168.56.102
```

Example Output

```text
21/tcp

FTP

vsFTPd 2.3.4

22/tcp

SSH

23/tcp

Telnet

80/tcp

Apache

139/tcp

Samba

3306/tcp

MySQL
```

Metasploitable2 intentionally contains many vulnerable services.

From these results we can confidently identify

```text
192.168.56.102

↓

Metasploitable2
```

---

# Why Did Source IP = Destination IP?

During our lab we accidentally scanned Kali itself.

Example

```bash
sudo nmap 192.168.56.101
```

Since

```text
192.168.56.101
```

was Kali's own Host-only IP,

Wireshark displayed

```text
Source

192.168.56.101

↓

Destination

192.168.56.101
```

Meaning

Kali communicated with itself.

No packets reached Metasploitable.

The correct target should have been

```text
192.168.56.102
```

---

# Our Practice Lab Workflow

```text
Windows Host

↓

Oracle VirtualBox

↓

Kali Linux

↓

Metasploitable2
```

Network Configuration

```text
Kali

Adapter 1

↓

NAT

Internet Access

Adapter 2

↓

Host-only

Attack Network

------------------------

Metasploitable

Adapter 1

↓

Host-only

Victim Network
```

Workflow

```text
Find Your IP

↓

Find Live Hosts

↓

Identify Unknown Host

↓

Scan Services

↓

Choose Target

↓

Perform Security Testing
```

Commands

```bash
hostname -I
```

↓

```bash
nmap -sn 192.168.56.0/24
```

↓

```bash
sudo nmap -A 192.168.56.102
```

---

# Final Project Workflow

```text
Phone Hotspot / Router

│

────────────────────────────

│

Kali VM

↓

Ubuntu VM (Suricata IDS)

↓

Victim Machine (Metasploitable)
```

Workflow

```text
Find Live Devices

↓

Identify Victim

↓

Launch Attack

↓

Generate Network Traffic

↓

Suricata Detects Activity

↓

Dashboard Displays Alerts
```

---

# Real-World Penetration Testing Workflow

```text
Receive Authorization

↓

Reconnaissance

↓

Host Discovery

↓

Port Scanning

↓

Service Enumeration

↓

Vulnerability Analysis

↓

Exploitation (If Authorised)

↓

Privilege Escalation

↓

Reporting
```

---

# Interview Questions

### What is Reconnaissance?

Collecting information about the target before performing security testing.

---

### What is Enumeration?

Extracting detailed information from discovered hosts and services.

---

### Difference between Reconnaissance and Enumeration?

Reconnaissance identifies potential targets.

Enumeration gathers detailed information from those targets.

---

### What does Nmap stand for?

Network Mapper.

---

### Why do we use Host Discovery first?

To identify live devices before performing detailed scans.

---

### What does the -sn option do?

Performs Host Discovery only.

No port scanning.

---

### What does the -A option do?

Enables

- OS Detection
- Version Detection
- NSE Scripts
- Traceroute

---

### Why did Source IP and Destination IP become identical?

Because the scan targeted Kali's own IP instead of the victim.

---

### How do attackers find victims?

By performing Host Discovery and Enumeration.

Attackers usually do not know the victim's IP beforehand.

---

### How do you determine the network to scan?

Use

```bash
ip a
```

or

```bash
hostname -I
```

Identify your IP address and subnet.

Example

```text
192.168.56.101/24
```

Network

```text
192.168.56.0/24
```

---

# Common Beginner Mistakes

❌ Scanning your own IP.

❌ Assuming Host Discovery identifies operating systems.

❌ Forgetting to check your own IP before scanning.

❌ Confusing Network Address with Host Address.

❌ Assuming the first discovered host is always the victim.

❌ Ignoring subnet information.

❌ Forgetting that one machine can have multiple network interfaces.

---

# Best Practices

- Perform Reconnaissance before Enumeration.
- Always verify your own IP address.
- Begin with Host Discovery.
- Enumerate only authorised systems.
- Document discovered hosts and services.
- Keep a network diagram of your lab.
- Verify scan results before drawing conclusions.
- Understand your network topology before attacking.
- Use isolated lab environments for practice.
- Follow ethical and legal guidelines for all testing activities.

---

# Commands Learned

```bash
# Show all network interfaces
ip a

# Show current IP addresses
hostname -I

# Display network interfaces (older systems)
ifconfig

# Display all interfaces, including inactive ones
ifconfig -a

# Test connectivity
ping <IP>

# Discover live hosts
nmap -sn <Network>/24

# Aggressive scan
sudo nmap -A <IP>
```

---

# Key Takeaways

- Every device requires a unique IP address.
- Devices on the same network share the same Network ID.
- `/24` means the first 24 bits identify the network.
- `ip a` displays only the current machine's interfaces.
- `hostname -I` quickly shows assigned IP addresses.
- `ping` verifies connectivity.
- `nmap -sn` discovers live hosts.
- `nmap -A` performs detailed enumeration.
- Reconnaissance collects information.
- Enumeration extracts detailed information from discovered systems.
- Always identify the correct target before scanning.
- Host Discovery is the foundation of every penetration test.