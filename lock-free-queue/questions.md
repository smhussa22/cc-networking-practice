# Lock-Free Queue

## Overview

A lock-free queue is a concurrent data structure that allows multiple threads to enqueue and dequeue elements without using mutexes. Lock-free algorithms use atomic operations (compare-and-swap, fetch-and-add) to ensure progress. A Single-Producer Single-Consumer (SPSC) ring buffer is the simplest and most cache-friendly implementation.

## Conceptual Questions

- What is a lock-free data structure?
- What is the difference between lock-free, wait-free, and obstruction-free?
- What is a lock-free queue?
- What is an SPSC queue?
- What is an MPSC queue?
- What is an MPMC queue?
- What is a ring buffer?
- What is a circular buffer?
- What is a cache line?
- What is false sharing?
- Why does false sharing hurt performance?
- How do you prevent false sharing?
- What is cache line padding?
- What is a memory barrier?
- What is acquire semantics?
- What is release semantics?
- What is relaxed memory ordering?
- What is sequentially consistent ordering?
- What is `std::atomic` in C++?
- What is `std::memory_order_acquire`?
- What is `std::memory_order_release`?
- What is `std::memory_order_relaxed`?
- What is `std::memory_order_seq_cst`?
- What is compare-and-swap (CAS)?
- What is fetch-and-add?
- What is the ABA problem?
- How does the ABA problem affect lock-free queues?
- What is a hazard pointer?
- What is an epoch-based reclamation scheme?
- What is the difference between a lock-free queue and a lock-based queue?
- When should you prefer a lock-free queue over a mutex-based queue?
- What is the LMAX Disruptor and how does it relate to ring buffers?

## Deep Dive Questions

- Describe the memory layout of an SPSC ring buffer.
- What is the head index?
- What is the tail index?
- How does the producer write to the ring buffer?
- How does the consumer read from the ring buffer?
- How does the producer check for a full buffer?
- How does the consumer check for an empty buffer?
- Why does the SPSC ring buffer need only one atomic variable for head and one for tail?
- Why can the producer use `memory_order_relaxed` to load head and `memory_order_release` to store tail?
- Why can the consumer use `memory_order_acquire` to load tail and `memory_order_relaxed` to store head?
- How does `memory_order_release` on the tail store synchronize with `memory_order_acquire` on the tail load?
- What happens if you use `memory_order_relaxed` for both stores and loads?
- Describe the Michael-Scott lock-free queue algorithm.
- How does the Michael-Scott queue use CAS to enqueue?
- How does the Michael-Scott queue use CAS to dequeue?
- Why does the Michael-Scott queue need a sentinel node?
- How does the ABA problem manifest in the Michael-Scott queue?
- What is the role of the `next` pointer in the Michael-Scott queue?
- Why is the Michael-Scott queue more complex than an SPSC ring buffer?
- How does false sharing between head and tail affect SPSC performance?
- What is the standard technique to avoid this (padding to cache line size)?
- How does the power-of-two buffer size optimization work for the ring buffer index?
- What is the modulo operation alternative for non-power-of-two sizes?
- How does prefetching help ring buffer performance?
- What is the difference between a bounded and unbounded lock-free queue?
- How does memory reclamation work for dynamically allocated nodes in an MPMC queue?

## Why Questions

- Why use a lock-free queue instead of a mutex-protected queue?
- Why is an SPSC ring buffer the most cache-friendly lock-free queue?
- Why does false sharing between head and tail pointers hurt throughput?
- Why must the SPSC ring buffer size be a power of two for optimal performance?
- Why does the producer need `memory_order_release` when storing the tail?
- Why does the consumer need `memory_order_acquire` when loading the tail?
- Why is the ABA problem not a concern for the SPSC ring buffer?
- Why is memory reclamation the hardest problem in general lock-free queues?
- Why is the LMAX Disruptor faster than a traditional lock-free queue?
- Why are lock-free queues not always faster than lock-based queues?

## Coding Questions

- Implement an SPSC ring buffer in C++.
- Implement enqueue with correct memory ordering.
- Implement dequeue with correct memory ordering.
- Add cache line padding to the SPSC ring buffer to prevent false sharing.
- Implement a full/empty check for the ring buffer.
- Implement a power-of-two size optimization for index wrapping.
- Implement a batch enqueue and batch dequeue.
- Implement the Michael-Scott MPMC queue using CAS.
- Implement a lock-free stack.
- Implement a thread pool using an SPSC ring buffer per worker thread.
- Implement a benchmark comparing lock-free vs mutex-based queue throughput.
- Implement an MPSC queue using a linked list with CAS.

## Edge Cases

- What happens when the ring buffer is full and the producer tries to enqueue?
- What happens when the ring buffer is empty and the consumer tries to dequeue?
- What happens when head and tail overflow (index wraparound)?
- What happens when two producers simultaneously CAS the same tail pointer in an MPMC queue?
- What happens when memory_order_relaxed is used incorrectly and causes data races?
- What happens when the buffer size is not a power of two and modulo is used?
- What happens when a dequeued element is accessed after memory reclamation in a GC-less language?

## Debugging Scenarios

- A lock-free queue produces incorrect results under high concurrency. How do you diagnose?
- Throughput of a lock-free queue is lower than a mutex queue. Why might this happen?
- A program using a lock-free queue crashes with a segfault under high load. What is the likely cause?
- False sharing is suspected in a ring buffer. How do you confirm and fix it?
- A consumer is starving even though the producer is writing at high rate. Why?
- An MPMC queue exhibits the ABA problem under specific timing. How do you reproduce and fix it?

## System Design Questions

- Design a high-throughput audio pipeline using SPSC ring buffers between threads.
- Design a network packet processing pipeline using lock-free queues.
- Design a logging system that uses a lock-free queue to avoid blocking application threads.
- Design a producer-consumer system where N producers feed M consumers using lock-free queues.

## Related Topics

- [CPP](../cpp/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [System Design](../system-design/questions.md)
