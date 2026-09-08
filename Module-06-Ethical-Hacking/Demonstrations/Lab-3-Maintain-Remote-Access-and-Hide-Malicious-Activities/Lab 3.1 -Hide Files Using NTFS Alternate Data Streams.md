# Lab 3.1 — Hide Files Using NTFS Alternate Data Streams

## 🎯 Objective

Demonstrate how NTFS Alternate Data Streams can store additional data associated with a normal file.

---

## Step 1 — Create the Laboratory Directory

Open PowerShell:

```powershell
New-Item -ItemType Directory -Path C:\Lab\ADS -Force
```

---

## Step 2 — Create a Normal File

```powershell
"Public workshop file" | Out-File C:\Lab\ADS\report.txt
```

Read the file:

```powershell
Get-Content C:\Lab\ADS\report.txt
```

---

## Step 3 — Create an Alternate Data Stream

```cmd
cmd /c "echo Hidden workshop data > C:\Lab\ADS\report.txt:hidden.txt"
```

---

## Step 4 — View the Normal Directory

```powershell
Get-ChildItem C:\Lab\ADS
```

Notice that the alternate stream does not appear as a normal file.

---

## Step 5 — Read the Alternate Stream

```powershell
Get-Content -Path C:\Lab\ADS\report.txt -Stream hidden.txt
```

Expected data:

```text
Hidden workshop data
```

---

## Step 6 — Enumerate Streams

```powershell
Get-Item C:\Lab\ADS\report.txt -Stream *
```

The output should identify the normal data stream and the additional stream.

---

## Step 7 — Remove the Alternate Stream

```powershell
Remove-Item -Path C:\Lab\ADS\report.txt -Stream hidden.txt
```

Verify:

```powershell
Get-Item C:\Lab\ADS\report.txt -Stream *
```

---

## 🧹 Cleanup

```powershell
Remove-Item C:\Lab\ADS -Recurse -Force
```

## 🧠 What You Learned

NTFS ADS can be relevant to:

* Digital forensics
* Malware investigations
* Endpoint monitoring
* File analysis

A normal directory listing may not reveal alternate streams.
