# Cryptography

## Cryptographic Protocols

Before public key cryptography, we only had symmetric key cryptography. Where the same key is used to both encrypt and decrypt the payload.

### Public Key Cryptography

- The receiver generates two keys
  - A public key $pk$, for encrypting
  - A private key $sk$, for decrypting
- She publicises the public key
  - People use this for decrypting messages
- She keeps the private key secret
  - She uses this for decrypting messages

#### RSA

- The receiver thinks of two large prime numbers $p,q$
  - About 300 digits long
  - She multiplies them together to get $N=pq$
  - She generates the public exponent $e$ (almost any $e$ will do)
  - She publicises $pk=(N,e)$. This is her full public key
- To encrypt message $m$, compute:
  - $m^e$ mod $N$
- The receiver can decrypt because she knows $p$ and $q$
  - Nobody else can factorise $N$, the computation takes too long

Typically, public key cryptography is used to establish a shared symmetric key for further communication. This is because symmetric key cryptography requires significantly less computing power.

## Signal and Diffie-Hellman Key Exchange

- Public information
  - Large prime $p$
  - Generator $g$ (a number)
- Alice has
  - Secret $a$
  - Public $A=g^a$ mod $p$
  - She sends this to Bob
- Bob has
  - Secret $b$
  - Public $B=g^b$ mod $p$
  - He sends this to Alice
- We assume that it is not possible for an eavesdropper to calculate $a$ or $b$
- Shared secret
  - $K = g^{ab}$ mod $p$
  - Alice and Bob take the public key they received from each other, and raise it to their secret exponent
  - $K = B^a$ mod $p$
  - $K = A^b$ mod $p$
- Assume
  - An attacker can't derive $g^{ab}$ mod $p$ from $g^a$ mod $p$ and $g^b$ mod $p$, given $g,p$

This shared key can now we used to share information using something such as AES.

## Blockchain and Bitcoin

- Bitcoin is a distributed e-cash system
  - No government or authority
  - The globally shared state incorporates the entire history of all transactions and all generated coins.
  - When you perform a transaction
    - You announce it
    - Some other participants compute a proof of work and incorporate it into the bitcoin blockchain

### Proof of Work

- Hash (using SHA-256)
  - The prior block
  - The transactions in the block being added
  - A randomly chosen nonce $n$
- Succeed when the digest (output of SHA-256) is below some threshold
  - This proves you tried a lot of different $n$ values
  - You make money as a result
  - The threshold necessary decreases as more participants join the network
- Broadcast the new block, including $n$.
  - This is now added to the blockchain
  - It took a long time to generate it, but anyone can test it

What problem is this trying to solve?

- This system gives us the ability to agree upon what constitutes a legitmately added transaction.
- It is deliberately made to be difficult and slow, so we don't get an enormous number of transactions added at any time.

### Bitcoin Agreement

- Sometimes different versions of the blockchain diverge
  - Simultaneous updates
  - Network connectivity problems
- Honest nodes should accept the longest version
  - Largest total work
- In practice this works pretty well
  - In principle an attacker with enough computing power could subvert it
