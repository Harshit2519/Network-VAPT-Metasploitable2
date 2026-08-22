# Network Vulnerability Assessment & Penetration Testing (VAPT)

A full-scope VAPT engagement performed against a simulated enterprise network in an isolated lab environment, following the **Penetration Testing Execution Standard (PTES)**. This project covers the complete workflow of a real-world security assessment — reconnaissance, vulnerability identification, manual exploitation, and professional reporting.

> **Note:** This assessment was conducted entirely within a private, isolated virtual lab against intentionally vulnerable training systems (Metasploitable2). No external, third-party, or production systems were tested.

---

## 🎯 Objective

Simulate a real-world penetration test to identify, validate, and document exploitable vulnerabilities in a network environment — combining automated scanning with manual exploitation to confirm actual risk, not just theoretical CVE matches.

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker Machine | Kali Linux |
| Target | Metasploitable2 (intentionally vulnerable Linux VM) |
| Network Mode | Bridged (isolated lab subnet) |
| Virtualization | VirtualBox |

## 🛠️ Skills & Tools Demonstrated

- **Reconnaissance & Enumeration:** Nmap (service/version detection, NSE scripting)
- **Exploitation:** Metasploit Framework
- **Post-Exploitation:** Privilege escalation validation, sensitive file access
- **Credential Auditing:** John the Ripper (offline dictionary attacks)
- **Methodology:** PTES-aligned engagement structure, CVSS severity scoring
- **Reporting:** Professional VAPT report writing with remediation guidance

## 🔍 Methodology (PTES)

1. Pre-Engagement — scope and rules of engagement definition
2. Reconnaissance — host discovery and full service enumeration
3. Vulnerability Assessment — CVE identification and CVSS classification
4. Exploitation — manual, verified exploitation of identified vulnerabilities
5. Post-Exploitation — privilege and impact validation
6. Reporting — structured findings with remediation recommendations

## 📊 Summary of Findings

| # | Vulnerability | Port/Service | CVE | Severity | Result |
|---|---|---|---|---|---|
| 1 | vsftpd 2.3.4 Backdoor Command Execution | 21/FTP | CVE-2011-2523 | Critical (9.8) | Unauthenticated remote root |
| 2 | Samba `usermap_script` Command Execution | 139,445/SMB | CVE-2007-2447 | Critical (10.0) | Unauthenticated remote root |
| 3 | UnrealIRCd 3.2.8.1 Backdoor Command Execution | 6667/IRC | CVE-2010-2075 | Critical (10.0) | Unauthenticated remote root |
| 4 | Weak Password Hashing (Offline Cracking) | N/A (local) | CWE-916 | High (7.5) | 3/7 accounts cracked in <1 min |

All three critical vulnerabilities resulted in **complete unauthenticated remote root compromise**, independently confirmed with command-line evidence (`id`, `whoami`). The fourth finding demonstrated that even with all services patched, weak MD5-crypt password hashing would still allow significant credential recovery via a standard wordlist attack.

## 📁 Repository Contents

```
├── README.md
├── report/
│   └── Network_VAPT_Report.docx      # Full professional VAPT report
├── scans/
│   └── metasploitable2_nmap_scan.txt # Raw Nmap reconnaissance output
├── evidence/
│   └── screenshots/                  # Exploitation proof-of-concept screenshots
└── findings-log/
    └── VAPT_Findings_Log.xlsx        # Structured findings tracker (CVSS, PoC, remediation)
```

## 📄 Full Report

The complete report — including detailed exploitation steps, evidence, CVSS-scored findings, risk assessment, and remediation recommendations for each vulnerability — is available in [`report/Network_VAPT_Report.docx`](./report/Network_VAPT_Report.docx).

## ⚠️ Disclaimer

This project was conducted for educational purposes only, within a private, isolated lab environment against intentionally vulnerable training software. None of the techniques described here were used against any system without explicit authorization. Unauthorized access to computer systems is illegal.

---

**Author:** Harshit Vishwakarma
**Program:** B.Tech CSE, Amity University Uttar Pradesh
