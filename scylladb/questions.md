# ScyllaDB

## Overview

ScyllaDB is a high-performance NoSQL database compatible with Apache Cassandra's data model and CQL (Cassandra Query Language). It is written in C++ using the Seastar framework, which provides a shared-nothing, asynchronous I/O architecture. ScyllaDB achieves significantly lower latency and higher throughput than Cassandra on equivalent hardware.

## Conceptual Questions

- What is ScyllaDB?
- What problem does ScyllaDB solve?
- What is the Cassandra Query Language (CQL)?
- How is ScyllaDB compatible with Cassandra?
- What is a keyspace in ScyllaDB?
- What is a table (column family) in ScyllaDB?
- What is a partition key?
- What is a clustering key?
- What is the difference between a partition key and a clustering key?
- What is the primary key in ScyllaDB?
- What is a composite partition key?
- What is a static column?
- What is a collection column (list, set, map)?
- What is a counter column?
- What is a materialized view in ScyllaDB?
- What is a secondary index in ScyllaDB?
- What is the replication factor?
- What is a replication strategy?
- What is SimpleStrategy?
- What is NetworkTopologyStrategy?
- What is eventual consistency?
- What is tunable consistency?
- What is a consistency level?
- What is `ANY` consistency?
- What is `ONE` consistency?
- What is `QUORUM` consistency?
- What is `ALL` consistency?
- What is `LOCAL_QUORUM` consistency?
- What is `EACH_QUORUM` consistency?
- What is hinted handoff?
- What is a read repair?
- What is anti-entropy repair?
- What is `nodetool repair`?
- What is a gossip protocol?
- What is the consistent hashing ring?
- What is a virtual node (vnode)?
- What is the token range?
- What is a coordinator node?
- What is a seed node?
- What is a compaction strategy?
- What is STCS (Size-Tiered Compaction Strategy)?
- What is LCS (Leveled Compaction Strategy)?
- What is TWCS (Time-Window Compaction Strategy)?
- What is the Seastar framework?
- What is the shared-nothing architecture?
- What is the shard-per-core model?
- What is write amplification?
- What is read amplification?
- What is space amplification?

## Deep Dive Questions

- Describe the ScyllaDB write path.
- What is a commit log (CommitLog)?
- What is a memtable?
- What is an SSTable (Sorted String Table)?
- How does a write go from client to CommitLog to memtable to SSTable?
- What is compaction and why is it necessary?
- Describe the ScyllaDB read path.
- What is the row cache?
- What is the key cache?
- What is a bloom filter and how is it used in read path optimization?
- What is a tombstone?
- Why do tombstones cause read performance problems?
- What is `gc_grace_seconds`?
- What is the risk of deleting data without proper repair?
- What is a partition tombstone versus a row tombstone?
- How does ScyllaDB handle concurrent reads and writes (MVCC vs. last-write-wins)?
- What is lightweight transactions (LWT / Compare-and-Set)?
- What is the Paxos protocol and how is it used in LWT?
- What is the difference between LWT and regular writes?
- How does ScyllaDB's consistent hashing map a partition key to a node?
- What is the Murmur3 partitioner?
- How does a coordinator node route a request to the correct replica?
- What is the difference between a local and remote request in a multi-DC setup?
- What is snitching in ScyllaDB (endpoint snitch)?
- What is the GossipingPropertyFileSnitch?
- What is the EC2Snitch?
- How does compaction affect read and write latency?
- What is SSTables and how are they immutable?
- What is a bloom filter false positive rate and how does it affect reads?
- How does ScyllaDB handle schema changes?
- What is schema agreement?
- What is the Seastar task scheduler and how does it avoid context switching?
- What is io_uring and does ScyllaDB support it?
- What is the difference between ScyllaDB's shard-per-core model and Cassandra's threading model?

## Why Questions

- Why use ScyllaDB instead of Cassandra?
- Why use ScyllaDB instead of PostgreSQL for high-throughput workloads?
- Why use ScyllaDB instead of Redis?
- Why does ScyllaDB use a shared-nothing architecture?
- Why does ScyllaDB use C++ instead of Java (like Cassandra)?
- Why is the partition key so important to ScyllaDB performance?
- Why must you model your data around your queries in ScyllaDB?
- Why is tunable consistency powerful but also dangerous?
- Why does ScyllaDB use eventual consistency instead of strong consistency?
- Why are tombstones a problem in ScyllaDB?
- Why does repair exist and when should you run it?
- Why use TWCS for time-series data?
- Why does LWT have higher latency than regular writes?

## Coding Questions

- Write a CQL table schema for a time-series sensor data workload.
- Write a CQL query that reads the latest N events for a given device.
- Write a CQL INSERT with a TTL.
- Write a CQL lightweight transaction (INSERT IF NOT EXISTS).
- Write a CQL batch statement.
- Write a CQL materialized view definition.
- Write a data model for a user activity feed with ScyllaDB.
- Implement a ScyllaDB client in Python or Go that retries on timeouts.
- Implement a token-aware driver query.
- Design a schema that avoids hotspots on a single partition.

## Edge Cases

- What happens when a partition grows to millions of rows?
- What happens when tombstone accumulation exceeds the tombstone warning threshold?
- What happens when `gc_grace_seconds` expires before repair is run?
- What happens when a node goes down and comes back up with stale data?
- What happens when the replication factor is greater than the number of nodes?
- What happens when a `QUORUM` write fails because not enough replicas are available?
- What happens when a bloom filter returns a false positive?
- What happens when compaction cannot keep up with write throughput?
- What happens when a schema migration is not fully propagated before a write?

## Debugging Scenarios

- Read latency is high but write latency is normal. What do you check?
- A specific partition is experiencing hotspot behavior. How do you identify it?
- A `nodetool repair` is taking too long. What could be the cause?
- Tombstone warnings are appearing in logs. How do you address them?
- ScyllaDB is using more disk than expected. What is the likely cause?
- Consistency level `QUORUM` reads are returning stale data. How is that possible?
- A node is showing as `DOWN` in `nodetool status`. How do you investigate?

## System Design Questions

- Design a time-series data store using ScyllaDB.
- Design a user session store using ScyllaDB.
- Design a leaderboard system using ScyllaDB.
- Design a multi-DC ScyllaDB deployment with low-latency local reads.
- Design a data pipeline that writes to ScyllaDB from Kafka.

## Related Topics

- [Kafka](../kafka/questions.md)
- [PostgreSQL](../postgresql/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)
