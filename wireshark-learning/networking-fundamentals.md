# Network Fundamentals (Part 1)

> Beginner → Cybersecurity Foundation Notes

---

# What is a Computer Network?

A **computer network** is a group of devices connected together so they can communicate and share data.

Devices can include:

- Computers
- Laptops
- Phones
- Servers
- Routers
- Printers
- IoT Devices

Think of a network as a city.

```
Houses = Devices

Roads = Network cables / Wi-Fi

Letters = Data

Postal Service = Internet
```

Without a network:

- No websites
- No online games
- No WhatsApp
- No YouTube
- No cloud storage

---

# Client vs Server

Most communication follows this model.

## Client

The device requesting something.

Examples:

- Browser
- Mobile App
- Laptop
- Phone

Example:

```
"I want Google's homepage."
```

---

## Server

The computer providing the requested resource.

Examples:

- Google Server
- YouTube Server
- TryHackMe Server

Example:

```
"Here's the webpage."
```

---

## Simple Example

```
You

↓

Browser (Client)

↓

Internet

↓

Google Server

↓

Google Homepage

↓

Back to You
```

---

# What is Data?

Everything sent over a network is data.

Examples:

- Text
- Images
- Passwords
- Videos
- Audio
- Documents

Computers understand only:

```
Binary

0 and 1
```

---

# Why Packets Exist

Imagine downloading a 2 GB movie.

Sending it as one huge file would be risky.

If one tiny part gets lost...

Everything must be sent again.

Instead...

The movie is divided into thousands of small pieces.

These pieces are called:

```
Packets
```

---

# What is a Packet?

A packet is the smallest unit of data sent across a network.

Think of it like a postal envelope.

```
+-------------------------+

HEADER

--------------------------

PAYLOAD

+-------------------------+
```

---

# Packet Header

The Header contains information about the packet.

Examples:

- Source IP
- Destination IP
- Source Port
- Destination Port
- Protocol
- Packet Number

Think:

```
Envelope Information
```

---

# Packet Payload

The Payload is the actual information.

Examples:

```
HTML

Images

Passwords

Messages

Videos
```

Think:

```
Letter inside envelope
```

---

# Header vs Payload

| Header | Payload |
|---------|----------|
| Metadata | Actual data |
| Routing information | Message |
| Helps delivery | Information being delivered |

---

# Why Packets Matter in Cybersecurity

Attackers inspect packets to find:

- Passwords
- Session Cookies
- Login Requests
- API Keys
- Sensitive Data

This is why HTTPS exists.

---

# MAC Address

Every network card has a unique hardware address.

This is called:

```
MAC Address

(Media Access Control)
```

Example:

```
00:0C:29:A4:F1:18
```

---

# Think of MAC Address

```
Fingerprint

or

Serial Number
```

It identifies the physical device.

---

# Important Facts

✔ Built into the network card

✔ Mostly never changes

✔ Used only on local networks

---

# IP Address

An IP Address identifies where a device is located on a network.

Example:

```
192.168.1.25
```

Think:

```
Home Address
```

---

# Difference

Imagine Amazon delivery.

```
MAC

↓

Who are you?

IP

↓

Where do you live?
```

---

# Easy Memory

```
MAC

Identity

IP

Location
```

---

# Private vs Public IP

## Private IP

Used inside your own network.

Examples

```
192.168.x.x

10.x.x.x

172.16.x.x
```

Cannot be accessed directly from the Internet.

---

## Public IP

Assigned by ISP.

Visible on Internet.

Example:

```
49.xx.xx.xx
```

Websites communicate with this address.

---

# IPv4

Most common.

```
192.168.1.10
```

32 bits

About 4.3 Billion addresses.

---

# IPv6

Created because IPv4 addresses were running out.

Example

```
2405:201:3002::
```

128 bits

Almost unlimited addresses.

---

# Ports

An IP tells packets:

```
Which Computer
```

A Port tells packets:

```
Which Program
```

Think of an apartment building.

```
Building

↓

IP Address

Apartment Number

↓

Port
```

---

# Why Ports Exist

Imagine one computer running:

- Chrome
- Discord
- Spotify
- SSH Server
- Web Server

How does data know where to go?

Ports.

---

# Common Ports

| Port | Service |
|------|----------|
|21|FTP|
|22|SSH|
|23|Telnet|
|25|SMTP|
|53|DNS|
|80|HTTP|
|110|POP3|
|143|IMAP|
|443|HTTPS|
|3389|RDP|

---

# Why Pentesters Scan Ports

Open ports mean:

```
A service is running.
```

Example

```
22 Open

↓

SSH Server exists
```

Now the attacker knows:

```
Possible Login Target
```

---

# What is a Protocol?

A protocol is simply:

```
A set of communication rules.
```

Like human languages.

```
English

Hindi

Japanese
```

Computers also need languages.

---

# TCP

Transmission Control Protocol

Most important transport protocol.

Purpose:

```
Reliable communication.
```

It guarantees:

✔ Delivery

✔ Correct order

✔ No missing packets

---

# Where TCP is Used

- Websites
- Banking
- SSH
- Downloads
- Emails

Basically...

Anywhere data loss is unacceptable.

---

# UDP

User Datagram Protocol

Purpose:

```
Fast communication.
```

No guarantee.

No checking.

No retransmission.

---

# Where UDP is Used

- Online Games
- Video Calls
- Voice Calls
- Streaming
- DNS

Speed is more important than perfection.

---

# TCP vs UDP

| TCP | UDP |
|------|------|
|Reliable|Fast|
|Checks delivery|No checking|
|Connection-oriented|Connectionless|
|Slower|Faster|
|Websites|Gaming|

---

# Easy Analogy

TCP

```
Registered Courier

Needs Signature

Tracks Package
```

UDP

```
Throw Letter

Hope It Arrives
```

---

# TCP Three-Way Handshake

Before communication starts...

Both computers agree to communicate.

Step 1

```
Client

SYN

"Can we talk?"
```

---

Step 2

```
Server

SYN-ACK

"Yes!"
```

---

Step 3

```
Client

ACK

"Great!"
```

Connection established.

---

Diagram

```
Client

SYN ------------>

      <---------- SYN ACK

ACK ------------>

Connected
```

---

# Why This Matters

Without a handshake:

The server cannot trust who is talking.

The handshake establishes a reliable connection before any important data (passwords, web pages, files) is exchanged.

---

# Cybersecurity Notes

✔ Nmap scans ports to discover services.

✔ Wireshark captures packets.

✔ Packets contain Header + Payload.

✔ MAC = Physical identity.

✔ IP = Network identity.

✔ Ports identify applications.

✔ TCP = Reliable.

✔ UDP = Fast.

✔ TCP Handshake = SYN → SYN-ACK → ACK.

# Network Fundamentals (Part 2)

> Beginner → Cybersecurity Foundation Notes

---

# Important Network Protocols

A **protocol** is a set of rules that devices follow to communicate.

Think of protocols as different jobs in a company.

```
HTTP   → Delivers websites

DNS    → Finds website addresses

ARP    → Finds devices on your LAN

ICMP   → Checks if devices are alive

TCP    → Reliable delivery

UDP    → Fast delivery
```

Every protocol has one specific purpose.

---

# ARP (Address Resolution Protocol)

## What is ARP?

ARP is responsible for converting an **IP Address into a MAC Address**.

Remember:

```
IP tells WHERE the computer is.

MAC tells WHO the computer is.
```

---

## Why ARP Exists

Imagine your computer wants to send data to:

```
192.168.1.25
```

It knows the IP.

But...

It doesn't know the MAC Address.

Without the MAC Address, it cannot send data over the local network.

So it asks everyone:

```
"Who has 192.168.1.25?"
```

The correct computer replies:

```
"I do."

"My MAC Address is
00:0C:29:A4:F1:18"
```

Now communication begins.

---

## ARP Flow

```
Computer A

↓

Needs to send packet

↓

Knows IP

↓

Doesn't know MAC

↓

Broadcasts ARP Request

↓

Target replies with MAC

↓

Packet is sent
```

---

## Why ARP Matters

Without ARP...

Devices inside the same Wi-Fi network cannot communicate.

---

## Cybersecurity Relevance

Attackers abuse ARP using:

```
ARP Spoofing

ARP Poisoning
```

Purpose:

Pretend to be another device.

Example:

```
Victim

↓

Attacker

↓

Router
```

Now the attacker can intercept traffic.

This is called:

```
Man-in-the-Middle (MITM)
```

---

# ICMP (Internet Control Message Protocol)

## What is ICMP?

ICMP is used to check:

```
Is another device reachable?
```

It sends diagnostic messages.

---

## Most Common Tool

```
ping
```

Example:

```bash
ping google.com
```

---

## What Happens?

Your computer sends:

```
Echo Request
```

The other device replies:

```
Echo Reply
```

---

Diagram

```
Computer

Echo Request

------------>

Server

Echo Reply

<------------
```

---

## Why Pentesters Use Ping

Before attacking a machine...

First check:

```
Is it alive?
```

If Ping succeeds

↓

Machine is reachable.

---

## Cybersecurity Relevance

Some administrators disable ICMP.

Why?

To hide systems from attackers performing reconnaissance.

---

# DNS (Domain Name System)

## What is DNS?

Humans remember names.

Computers understand numbers.

DNS translates:

```
google.com

↓

142.250.xxx.xxx
```

Think of DNS as:

```
Internet Phonebook
```

---

## Without DNS

Instead of typing:

```
google.com
```

You would have to remember:

```
142.250.190.46
```

Impossible for thousands of websites.

---

## DNS Lookup Process

You type:

```
tryhackme.com
```

↓

DNS Server is asked

↓

DNS finds IP

↓

Returns IP

↓

Browser connects

↓

Website loads

---

Diagram

```
Browser

↓

DNS Query

↓

DNS Server

↓

Returns IP Address

↓

Browser connects

↓

Website Opens
```

---

## Common Command

```bash
nslookup google.com
```

Purpose:

```
Find the IP Address of a domain.
```

---

## Cybersecurity Uses

DNS can reveal:

- Internal infrastructure
- Hidden subdomains
- Server locations

Attackers often perform DNS Enumeration.

---

# HTTP & HTTPS

## What is HTTP?

HTTP stands for:

```
HyperText Transfer Protocol
```

It is the protocol used to transfer web pages.

---

Example

```
Browser

↓

GET /index.html

↓

Server

↓

Returns webpage
```

---

Problem:

HTTP is NOT encrypted.

Anyone intercepting packets can read:

- Usernames
- Passwords
- Cookies
- Messages

---

# HTTPS

HTTPS is:

```
HTTP

+

TLS Encryption
```

Now packets become encrypted.

Attackers can still capture them...

But they cannot understand the contents.

---

Think

HTTP

```
Postcard

Everyone can read it.
```

HTTPS

```
Locked Safe

Only sender and receiver
have the key.
```

---

# Why HTTPS Matters

Without HTTPS:

Wireshark can literally display:

```
Username

Password

Cookies

Messages
```

With HTTPS:

You'll mostly see encrypted data.

---

# Data Encapsulation

## What is Encapsulation?

When data travels through a network...

Every layer adds its own information.

Think of shipping a package.

```
Gift

↓

Gift Box

↓

Shipping Box

↓

Address Label

↓

Truck
```

Computers do exactly the same.

---

## Layer-by-Layer

Application creates data.

↓

TCP adds TCP Header.

↓

IP adds IP Header.

↓

Ethernet adds Ethernet Header.

↓

Network sends Frame.

---

Diagram

```
Application Data

↓

TCP Header

↓

IP Header

↓

Ethernet Header

↓

Network Cable/Wi-Fi
```

---

Each layer wraps the previous one.

Like Russian nesting dolls.

---

# Decapsulation

At the receiving computer...

Everything happens backwards.

Ethernet Header removed.

↓

IP Header removed.

↓

TCP Header removed.

↓

Original data delivered.

---

Diagram

```
Frame

↓

Packet

↓

Segment

↓

Application Data
```

---

# Why Encapsulation Exists

Each layer has a different job.

Ethernet

↓

Local delivery

IP

↓

Routing

TCP

↓

Reliable communication

Application

↓

Actual information

---

# Packet Journey Example

Imagine opening Google.

Step 1

You type

```
google.com
```

↓

Browser creates HTTP request.

---

Step 2

TCP adds reliability.

---

Step 3

IP adds destination address.

---

Step 4

Ethernet adds MAC Addresses.

---

Step 5

Packet travels across routers.

---

Step 6

Google receives packet.

---

Step 7

Headers removed.

---

Step 8

Google sends webpage back.

---

# Why This Matters in Cybersecurity

When using Wireshark...

You'll literally see:

```
Ethernet

↓

Internet Protocol

↓

TCP

↓

HTTP
```

Every packet follows this structure.

Understanding these layers makes packet analysis much easier.

---

# Most Important Things to Remember

```text
ARP = IP → MAC

ICMP = Ping

DNS = Domain → IP

HTTP = Unencrypted Web

HTTPS = Encrypted Web

Encapsulation =
Every layer adds its own header.

Decapsulation =
Headers removed at destination.

TCP ensures reliability.

IP handles routing.

Ethernet handles local delivery.
```

---

# 30-Second Revision

```text
ARP → Find MAC

ICMP → Ping

DNS → Find IP

HTTP → Normal Web

HTTPS → Secure Web

Encapsulation

Application
↓

TCP
↓

IP
↓

Ethernet

Destination removes each layer
in reverse order.
```

