+++
chapter = false
title = "Security Basics"
weight = 5
+++

<!-- Introduction -->
In this article, we list common attack paradigms / patterns, try to explain them,
and potentially list examples.

- proxy attack
- downgrade attack
- MitM attack
- side channel attack
- roll-back attack
- DoS attack
- relay / replay attack
- supply chain attack

- Slow Loris
- POODLE
- Heartbleed
- Cuckoo attack (TPMs)

- confused deputy attack (TEE: on ARM TrustZone)
- Cold Boot attack


- Runtime attacks:
    - Buffer Overflow
    - Format String
    - Double free
    - Use-after-free


- proxy attack: contact other host for faster computation of checksum 
in the context of time-based attestation
- downgrade attack: force a key exchange protocol to use 
weaker cryptographic primitives than either participant supports
- man-in-the-middle attack: pretend to both participants to be the other participant
- side-channel attacks: any attack based not on the protocol but on a 
concrete implementation, where information to reduce the keyspace is leaked
over a so-called 'side channel'
- roll-back attack: roll back state
- denial of service attack: attack where the legitimate users of the service
can no longer use it (are denied access in some way)

