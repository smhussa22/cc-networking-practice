# System Design

## Overview

System design interviews require designing scalable, reliable, and maintainable distributed systems under constraints. This section covers the full range of system design questions relevant to networking, infrastructure, and backend engineering, including voice/video, data pipelines, monitoring, and distributed storage.

## Conceptual Questions

- What is horizontal scaling?
- What is vertical scaling?
- What is a load balancer?
- What is a reverse proxy?
- What is a CDN (Content Delivery Network)?
- What is a cache?
- What is cache eviction?
- What is LRU (Least Recently Used) eviction?
- What is LFU (Least Frequently Used) eviction?
- What is cache invalidation?
- What is cache stampede?
- What is a database replica?
- What is read/write splitting?
- What is database sharding?
- What is consistent hashing?
- What is a virtual node in consistent hashing?
- What is a message queue?
- What is a pub/sub system?
- What is eventual consistency?
- What is strong consistency?
- What is the CAP theorem?
- What is the PACELC theorem?
- What is availability?
- What is partition tolerance?
- What is consistency (in CAP)?
- What is a service mesh?
- What is a sidecar proxy?
- What is rate limiting?
- What is a token bucket algorithm?
- What is a leaky bucket algorithm?
- What is circuit breaking?
- What is a health check?
- What is a heartbeat?
- What is service discovery?
- What is a leader election?
- What is the Raft consensus algorithm?
- What is the Paxos consensus algorithm?
- What is idempotency?
- What is at-least-once delivery?
- What is at-most-once delivery?
- What is exactly-once delivery?
- What is a distributed transaction?
- What is two-phase commit (2PC)?
- What is saga pattern?
- What is the outbox pattern?
- What is CQRS (Command Query Responsibility Segregation)?
- What is event sourcing?
- What is a write-ahead log (WAL)?
- What is a bloom filter?
- What is a count-min sketch?
- What is a HyperLogLog?
- What is a time-series database?
- What is an inverted index?
- What is a merkle tree?
- What is vector clock?
- What is a distributed lock?
- What is a fencing token?

## System Design Questions

### Real-Time Communication

- Design Discord voice chat.
- Design Slack.
- Design a WebSocket-based chat system that scales to 10 million concurrent users.
- Design a push notification service.
- Design a live sports score feed.
- Design a collaborative document editor (Google Docs).
- Design a video conferencing system.

### Networking and Monitoring

- Design a NetFlow collector that processes 1 million flow records per second.
- Design a DHCP server.
- Design a DNS resolver.
- Design a distributed network monitoring system.
- Design Splunk ingestion (500GB/day, full-text search, alerting).
- Design a metrics pipeline (collection, aggregation, storage, visualization).
- Design an alert engine that processes events and fires notifications.
- Design a distributed tracing backend (like Jaeger or Zipkin).
- Design a distributed logger.
- Design a log aggregation pipeline.
- Design a monitoring system for 10,000 network devices using SNMP.
- Design a BGP route monitoring system that detects hijacks.

### Data and Storage

- Design a distributed key-value store.
- Design a time-series database.
- Design a distributed file system.
- Design a distributed object store (like S3).
- Design a distributed SQL database.
- Design a search engine.
- Design a URL shortener.
- Design a distributed cache.
- Design a rate limiter.
- Design an LRU cache.
- Design a consistent hashing ring.

### Infrastructure and Platform

- Design a Kubernetes monitoring stack.
- Design service discovery for a microservices architecture.
- Design a zero-downtime deployment system.
- Design a distributed job scheduler.
- Design a distributed cron system.
- Design an API gateway.
- Design a feature flag system.
- Design a configuration management system.
- Design a secret management system.
- Design a distributed rate limiter.
- Design a multi-tenant SaaS backend.

### Media and Streaming

- Design a video streaming platform (Netflix-like).
- Design an audio conferencing server with jitter buffer and PLC.
- Design a live video transcoding pipeline.
- Design a content delivery network (CDN).

## Deep Dive Questions

- When designing a system for 1 million RPS, what bottlenecks do you identify first?
- How do you estimate storage requirements for a system?
- How do you estimate bandwidth requirements?
- How do you estimate QPS (queries per second) from DAU and usage patterns?
- What is back-of-the-envelope estimation?
- How do you design a system for 99.99% availability?
- What is the impact of network latency on system design?
- How do you handle hot partitions in a sharded database?
- How do you design for graceful degradation?
- How do you handle thundering herd after a cache miss?
- How do you design a system that is both consistent and available during a partition?
- How do you design for idempotency in a distributed system?
- How do you avoid the double-spend problem in distributed payments?
- What is the two-generals problem?
- What is the Byzantine generals problem?
- What is a split-brain scenario?
- How do you prevent split-brain?
- What is a fencing token and how does it prevent split-brain?

## Why Questions

- Why use Kafka instead of a database as a message queue?
- Why use ScyllaDB instead of PostgreSQL for high-throughput writes?
- Why use a CDN instead of serving all traffic from origin?
- Why use consistent hashing instead of modulo for sharding?
- Why use eventual consistency instead of strong consistency for global systems?
- Why is two-phase commit not used in modern distributed systems?
- Why use saga instead of 2PC for distributed transactions?
- Why use event sourcing instead of mutable state?
- Why use CQRS?
- Why use a bloom filter for a key-value store?
- Why use circuit breaking?
- Why use a sidecar proxy instead of a library for service mesh?

## Edge Cases

- What happens when the leader in a Raft cluster fails?
- What happens when a message queue consumer falls behind?
- What happens when consistent hashing adds a new node?
- What happens when consistent hashing removes a node?
- What happens when a cache is cold (cache miss storm)?
- What happens when a distributed lock holder crashes before releasing the lock?
- What happens when a two-phase commit coordinator fails?
- What happens when the outbox pattern's relay fails?
- What happens when two services try to acquire the same distributed lock simultaneously?

## Debugging Scenarios

- A service is returning 503s under high load. How do you diagnose?
- A distributed system has high tail latency (p99 is 10x p50). How do you investigate?
- A Kafka consumer group has lag growing unboundedly. How do you debug?
- A distributed cache has a low hit rate. How do you investigate?
- A system experiences cascading failures. How do you identify the root cause?
- A database replica is falling behind the primary. How do you diagnose?
- A rate limiter is not working correctly across multiple instances. Why?

## Related Topics

- [Kafka](../kafka/questions.md)
- [ScyllaDB](../scylladb/questions.md)
- [PostgreSQL](../postgresql/questions.md)
- [Kubernetes](../kubernetes/questions.md)
- [Splunk](../splunk/questions.md)
- [NetFlow](../netflow/questions.md)
- [RTP](../rtp/questions.md)
- [Jitter Buffer](../jitter-buffer/questions.md)
- [Debugging](../debugging/questions.md)
