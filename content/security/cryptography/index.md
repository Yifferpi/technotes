---
title: "Cryptography"
date: 2022-01-12T15:03:55+01:00
draft: False
---

## Security properties
There are different security concepts that are gathered under the umbrella
term "security". In the following, we introduce some of these concepts and try
to outline the difference and clarify for later discussions.


- **Confidentiality**: keep unauthorized people from reading the data / keep 
data secret. In some literature, there is further distinction between 
secrecy (keep *own* data secret) and 
confidentiality (keep *someone else's* data secret).

- **Authentication**: knowing the source / sender of the data to be legitimate / the
person they pretend to be (*data (origin) authentication*) 
or verifying the identity and liveness
of another protocol participant (*entity authentication*).

- **Integrity**: knowing data has not been changed / tampered with by someone 
unauthorized to do so.

- **Privacy**: keep data *about a person* secret
- **Anonymity**: keep *identity* of a protocol participant secret

- **Authorization**: check whether someone is entitled to use a certain service / access
certain data.

- **Availability**: make sure communication cannot be prevented / protect against
Denial of Service. 

<!--TODO: maybe point some things out like differences, compare some properties -->

## Security primitives
Security primitives is what we call basic building blocks for more complex
cryptographic algorithms. We distunguish two types: symmetric and asymmetric.
The simple but fundamental difference is the following:
in symmetric procedures, there is **one** key only
whereas in asymmetric procedures, there are two distinct keys where one is usually
published and the other kept secret.

| Property   | confidentiality       | authentication    |
| ---------- | ---------------       | ----------------- |
| symmetric  | Symmetric Encryption  | MAC               |
| asymmetric | Public Key Encryption | Digital Signature | 

Symmetric cryptography is much faster / less expensive than asymmetric cryptography.
This is reflected in the key size that is commonly used: symmetric procedures like
AES use key sizes of around 128 to 256 bit whereas asymmetric procedures like RSA
use keys of 4096 bit.

The question then is why do we need asymmetric crypto?

As we mentioned, symmetric procedures have only one key. That same key is used
for both, encryption and decryption. This implies that communicating parties must
both be in possession of this key, i.e., must have a shared secret. This is 
not always the case. This is where asymmetric crypto comes in handy.

![Symmetric crypto](symmetric_crypto.png?width=18cm)

In asymmetric procedures on the other hand, there are two keys a and b. If a
message is encrypted using key a, then it can only be decrypted with key b and vice
versa. By making key a your private key and publishing key b you allow people to
encrypt messages that only you can read.

### Symmetric Encryption
Symmetric encryption can be split into:
- block ciphers (pseudo-random permutation)
- stream ciphers (pseudo-random generator)


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

