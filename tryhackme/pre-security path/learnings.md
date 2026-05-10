# MODULE 1

---

## IP Address
- Identifies a device on a network.
- Types:
  - Public IP → visible on internet.
  - Private IP → used inside local networks.
- IPv4 example:
```bash
192.168.1.1
```

### Important
- Devices in same network usually have similar starting numbers.
- IP addresses can change (dynamic IPs).

---

## MAC Address
- Unique hardware address of a device.
- Works at Layer 2 (Data Link Layer).
- Example:
```bash
00:1A:2B:3C:4D:5E
```

### Important
- Used for communication inside local network.
- Usually permanent.
- Can be spoofed/changed.

---

## IP vs MAC Address

| IP Address | MAC Address |
|---|---|
| Logical address | Physical hardware address |
| Can change | Usually fixed |
| Used across networks/internet | Used inside local network |
| Layer 3 | Layer 2 |

---

## MAC Spoofing
- Changing visible MAC address of a device.
- Used for:
  - Privacy
  - Security testing
  - Bypassing MAC filters

### Note
- Can also be abused maliciously.

---

## Ping Command
Used to test connectivity between devices.

### Basic Usage
```bash
ping google.com
```

### Important Things
- Checks if target is reachable.
- Shows latency (response time).
- Detects packet loss.

### Terms
- `TTL` → Time To Live
- `time=` → response speed in milliseconds

### Useful Command
```bash
ping -c 4 google.com
```

---

## ifconfig Command
Used to view network interface information in Linux.

### Basic Usage
```bash
ifconfig
```

### Important Fields
- `inet` → IPv4 address
- `ether` → MAC address
- `RX packets` → received data
- `TX packets` → transmitted data
- `netmask` → network range
- `broadcast` → sends data to all devices in network

### What I Practiced
- Checked real IP address.
- Checked real MAC address.
- Understood sections of `ifconfig` output.
- Used `ping` for connectivity testing.

---

## Commands To Remember
```bash
ifconfig
ping google.com
ping -c 4 google.com
```

---

## Quick Revision
- IP = identifies device on network.
- MAC = identifies hardware.
- Ping = tests connectivity.
- ifconfig = shows network details.
- MAC spoofing = changing visible MAC address.






# Module 2 - DNS

---

## DNS (Domain Name System)
- DNS gives names to IP addresses.
- Makes websites easier for humans to remember.

Example:
```text
142.x.x.x → google.com
```

### Important
- Without DNS, we would need to remember IP addresses.
- DNS helps connect domain names to IP addresses.

---

## Domain Structure

Example:
```text
sub.example.com
```

### Parts
- `.com` → Top Level Domain (TLD)
- `example` → Second Level Domain
- `sub` → Subdomain

---

## Top Level Domain (TLD)
- Last part of domain name.

Examples:
```text
.com
.org
.net
.edu
```

---

## Second Level Domain
- Main name of website.

Example:
```text
google
```

---

## Subdomain
- Small section added before main domain.

Examples:
```text
mail.google.com
blog.website.com
```

---

## DNS Record Types

### A Record
- Connects domain to IPv4 address.

---

### AAAA Record
- Connects domain to IPv6 address.

---

### MX Record
- Used for mail servers.

---

### CNAME Record
- Alias for another domain.

---

### TXT Record
- Stores text information in DNS.

---

## TTL (Time To Live)
- Shows how long DNS information is stored before refreshing.

---

## dig Command
Used to get DNS information.

### Commands Practiced
```bash
dig google.com
dig +short google.com
dig google.com A
dig google.com MX
dig google.com CNAME
```

### What I Practiced
- Extracted DNS records.
- Used `+short` for shorter output.
- Viewed TTL values.

---

## nslookup Command
Used for DNS lookups.

### Commands Practiced
```bash
nslookup google.com
nslookup 8.8.8.8
nslookup -type=MX google.com
```

### What I Practiced
- Converted domain → IP.
- Converted IP → domain.
- Checked DNS record types.

---

## Quick Revision
- DNS gives names to IP addresses.
- TLD = `.com`, `.org`, etc.
- Subdomain comes before main domain.
- A = IPv4
- AAAA = IPv6
- MX = mail server
- CNAME = alias
- TXT = text information
- dig = DNS info tool
- nslookup = DNS lookup tool
- TTL = DNS cache time


