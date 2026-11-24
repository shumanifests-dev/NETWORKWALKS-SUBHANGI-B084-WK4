# Black-Box Web Application Penetration Test — Mediroza General Hospital

![Assessment](https://img.shields.io/badge/Type-Black--Box%20Pentest-critical)
![Environment](https://img.shields.io/badge/Environment-Kali%20Linux-blue)
![Standards](https://img.shields.io/badge/Standards-OWASP%20WSTG%20v4.2%20%7C%20CVSS%20v3.1-informational)
![Batch](https://img.shields.io/badge/Program-B084%20Networkwalks-success)

Full black-box web application penetration test and vulnerability assessment conducted against **Mediroza General Hospital** (`https://medirozahospital.com`) as part of **Program / Batch B084 – Networkwalks**.

> **Authorization & Scope:** Executed under written client authorization during a 3-day assessment window (22–24 November 2026) from a Kali Linux VirtualBox environment, strictly excluding social engineering, denial-of-service (DoS/DDoS), and out-of-scope systems.

---

## Engagement Overview

| Parameter | Details |
| :--- | :--- |
| **Target Host** | `https://medirozahospital.com` (`199.188.201.16`) |
| **Technology Stack** | Mediroza CMS 1.4.2 / LiteSpeed / PHP 8.2.36 / MySQL |
| **Assessment Type** | Full Black-Box Web Application Penetration Test |
| **Testing Environment** | Kali Linux x86_64 (VirtualBox) |
| **Prepared By** | Subhangi (Batch B084 – Networkwalks) |

---

## End-to-End Attack Kill Chain

```text
[Phase 1: Recon] /robots.txt + LiteSpeed autoindex expose /patient/, /staff/, /old/
       │
       ▼
[Phase 2: Exploitation] SQLi (admin' -- -) on /patient/login.php bypasses auth (CVSS 9.8)
       │
       ▼
[Phase 3: Crypto Forensics] pdf2john.pl + hashcat (-m 10500) crack RC4-128 PDFs in 2s
       │
       ▼
[Phase 4: Post-Exploitation] pypdf extracts /Comments metadata pointing to /old/ backup
       │
       ▼
[Impact] Unauthenticated download of mediroza_db_backup_2019.sql (HR & Shareholder DB)