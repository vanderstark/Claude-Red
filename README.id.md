![claude-red banner](/assets/banner.png)

<div align="center">

# claude-red
**Offensive security skills untuk Claude — berkas berstruktur `SKILL.md` yang mengubah Claude menjadi operator red team berbasis konteks.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-78-red.svg)](#skill-index)
[![Categories](https://img.shields.io/badge/categories-23-orange.svg)](#categories)
[![Stars](https://img.shields.io/github/stars/SnailSploit/claude-red?style=social)](https://github.com/SnailSploit/claude-red)
[![Forks](https://img.shields.io/github/stars/SnailSploit/claude-red?style=social)](https://github.com/SnailSploit/claude-red/network/members)

[Overview](#overview) &bull; [Quickstart](#quickstart) &bull; [Categories](#categories) &bull; [Skill Index](#skill-index) &bull; [Roadmap](#roadmap) &bull; [Mengontribusi](#mengontribusi)

</div>

---

## Overview

`claude-red` adalah perpustakaan yang ditrulasi berisi skill keamanan offensive untuk sistem [Claude Skills](https://docs.claude.com). Setiap skill adalah berkas struktur `SKILL.md` yang memberi Claude metodologi ahli level untuk permukaan serangan tertentu — mulai dari SQL injection hingga shellcode, EDR evasion hingga ADCS abuse.

Letakkan skill ke dalam lingkungan Claude Anda dan ia berperilakulah sebagai specialist domain: ia mengerti teknik, peralatan, edge cases, dan jalur eskalasi. Skills dimuat secara on-demand berdasarkan trigger percakapan — Anda tidak membayar context untuk skills yang tidak digunakan.

**Use cases:** penghuluatan red team yang terotorisasi, triage bug bounty, riset keamanan, persiapan CTF, pelatihan operator, dan eksplorasi permukaan serangan secara terstruktur.

---

## Quickstart

### Claude Skills System (Disarankan)

```bash
git clone https://github.com/SnailSploit/claude-red ~/.claude/skills/claude-red
```

Claude secara otomatis memuat skills yang cocok berdasarkan trigger percakapan (misal, menyebut SQL injection memuat `offensive-sqli`).

Untuk menginstal satu kategori:

```bash
git clone --filter=blob:none --sparse https://github.com/SnailSploit/claude-red
cd claude-red && git sparse-checkout set Skills/web Skills/active-directory
```

### Claude Code

```bash
cat Skills/web/offensive-sqli/SKILL.md | claude --system-file -
cat Skills/active-directory/**/SKILL.md | claude --system-file -
```

### Claude.ai (Manual)

Tempel konten `SKILL.md` ke dalam system prompt proyek atau tempel di awal percakapan Anda.

### Skrip Instalasi

```bash
./install.sh                           # interaktif
./install.sh --target ~/.claude/skills # target eksplisit
./install.sh --category web            # satu kategori
```

---

## Kategori

| Kategori | Skills | Fokus |
|---|---:|---|
| [Web Application](#web-application) | 16 | OWASP Top 10, business logic, advanced web vulnerability classes |
| [Auth & Identity](#auth--identity) | 2 | JWT exploitation, OAuth/OIDC abuse |
| [Active Directory](#active-directory) | 1 | On-prem AD attack methodology |
| [Wireless](#wireless) | 14 | 802.11, WPA2/3, EAP, WPS, evil-twin, BLE, Zigbee, Z-Wave, LoRa, sub-GHz |
| [Cloud](#cloud) | 1 | AWS, Azure, GCP attack paths |
| [Mobile](#mobile) | 1 | Android dan iOS application testing |
| [IoT & Embedded](#iot--embedded) | 1 | Hardware, firmware, RTOS, ICS/OT |
| [Infrastructure & Red Team](#infrastructure--red-team) | 7 | Initial access, EDR evasion, advanced red team operations, Windows internals |
| [Exploit Development](#exploit-development) | 6 | Stack/heap corruption, ROP, mitigations, crash analysis, TOCTOU |
| [Fuzzing & Vulnerability Research](#fuzzing--vulnerability-research) | 4 | libFuzzer, AFL++, coverage-guided fuzzing, vulnerability taxonomy |
| [Reconnaissance](#reconnaissance) | 2 | OSINT tooling dan structured intelligence collection |
| [API Security](#api-security) | 2 | REST/gRPC/WebSocket testing, business logic abuse |
| [Container & Kubernetes](#container--kubernetes) | 2 | Container escape, Kubernetes cluster exploitation |
| [CI/CD & Pipeline](#cicd--pipeline) | 2 | Pipeline exploitation, secrets extraction |
| [Cryptography](#cryptography) | 2 | Cryptographic implementation attacks, TLS/SSL |
| [Privilege Escalation](#privilege-escalation) | 2 | Linux dan Windows privilege escalation |
| [Post-Exploitation](#post-exploitation) | 3 | Lateral movement, persistence mechanisms, data exfiltration |
| [Forensics & C2](#forensics--c2) | 2 | Anti-forensics tradecraft, C2 framework operations |
| [Supply Chain](#supply-chain) | 2 | Supply chain attacks, dependency confusion |
| [Social Engineering](#social-engineering) | 2 | Phishing campaigns, physical/vishing/smishing |
| [Network Attacks](#network-attacks) | 1 | Layer 2/3 attacks, MITM, protocol poisoning |
| [AI Security](#ai-security) | 1 | Prompt injection, jailbreaking, RAG poisoning |
| [Utility](#utility) | 2 | Fast triage checklists, professional reporting |

---