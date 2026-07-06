# Networking Fundamentals

## Overview

Networking fundamentals cover the core concepts that underpin all network communication: the OSI and TCP/IP models, addressing, routing, switching, and the protocols that make the Internet work. This is the foundation required to understand every other topic in this repository.

## Conceptual Questions

- What is a protocol stack? 
A collection of networking protocols in layers that work together to send and receive data with each protocol responsible for a specific job.

- What is the TCP/IP model?
A four layer networking architecture that describes how dat amoves from an application on one device to another across a network.

- What are the four layers of the TCP/IP model?

Application -> provides network services to applications such as DHCP, DNS, HTTP, SSH. *what service do i want?*. application protocols define message rules and meaning. 
Transport   -> provides end to end communication between applications, like TCP for reliable delivery, or UDP for fast connectionless delivery. *how should it be delivered*. 
Internet    -> Handles logical addressing and routing of packets between networks via IP or ICMP. *where is it going*. IP is responsible for getgting a packet from one machine to another across multiple networks; gives every device a IP, routes packets across routers,a nd breaks network into source -> destination. Logical addressing is an address that is assigned in software and can change depending on the network.
Link        -> handles comuniocation over the local network and physical medium, e.g. ethernet or wifi *how do i send it on this local network*. Defines ohw bits are structured into frames, how devices share the medium, how mac addresses are used, etc. At this layer IP is irrelevant and MAC addresses are. Essentially ,link layer = delivery inside a single network.

- What is the OSI model?
- What are the seven layers of the OSI model?
- How does the TCP/IP model map to the OSI model?
- What is the physical layer?
- What is the data link layer?
- What is the network layer?
- What is the transport layer?
- What is the session layer?
- What is the presentation layer?
- What is the application layer?
- What is a protocol?
- What is encapsulation?
- What is decapsulation?
- What is a PDU (Protocol Data Unit)?
- What is a frame (Layer 2 PDU)?
- What is a packet (Layer 3 PDU)?
- What is a segment (Layer 4 PDU)?
- What is an IP address?
- What is IPv4?
- What is IPv6?
- What is CIDR notation?
- What is a subnet mask?
- What is a subnet?
- What is subnetting?
- What is a broadcast address?
- What is a network address?
- What is VLSM (Variable Length Subnet Masking)?
- What is a MAC address?
- What is ARP (Address Resolution Protocol)?
- How does ARP work?
- What is a gratuitous ARP?
- What is ARP spoofing?
- What is an ARP table?
- What is a routing table?
- What is a default gateway?
- What is a static route?
- What is a dynamic route?
- What is a routing protocol?
- What is an IGP (Interior Gateway Protocol)?
- What is an EGP (Exterior Gateway Protocol)?
- What is ICMP?
- What is an ICMP echo request (ping)?
- What is an ICMP echo reply (pong)?
- What is an ICMP unreachable?
- What is an ICMP redirect?
- What is TTL (Time to Live)?
- What happens when TTL reaches zero?
- What is traceroute and how does it use TTL?
- What is NAT (Network Address Translation)?
- What is SNAT?
- What is DNAT?
- What is PAT (Port Address Translation)?
- What is a firewall?
- What is a stateful firewall?
- What is a stateless firewall?
- What is a DMZ?
- What is a VLAN?
- What is 802.1Q VLAN tagging?
- What is a trunk port?
- What is an access port?
- What is STP (Spanning Tree Protocol)?
- What is RSTP (Rapid Spanning Tree Protocol)?
- What is a switch?
- What is a router?
- What is a hub?
- What is a bridge?
- What is MTU (Maximum Transmission Unit)?
- What is MSS (Maximum Segment Size)?
- What is the relationship between MTU and MSS?
- What is fragmentation?
- What is the Don't Fragment (DF) bit?
- What is PMTUD (Path MTU Discovery)?
- What is a socket?
- What is a port?
- What is an ephemeral port?
- What is a well-known port?
- What is the TCP three-way handshake?
- What is the SYN flag?
- What is the SYN-ACK?
- What is the ACK flag?
- What is the FIN flag?
- What is the RST flag?
- What is the four-way TCP close?
- What is the TIME_WAIT state?
- What is TCP sequence number?
- What is TCP acknowledgment number?
- What is TCP flow control?
- What is the TCP receive window?
- What is TCP congestion control?
- What is slow start?
- What is congestion avoidance?
- What is fast retransmit?
- What is fast recovery?
- What is CWND (congestion window)?
- What is SSTHRESH?
- What is Cubic TCP?
- What is BBR (Bottleneck Bandwidth and Round-trip time)?
- What is the TLS handshake?
- What is TLS 1.2?
- What is TLS 1.3?
- What is a certificate?
- What is a CA (Certificate Authority)?
- What is SNI (Server Name Indication)?
- What is OCSP stapling?
- What is HSTS?
- What is DNS over HTTPS (DoH)?
- What is DNS over TLS (DoT)?

## Deep Dive Questions

- Describe the IPv4 header fields.
- What is the Version field?
- What is the IHL (Internet Header Length) field?
- What is the DSCP field?
- What is the ECN field?
- What is the Total Length field?
- What is the Identification field?
- What are the Flags field bits (Reserved, DF, MF)?
- What is the Fragment Offset field?
- What is the TTL field?
- What is the Protocol field?
- What is the Header Checksum field?
- What are the Source and Destination Address fields?
- What is the Options field?
- Describe the TCP header fields.
- What is the Source Port and Destination Port?
- What is the Sequence Number?
- What is the Acknowledgment Number?
- What is the Data Offset field?
- What are the reserved bits?
- What are the control bits (URG, ACK, PSH, RST, SYN, FIN)?
- What is the Window Size field?
- What is the Checksum field?
- What is the Urgent Pointer field?
- What are TCP Options?
- What is the MSS option?
- What is the Window Scale option?
- What is the SACK (Selective Acknowledgment) option?
- What is the Timestamp option?
- What is the NOP option?
- Describe the Ethernet frame format.
- What is the preamble?
- What is the SFD (Start Frame Delimiter)?
- What is the destination MAC address?
- What is the source MAC address?
- What is the EtherType field?
- What is the payload?
- What is the FCS (Frame Check Sequence)?
- Describe the IPv4 fragmentation process.
- What is the ARP request/reply exchange in detail?
- How does a router forward a packet?
- What is longest-prefix match (LPM)?
- What is a FIB (Forwarding Information Base)?
- What is a RIB (Routing Information Base)?
- What is the difference between FIB and RIB?
- Describe the TLS 1.3 handshake step by step.
- What is the Client Hello?
- What is the Server Hello?
- What is the key share?
- What is the Encrypted Extensions message?
- What is the Certificate and CertificateVerify message?
- What is the Finished message?
- What is 0-RTT in TLS 1.3?

## Why Questions

- Why does the OSI model have seven layers?
- Why does TCP/IP have fewer layers than OSI?
- Why does TCP use a three-way handshake?
- Why does TCP use a four-way close instead of two?
- Why does TIME_WAIT last 2*MSL?
- Why use MSS instead of MTU?
- Why does IP use TTL?
- Why does NAT break end-to-end connectivity?
- Why does TLS 1.3 remove the RSA key exchange?
- Why does TLS 1.3 only support AEAD cipher suites?
- Why does IPv6 remove fragmentation from routers?
- Why does ARP only work on the local subnet?
- Why does routing require a default gateway?
- Why does STP exist?
- Why does TCP use sequence numbers instead of message numbers?
- Why does TCP congestion control use exponential slow start?

## Coding Questions

- Implement a raw socket that sends and receives IPv4 packets.
- Implement an ARP request sender.
- Implement a packet sniffer using a raw socket or pcap.
- Implement a traceroute using UDP probes and ICMP TTL exceeded responses.
- Implement a ping using ICMP echo request/reply.
- Implement a subnet calculator that computes network, broadcast, and host range.
- Implement longest-prefix match for a routing table.
- Implement a NAT table (source IP/port translation).
- Implement a simple TCP state machine.
- Parse a raw Ethernet frame and extract the IP and TCP headers.

## Edge Cases

- What happens when two hosts have the same IP on the same subnet?
- What happens when ARP cache is stale and the MAC has changed?
- What happens when TTL is 1 and the packet must cross another router?
- What happens when MTU mismatches cause fragmentation that is silently dropped?
- What happens when TCP SYN cookies are used and options are lost?
- What happens when NAT mappings expire while a connection is idle?
- What happens when the TLS certificate is expired?
- What happens when SNI is missing and a server hosts multiple TLS certificates?

## Debugging Scenarios

- A host cannot ping its default gateway. How do you debug?
- DNS resolves but connection is refused. How do you investigate?
- TCP connection is established but data transfer is slow. What do you check?
- PMTUD is broken and large packets are silently dropped. How do you detect this?
- ARP is flooding the network. What is the cause?
- TLS handshake fails with a certificate error. How do you diagnose?
- A firewall is silently dropping packets without ICMP unreachable. How do you detect it?

## System Design Questions

- Design a network monitoring system that tracks packet loss and latency across the network.
- Design a BGP route analyzer that monitors the global routing table for anomalies.
- Design a TLS inspection proxy.
- Design a software-defined networking (SDN) controller.

## Related Topics

- [DNS](../dns/questions.md)
- [DHCP](../dhcp/questions.md)
- [BGP](../bgp/questions.md)
- [OSPF](../ospf/questions.md)
- [UDP](../udp/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [Debugging](../debugging/questions.md)
