---
title: "Cryptography"
date: 2022-01-12T15:03:55+01:00
draft: False
---


## Security primitives

|            | confidentiality       | authentication |
| ---------- | ---------------       | -------------- |
| symmetric  | Symmetric Encryption  | MAC            |
| asymmetric | Public Key Encryption | Digital Signature | 

### Symmetric Encryption
Symmetric encryption can be split into:
- block ciphers (pseudo-random permutation)
- stream ciphers (pseudo-random generator)

![Symmetric crypto](symmetric_crypto.png?width=18cm)

Stream Ciphers: generate pseudo-random key stream from a key k and an initialization
vector IV. xor the keystream with the plaintext to obtain a cipher text.
Whoever can generate the same keystream can decrypt the message again.

This is basically a one-time pad **as long as the key stream is never reused**.

Examples: AES in CTR mode, Salsa, ChaCha (used in TLS1.3, Wireguard)

Potential vulnerabilities: keystream reuse attacks (xor is dangerous)

Block Ciphers: A substitution cipher with random permutation,
the key defines a one-to-one mapping between an input block and output block.
Each block of plaintext is encrypted separately.

Encrypting the blocks by itself is **not secure**. There are different modes of
operation for block ciphers:
- ECB (Electronic Code Book) (**not secure**: Linux penguin..)
- CBC (Cipher Block Chaining)
Other modes that make a stream cipher from a block cipher again:
- CFB (Cipher Feedback)
- OFB (Output Feedback)
- CTR (Counter Mode)
- GCM (Galois Counter Mode) (encryption and integrity in single pass)

Example: DES, AES

### Message Authentication Codes
Provide a cryptographic checksum for authentication / integrity.
Compute `MAC(k, m)` where k is a shared symmetric key and m a message.

Hash-based MAC are referred to as *HMAC*. Block cipher based MAC: *CMAC*

### Authenticated Encryption with Associated Data (AEAD)
AEAD has two goals: encrypt the plaintext message and ensure the integrity
of the ciphertext and its associated data.

![AEAD Encrypt](aead_encrypt.png?width=15cm)

Essentially aims to combine encryption and integrity protection in a secure way.
Uses "Encrypt-then-MAC" to avoid problems with "MAC-then-Encrypt" and
"Encrypt-and-MAC"
Comes as a single ready-to-use cryptographic primitive with a simple API.

AES-GCM is a nonce-based AEAD built from a block cipher in CTR mode and the Galois MAC.
Today mostly with AES (therefore AES-GCM)

### Diffie Hellmann Key Exchange
Public values: large prime p, generator g
Alice has secret value a, Bob has secret value b

TODO: exchange example in small numbers, exchange graphic,
clock analogy, color mixing example

The problem: Man-in-the-Middle attack. (--> discussion of Out-of-Band channels)

### RSA
Textbook RSA:
1. pick p, q large secret primes.
2. pick e, compute d such that e\*d = 1 mod (p-1)(q-1)
3. - public key: e, N=pq
   - private key: d

The keypair can be used for either digital signatures or public key encryption.

### Hash functions
A hash function maps an arbitrary-length input to a finite length output.
Properties of a secure (cryptographic) hash function:
- One-way
- Weak collision resistence
- Strong collision resistence

Examples: MD5 (*broken*), SHA-1 (*broken*), SHA-2, SHA-3

One-way hash chains:
- use in reverse order of construction for e.g. time-delayed authentication

Merkle Hash Trees:
![Merkle Hash Tree](merkle_hash_tree.png?width=12cm)

D_i are data values. Verifier knows T_0 hash value.


### General Notes
Difference between authentication with MAC vs. with Digital Signature:
authentication with MAC enables *the receiver* to verify the origin. But the
receiver cannot convince a third party. Problem: the one who can verify can also forge.

## Security properties
- Integrity: (Data integrity)
Data has not been changed by someone unauthorized to do so. The point
is not to prevent change but make it possible for the receiver to tell if it occured.

- Confidentiality: data remains secret / unreadible to the adversary
An unauthorized person cannot understand / read the data.
Sometimes, we distinguish further:
    - Secrecy: keep (own) data hidden from unintended receivers
    - Confidentiality: keep *someone else's* data secret

- Privacy: keep data *about a person* secret
- Anonymity: keep *identity* of a protocol participant secret

- Authentication: know the source of data to be legitimate. Identity of the sender
is correct. Sender is indeed the person he/she pretends to be.
Distinguish: 
    - data (origin) authentication: ensure data originates from the claimed sender
    - entity authentication: (identification): verify identity and liveness of another
    protocol participant

- Authorization: Check whether someone is entitled to use a certain service / access
certain data.


