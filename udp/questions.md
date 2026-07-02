# UDP

## Overview

User Datagram Protocol (UDP) is a connectionless, unreliable transport-layer protocol (IP protocol 17). It provides no guarantees of delivery, ordering, or duplicate elimination. UDP is used when low latency is more important than reliability, or when the application layer implements its own reliability mechanisms.

## Conceptual Questions

- What is UDP?
- What problem does UDP solve?
- What is the difference between UDP and TCP?
- What does connectionless mean?
- What does unreliable mean in the context of UDP?
- What is a datagram?
- What is the maximum size of a UDP datagram?
- What is fragmentation?
- What is MTU?
- What is Path MTU Discovery (PMTUD)?
- Why does UDP not guarantee ordering?
- Why does UDP not guarantee delivery?
- Why does UDP not detect or recover from duplication?
- What is the UDP checksum?
- Is the UDP checksum mandatory?
- What does the UDP checksum cover (pseudo-header)?
- What are the socket APIs for UDP?
- What is `sendto()`?
- What is `recvfrom()`?
- What is `connect()` on a UDP socket?
- What is a connected UDP socket?
- What is a broadcast address and how does UDP use it?
- What is multicast and how does UDP use it?
- What is anycast?
- What protocols are built on top of UDP?
- When should you choose UDP over TCP?
- What is QUIC and how does it relate to UDP?

## Deep Dive Questions

- Describe the UDP header format.
- What is the Source Port field?
- What is the Destination Port field?
- What is the Length field?
- What is the Checksum field?
- How is the UDP pseudo-header constructed for checksum calculation?
- What fields from the IP header are included in the UDP pseudo-header?
- How does UDP fragmentation work at the IP layer?
- What is the Fragment Offset field in IP?
- What is the More Fragments (MF) bit?
- What happens when a fragment is lost?
- Why is fragmentation harmful to UDP performance?
- What is the `SO_RCVBUF` socket option?
- What is the `SO_SNDBUF` socket option?
- What happens when the receive buffer overflows?
- What is `SO_REUSEADDR`?
- What is `SO_REUSEPORT`?
- What is non-blocking I/O on a UDP socket?
- How does `select()` work with UDP sockets?
- How does `poll()` work with UDP sockets?
- How does `epoll()` work with UDP sockets?
- What is the difference between edge-triggered and level-triggered epoll?
- What is `recvmmsg()` and why is it used for high-performance UDP?
- What is `sendmmsg()`?
- What is `MSG_DONTWAIT`?
- What is `MSG_WAITALL`?
- What is `MSG_TRUNC`?

## Why Questions

- Why use UDP instead of TCP for video streaming?
- Why use UDP for DNS?
- Why use UDP for DHCP?
- Why does RTP use UDP?
- Why does NetFlow use UDP for export?
- Why doesn't UDP have flow control?
- Why doesn't UDP have congestion control?
- Why is UDP preferred for gaming?
- Why is implementing reliability over UDP sometimes better than using TCP?
- Why does UDP not have a connection establishment handshake?
- Why must applications built on UDP handle their own packet loss?

## Coding Questions

- Implement a UDP sender using BSD sockets.
- Implement a UDP receiver using BSD sockets.
- Implement a simple UDP-based chat application.
- Implement a UDP packet parser.
- Implement a UDP echo server.
- Implement reliability over UDP: sequence numbers, ACKs, retransmission.
- Implement a sliding window protocol over UDP.
- Implement a UDP receiver with `epoll`.
- Implement a UDP server using `recvmmsg` for batched receives.
- Implement Path MTU Discovery for a UDP sender.
- Implement a UDP-based heartbeat mechanism.
- Implement a simple stop-and-wait ARQ over UDP.
- Implement a UDP multicast sender.
- Implement a UDP multicast receiver.

## Edge Cases

- What happens when a UDP packet exceeds the MTU and IP fragmentation occurs?
- What happens when one IP fragment is lost?
- What happens when a UDP datagram is larger than the receive buffer?
- What happens when two processes bind to the same UDP port without SO_REUSEPORT?
- What happens when the network reorders UDP packets?
- What happens when a UDP packet is duplicated in the network?
- What happens when the UDP checksum is disabled and corruption occurs?
- What happens on a path that silently drops large packets (PMTUD blackhole)?
- How do you detect and recover from PMTUD blackholes?
- What happens when a UDP receiver is too slow and its buffer overflows?

## Debugging Scenarios

- Packet loss jumps to 30% on a UDP flow. How do you investigate?
- UDP latency spikes intermittently. What could cause this?
- A UDP receiver drops packets even though the sender is slow. Why?
- A UDP server stops receiving data after some time. What do you check?
- `recvfrom()` returns `EWOULDBLOCK` unexpectedly. Why?
- UDP throughput is much lower than expected. What do you investigate?
- Wireshark shows retransmissions on UDP. How is that possible and what does it mean?

## System Design Questions

- Design a reliable file transfer protocol over UDP.
- Design a UDP-based real-time multiplayer game network layer.
- Design a high-throughput UDP log shipping system.
- Design a multicast-based market data distribution system.
- Design a UDP-based media streaming protocol.

## Related Topics

- [RTP](../rtp/questions.md)
- [RFC6298](../rfc6298/questions.md)
- [Jitter Buffer](../jitter-buffer/questions.md)
- [DNS](../dns/questions.md)
- [DHCP](../dhcp/questions.md)
- [NetFlow](../netflow/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
