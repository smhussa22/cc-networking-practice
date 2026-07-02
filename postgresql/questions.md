# PostgreSQL

## Overview

PostgreSQL is an open-source object-relational database system known for its standards compliance, extensibility, and support for advanced features including MVCC, full ACID transactions, complex queries, and a rich type system.

## Conceptual Questions

- What is PostgreSQL?
- What is ACID?
- What is Atomicity?
- What is Consistency?
- What is Isolation?
- What is Durability?
- What is MVCC (Multi-Version Concurrency Control)?
- What is a transaction?
- What is a transaction isolation level?
- What are the four standard isolation levels?
- What is Read Uncommitted?
- What is Read Committed?
- What is Repeatable Read?
- What is Serializable?
- What is a dirty read?
- What is a non-repeatable read?
- What is a phantom read?
- What is a serialization anomaly?
- What is an index?
- What is a B-tree index?
- What is a hash index?
- What is a GiST index?
- What is a GIN index?
- What is a BRIN index?
- When should you use each index type?
- What is a partial index?
- What is an expression index?
- What is a covering index?
- What is a foreign key?
- What is a primary key?
- What is a unique constraint?
- What is a check constraint?
- What is a NOT NULL constraint?
- What is a sequence?
- What is SERIAL?
- What is BIGSERIAL?
- What is IDENTITY column?
- What is a view?
- What is a materialized view?
- What is a CTE (Common Table Expression)?
- What is a window function?
- What is a trigger?
- What is a stored procedure?
- What is a function?
- What is VACUUM?
- What is autovacuum?
- What is ANALYZE?
- What is WAL (Write-Ahead Log)?
- What is a checkpoint?
- What is pg_hba.conf?
- What is connection pooling?
- What is PgBouncer?
- What is streaming replication?
- What is logical replication?
- What is a publication and subscription in logical replication?
- What is a standby server?
- What is hot standby?
- What is point-in-time recovery (PITR)?

## Deep Dive Questions

- Explain how MVCC works in PostgreSQL.
- What is a tuple (row version) in PostgreSQL's heap?
- What are xmin and xmax fields in a tuple?
- What is the transaction ID (XID)?
- How does PostgreSQL determine which version of a tuple is visible to a transaction?
- What is a snapshot in PostgreSQL's MVCC?
- What is the difference between heap-only tuple (HOT) updates and regular updates?
- How does dead tuple accumulation happen and why does VACUUM address it?
- What is XID wraparound and why is it dangerous?
- How does the B-tree index work for range queries?
- How does the hash index differ from the B-tree index in functionality?
- Explain the PostgreSQL query planner and optimizer.
- What does EXPLAIN output show?
- What does EXPLAIN ANALYZE add?
- What is a seq scan?
- What is an index scan?
- What is an index-only scan?
- What is a bitmap index scan?
- What is a hash join?
- What is a merge join?
- What is a nested loop join?
- How does the planner decide which join type to use?
- What are planner statistics (pg_statistic)?
- What is the cost model in the planner?
- What are seq_page_cost and random_page_cost?
- How does WAL ensure durability?
- What is WAL level (minimal, replica, logical)?
- How does streaming replication use WAL?
- What is replication lag?
- What is synchronous_commit?
- What is a WAL sender and WAL receiver?
- What is a replication slot?
- What are the risks of replication slots?
- How does logical replication differ from streaming replication?
- What is table bloat?
- What is index bloat?
- How does VACUUM FULL differ from regular VACUUM?
- What is pg_catalog?
- What are system catalogs?
- What is pg_stat_activity?
- What is pg_locks?
- What is a deadlock?
- How does PostgreSQL detect deadlocks?
- What is lock escalation?
- What is an advisory lock?
- What is LISTEN/NOTIFY?

## Why Questions

- Why use PostgreSQL over MySQL?
- Why use PostgreSQL over a NoSQL database like MongoDB?
- Why does PostgreSQL use MVCC instead of locking for reads?
- Why does VACUUM exist and why isn't dead tuple cleanup automatic?
- Why is XID wraparound dangerous and how does PostgreSQL prevent it?
- Why use B-tree indexes instead of hash indexes for most workloads?
- Why use a materialized view instead of a regular view?
- Why use PgBouncer instead of letting applications connect directly?
- Why use logical replication instead of streaming replication?
- Why is synchronous_commit=off risky?

## Coding Questions

- Design a schema for a social network with users, posts, and follows.
- Write a query that uses a window function to rank users by post count.
- Write a query that uses a CTE to recursively traverse a tree structure.
- Write a query that uses EXPLAIN ANALYZE and identify the bottleneck.
- Write an index that improves a specific slow query.
- Write a trigger that maintains an audit log table.
- Write a materialized view and a refresh strategy.
- Write a query that detects deadlocks via pg_locks.
- Implement optimistic locking using a version column.
- Implement a queue using PostgreSQL and SKIP LOCKED.
- Write a migration that adds a NOT NULL column to a large table without downtime.

## Edge Cases

- What happens when a transaction tries to update a row that another transaction has updated but not yet committed?
- What happens when two transactions both try to insert a row with the same unique key?
- What happens when XID wraparound is not addressed?
- What happens when a replication slot's WAL accumulates indefinitely because the subscriber is down?
- What happens when autovacuum cannot keep up with write volume?
- What happens when connection limits are exhausted?
- What happens when a long-running transaction blocks VACUUM?
- What happens when a foreign key constraint is violated?

## Debugging Scenarios

- A query that was fast yesterday is now slow. How do you diagnose?
- The database is running out of disk space. What do you check?
- A table has excessive bloat. How do you identify and address it?
- Replication lag is growing. How do you investigate?
- pg_stat_activity shows a long-running idle transaction. What do you do?
- A query returns different results depending on isolation level. How do you explain it?
- Autovacuum is running constantly but table bloat persists. Why?
- Connection count is at the limit and new connections are being rejected. What do you do?

## System Design Questions

- Design a PostgreSQL high-availability setup with automatic failover.
- Design a schema and indexing strategy for a time-series workload.
- Design a multi-tenant SaaS database schema.
- Design a read-scaling architecture using PostgreSQL replicas.
- Design a PITR backup and recovery strategy.

## Related Topics

- [ScyllaDB](../scylladb/questions.md)
- [Kafka](../kafka/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)
