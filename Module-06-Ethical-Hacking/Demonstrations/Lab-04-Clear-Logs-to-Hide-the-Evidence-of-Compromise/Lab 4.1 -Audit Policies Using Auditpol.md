# Lab 4.1 — Audit Policies Using Auditpol

## 🎯 Objective

Configure Windows process-creation auditing and investigate the resulting Security event.

---

## Step 1 — View Current Audit Policies

Open **PowerShell as Administrator**:

```powershell
auditpol /get /category:*
```

---

## Step 2 — Enable Process Creation Auditing

```powershell
auditpol /set /subcategory:"Process Creation" /success:enable
```

Verify:

```powershell
auditpol /get /subcategory:"Process Creation"
```

---

## Step 3 — Generate a Process Creation Event

Launch Notepad:

```powershell
notepad.exe
```

Close Notepad after launching it.

---

## Step 4 — Search for Event ID 4688

```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4688} -MaxEvents 5 |
    Format-List TimeCreated, Id, Message
```

---

## Step 5 — Search Specifically for Notepad

```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4688} |
    Where-Object {$_.Message -match "notepad.exe"} |
    Select-Object -First 1 TimeCreated, Id, Message |
    Format-List
```

---

## Step 6 — Disable the Audit Policy

```powershell
auditpol /set /subcategory:"Process Creation" /success:disable
```

Verify:

```powershell
auditpol /get /subcategory:"Process Creation"
```

---

## 🧠 What You Learned

Windows Event ID **4688** records process creation when the appropriate auditing policy is enabled.

This is useful for detecting:

* Suspicious processes
* Unexpected executables
* Command interpreters
* Malware execution
* Post-compromise activity
