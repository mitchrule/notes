## Digital Signatures and Message Integrity

### Hash Functions

- A hash function takes an input $m$ and computes a fixed length string $H(m)$
- Cryptographic hash functions are required to have the following property
  - It is computationally infeasible to find any two different messages $x$ and
    $y$ such that $H(x) = H(y)$

### Message Authentication Codes (MAC)

To perform message integrity, Alice and Bob will need a shared secret $s$. This
secret is called the _authentication key_. This shared secret allows message integrity
to be performed.

1. Alice creates message $m$, concatenates $s$ with $m$ to create $m + s$, and calculates the hash $H(m+s)$. This is called the message authentication code (MAC).
2. Alice the appends the MAC to the message $m$, creating an extended message $(m, H(m + s))$, and sends the extended message to Bob/
3. Bob receives an extended message $(m, h)$ and knowing $s$, calculates the MAC $H(m + s)$. If $H(m + s) = h$, everything is fine.

There are a number of different standards for MACs that have been proposed over time.
The most popular current standard is HMAC, which can be used with either MD5 or SHA-1
hashes. HMAC runs the authentication key through the hash function twice.

### Digital Signatures

Digital signatures work much like real world signatures.
They are used to indicate who the author of a document is, or to show that
someone agrees with the contents of a document.

Digital signing should be done in a verifiable and nonforgeable way.
It must be possible to prove that a document signed by an individual was actually
signed by that individual.

Public key cryptography is an excellent candidate for providing digital signatures.

- Bob wants to digitally sign a document $m$.
- To sign this document, Bob used his private key $K_b^-$ to compute $K_b^-(m)$.
- To verify that Bob signed the document, Alice can take Bob's public key, $K_b^+$ and used it to decrypt $K_b^-(m)$.
  - If this produces $m$, Alice has proven that Bob signed $m$.
- Whoever signed the document must have had access to Bob's private key.
  - Only Bob should have access to this key because the public key is not help in learning the private key.
  - This assumes that $K_b^-$ has not been stolen or given away by Bob.

If $m$ was modified to become $m'$, the signature Bob created for $m$ will not be valid
for $m'$. Since $K_b^+(K_b^-(m))$ does not equal $m$.

Signing data by encryption is computationally expensive and often overkill to be
encrypting the entire document. A better approach is to using hash functions.
This same process above can be used but replacing $m$ for $H(m)$.
Since $H(m)$ is generally smaller than $m$, less computational effort is required
to create the digital signature.

#### MACs vs. Digital Signatures

- Both digital signatures and MACs start with a message/document.
- To create a MAC out of the message we append an authentication key to the message, and then take the hash of the result.
  - Neither public nor symmetric key encryption is involved in the creating of the MAC.
- Digital signatures are a "heavier" technique because it requires underlying public key infrastructure with certification authorities.

#### Public Key Certification

Public key certification is certifying that a public key belongs to a specific entity.
It is used in many secure networking protocols, IPsec, SSL.
This stops people from impersonating another entity and sending a message encrypted with their own
keys sending their public key to verify it. The receiver would think that the message was from someone
else and the public key would decrypt it perfectly.

To ensure that a public key belongs to who we think it does, we use a _certificate authority (CA)_.
A CA's job is to validate identities and issue certificates. A CA has the following roles.

1. Verify that an entity is who it says it is.
   1. There are no mandated procedures for how this is done. One must trust the CA to a certain degree
2. Once the CA verifies the identity of the entity, the CA creates a certificate that binds the public
   key of that entity to the entity. The certificate contains the public key and globally unique identifying
   information about the owner of the public key. For example a name or IP address.
   This certificate is then digiatally signed by the CA.
