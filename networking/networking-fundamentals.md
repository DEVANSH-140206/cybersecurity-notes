> These notes contain concise networking fundamentals focused on cybersecurity and practical understanding.

# Networking Fundamentals

## Networking Basics
- Networking allows devices to communicate and exchange data.
- Main goal: transfer data from one device to another reliably.

---

# Important Devices

## Router
- Connects different networks
- Works at Layer 3 (Network Layer)
- Uses IP addresses
- Responsible for routing packets between networks

## Switch
- Connects devices within the same local network
- Works at Layer 2 (Data Link Layer)
- Uses MAC addresses

## NIC (Network Interface Card)
- Hardware that connects a device to a network
- Every NIC has a unique MAC address

---

# MAC Address
- Layer 2 address
- 48-bit hexadecimal address
- Used for hop-to-hop communication inside local networks

Example formats:
```text
AA-BB-CC-DD-EE-FF
AA:BB:CC:DD:EE:FF
AABB.CCDD.EEFF
```

Important:
- Every NIC has a unique MAC address
- MAC addresses change at every hop

---

# IP Address
- Layer 3 address
- 32-bit address in IPv4
- Written as 4 octets

Example:
```text
192.168.1.1
```

Range of each octet:
```text
0 - 255
```

Purpose:
- End-to-end communication across networks

Important:
- IP addresses usually remain the same from source to destination

---

# OSI Model

## Layer 1 — Physical Layer
Purpose:
- Transfers raw bits (1s and 0s)

Examples:
- Cables
- Signals

---

## Layer 2 — Data Link Layer
Purpose:
- Hop-to-hop delivery

Uses:
- MAC addresses

Devices:
- Switches
- NICs

---

## Layer 3 — Network Layer
Purpose:
- End-to-end delivery

Uses:
- IP addresses

Devices:
- Routers

---

## Layer 4 — Transport Layer
Purpose:
- Service-to-service delivery
- Ensures correct application receives correct data

Uses:
- Port numbers

Protocols:
- TCP
- UDP

---

# TCP vs UDP

## TCP
- Reliable
- Connection-oriented
- Error checking
- Slower

Common uses:
- HTTP/HTTPS
- SSH
- FTP

---

## UDP
- Faster
- Connectionless
- No delivery guarantee
- Lower overhead

Common uses:
- DNS
- Gaming
- Streaming

---

# Ports
Ports identify services/applications running on a system.

Range:
```text
0 - 65535
```

Important Ports:

| Port | Protocol | Service |
|------|----------|---------|
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 22 | TCP | SSH |
| 53 | UDP/TCP | DNS |

---

# Packet Flow

## Layer 3 Header Adds:
- Source IP
- Destination IP

Purpose:
- End-to-end delivery

---

## Layer 2 Header Adds:
- Source MAC
- Destination MAC

Purpose:
- Hop-to-hop delivery

Important:
- Routers remove and rebuild Layer 2 headers at every hop

---

# Why Both IP and MAC Addresses Exist

## MAC Address
- Local communication
- Device-to-device delivery

## IP Address
- Global communication
- Identifies end devices across networks

---

# ARP (Address Resolution Protocol)
Purpose:
- Maps IP addresses to MAC addresses

Important:
- Connects Layer 2 and Layer 3 communication

---

# Clients and Servers

## Client
Requests services/data.

Examples:
- Browser
- Game client
- Chat application

---

## Server
Responds to requests.

Examples:
- Web server
- Chat server
- DNS server

---

# HTTP vs HTTPS

## HTTP
- Unencrypted communication
- Port 80

## HTTPS
- Encrypted secure communication
- Port 443

---

# Important Networking Terms

## Packet
Unit of data sent across a network.

## Hop
Movement of data from one device/router to another.

## End-to-End Delivery
Data moving from source device to destination device.

## Hop-to-Hop Delivery
Data moving between neighboring devices.

---

# Main Things To Remember
- Switches use MAC addresses
- Routers use IP addresses
- Layer 2 = hop-to-hop delivery
- Layer 3 = end-to-end delivery
- Layer 4 uses ports
- TCP = reliable
- UDP = fast
- MAC addresses change every hop
- IP addresses usually stay the same
- ARP maps IP addresses to MAC addresses