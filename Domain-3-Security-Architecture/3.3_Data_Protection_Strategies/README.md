## 3.3 Protecting Data
 
### Data Types
 
| Type | Description |
|---|---|
| Regulated | Subject to government laws. HIPAA (PHI), PCI DSS (payment), GDPR (EU personal data). |
| Trade Secret | Unique to the organization. Not publicly disclosed. Protected by contract and law. |
| Intellectual Property | May be publicly visible but protected. Copyrights, trademarks, patents. |
| Legal Information | Court records, contracts, attorney communications, PII in legal documents. |
| Financial Information | Internal financials, customer payment records, credit card data, bank records. Highly regulated. |
| Human-Readable | Understandable without processing. Text, spreadsheets, images. |
| Non-Human-Readable | Requires processing to interpret. Encoded data, barcodes, binary files, encrypted content. |
 
### Data Classifications
 
| Classification | Access Level and Purpose |
|---|---|
| Public / Unclassified | No restrictions on viewing. Intentionally released for general access. |
| Private / Restricted | Restricted access. May require NDA. Not for general distribution. |
| Confidential | Very sensitive. Requires approval to view. Significant damage if disclosed. |
| Sensitive | Includes PII, PHI, and intellectual property. Strict access controls required. |
| Critical | Must always be accessible. Availability is the primary concern. |
 
### States of Data
 
| State | Where It Exists | How to Protect It |
|---|---|---|
| Data at Rest | Stored: HDD, SSD, flash drive, cloud storage | Full-disk encryption, file/folder encryption, ACL-based access controls |
| Data in Transit | Moving across a network | TLS (transport layer), IPsec (network layer), firewall, IPS |
| Data in Use | In memory: RAM, CPU registers, cache | Mostly decrypted. Vulnerable to memory scraping attacks. |
 
### Data Sovereignty
 
- Data stored in a country is subject to that country's laws.
- GDPR requires that data collected on EU citizens be stored within the EU.
- GDPR grants individuals the right to erasure (right to be forgotten).
- Compliance laws may prohibit moving data across national borders.
- Cloud providers must be evaluated based on where they physically store data, not just where they are headquartered.
### Geolocation vs. Geofencing
 
```
Geolocation:  determines where a user is (GPS, 802.11, IP address, mobile provider)
Geofencing:   uses that location to automatically allow or restrict access
              based on whether the user is inside or outside a defined boundary
 
Example: administrative console access permitted only when physically
         within the corporate building perimeter
```
 
### Methods to Protect Data
 
| Method | How It Works |
|---|---|
| Encryption | Converts plaintext to ciphertext using a key. Reversible with the correct key. Protects data at rest and in transit. |
| Hashing | One-way conversion to a fixed-length digest. Irreversible. Integrity verification and password storage. |
| Masking | Hides part of the original data in display or export. Original data intact in storage. Permissions-controlled. |
| Tokenization | Replaces sensitive data with a non-related token. Original stored in a secure vault. No mathematical relationship to original. Common in credit card processing. |
| Obfuscation | Makes data or code difficult to understand. Includes steganography, masking, and code obfuscation. |
| Segmentation | Separates sensitive data into different storage locations. Strongest controls applied to the most sensitive data. |
| Permission Restrictions | ACLs and role-based controls. Enforced at authentication and after login. |
| DLP | Data Loss Prevention. Monitors and controls data movement via email, USB, cloud upload, and print. Blocks or alerts when sensitive data moves to an unauthorized destination. Both detective and preventive. Required by PCI DSS and HIPAA. |
| Geographic Restrictions | Limits data access based on user location. Geofencing automatically allows or restricts access based on physical boundary. |
