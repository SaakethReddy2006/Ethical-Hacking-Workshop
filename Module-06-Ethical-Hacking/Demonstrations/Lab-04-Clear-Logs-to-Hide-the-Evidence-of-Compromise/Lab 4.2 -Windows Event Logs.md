# Lab 4.2 — Windows Event Logs

## 🎯 Objective

Examine Windows Security Event Logs and understand the forensic significance of security log clearing.

> ⚠️ This demonstration intentionally modifies the Security log. Perform it only inside the workshop VM and restore the VM from a snapshot afterward if necessary.

---

## Step 1 — Inspect the Security Log

Open PowerShell as Administrator:

```powershell
Get-WinEvent -ListLog Security |
    Select-Object LogName, RecordCount, IsEnabled
```

---

## Step 2 — Display Recent Security Events

```powershell
Get-WinEvent -LogName Security -MaxEvents 10 |
    Select-Object TimeCreated, Id, ProviderName, Message |
    Format-List
```

---

## Step 3 — Generate a Process Event

```powershell
notepad.exe
```

Close Notepad.

---

## Step 4 — Search for Process Creation Events

```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4688} -MaxEvents 10 |
    Where-Object {$_.Message -match "notepad.exe"} |
    Select-Object TimeCreated, Id, Message |
    Format-List
```

---

## Step 5 — Check the Security Log Record Count

```powershell
(Get-WinEvent -ListLog Security).RecordCount
```

Record count represents the number of event records currently maintained in the log.

---

## Step 6 — Demonstrate Security Log Clearing

> Perform this step only in the isolated workshop VM.

```powershell
wevtutil cl Security
```

---

## Step 7 — Check the Log Again

```powershell
Get-WinEvent -ListLog Security |
    Select-Object LogName, RecordCount, IsEnabled
```

Then:

```powershell
Get-WinEvent -LogName Security -MaxEvents 5
```

---

## Step 8 — Look for Event ID 1102

```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=1102} -MaxEvents 5 |
    Format-List TimeCreated, Id, Message
```

Event ID **1102** is associated with the Security audit log being cleared.

---

## 🧠 What You Learned

Clearing logs does not necessarily eliminate evidence.

Security monitoring systems can detect log-clearing activity, and centralized logging can preserve events outside the compromised machine.

For real environments, logs should ideally be forwarded to a centralized and protected logging platform.
