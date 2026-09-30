# Password Attacks

A password attack is any attempt to steal, guess, or crack a user's password to gain unauthorized access to a system, account, or network.

## Common Types of Password Attacks

| # | Attack Type | Description | Example |
|---|-------------|-------------|---------|
| 1 | Brute Force | Tries every possible combination until one works | Hydra guessing a password |
| 2 | Dictionary Attack | Uses a list of likely passwords | A wordlist such as rockyou.txt |
| 3 | Credential Stuffing | Reuses username/password pairs leaked from other breaches | Leaked Gmail logins reused elsewhere |
| 4 | Password Spraying | Tries one common password across many accounts to avoid lockouts | Trying one weak password on all usernames |
| 5 | Phishing | Tricks the user into typing a password on a fake login page | Fake email asking you to log in |
| 6 | Keylogging | Malware records keystrokes | Spyware logging typing |
| 7 | Shoulder Surfing | Attacker watches someone type | Looking at a screen in a cafe |
| 8 | Rainbow Table | Uses precomputed hashes to reverse password hashes | Cracking MD5 hashes |

## Tools Commonly Used

| Tool | Purpose |
|------|---------|
| Hydra | Brute force and dictionary attacks |
| John the Ripper | Cracking hashed passwords |
| Hashcat | GPU-based hash cracking |
| Burp Suite | Brute-forcing login forms in web apps |
| Mimikatz | Extracting credentials from Windows memory |

## How Operating Systems Store Passwords

### Windows

- Local passwords are stored in the SAM (Security Account Manager) file, in the Windows config folder.
- They are stored as NTLM hashes, not plain text.
- The SAM file is locked while Windows is running, so attackers use offline access (booting another OS) or LSASS memory dumping.
- Tools: Mimikatz, samdump2, pwdump.

### Linux

- Usernames and user info are in `/etc/passwd`.
- Password hashes are in `/etc/shadow`, which normal users cannot read.
- Hashes commonly use SHA-512 or bcrypt.
- Tools to audit them: John the Ripper, Hashcat.

### macOS

- Passwords are stored in the Keychain and the system directory services.
- They are encrypted and protected by the user's login password.

### Summary

| OS | Location | Format | Example Tools |
|----|----------|--------|---------------|
| Windows | SAM, LSASS | NTLM hash | Mimikatz, samdump2 |
| Linux | /etc/shadow | SHA hashes | John, Hashcat |
| macOS | Keychain, Directory Services | Encrypted | security tool |
| Browsers | Encrypted SQLite user data | Encrypted | LaZagne |

## Defensive Takeaways (SOC View)

- Many failed logins from one IP in the logs suggests brute force.
- One failed login across many accounts suggests password spraying.
- Alert on access to LSASS memory and on Mimikatz-like behavior in EDR.
- Enforce account lockout, MFA, and strong password policies.
