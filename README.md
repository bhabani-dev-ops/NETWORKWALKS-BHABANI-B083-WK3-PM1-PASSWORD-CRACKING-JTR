# NETWORKWALKS-BHABANI-B083-WK3-PM1-PASSWORD-CRACKING-JTR

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Tool](https://img.shields.io/badge/tool-John%20the%20Ripper-red)
![Platform](https://img.shields.io/badge/platform-Kali%20Linux-blue)
![Category](https://img.shields.io/badge/category-Password%20Cracking-orange)

## 📌 Project Overview

This repository documents **Week 3 – Project Module 1** of the Networkwalks Cybersecurity & Ethical Hacking internship: cracking the password of an encrypted PDF file using **John the Ripper (JTR)**, via both the **CLI (`john`)** and the **GUI (`Johnny`)**, on Kali Linux.

## 🎯 Objective

Recover the password of the protected file `My-Locked-PDF1.pdf` using JTR John and JTR Johnny, to understand how password cracking works and why strong passwords matter for protecting sensitive files.

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| `pdf2john` | Extracts a crackable hash from the password-protected PDF |
| `john` (John the Ripper CLI) | Cracks the extracted hash using its default wordlist |
| `johnny` (Johnny GUI) | GUI front-end for John the Ripper, used to verify the crack visually |

## 🖥️ Environment

- **OS:** Kali Linux
- **Target file:** `My-Locked-PDF1.pdf`

## 📋 Steps Performed

### Step 1: Extract the password hash

```bash
pdf2john My-Locked-PDF1.pdf > hash1.txt
cat hash1.txt
```

Output:
```
My-Locked-PDF1.pdf:$pdf$4*4*128*-1060*1*16*55d1a5c14175da449753199e44971d32*32*777fd021a7f3c5ae598c0c6495c7f76e00000000000000000000000000000000*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1
```

📸 **Screenshot 1** – Hash extracted from the PDF
`![Hash Extraction](01-hash-extracted.png)`

### Step 2: Crack the hash with John the Ripper (CLI)

```bash
john hash1.txt
```

Output:
```
Loaded 1 password hash (PDF [MD5 SHA2 RC4/AES 32/64])
Proceeding with wordlist:/usr/share/john/password.lst
password1        (My-Locked-PDF1.pdf)
1g 0:00:00:00 DONE 2/3 (2026-09-24 03:20) 1.052g/s 43425p/s 43425c/s 43425C/s
Session completed.
```

Verified with:
```bash
john --show --format=PDF hash1.txt
```

📸 **Screenshot 2** – Password cracked via John CLI (`password1`)
`![John CLI Crack](02-john-cli-cracked.png)`

### Step 3: Verify with Johnny (GUI)

- Opened Johnny → **Open password file** → selected `hash1.txt`
- Clicked **Start new attack**
- Result: `100% (1/1: 1 cracked, 0 left)` → password `password1`

📸 **Screenshot 3** – Password cracked via Johnny GUI
`![Johnny GUI Crack](04-johnny-gui-cracked.png)`

### Step 4: Unlock the PDF

Opened `My-Locked-PDF1.pdf` using the recovered password `password1` — file unlocked successfully.

## ✅ Result

| File | Recovered Password |
|------|--------------------|
| My-Locked-PDF1.pdf | `password1` |

## 🧠 What I Learned

- How to extract a crackable hash from a password-protected PDF using `pdf2john`
- How John the Ripper uses wordlists (e.g. `password.lst`, `rockyou.txt`) to perform dictionary-based password cracking
- The difference between using JTR via CLI (`john`) vs its GUI front-end (`johnny`) — same cracking engine, different interface
- Why weak, dictionary-based passwords (like `password1`) are cracked almost instantly, reinforcing the need for strong, unique passwords

## ⚠️ Disclaimer

This exercise was performed strictly for educational purposes as part of the Networkwalks Cybersecurity & Ethical Hacking internship, using a file provided for lab practice. Password cracking techniques should only ever be used on systems/files you own or have explicit written authorization to test.

## 👤 Author

| Field | Detail |
|-------|--------|
| Name | Bhabani Priyadarshini Panda |
| Program | Networkwalks Cybersecurity & Ethical Hacking Internship |
| Batch | B083 |
| Week | Week 3 – Project Module 1 |
| LinkedIn | [linkedin.com/in/bhabani-panda-79a04a308](https://linkedin.com/in/bhabani-panda-79a04a308) |
