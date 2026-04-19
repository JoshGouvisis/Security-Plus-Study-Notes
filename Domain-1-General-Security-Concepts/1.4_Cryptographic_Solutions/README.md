## 1.4 - Cryptographic Solutions

### Public Key Infrastructure (PKI)

PKI is the complete framework of policies, procedures, hardware, software, and people used to create, distribute, manage, store, and revoke digital certificates. It binds public keys to verified identities through a chain of trust.

### Encryption Types

#### Symmetric Encryption
- Single shared key for both encryption and decryption (secret key encryption)
- Fast with low computational overhead
- Key must be securely exchanged before use
- Key size: 128 bits or larger

#### Asymmetric Encryption
- Mathematically linked key pair: public key (freely distributed) and private key (never shared)
- Data encrypted with the public key can only be decrypted with the private key
- Slower than symmetric due to mathematical complexity
- Key size: 3,072 bits or larger

#### Key Exchange

The core challenge: how do two parties securely agree on a symmetric key over an untrusted network?

1. Server sends its public key inside a certificate
2. Client verifies the certificate against a trusted CA
3. Client generates a session key and encrypts it with the server's public key
4. Server decrypts with its private key
5. Both parties now share the symmetric session key
6. All bulk data transfer uses the faster symmetric key

This is the basis of TLS and HTTPS. Asymmetric solves the key distribution problem. Symmetric handles bulk data efficiently.

- Out-of-band key exchange: key delivered by phone, courier, or in person, never over the internet
- In-band key exchange: key delivered over the network, protected by asymmetric encryption
- Key escrow: a trusted third party holds a copy of private keys for authorized recovery

### Encryption Levels

| Level | Description |
|---|---|
| Full-disk | Encrypts the entire storage volume. BitLocker (Windows), FileVault (macOS). |
| Partition/Volume | Encrypts a defined section of the disk. |
| File | Encrypts individual files. EFS (Encrypting File System) on Windows. |
| Database | Can encrypt the entire database or individual columns using separate symmetric keys. |
| Transport | Protects data in transit. HTTPS, TLS, IPsec, SSL/TLS VPN. |

### Key Stretching

Key stretching makes a weak password resistant to brute-force and offline cracking by increasing the computational cost of each guess. Also called key strengthening.

Method: hash the input repeatedly. Hash the password, hash the result, hash that result again. Repeat thousands of times. An attacker attempting brute force must reverse every layer of hashing per guess.

Note: Professor Messer's SY0-701 "Encrypting Data" video (1.4) covers the key stretching concept and mechanism. For named algorithm coverage (bcrypt, PBKDF2), supplement with the Darril Gibson study guide or Jason Dion's Udemy course, as these are referenced in the exam objectives but not named explicitly in the SY0-701 video series.

| Algorithm | Notes |
|---|---|
| bcrypt | Based on the Blowfish cipher. Adaptive cost factor. Common in web application password storage. |
| PBKDF2 | Password-Based Key Derivation Function 2. NIST recommended. Configurable iteration count. |
| scrypt | Memory-intensive. Designed to resist GPU and ASIC-accelerated brute-force attacks. |

### Hashing

- Maps data of any length to a fixed-length output (fingerprint or digest)
- One-way function: the original data cannot be recovered from the hash
- SHA-256 produces a 256-bit hash (64 hexadecimal characters)
- Used for: file integrity verification, password storage, digital signatures
- Collision: two different inputs produce the same hash output. MD5 has known collisions and must not be used for security purposes.

#### Salting

A random value (salt) added to a password before hashing.

stored_value = hash(password + salt)

- Each user receives a unique salt, so identical passwords produce different hashes
- Defeats rainbow table attacks (precomputed hash-to-password lookup lists)
- Does not stop brute force, but significantly increases the cost per attempt

### Digital Signatures

Sender side:
1. Hash the message
2. Encrypt the hash with the sender's private key (this is the signature)
3. Attach the signature to the message

Receiver side:
1. Decrypt the signature using the sender's public key
2. Independently hash the received message
3. Compare both hashes: if they match, integrity and origin are verified

| Property | What It Proves |
|---|---|
| Integrity | Any modification to the message invalidates the signature |
| Authentication | Only the holder of the private key could have created the signature |
| Non-repudiation | The sender cannot deny having signed the message |

The message does not need to be encrypted to be signed.

### Encryption Technologies

#### Trusted Platform Module (TPM)
- Cryptographic chip soldered to the motherboard
- Contains a random number generator and key generators
- Stores unique keys burned in during manufacturing
- Stores BitLocker encryption keys
- Password protected, preventing dictionary attacks
- Per-device: manages keys for that specific device only

#### Hardware Security Module (HSM)
- Dedicated hardware device for enterprise-scale cryptographic operations
- Stores thousands of cryptographic keys securely
- Available as a plug-in card or standalone network appliance
- Used in enterprise environments, certificate authorities, and payment processing

TPM vs. HSM: TPM is embedded in one device and serves that device only. HSM is a separate, high-capacity device managing keys at enterprise scale. When a question involves large-scale key management, CA operations, or payment infrastructure, HSM is the correct answer.

#### Key Management System
- Centralized platform (on-premise or cloud-based) for managing all cryptographic keys
- Creates keys for specific services (SSL/TLS, SSH), assigns to users, rotates on schedule, logs all usage

#### Secure Enclave
- An isolated processor separate from the main CPU
- Has its own boot ROM, true random number generator, and real-time memory encryption
- Stores root cryptographic keys and performs AES encryption in hardware
- Example: Apple T2 chip, iPhone Secure Enclave

### Obfuscation Techniques

| Technique | How It Works |
|---|---|
| Steganography | Hides data inside another file (image, audio, video, or TCP packet) so its presence is not apparent |
| Tokenization | Replaces sensitive data with a random token. Original stored in a separate secure vault. Token has no mathematical relationship to the original. Common in credit card processing (PCI DSS). |
| Data Masking | Partially conceals data in display or export. Original data intact in storage. Permissions-controlled. Uses substitution, shuffling, or masking. |

Tokenization vs. encryption:
- Encryption: original_data + key produces ciphertext, which is reversible with the key
- Tokenization: original_data produces a random_token with no mathematical relationship to the original, stored separately

### Blockchain
- A distributed ledger maintained and replicated across all participants
- Each transaction is cryptographically linked to the previous one and cannot be altered without network consensus
- Applications: payment processing, digital identity, supply chain monitoring, digital voting

### Certificates and PKI Components

A digital certificate binds a public key to a verified identity using the X.509 standard.

X.509 certificate contents: serial number, version, signature algorithm, issuer, subject (key holder), public key, extensions.

| Component | Purpose |
|---|---|
| Certificate Authority (CA) | Issues and digitally signs certificates. Trusted by browsers and operating systems. |
| Third-party CA | A public CA trusted by browsers. Vets domain and identity ownership before signing. |
| Private/Self-signed CA | Internal CA built in-house. Devices must be manually configured to trust it. |
| Wildcard Certificate | Covers all subdomains under a domain using the Subject Alternative Name (SAN) extension. |
| CRL | Certificate Revocation List. Maintained by the CA. Lists all revoked certificates. |
| OCSP | Online Certificate Status Protocol. Real-time certificate validity check. |
| OCSP Stapling | The certificate holder attaches a CA-signed OCSP response to the TLS handshake, proving current validity without requiring the browser to contact the CA directly. |

#### Root of Trust

A trusted anchor that validates everything above it in the certificate chain.

Root CA (self-signed, pre-installed in OS/browser)
  > Intermediate CA (signed by root)
    > End-entity certificate (signed by intermediate)

Can be implemented in hardware (HSM, TPM, Secure Enclave) or software (CA).
