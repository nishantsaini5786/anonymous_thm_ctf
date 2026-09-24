<!-- ═══════════════════════════════════════════════════════════════════ -->
<!--                    ANONYMOUS · TRYHACKME                           -->
<!-- ═══════════════════════════════════════════════════════════════════ -->

<div align="center">

```
█████╗ ███╗   ██╗ ██████╗ ███╗   ██╗██╗   ██╗███╗   ███╗ ██████╗ 
██╔══██╗████╗  ██║██╔═══██╗████╗  ██║╚██╗ ██╔╝████╗ ████║██╔═══██╗
███████║██╔██╗ ██║██║   ██║██╔██╗ ██║ ╚████╔╝ ██╔████╔██║██║   ██║
██╔══██║██║╚██╗██║██║   ██║██║╚██╗██║  ╚██╔╝  ██║╚██╔╝██║██║   ██║
██║  ██║██║ ╚████║╚██████╔╝██║ ╚████║   ██║   ██║ ╚═╝ ██║╚██████╔╝
╚═╝  ╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝   ╚═╝     ╚═╝ ╚═════╝ 
```

### `[ We are Anonymous. We are Legion. We do not forgive. We do not forget. Expect us. ]`

![Platform](https://img.shields.io/badge/Platform-TryHackMe-red?style=for-the-badge&logo=tryhackme)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy%2FMedium-green?style=for-the-badge)
![OS](https://img.shields.io/badge/OS-Linux-blue?style=for-the-badge&logo=linux)
![Status](https://img.shields.io/badge/Status-ROOTED-critical?style=for-the-badge)

</div>

---

```bash
┌──(root㉿kali)-[~]
└─# whoami
root
┌──(root㉿kali)-[~]
└─# echo "Mission Accomplished ✔"
```

---

## 🎯 Mission Brief

> **Codename:** `ANONYMOUS`
> **Target IP:** `10.146.161.175`
> **Objective:** Capture `user.txt` and `root.txt`
> **Difficulty:** Easy / Medium
> **Class:** Boot2Root · Linux

A Linux box hiding in plain sight. Three doors left open —
**FTP**, **SMB**, and **SSH** — and a silent cron job that never
stops watching. One writable script is all it takes to bring
the whole system down.

---

## 🧠 Skills Unlocked

| 🛠️ Area | 💥 Technique |
|----------|--------------|
| Reconnaissance | `nmap` full port & service scan |
| FTP Abuse | Anonymous login → download files |
| SMB Enumeration | `smbclient` · null session · share listing |
| Credential Reuse | Leaked creds → SSH access |
| Privilege Escalation | Cron job + world-writable script → root shell |

---

## 🗺️ Attack Path

```mermaid
graph LR
    A[🔍 Nmap Scan] --> B[📂 FTP Anonymous]
    A --> C[📁 SMB Shares]
    C --> D[🔑 user.txt]
    B --> E[📜 clean.sh Leaked]
    D --> F[🚪 SSH Login]
    F --> G[🕒 Cron Job Found]
    G --> H[✏️ Modify clean.sh]
    H --> I[👑 ROOT]
    I --> J[🏁 root.txt]
```

---

## ⚔️ Kill Chain

```diff
+ [01] RECON      →  4 open ports discovered
+ [02] FTP        →  anonymous access granted
+ [03] SMB        →  share "pics" exposed user.txt
+ [04] CREDS      →  reused to log in via SSH
+ [05] PRIVESC    →  /opt/clean.sh writable by all
+ [06] CRON       →  root executes script every minute
+ [07] PAYLOAD    →  reverse shell injected
+ [08] ROOT       →  full system compromise
```

---

## 🧰 Arsenal

```
nmap   ·   ftp   ·   smbclient   ·   enum4linux   ·   nc   ·   ssh
```

---

## 📸 Captured Flags

```bash
user.txt  →  90ddf992585815ff991e68748c414740
root.txt  →  4d930091c31a622a7ed10f27999af363
```

---

## 🖼️ Evidence
<img width="1920" height="1080" alt="Screenshot_2026-09-23_22_34_54" src="https://github.com/user-attachments/assets/05c939c5-b4e7-4be0-9fbc-a9ab66e9f219" />
<img width="1920" height="1080" alt="Screenshot_2026-09-23_22_37_42" src="https://github.com/user-attachments/assets/a10b2882-77dd-4a32-8618-42da51034ae1" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_23_22_33" src="https://github.com/user-attachments/assets/5fc401f1-c741-467c-b7a2-afa8b196059b" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_21_51_54" src="https://github.com/user-attachments/assets/1cbe9d28-2ac9-4014-9015-79507e7ac9dd" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_21_54_56" src="https://github.com/user-attachments/assets/295f16bb-2394-4ddf-b2d9-34aefe0595ff" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_21_56_30" src="https://github.com/user-attachments/assets/13f51afc-71a3-43c0-99a2-8076a5d3ccc5" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_21_56_32" src="https://github.com/user-attachments/assets/e0d0aa0b-4c66-4092-a413-cca98997b4f0" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_22_43_38" src="https://github.com/user-attachments/assets/bd930e17-27a7-4062-9e88-662dd7d5ef73" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_22_34_19" src="https://github.com/user-attachments/assets/b5a81947-3a8c-4307-a1a4-0e30c8806ae0" />
<img width="500" height="197" alt="put" src="https://github.com/user-attachments/assets/a81d858a-1012-42cc-aa39-543701b4d026" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_23_19_12" src="https://github.com/user-attachments/assets/8f0ad26f-4d79-44e3-b71b-3eacf9a3b17f" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_23_19_53" src="https://github.com/user-attachments/assets/9bfa3fe5-75f1-449b-954b-467a2d91b297" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_23_25_59" src="https://github.com/user-attachments/assets/26259c36-33f4-48eb-803d-132dd51a8097" />
<img width="1920" height="1080" alt="Screenshot_2026-09-24_23_27_01" src="https://github.com/user-attachments/assets/9c9b2de7-5693-406c-8674-c1c58381f9df" />

---

## 💡 One-Line Takeaway

> Enumerate. Enumerate. Enumerate.
> Then let a silent cron job hand you the keys to the kingdom.

---

<div align="center">

```
╔══════════════════════════════════════════════════════════════╗
║   "The quieter you become, the more you are able to hear."  ║
╚══════════════════════════════════════════════════════════════╝
```

⭐ Star this repo if it helped you level up ⭐

</div>

---

> ⚠️ Disclaimer: This writeup is for educational purposes only.
> All testing was conducted in a controlled lab environment
> (TryHackMe) with full permission.
