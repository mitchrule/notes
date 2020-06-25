## Kurose and Ross Chapter 4 Questions

### Section 4.1

1. Recall that the name of a transport layer packet is a segment and the name of a
   link layer packet is a frame. What is the name of a network layer packet? What
   is the fundamental difference between a router and a link layer switch?

   A network layer packet is called a datagram. A router is designed to direct data
   in a network. When it receives a packet, it forwards it to the next step in the
   journey to its destination. Routers can be used to connect networks. A switch
   is made only for LANs. They are used for connecting devices within the same network.

2. The network layer can be broadly divided into data plane functionality and control
   plane functionality. What are the two main functions of the two planes?

   The data plane handles the actual transfer of packets from one host to another,
   known as forwarding. The control plane handles the network wide process of using
   routing algorithms to build routing tables so the data plane knows where to forward
   the data. This is known as routing.

### Section 4.3

17. Suppose host A sends host B a TCP segment encapsulated in an IP datagram.
    When host B receives the datagram, how does the network layer in host B know it
    should pass the segment (the payload of the datagram), to TCP rather than to UDP
    or some other protocol?

    There is a field within the datagram header called protocol. This indicates
    which upper layer protocol the payload should be handed to.

18. What field in the IP header can be used to ensure that a packet is forwarded
    through no more than $N$ routers?

    The time-to-live field. This is decremented each time to packet is forwarded.

19. Recall that we saw the internet checksum being used in both transport layer
    segment and in network layer datagrams (IP header). Now consider a transport layer segment
    encapsulated in an IP datagram. Are the checksums in the segment header and
    datagram header computed over any common bytes in the IP datagram?

    There should be no common bytes between the two checksums. The checksum for
    the TCP segment is computed over the payload and the header. The datagram
    checksum is only computed against the header fields of the datagram, not the
    payload, which is the TCP segment.

20. When a large datagram is fragmented into multiple smaller datagrams, where are
    these smaller datagrams reassembled into a single larger datagram?

    If the fragmented datagrams encounter a router capable of handling larger datagrams,
    they can be reassembled at that router before being forwarded on. Otherwise,
    they will be reassembled at the host.

21. A router has eight interfaces. How many IP addresses will it have?

    The router would have at least 9 IP addresses. One for each of the outgoing
    interfaces and another for at least one incoming interface.

22. What is meant by the term "route aggregation"? Why is it useful for a router
    to perform toure aggregation?

    Aggregation allows routers to only maintain routing tables for prefixes of
    addresses. Any incoming address that matches the prefix is forwarded on that
    interface. This allows much smaller routing tables to be created.
