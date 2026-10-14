# Capstone Project 3: Penetration Test Report (Metasploitable 3 Environment)

## 📜 Project Overview
This repository contains the final penetration test report and supporting documentation for **Capstone Project 3**, conducted by **Group 4**. The assessment targeted a simulated legacy hybrid environment (Metasploitable 3) representing a midsize organization's development infrastructure.

The project demonstrates the full lifecycle of a professional penetration test, including scoping, reconnaissance, exploitation, post-exploitation analysis, and remediation planning, adhering to **PTES** and **NIST SP 800-115** standards.

## ⚠️ Confidentiality & Disclaimer
**This document contains proprietary and confidential security assessment information.**
- **Access:** Restricted to authorized personnel, academic assessors, and the internal security team.
- **Scope:** This assessment is a snapshot of a controlled laboratory environment as of **11 September 2026**.
- **Limitations:** The absence of a finding does not prove vulnerability absence. Testing was non-destructive and limited to the defined scope (192.168.56.0/24).
- **Usage:** Findings are intended for educational purposes and internal security improvement simulations only.

## 🎯 Assessment Objectives
The primary goals of this engagement were:
1.  Identify exploitable attack paths in a legacy development environment.
2.  Validate defensive visibility (using Wazuh telemetry).
3.  Test custom Python tooling for reconnaissance and scanning.
4.  Produce a prioritized remediation plan to mitigate critical risks.

## 📊 Executive Summary of Findings
The assessment identified **11 findings** across the target infrastructure:
- **🔴 Critical (2):** Direct privileged host compromise potential (e.g., MS17-010/EternalBlue, ProFTPD mod_copy).
- **🟠 High (3):** Likely unauthorized access or lateral movement capabilities (e.g., Default credentials, Exposed admin routes).
- **🟡 Medium (4):** Material exposures requiring planned remediation (e.g., Reflected XSS, SUID misconfigurations).
- **🟢 Low (2):** Hardening weaknesses and best practice violations.

**Overall Risk Posture:** **Critical.** Immediate isolation and remediation of SMBv1, vulnerable services, and weak credentials are required.

## 🛡️ Scope of Work
### In-Scope Assets
| Asset ID | Description | Platform | Role |
| :--- | :--- | :--- | :--- |
| ASSET-01 | Target Linux Machine | Ubuntu 14.04.5 LTS | Linux services, web/app surface. |
| ASSET-02 | Target Windows Machine | Windows Server 2008 R2 | Windows services, SMB. |
| ASSET-03 | Custom Web Infrastructure | Python/Flask | Application surface. |
| ASSET-04 | Diagnostic/Admin Endpoint | API Utilities | Administrative functions. |
| ASSET-05 | Database Engine | Legacy DB Service | Data storage. |

**Network Range:** 192.168.56.0/24 (Isolated Lab Environment)
**Testing Platform:** Kali Linux (192.168.56.1)

### Out-of-Scope
- Production systems outside the development subnet.
- Social engineering, phishing, or physical security testing.
- Denial-of-Service (DoS) or destructive actions.
- Third-party cloud infrastructure.

## 🔍 Methodology
The assessment followed a strict four-phase methodology:
1.  **Reconnaissance:** Host discovery, OS fingerprinting, and network mapping (Nmap, Custom Python TCP Scanner).
2.  **Enumeration & Scanning:** Service-specific enumeration, vulnerability scanning (Nessus/OpenVAS), and web app checks.
3.  **Exploitation & Post-Exploitation:** Controlled validation of findings, privilege escalation checks, and lateral movement review (Metasploit, Manual Validation).
4.  **Evidence & Reporting:** Consolidation of findings, severity ranking (CVSS), and remediation mapping.

## 📂 Repository Contents
- `Capstone_Project_3_Penetration_Test_Report.pdf`: The full, confidential penetration test report.
- `Executive_Summary_Redacted.pdf`: A sanitized version of findings for public sharing (if applicable).
- `Scripts/`: Custom Python tools developed for reconnaissance and scanning (if applicable).
- `Remediation_Guidelines.md`: Detailed steps for fixing identified vulnerabilities.

## 🔑 Key Findings & Remediation Highlights
| ID | Finding | Severity | Recommendation |
| :--- | :--- | :--- | :--- |
| F-01 | SMBv1 / MS17-010 (EternalBlue) | **Critical** | Apply MS patches, disable SMBv1, restrict TCP 445. |
| F-02 | ProFTPD mod_copy (CVE-2015-3306) | **Critical** | Upgrade/retire service, disable mod_copy, migrate to SFTP. |
| F-03 | Default/Weak Credentials | **High** | Rotate credentials, enforce MFA, disable root SSH. |
| F-04 | Reflected XSS | **Medium** | Implement output encoding, CSP, and secure cookie controls. |

*See the full report for detailed evidence, CVSS scores, and specific remediation steps.*

## 🤝 Team & Roles
**Group 4 - Penetration Testing Specialists**
- **Assessment Lead:** Junior Penetration Tester
- **Team Members:** [Insert Names or "Redacted for Privacy"]
- **Client Point of Contact:** Security Team Lead (Simulated)

## 📜 License & Ethics
This project is licensed under the MIT License for educational purposes.
- **Ethical Commitment:** All testing was authorized, controlled, and conducted within an isolated laboratory environment.
- **Compliance:** Adheres to the **EC-Council Code of Ethics** and academic integrity policies.
- **Data:** No real-world client data was used or exposed.

---
*Prepared by Group 4 for Capstone Project 3. Date: 11 September 2026.*
*Status: Complete. Confidential.*
