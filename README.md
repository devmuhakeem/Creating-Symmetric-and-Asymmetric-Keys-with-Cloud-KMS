# Creating Symmetric and Asymmetric Keys with Cloud KMS

A hands-on Google Cloud lab where I created both a symmetric and an asymmetric encryption key using Cloud Key Management Service, to support a secure on-premises-to-cloud data migration.

## Scenario
A fictional bank needed to move a large volume of sensitive customer data — financial transactions and PII — from on-premises servers into the cloud. The CISO wanted confidentiality and integrity protected at rest, in transit, and in use. My job was to build the encryption keys needed to support that migration securely.

## What I did

### 1. Created a symmetric key
Set up a key ring (`demo-key-ring`) scoped to a specific region, then created a symmetric key (`demo-key`) with:
- Software protection level
- Generated key material
- Purpose: symmetric encrypt/decrypt
- A 90-day key rotation period

Symmetric keys use a single key for both encrypting and decrypting, which makes them fast — the standard choice for bulk data encryption.

### 2. Created an asymmetric key
Within the same key ring, created a second key (`demo-asymmetric-key`) with:
- Software protection level
- Generated key material
- Purpose: asymmetric decrypt

Asymmetric keys use a mathematically linked public/private key pair. Slower than symmetric encryption, but they solve the key distribution problem — you can share a public key openly without ever exposing the private key.

## Key takeaways
- Symmetric and asymmetric encryption aren't competing choices — they're usually combined. HTTPS itself uses asymmetric cryptography for the handshake, then switches to symmetric for the actual data transfer, because it's faster
- Key rotation periods matter for long-lived data protection — a key that never rotates is a bigger liability the longer it's in use
- Managing keys through Cloud KMS rather than embedding them in application code keeps them centrally auditable and access-controlled

## Tools
Google Cloud Key Management Service (KMS)

---
*Completed as a Google Cloud Skills Boost lab.*
