# VMware Pro — Lab Setup Guide

Configuration guide for the **Ethical Hacking Workshop** lab environment: isolated virtual machines for controlled cybersecurity exercises.

## Objective

Build an isolated virtualized environment for:

- Ethical Hacking
- Vulnerability Assessment
- Network Security
- Malware Analysis
- Digital Forensics
- Security Monitoring

## Lab Architecture

### Module 06 — Ethical Hacking

```
                         VMware Pro
                             │
                     Host-Only Network
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                   │
      ┌───▼────┐       ┌─────▼─────┐      ┌──────▼───────┐
      │  Kali  │       │ Windows 10│      │ Metasploitable│
      │ Linux  │       │  Target   │      │       2       │
      │Attacker│       │           │      │ Vulnerable VM │
      └────────┘       └─────┬─────┘      └───────────────┘
                              │
                        ┌─────▼─────┐
                        │ Windows   │
                        │ Server    │
                        │   2022    │
                        │ AD Target │
                        └───────────┘
```

### Module 07 — Malware Analysis

```
                         VMware Pro
                             │
                     Host-Only Network
                             │
              ┌──────────────┴──────────────┐
              │                             │
        ┌─────▼──────┐                ┌─────▼─────┐
        │ Windows 10 │                │  REMnux   │
        │  Malware   │                │ Analysis  │
        │  Analysis  │                │    VM     │
        │Workstation │                │(Optional) │
        └────────────┘                └───────────┘
```

## Required Virtual Machines

| Virtual Machine | Role | Module |
|---|---|---|
| Kali Linux | Attacker / Security Testing | 06 |
| Windows 10 | Vulnerable Target / Analysis Workstation | 06 + 07 |
| Metasploitable 2 | Intentionally Vulnerable Linux Target | 06 |
| Windows Server 2022 | Active Directory / Windows Server Target | 06 |
| REMnux | Malware Analysis Support | 07 |

## VMware Installation

Install VMware Workstation Pro on the host:

- Official site: https://www.vmware.com/
- Broadcom download portal: https://support.broadcom.com/

VMware software availability and download locations may change — use the official Broadcom portal for current releases.

### Creating a New VM (manual OS install)

1. Open VMware Workstation Pro.
2. Select **Create a New Virtual Machine** → **Typical**.
3. Select the OS installation media and guest OS type.
4. Name the VM and choose a storage location.
5. Configure CPU, RAM, and storage.
6. Finish the wizard and boot the VM to complete installation.

### Importing an Existing VM (pre-built appliances)

1. Open VMware Workstation Pro.
2. Choose **Open/Import** an existing VM or appliance.
3. Browse to the downloaded VM/appliance and import it.
4. Review the hardware configuration and set the network adapter.
5. Boot the VM and verify connectivity inside the isolated lab.

> Always obtain VM images from their official project or a trusted distribution source.

## Network Configuration

The workshop uses a VMware **Host-only** network to isolate lab traffic and avoid exposing vulnerable systems externally.

### Setting Up the Host-only Network

1. Open **Edit → Virtual Network Editor**.
2. Locate the Host-only VMware network.
3. Confirm it exists and that all lab VMs use it.

```
VMware Host-only Network
          │
          ├── Kali Linux
          ├── Windows 10
          ├── Metasploitable 2
          └── Windows Server 2022
```

*Exact network name/subnet may vary by system.*

### Avoid Unnecessary Exposure

- Avoid **Bridged Network** for vulnerable machines unless specifically required.
- Never expose vulnerable VMs to public networks, untrusted Wi-Fi, the internet, or internet-facing port forwarding.

```
Host Computer → VMware Workstation Pro → Host-only Network
                                              ├── Kali
                                              ├── Windows 10
                                              ├── Metasploitable 2
                                              └── Windows Server 2022
```

## Basic Network Verification

**Kali Linux / Metasploitable 2:**
```bash
ip addr
ip route
```

**Windows:**
```cmd
ipconfig
```

Confirm the correct Host-only adapter/interface is active on each VM.

### Connectivity Testing

From Kali:
```bash
ping <WINDOWS10-IP>
ping <METASPLOITABLE-IP>
ping <SERVER-IP>
```

A failed ping doesn't necessarily mean the VM is unreachable — target firewalls may block ICMP.

## Snapshot Strategy

Take a snapshot after each clean setup:

| VM | Snapshot Name |
|---|---|
| Kali | `ETHICAL-HACKING-TOOLS-READY` |
| Windows 10 | `CLEAN / LAB-READY` |
| Metasploitable 2 | `CLEAN / LAB-READY` |
| Windows Server 2022 | `WIN-SERVER-2022-CLEAN` |
| Malware Analysis Windows 10 | `MALWARE-ANALYSIS-READY` |
| REMnux | `REMNUX-CLEAN` |

**Workflow:** Clean VM → Install software → Configure network → Verify → Snapshot → Run exercise → Revert as needed.

Snapshots let participants quickly recover from misconfiguration, failed experiments, or unwanted changes — especially important for malware analysis.

## Malware Analysis Isolation

Keep the malware-analysis environment separate from the general-purpose host.

```
                   VMware Pro
                       │
                Host-only Network
                       │
              ┌────────┴────────┐
              │                 │
        Windows 10           REMnux
        Analysis VM        Analysis VM
```

Before analyzing a sample:
1. Confirm VM isolation.
2. Verify the correct clean snapshot exists.
3. Start monitoring tools.
4. Perform the controlled exercise.
5. Stop the exercise and revert the VM.

## Recommended VM Organization

```
VMware Labs/
├── Module-06/
│   ├── Kali/
│   ├── Windows-10/
│   ├── Metasploitable-2/
│   └── Windows-Server-2022/
└── Module-07/
    ├── Windows-10-Malware-Analysis/
    └── REMnux/
```

## Pre-Exercise Checklist

- [ ] Correct VM selected
- [ ] Correct CPU/RAM allocation
- [ ] Correct disk attached
- [ ] Network adapter configured
- [ ] Host-only network selected
- [ ] Unnecessary shared folders disabled
- [ ] Unnecessary host integration disabled
- [ ] Clean snapshot available
- [ ] VM boots successfully

## Official Project Resources

- VMware: https://www.vmware.com/ | https://support.broadcom.com/
- Kali Linux: https://www.kali.org/ | https://www.kali.org/get-kali/
- Metasploitable: https://sourceforge.net/projects/metasploitable/
- Windows: https://www.microsoft.com/windows/
- REMnux: https://remnux.org/ | https://docs.remnux.org/

## Lab Safety

This environment contains intentionally vulnerable systems and security-testing tools. Use it only for:

- Authorized educational activities
- Controlled security testing
- Workshop demonstrations
- Cybersecurity training

Never expose intentionally vulnerable systems to networks you do not control.

---

Once VMs are imported/installed, configured for the Host-only network, verified, and snapshotted, the lab is ready for the workshop.
