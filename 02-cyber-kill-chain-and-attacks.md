# Cyber Attacks and the Cyber Kill Chain

## What Is a Cyber Attack?

Any attempt to damage, steal, destroy, or gain unauthorized access to data, systems, or networks using digital methods.

**Why attacks happen:** stealing sensitive data, disrupting services, spreading malware, financial gain, espionage, and hacktivism.

## Common Types of Cyber Attacks

| Type | What It Means |
|------|---------------|
| Phishing | Fake emails or websites trick users into giving data |
| Malware | Harmful software such as ransomware or trojans |
| DDoS | Flooding a website with traffic until it crashes |
| Brute Force | Guessing passwords until one works |
| SQL Injection | Injecting malicious code into databases |
| MITM (Man-in-the-Middle) | Attacker intercepts data between two parties |
| Zero-Day | Exploiting a vulnerability before it is patched |

## The Cyber Kill Chain

A framework created by Lockheed Martin that describes the steps an attacker follows, from reconnaissance to full control. Security teams use it to detect and stop attacks early.

| Stage | Name | What Happens | Example |
|-------|------|--------------|---------|
| 1 | Reconnaissance | Attacker gathers info on the target | Scanning IPs, finding open ports |
| 2 | Weaponization | Create a malicious payload | Building a backdoored PDF |
| 3 | Delivery | Send the payload to the target | Phishing email |
| 4 | Exploitation | Exploit a vulnerability | Word macro or software flaw |
| 5 | Installation | Install malware on the system | Dropping a trojan or backdoor |
| 6 | Command & Control | Victim connects back to attacker server | C2 communication |
| 7 | Actions on Objectives | Steal, destroy, or control | Data exfiltration, encryption, spying |

**Why it is useful:** it helps detect attacks early, shows where defenses are weak, and lets you break the chain at any stage.

**Example:** an attacker scans a company's public IPs, sends HR a fake job-offer PDF, HR opens it and a macro exploit runs, malware installs and connects to the attacker's server, and confidential files get stolen. If the SOC catches it at email filtering (delivery) or macro execution (exploitation), the chain is broken.

**Use in a SOC:** map alerts to kill chain stages for faster response.

## Top Attack Types in a SOC

| # | Attack Type | Description | Example in a SOC |
|---|-------------|-------------|------------------|
| 1 | Phishing | Fake emails trick users into clicking links or entering data | SIEM detects a user clicked a suspicious URL |
| 2 | Brute Force | Repeated attempts to guess credentials | Many failed logins from one IP |
| 3 | Malware | Malicious software infects a system | EDR alerts on malicious file execution |
| 4 | Ransomware | Files are encrypted and money is demanded | Files renamed and a ransom note appears |
| 5 | Insider Threat | Misuse from inside the organization | Unusual access at odd times or large downloads |
| 6 | DDoS | Flooding servers with traffic | External IPs sending excessive traffic |
| 7 | SQL Injection | Malicious SQL in input fields | WAF logs show strange SQL queries |
| 8 | MITM | Attacker intercepts traffic | Network traffic shows SSL stripping |
| 9 | Privilege Escalation | Attacker gains a higher access level | A regular user suddenly has admin rights |
| 10 | Zero-Day Exploit | Exploiting an unpatched vulnerability | Unusual behavior matching an exploit pattern |
