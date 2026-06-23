## Cryptographic Algorithms

Cryptography, which literally means "secret writing", is the art of making information secure by
encoding it. This is the opposite of security through obscurity.

The following terminology is used to discuss cryptography:
    Plaintext(*or cleartext*) - is an unencrypted message
    Ciphertext - is an encrypted message
    Algorithm - is the process used to encrypt and decrypt a message
    Cryptanalysis - is the art of cracking cryptographic systems.
    
There are three main types of cryptographic algorithms with different roles to play in the assurance
of the security properties:
    - confidentiality
    - integrity
    - non-repudiation

These types are hashing algorithms and two types of encryption ciphers: symmetric and asymmetric

An encryption algorithm or cipher is a type of cryptographic process that encodes data so that it
can be stored or transmitted securely and then decrypted only by its owner or its intended
recipient. Using a **key** with the encryption cipher ensures that decryption can only be performed
by an authorized person.

Substitution and Transposition Algorithms:
    A substitutio algorithm cipher involves replacing characters or blocks in the plaintext with
    different ciphertext. Simple substitution ciphers rotate or scramble letters of the alphabet.
    For example, ROT13 rotates each letter 13 places, so A becomes N, for instance.
    In contrast to substitution ciphers, the units in a transposition cipher stays the same in
    plaintext and ciphertext, but their order is changed, according to some mechanism. 
    
Symmetric Algorithms:
    encryption and decryption are both performed by the same secret key. The secret key must be kept
    known to authorized persons only. If the key is lost or stolen, the security is breached.
    Symmetric encryption is used for confidentiality. 
    
    Keys for modern symmetric ciphers use a pseudorandomly generated number of bits. The number of
    bits is the key length.
    
Asymmetric Encryption:
    encryption and decryption are performed by two different but related public and private keys in
    a key pair.
    
    When a public key is usd to encrypt a message, only the paired private key can decrypt the
    ciphertext. The public key cannot be used to decrypt the ciphertext.
    
    The drawback of asymmetric encryption is that it involves substantial computing overhead
    compared to symmetric encryption. Where a large amount of data is being encrypted on disk or
    transported over a network, asymmetric encryption is inefficient.
    
Hashing:
    Algorithm that produces a fixed length string of bits from an input plaintext that can be of any
    length. The output can be referred to as a hash or as a message digest. The function is designed
    so that it is impossible to recover the plaintext data from the digest (one-way) and so that
    different inputs are unlikely to produce the same output (a collision).
    
---

## Public Key Infrastructure

Certificate Authorities:
    Public key cryptography solves the problem of distributing encryption keys when you want to
    communicate securely with others or authenticate a message that you send to others.
    
    The basic problem with public key cryptography is that while the owner of a private key can
    authenticate messages, there is no mechanism for establishing the owner's identity. This problem
    is particularly evident with e-commerce. How can you be sure that a shopping site or banking
    service is really maintained by whom it claims?
    
    Public key infrastructure (PKI) aims to prove that the owners of public keys are who they say
    they are. Under PKI, anyone issuing a public key should publish it in a digital certificate. The
    certificate's validity is quaranteed by a certificate authority (CA).
    
Digital Certificates:
    a wrapper for a subject's public key. As well as the public key, it contains information about
    the subject and the certificate's issuer. 
   

