# Kafka

## Overview

Apache Kafka is a distributed event streaming platform designed for high-throughput, fault-tolerant, real-time data pipelines. Kafka organizes messages into topics divided into partitions, stores them durably on disk, and supports both real-time and batch consumption by multiple independent consumer groups.

## Conceptual Questions

- What is Kafka?
- What problem does Kafka solve?
- What is a broker?
- What is a topic?
- What is a partition?
- What is an offset?
- What is a consumer group?
- What is a producer?
- What is a consumer?
- What is the difference between a queue and a log?
- How does Kafka differ from a traditional message queue (RabbitMQ, ActiveMQ)?
- What is a Kafka record (message)?
- What fields does a Kafka record contain?
- What is a record key?
- What is a record value?
- What is a record timestamp?
- What are record headers?
- What is replication in Kafka?
- What is the replication factor?
- What is a leader replica?
- What is a follower replica?
- What is ISR (In-Sync Replicas)?
- What happens when the leader fails?
- What is leader election in Kafka?
- What is ZooKeeper's role in Kafka?
- What is KRaft mode (Kafka without ZooKeeper)?
- What is the `acks` producer configuration?
- What does `acks=0` mean?
- What does `acks=1` mean?
- What does `acks=all` (or `acks=-1`) mean?
- What is `min.insync.replicas`?
- What is idempotent producer?
- What is exactly-once semantics (EOS)?
- What is a Kafka transaction?
- What is `auto.offset.reset`?
- What is `earliest`?
- What is `latest`?
- What is consumer lag?
- What is `__consumer_offsets` topic?
- What is log compaction?
- What is retention policy?
- What is `log.retention.hours`?
- What is `log.retention.bytes`?
- What is Kafka Connect?
- What is Kafka Streams?
- What is ksqlDB?
- What is a Schema Registry?
- What is Avro?
- What is Protobuf support in Kafka?

## Deep Dive Questions

- Describe the Kafka network protocol (Kafka wire protocol).
- What is the structure of a Kafka request?
- What is the structure of a Kafka response?
- What is an API key in the Kafka protocol?
- What are the key Kafka API operations (Produce, Fetch, Metadata, OffsetFetch, etc.)?
- Describe how a producer sends a message.
- What is the producer batch and how does batching improve throughput?
- What is `linger.ms`?
- What is `batch.size`?
- What is `buffer.memory`?
- What is `compression.type`?
- How does the producer partition a record when no key is specified?
- How does the producer partition a record when a key is specified?
- What is sticky partitioning?
- Describe how a consumer fetches messages.
- What is a fetch request?
- What is `fetch.min.bytes`?
- What is `fetch.max.wait.ms`?
- What is `max.poll.records`?
- How does the consumer commit offsets?
- What is auto-commit and what are its risks?
- What is manual offset commit?
- What is the difference between commitSync and commitAsync?
- How does Kafka store data on disk?
- What is a log segment?
- What is an index file?
- What is a time index file?
- How does Kafka achieve low-latency reads using the page cache?
- What is zero-copy (sendfile) and how does Kafka use it?
- Describe the consumer group rebalance protocol.
- What triggers a rebalance?
- What is the group coordinator?
- What is the group leader?
- What is the rebalance protocol (JoinGroup, SyncGroup)?
- What is cooperative (incremental) rebalancing?
- What is static group membership?
- What is `session.timeout.ms`?
- What is `heartbeat.interval.ms`?
- What is `max.poll.interval.ms`?
- How does Kafka ensure ordering within a partition?
- Why can't Kafka guarantee ordering across partitions?
- What is log compaction and how does it work?
- What is the `__consumer_offsets` topic internal structure?
- How does the idempotent producer prevent duplicate messages?
- What is the producer epoch?
- How do Kafka transactions work across multiple partitions and topics?
- What is the two-phase commit used in Kafka transactions?

## Why Questions

- Why use Kafka instead of RabbitMQ?
- Why use Kafka instead of a database as a message queue?
- Why does Kafka store messages on disk instead of in memory?
- Why does Kafka use sequential I/O and how does that affect performance?
- Why does Kafka use the page cache instead of its own memory management?
- Why does partitioning enable parallelism?
- Why does Kafka not support per-message acknowledgment like RabbitMQ?
- Why does `acks=all` not guarantee exactly-once delivery on its own?
- Why is consumer group rebalancing disruptive?
- Why use log compaction instead of retention-based deletion?
- Why use a schema registry?
- Why was ZooKeeper removed in favor of KRaft?

## Coding Questions

- Implement a Kafka producer that sends JSON messages to a topic.
- Implement a Kafka consumer that reads from a topic and commits offsets manually.
- Implement a consumer that handles rebalance events.
- Implement an idempotent producer.
- Implement a transactional producer that writes to multiple topics atomically.
- Implement a consumer that resumes from the last committed offset after restart.
- Implement a dead letter queue pattern in Kafka.
- Implement lag monitoring for a consumer group.
- Implement a Kafka Streams word count application.
- Implement a producer that uses a custom partitioner.
- Implement a consumer that reads from a specific offset.

## Edge Cases

- What happens when all replicas in the ISR fail?
- What happens when `min.insync.replicas` is greater than the number of available replicas?
- What happens when a consumer poll loop takes longer than `max.poll.interval.ms`?
- What happens when the leader fails during a produce request with `acks=all`?
- What happens when a consumer crashes mid-processing before committing offsets?
- What happens when log compaction removes a message a consumer has not yet read?
- What happens when two consumers in different groups read the same partition at different rates?
- What happens when the `__consumer_offsets` topic loses replicas?
- What happens when a transactional producer crashes mid-transaction?
- What happens when a new consumer joins a group with `auto.offset.reset=latest` for the first time?

## Debugging Scenarios

- Consumer lag is growing on a topic. How do you investigate?
- A producer is receiving `NotLeaderForPartitionException`. Why?
- A consumer is being kicked out of the group repeatedly. What is the likely cause?
- Messages are being duplicated in the output. How do you trace the cause?
- Kafka throughput drops suddenly. What do you check?
- A Kafka topic has uneven partition sizes. Why?
- Messages are being delivered out of order. How is this possible?
- A Kafka Connect connector keeps failing. How do you debug it?

## System Design Questions

- Design a Kafka-based event sourcing system.
- Design a metrics ingestion pipeline using Kafka.
- Design a Kafka-based distributed tracing backend.
- Design a Splunk-like log aggregation system using Kafka.
- Design a Kafka consumer that processes messages exactly once and writes to a database.
- Design a multi-datacenter Kafka replication setup (MirrorMaker).
- Design an alert engine that consumes Kafka events and fires notifications.

## Related Topics

- [ScyllaDB](../scylladb/questions.md)
- [PostgreSQL](../postgresql/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)
- [Splunk](../splunk/questions.md)
