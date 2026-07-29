# VirtualBox Notes

This document contains the fundamental concepts of virtualization and Oracle VirtualBox that are required for building cybersecurity labs.

---

# What is Virtualization?

## Definition

Virtualization is the process of creating a virtual (software-based) version of a computer instead of using separate physical hardware. It allows multiple operating systems to run independently on a single physical machine.

## Why is it needed?

- Run multiple operating systems on one computer.
- Build isolated cybersecurity labs.
- Test software safely.
- Practice penetration testing without affecting the host system.
- Save hardware costs.

## How does it work?

A virtualization software called a **hypervisor** creates Virtual Machines (VMs). Each VM behaves like a completely independent computer with its own CPU, RAM, storage, operating system, and network adapters.

## Advantages

- Safe testing environment
- Isolation between systems
- Multiple operating systems on one computer
- Easy backup and recovery using snapshots
- Cost-effective

## Disadvantages

- Consumes RAM, CPU, and storage.
- Performance is slightly lower than running directly on physical hardware.
- Requires virtualization support (Intel VT-x / AMD-V).

## Example

Windows Laptop

↓

Oracle VirtualBox

↓

Kali Linux VM

↓

Metasploitable2 VM

## Commands

None

## Notes / Best Practices

- Always allocate resources according to your hardware.
- Keep enough RAM available for the host operating system.
- Use snapshots before making major changes.

---

# Hypervisor

## Definition

A Hypervisor is software that creates and manages Virtual Machines.

## Why is it needed?

Without a hypervisor, virtual machines cannot run.

## How does it work?

The hypervisor shares the host computer's CPU, RAM, storage, and other hardware resources among multiple virtual machines.

## Advantages

- Efficient hardware utilization
- Resource management
- VM isolation

## Disadvantages

- Uses host system resources.

## Example

Oracle VirtualBox is a Type-2 Hypervisor.

## Commands

None

## Notes / Best Practices

Common hypervisors include:

- Oracle VirtualBox
- VMware Workstation
- Hyper-V
- KVM

---

# Host Operating System (Host OS)

## Definition

The Host OS is the operating system installed directly on the physical computer.

## Why is it needed?

It provides hardware access and runs the hypervisor.

## How does it work?

The hypervisor runs as an application on the Host OS.

## Advantages

- Controls physical hardware.
- Runs normal applications alongside virtual machines.

## Example

Windows 11 running Oracle VirtualBox.

## Commands

None

## Notes / Best Practices

Only one Host OS exists on a computer.

---

# Guest Operating System (Guest OS)

## Definition

A Guest OS is an operating system running inside a Virtual Machine.

## Why is it needed?

Allows running different operating systems without replacing the Host OS.

## How does it work?

The Guest OS believes it has its own hardware, while VirtualBox provides virtual hardware.

## Advantages

- Safe testing
- Easy installation
- Isolation from Host OS

## Example

Kali Linux

Ubuntu

Metasploitable2

## Commands

None

## Notes / Best Practices

Each Guest OS has its own files, settings, and network configuration.

---

# Virtual Machine (VM)

## Definition

A Virtual Machine is a software-based computer that behaves like a physical computer.

## Why is it needed?

To safely run another operating system without modifying the Host OS.

## How does it work?

The VM uses virtual CPU, RAM, storage, graphics, and networking provided by the hypervisor.

## Advantages

- Isolation
- Easy cloning
- Snapshots
- Safe malware testing

## Disadvantages

- Slower than physical hardware.
- Limited by host resources.

## Example

Our Kali Linux VM.

## Commands

None

## Notes / Best Practices

Treat every VM as if it were an independent physical computer.

---

# Virtual Hard Disk

## Definition

A Virtual Hard Disk stores all files of a Virtual Machine.

## Why is it needed?

Without a virtual disk, the VM cannot store an operating system or data.

## How does it work?

The virtual hard disk is stored as a file on the Host OS.

## Types

### VDI

VirtualBox Disk Image

Native VirtualBox format.

### VMDK

Virtual Machine Disk

Originally developed for VMware but also supported by VirtualBox.

### VHD

Virtual Hard Disk

Developed by Microsoft.

## Advantages

- Portable
- Easy backup
- Easy copying

## Disadvantages

Large file sizes.

## Example

kali-linux-2026.2-virtualbox-amd64.vdi

## Commands

None

## Notes / Best Practices

Store virtual disks on a drive with plenty of free space.

---

# Oracle VirtualBox Installation

## Definition

Oracle VirtualBox is a free Type-2 hypervisor used to create and manage Virtual Machines.

## Why is it needed?

It provides the virtualization platform for our cybersecurity lab.

## How does it work?

VirtualBox creates virtual hardware for Guest Operating Systems.

## Advantages

- Free
- Cross-platform
- Snapshot support
- Easy networking

## Example

VirtualBox Version 7.2.8

## Commands

None

## Notes / Best Practices

Always use the latest stable version.

---

# VirtualBox Extension Pack

## Definition

The Extension Pack adds extra features that are not included in the default VirtualBox installation.

## Why is it needed?

It enables advanced hardware support.

## Features

- USB 2.0 / USB 3.0 support
- NVMe support
- Disk encryption
- Webcam passthrough
- Remote Desktop (VRDP)

## Advantages

Improves hardware compatibility.

## Disadvantages

Not required for basic cybersecurity labs.

## Commands

None

## Notes / Best Practices

Install the version that matches your VirtualBox version.

---

# Importing Kali Linux VM

## Definition

Importing means adding a pre-built Kali Linux Virtual Machine into VirtualBox.

## Why is it needed?

It saves time because Kali is already installed and configured.

## How does it work?

VirtualBox loads the provided VDI/VBOX files instead of installing Kali manually.

## Example

Machine

↓

Open

↓

Select the .vbox file

## Commands

None

## Notes / Best Practices

Use the official pre-built VirtualBox image from Kali's website.

---

# Virtual Machine Settings

## RAM

### Definition

Memory allocated to the VM.

### Best Practice

Allocate enough RAM for smooth performance while leaving sufficient memory for the Host OS.

---

## CPU

### Definition

Virtual processor cores assigned to the VM.

### Best Practice

Do not allocate all CPU cores to the VM.

---

## Video Memory

### Definition

Memory reserved for graphics.

### Best Practice

Increase video memory for smoother graphical performance.

---

## Graphics Controller

### Definition

Controls virtual graphics hardware.

### Best Practice

Use **VBoxSVGA** for Linux guests.

---

## 3D Acceleration

### Definition

Allows limited GPU acceleration inside the VM.

### Best Practice

Enable it for better graphical performance unless it causes compatibility issues.

---

# Snapshots

## Definition

A Snapshot saves the complete state of a Virtual Machine at a specific point in time.

## Why is it needed?

Allows returning to a previous working state if something breaks.

## Advantages

- Instant recovery
- Safe experimentation
- Easy rollback

## Disadvantages

Snapshots consume additional disk space.

## Example

Fresh Kali Installation

↓

Snapshot

↓

Experiment

↓

Restore Snapshot if needed

## Commands

None

## Notes / Best Practices

Create a snapshot immediately after completing a clean installation and system update.

---

# Shared Clipboard

## Definition

Allows copying and pasting between the Host OS and Guest OS.

## Why is it needed?

Makes transferring text much easier.

## Modes

- Disabled
- Host to Guest
- Guest to Host
- Bidirectional

## Notes / Best Practices

Use **Bidirectional** when needed.

---

# Shared Folders

## Definition

Allows sharing folders between the Host OS and Guest OS.

## Why is it needed?

Makes file transfer easier.

## Advantages

- No USB required
- Faster file sharing

## Disadvantages

Can reduce isolation if sensitive files are shared.

## Notes / Best Practices

Share only folders that are necessary.

---

# Our Cybersecurity Lab Architecture

```text
Windows Laptop
        │
        ▼
Oracle VirtualBox
        │
 ┌──────┴────────┐
 │               │
 ▼               ▼
Kali Linux   Metasploitable2
```

## Notes

- Windows is the Host Operating System.
- Oracle VirtualBox is the Hypervisor.
- Kali Linux and Metasploitable2 are Guest Operating Systems.
- Each Guest OS behaves like an independent computer.
- Networking between the VMs will be configured separately.