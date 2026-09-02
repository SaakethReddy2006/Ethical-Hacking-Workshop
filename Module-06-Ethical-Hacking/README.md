# 🔴 Module 06 — Ethical Hacking

This module provides hands-on practical exercises covering common ethical hacking and penetration testing techniques in an isolated VMware laboratory environment.

---

## 🖥️ Lab Environment

| Machine | Role | IP Address |
|---|---|---|
| Kali Linux | Attacker / Security Testing | `<KALI-IP>` |
| Windows 10 | Windows Target | `<WINDOWS10-IP>` |
| Metasploitable 2 | Vulnerable Linux Target | `<METASPLOITABLE-IP>` |
| Windows Server 2022 | Active Directory Lab | `<SERVER-IP>` |

> **Note:** IP addresses are represented using placeholders. Replace them with the IP addresses assigned to your own lab machines.

---

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
- Credential / Hash Analysis

### Lab 03 — Maintain Remote Access / Hide

- NTFS Alternate Data Streams
- Whitespace Steganography
- OpenStego
- Boot / Logon Autostart
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

### Kali Linux

➡️ [Kali Tools Installation Guide](Installation-Guide/Kali-Tools.md)

### Windows

➡️ [Windows Tools Installation Guide](Installation-Guide/Windows-Tools.md)

---

## 🧪 Demonstrations

Step-by-step demonstrations of the techniques covered during the workshop.

➡️ [Module 06 Demonstrations](Demonstrations/)

Each demonstration will contain:

- 🎯 Objective
- 🛠️ Tools Required
- ⚙️ Lab Setup
- 📝 Step-by-Step Procedure
- 💻 Commands
- 📸 Expected Results
- ⚠️ Safety Notes

---

## 🌐 Network Setup

The lab uses a VMware **Host-Only Network** to provide an isolated environment for the practical exercises.

```text
                VMware Host-Only Network
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      Kali Linux     Windows 10    Metasploitable 2
      <KALI-IP>     <WINDOWS10-IP>  <METASPLOITABLE-IP>
       Attacker         Target       Vulnerable Target
                           │
                           ▼
                  Windows Server 2022
                     <SERVER-IP>
                    AD Lab Target

## ⚠️ Lab Safety

All exercises must be performed only in the authorized workshop laboratory environment.

Use isolated virtual machines and Host-Only networking when working with vulnerable systems.

Do not test these techniques against systems without explicit authorization.
