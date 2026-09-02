# 🏗️ Ethical Hacking Workshop — Lab Architecture

This document describes the overall virtual laboratory architecture used for the **Ethical Hacking Workshop**.

The workshop is divided into two primary environments:

- **Module 06 — Ethical Hacking**
- **Module 07 — Malware Analysis**

Both environments are implemented using virtual machines running under **VMware Workstation Pro**.

---

# 🎯 Architecture Objective

The laboratory is designed to provide an isolated and controlled environment for cybersecurity training.

The architecture supports:

- Ethical hacking
- Vulnerability assessment
- Network security testing
- Penetration testing
- Malware analysis
- Reverse engineering
- Digital forensics
- Security monitoring
- Controlled security experimentation

All intentionally vulnerable systems should remain inside the authorized laboratory environment.

---

# 🖥️ Overall Workshop Architecture

```text
                              ┌───────────────────────┐
                              │      Host Machine     │
                              │      Windows Host     │
                              └───────────┬───────────┘
                                          │
                                          ▼
                              ┌───────────────────────┐
                              │      VMware Pro       │
                              │   Virtual Laboratory  │
                              └───────────┬───────────┘
                                          │
                    ┌─────────────────────┴─────────────────────┐
                    │                                           │
                    ▼                                           ▼
          ┌───────────────────────┐                   ┌───────────────────────┐
          │      Module 06        │                   │      Module 07        │
          │   Ethical Hacking     │                   │   Malware Analysis    │
          └───────────┬───────────┘                   └───────────┬───────────┘
                      │                                           │
                      ▼                                           ▼
             Host-Only Network                           Host-Only Network
                      │                                           │
       ┌──────────────┼──────────────┐                 ┌───────────┴──────────┐
       │              │              │                 │                      │
       ▼              ▼              ▼                 ▼                      ▼
    Kali         Windows 10    Metasploitable     Windows 10             REMnux
   Attacker        Target             2            Analysis VM          Analysis VM
                                      │
                                      ▼
                              Windows Server 2022
                                  AD Target
🔴 Module 06 — Ethical Hacking

Module 06 is designed around an attacker-and-target laboratory model.

Core Virtual Machines
Virtual Machine	Role
Kali Linux	Attacker / Security Testing
Windows 10	Windows Target
Metasploitable 2	Intentionally Vulnerable Linux Target
Windows Server 2022	Windows Server / Active Directory Target
🧑‍💻 Kali Linux
Role

Kali Linux acts as the primary security-testing workstation.

It is used for activities such as:

Network discovery
Enumeration
Vulnerability assessment
Web security testing
Password auditing
Exploitation in the controlled lab
Post-exploitation exercises
Network traffic analysis
Position in Architecture
                 Kali Linux
                Attacker VM
                     │
                     ▼
              Host-Only Network
                     │
        ┌────────────┼─────────────┐
        ▼            ▼             ▼
   Windows 10   Metasploitable  Windows Server
                    2              2022
🪟 Windows 10 — Security Target
Role

Windows 10 acts as a controlled Windows target for security-testing exercises.

It can be used for:

Client-side security exercises
Windows security configuration analysis
Authentication testing
Vulnerability assessment
Security monitoring
Controlled attack simulation

The same operating system can also be configured as a separate malware-analysis workstation for Module 07.

🐧 Metasploitable 2
Role

Metasploitable 2 is an intentionally vulnerable Linux virtual machine designed for security training.

It provides a controlled target for:

Service enumeration
Vulnerability assessment
Exploitation exercises
Network security testing
Architecture
Kali Linux
    │
    ▼
Host-Only Network
    │
    ▼
Metasploitable 2

Metasploitable 2 should never be exposed to untrusted networks.

🪟 Windows Server 2022
Role

Windows Server 2022 provides the Windows Server and Active Directory environment required for advanced Module 06 exercises.

It can support laboratory activities involving:

Windows Server administration
Active Directory
Domain environments
Authentication
Windows security
Security assessment
Architecture
                    Windows Server 2022
                            │
                       AD Environment
                            │
                 ┌──────────┴──────────┐
                 │                     │
              Windows 10             Kali
               Target             Assessment

Active Directory exercises should be performed only within the isolated workshop network.

🟣 Module 07 — Malware Analysis

Module 07 uses a separate analysis-focused environment.

Core Virtual Machines
Virtual Machine	Role
Windows 10	Primary Malware Analysis Workstation
REMnux	Supporting Malware Analysis Environment
🪟 Windows 10 — Malware Analysis Workstation

The Windows 10 analysis workstation is used for controlled static and dynamic malware-analysis exercises.

Typical analysis tools include:

Hybrid Analysis
BinText
PEiD
Detect It Easy
PE Explorer
Dependency Walker
IDA Free
x64dbg / x32dbg
Ghidra
TCPView
CurrPorts
Process Monitor
Regshot
Autoruns
Process Explorer
DNSQuerySniffer
Architecture
                Windows 10
             Analysis Workstation
                      │
                      ▼
               Host-Only Network
                      │
                      ▼
                    REMnux
🐧 REMnux
Role

REMnux provides a Linux-based environment designed specifically for malware analysis and reverse engineering.

It can support:

Malware triage
Static analysis
Network analysis
Reverse engineering
Traffic analysis
File analysis

REMnux is an optional supporting environment for the core Windows-based exercises.

🌐 Network Architecture

The workshop uses VMware Host-only networking to isolate laboratory systems from external networks.

Module 06
                   Module 06 Host-Only Network
                              │
           ┌──────────────────┼──────────────────┐
           │                  │                  │
           ▼                  ▼                  ▼
        Kali Linux        Windows 10       Metasploitable 2
        Attacker            Target          Vulnerable Linux
                              │
                              ▼
                      Windows Server 2022
                         AD Environment
Module 07
                   Module 07 Host-Only Network
                              │
                    ┌─────────┴─────────┐
                    │                   │
                    ▼                   ▼
                Windows 10           REMnux
             Analysis Workstation   Analysis VM
🔒 Network Isolation

Host-only networking is used so that laboratory machines can communicate with each other without requiring direct exposure to external networks.

This is particularly important when working with:

Intentionally vulnerable operating systems
Security-testing tools
Malware-analysis environments
Experimental configurations
🚫 External Network Exposure

The laboratory should not unnecessarily expose vulnerable machines to:

Public networks
Untrusted Wi-Fi
The public Internet
Internet-facing port forwarding

Avoid unnecessary use of:

Bridged Networking

for intentionally vulnerable systems.

The preferred configuration is:

Host Machine
     │
     ▼
VMware Workstation Pro
     │
     ▼
Host-Only Network
     │
     ├── Kali
     ├── Windows 10
     ├── Metasploitable 2
     └── Windows Server 2022
