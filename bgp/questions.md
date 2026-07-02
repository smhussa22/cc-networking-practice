# BGP

## Overview

Border Gateway Protocol (BGP) is the inter-domain routing protocol of the Internet. It is a path-vector protocol that exchanges reachability information between autonomous systems (ASes). BGP runs over TCP on port 179 and uses a finite state machine to manage peer relationships.

## Conceptual Questions

- What is BGP?
- What problem does BGP solve?
- What is an autonomous system (AS)?
- What is an ASN (Autonomous System Number)?
- What is the difference between eBGP and iBGP?
- Why does BGP use TCP instead of UDP?
- What port does BGP run on?
- What is a BGP peer (neighbor)?
- What is a BGP session?
- What is a BGP prefix?
- What is a route in BGP?
- What is a path attribute?
- What is route selection?
- What is route withdrawal?
- What is a BGP UPDATE message used for?
- What is route flap?
- What is route flap damping?
- What is a BGP community?
- What is a large community?
- What is graceful restart?
- What is a BGP confederation?
- What is a route reflector?
- Why is route reflection needed?
- What is a full mesh in iBGP?
- What is the BGP decision process (best path selection)?
- What is the role of NEXT_HOP?
- What is recursive route lookup?
- What is BGP route aggregation (summarization)?
- What is a null route (blackhole route) in BGP?
- What is BGP hijacking?
- What is RPKI?
- What is BGP route leak?

## Deep Dive Questions

- Describe the BGP FSM (Finite State Machine) states.
- What is the Idle state?
- What is the Connect state?
- What is the Active state?
- What is the OpenSent state?
- What is the OpenConfirm state?
- What is the Established state?
- Describe transitions between each FSM state.
- What triggers a transition from Idle to Connect?
- What triggers a transition from Connect to Active?
- What triggers a transition from Active back to Idle?
- What triggers a transition to OpenSent?
- What triggers a transition to OpenConfirm?
- What triggers a transition to Established?
- Describe the OPEN message fields.
- What is the BGP version field in OPEN?
- What is the My AS field in OPEN?
- What is the Hold Time field in OPEN?
- What is the BGP Identifier in OPEN?
- What are Optional Parameters in OPEN?
- Describe the KEEPALIVE message.
- How is the hold timer maintained?
- What happens when the hold timer expires?
- Describe the UPDATE message fields.
- What is the Withdrawn Routes field?
- What is the Path Attributes field?
- What is the NLRI (Network Layer Reachability Information) field?
- Describe the NOTIFICATION message.
- What are the error codes and subcodes in NOTIFICATION?
- Describe the path attribute AS_PATH.
- Describe the path attribute NEXT_HOP.
- Describe the path attribute LOCAL_PREF.
- Describe the path attribute MED (Multi-Exit Discriminator).
- Describe the path attribute ORIGIN.
- What are the three ORIGIN values (IGP, EGP, Incomplete)?
- What is the ATOMIC_AGGREGATE attribute?
- What is the AGGREGATOR attribute?
- Describe the BGP best path selection process step by step.
- What is the weight attribute (Cisco-specific)?
- Why is LOCAL_PREF preferred over MED?
- When is AS_PATH length used in best path selection?
- When does MED apply?
- What is the tie-breaker when all other attributes are equal?
- How does iBGP differ from eBGP in terms of NEXT_HOP handling?
- What is the iBGP split-horizon rule?
- How does a route reflector break the iBGP split-horizon rule?
- What is the CLUSTER_LIST attribute?
- What is the ORIGINATOR_ID attribute?
- How do confederations reduce iBGP full mesh?
- What is the 4-byte ASN extension (RFC 4893)?
- What is the AS4_PATH attribute?
- What is ADD-PATH (RFC 7911)?

## Why Questions

- Why does BGP use TCP instead of a protocol like OSPF's own transport?
- Why port 179?
- Why is BGP a path-vector protocol instead of a distance-vector or link-state protocol?
- Why does iBGP require a full mesh by default?
- Why doesn't iBGP modify AS_PATH?
- Why is LOCAL_PREF used within an AS and MED used between ASes?
- Why does BGP not automatically detect the best path based on latency?
- Why is route flap damping controversial?
- Why is graceful restart important for production networks?
- Why is BGP considered the protocol that holds the Internet together?
- Why is BGP hijacking possible and what does RPKI do to prevent it?
- Why use communities instead of multiple BGP sessions?

## Coding Questions

- Implement a BGP FSM.
- Implement a BGP OPEN message parser.
- Implement a BGP UPDATE message parser.
- Implement a BGP NOTIFICATION message parser.
- Implement a BGP KEEPALIVE sender.
- Implement a prefix trie for IP routing.
- Implement longest prefix match (LPM) lookup.
- Implement BGP best path selection given a set of paths with attributes.
- Implement AS_PATH loop detection.
- Implement a BGP route table that stores prefixes with their attributes.
- Implement a BGP UPDATE encoder.
- Implement BGP community parsing and filtering.

## Edge Cases

- What happens when both peers propose different hold times?
- What happens when a BGP session drops mid-transfer of an UPDATE?
- What happens when AS_PATH contains your own ASN (loop detection)?
- What happens when NEXT_HOP is unreachable?
- What happens when two paths are exactly equal through all decision process steps?
- What happens when a route reflector receives a route with its own CLUSTER_LIST entry?
- What happens when a NOTIFICATION is received with an unknown error code?
- How does BGP handle a peer that sends malformed UPDATE messages?
- What happens when the hold timer is negotiated to zero?
- How does BGP handle duplicate prefix advertisements?

## Debugging Scenarios

- BGP adjacency keeps flapping. What do you investigate?
- BGP session stays in Active state and never reaches Established. Why?
- A prefix is in the BGP table but not being used for forwarding. What do you check?
- Route from a peer is received but immediately withdrawn. What could cause this?
- A specific prefix is not being propagated to iBGP peers. Why?
- BGP memory usage spikes. What could be sending excessive prefixes?
- BGP convergence after a link failure is slow. How do you investigate?
- A route is being selected that seems suboptimal. Walk through the decision process.

## System Design Questions

- Design a BGP route collector that stores the global routing table history.
- Design a BGP monitoring system that detects route hijacks in real time.
- Design a route server for an Internet exchange point (IXP).
- Design a system to simulate BGP convergence at scale.

## Related Topics

- [OSPF](../ospf/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [Debugging](../debugging/questions.md)
- [System Design](../system-design/questions.md)
