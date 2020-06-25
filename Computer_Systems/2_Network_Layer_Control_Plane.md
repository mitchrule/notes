## Network Layer - Control Plane

### Routing Algorithms

A graph is used to formulate routing problems. Nodes in the graph represent
routers and edges represent the physical links between there routers.

A centralised routing algorithm computes the least cost path between a source and
destination using complete, global knowledge about the network. The algorithm
takes the connectivity between all nodes and all link costs as inputs.
This requires that the algorithm somehow obtain this information before actually
performing the calculation. Then the calculation can be done at one site.
Algorithms with global state information are often referred to as _link state (LS) algorithms_, since the algorithm must be aware of the cost of each link in the
network.

In a decentralised routing algorithm, the calculation of the lesat cost path is
carried out in an iterative, distributed manner by the routers. No node has complete
information about the costs of all network links. Each node begins with only the knowledge
of the costs of its own directly attached links. Through an iterative process of calculation
and exchange of information with its neighbouring nodes, a node gradually calculates the least
cost path to a destination or set of destinations. A _distance vector (DV) algorithm_ is used
to do this.

#### Link State Routing

Link state routing uses a pathfinding algorithm such as Dijkstra's algorithm over the complete
graph of all routers in the network to create the routing tables.

#### Distance Vector Routing Algorithm

Each node $x$ begins with $D_x (y)$, an estimate of the cost of the lest cost path from itself to
node $y$, for all nodes, $y$, in $N$. Let $D_x = [D_x (y): y$ in $N]$ be the node $x$'s distance
vector, which is the vector of cost estimates from $x$ to all other nodes. Each node maintains
the following routing information:

- For each neighbour $v$, the cost $c(x,v)$ from $x$ to directly attached neighbour $v$.
- Node $x$'s distance vector.
- The distance vectors for each of its neihgbours.

In the dsitributed, asynchronous algorithm, from time to time, each node sends a copy of its
distance vector to each of its neighbours. When node $x$ receives a new distance vector from any
of its neighbours $w$ it saves $w$'s distance vector, and then uses the Bellman-Ford equation
to update its own distance vector as follows:.

$D_x (y) = min_v \{c(x,v) + D_v (y) \}$ for each node $y$ in $N$.

If node $x$'s distance vector has changed as a result of this update step, it will send its
updated distance vector to each of its neighbours. As long as all the nodes continue to exchange
their distance vectors in an asynchronous fashion, each cost estimate converges to the actual
cost of the least cost path from node $x$ to $y$.

### Internet Control Message Protocol

The Internet Control Message Protocol (ICMP) is used by hosts and routers to communicate network
layer information to each other, most commonly used for error reporting.

ICMP is often considered part of IP, but technically it lies just above IP, as ICMP messages are
carried inside IP datagrams. ICMP messages are carried as IP payload, just as TCP or UDP segments
are.

ICMP messages have a type and a code field, and contain the header and the first 8 bytes of the IP
datagram that caused the ICMP message to be generated in the first place.

Here are come ICMP message types:

| _ICMP Type_ | _Code_ | _Description_                      |
| ----------- | ------ | ---------------------------------- |
| 0           | 0      | echo reply (to ping)               |
| 3           | 0      | destination network unreachable    |
| 3           | 1      | destination host unreachable       |
| 3           | 2      | destination protocol unreachable   |
| 3           | 3      | destination port unreachable       |
| 3           | 6      | destination network unknown        |
| 3           | 7      | destination host unknown           |
| 4           | 0      | source quench (congestion control) |
| 8           | 0      | echo request                       |
| 9           | 0      | router advertisement               |
| 10          | 0      | router discovery                   |
| 11          | 0      | TTL expired                        |
| 12          | 0      | IP header bad                      |
