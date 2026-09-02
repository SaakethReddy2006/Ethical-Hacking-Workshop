# 🔴 Ethical Hacking Workshop — Lab Documentation

This repository contains the **laboratory setup, installation guides, and practical documentation for the modules handled by our team** as part of the Ethical Hacking Workshop.

The workshop consists of multiple modules, with different modules being handled by different team members.

---

# 📚 Modules Covered in This Repository

## 🔴 Module 06 — Ethical Hacking

This section covers the ethical hacking and security-testing laboratories handled by our team.

### Topics Include

- Reconnaissance and Enumeration
- Password Security
- Vulnerability Assessment
- Client-Side Security
- Exploitation
- Privilege Escalation
- Persistence
- Steganography
- NTFS Alternate Data Streams
- Log and Artifact Analysis

### 📘 Module 06

[🔴 Open Module 06 — Ethical Hacking](./Module-06-Ethical-Hacking/README.md)

### 📥 Installation Guides

[💻 Kali Tools Installation Guide](./Module-06-Ethical-Hacking/Installation-Guide.md)

[🪟 Windows Tools Installation Guide](./Module-06-Ethical-Hacking/Windows-Tools-Installation-Guide.md)

---

## 🟣 Module 07 — Malware Analysis

This section covers the malware-analysis laboratories handled by our team.

### Topics Include

- Trojan Analysis
- Malware Analysis
- Static Analysis
- PE Analysis
- String Extraction
- Reverse Engineering
- Disassembly
- Decompilation
- Process Monitoring
- Registry Monitoring
- File-System Monitoring
- Network Monitoring
- DNS Analysis

### 📘 Module 07

[🟣 Open Module 07 — Malware Analysis](./Module-07-Malware-Analysis/README.md)

### 📥 Installation Guide

[🧪 Module 07 Installation Guide](./Module-07-Malware-Analysis/Installation-Guide.md)

---

# 🖥️ Laboratory Environment

The laboratories are built using **VMware Workstation Pro** and isolated virtual machines.

```text
                    VMware Workstation Pro
                             │
                    Isolated Lab Networks
                             │
              ┌──────────────┴──────────────┐
              │                             │
              ▼                             ▼
       Module 06 Lab                  Module 07 Lab
       Ethical Hacking              Malware Analysis
              │                             │
       ┌──────┼──────┐               ┌──────┴──────┐
       ▼      ▼      ▼               ▼             ▼
     Kali  Win10  Metasploitable   Win10         REMnux
                    2             Analysis
              │
              ▼
        Windows Server
            2022
