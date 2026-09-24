<!-- ═══════════════════════════════════════════════════════════════════ -->
<!--                  A N O N Y M O U S   ·   T H M                     -->
<!-- ═══════════════════════════════════════════════════════════════════ -->

<div align="center">

<h1>🕶️ A N O N Y M O U S 🕶️</h1>

<h3><i>"We are Anonymous. We are Legion.<br>We do not forgive. We do not forget. Expect us."</i></h3>

```
    █████╗ ███╗   ██╗ ██████╗ ███╗   ██╗██╗   ██╗███╗   ███╗ ██████╗ ██╗   ██╗███████╗
   ██╔══██╗████╗  ██║██╔═══██╗████╗  ██║╚██╗ ██╔╝████╗ ████║██╔═══██╗██║   ██║██╔════╝
   ███████║██╔██╗ ██║██║   ██║██╔██╗ ██║ ╚████╔╝ ██╔████╔██║██║   ██║██║   ██║███████╗
   ██╔══██║██║╚██╗██║██║   ██║██║╚██╗██║  ╚██╔╝  ██║╚██╔╝██║██║   ██║██║   ██║╚════██║
   ██║  ██║██║ ╚████║╚██████╔╝██║ ╚████║   ██║   ██║ ╚═╝ ██║╚██████╔╝╚██████╔╝███████║
   ╚═╝  ╚═╝╚═╝  ╚═══╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝   ╚═╝     ╚═╝ ╚═════╝  ╚═════╝ ╚══════╝
                          ▓▓▓  HACK THE PLANET  ▓▓▓
```

<p>
  <img src="https://img.shields.io/badge/Platform-TryHackMe-red?style=for-the-badge&logo=tryhackme&logoColor=white"/>
  <img src="https://img.shields.io/badge/Difficulty-Easy%20%2F%20Medium-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/OS-Linux-blue?style=for-the-badge&logo=linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Class-Boot2Root-black?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-ROOTED-critical?style=for-the-badge&logo=gnubash&logoColor=white"/>
</p>

</div>

---

<div align="center">

```console
┌──(root㉿anonymous)-[~]
└─# whoami
root

┌──(root㉿anonymous)-[~]
└─# id
uid=0(root) gid=0(root) groups=0(root)

┌──(root㉿anonymous)-[~]
└─# echo "Mission Accomplished ✔"
Mission Accomplished ✔
```

</div>

---

## 🎯 Mission Brief

<table align="center">
<tr><td align="right"><b>Codename</b></td><td><code>ANONYMOUS</code></td></tr>
<tr><td align="right"><b>Platform</b></td><td>TryHackMe</td></tr>
<tr><td align="right"><b>Target IP</b></td><td><code>10.146.161.175</code></td></tr>
<tr><td align="right"><b>Objective</b></td><td>Capture <code>user.txt</code> &amp; <code>root.txt</code></td></tr>
<tr><td align="right"><b>Difficulty</b></td><td>Easy / Medium</td></tr>
<tr><td align="right"><b>Class</b></td><td>Boot2Root · Linux</td></tr>
</table>

> *A Linux box hiding in plain sight.*
> Three doors left wide open — **FTP**, **SMB**, and **SSH** —
> and a silent **cron job** that never stops watching.
> One writable script is all it takes to bring the whole system down.

---

## 🧠 Skills Unlocked

| 🛠️ Area                | 💥 Technique                                          |
|------------------------|------------------------------------------------------|
| 🔍 **Reconnaissance**   | `nmap` full port & service scan                      |
| 📂 **FTP Abuse**        | Anonymous login → download sensitive files           |
| 📁 **SMB Enumeration**  | `smbclient` · null session · share listing           |
| 🔑 **Credential Reuse** | Leaked creds → SSH access                            |
| 👑 **Privilege Escalation** | Cron job + world-writable script → reverse shell |

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

    style A fill:#1f6feb,color:#fff
    style I fill:#d32f2f,color:#fff
    style J fill:#f9a825,color:#000
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

<p align="center">
  <img src="https://img.shields.io/badge/nmap-4682B4?style=flat-square&logo=linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/ftp-00599C?style=flat-square&logo=files&logoColor=white"/>
  <img src="https://img.shields.io/badge/smbclient-8B0000?style=flat-square&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/enum4linux-444444?style=flat-square&logo=linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/netcat-2E2E2E?style=flat-square&logo=gnubash&logoColor=white"/>
  <img src="https://img.shields.io/badge/ssh-4B0082?style=flat-square&logo=openssh&logoColor=white"/>
</p>

---

## 🏆 Captured Flags

```bash
╭─────────────────────────────────────────────────────────────╮
│  user.txt  →  90ddf992585815ff991e68748c414740              │
│  root.txt  →  4d930091c31a622a7ed10f27999af363              │
╰─────────────────────────────────────────────────────────────╯
```

---

## 🖼️ Evidence

<div align="center">


<img width="900" src="https://github.com/user-attachments/assets/05c939c5-b4e7-4be0-9fbc-a9ab66e9f219"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/a10b2882-77dd-4a32-8618-42da51034ae1"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/5fc401f1-c741-467c-b7a2-afa8b196059b"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/1cbe9d28-2ac9-4014-9015-79507e7ac9dd"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/295f16bb-2394-4ddf-b2d9-34aefe0595ff"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/13f51afc-71a3-43c0-99a2-8076a5d3ccc5"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/e0d0aa0b-4c66-4092-a413-cca98997b4f0"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/bd930e17-27a7-4062-9e88-662dd7d5ef73"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/b5a81947-3a8c-4307-a1a4-0e30c8806ae0"/><br><br>

<img width="500" src="https://github.com/user-attachments/assets/a81d858a-1012-42cc-aa39-543701b4d026"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/8f0ad26f-4d79-44e3-b71b-3eacf9a3b17f"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/9bfa3fe5-75f1-449b-954b-467a2d91b297"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/26259c36-33f4-48eb-803d-132dd51a8097"/><br><br>

<img width="900" src="https://github.com/user-attachments/assets/9c9b2de7-5693-406c-8674-c1c58381f9df"/><br>

</div>

---

## 💡 One-Line Takeaway

> **Enumerate. Enumerate. Enumerate.**
> Then let a silent cron job hand you the keys to the kingdom.

---

<div align="center">

```
╔══════════════════════════════════════════════════════════════╗
║   "The quieter you become, the more you are able to hear."  ║
║                        — Kali Linux                          ║
╚══════════════════════════════════════════════════════════════╝
```

### ⭐ Star this repo if it helped you level up ⭐

<sub>Made with 🖤 by a fellow hacker</sub>

</div>

---

> ⚠️ **Disclaimer**
> This writeup is for **educational purposes only**.
> All testing was conducted in a controlled lab environment
> (TryHackMe) with full permission.

<!-- ═══════════════════════════════════════════════════════════════════ -->
<!--                          END OF FILE                                -->
<!-- ═══════════════════════════════════════════════════════════════════ -->
