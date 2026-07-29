# Virtual Networking

This document explains the networking modes provided by Oracle VirtualBox and how they are used to build isolated cybersecurity labs and multi-machine environments.

---

# Why Virtual Networking?

## Definition

Virtual Networking allows Virtual Machines (VMs) to communicate with the host computer, other virtual machines, physical devices, and the Internet without requiring separate physical network hardware.

## Why is it needed?

- Connect multiple VMs together.
- Simulate real-world computer networks.
- Practice penetration testing safely.
- Build isolated cybersecurity labs.
- Test network attacks and defenses.

## How does it work?

VirtualBox creates virtual Network Interface Cards (NICs) for each VM. These adapters behave like physical Ethernet or Wi-Fi cards and can be connected to different virtual network modes.

## Advantages

- No additional hardware required.
- Safe and isolated testing.
- Flexible network configurations.
- Easy to switch between different network modes.

## Disadvantages

- Incorrect configuration may prevent communication.
- Some network modes have limited functionality.

## Example

```text
Windows Host
      │
VirtualBox
      │
 ┌────┴─────┐
 │          │
Kali VM   Ubuntu VM
```

## Commands

None

## Notes / Best Practices

Choose the networking mode according to your lab requirements instead of always using the default settings.

---

# Virtual Network Adapter

## Definition

A Virtual Network Adapter is a software-based Network Interface Card (NIC) assigned to a Virtual Machine.

## Why is it needed?

Without a network adapter, a VM cannot communicate with any other machine or the Internet.

## How does it work?

VirtualBox emulates a physical network card. The Guest Operating System detects it exactly like real hardware.

Each VM can have multiple network adapters.

## Advantages

- Behaves like a real NIC.
- Supports multiple networking modes.
- Multiple adapters can be attached simultaneously.

## Disadvantages

- Incorrect adapter configuration can isolate the VM.

## Example

```text
Kali VM

Adapter 1
Adapter 2
```

## Commands

None

## Notes / Best Practices

Use separate adapters when a VM requires Internet access and an isolated lab network at the same time.

---

# NAT (Network Address Translation)

## Definition

NAT allows a Virtual Machine to access the Internet through the Host Operating System while hiding the VM from other devices on the network.

## Why is it needed?

Provides Internet access without exposing the VM directly to the local network.

## How does it work?

The Host OS acts as a router.

```text
Internet
     │
Windows Host
     │
VirtualBox NAT
     │
Kali VM
```

The VM sends traffic through the Host, which forwards it to the Internet.

## Advantages

- Internet access.
- Safe default configuration.
- Easy to set up.

## Disadvantages

- Other physical devices usually cannot directly communicate with the VM.
- Not suitable for multi-laptop cybersecurity demonstrations.

## Example

Updating Kali Linux.

```bash
sudo apt update
sudo apt full-upgrade -y
```

## Commands

None

## Notes / Best Practices

Use NAT whenever a VM only needs Internet access.

---

# Host-only Adapter

## Definition

Host-only networking creates a private network between the Host Operating System and Virtual Machines.

## Why is it needed?

To build isolated cybersecurity labs without exposing attack traffic to the Internet or the local network.

## How does it work?

VirtualBox creates its own private virtual network.

```text
Windows Host
      │
Host-only Network
      │
 ┌────┴────┐
 │         │
Kali   Metasploitable2
```

Only devices connected to this Host-only network can communicate.

## Advantages

- Completely isolated.
- Safe for penetration testing.
- Ideal for learning.

## Disadvantages

- No Internet access through this adapter.
- Other physical computers cannot access the VMs.

## Example

Practicing attacks from Kali against Metasploitable2.

## Commands

```bash
ip a

hostname -I

ping <IP_Address>
```

## Notes / Best Practices

Host-only is the recommended mode for practicing attacks on a single computer.

---

# Bridged Adapter

## Definition

Bridged Adapter connects a Virtual Machine directly to the same physical network as the Host Operating System.

## Why is it needed?

Allows VMs on different physical computers to communicate with each other.

## How does it work?

The VM appears as an independent computer on the network.

```text
Phone Hotspot
      │
───────────────
│      │      │
Kali  Ubuntu  Victim
```

Each VM receives its own IP address.

Example

```text
Kali VM             192.168.1.10

Ubuntu IDS          192.168.1.11

Metasploitable2     192.168.1.12
```

## Advantages

- Full communication with other computers.
- Internet access.
- Realistic network simulation.

## Disadvantages

- Less isolated than Host-only.
- Misconfiguration can expose the VM to other devices on the network.

## Example

Used during the final IDS project demonstration.

## Commands

```bash
ip a

hostname -I

ping <IP_Address>
```

## Notes / Best Practices

Use Bridged mode only on trusted networks.

---

# Internal Network

## Definition

Internal Network allows communication only between Virtual Machines connected to the same Internal Network.

## Why is it needed?

Creates a completely isolated virtual network.

## How does it work?

Only VMs connected to the same Internal Network can communicate.

```text
Kali

│

Internal Network

│

Ubuntu

│

Metasploitable2
```

The Host Operating System cannot communicate with these VMs.

## Advantages

- Highest isolation.
- Safe malware testing.
- Ideal for advanced labs.

## Disadvantages

- No Internet.
- Host cannot access the VMs.

## Example

Advanced malware analysis labs.

## Commands

None

## Notes / Best Practices

Use Internal Network only when complete isolation is required.

---

# NAT vs Host-only vs Bridged vs Internal

| Feature | NAT | Host-only | Bridged | Internal |
|----------|-----|-----------|----------|----------|
| Internet Access | ✅ Yes | ❌ No | ✅ Yes | ❌ No |
| VM ↔ Host Communication | ✅ Yes | ✅ Yes | ✅ Yes | ❌ No |
| VM ↔ VM Communication | Limited | ✅ Yes | ✅ Yes | ✅ Yes |
| VM ↔ Other Physical Computers | ❌ No | ❌ No | ✅ Yes | ❌ No |
| Safe for Practicing Attacks | ⭐ Good | ⭐⭐⭐ Best | ⚠️ Use Carefully | ⭐⭐⭐ Best |
| Used During Learning | Sometimes | ✅ Yes | ❌ No | Advanced Labs |
| Used During Final Project | ❌ No | ❌ No | ✅ Yes | ❌ No |

---

# Multiple Network Adapters

## Definition

A Virtual Machine can use more than one network adapter simultaneously.

## Why is it needed?

Different adapters can serve different purposes.

Example:

- One adapter for Internet access.
- One adapter for communication with the lab network.

## Example

```text
Kali

Adapter 1 → NAT

Adapter 2 → Host-only
```

## Advantages

- Internet access.
- Isolated attack network.
- Flexible configurations.

## Disadvantages

- Slightly more complex to configure.

## Notes / Best Practices

This is a common configuration for penetration testing machines.

---

# Practice Lab Setup

## Objective

Practice attacks safely on a single laptop.

```text
Internet
      │
     NAT
      │
   Kali Linux
      │
 Host-only
      │
Metasploitable2
```

## Configuration

### Kali

```text
Adapter 1 → NAT

Adapter 2 → Host-only
```

### Metasploitable2

```text
Adapter 1 → Host-only
```

## Why this setup?

- Kali has Internet for updates and downloading tools.
- Kali and Metasploitable2 communicate through an isolated network.
- Attack traffic never leaves the computer.

---

# Final Project Setup

## Objective

Connect three different laptops during the project demonstration.

```text
                 Phone Hotspot
                       │
───────────────────────┼──────────────────────
        │              │              │
        │              │              │
   Kali VM       Ubuntu VM       Metasploitable2 VM
 (Bridged)      (Bridged)          (Bridged)
```

Each Virtual Machine receives its own IP address from the hotspot.

Example

```text
Kali VM             192.168.43.101

Ubuntu IDS          192.168.43.102

Metasploitable2     192.168.43.103
```

Kali attacks the victim.

Ubuntu monitors the network traffic.

Suricata generates alerts.

Dashboard displays detected attacks.

---

# Why Host-only is used during Practice

## Reasons

- Completely isolated environment.
- Safe penetration testing.
- No risk of attacking other devices.
- No additional hardware required.
- Easy to reset and rebuild.

---

# Why Bridged is used during the Final Demonstration

## Reasons

- All team members use different physical laptops.
- Every VM needs its own IP address.
- The IDS must monitor real network traffic.
- Simulates a real organizational network.
- Allows communication between all project components.

---

# Mobile Hotspot vs Bridged Adapter

Many beginners confuse these two concepts.

A **Mobile Hotspot** is the physical network that devices connect to.

A **Bridged Adapter** is a VirtualBox networking mode that allows a VM to join that physical network as an independent device.

Example

```text
Phone Hotspot
      │
Windows Laptop
      │
VirtualBox
      │
Bridged Adapter
      │
Kali VM
```

The hotspot provides the network.

The Bridged Adapter determines how the VM connects to that network.

---

# Commands Used During Networking

```bash
ip a
```

Displays all network interfaces and their IP addresses.

---

```bash
hostname -I
```

Displays the system's IP address.

---

```bash
ping <IP_Address>
```

Tests network connectivity between two machines.

---

# Best Practices

- Use **Host-only** for practicing attacks on a single computer.
- Use **Bridged** when multiple physical machines need to communicate.
- Use **NAT** when only Internet access is required.
- Create a Snapshot before changing networking settings.
- Verify connectivity using `ping` before starting any security testing.
- Never perform penetration testing on networks or systems without proper authorization.



---

# Changing the Virtual Network Type in Oracle VirtualBox

## Objective

VirtualBox allows each Virtual Machine (VM) to connect to different types of virtual networks. Changing the network type determines how the VM communicates with the Internet, the Host OS, other VMs, and physical computers.

---

# Steps to Change the Network Adapter Type

## Step 1

Shut down the Virtual Machine completely.

> Do **not** use **Save State**.
>
> The VM should be **Powered Off** before changing networking settings.

---

## Step 2

Open **Oracle VirtualBox**.

---

## Step 3

Select the Virtual Machine.

Example

- Kali Linux
- Ubuntu
- Metasploitable2

---

## Step 4

Click

```text
Settings
```

---

## Step 5

Open

```text
Network
```

You will see

```text
Adapter 1

Adapter 2

Adapter 3

Adapter 4
```

Each adapter acts like a separate physical Network Interface Card (NIC).

---

## Step 6

Tick

```text
Enable Network Adapter
```

if it is disabled.

---

## Step 7

From

```text
Attached To
```

select the required networking mode.

Available options include

- NAT
- NAT Network
- Bridged Adapter
- Internal Network
- Host-only Adapter
- Generic Driver

For this project we mainly use

- NAT
- Host-only Adapter
- Bridged Adapter

---

## Step 8

Click

```text
OK
```

Start the Virtual Machine.

---

# Practice Configuration (Single Laptop)

## Objective

Practice penetration testing safely on one laptop.

---

## Kali Linux

### Adapter 1

```text
Attached To

↓

NAT
```

Purpose

- Internet access
- Download tools
- Update Kali
- Install packages

---

### Adapter 2

```text
Attached To

↓

Host-only Adapter
```

Purpose

- Connect Kali to Metasploitable2
- Launch attacks
- Keep attack traffic isolated

---

Final Configuration

```text
Kali

Adapter 1 → NAT

Adapter 2 → Host-only
```

---

## Metasploitable2

Only one adapter is required.

```text
Adapter 1

↓

Host-only Adapter
```

Purpose

- Receive attacks from Kali
- Stay isolated from the Internet

---

Final Configuration

```text
Metasploitable2

Adapter 1 → Host-only
```

---

# Network Diagram (Practice)

```text
                   Internet
                       │
                 Windows Laptop
                       │
                  NAT Adapter
                       │
                 Kali Linux VM
                       │
             Host-only Adapter
                       │
             Metasploitable2 VM
```

---

# Why Use Two Adapters for Kali?

Kali has two different jobs.

Adapter 1

- Download updates
- Install tools
- Internet browsing

Adapter 2

- Attack Metasploitable2
- Scan ports
- Perform penetration testing

Keeping these networks separate is considered good practice.

---

# Checking the Network

Inside Kali

```bash
ip a
```

Shows all network interfaces.

---

```bash
hostname -I
```

Displays the assigned IP addresses.

Since Kali has two adapters, it may have two IP addresses.

Example

```text
NAT

10.0.2.15

Host-only

192.168.56.101
```

---

Test communication

```bash
ping <Metasploitable_IP>
```

If replies are received, the Host-only network is working correctly.

---

# Final Project Configuration (Three Different Laptops)

## Team Members

Laptop 1

Kali Linux VM

↓

Attacker

---

Laptop 2

Ubuntu VM

↓

Suricata IDS

↓

Dashboard

---

Laptop 3

Metasploitable2 VM

↓

Victim Machine

---

# Physical Network

All three laptops connect to the same Wi-Fi network.

This can be

- Mobile Hotspot
- Home Wi-Fi Router
- College Wi-Fi (if permitted)

Example

```text
Phone Hotspot

        │
────────┼────────
        │
 Laptop 1
 Laptop 2
 Laptop 3
```

---

# VirtualBox Configuration

## Kali

Adapter 1

```text
Bridged Adapter
```

---

## Ubuntu

Adapter 1

```text
Bridged Adapter
```

---

## Metasploitable2

Adapter 1

```text
Bridged Adapter
```

---

# Network Diagram (Final Demonstration)

```text
                    Phone Hotspot
                           │
───────────────────────────┼──────────────────────────
            │              │               │
            │              │               │
      Laptop 1        Laptop 2       Laptop 3
            │              │               │
      Kali VM       Ubuntu VM      Metasploitable2 VM
      (Bridged)      (Bridged)         (Bridged)
```

Each VM receives its own IP address.

Example

```text
Kali VM

192.168.43.101

Ubuntu VM

192.168.43.102

Metasploitable2 VM

192.168.43.103
```

---

# Communication Flow During the Demonstration

```text
Kali VM
     │
     │ Attack Traffic
     ▼
Metasploitable2 VM
     │
     │ Network Packets
     ▼
Ubuntu VM (Suricata IDS)
     │
     │ Alerts
     ▼
Dashboard
```

The IDS monitors the network traffic and detects attacks while the victim machine is being targeted.

---

# Switching Between Practice and Demonstration

## Practice Mode

Kali

```text
Adapter 1 → NAT

Adapter 2 → Host-only
```

Metasploitable2

```text
Adapter 1 → Host-only
```

Ubuntu (optional for practice)

```text
Adapter 1 → Host-only
```

---

## Demonstration Mode

Kali

```text
Adapter 1 → Bridged
```

Ubuntu

```text
Adapter 1 → Bridged
```

Metasploitable2

```text
Adapter 1 → Bridged
```

---

# Summary

| Situation | Kali | Ubuntu IDS | Metasploitable2 |
|-----------|------|------------|-----------------|
| Practice Alone | NAT + Host-only | Host-only (optional) | Host-only |
| Final Demonstration | Bridged | Bridged | Bridged |

---

# Best Practices

- Always **Power Off** the VM before changing network settings.
- Verify the IP address after changing the adapter using `ip a` or `hostname -I`.
- Test connectivity using `ping` before starting attacks.
- Use **Host-only** for isolated practice on a single laptop.
- Use **Bridged Adapter** when multiple physical laptops need to communicate on the same network.
- Keep a clean VirtualBox Snapshot before changing networking settings so you can quickly restore a working configuration if needed.