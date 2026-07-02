# Debugging

## Overview

Debugging in networking and systems engineering requires a systematic methodology: observe symptoms, form hypotheses, isolate variables, and verify fixes. This section covers debugging scenarios across the full stack — from physical and network layer issues to application and distributed system failures.

## Conceptual Questions

- What is a systematic debugging methodology?
- What is the divide-and-conquer approach to debugging?
- What is binary search debugging?
- What is hypothesis-driven debugging?
- What is rubber duck debugging?
- What is a minimum reproducible example (MRE)?
- What is an oscillating failure vs a consistent failure?
- What is a Heisenbug?
- What is a timing-related bug?
- What is a race condition?
- What tools do you use to debug network issues?
- What is `ping`?
- What is `traceroute`?
- What is `tcpdump`?
- What is Wireshark?
- What is `ss`?
- What is `netstat`?
- What is `ip route`?
- What is `ip addr`?
- What is `arp -n`?
- What is `nslookup`?
- What is `dig`?
- What is `curl -v`?
- What is `strace`?
- What is `ltrace`?
- What is `gdb`?
- What is `perf`?
- What is `pmap`?
- What is `lsof`?
- What is `nsenter`?
- What is `kubectl exec`?
- What is `kubectl describe`?
- What is `kubectl logs`?
- What is `kubectl events`?

## Network Debugging Scenarios

- Wireshark shows TCP retransmissions. Walk through your investigation.
- DNS lookup takes 5 seconds. How do you debug it?
- Packet loss jumps to 30% on a specific path. How do you investigate?
- A host cannot ping its default gateway. What do you check?
- DNS resolves but connection is refused. How do you investigate?
- A TCP connection establishes but data transfer is extremely slow. What do you check?
- MTU mismatch is suspected. How do you confirm and fix it?
- ARP table shows no entry for a known host. How do you investigate?
- A firewall is silently dropping packets (no ICMP unreachable). How do you detect it?
- BGP adjacency keeps flapping. What do you investigate?
- DHCP clients are not getting leases. How do you debug?
- NetFlow exporter stops sending data. How do you investigate?
- OSPF adjacency forms and drops repeatedly. What do you check?
- SNMP polls time out from the management server. What do you investigate?

## Application Debugging Scenarios

- A service returns HTTP 502 Bad Gateway. What does that mean and how do you investigate?
- A service returns HTTP 503 Service Unavailable. What are the causes?
- A service returns HTTP 504 Gateway Timeout. What do you check?
- An API is slow for some users but fast for others. How do you approach this?
- A TLS handshake is failing. How do you diagnose?
- JWT validation is failing intermittently. What do you check?
- OAuth flow is redirecting users in an infinite loop. Why?
- A WebSocket connection drops after 60 seconds. How do you debug?
- A Kafka consumer group has growing lag. How do you investigate?
- A ScyllaDB read is slow for a specific partition. How do you diagnose?
- PostgreSQL query performance degrades over time. What do you check?
- PostgreSQL replication lag is growing. How do you investigate?

## Infrastructure Debugging Scenarios

- A Kubernetes pod is in CrashLoopBackOff. Walk through your investigation.
- A Kubernetes pod is Pending and never schedules. What do you check?
- A Kubernetes deployment rollout is stuck. How do you investigate?
- A Kubernetes pod cannot reach another pod across nodes. How do you diagnose?
- An EKS node is NotReady. How do you investigate?
- An ALB returns 502 for all requests. How do you investigate?
- A Lambda function is timing out. How do you investigate?
- An EC2 instance cannot reach the Internet from a private subnet. How do you debug?
- An IAM role is returning AccessDenied errors. How do you diagnose?
- An Auto Scaling Group is not scaling despite high CPU. How do you investigate?
- CloudWatch metrics are missing for an EC2 instance. Why?

## Systems Debugging Scenarios

- A C++ program crashes with a segfault. How do you find the root cause?
- A multithreaded program deadlocks. How do you diagnose it?
- A program has a memory leak. How do you find it?
- A multithreaded program has a data race. How do you detect it?
- A lock-free queue produces incorrect results under concurrency. How do you debug?
- A server's CPU is pegged at 100% with unknown cause. How do you diagnose?
- A process is consuming unexpectedly large amounts of memory. How do you investigate?
- A program is making unexpected system calls. How do you detect them?
- Disk I/O is saturated on a server. How do you identify the cause?
- A program is running slower than expected. How do you profile it?

## Real-Time Media Debugging Scenarios

- Audio on a VoIP call is choppy. What do you check?
- Video is freezing intermittently. How do you diagnose?
- RTCP receiver reports show high jitter. What does that imply?
- RTCP reports show growing cumulative packet loss. How do you investigate?
- A jitter buffer is growing unboundedly over a long call. Why?
- PLC is being invoked frequently even though packet loss is low. What could cause this?

## Debugging Tools Reference

- How do you use `tcpdump` to capture traffic on a specific interface and port?
- How do you use `tcpdump` to capture and write to a pcap file?
- How do you filter Wireshark by TCP stream?
- How do you use `ss` to show all listening ports?
- How do you use `ss` to show socket statistics for a specific process?
- How do you use `strace` to trace system calls of a running process?
- How do you use `perf stat` to measure CPU performance counters?
- How do you use `perf record` and `perf report` to profile CPU usage?
- How do you use `gdb` to attach to a running process?
- How do you use `gdb` to get a backtrace after a crash?
- How do you use `lsof` to find open file descriptors of a process?
- How do you use `nsenter` to debug a container's network namespace?
- How do you use `kubectl exec` to run a command inside a pod?
- How do you use `kubectl port-forward` to access a service locally?
- How do you read a `tcpdump` capture to identify TCP retransmissions?
- How do you identify a PMTUD blackhole using Wireshark?
- How do you identify connection resets (RST) in Wireshark?
- How do you identify a SYN flood in Wireshark?

## Why Questions

- Why start debugging at Layer 1 and work up instead of starting at the application layer?
- Why is the divide-and-conquer approach effective for network debugging?
- Why is it important to establish a baseline before debugging performance issues?
- Why do timing-related bugs disappear when you add logging?
- Why is a minimum reproducible example valuable?
- Why should you verify your fix actually solves the problem instead of just testing if the symptom is gone?

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [Kubernetes](../kubernetes/questions.md)
- [BGP](../bgp/questions.md)
- [DHCP](../dhcp/questions.md)
- [DNS](../dns/questions.md)
- [Kafka](../kafka/questions.md)
- [PostgreSQL](../postgresql/questions.md)
- [CPP](../cpp/questions.md)
