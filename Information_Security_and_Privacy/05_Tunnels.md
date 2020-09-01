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
- Rules can also provide QoS based on UP or port.

## Deep Packet Inspection

- Inspects the contents of a packet and headers.
- Stateful filter redirects packets to a proxy that examines packets.
- Much more powerful.
- Much more intrusive and difficult to circumvent.
- Great Firewall of China uses DPI.
