# kessari-crypto
kessari-crypto — Cryptographic primitives used by the Kessari protocol, including hashing, signatures, key formats, and verification utilities. Provides deterministic, auditable security foundations for transactions, wallets, and network validation.

# kessari-crypto

Cryptographic primitives used by the Kessari protocol.

This crate provides deterministic, auditable implementations of hashing, signatures, key formats, and verification utilities required for secure transaction processing and network validation.

This library does not implement network logic or economic behavior — it only defines the mathematical security foundation of the protocol.

---

## Scope

The crate includes:

- key generation
- address derivation
- digital signatures
- signature verification
- hashing utilities
- serialization formats

All functions must produce identical outputs across all supported platforms.

---

## Design Requirements

The following properties are mandatory:

- deterministic output
- constant-time operations where applicable
- platform-independent behavior
- explicit serialization formats
- no hidden randomness

Any change affecting output values is considered a breaking protocol change.

---

## Example

```rust
use kessari_crypto::{Keypair, sign, verify};

let keypair = Keypair::generate();

let message = b"hello";

let signature = sign(&keypair.private, message);

assert!(verify(&keypair.public, message, &signature));
```
## Relationship to the Protocol

Applications → SDK → Node → Validation → Cryptography (this crate)

Every transaction ultimately depends on these primitives for correctness and security.

---

## Security Notice

This library is consensus-critical.

Modifications must preserve deterministic behavior across nodes or the network may fork.

---

## Documentation

Protocol specification:  
https://github.com/kessari-protocol/kessari-docs

---

## Status

Early implementation. Interfaces may evolve prior to mainnet stabilization.

