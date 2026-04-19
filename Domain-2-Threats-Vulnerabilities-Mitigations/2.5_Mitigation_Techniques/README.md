## 2.5 Mitigation Techniques
 
### Core Mitigation Controls
 
| Technique | Description |
|---|---|
| Segmentation | Physical, logical, or virtual separation of network zones. Prevents lateral movement. Required for PCI compliance. |
| Access Control (ACL) | Allow or deny traffic by source IP, destination IP, port, time of day, or application. Applied at routers, firewalls, and OS level. |
| Application Allow List | Only pre-approved applications may execute. Most restrictive. Defeats unauthorized code execution entirely. |
| Application Deny List | Blocks known-bad applications. Used by antivirus and anti-malware. Less restrictive than allow list. |
| Isolation / Quarantine | Compromised or non-compliant systems moved to a private VLAN with limited access pending remediation. |
| Patching | Monthly scheduled patches plus emergency out-of-band patches for critical vulnerabilities. Test before broad deployment. Includes third-party apps and drivers. |
| Encryption | File-level (EFS), full-disk (BitLocker, FileVault), application data, and network communication (VPN). |
| Monitoring (SIEM) | Aggregates logs from IPS, firewalls, authentication systems, web servers, and databases. Enables alerting, correlation, and archiving. |
| Least Privilege | Users receive only the minimum permissions required for their role. No standard user accounts run with admin rights. |
| Configuration Enforcement | Posture assessment checks OS patch level, EDR version, firewall status, and certificate validity before granting network access. Non-compliant systems are quarantined. |
| Decommissioning | Formal policy for retiring devices. Sanitize or destroy storage media. Prevents data recovery from discarded hardware. |
 
### Hardening Techniques
 
| Technique | Description |
|---|---|
| Endpoint Protection (EDR) | Detects threats via signatures, behavioral analysis, and ML. Root cause analysis, isolation, quarantine, and rollback. |
| Host-based Firewall | Software firewall on every endpoint. Controls inbound/outbound traffic by process. Blocks unknown processes. Centrally managed. |
| HIPS | Host-based Intrusion Prevention System. Detects and blocks known attacks, validates service requests, monitors registry and file writes. |
| Port and Protocol Disabling | Close every port not explicitly required. Scan with NMAP to verify. Manage remaining ports with NGFW. |
| Default Password Changes | Change factory credentials on every network device, application, and management interface before deployment. |
| Remove Unnecessary Software | Every installed application is a potential vulnerability. Remove all unused software to reduce attack surface. |
| OS and Application Updates | Apply patches, service packs, and security fixes. Test before broad deployment. Maintain backups. |
| Account Controls | Enforce password policy, disable direct root login, limit account privileges, audit privileged accounts regularly. |
 
### Allow List Implementation Options
 
- Application hash: allow only apps matching a specific cryptographic hash
- Certificate: allow only apps with a valid digital signature from an approved publisher
- Path: allow only apps executing from approved directories
- Network zone: allow only apps executing from within an approved network zone
---
 
## Quick Reference
 
| Concept | Key Facts |
|---|---|
| Threat actor types | Nation-state (APT), Unskilled, Hacktivist, Insider, Organized crime, Shadow IT |
| Largest attack vector | Message-based: email, SMS, IM |
| Phishing vs. spear phishing | Phishing: broad, untargeted. Spear phishing: specific person or org using personalized details. |
| Whaling | Spear phishing targeting senior executives. Their authority and financial access is the exploit. |
| Shoulder surfing | Observing credential entry in person or via camera |
| Tailgating vs. piggybacking | Tailgating: authorized person unaware. Piggybacking: authorized person knowingly allows entry. |
| Dumpster diving | Recovering sensitive data from discarded materials. Mitigate with shredding and clean desk policy. |
| Supply chain attack | Compromise happens upstream at vendor, MSP, or software update level |
| Buffer overflow | Overwrites adjacent memory to redirect code execution. Repeatable once crafted. |
| XSS reflected | Script in crafted URL, executes only for victim who clicks. Non-persistent. |
| XSS stored | Script written to server, executes for every visitor automatically. Persistent, wider blast radius. |
| Trojan delivery | Social engineering. User voluntarily executes. Does not self-replicate. |
| Fileless malware | Operates entirely in memory. Never written to disk. Evades signature-based antivirus. |
| Botnet | Network of compromised machines used for DDoS, spam, and malware distribution at scale. |
| DNS amplification | Small spoofed query triggers large DNS/NTP/ICMP response directed at victim |
| Replay vs. on-path | Replay retransmits captured credentials later. On-path is active real-time interception. |
| Credential stuffing | Previously breached username/password pairs tried across services. Exploits password reuse. |
| Pass-the-Hash | Captured NTLM hash used directly to authenticate without cracking |
| Privilege escalation | Vertical: user to admin. Horizontal: user to another user's resources. |
| Downgrade attack | Forces weaker encryption. SSL stripping is the common implementation. |
| Password spraying | Common passwords across many accounts, staying under lockout thresholds |
| Allow vs. deny list | Allow: only approved apps run. Deny: only known-bad apps are blocked. |
| Least privilege | Users receive only the minimum permissions required for their role |
| EDR | Detects, isolates, quarantines, and rolls back threats at the endpoint level |
