## 1.2 - Fundamental Security Concepts

### CIA Triad

The three foundational principles of information security. Every security decision maps to one or more of these.

| Principle | Definition | Controls |
|---|---|---|
| Confidentiality | Information accessible only to authorized individuals | Encryption, access controls, MFA |
| Integrity | Data stored and transmitted exactly as intended; any modification is detectable | Hashing, digital signatures, certificates |
| Availability | Authorized users can access systems and data when needed | Redundancy, fault tolerance, patching |

### Non-Repudiation

Provides cryptographic proof that a message came from a specific sender and was not altered.

| Component | Mechanism | What It Proves |
|---|---|---|
| Proof of integrity | Hash of the data | The data has not changed |
| Proof of origin | Digital signature (created with sender's private key) | The message came from a specific sender |

A hash alone proves integrity but does not identify the sender. A digital signature proves both. Non-repudiation requires both.

### AAA Framework

| Element | Definition |
|---|---|
| Identification | Who you claim to be, typically a username |
| Authentication | Proving the claim using passwords, certificates, biometrics, or tokens |
| Authorization | What you are permitted to access based on your verified identity |
| Accounting | Logging what you did: login time, data accessed, resources used, logout time |

#### Authenticating Devices

Devices authenticate using digitally signed certificates issued by a trusted internal Certificate Authority (CA). Business processes such as VPN access and network admission control rely on device certificates.
