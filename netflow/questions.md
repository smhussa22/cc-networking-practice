# NetFlow

## Overview

NetFlow is a network protocol developed by Cisco for collecting IP traffic information and monitoring network flows. A flow is defined by a set of key fields (the five-tuple), and NetFlow exporters send aggregated flow records to a collector. It is widely used for traffic analysis, capacity planning, and security monitoring.

## Conceptual Questions

- What is NetFlow?
- What problem does NetFlow solve?
- What is a flow?
- What is the five-tuple that defines a flow?
- What is a NetFlow exporter?
- What is a NetFlow collector?
- What is a NetFlow aggregator?
- What is the difference between NetFlow v5 and IPFIX?
- What is sFlow and how does it differ from NetFlow?
- What is sampling in NetFlow?
- What is the difference between sampled and unsampled NetFlow?
- What is an active timeout?
- What is an inactive timeout?
- When does a flow expire due to active timeout?
- When does a flow expire due to inactive timeout?
- What is a NetFlow template record?
- What is a NetFlow data record?
- Why did Cisco introduce templates in NetFlow v9 and IPFIX?
- What transport protocol does NetFlow use?
- Why does NetFlow use UDP?
- What is the NetFlow export format?
- How does a router determine which interface to export NetFlow from?
- What is bidirectional flow and how does NetFlow handle it?
- What is the difference between ingress and egress NetFlow?

## Deep Dive Questions

- Describe the NetFlow v5 header format.
- What fields are in a NetFlow v5 header?
- What is the version field?
- What is the count field?
- What is the sys_uptime field?
- What is the unix_secs and unix_nsecs field?
- What is the flow_sequence field?
- What is the engine_type and engine_id field?
- What is the sampling_interval field?
- Describe the NetFlow v5 flow record format.
- What is srcaddr?
- What is dstaddr?
- What is nexthop?
- What is input and output interface index?
- What is dPkts?
- What is dOctets?
- What is first and last (uptime of first/last packet)?
- What is srcport and dstport?
- What is tcp_flags?
- What is prot (protocol)?
- What is tos?
- What is src_as and dst_as?
- What is src_mask and dst_mask?
- How does NetFlow v9 differ structurally from v5?
- What is a template flowset in v9?
- What is a data flowset in v9?
- What is an options template in v9?
- Describe the IPFIX message format.
- How does IPFIX extend NetFlow v9?

## Why Questions

- Why use NetFlow instead of packet capture (pcap)?
- Why does NetFlow use UDP for export?
- Why does NetFlow use sampling instead of capturing every packet?
- Why are active and inactive timeouts both needed?
- Why did NetFlow v9 introduce templates instead of fixed record formats?
- Why use IPFIX over NetFlow v9?
- Why aggregate flows at the exporter rather than sending raw packet data?
- Why might a NetFlow collector receive duplicate or out-of-order records?

## Coding Questions

- Parse a NetFlow v5 packet from a raw byte buffer.
- Implement a NetFlow v5 record decoder.
- Implement a NetFlow v5 header parser.
- Aggregate flow records by source IP.
- Aggregate flow records by destination port.
- Implement a flow expiry engine using active and inactive timeouts.
- Implement a NetFlow v9 template cache.
- Implement a NetFlow v9 data record decoder using a cached template.
- Write a NetFlow collector that listens on UDP and stores records.
- Compute bytes-per-second and packets-per-second from flow records.
- Detect top talkers from a set of flow records.

## Edge Cases

- What happens when the NetFlow collector receives a data record before the template record?
- What happens when a flow record arrives out of order at the collector?
- How do you handle UDP packet loss in NetFlow export?
- What happens when the flow_sequence counter rolls over?
- How do you handle a flow that spans multiple export packets?
- What happens when two flows have the same five-tuple due to NAT?
- How do you handle duplicate flow records at the collector?
- What happens when sampling is enabled and you need to estimate true traffic volume?
- How do you handle flows that are never expired (long-lived TCP sessions)?

## Debugging Scenarios

- A NetFlow exporter stops sending records. How do you investigate?
- The NetFlow collector shows a gap in flow data. What could cause it?
- Flow byte counts seem lower than expected. What might be wrong?
- The collector receives template records but no data records. Why?
- NetFlow records show incorrect timestamps. What fields do you check?
- High CPU on the exporting router correlates with NetFlow being enabled. How do you diagnose?

## System Design Questions

- Design a NetFlow collector that handles 1 million flow records per second.
- Design a distributed NetFlow aggregation pipeline.
- Design a NetFlow-based anomaly detection system.
- Design a storage backend for long-term NetFlow retention and fast querying.
- Design a NetFlow visualization dashboard.

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [UDP](../udp/questions.md)
- [Splunk](../splunk/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)
