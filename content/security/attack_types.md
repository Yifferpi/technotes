+++
chapter = false
title = "attack types / classes"
weight = 5
+++

<!-- Introduction -->
In this article, we list common attack paradigms / patterns, try to explain them,
and potentially list examples.

- proxy attack: contact other host for faster computation of checksum in the context of time-based attestation
- downgrade attack: force a key exchange protocol to use weaker cryptographic 
primitives than either participant supports
- man-in-the-middle attack: pretend to both participants to be the other participant
- side-channel attacks: any attack based not on the protocol but on a 
concrete implementation, where information to reduce the keyspace is leaked
over a so-called 'side channel'
