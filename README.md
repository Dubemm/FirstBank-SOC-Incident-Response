# FirstBank Nigeria — SOC Incident Response Lab

A hands-on SOC (Security Operations Center) investigation simulating a real-world bank breach — from initial compromise to fraudulent wire transfers — using **Splunk** for log analysis and **Python** for automated reporting.

## Scenario
FirstBank Nigeria's fraud-detection system flagged a cluster of unusual overnight wire transfers. As the investigating analyst, the goal was to determine how the attacker got in, how they moved through the environment, and what the full financial impact was.

## Tech Stack
- **Splunk Enterprise** (via Docker) — log ingestion and investigation
- **Python 3** — automated analysis, risk scoring, and report generation
- **Docker Compose** — environment orchestration

## Attack Chain Uncovered
1. **Initial Access** — SQL injection attack (via `sqlmap`) against the login page, bypassing authentication
2. **Privilege Escalation** — hijacking of an internal service account (`svc_report`)
3. **Lateral Movement** — pivot from the public web server to the core transaction server via a network logon (Windows EventCode 4624, LogonType=3)
4. **Impact** — execution of a fraud script (`bulk_transfer.py`) issuing 5 unauthorized wire transfers totaling NGN 12,491,436.99

## What's in This Repo
- `student/analysis.py` — Python script that parses Nessus vulnerability data and Splunk exports, calculates host risk scores, and auto-generates an incident report
- `student/incident_report.txt` — auto-generated technical findings report
- `student/project_screenshot/` — Splunk investigation evidence (SPL queries + results)
- `student/Report.pdf` — full written incident response report for a C-suite audience, covering executive summary, customer impact, Nigerian regulatory obligations (CBN, BOFIA, NDPA), and remediation recommendations

## Key Skills Demonstrated
- SPL (Splunk Search Processing Language) query writing and log correlation across multiple sources (web, Windows auth, transaction logs)
- Python scripting for security data analysis
- Incident timeline reconstruction
- Risk scoring methodology (CVSS-based)
- Regulatory/compliance reporting (Nigerian financial sector)

> **Note:** All data in this project is synthetic, generated for cybersecurity training purposes only. No real individuals, accounts, or institutions are represented.
