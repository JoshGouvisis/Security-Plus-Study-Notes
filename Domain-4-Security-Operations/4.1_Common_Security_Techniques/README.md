## 4.1 Security Techniques
 
### Secure Baselines
 
- Establish: define expected security configuration using manufacturer guidelines and CIS Benchmarks.
- Deploy: centralized console, Active Directory Group Policy, MDM, or automation tools.
- Maintain: test updates before deployment, measure against baseline continuously to detect configuration drift.
### Hardening Targets
 
| Target | Hardening Approach |
|---|---|
| Mobile Devices | Updates critical. MDM controls app policies, data access, camera, screen locks, and PINs. Segmentation protects data. |
| Workstations | Automate monthly patches. Connect to Group Policy or MDM. Remove unnecessary software. Monitor OS, apps, and firmware continuously. |
| Switches/Routers | Purpose-built embedded OS. Configure authentication. Disable unused ports. Check manufacturer for firmware updates. |
| Cloud Infrastructure | Least privilege on all accounts. Configure EDR. Cloud-to-cloud (C2C) backups. Audit IAM roles regularly. |
| Servers | OS patches, service packs, security patches. Enforce password complexity. Limit network access. Antivirus monitoring. |
| ICS/SCADA | Extensive segmentation. No outside access to control network. Manage power, refining, and industrial facilities. |
| Embedded Systems | Segment and firewall. Apply security patches where available. Not easy to upgrade. |
| RTOS | Isolate the system. Run minimum services. Host-based firewall. Protect all connections. |
| IoT Devices | Weak defaults from manufacturers. Deploy updates quickly. Place on a dedicated VLAN isolated from production systems. |
 
### Mobile Deployment Models
 
| Model | Description |
|---|---|
| BYOD | Bring Your Own Device. Employee owns the device. Must meet company security requirements. Difficult to fully secure. MDM enforces policy. |
| COPE | Corporate Owned, Personally Enabled. Company purchases the device. Used as corporate and personal. Organization retains full control. |
| CYOD | Choose Your Own Device. Employee selects from an approved list. Company owns and manages the device. |
 
### Connection Methods and Security Concerns
 
| Method | Security Considerations |
|---|---|
| Cellular | Traffic monitoring, location tracking, worldwide roaming exposure. |
| Wi-Fi | Data capture, on-path attacks, denial of service via frequency interference. Secure with WPA3. |
| Bluetooth | Bluetooth sniffing, BlueJacking, BlueSnarfing. Short-range personal area network. Do not pair with unknown devices. |
 
### Wireless Security
 
| Protocol / Feature | Description |
|---|---|
| WPA2 PSK | Single pre-shared key for all users. Handshake can be captured and brute-forced offline using GPU or cloud cracking. Cracking the PSK exposes all users. |
| WPA3 Personal (SAE) | Simultaneous Authentication of Equals. Forward secrecy. Each session derives a unique key even when all users share the same passphrase. Defeats offline brute force. |
| WPA3 Enterprise | 802.1X authentication. Each user authenticates individually via RADIUS. Strongest wireless security. Required in enterprise environments. |
| GCMP | Galois/Counter Mode Protocol. Used by WPA3. AES for data confidentiality plus GMAC for message integrity. Stronger than WPA2's CCMP/TKIP. |
| Open System | No authentication. No encryption. Anyone can connect. Never use in a corporate environment. |
 
```
WPA2 PSK weakness:
1. Attacker captures the four-way handshake during authentication
2. Brute-forces the PSK offline using GPU/cloud resources
3. With the PSK, every user's traffic can be decrypted
 
WPA3 SAE solution:
1. Each authentication session derives a unique key (forward secrecy)
2. Capturing a session does not expose past or future sessions
3. Offline brute force of captured handshakes is not possible
```
 
- RADIUS: centralized AAA protocol. Authenticates users for routers, switches, firewalls, and wireless. Available on most server operating systems.
- 802.1X: port-based Network Access Control. No network access until the device authenticates. Works with EAP and a RADIUS/LDAP/TACACS+ backend.
### Application Security
 
| Technique | Description |
|---|---|
| Input Validation | Validate all input against expected format, length, and type. Normalize input to prevent injection. Fuzzers identify gaps automated checks miss. |
| Secure Cookies | Set Secure attribute (HTTPS only) and HttpOnly attribute (prevents JavaScript access). Never store sensitive data directly in a cookie. |
| SAST | Static Application Security Testing. Analyzes source code without executing it. Finds buffer overflows, SQL injection patterns, hardcoded credentials. Has false positives. Must verify each finding. |
| DAST | Dynamic Application Security Testing. Tests the running application. Sends input and observes behavior. Finds runtime vulnerabilities SAST misses: auth flaws, session management issues, insecure cryptographic implementations. |
| Code Signing | Developer digitally signs the application. A trusted CA signs the developer's public key. Users can verify the app has not been tampered with since it was signed. |
| Sandboxing | Isolates an application from unrelated resources. VMs, mobile devices, browser iframes, Windows UAC. Prevents one compromised app from accessing others. |
| Package Monitoring | Confirms software packages come from trusted sources with no added malware. Hash verification before installation. |
 
### SAST vs. DAST
 
```
SAST (Static):
- Reviews source code without executing the application
- Best at: injection flaws, buffer overflows, hardcoded credentials
- Cannot find: runtime issues, authentication failures, session management problems
 
DAST (Dynamic):
- Tests the running application
- Best at: runtime issues, authentication flaws, session management, insecure cryptography
- Cannot find: issues in code that never executes during testing
 
Use both for complete coverage.
