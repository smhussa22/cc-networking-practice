# OSPF

## Overview

Open Shortest Path First (OSPF) is a link-state interior gateway protocol (IGP) used within a single autonomous system. Each router builds a complete map of the network topology (the link-state database) and runs Dijkstra's SPF algorithm to compute the shortest path tree. OSPF uses its own IP protocol number (89) rather than TCP or UDP.

## Conceptual Questions

- What is OSPF?
- What problem does OSPF solve?
- What is a link-state protocol?
- How does OSPF differ from RIP?
- How does OSPF differ from BGP?
- What is a link-state database (LSDB)?
- What is a Link State Advertisement (LSA)?
- What is the SPF algorithm?
- What is the cost metric in OSPF?
- How is cost calculated from interface bandwidth?
- What is an OSPF area?
- What is the backbone area (Area 0)?
- What is an ABR (Area Border Router)?
- What is an ASBR (Autonomous System Boundary Router)?
- What is a stub area?
- What is a totally stubby area?
- What is an NSSA (Not-So-Stubby Area)?
- What is the DR (Designated Router)?
- What is the BDR (Backup Designated Router)?
- Why are DR and BDR elected on broadcast networks?
- What is the DR election process?
- What determines DR/BDR priority?
- What is the OSPF Hello packet?
- What is the Hello interval?
- What is the Dead interval?
- What are OSPF neighbor states?
- What is the Down state?
- What is the Init state?
- What is the 2-Way state?
- What is the ExStart state?
- What is the Exchange state?
- What is the Loading state?
- What is the Full state?
- What is OSPFv3 and how does it differ from OSPFv2?
- What is OSPF authentication?
- What is OSPF graceful restart?

## Deep Dive Questions

- Describe the OSPF packet types.
- What is packet type 1 (Hello)?
- What is packet type 2 (Database Description / DBD)?
- What is packet type 3 (Link State Request / LSR)?
- What is packet type 4 (Link State Update / LSU)?
- What is packet type 5 (Link State Acknowledgment / LSAck)?
- Describe the OSPF common packet header fields.
- What is the Version field?
- What is the Type field?
- What is the Packet Length field?
- What is the Router ID field?
- What is the Area ID field?
- What is the Checksum field?
- What is the AuType field?
- Describe the Hello packet fields.
- What is the Network Mask field in Hello?
- What is the HelloInterval?
- What is the Options field?
- What is the Router Priority?
- What is the RouterDeadInterval?
- What is the Designated Router field?
- What is the Backup Designated Router field?
- What is the Neighbor field list?
- Describe LSA types.
- What is a Type 1 (Router) LSA?
- What is a Type 2 (Network) LSA?
- What is a Type 3 (Summary) LSA?
- What is a Type 4 (ASBR Summary) LSA?
- What is a Type 5 (AS External) LSA?
- What is a Type 7 (NSSA External) LSA?
- Describe the LSA header fields.
- What is the LS Age field?
- What is the LS Type field?
- What is the Link State ID?
- What is the Advertising Router?
- What is the LS Sequence Number?
- What is the LS Checksum?
- What is the Length field?
- How does OSPF flood LSAs?
- How does OSPF use sequence numbers to prevent stale LSAs?
- What is the MaxAge value and what happens when an LSA reaches it?
- How does SPF use the LSDB to build the shortest path tree?
- How does OSPF handle equal-cost multipath (ECMP)?
- How does OSPF handle incremental SPF recalculations?

## Why Questions

- Why does OSPF use link-state instead of distance-vector?
- Why does OSPF use its own IP protocol number instead of TCP or UDP?
- Why does OSPF require Area 0 as the backbone?
- Why are DR and BDR needed on broadcast segments?
- Why is OSPF faster to converge than RIP?
- Why does OSPF have multiple area types (stub, NSSA, etc.)?
- Why does OSPF use Dijkstra instead of Bellman-Ford?
- Why is the OSPF cost metric bandwidth-based?
- Why does OSPF use sequence numbers for LSA versioning?

## Coding Questions

- Implement Dijkstra's algorithm for a graph of routers and links.
- Implement a shortest path tree builder from an OSPF LSDB.
- Implement an OSPF Hello packet parser.
- Implement an OSPF LSA header parser.
- Implement a Type 1 (Router) LSA parser.
- Implement an OSPF neighbor state machine.
- Implement the DR election algorithm.
- Compute the routing table from an SPF result.
- Implement equal-cost multipath (ECMP) route installation.

## Edge Cases

- What happens when two routers have the same Router ID?
- What happens when the DR fails and the BDR must take over?
- What happens when an LSA sequence number wraps around?
- What happens when an area is partitioned (no path to Area 0)?
- What happens when the Hello/Dead interval mismatch between neighbors?
- What happens when OSPF authentication keys mismatch?
- How does OSPF handle a link that bounces rapidly?
- What happens when the LSDB grows very large?

## Debugging Scenarios

- Two OSPF routers are stuck in the 2-Way state and never reach Full. Why?
- An OSPF adjacency forms and immediately drops. What do you investigate?
- A route appears in the LSDB but not in the routing table. Why?
- OSPF convergence after a link failure takes longer than expected. What do you check?
- The DR election keeps re-running on a broadcast segment. What could cause this?
- OSPF memory usage spikes on a router. What is the likely cause?

## System Design Questions

- Design a network simulation that runs OSPF among virtual routers.
- Design a tool that visualizes the OSPF LSDB as a graph.
- Design a system that detects OSPF topology changes and triggers alerts.

## Related Topics

- [BGP](../bgp/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [Debugging](../debugging/questions.md)
