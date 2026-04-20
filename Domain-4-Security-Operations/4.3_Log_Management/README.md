## 4.3 Vulnerability Management
 
### Identification Methods
 
| Method | Description |
|---|---|
| Vulnerability Scan | Non-intrusive. Identifies potential vulnerabilities by checking configurations, open ports, and known CVEs. Does not exploit. Tests from inside and outside the network. |
| Penetration Test | Simulated attack. Actively attempts to exploit vulnerabilities. Lateral movement, privilege escalation, persistence. Often compliance-mandated. |
| SAST | Static code analysis. Reviews source code. Finds injection flaws, buffer overflows, hardcoded credentials. |
| DAST / Fuzzing | Tests running application. Sends random/malformed input and watches for crashes, errors, or exceptions. Finds runtime vulnerabilities. |
| Package Monitoring | Confirms software packages are from trusted sources with no embedded vulnerabilities. Hash verification before installation. |
| Threat Feeds | OSINT: public forums, government databases, commercial data. Proprietary: paid threat analytics. Dark web: hacking forums, credential markets. ISAOs: sector-specific sharing organizations. |
 
### CVSS Scoring Criteria
 
CVSS scores vulnerabilities from 0 to 10. Understanding the six components is required for exam scenarios.
 
| Component | What It Measures |
|---|---|
| Attack Vector | How the vulnerability is exploited: Network (remotest), Adjacent, Local, or Physical. Network = highest severity. |
| Attack Complexity | Conditions required. Low = straightforward attack. High = specific conditions required. |
| Privileges Required | Access level needed before exploiting. None, Low, or High. |
| User Interaction | Whether a victim must take an action. None = no user required. Required = victim must do something. |
| Scope | Whether the exploit affects resources beyond its security scope. Unchanged or Changed. |
| CIA Impact | Confidentiality, Integrity, and Availability impact. Each rated None, Low, or High. Drives the overall base score. |
 
```
CVSS severity ranges:
Critical: 9.0 - 10.0
High:     7.0 - 8.9
Medium:   4.0 - 6.9
Low:      0.1 - 3.9
None:     0.0
 
CVE vs. CVSS:
CVE = unique identifier for a specific vulnerability (e.g., CVE-2021-44228)
CVSS = the scoring system that quantifies severity of that CVE
Reference: nvd.nist.gov and cve.mitre.org
```
 
### Vulnerability Analysis and Prioritization
 
- False positive: scanner reports a vulnerability that does not actually exist. Requires manual verification. Different from a low-severity real finding.
- False negative: a real vulnerability that the scanner missed. Update signatures and cross-reference public databases.
- Exposure factor: the loss of value or business function if the vulnerability is exploited. Informs prioritization beyond raw CVSS score.
- Environmental variables: the same CVSS score carries different effective risk in different environments. An isolated test lab vs. a public production database requires different response urgency.
- Risk tolerance: the organization's acceptable level of risk. Drives patch scheduling and exception documentation.
### Remediation and Validation
 
- Patching: scheduled monthly plus emergency out-of-band patches for zero-day vulnerabilities.
- Segmentation: limit exploit scope. Air-gap or use internal NGFWs if patching is not immediately possible.
- Compensating controls: disable the problematic service, revoke access, or limit external exposure until a patch is deployed.
- Insurance: cybersecurity insurance covers lost revenue, data recovery, and ransomware. Intentional acts and fund transfers are generally excluded.
- Exceptions and exemptions: document unpatched vulnerabilities with a defined review timeline and compensating controls in place.
- Validation: rescan after patching to confirm the vulnerability is closed. Audit and manually verify critical systems.
- Reporting: continuous reports on number of vulnerabilities, patched vs. unpatched systems, and new threat notifications. Automation required at scale.
