# Lab 3.3 — Boot/Logon Autostart Persistence

## 🎯 Objective

Demonstrate Windows startup persistence using a harmless PowerShell test script.

The script only writes a timestamp to a laboratory file.

---

## Step 1 — Create the Lab Directory

```powershell
New-Item -ItemType Directory -Path C:\Lab\Persistence -Force
```

---

## Step 2 — Create the Test Script

```powershell
@'
"Persistence test executed at $(Get-Date)" | Out-File C:\Lab\Persistence\execution.txt -Append
'@ | Out-File C:\Lab\Persistence\startup-test.ps1 -Encoding UTF8
```

Verify:

```powershell
Get-Content C:\Lab\Persistence\startup-test.ps1
```

---

## Step 3 — Identify the Windows Startup Folder

```powershell
$Startup = [Environment]::GetFolderPath('Startup')
```

Display it:

```powershell
$Startup
```

---

## Step 4 — Create the Startup Shortcut

```powershell
$WshShell = New-Object -ComObject WScript.Shell

$Shortcut = $WshShell.CreateShortcut("$Startup\Workshop-Test.lnk")

$Shortcut.TargetPath = "powershell.exe"

$Shortcut.Arguments = '-NoProfile -ExecutionPolicy Bypass -File "C:\Lab\Persistence\startup-test.ps1"'

$Shortcut.Save()
```

---

## Step 5 — Verify the Startup Entry

```powershell
Get-ChildItem $Startup
```

Look for:

```text
Workshop-Test.lnk
```

---

## Step 6 — Restart Windows

```powershell
Restart-Computer
```

After Windows starts and you log in, check:

```powershell
Get-Content C:\Lab\Persistence\execution.txt
```

A timestamp should be present.

---

## Step 7 — Remove the Persistence Mechanism

```powershell
$Startup = [Environment]::GetFolderPath('Startup')

Remove-Item "$Startup\Workshop-Test.lnk" -Force
```

Verify:

```powershell
Get-ChildItem $Startup
```

---

## Step 8 — Remove the Lab Files

```powershell
Remove-Item C:\Lab\Persistence -Recurse -Force
```

---

## 🧠 What You Learned

Windows startup locations can be used by software to automatically execute programs when a user logs in.

Defenders should monitor persistence locations and investigate unexpected startup entries.
