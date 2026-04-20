## 4.6 Identity and Access Management
 
### IAM Concepts
 
| Concept | Description |
|---|---|
| Provisioning | Create accounts with name, attributes, group memberships, and permissions during hiring, transfers, or promotions. Principle of least privilege applies. |
| De-Provisioning | Remove or disable accounts on separation, transfer, or role change. Timely de-provisioning prevents orphaned accounts with excess access. |
| Identity Proofing | Confirming a user is who they claim to be during account creation: validation (passwords, security questions) and verification (passport, in-person, automated check). |
| Attestation | Periodic review and formal confirmation that user access rights are still appropriate for their current role. Required by many compliance frameworks. |
| Federation | Extends authentication across organizational boundaries. Partners and customers authenticate using their own credentials. Login with Google is a common example. |
| SSO | Single Sign-On. One authentication event grants access to all assigned resources. |
| LDAP | Lightweight Directory Access Protocol. Reads and writes directory information over IP. Used to query Active Directory and X.500-compatible directories. |
| SAML | Security Assertion Markup Language. Open standard for exchanging authentication and authorization data. Enterprise web SSO. XML-based. Not designed for mobile apps. |
| OAuth | Authorization framework. Determines what resources a user can access between applications. NOT an authentication protocol by itself. |
| OIDC | OpenID Connect. Authentication layer built on top of OAuth 2.0. Handles SSO authentication for modern apps including mobile. |
| Interoperability | VPN concentrators authenticate against LDAP. New apps use OAuth for API access. Different systems communicate through standard protocols. |
 
### SAML vs. OAuth vs. OIDC
 
```
SAML:
- Enterprise web SSO
- XML-based
- Handles both authentication and authorization
- Not designed for mobile applications
 
OAuth:
- Authorization framework ONLY
- Determines what resources an app can access on behalf of a user
- Does NOT handle authentication by itself
- Created by Twitter, Google, and others
 
OIDC (OpenID Connect):
- Authentication layer built ON TOP of OAuth 2.0
- Handles SSO including mobile applications
- Adds authentication to what OAuth provides
- Use when you see: "login with Google/Facebook/Microsoft" on a modern app
 
Exam trap: OAuth is not an authentication protocol.
OIDC is the authentication piece. SAML is for enterprise.
OIDC/OAuth is for modern and mobile.
```
 
### Access Control Models
 
| Model | Description |
|---|---|
| Mandatory (MAC) | OS enforces access based on security labels (Confidential, Secret, Top Secret). Admin assigns labels. Users cannot override. Highest security, lowest flexibility. |
| Discretionary (DAC) | Resource owner controls who has access and can modify permissions at any time. Most flexible. Less secure because users can inadvertently grant broad access. |
| Role-Based (RBAC) | Access granted based on job role (Manager, Director, Analyst). Admin assigns roles; roles carry permissions. Windows Groups implement RBAC. |
| Rule-Based | Admin creates explicit rules tied to objects. System checks ACLs. Example: lab network access allowed only 9am-5pm. |
| Attribute-Based (ABAC) | Access decisions combine multiple parameters: resource type, IP address, time of day, location, relationship to data. Most granular and flexible model. |
| Time-of-Day Restrictions | Access restricted during certain hours or days. Training rooms inaccessible 12am-6am. Conference rooms restricted after 8pm. |
| Least Privilege | Users receive only the permissions required for their role. Standard users never run with admin rights. |
 
### Multifactor Authentication
 
| Factor | Examples |
|---|---|
| Something You Know | Password, PIN, pattern. Weakest factor alone. Easily stolen or guessed. |
| Something You Have | Smart card, USB security key, hardware or software token (HOTP/TOTP), smartphone authenticator app. |
| Something You Are | Biometric: fingerprint, facial recognition, voice print, retina scan. Stored as a mathematical representation. Difficult to change if compromised. |
| Somewhere You Are | GPS location, IP address geolocation, proximity to a known Wi-Fi or mobile network. |
 
### Password Security and Privileged Access Management
 
- Password complexity: mix upper/lowercase, numbers, and special characters. Minimum 8 characters. Longer is significantly stronger.
- Password expiration: 30, 60, or 90-day cycles. Change more frequently for higher-privilege accounts.
- Password managers: different password per account. Enterprise versions add centralized management and recovery.
- Passwordless: facial recognition, security keys, biometrics. Solves password reuse and management problems.
- Just-in-time permissions: admin rights granted for a limited time window on request. Access approved based on policy. Breached accounts never hold persistent elevated rights.
- Password vaulting: primary credentials stored in a secure vault. Users never see the actual password. Credentials used for one session then rotated or deleted.
- Ephemeral credentials: short-lived, temporary credentials that expire automatically after a single session or defined time period. Never reused.
