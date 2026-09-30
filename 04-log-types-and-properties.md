# Log Types and Log Properties

Logs are records of events or activities on a system, network, or application. They are the raw material of every SOC investigation.

## Why Logs Matter

- Detect attacks such as brute force, malware, and privilege escalation
- Monitor user behavior
- Support audits and policy enforcement
- Troubleshoot issues
- Trigger alerts in a SIEM

## Main Log Types in a SOC

| # | Log Type | What It Records | Example |
|---|----------|-----------------|---------|
| 1 | System Logs | OS-level events | Boot, shutdown, hardware errors |
| 2 | Security Logs | Authentication, access control, security events | Login success or failure, file access, sudo use |
| 3 | Application Logs | Events from apps and services | Web server errors, database query failures |
| 4 | Windows Event Logs | System, Security, and Application logs on Windows | Viewed in Event Viewer |
| 5 | Authentication Logs | Logins, logouts, password changes, failed attempts | `/var/log/auth.log` on Linux |
| 6 | Firewall Logs | Allowed and blocked traffic, rules applied | Denied traffic on a port |
| 7 | IDS/IPS Logs | Intrusion detection and prevention alerts | Port scan detected |
| 8 | Web Server Logs | HTTP requests, responses, status codes | GET /admin returning 404 |
| 9 | DNS Logs | Domain lookups and failures | Query to a malicious domain |
| 10 | Proxy Logs | User web traffic and URLs visited | A user opening a website from an internal IP |
| 11 | Mail Logs | Email activity, spam, phishing | SMTP relay, delivery failure |
| 12 | Endpoint Security Logs | Antivirus and EDR events | Malware detected, file quarantined, device isolated |

### Endpoint Security Logs

These come from endpoint protection tools:

- Antivirus (Windows Defender, Symantec)
- EDR (CrowdStrike, SentinelOne, Microsoft Defender for Endpoint)
- Threat detection agents

## Log Properties

Log properties are the key fields inside a log entry. They tell you what happened, when, where, and how.

| Property | Description | Example |
|----------|-------------|---------|
| Timestamp | Date and time of the event | 2025-06-18 14:03:12 |
| Event ID | Identifier for the type of event | 4625 (failed logon in Windows) |
| Event Type / Severity | Nature or criticality of the event | Critical, Warning, Info |
| Source / Hostname | Device or application that generated the log | WIN10-LAB01, webserver01 |
| Username / User ID | User involved in the event | Administrator |
| Process Name / ID | Process involved | powershell.exe |
| IP Address | Source or destination address | 192.168.1.100 |
| Port Number | Port used in the communication | 22 (SSH), 443 (HTTPS) |
| Protocol | Network protocol used | TCP, UDP, HTTP, DNS |
| Action / Result | What happened | Login failed, access granted, file quarantined |
| Command / Path | Specific command or file path | C:\Windows\System32\cmd.exe |
| Log Source Type | Kind of device that produced the log | Firewall, Linux Syslog, EDR |

## Tools That Use Log Properties

- SIEMs: Splunk, QRadar, Wazuh
- EDR platforms: CrowdStrike, Defender
- Log parsers and collectors: Logstash, Graylog
