## 5.5 Audits and Assessments
 
### Audit Types
 
- Internal audits: assess compliance with regulatory and industry requirements. Audit committee oversees risk management activities. Self-assessments consolidated into ongoing reports.
- External audits: independent third-party audits. Type and frequency based on regulatory requirements. Examinations require hands-on research. Assessments evaluate current activities and recommend improvements.
- Attestation: formal confirmation of the accuracy of a company's security posture. May be required by regulators or customers.
### Penetration Testing Types
 
| Type | Description |
|---|---|
| White Box (Known Environment) | Tester has full knowledge: network diagrams, source code, credentials. Most efficient. Least realistic. Used for thorough testing when time is limited. |
| Gray Box (Partially Known) | Tester has partial knowledge. Focuses on specific systems or applications. Simulates an insider or partially informed attacker. |
| Black Box (Unknown Environment) | Tester has no prior knowledge. Also called a blind test. Simulates an external attacker with no inside information. Most realistic. Most time-consuming. |
| Physical | Tests physical security controls: building entry, badge systems, tailgating, server room access. Can bypass OS security. |
| Offensive (Red Team) | Attacks the system and actively looks for vulnerabilities to exploit. Simulates a real adversary. |
| Defensive (Blue Team) | Identifies and responds to attacks in real time. Monitors for intrusion. Prevents unauthorized access. |
| Integrated (Purple Team) | Combines red and blue activities. Creates an ongoing iterative process: attack, detect, patch, repeat. |
 
```
Working knowledge terminology (exam uses both naming conventions):
White box    = known environment      = full disclosure
Gray box     = partially known        = mix of known and unknown
Black box    = unknown environment    = blind test
```
 
### Reconnaissance
 
- Passive reconnaissance: learns from open sources without interacting with the target. Social media, corporate website, online forums, business organizations, dumpster diving. No risk of detection.
- Active reconnaissance: directly interacts with the target. Ping scans, port scans, DNS queries, OS fingerprinting, service version scans. Risk of detection.
