# Tunnels

## What is a tunnel?

Tunnelling involves encapsulation of one protocol by another.

Tunnelling involves routing such that two physically disconnected devices can communicate.

## Why use a tunnel?

### Security

Many network protocols transmit data in plain text. An encrypted tunnel allows you to transmit data securely over insecure protocols.

### Connect to a workplace or another network

Remote access VPN to give your device a LAN IP address on your office network or connect two or more networks.

### Keeping Communications Private

## Tunnel Encryption

Encrypted tunnels allow you to transmit data in a secure and private way.

Historically, the internet was very small and there was a high degree of trust between users. This is why so many of our protocols transmit data in plain text.

## Routing

### Site to Site Routing

- Used to connect two different sites.
- For example, two offices of the same business.
- Printers, computers, servers, databases can be shared across sites.

### Remote Access Routing

- Used by a single host to connect to a remote site.
- For example, connecting your laptop to your office network in order to work from home.
- The computer would appear to be on the local network of the remote site.
- Involves NAT at the tunnel endpoint.

### Tunnelling to Bypass a Firewall

- All traffic passes through and encrypted tunnel.
- Firewalls and ISPs cannot read the encrypted traffic in order to filter or track it.

## Encapsulation

- Tunnelling involves the encapsulation of one protocol by another.
  - Like an envelope within an envelope.

## Tunnels are Transparent

- Transparent to both the application and the user.
- An application does not know its traffic is being routed through a tunnel.

## Tunnelling Protocols

### SSH

- Secure Shell.
- Often thought of as a secure telnet.
  - Is actually a cryptographic protocol for tunnelling anything.
- Runs on port 22.
- Uses an ephemeral Diffie-Hellman for public key exchange and then a symmetric AES for data.
- Multiple authentication mechanisms.
  - username/password
  - public/private key pair
- Snowden claims that the NSA can sometimes decrypt SSH
- Assumes the attacker does not have access to memory such as in a virtual environment.
- Can be difficult to keep track of which SSH keys are in use and what they are used for.

### PPTP

- Largely superceded.
- Built into many OSs
- Has many security flaws in its authentication mechanisms.
- NSA can break it.
- Easy to firewall and block.

### OpenVPN

- Open source.
- Uses OpenSSL for encryption.
  - Assumes that OpenSSL is secure.
- Can choose cipher for crypto, but generally variants of Diffie Hellman with AES.
- Perfect forward secrecy through DH key negotiation.
- Renegotiates AES key every 6 hours by default.
- Multiple authentication mechanisms.
  - username/password
  - public/private key pair
- Port 1194/UDP
- Can be configured to use TCP so it appears like web traffic.
- Bloated code base
- Can traverse NAT and most firewalls.
- Slow - latency hit.
- Can be configured for minimal or no logging.
- Requires 3rd party software.
- Make sure data stream is encrypted using AES not Blowfish.

### HTTP Tunnelling

- Great for traversing a proxy.

### Wireguard

- Small codebase, less possible mistakes.
- Extremely fast with very little latency hit.
- Uses a variant of Diffie-Hellman for key exchange and ChaCha, a variant of Salsa20, for symmetric key.
- Every few minutes a new symmetric key is negotiated to ensure perfect forward secrecy.
- Salsa20 is faster than AES.

# Firewalls

## Packet Filter

Accepts, rejects, drops, or modifies packets according to a set of rules.

These rules are based upon 5 TCP/IP header fields (source address, source port, destination address, destination port, protocol), and if ICMP then ICMP type and code.

Stateless - each packet is processed independently.

Stateful - keeps track of packets.

## Host Based Firewalls

- Runs on a device and controls incoming and outgoing traffic.
- Block network access for an aplication or firce it to use a tunnel.
- Rate limit incoming traffic.
- Block incoming traffic by default.
- Log packets it denies as part of Intrusion Detection System (IDS).

## Network Based Firewalls

- Run on a gateway router allowing, blocking, or dropping traffic between two or more networks.
- A bottleneck or chokepoint through which traffic must pass.
- Caching
- Can redirect packets.
- Rules can control access by port.
- Rules can also provide QoS based on IP or port.

## Deep Packet Inspection

- Inspects the contents of a packet and headers.
- Stateful filter redirects packets to a proxy that examines packets.
- Much more powerful.
- Much more intrusive and difficult to circumvent.
- Great Firewall of China uses DPI.
