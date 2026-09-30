# SOC Analyst Overview

A SOC (Security Operations Center) analyst monitors and defends an organization's networks and systems from cyber threats in real time.

## What the Role Includes

1. **Monitoring & Detection**: watch systems and logs 24/7 using a SIEM (Splunk, QRadar) and spot suspicious activity such as failed logins or malware behavior.
2. **Analysis & Investigation**: analyze alerts to decide whether each one is a real threat or a false positive, and understand how the attack works (phishing, malware, brute-force).
3. **Incident Response**: block IPs, isolate devices, reset passwords, work with IT, network and forensics teams, and document every step.
4. **Threat Intelligence**: use sources like VirusTotal and AbuseIPDB, follow new attack types, and feed what you learn into SIEM rules.
5. **Tuning & Optimization**: reduce false positives by fine-tuning SIEM rules.
6. **Reporting**: write daily, weekly and incident reports and share findings with senior analysts or managers.

## SOC Analyst Levels

| Level | Role |
|-------|------|
| L1 (Tier 1) | Monitors alerts, basic triage and escalation |
| L2 (Tier 2) | Deep investigations, threat hunting |
| L3 (Tier 3) | Advanced analysis, malware reverse engineering, improves detection rules |
| SOC Manager | Leads the team, manages reporting and strategy |

## Risk Management

Finding risks, measuring how bad and how likely they are, and deciding how to reduce or avoid them.

| Step | Description |
|------|-------------|
| 1. Identify | Find assets and threats (servers, malware) |
| 2. Analyze | Evaluate impact and likelihood |
| 3. Prioritize | Focus on high-risk items first |
| 4. Mitigate | Apply controls (firewalls, training, backups) |
| 5. Monitor | Keep checking for new risks or failed controls |

**Example:** a hacker steals customer data. Impact: high. Likelihood: medium. Response: encryption, strong passwords, regular audits.

## Incident Response Lifecycle

| Phase | Name | Description |
|-------|------|-------------|
| 1 | Preparation | Build tools, training, policies and communication plans |
| 2 | Identification | Detect and confirm whether an incident happened |
| 3 | Containment | Isolate affected systems to stop the spread |
| 4 | Eradication | Remove the threat and patch vulnerabilities |
| 5 | Recovery | Restore systems and monitor for weakness |
| 6 | Lessons Learned | Review what went right or wrong and improve |

**Example (brute-force on a web server):** the SIEM alerts on repeated failed logins, the analyst confirms the attack, isolates the server and blocks the IP, removes the malware and patches the vulnerable plugin, rebuilds the server, then writes a report that leads to an automated patching policy.
