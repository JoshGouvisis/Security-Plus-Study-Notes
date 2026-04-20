## 4.9 Security Data Sources
 
### Log Types
 
| Source | What It Reveals |
|---|---|
| Firewall logs | Traffic flows, allowed/denied connections, port usage. NGFW adds application identity, URL category, and anomalies. |
| Application logs | Application-level events. Parse in SIEM to remove noise and correlate with other log sources. |
| Endpoint logs | Logon events, process creation, policy changes, account management. Rich source for detection of attacker activity. |
| OS security logs | Authentication, brute force, service changes, file modifications. Find problems before they escalate. |
| IPS/IDS logs | Known attack signatures and anomalous traffic patterns. Timestamp, attack type, source/destination IP and port. |
| Network logs | Routing updates, authentication failures, network security events from switches, routers, APs, and VPN concentrators. |
| Metadata | Data describing other data. Email headers, mobile GPS, web browser fingerprint, file author and creation date. |
| DNS sinkhole | Flags internal devices attempting to reach known malicious domains. Reveals compromised systems proactively. |
 
### Investigative Data Sources
 
- Vulnerability scans: missing controls, misconfigurations (open shares, guest access), and known real vulnerabilities.
- Automated reports: SIEM report generators create scheduled security summaries. Large data volumes require significant processing time.
- Dashboards: real-time status summaries on a single screen. Customizable in SIEM platforms. Not designed for long-term historical analysis.
- Packet captures: deep protocol analysis. Identifies unknown traffic, verifies filtering controls, and reveals application data. Tools: Wireshark, tcpdump.
---
 
## Quick Reference
 
| Concept | Key Facts |
|---|---|
| Secure baseline | Document expected config, deploy via GPO/MDM, maintain with drift detection. |
| BYOD vs. COPE | BYOD: employee owns. COPE: company owns, employee uses. CYOD: employee picks from approved list. |
| WPA2 PSK weakness | Handshake captured and brute-forced offline. Exposes all users if PSK is cracked. |
| WPA3 SAE | Forward secrecy. Each session unique key. Captured handshakes cannot be brute-forced retroactively. |
| WPA3 Enterprise | 802.1X with individual RADIUS authentication. Strongest wireless security. |
| SAST vs. DAST | SAST: source code review, no execution. DAST: running app, runtime issues. Both needed for full coverage. |
| CVSS range | Critical: 9.0-10.0. High: 7.0-8.9. Medium: 4.0-6.9. Low: 0.1-3.9. |
| CVE vs. CVSS | CVE: unique vulnerability identifier. CVSS: severity score for that CVE. |
| IR phases in order | Preparation, Detection, Analysis, Containment, Eradication, Recovery, Lessons Learned. |
| Containment before eradication | Stop the spread first, then remove the cause. |
| Order of volatility | CPU registers, RAM, swap/page file, local disk, remote storage, backups. Most volatile first. |
| RAM capture rule | Must be captured before powering down. Running malware and encryption keys lost permanently on shutdown. |
| Chain of custody | Every handler documented. Hashes verify integrity. Label, seal, store. |
| Legal hold | Preserve specific data for litigation. Initiated by legal counsel. ESI must not be altered. |
| DNS sinkhole | Redirects malicious domain queries to controlled IP. Identifies infected internal devices. |
| SAML | Enterprise web SSO. XML-based. Authentication and authorization. Not for mobile. |
| OAuth | Authorization framework ONLY. NOT an authentication protocol. |
| OIDC | Authentication layer on top of OAuth 2.0. SSO including mobile apps. |
| Attestation | Periodic review confirming user access rights are still appropriate. Compliance requirement. |
| Ephemeral credentials | Short-lived, session-specific. Expire automatically. Never reused. |
| PAM / JIT | Admin rights granted temporarily on request. Breached accounts never hold persistent elevated rights. |
| SPF | Authorized sending servers listed in DNS TXT record. |
| DKIM | Mail server signs messages. Receiving server validates digital signature. |
| DMARC | Policy for failed SPF/DKIM. Quarantine or reject. Reports to domain owner. Requires SPF and DKIM first. |
| FIM | Monitors OS and app files for unauthorized changes. Windows: SFC. Linux: Tripwire. |
| EDR vs. XDR | EDR: endpoint only. XDR: endpoint plus network and cloud data correlated together. |
| UBA | Detects anomalous user and host behavior via rules, pattern matching, and statistical analysis. |
| CVSS components | Attack vector, complexity, privileges required, user interaction, scope, CIA impact. |
 
