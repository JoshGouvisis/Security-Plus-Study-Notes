## 4.4 Security Monitoring
 
### Monitoring Activities
 
- Log aggregation: SIEM collects logs from all sources into one centralized platform. Enables correlation across diverse systems.
- Alerting: real-time notification via SMS, email, or security console. Alerts must be actionable and accurate.
- Alert tuning: adjust thresholds and signatures to minimize false positives and false negatives.
- Quarantine: isolate a system or user to prevent a security issue from spreading while investigation occurs.
- Scanning: continuous checks across systems to gather raw security data.
- Archiving: store logs over time for compliance mandates and long-term forensic investigations. Average breach detection time is approximately nine months.
### Security Data Sources
 
| Source | What It Contains and Why It Matters |
|---|---|
| Firewall Logs | Source/destination IP, port numbers, allow/deny disposition. NGFW adds application used, URL category, and anomalies. Critical for traffic analysis and incident reconstruction. |
| Application Logs | Application-specific events. Windows: Event Viewer. Linux/macOS: /var/log. Parse in SIEM to filter noise and correlate with other sources. |
| Endpoint Logs | Logon events, policy changes, system events, process creation, account management. Combined with IPS events to correlate endpoint activity with network detections in SIEM. |
| OS Security Logs | Authentication details, brute-force attempts, service changes, file modifications. Identifies problems before they escalate. |
| IPS/IDS Logs | Predefined vulnerability matches and anomaly detections. Key data points: timestamp, attack type, source/destination IP and port. |
| Network Logs | Events from switches, routers, access points, and VPN concentrators. Captures routing changes, authentication failures, and network security events. |
| Metadata | Data that describes other data. Email: header details, sending servers. Mobile: device type, GPS location. Web: OS, browser, IP address. Files: author, creation date, location. |
| DNS Sinkhole | Redirects DNS queries for known malicious domains to a controlled IP. When an infected device attempts to reach a command-and-control server by domain name, the sinkhole logs the attempt and reveals which internal systems are compromised. |
 
### Security Tools
 
- SCAP: Security Content Automation Protocol. NIST-managed framework allowing security tools to identify and share vulnerability information in a standardized, interoperable format.
- SIEM: central hub for log collection, aggregation, correlation, and forensic analysis.
- Antivirus/anti-malware: Trojans, worms, macro viruses, spyware, ransomware, and fileless malware.
- DLP: monitors data in use (endpoint), in motion (network), and at rest (server/cloud). Blocks SSNs, credit card numbers, and PHI from unauthorized movement.
- SNMP traps: devices send unsolicited alerts to the management system when predefined thresholds are exceeded.
- NetFlow: collects traffic flow statistics. Probe watches communication, sends summary to collector. Baseline and anomaly detection.
- Vulnerability scanner: identifies open ports, known CVEs, and misconfigurations. Does not exploit.
- EDR: endpoint detection. Signature, behavioral, and ML-based. Root cause analysis. Isolate, quarantine, rollback.
- XDR: extends EDR to correlate endpoint, network, and cloud data. Reduces missed detections and investigation time.
- UBA: user behavior analytics. Detects anomalous user and host behavior using rules, pattern matching, and statistical analysis.
