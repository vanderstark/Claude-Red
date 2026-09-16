![claude-red banner](/assets/banner.png)

<div align="center">

# claude-red

**Skill keamanan offensive untuk Claude — berkas `SKILL.md` siap pakai yang mengubah Claude menjadi operator red team berbasis konteks.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-78-red.svg)](#skill-index)
[![Categories](https://img.shields.io/badge/categories-23-orange.svg)](#categories)
[![Stars](https://img.shields.io/github/stars/SnailSploit/claude-red?style=social)](https://github.com/SnailSploit/claude-red)
[![Forks](https://img.shields.io/github/forks/SnailSploit/claude-red?style=social)](https://github.com/SnailSploit/claude-red/network/members)

[Overview](#overview) &bull; [Quickstart](#quickstart) &bull; [Categories](#categories) &bull; [Skill Index](#skill-index) &bull; [Roadmap](#roadmap) &bull; [Mengontribusi](#mengontribusi)

</div>

---

## Overview

`claude-red` adalah perpustakaan terpilih berisi skill keamanan offensive untuk sistem [Claude Skills](https://docs.claude.com). Setiap skill adalah berkas terstruktur `SKILL.md` yang mempersiapkan Claude dengan metodologi tingkat ahli untuk permukaan serangan tertentu — mulai dari SQL injection hingga shellcode, EDR evasion hingga ADCS abuse.

Letakkan skill ke dalam lingkungan Claude Anda dan ia berperilaku sebagai specialist domain: menguasai teknik, peralatan, edge case, dan jalur eskalasi. Skills dimuat secara on-demand berdasarkan pemicu percakapan — Anda tidak membayar context untuk skills yang tidak digunakan.

**Use cases:** penghuluatan red team yang terotorisasi, triage bug bounty, riset keamanan, persiapan CTF, pelatihan operator, dan eksplorasi permukaan serangan secara metodis.

---

## Quickstart

### Claude Skills System (Disarankan)

```bash
git clone https://github.com/SnailSploit/claude-red ~/.claude/skills/claude-red
```

Claude secara otomatis memuat skills yang cocok berdasarkan pemicu percakapan (misalnya, menyebut SQL injection memuat `offensive-sqli`).

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

Tempel isi dari berkas `SKILL.md` ke system prompt proyek atau tambahkan di awal percakapan.

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
| [Active Directory](#active-directory) | 1 | Metodologi serangan AD on-premise |
| [Wireless](#wireless) | 14 | 802.11, WPA2/3, EAP, WPS, evil-twin, BLE, Zigbee, Z-Wave, LoRa, sub-GHz |
| [Cloud](#cloud) | 1 | Jalur serangan AWS, Azure, GCP |
| [Mobile](#mobile) | 1 | Pengujian aplikasi Android dan iOS |
| [IoT & Embedded](#iot--embedded) | 1 | Hardware, firmware, RTOS, ICS/OT |
| [Infrastructure & Red Team](#infrastructure--red-team) | 7 | Initial access, EDR evasion, operasi red team lanjutan, Windows internals |
| [Exploit Development](#exploit-development) | 6 | Stack/heap corruption, ROP, mitigations, crash analysis, TOCTOU |
| [Fuzzing & Vulnerability Research](#fuzzing--vulnerability-research) | 4 | libFuzzer, AFL++, fuzzing berbasis coverage, taksonomi kerentanan |
| [Reconnaissance](#reconnaissance) | 2 | Alat OSINT dan pengumpulan intelijen terstruktur |
| [API Security](#api-security) | 2 | Pengujian REST/gRPC/WebSocket, abuse business logic |
| [Container & Kubernetes](#container--kubernetes) | 2 | Container escape, eksploitasi klaster Kubernetes |
| [CI/CD & Pipeline](#cicd--pipeline) | 2 | Eksploitasi pipeline, ekstraksi rahasia |
| [Cryptography](#cryptography) | 2 | Serangan implementasi kriptografi, TLS/SSL |
| [Privilege Escalation](#privilege-escalation) | 2 | Eskalasi hak Linux dan Windows |
| [Post-Exploitation](#post-exploitation) | 3 | Lateral movement, mekanisme persistence, data exfiltration |
| [Forensics & C2](#forensics--c2) | 2 | Tradecraft anti-forensik, operasi framework C2 |
| [Supply Chain](#supply-chain) | 2 | Serangan supply chain, dependency confusion |
| [Social Engineering](#social-engineering) | 2 | Kampanye phishing, physical/vishing/smishing |
| [Network Attacks](#network-attacks) | 1 | Serangan layer 2/3, MITM, protocol poisoning |
| [AI Security](#ai-security) | 1 | Prompt injection, jailbreaking, RAG poisoning |
| [Utility](#utility) | 2 | Checklist triage cepat, pelaporan profesional |

---
---

## Roadmap

Perpustakaan ini terus dikembangkan melalui beberapa fase. Lihat [CHANGELOG.md](CHANGELOG.md) untuk riwayat rilis.

| Fase | Fokus | Skills | Status |
|---|---|---:|---|
| 1 | AD Internal/Windows — dipecah menjadi skill terfokus | +16 | Direncanakan |
| 2 | Identitas Cloud — Entra, ADFS, Okta, M365 | +10 | Direncanakan |
| 3 | Nirkabel — WPA2/3, EAP, BLE, Zigbee, Z-Wave, LoRa, sub-GHz | +12 | Selesai |
| 4 | IoT — UART/JTAG, ekstraksi flash, fault injection, RTOS, ICS | +10 | Direncanakan |
| 5 | Dasar Web — rekonsiliasi, bypass otorisasi, access control, CSRF, CORS | +8 | Direncanakan |
| 6 | Lanjutan Web — proto pollution, SAML, OIDC, WebSocket, SSI/ESI | +10 | Direncanakan |
| 7 | Dokumentasi dan poles alat | — | Selesai |
| 8 | Kategori baru — 10 domain baru dengan 20 skill | +20 | Selesai |
| 9 | Penulisan ulang mendalam — deserialisasi, GraphQL, red team lanjutan, SSTI | — | Selesai |

Target: ~130 skills di lebih dari 23 kategori.

---

## Mengontribusi

Kontribusi sangat diterima. Lihat [CONTRIBUTING.md](CONTRIBUTING.md) untuk template skill, standar frontmatter, dan proses review. Skill yang terfokus pada satu permukaan serangan lebih disukai daripada tinjauan umum yang monolitik.

## Lisensi

[MIT](LICENSE) — gunakan secara bebas, atribusi sangat dihargai.

## Penghargaan

- **Penulis:** [Kai Aizen](https://snailsploit.com) (SnailSploit) — riset keamanan GenAI
- **Checklist Asli:** [Sahar Shlichov](https://github.com/sahar042/offensive-checklist) — koleksi checklist ofensif yang menjadi dasar bagi banyak skill ini
- **Komunitas:** Pull request dan umpan balik yang menjaga perpustakaan tetap selaras dengan perkembangan lanskap ancaman

---

<div align="center">

*Berikan Claude skill yang tepat dan ia berhenti menjadi sekadar chatbot — ia menjadi operator.*

[snailsploit.com](https://snailsploit.com) &bull; [GitHub](https://github.com/SnailSploit) &bull; [Riset](https://snailsploit.com/research) &bull; [X](https://x.com/SnailSploit)

</div>
