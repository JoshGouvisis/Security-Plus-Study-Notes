## 2.4 Indicators of Malicious Activity
 
### Malware Types
 
| Malware Type | Behavior and Key Facts |
|---|---|
| Ransomware | Encrypts files and demands payment for the decryption key. Mitigate with maintained offline backups. |
| Virus | Requires user execution to spread. Types: program, boot sector, script, macro. Fileless variant operates entirely in memory, never written to disk, evading signature-based antivirus detection. |
| Worm | Self-replicates with no user action. Spreads across networks rapidly. Mitigated by firewalls and IDS/IPS. |
| Trojan | Masquerades as legitimate software. User voluntarily executes it. Does not self-replicate. Delivers payload or backdoor. |
| Spyware | Monitors user activity, browser habits, and keystrokes. Sends captured data to attacker. Can include keylogger functionality. |
| Bloatware | Pre-installed by manufacturer. Consumes resources and may contain exploitable vulnerabilities. |
| Keylogger | Captures keystrokes, clipboard content, screen activity, and chat. Sends data to attacker. Works around encryption at the input layer. |
| Logic Bomb | Dormant until triggered by a time, date, or user event. Difficult to detect before detonation. Prevented by process auditing and code review. |
| Rootkit | Modifies core OS kernel files. Invisible to task manager and most antivirus tools. Remove with specialized rootkit scanners or secure boot with UEFI. |
| Botnet | A network of compromised machines (bots) controlled by an attacker (bot herder) through a command-and-control server. Used to conduct DDoS attacks, send spam, and distribute malware at scale. Individual bots are often compromised without the owner's knowledge. |
 
### Trojan vs. Virus vs. Worm
 
```
Trojan:  social engineering required > user voluntarily executes > payload delivered > does not self-replicate
Virus:   user execution required > replicates through file system or network > may cause damage
Worm:    no user action required > self-replicates > spreads autonomously across networks
```
 
Fileless virus: operates entirely in memory, never written to disk. Evades signature-based antivirus because there is no file to scan.
 
### Physical Attacks
 
| Attack | Description |
|---|---|
| Brute Force | Physical force to breach doors, windows, or enclosures to gain access to hardware. |
| RFID Cloning | Duplicates access badges or key fobs using a reader purchasable online. Cloning takes seconds: read one card, write to another. |
| Environmental | Attacks targeting power (UPS, generators), HVAC systems, or fire suppression to force a shutdown or cause physical damage. |
 
### Network and Application Attacks
 
| Attack Type | Description |
|---|---|
| DoS | Forces a service to fail by exploiting a vulnerability or exhausting resources. Can be unintentional (Layer 2 loop, bandwidth saturation). |
| DDoS | Coordinated botnet attack using thousands or millions of compromised machines to overwhelm a target. |
| DDoS Amplification/Reflection | Small query with spoofed source IP triggers a large response from DNS/NTP/ICMP directed at the victim. Amplification factor = response size divided by query size. |
| DNS Poisoning | Modifies DNS server records or client host files to redirect legitimate traffic to attacker-controlled destinations. |
| Domain Hijacking | Gains control of a domain registration account via brute force, social engineering, or email compromise. |
| URL Hijacking / Typosquatting | Registers misspelled domain names to intercept mistyped traffic. Redirects to phishing, competitor, or malware sites. |
| Wireless Deauthentication | Sends 802.11 deauthentication frames to disconnect clients from an access point. A DoS attack against wireless users. |
| RF Jamming | Transmits interfering signals to prevent wireless communication. Must be physically close. Detectable by fox-hunting the signal source. |
| On-Path (MitM) | Active real-time interception between two communicating parties. ARP poisoning is the common local network implementation. |
| Replay | Captures valid credentials or session tokens and retransmits them later. Does not require active real-time positioning. Not the same as on-path. |
| Pass-the-Hash | Captured NTLM hash used directly to authenticate without cracking the original password. A specific form of credential replay. |
| Credential Stuffing | Uses large databases of previously breached username/password pairs to attempt authentication across multiple services. Exploits password reuse. Distinct from brute force, which generates guesses rather than using known pairs. |
| Privilege Escalation | Vertical: user gains admin or root-level rights by exploiting a vulnerability. Horizontal: user accesses another user's resources at the same privilege level. |
| Directory Traversal | Reads files outside the web root by manipulating file path input (e.g., ../../etc/passwd). |
| CSRF | Tricks an authenticated user's browser into submitting an unauthorized request to a trusted site. Also called XSRF or sea-surf. |
 
### DNS Amplification Flow
 
```
1. Attacker sends small DNS query with victim's IP spoofed as the source
2. DNS server returns a large response to the victim, not the attacker
3. Amplification factor = size of response divided by size of query
4. Attacker repeats across many DNS servers > victim is overwhelmed by traffic it never requested
```
 
### Replay vs. On-Path vs. Credential Stuffing
 
```
On-path (MitM):       active real-time positioning between parties, intercepting live traffic
Replay:               captures valid data (session ID, NTLM hash), retransmits it later, no real-time positioning needed
Pass-the-Hash:        specific replay variant, NTLM hash used directly to authenticate without cracking
Credential stuffing:  uses previously breached username/password pairs, not captured tokens, exploits reuse across services
```
 
### Cryptographic Attacks
 
| Attack | Description |
|---|---|
| Birthday Attack | Brute-force hash collision: generate many inputs seeking two that produce the same hash output. Mitigated by large hash output sizes. |
| Collision | Two different inputs produce the same hash output. MD5 has known collisions and must not be used for security purposes. |
| Downgrade Attack | Forces a system to negotiate a weaker encryption algorithm. SSL stripping: attacker on-path removes HTTPS and serves HTTP to the client while maintaining encrypted connection to the server. |
 
### Password Attacks
 
| Attack | Description |
|---|---|
| Spraying | Most common passwords tried across many accounts. Stays under lockout thresholds by limiting attempts per account. No alerts triggered. |
| Brute Force (online) | Continuously attempts logins against a live authentication system. Detectable via lockout and alerting. |
| Brute Force (offline) | Attacker obtains the hash list and computes hashes locally. No lockout mechanism. Speed limited by hash algorithm strength and hardware. |
| Credential Stuffing | Automated use of previously breached username/password pairs across multiple services. Exploits password reuse. Distinct from brute force, which generates guesses. |
 
### Indicators of Compromise (IoC)
 
| Indicator | What It Signals |
|---|---|
| Account Lockout | Credentials failing, lockout exceeded, or admin-disabled. Attacker may trigger lockout to force a support call and social engineer the reset. |
| Concurrent Session Usage | Same account authenticated from multiple locations or devices simultaneously. |
| Blocked Content | Security tools blocking update connections or antimalware sites indicates an active attacker suppressing defenses. |
| Impossible Travel | Authentication events from geographically distant locations within a physically impossible timeframe. |
| Resource Consumption | Unusual file transfers, unexpected outbound firewall traffic, or CPU/memory/bandwidth spikes. |
| Resource Inaccessibility | Server down, files encrypted, or services returning errors. May indicate ransomware or DoS. |
| Out-of-Cycle Logging | Patches applying outside normal windows, firewall timestamps at unexpected hours, or scheduled tasks firing at wrong times. |
| Missing Logs | Attacker cleared logs to conceal activity. Logs must be stored off-system and monitored continuously. |
| Published/Documented | Stolen data posted publicly by the attacker as proof of access or as leverage. |
