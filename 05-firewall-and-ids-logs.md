# Firewall Logs and IDS/IPS Logs

## Firewall Logs

Firewall logs record network traffic events: what was allowed, blocked, or only monitored. They show what traffic is coming in and out, what was denied, and which security policies were triggered.

### Common Firewall Log Fields

| Field | Description | Example |
|-------|-------------|---------|
| Timestamp | Date and time of the event | 2025-06-18 10:43:12 |
| Source IP | Device that started the connection | 192.168.1.10 |
| Destination IP | Target system or server | 10.0.0.5 |
| Source Port | Port used on the sender side | 52345 |
| Destination Port | Port the target service listens on | 443, 80, 22 |
| Protocol | Communication protocol | TCP, UDP, ICMP |
| Action / Status | What the firewall did | ALLOW, DENY, DROP |
| Rule ID / Policy | Which rule was triggered | Block_SSH, Allow_HTTP |
| Interface | Network interface of the event | eth0, WAN, LAN |

### Why Firewall Logs Matter in a SOC

| Purpose | Explanation |
|---------|-------------|
| Detect unauthorized access | Blocked or suspicious traffic, for example to port 22 |
| Identify malware communication | Outbound connections to malicious IPs |
| Investigate intrusion attempts | Scanning, brute-force, or DoS activity |
| Validate security policies | See which rules are triggered or bypassed |
| Build network baselines | Understand normal vs abnormal traffic |

### Log Formats Depend on the Vendor

| Vendor | Notes |
|--------|-------|
| Cisco ASA | Messages start with a code such as %ASA-6-106015 |
| pfSense | Syslog-style filterlog lines with source, destination, and action |
| Windows | Appears in Event Viewer under Windows Firewall With Advanced Security |
| FortiGate | Key-value fields such as srcip, dstip, action, service |

### Common Firewall Actions

| Action | Meaning |
|--------|---------|
| ALLOW / ACCEPT | The firewall permitted the traffic |
| DENY / BLOCK | The firewall actively blocked the traffic |
| DROP | Traffic silently discarded without a response |
| RESET | Connection forcefully terminated |
| LOG ONLY | Recorded but neither blocked nor allowed |

### Detection Use Cases

- **Port scanning:** many different destination ports from the same source IP in a short time window.
- **Brute-force logins:** repeated denied or failed connections to SSH or RDP from one source.
- **Data exfiltration:** unusually large outbound transfers to an unfamiliar external IP.
- **Command and Control (C2):** regular, repeated outbound connections to a suspicious external host.

### Real-World Analysis Tips

| What to Look For | What It Might Indicate |
|------------------|------------------------|
| Repeated DENY on port 3389 | Remote Desktop attack attempt |
| SYN packets with no ACK | TCP SYN scan (half-open) |
| Inbound from random ports | Malware communication or spoofed connections |
| Unexpected protocols such as Telnet | Insecure services being probed |

## IDS and IPS Logs

| Type | Full Name | Function |
|------|-----------|----------|
| IDS | Intrusion Detection System | Detects and alerts on suspicious or malicious traffic |
| IPS | Intrusion Prevention System | Detects and blocks malicious traffic in real time |

IDS/IPS logs are alerts generated when the system observes scanning, exploit attempts, malware traffic, or anything matching a known threat signature.

### Key Fields in IDS/IPS Logs

| Property | Description | Example |
|----------|-------------|---------|
| Timestamp | When the alert occurred | 2025-06-18 14:55:02 |
| Signature / Alert Name | The rule that matched | ET SCAN NMAP -sS |
| Source IP | Attacker or sender | 185.10.20.5 |
| Destination IP | Targeted machine | 192.168.1.15 |
| Protocol | Network protocol | TCP, DNS, HTTP |
| Source Port | Port on the attacker side | 50421 |
| Destination Port | Port targeted on your network | 22, 443, 80 |
| Action (IPS only) | What the IPS did | ALERT, BLOCK, DROP |
| Classification | General attack category | Attempted-Information-Leak |
| Severity / Priority | Risk level | High, Medium, Low |
