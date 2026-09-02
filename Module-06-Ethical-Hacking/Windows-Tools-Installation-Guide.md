# Module 06 — Windows Tools Installation Guide

Installation procedures, official download sources, requirements, and verification steps for the Windows-based tools used in **Module 06 — Ethical Hacking**.

These tools run inside the isolated Windows lab environment for controlled cybersecurity training.

## Windows Laboratory Environment

```
                    VMware Pro
                         │
                  Host-Only Network
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
         Windows 10          Windows Server 2022
          Lab Target           Server / AD Lab
```

> Use these tools only on systems you own or are explicitly authorized to test.

## Tools Covered

| Tool | Purpose | Platform |
|---|---|---|
| OpenStego | Steganography / Data Hiding | Windows |
| L0phtCrack | Password Security Auditing | Windows |
| Sysinternals Streams | NTFS Alternate Data Stream Analysis | Windows |

---

## 1. OpenStego

Open-source steganography application for data hiding, extraction, watermarking, and steganalysis. Written in Java; supports Windows and other Java-supported platforms.

**Sources:**
- Website: https://www.openstego.com/
- GitHub: https://github.com/syvaidya/openstego
- Releases: https://github.com/syvaidya/openstego/releases (current: v0.8.6)

### Requirements

Requires a 64-bit Java/JDK. The lab environment used **Eclipse Temurin**:
- Website: https://adoptium.net/
- Install docs: https://adoptium.net/installation

### Install Java

1. Open the official Adoptium website.
2. Download a compatible 64-bit JDK for Windows.
3. Run the installer and complete the wizard.
4. Verify:
   ```cmd
   java -version
   ```

### Install OpenStego

1. Open the [Releases page](https://github.com/syvaidya/openstego/releases).
2. Download the Windows package for the required release.
3. Extract/install per the package provided.
4. If using a portable distribution, store it at:
   ```
   C:\LabTools\Windows_Tools\OpenStego\
   ```

### Optional: Configure JAVA_HOME

If a tool doesn't detect Java correctly:

```cmd
setx JAVA_HOME "C:\Program Files\Eclipse Adoptium\jdk-<VERSION>" /M
```

Open a new Command Prompt, then verify:

```cmd
echo %JAVA_HOME%
java -version
```

Replace `<VERSION>` with the installed JDK version.

### Verification

Launch OpenStego and confirm it opens successfully. Command-line usage:

```cmd
java -jar <path>\openstego.jar help
```

Supported commands: `embed`, `extract`, `gensig`, `embedmark`, `checkmark`, `algorithms`, `readformats`, `writeformats`, `help`.

CLI docs: https://www.openstego.com/cmdline.html

---

## 2. L0phtCrack

Password auditing and strength-assessment tool for studying password auditing, hash analysis, authentication security, and password policy effectiveness in an authorized lab.

**Sources:**
- Website: https://www.l0phtcrack.com/
- Repository: https://gitlab.com/l0phtcrack/l0phtcrack
- 7.2.0 release directory: https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0

The release directory includes `lc7setup_v7.2.0_Win32.exe` and `lc7setup_v7.2.0_Win64.exe`. Use the 64-bit installer for a typical 64-bit lab system.

### Installation

1. Open the [7.2.0 release directory](https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0).
2. Download `lc7setup_v7.2.0_Win64.exe`.
3. Run the installer and follow the wizard.
4. Recommended location for supporting files:
   ```
   C:\LabTools\Windows_Tools\L0phtCrack\
   ```

### Verification

Launch L0phtCrack and confirm the application opens, the main interface loads, and password-auditing functionality is available.

> Only use test accounts, hashes, or systems you have explicit authorization to audit.

### Note on Version

L0phtCrack 7.2.0 is a historical/open-source release included because it's part of the Module 06 syllabus, used only in the controlled lab. It is **not** a current enterprise password-auditing recommendation.

---

## 3. Sysinternals Streams

Microsoft Sysinternals command-line utility that identifies NTFS Alternate Data Streams (ADS) — useful for demonstrating hidden file data and ADS identification during security investigations.

**Sources:**
- Documentation: https://learn.microsoft.com/en-us/sysinternals/downloads/streams
- Sysinternals index: https://learn.microsoft.com/en-us/sysinternals/downloads/ (current: Streams v1.6)

### Installation

Streams is a portable utility — no installer required.

1. Download the Streams ZIP from the [official page](https://learn.microsoft.com/en-us/sysinternals/downloads/streams).
2. Extract the archive.
3. Create the directory:
   ```
   C:\LabTools\Windows_Tools\Streams\
   ```
4. Place `streams.exe` inside it.

Optionally add the directory to PATH, or run it directly:

```cmd
cd C:\LabTools\Windows_Tools\Streams
```

### Verification

```cmd
streams.exe
```

Usage information should display. Basic syntax:

```
streams [-s] [-d] <file or directory>
```

- `-s` — recursively processes subdirectories
- `-d` — deletes alternate streams

Use only for controlled laboratory analysis.

---

## Recommended Directory Layout

```
C:\LabTools\
└── Windows_Tools\
    ├── OpenStego\
    ├── L0phtCrack\
    └── Streams\
```

## Installation Verification Checklist

| Tool | Installed | Verified |
|---|---|---|
| OpenStego | ✅ | ✅ |
| L0phtCrack 7.2.0 | ✅ | ✅ |
| Sysinternals Streams | ✅ | ✅ |

## Official Download Sources

**OpenStego**
- https://www.openstego.com/
- https://github.com/syvaidya/openstego
- https://github.com/syvaidya/openstego/releases

**L0phtCrack**
- https://www.l0phtcrack.com/
- https://gitlab.com/l0phtcrack/l0phtcrack
- https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0

**Sysinternals Streams**
- https://learn.microsoft.com/en-us/sysinternals/downloads/streams
- https://learn.microsoft.com/en-us/sysinternals/downloads/

## Lab Safety

These tools must only be used inside the authorized workshop environment.

**Always**
- Use dedicated laboratory accounts and test data.
- Work inside isolated VMs, on the intended lab network.
- Take snapshots before major configuration changes.

**Never**
- Audit passwords belonging to other users without authorization.
- Use password hashes obtained from unauthorized systems.
- Expose vulnerable laboratory machines to public networks.
