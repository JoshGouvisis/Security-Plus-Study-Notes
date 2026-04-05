# 1.4 Cryptographic Solutions

This section details the logic of encryption, hashing, and the infrastructure used to manage trust.

## Encryption Methodologies
* **Symmetric Encryption:** One shared key for encryption and decryption. Fast and ideal for bulk data.
* **Asymmetric Encryption:** A public and private key pair. Used for secure key exchange and signatures.
* **Perfect Forward Secrecy (PFS):** Ensures that compromised long-term keys cannot decrypt past session data.

## Integrity and Trust
* **Hashing:** A one-way function used to verify data integrity.
* **Salting:** Adding random data to a password before hashing to stop rainbow table attacks.
* **Digital Signatures:** Using a private key to sign a hash. Provides integrity and non-repudiation.

## PKI and Hardware Security
* **Certificate Authority (CA):** The trusted entity that issues and signs digital certificates.
* **CSR (Certificate Signing Request):** The application sent to a CA to obtain a certificate.
* **OCSP Stapling:** A method for real-time certificate status checks during a secure connection.
* **TPM:** A hardware chip on a motherboard for local key storage.
* **HSM:** A dedicated device for managing thousands of cryptographic keys.
