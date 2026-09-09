# 🔴 Module 06 — Ethical Hacking

This module provides hands-on practical exercises covering common ethical hacking and penetration testing techniques in an isolated VMware laboratory environment.

The demonstrations focus on controlled security testing, privilege escalation, persistence concepts, system auditing, and log analysis.

---

## 🖥️ Lab Environment

| Machine | Role |
|---|---|
| Kali Linux | Attacker / Security Testing |
| Windows 10 | Windows Target |
| Metasploitable 2 | Vulnerable Linux Target |
| Windows Server 2022 | Active Directory Lab |

> **Note:** IP addresses may differ depending on the VMware network configuration used during the workshop.

---

# 📚 Labs

## 🔴 Lab 01 — Gain Access

This lab introduces controlled techniques used during security assessment and gaining access to vulnerable systems.

### 1.1 Active Online Attack Using Responder

Demonstrates how Responder can be used in an isolated lab to observe and analyze network authentication traffic.

👉 **[Open Demonstration](<Demonstrations/Lab-01-Gain-Access/Lab 1.1 -Active Online Attack Using Responder.md>)**

### 1.2 Audit System Passwords Using L0phtCrack

Demonstrates password auditing using L0phtCrack in the controlled laboratory environment.

👉 **[Open Demonstration](<Demonstrations/Lab-01-Gain-Access/Lab 1.2 -Audit System Passwords Using L0phtCrack.md>)**

### 1.3 Find Vulnerabilities Using Exploit Research

Demonstrates researching known vulnerabilities and understanding available exploit information.

👉 **[Open Demonstration](<Demonstrations/Lab-01-Gain-Access/Lab 1.3 -Find Vulnerabilities Using Exploit Research.md>)**

### 1.5 Gain Access to a Remote System Using Armitage

Demonstrates controlled remote-system exploitation using Armitage in the isolated lab.

👉 **[Open Demonstration](<Demonstrations/Lab-01-Gain-Access/Lab 1.5 -Gain Access to a Remote System Using Armitage.md>)**

---

## 🟠 Lab 02 — Linux Privilege Escalation

This lab introduces privilege-escalation concepts on a deliberately vulnerable Linux system.

### 2.1 Linux Privilege Escalation

Demonstrates enumeration and privilege-escalation techniques against the controlled Linux laboratory target.

👉 **[Open Demonstration](<Demonstrations/Lab-02-Linux-Privilege-Escalation/Lab 2.1 -Linux Privilege Escalation.md>)**

---

## 🟡 Lab 03 — Maintain Remote Access and Hide Malicious Activities

This lab demonstrates selected persistence and information-hiding concepts in the controlled workshop environment.

### 3.1 Hide Files Using NTFS Alternate Data Streams

Demonstrates the use of NTFS Alternate Data Streams to store data outside the normal visible file content.

👉 **[Open Demonstration](<Demonstrations/Lab-03-Maintain-Remote-Access-and-Hide-Malicious-Activities/Lab 3.1 -Hide Files Using NTFS Alternate Data Streams.md>)**

### 3.2 Image Steganography Using OpenStego

Demonstrates hiding information inside an image using OpenStego.

👉 **[Open Demonstration](<Demonstrations/Lab-03-Maintain-Remote-Access-and-Hide-Malicious-Activities/Lab 3.2 -Image Steganography Using OpenStego.md>)**

### 3.3 Boot / Logon Autostart Persistence

Demonstrates a controlled Windows startup persistence mechanism using the Startup folder.

👉 **[Open Demonstration](<Demonstrations/Lab-03-Maintain-Remote-Access-and-Hide-Malicious-Activities/Lab-3.3-Boot-Logon-Autostart-Persistence.md>)**

---

## 🟢 Lab 04 — Clear Logs / Analyze Evidence of Compromise

This lab focuses on Windows and Linux auditing and log-management concepts.

### 4.1 Audit Policies Using Auditpol

Demonstrates examining and managing Windows audit policies using `auditpol`.

👉 **[Open Demonstration](<Demonstrations/Lab-04-Clear-Logs-to-Hide-the-Evidence-of-Compromise/Lab 4.1 -Audit Policies Using Auditpol.md>)**

### 4.2 Windows Event Logs

Demonstrates examining Windows Event Logs and understanding security-relevant events.

👉 **[Open Demonstration](<Demonstrations/Lab-04-Clear-Logs-to-Hide-the-Evidence-of-Compromise/Lab 4.2 -Windows Event Logs.md>)**

### 4.3 Linux Log Analysis

Demonstrates examining Linux logs for security events and system activity.

👉 **[Open Demonstration](<Demonstrations/Lab-04-Clear-Logs-to-Hide-the-Evidence-of-Compromise/Lab 4.3 -Linux Log Analysis.md>)**

---

# 📥 Installation Guides

Installation instructions for the tools used in Module 06 are maintained separately.

### Kali Linux

👉 **[Kali Tools Installation Guide](Installation-Guide/Kali-Tools.md)**

### Windows

👉 **[Windows Tools Installation Guide](Windows-Tools-Installation-Guide.md)**

---

# 🧪 Demonstrations

All practical demonstrations are available in the `Demonstrations` directory.

👉 **[📂 Module 06 Demonstrations](Demonstrations/)**

The current demonstrations cover:

- Network authentication traffic analysis
- Password auditing
- Vulnerability research
- Controlled remote-system exploitation
- Linux privilege escalation
- NTFS Alternate Data Streams
- Image steganography
- Windows startup persistence
- Windows audit policies
- Windows Event Log analysis
- Linux log analysis

---

# 🔬 Practical Workflow

The demonstrations follow a controlled ethical-hacking workflow:

```text
                    Lab Environment
                          │
                          ▼
                 Reconnaissance /
                 Vulnerability Research
                          │
                          ▼
                  Controlled Access
                          │
                          ▼
                Privilege Escalation
                          │
                          ▼
             Persistence / Hiding Concepts
                          │
                          ▼
                 Auditing & Logging
                          │
                          ▼
                  Evidence Analysis

Each activity is performed against intentionally configured laboratory systems.

🌐 Network Setup

The laboratory uses a VMware Host-Only Network to provide an isolated environment for security testing.

                VMware Host-Only Network
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      Kali Linux     Windows 10    Metasploitable 2
       Attacker         Target       Vulnerable Target
                         │
                         ▼
                Windows Server 2022
                    AD Lab Target

IP addresses are environment-dependent and should be determined from the individual lab configuration.
