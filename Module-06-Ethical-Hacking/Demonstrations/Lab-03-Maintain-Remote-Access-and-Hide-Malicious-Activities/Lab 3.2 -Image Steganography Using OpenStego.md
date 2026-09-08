# Lab 3.2 — Image Steganography Using OpenStego

## 🎯 Objective

Demonstrate how harmless information can be embedded inside an image using steganography.

---

## Step 1 — Create the Laboratory Directory

```powershell
New-Item -ItemType Directory -Path C:\Lab\Stego -Force
```

---

## Step 2 — Create the Secret Test File

```powershell
"Confidential workshop demonstration data" | Out-File C:\Lab\Stego\secret.txt
```

Verify:

```powershell
Get-Content C:\Lab\Stego\secret.txt
```

---

## Step 3 — Add a PNG Image

Place an ordinary PNG image inside:

```text
C:\Lab\Stego\
```

Verify:

```powershell
Get-ChildItem C:\Lab\Stego
```

---

## Step 4 — Open OpenStego

Launch OpenStego.

Select:

```text
Hide data
```

Configure:

```text
Message/File:
C:\Lab\Stego\secret.txt

Cover file:
C:\Lab\Stego\<image>.png
```

Select an output location for the generated stego image.

---

## Step 5 — Extract the Data

OpenStego can also be used to demonstrate extraction.

Select:

```text
Extract data
```

Select the generated stego image and provide an output directory.

---

## Step 6 — Verify the Extracted File

```powershell
Get-ChildItem C:\Lab\Stego
```

Read the extracted file:

```powershell
Get-Content <extracted-file>
```

---

## 🧠 What You Learned

Steganography hides information inside another file.

```text
Cover Image
     +
Hidden Data
     ↓
Stego Image
```

Steganography is different from encryption because the primary objective is to conceal the existence of the message.
