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