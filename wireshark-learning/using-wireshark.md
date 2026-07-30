# Network Fundamentals (Part 3)

> Beginner → Cybersecurity Foundation Notes

---

# Wireshark

## What is Wireshark?

**Wireshark** is the world's most popular **packet analyzer (packet sniffer).**

It captures network traffic and allows you to inspect **every packet** travelling through a network.

Think of Wireshark as:

```text
A CCTV Camera

for Network Traffic
```

Instead of recording people...

It records packets.

---

# Why Cybersecurity Professionals Use Wireshark

Wireshark helps you:

- Analyze network traffic
- Troubleshoot network problems
- Detect malware communication
- Capture passwords sent over HTTP
- Investigate incidents
- Understand how protocols work
- Perform digital forensics

Nearly every:

- SOC Analyst
- Blue Teamer
- Incident Responder
- Malware Analyst
- Pentester

uses Wireshark.

---

# Packet Sniffing

Packet Sniffing means:

```text
Capturing packets
travelling across a network.
```

Example:

```
Laptop

↓

Router

↓

Internet
```

Wireshark captures those packets and shows exactly what was sent.

---

# Promiscuous Mode

Normally...

A Network Interface Card (NIC) only accepts packets meant for itself.

In **Promiscuous Mode**:

The NIC accepts **all packets** it can see.

Think:

```
Normal Mode

"I'll only read my own letters."

Promiscuous Mode

"I'll read every letter passing by."
```

This is why Wireshark can inspect traffic from many devices (depending on the network setup).

---

# Wireshark Interface

When you open a capture...

You will see **3 important panes.**

---

## 1. Packet List Pane

Located at the top.

Shows every captured packet.

Example:

```
No.

Time

Source

Destination

Protocol

Length

Info
```

Think:

```text
Table of Contents
```

---

## 2. Packet Details Pane ⭐

The most important section.

Shows every protocol layer inside the selected packet.

Example:

```
Ethernet II

↓

Internet Protocol (IP)

↓

Transmission Control Protocol (TCP)

↓

HTTP
```

Each layer can be expanded.

Example:

```
TCP

▼

Source Port

Destination Port

Flags

Sequence Number

Acknowledgement Number
```

This is where analysts spend most of their time.

---

## 3. Packet Bytes Pane

Shows the packet's raw contents.

Left side:

```
Hexadecimal
```

Right side:

```
ASCII Text
```

Example:

```
48 54 54 50

↓

HTTP
```

Useful for:

- Malware Analysis
- Reverse Engineering
- Forensics

---

# Display Filters

A packet capture may contain:

```
10 packets

100 packets

10,000 packets

100,000 packets
```

Reading everything is impossible.

Filters allow you to display only the packets you care about.

---

# Most Important Filters

## Show only IP traffic

```text
ip
```

---

## Show traffic to or from an IP

```text
ip.addr == 192.168.1.10
```

---

## Source IP only

```text
ip.src == 192.168.1.10
```

---

## Destination IP only

```text
ip.dst == 192.168.1.20
```

---

## TCP Only

```text
tcp
```

---

## UDP Only

```text
udp
```

---

## ICMP Only

```text
icmp
```

Useful when analyzing:

```
Ping
```

---

## DNS Only

```text
dns
```

Shows:

- Queries
- Responses

---

## HTTP Only

```text
http
```

Shows:

- GET Requests
- POST Requests
- Responses

---

## Specific Port

```text
tcp.port == 80
```

Only traffic on Port 80.

---

## POST Requests

```text
http.request.method == "POST"
```

Very useful during:

- Login analysis
- Form submissions

---

# Follow TCP Stream ⭐

One of Wireshark's most powerful features.

Packets belonging to the same conversation are scattered throughout the capture.

Instead of reading hundreds of packets...

Wireshark can rebuild the entire conversation.

---

How?

```
Right Click Packet

↓

Follow

↓

TCP Stream
```

---

Example

Instead of seeing:

```
Packet 15

Packet 27

Packet 46

Packet 80
```

Wireshark combines them into:

```
Complete Conversation
```

---

Very useful for reading:

- HTTP Requests
- HTTP Responses
- Telnet Sessions
- FTP Commands

---

# Practical Traffic Generation

To understand protocols...

Generate traffic yourself.

---

## ICMP

```bash
ping -c 4 8.8.8.8
```

Produces:

```
Echo Request

Echo Reply
```

Filter:

```
icmp
```

---

## DNS

```bash
nslookup example.com
```

Produces:

```
DNS Query

DNS Response
```

Filter:

```
dns
```

---

## HTTP

```bash
curl http://example.com
```

Produces:

```
HTTP GET

↓

HTTP 200 OK
```

Filter:

```
http
```

---

# Reading a Packet

Suppose you click an HTTP packet.

Packet Details might look like:

```
Ethernet II

↓

Internet Protocol Version 4

↓

Transmission Control Protocol

↓

Hypertext Transfer Protocol
```

This is **encapsulation** in action.

Each protocol has added its own header.

---

# HTTP Packet Example

```
GET /index.html HTTP/1.1

Host: example.com

User-Agent: Chrome
```

This tells us:

- Method
- Requested Page
- Website
- Browser

---

# DNS Packet Example

```
Query:

example.com

↓

Response

93.184.216.34
```

Meaning:

```
DNS translated the domain into an IP.
```

---

# ICMP Packet Example

```
Echo Request

↓

Echo Reply
```

Meaning:

```
Target is reachable.
```

---

# TCP Packet Example

```
SYN

↓

SYN ACK

↓

ACK
```

Meaning:

```
Connection Established
```

---

# Why Pentesters Love Wireshark

Wireshark helps identify:

- Credentials sent over HTTP
- Session Cookies
- API Requests
- DNS Requests
- Hidden Endpoints
- Malware Traffic
- Beaconing
- C2 Communication

---

# Why Blue Teams Love Wireshark

Blue Team analysts use Wireshark to:

- Investigate attacks
- Find suspicious connections
- Detect malware
- Verify alerts
- Analyze phishing
- Investigate data theft

---

# Common Beginner Mistakes

❌ Looking at every packet manually

✔ Use display filters

---

❌ Ignoring Packet Details

✔ Expand every protocol layer

---

❌ Forgetting Follow TCP Stream

✔ Reconstruct conversations

---

❌ Memorizing every field

✔ Understand what each protocol is responsible for

---

# Real Cybersecurity Workflow

```
Capture Packets

↓

Apply Filters

↓

Find Interesting Traffic

↓

Inspect Packet Details

↓

Follow TCP Stream

↓

Understand Communication

↓

Identify Suspicious Activity
```

---

# Memory Tricks

```text
Packet = Letter

Header = Envelope

Payload = Letter Inside

MAC = Identity

IP = Address

Port = Apartment

TCP = Reliable Courier

UDP = Fast Delivery

ARP = Find MAC

DNS = Internet Phonebook

ICMP = Ping

HTTP = Normal Website

HTTPS = Secure Website

Wireshark = CCTV for Networks

Packet List = Table of Contents

Packet Details = Most Important

Packet Bytes = Raw Data

Follow TCP Stream = Entire Conversation
```

---

# Complete Networking Flow (Everything Together)

```
1. User types:

google.com

↓

2. DNS

Find Google's IP Address

↓

3. Browser creates HTTP Request

↓

4. TCP performs
SYN → SYN-ACK → ACK

↓

5. TCP adds Header

↓

6. IP adds Header

↓

7. Ethernet adds Header

↓

8. Packet travels through network

↓

9. Google receives packet

↓

10. Google sends HTTP Response

↓

11. Wireshark can capture every packet in this journey
```

---

# 60-Second Revision

```text
Network = Connected Devices

Packet = Header + Payload

MAC = Physical Identity

IP = Network Address

Port = Application

Protocol = Communication Rules

TCP = Reliable

UDP = Fast

ARP = IP → MAC

DNS = Domain → IP

ICMP = Ping

HTTP = Unencrypted

HTTPS = Encrypted

Encapsulation = Layers add headers

Wireshark = Packet Analyzer

3 Panes:
• Packet List
• Packet Details ⭐
• Packet Bytes

Best Filters:
ip
tcp
udp
icmp
dns
http

Best Feature:
Follow TCP Stream
```