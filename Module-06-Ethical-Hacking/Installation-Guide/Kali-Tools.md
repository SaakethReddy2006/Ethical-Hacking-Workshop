# 🐉 Module 06 — Ethical Hacking
# 📥 Kali Tools Installation Guide

This guide contains the installation, purpose, and verification procedures for the tools prepared for **Module 06 — Ethical Hacking**.

> ⚠️ All tools and techniques in this repository are intended for authorized educational laboratory environments only.

---

# 🖥️ Lab Environment

The workshop uses isolated VMware virtual machines for practical exercises.

| Machine | Role | IP Address |
|---|---|---|
| Kali Linux | Attacker / Security Testing | `<KALI-IP>` |
| Windows 10 | Windows Target | `<WINDOWS10-IP>` |
| Metasploitable 2 | Vulnerable Linux Target | `<METASPLOITABLE-IP>` |
| Windows Server 2022 | Active Directory Lab | `<SERVER-IP>` |

> IP addresses are represented using placeholders so that this guide can be used by different workshop participants.

---

# 🌐 Network Configuration

The ethical hacking laboratory uses a **VMware Host-Only Network**.

```text
                VMware Host-Only Network
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      Kali Linux     Windows 10    Metasploitable 2
      <KALI-IP>     <WINDOWS10-IP>  <METASPLOITABLE-IP>
       ATTACKER         TARGET       VULNERABLE TARGET
                           │
                           ▼
                  Windows Server 2022
                     <SERVER-IP>
                    AD LAB TARGET
```

Replace the placeholder IP addresses with the IP addresses assigned to your own laboratory machines.

---

# 🐉 Kali Linux Tools

## 1. 🔎 Nmap

### 🎯 Purpose
Nmap is a network discovery and security auditing tool used for:
- Host discovery
- Port scanning
- Service enumeration
- Version detection
- Basic OS detection

### 📥 Installation
```bash
sudo apt update
sudo apt install nmap -y
```

### ✅ Verification
```bash
nmap --version
```
A successful installation displays the installed Nmap version.

---

## 2. 🔌 Netcat

### 🎯 Purpose
Netcat is a networking utility used for:
- TCP/UDP connection testing
- Network troubleshooting
- Testing network services
- Client/server communication in the laboratory

### 📥 Installation
```bash
sudo apt install netcat-openbsd -y
```

### ✅ Verification
```bash
nc -h
```
If the help information is displayed, Netcat is installed successfully.

---

## 3. 🛡️ Responder

### 🎯 Purpose
Responder is used in controlled laboratory environments to demonstrate Windows network authentication and name-resolution security concepts.

### 📥 Installation
```bash
sudo apt install responder -y
```

### ✅ Verification
```bash
responder --help
```
If the Responder help information is displayed, the installation is successful.

---

## 4. 🔐 Hydra

### 🎯 Purpose
Hydra is a network login auditing tool used to demonstrate password security against authorized laboratory services.

### 📥 Installation
```bash
sudo apt install hydra -y
```

### ✅ Verification
```bash
hydra -h
```
The Hydra help menu confirms that the tool is available.

---

## 5. 🔑 John the Ripper

### 🎯 Purpose
John the Ripper is a password auditing and hash analysis tool used to demonstrate password security concepts.

### 📥 Installation
```bash
sudo apt install john -y
```

### ✅ Verification
```bash
john --version
```
The installed John the Ripper version should be displayed.

---

## 6. ⚡ Hashcat

### 🎯 Purpose
Hashcat is a password recovery and hash auditing tool used for authorized security testing.

### 📥 Installation
```bash
sudo apt install hashcat -y
```

### ✅ Verification
```bash
hashcat --version
```
The installed Hashcat version should be displayed.

---

## 7. 💥 Metasploit Framework

### 🎯 Purpose
Metasploit is a penetration-testing framework used to demonstrate:
- Vulnerability exploitation
- Payload concepts
- Post-exploitation
- Meterpreter
- Security testing workflows

All demonstrations must use intentionally vulnerable laboratory targets.

### 📥 Installation
```bash
sudo apt install metasploit-framework -y
```

### ⚙️ Initialize Database
```bash
sudo msfdb init
```

### ✅ Verification
```bash
msfconsole --version
```

### 🔍 Database Verification
Start Metasploit:
```bash
msfconsole
```
Inside Metasploit:
```bash
db_status
```
A connected database should be reported.

---

## 8. 📚 SearchSploit

### 🎯 Purpose
SearchSploit provides a command-line interface for searching the Exploit Database.

It can be used during vulnerability research and security assessment exercises.

### 📥 Installation
```bash
sudo apt install exploitdb -y
```

### ✅ Verification
```bash
searchsploit --version
```
The installed SearchSploit version should be displayed.

---

## 9. 🖥️ enum4linux

### 🎯 Purpose
enum4linux is used to enumerate information from Windows and SMB systems during authorized laboratory exercises.

It can assist with demonstrations involving:
- SMB enumeration
- User enumeration
- Share enumeration
- Domain/workgroup information

### 📥 Installation
```bash
sudo apt install enum4linux -y
```

### ✅ Verification
```bash
enum4linux -h
```

---

## 10. 📁 smbclient

### 🎯 Purpose
smbclient is a command-line SMB/CIFS client used for authorized SMB enumeration and testing.

### 📥 Installation
```bash
sudo apt install smbclient -y
```

### ✅ Verification
```bash
smbclient --version
```

---

## 11. 📖 LDAP Utilities

### 🎯 Purpose
LDAP utilities provide command-line tools for querying and interacting with LDAP directory services.

They are useful during Active Directory and directory-service security demonstrations.

### 📥 Installation
```bash
sudo apt install ldap-utils -y
```

### ✅ Verification
```bash
ldapsearch -VV
```
The OpenLDAP version information confirms the installation.

---

## 12. 📦 NFS Utilities

### 🎯 Purpose
NFS utilities provide tools for discovering and interacting with Network File System exports during authorized Linux security exercises.

### 📥 Installation
```bash
sudo apt install nfs-common -y
```

### ✅ Verification
```bash
showmount --version
```

---

## 13. 🦈 Wireshark

### 🎯 Purpose
Wireshark is a network protocol analyzer used to:
- Capture network traffic
- Inspect packets
- Analyze protocols
- Troubleshoot network communication
- Observe security-related network activity

### 📥 Installation
```bash
sudo apt install wireshark -y
```
During installation, Kali may ask whether non-root users should be allowed to capture packets. Select the appropriate option for the laboratory setup.

### ✅ Verification
```bash
wireshark --version
```
Launch Wireshark with:
```bash
wireshark
```

---

## 14. 🌐 Gobuster

### 🎯 Purpose
Gobuster is used for authorized web content enumeration.

It can be used to demonstrate:
- Directory enumeration
- File enumeration
- Web application reconnaissance

### 📥 Installation
```bash
sudo apt install gobuster -y
```

### ✅ Verification
```bash
gobuster version
```
If the version command does not display the version directly, use:
```bash
gobuster --help
```

---

## 15. 💉 SQLMap

### 🎯 Purpose
SQLMap is an automated SQL injection testing tool used against intentionally vulnerable applications.

### 📥 Installation
```bash
sudo apt install sqlmap -y
```

### ✅ Verification
```bash
sqlmap --version
```

---

## 16. 🖼️ Steghide

### 🎯 Purpose
Steghide is a steganography tool used to demonstrate hiding and extracting information within supported media files.

### 📥 Installation
```bash
sudo apt install steghide -y
```

### ✅ Verification
```bash
steghide --version
```

---

## 17. 🧩 Binwalk

### 🎯 Purpose
Binwalk is used for analyzing binary files and identifying embedded or compressed data.

It is useful for firmware and binary-analysis demonstrations.

### 📥 Installation
```bash
sudo apt install binwalk -y
```

### ✅ Verification
```bash
binwalk --version
```

---

## 18. 🏷️ ExifTool

### 🎯 Purpose
ExifTool is used to inspect metadata contained in files and media.

It can demonstrate:
- Metadata analysis
- File information gathering
- Digital forensics concepts

### 📥 Installation
```bash
sudo apt install libimage-exiftool-perl -y
```

### ✅ Verification
```bash
exiftool -ver
```

---

## 19. 🕷️ Armitage

### 🎯 Purpose
Armitage provides a graphical interface for the Metasploit Framework and is used for controlled penetration-testing demonstrations.

### 📥 Installation
```bash
sudo apt install armitage -y
```

### ✅ Verification
```bash
armitage --help
```
Launch Armitage with:
```bash
armitage
```

---

# 🪟 Windows Tools

## 20. 🔐 OpenStego

### 🎯 Purpose
OpenStego is used to demonstrate image steganography and data hiding.

It can be used to demonstrate:
- Data hiding
- Data extraction
- Steganography concepts

### 📥 Installation
OpenStego is a Java-based application.

Download the appropriate release from the official OpenStego project and follow the project's installation instructions.

**Requirements**
- Java Runtime Environment / JDK
- OpenStego

### ✅ Verification
Launch OpenStego and confirm that the application starts successfully.

---

## 21. 🔑 L0phtCrack

### 🎯 Purpose
L0phtCrack is a Windows password auditing tool used to demonstrate password security assessment in an authorized laboratory environment.

### 📥 Installation
Install the prepared L0phtCrack release on the Windows 10 laboratory VM.

Follow the installation wizard.

### ✅ Verification
Launch L0phtCrack and confirm that the application opens successfully.

> ⚠️ Use L0phtCrack only for authorized password auditing within the workshop laboratory.

---

## 22. 📂 Sysinternals Streams

### 🎯 Purpose
Streams is a Microsoft Sysinternals command-line utility used to identify NTFS Alternate Data Streams (ADS).

It is used in the workshop to demonstrate NTFS file-system features and security concepts.

### 📥 Installation
Download the official Microsoft Sysinternals Streams package.

Extract the archive and locate:
```
streams.exe
```
Place the executable in a suitable laboratory tools directory.

### ✅ Verification
Open Command Prompt and navigate to the directory containing `streams.exe`.

Run:
```
streams.exe
```
If the usage/help information is displayed, Streams is ready to use.
