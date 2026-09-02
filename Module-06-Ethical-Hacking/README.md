# 🔴 Module 06 — Ethical Hacking

This module provides hands-on practical exercises covering common ethical hacking and penetration testing techniques in an isolated VMware laboratory environment.

## 🖥️ Lab Environment

| Machine | Role | IP Address |
|---|---|---|
| Kali Linux | Attacker | 192.168.153.130 |
| Windows 10 | Windows Target | 192.168.153.129 |
| Metasploitable 2 | Vulnerable Linux Target | 192.168.153.131 |
| Windows Server 2022 | Active Directory Lab | DHCP / Lab Configuration |

## 📚 Labs

### Lab 01 — Gain Access
- Responder
- L0phtCrack
- Exploit Sites
- Client-Side Vulnerabilities
- VNC
- Armitage
- Ninja / Jonin
- Buffer Overflow

### Lab 02 — Privilege Escalation
- Privilege Escalation Techniques
- Metasploit & Meterpreter
- pkexec
- NFS Misconfiguration
- UAC & Sticky Keys
- Credential/Hash Analysis

### Lab 03 — Maintain Remote Access / Hide
- NTFS Alternate Data Streams
- Whitespace Steganography
- OpenStego
- Boot/Logon Autostart
- Active Directory Persistence
- WMI
- Covert Channels

### Lab 04 — Clear Logs
- Auditpol
- Windows Event Log Management
- Linux Log Management
- Artifact Hiding
- CCleaner

---

## 📥 Installation Guides

Installation instructions for the tools used in Module 06.

➡️ [Kali Tools](Installation-Guide/Kali-Tools.md)

➡️ [Windows Tools](Installation-Guide/Windows-Tools.md)

---

## 🧪 Demonstrations

Step-by-step demonstrations of the techniques covered during the workshop.

➡️ [Demonstrations](Demonstrations/)

---

## 🌐 Network Setup

The lab uses a VMware Host-Only network:

```text
                VMware Host-Only Network
                   192.168.153.0/24
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
           Kali        Windows 10    Metasploitable 2
       .153.130         .153.129        .153.131
         Attacker         Target       Vulnerable Target
                           │
                           ▼
                   Windows Server 2022
                      AD Lab Target

## ⚠️ Lab Safety

All exercises must be performed only in the authorized workshop laboratory environment.

Use isolated virtual machines and Host-Only networking when working with vulnerable systems.

Do not test these techniques against systems without explicit authorization.
