# Lab 1.2 — Audit System Passwords Using L0phtCrack

## 🎯 Objective

Demonstrate offline password auditing against a deliberately created Windows laboratory account.

## 🧪 Requirements

* Windows laboratory VM
* L0phtCrack 7
* Administrator privileges
* A controlled laboratory wordlist

> ⚠️ Only audit password hashes from systems/accounts for which you have authorization.

---

## Step 1 — Create a Laboratory Wordlist

Create the directory:

```powershell
New-Item -ItemType Directory -Path C:\Lab -Force
```

Create a small test wordlist:

```powershell
@"
Workshop123!
Password123!
LabPassword123!
"@ | Out-File C:\Lab\lab-passwords.txt -Encoding ASCII
```

Check it:

```powershell
Get-Content C:\Lab\lab-passwords.txt
```

---

## Step 2 — Open L0phtCrack

Run **L0phtCrack 7 as Administrator**.

Select:

```text
Import
   ↓
Import from local Windows system
   ↓
Run Import Immediately
```

Allow the local Windows password hashes to be imported.

---

## Step 3 — Create a New Audit

Navigate to:

```text
Audit
   ↓
New Audit
```

Select:

```text
Dictionary
```

Choose:

```text
C:\Lab\lab-passwords.txt
```

---

## Step 4 — Start the Audit

Start the password audit.

L0phtCrack will compare the candidate passwords against the imported laboratory password hashes.

---

## Step 5 — Examine the Result

Locate:

```text
ntlm_lab
```

If the password used for the laboratory account exists in the wordlist, the audit should identify it.

---

## 🧠 What You Learned

Password auditing demonstrates why:

* Weak passwords are vulnerable to dictionary attacks.
* Password hashes should be protected.
* Strong and unique passwords are important.
* Password auditing should only be performed with authorization.

## 🧹 Cleanup

Remove the laboratory wordlist:

```powershell
Remove-Item C:\Lab\lab-passwords.txt -Force
```

Remove the temporary account if it is no longer required:

```cmd
net user ntlm_lab /delete
```
