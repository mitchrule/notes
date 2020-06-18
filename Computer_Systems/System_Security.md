## System Security

### Securing TCP Connections (SSL)

#### (Almost) SSL

During the handshake phase Bob needs to:

1. Establish a TCP connection with Alice.
2. Verify that Alice really is Alice.
   1. Bob sends a hello message, Alice replies with her certificate, which is
      certified by a CA. Bob knows that the public key in the certificate belongs
      to Alice.
3. Send Alice a master secret key, which will be used by both Alice and Bob to
   generate all the symmetric keys they need for the SSL session.
   1. Bob generates a Master Secret (MS), encrypts it with Alice's public key
      to create the Encrypted Master Secret (EMS) to send to Alice. Alice can decrypt
      this. Now Bob and Alice both know the master secret for that SSL session.

It is generally considered safer if Alice and Bob do not use the same key for an
SSL session. Instead they can use different keys.

- $E_B =$ session encryption key for data sent from Bob to Alice.
- $M_B =$ session MAC key for data sent from Bob to Alice.
- $E_A =$ session encryption key for data sent from Alice to Bob.
- $M_A =$ session MAC key for data sent from Alice to Bob.

#### Data Transfer

Alice and Bob share the above four session keys.
SSL breaks the data stream into records and appends a MAC to each record for
integrity checking. Bob then encrypts the record+MAC. To create the MAC, Bob inputs
the record data and key $M_B$ into a hash function. To encrypt the package record, Bob
uses his session encryption key $E_B$.

#### Real SSL

SSL does not mandate that Alice and Bob use specific algorithms to complete the
handshake and data transfer. SSL allows them to agree on the algorithms they wish
to use.

1. The client sends a list of cryptographic algorithms it supports, along with a client nonce.
2. The server chooses a symmetric algorithm, a public key algorithm, and a MAC algorithm.
   It sends the client its choices, along with it's certificate and a server nonce.
3. The client verifies the certificate, creates a pre-master secret (PMS) and encrypts it
   with the server's public key before sending it to the server.
4. Using the same key derivation function, the client and server independently compute the master secret (MS)
   from the PMS and nonces. It is then sliced up to create two encryption and two MAC keys.
5. The client sends a MAC of all the handshake messages.
6. The server sends a MAC of all the handshake messages.
