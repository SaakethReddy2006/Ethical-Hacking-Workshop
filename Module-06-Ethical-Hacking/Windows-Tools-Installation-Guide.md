# 🪟 Module 06 — Windows Tools Installation Guide

This document provides the installation procedures, official download sources, requirements, and verification steps for the Windows-based tools used in **Module 06 — Ethical Hacking**.

These tools are installed on the Windows laboratory environment and used for controlled cybersecurity training.

---

## 🧪 Windows Laboratory Environment

The Windows tools in this guide are used inside the isolated workshop environment.

```text
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

> ⚠️ Use these tools only on systems you own or are explicitly authorized to test.

---

## 📋 Tools Covered

| Tool | Purpose | Platform |
|---|---|---|
| 🔵 OpenStego | Steganography / Data Hiding | Windows |
| 🔴 L0phtCrack | Password Security Auditing | Windows |
| 🟢 Sysinternals Streams | NTFS Alternate Data Stream Analysis | Windows |

---

## 🔵 1. OpenStego

**🎯 Purpose**

OpenStego is an open-source steganography application. It provides functionality for:
- 🙈 Data hiding
- 🔓 Data extraction
- 💧 Watermarking
- 🧪 Steganography analysis

Written in Java, it supports Windows and other Java-supported platforms. Source code and releases are on GitHub.

**🔗 Official Sources**
- 🌐 Website: https://www.openstego.com/
- 🐙 GitHub: https://github.com/syvaidya/openstego
- 📦 Releases: https://github.com/syvaidya/openstego/releases

> 💡 The current release listing includes **OpenStego v0.8.6**.

**⚙️ Requirements**

OpenStego requires Java. Recommended: 64-bit Java / JDK.

For the prepared lab environment, **Eclipse Temurin** was used:
- 🌐 Website: https://adoptium.net/
- 📖 Install docs: https://adoptium.net/installation

**📥 Installation — Java**

1. ☕ Open the official Adoptium website.
2. ⬇️ Download a compatible 64-bit JDK for Windows.
3. 🖱️ Install the JDK and complete the wizard.
4. ✅ Verify:
   ```cmd
   java -version
   ```
   A Java version should be displayed.

**📥 Installation — OpenStego**

1. 🔗 Open the [Releases page](https://github.com/syvaidya/openstego/releases).
2. 🗂️ Select the required release.
3. ⬇️ Download the Windows package.
4. 📦 Extract/install per the package provided.
5. 🗄️ If using a portable distribution, store it at:
   ```
   C:\LabTools\Windows_Tools\OpenStego\
   ```

**🛠️ Optional: Configure JAVA_HOME**

If a tool doesn't detect Java correctly:

```cmd
setx JAVA_HOME "C:\Program Files\Eclipse Adoptium\jdk-<VERSION>" /M
```

Open a new Command Prompt, then verify:

```cmd
echo %JAVA_HOME%
java -version
```

> 🔁 Replace `<VERSION>` with the installed JDK version.

**✅ Verification**

Launch OpenStego and confirm it opens successfully. 🚀

Command-line usage:
```cmd
java -jar <path>\openstego.jar help
```

Supported commands: `embed` 🙈 · `extract` 🔓 · `gensig` · `embedmark` · `checkmark` · `algorithms` · `readformats` · `writeformats` · `help`

📖 CLI docs: https://www.openstego.com/cmdline.html

---

## 🔴 2. L0phtCrack

**🎯 Purpose**

L0phtCrack is a password auditing and password-strength assessment tool. In an authorized lab, it can be used to study:
- 🔑 Password auditing
- 💪 Password strength
- #️⃣ Hash analysis
- 🔐 Authentication security
- 📜 Password policy effectiveness

**🔗 Official Sources**
- 🌐 Website: https://www.l0phtcrack.com/
- 🦊 GitLab: https://gitlab.com/l0phtcrack/l0phtcrack
- 📦 7.2.0 release directory: https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0

The release directory includes Windows installers:
- `lc7setup_v7.2.0_Win32.exe`
- `lc7setup_v7.2.0_Win64.exe` ⭐ (recommended for typical 64-bit lab systems)

**📥 Installation**

1. 🔗 Open the [7.2.0 release directory](https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0).
2. ⬇️ Download `lc7setup_v7.2.0_Win64.exe`.
3. 🖱️ Run the installer and follow the wizard.
4. 🗄️ Recommended location for supporting files:
   ```
   C:\LabTools\Windows_Tools\L0phtCrack\
   ```

**✅ Verification**

Launch L0phtCrack and confirm:
- ✅ The application opens successfully
- ✅ The main interface loads
- ✅ Password-auditing functionality is available

> ⚠️ Only use test accounts, hashes, or systems you have explicit authorization to audit.

**📌 Important Status Note**

L0phtCrack 7.2.0 is a historical/open-source release, included because it's part of the Module 06 training syllabus and used only in the controlled lab.

> 🚫 Do not treat this legacy release as a current enterprise password-auditing recommendation.

---

## 🟢 3. Sysinternals Streams

**🎯 Purpose**

Streams is a Microsoft Sysinternals command-line utility used to identify NTFS Alternate Data Streams (ADS). It can help demonstrate:
- 🌊 NTFS alternate data streams
- 🙈 Hidden file data
- 🏷️ File metadata associated with alternate streams
- 🕵️ ADS identification during security investigations

**🔗 Official Sources**
- 📖 Documentation: https://learn.microsoft.com/en-us/sysinternals/downloads/streams
- 🗂️ Sysinternals index: https://learn.microsoft.com/en-us/sysinternals/downloads/

> 💡 The Microsoft Sysinternals utilities index currently lists **Streams v1.6**.

**📥 Installation**

Streams is a portable command-line utility — no installer required.

1. ⬇️ Download the Streams ZIP from the [official page](https://learn.microsoft.com/en-us/sysinternals/downloads/streams).
2. 📦 Extract the archive.
3. 🗄️ Create the directory:
   ```
   C:\LabTools\Windows_Tools\Streams\
   ```
4. 📥 Place `streams.exe` inside it.

**🛠️ Add Streams to PATH — Optional**

You can optionally add the Streams directory to the Windows PATH, or run the executable directly:

```cmd
cd C:\LabTools\Windows_Tools\Streams
```

**✅ Verification**

```cmd
streams.exe
```

Usage information should display. 🎉 Basic syntax:

```
streams [-s] [-d] <file or directory>
```

- `-s` 🔁 — recursively processes subdirectories
- `-d` 🗑️ — deletes alternate streams

> ⚠️ Use only for controlled laboratory analysis.

---

## 📁 Recommended Windows Tools Directory

```
C:\LabTools\
└── Windows_Tools\
    ├── 🔵 OpenStego\
    ├── 🔴 L0phtCrack\
    └── 🟢 Streams\
```

---

## ✅ Installation Verification Checklist

| Tool | Installed | Verified |
|---|---|---|
| 🔵 OpenStego | ✅ | ✅ |
| 🔴 L0phtCrack 7.2.0 | ✅ | ✅ |
| 🟢 Sysinternals Streams | ✅ | ✅ |

---

## 🔗 Official Download Sources

**🔵 OpenStego**
- 🌐 https://www.openstego.com/
- 🐙 https://github.com/syvaidya/openstego
- 📦 https://github.com/syvaidya/openstego/releases

**🔴 L0phtCrack**
- 🌐 https://www.l0phtcrack.com/
- 🦊 https://gitlab.com/l0phtcrack/l0phtcrack
- 📦 https://gitlab.com/l0phtcrack/l0phtcrack.gitlab.io/-/tree/main/public/releases/7.2.0

**🟢 Sysinternals Streams**
- 📖 https://learn.microsoft.com/en-us/sysinternals/downloads/streams
- 🗂️ https://learn.microsoft.com/en-us/sysinternals/downloads/

---

## 🔐 Lab Safety

These tools must only be used inside the authorized workshop environment.

**✅ Always**
- 👤 Use dedicated laboratory accounts
- 🧪 Use test data
- 🖥️ Work inside isolated VMs
- 🌐 Keep vulnerable systems on the intended lab network
- 📸 Take snapshots before major configuration changes

**🚫 Never**
- 🔑 Audit passwords belonging to other users without authorization
- #️⃣ Use password hashes obtained from unauthorized systems
- 🌍 Expose vulnerable laboratory machines to public networks
- 🔒 Store real credentials in the repository
- ⛔ Commit passwords, hashes, license files, or sensitive data to GitHub

---

## 🎉 Setup Complete

Once OpenStego, L0phtCrack, and Streams are installed and verified, your Module 06 Windows toolkit is ready! 🪟🔐🟢
