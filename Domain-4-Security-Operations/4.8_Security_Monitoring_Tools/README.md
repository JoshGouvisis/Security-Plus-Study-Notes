## 4.8 Incident Response
 
### Incident Response Lifecycle
 
| Phase | Description |
|---|---|
| 1. Preparation | Establish communication plans, gather forensic tools, document network diagrams and baselines, define policies. Done before any incident occurs. |
| 2. Detection | Identify that an incident has occurred. Sources: IDS/IPS alerts, AV notifications, log anomalies, user reports, threat intelligence feeds. |
| 3. Analysis | Determine scope, severity, and nature. Review logs, correlate events, confirm true positive, assess impact on business. |
| 4. Containment | Stop the spread. Isolate affected systems, block malicious traffic, quarantine endpoints. Must occur BEFORE eradication. |
| 5. Eradication | Remove the root cause. Delete malware, close exploited vulnerabilities, disable compromised accounts, rebuild affected systems. |
| 6. Recovery | Restore to normal operation. Restore from clean backups, tighten perimeter, verify systems are clean, monitor closely. |
| 7. Lessons Learned | Post-incident meeting with all stakeholders. Document what happened, how the plan performed, what to improve, and what indicators to watch for next time. |
 
```
Critical phase order trap:
Containment must come BEFORE Eradication.
Stop the spread first, then remove the cause.
Attempting eradication without containment risks spreading
the malware to additional systems during the removal process.
```
 
### Threat Hunting
 
- Proactive search for attackers who have evaded automated detection.
- Driven by intelligence data and hypotheses rather than waiting for alerts.
- Analyzes logs, network flows, and endpoint telemetry for subtle indicators of compromise.
- Finds attackers who have established persistence but have not yet triggered signatures.
### Digital Forensics
 
| Concept | Description |
|---|---|
| Legal Hold | Initiated by legal counsel. Requires preservation of specific data for potential litigation. Electronic Stored Information (ESI) must not be altered or deleted once notified. |
| Chain of Custody | Documents every person who has handled the evidence. Hashes verify integrity. Label, catalog, seal, and store all items. Tamper-evident packaging. |
| Acquisition | Obtain disk images, RAM dumps, firmware, OS files, and log data. Use write blockers on physical drives. Take VM snapshots. Preserve in order of volatility. |
| Preservation | Work from copies. Never analyze original evidence. Mobile devices: enable airplane mode before seizure to prevent remote wipe. Follow RFC 3227. |
| Reporting | Document findings for internal use or legal proceedings. Include summary, acquisition methodology, analysis findings, and professional conclusions. |
| E-Discovery | Collect, prepare, review, and produce electronic documents for legal proceedings. Works with digital forensics. May uncover deleted data requiring forensic recovery. |
 
### Order of Volatility
 
Evidence must be collected in order of volatility: most volatile first. Data that disappears on power-off must be captured before the system is shut down.
 
| Priority | Data Source | Notes |
|---|---|---|
| 1 | CPU registers and cache | Highest volatility. Lost immediately on power-off. Capture first if possible. |
| 2 | RAM (system memory) | Active processes, open network connections, encryption keys, running malware. Lost on shutdown. Must capture with live memory imaging tool before powering down. |
| 3 | Swap / Page file | Virtual memory on disk. Contains overflow from RAM. More persistent but still considered volatile. |
| 4 | Local disk storage | HDDs, SSDs, USB drives. Non-volatile. Standard forensic imaging with a write blocker to preserve integrity. |
| 5 | Remote / network storage | NAS, SAN, cloud storage. Requires coordination with storage administrators and possibly a legal process for cloud data. |
| 6 | Backups and archives | Least volatile. Slowest to change. Provides historical context for when the attacker first appeared. |
 
```
Critical rule: NEVER power down a compromised system before capturing RAM.
 
On shutdown you permanently lose:
- All running processes (including malware loaded in memory)
- Active network connections
- Encryption keys held in memory
- Any in-memory artifacts not yet written to disk
 
Use a live forensic imaging tool (e.g., DumpIt, WinPmem, LiME for Linux)
to capture RAM before any other action.
```
 
### Incident Planning and Exercises
 
- Tabletop exercise: key stakeholders walk through a simulated scenario verbally. No live systems. Identifies gaps in plans and communication.
- Simulation: live test of a simulated event (phishing campaign, data breach). Tests both technical controls and human response simultaneously.
- Root cause analysis: determines the fundamental cause of the incident. Multiple root causes may exist. Documents the response to the mistake as well as the technical fix.
