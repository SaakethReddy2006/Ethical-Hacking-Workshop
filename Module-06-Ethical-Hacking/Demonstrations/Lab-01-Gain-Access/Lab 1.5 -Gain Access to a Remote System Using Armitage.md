# Lab 1.5 — Gain Access to a Remote System Using Armitage

## 🎯 Objective

Demonstrate a controlled exploitation workflow against Metasploitable 2 using Armitage and Metasploit.

## 🧪 Lab Network

```text
Kali
192.168.153.130

Metasploitable 2
192.168.153.131
```

---

## Step 1 — Start PostgreSQL

```bash
sudo systemctl start postgresql
```

Check status:

```bash
sudo systemctl status postgresql
```

---

## Step 2 — Initialize Metasploit Database

```bash
sudo msfdb init
```

If the database is already initialized, continue to the next step.

---

## Step 3 — Verify Metasploit Database

```bash
msfconsole -q -x "db_status; exit"
```

A successful database connection should be reported.

---

## Step 4 — Start Armitage

```bash
sudo armitage
```

When prompted:

```text
Start Metasploit RPC?
```

Select:

```text
Yes
```

If Armitage requests the attacker's IP, enter the Kali lab IP:

```text
192.168.153.130
```

---

## Step 5 — Add the Target

In Armitage:

```text
Hosts
   ↓
Add Hosts
```

Enter:

```text
192.168.153.131
```

---

## Step 6 — Scan the Target

Right-click the target:

```text
Scan
```

Allow the scan to complete.

---

## Step 7 — Find Applicable Attacks

Navigate to:

```text
Attacks
   ↓
Find Attacks
```

If required, adjust:

```text
Armitage
   ↓
Set Exploit Rank
```

so appropriate modules are considered.

---

## Step 8 — Select the Vulnerable FTP Service

Right-click the target and navigate to:

```text
Attack
   ↓
ftp
   ↓
VSFTPD 2.3.4 Backdoor Command Execution
```

Launch the module against the lab target.

---

## Step 9 — Verify the Session

Open a Metasploit console and run:

```text
sessions -l
```

A successful controlled demonstration should show the created session.

---

## 🧹 Cleanup

Terminate the laboratory session after the demonstration.

Return both VMs to their clean snapshots when the workshop exercise is complete.
