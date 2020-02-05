---
title: Cryptography for mere mortals
theme: simple
---

# Cryptography for Mere Mortals

---

## Who am I

* (Web) software engineer
* Freelancer
* Security enthusiast
* Twitter: @vangool_it

Note:
keep it short, nobody cares

---

## Why this talk?

Note: 
* Information is hard to find
* Disconnect between basic and complicated information
* Errors are common, mistakes easy to make
* Lots of implementations have no reasoning behind them
* Coursera course by Dan Boneh
* Looked up the complex stuff so you don't have to

---

## Trust and the CIA

Disclaimer: Don't trust the CIA

Note: 
* Go into what trust means, and what each of the CIA letters mean
* Crypto keeps trust small while not restricting freedom
* Crypto deals with C and I, not A
* Implementations can affect A

---

## The nature of data

Note: 
* For crypto, it's all numbers
* Crypto is just math on these numbers
* Data at rest vs in transit

---

## Symmetric cryptography

Note:
* Only one key for both ways
* Mostly useful for data at rest
* Less useful for data in transit
* Key sharing is problematic

----

## Stream ciphers

Note:
* Like One-Time Pad
* Operate on arbitrary length data
* Require key size the same as data size

----

## Block ciphers

Note:
* Like AES
* Operate on fixed length data blocks
* Require fixed key size
* ECB mode is trash
* CBC mode is less trash but still trash

---

## Asymmetric cryptorgaphy

Note:
* Like RSA
* Different key for each direction
* TLS uses asymmetric crypto
 * Cert is pub key
* Useful for data in transit
* Less useful for data at rest
* Key sharing is easier (but still complicated under the hood)
* Doesn't usually need to be handled by the application
 * But sometimes it does, like with async stuff
 * In those cases, use things like JWT and WS-SEC

---

## Hashing

Note:
* One way -> hash is not easily reversed to valid data
* No secrets involved, so easily forged
* Can be used to verify I, but only in some cases
 * Transmission errors
 * See if two things match (like passwords or files)
* Does not protect C: identical P -> identical H
 * Salting helps this!

---

## Signing

Note:
* Like HMAC
* It's hashing but with secrets!
* Useful for protecting integrity
* Can also be used to protect ciphertexts from tampering
* Can be done symmetrically or asymmetrically
* Encrypt-then-sign!

---

## What is security?

----

### For hashing

Collisions are unlikely

----

### For password hashing

It's also slow 

----

### For encryption

Data is indistinguishable from random

Note:
* This does not mean the data IS random!
 * Right to be forgotten: don't do this!

----

### For signing

Forging signatures is hard

Note:
* Signatures can still be easily verifiable even without secrets
* Do not guarantee any confidentiality

---

## In conclusion

* Encryption protects confidentiality, but not integrity
* Symmetric cryptography for data at rest
* Asymmetric cryptography for data in transit
* Use hashing and signing to protect integrity
 * But consider your threat models
* Use authenticated encryption where possible

---

## Common pitfalls

* Weak keys/IVs
* Descriptive errors
* Misconfiguration
* Side channel attacks

Note:
* Go into zero IVs or default keys
 * Not just for cryptography, signing too
 * Symfony's secret -> used for remember me token signature
* Descriptive errors leak implementation details
 * Go into padding oracles
* Misconfigurations such as weak modes or algorithms
* Side channel attacks such as timing or power attacks

---

# Any questions?
