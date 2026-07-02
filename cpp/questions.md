# C++

## Overview

C++ is a statically typed, compiled systems programming language that provides deterministic resource management (RAII), zero-cost abstractions, and low-level memory control. It is the language of choice for high-performance networked systems, game engines, databases, and operating system components.

## Conceptual Questions

- What is RAII (Resource Acquisition Is Initialization)?
- What is the Rule of Three?
- What is the Rule of Five?
- What is the Rule of Zero?
- What is a copy constructor?
- What is a copy assignment operator?
- What is a destructor?
- What is a move constructor?
- What is a move assignment operator?
- What is move semantics?
- What is an rvalue reference?
- What is an lvalue?
- What is an rvalue?
- What is `std::move()`?
- What is `std::forward()`?
- What is perfect forwarding?
- What is copy elision?
- What is RVO (Return Value Optimization)?
- What is NRVO (Named Return Value Optimization)?
- What is a virtual function?
- What is a vtable?
- What is dynamic dispatch?
- What is a pure virtual function?
- What is an abstract class?
- What is multiple inheritance?
- What is virtual inheritance?
- What is the diamond problem?
- What is `override`?
- What is `final`?
- What is `noexcept`?
- What is a template?
- What is template specialization?
- What is partial template specialization?
- What is a variadic template?
- What is `constexpr`?
- What is `consteval`?
- What is `constinit`?
- What is `inline`?
- What is `static` in the context of a class member?
- What is `static` in the context of a function or variable?
- What is `extern`?
- What is a smart pointer?
- What is `std::unique_ptr`?
- What is `std::shared_ptr`?
- What is `std::weak_ptr`?
- What is the reference count in `shared_ptr`?
- What is a cyclic reference in `shared_ptr` and how does `weak_ptr` break it?
- What is `std::thread`?
- What is `std::mutex`?
- What is `std::lock_guard`?
- What is `std::unique_lock`?
- What is `std::condition_variable`?
- What is `std::atomic`?
- What is `std::memory_order`?
- What is a data race?
- What is undefined behavior (UB) caused by data races?
- What is `std::vector`?
- What is vector reallocation?
- What is iterator invalidation?
- What is `std::unordered_map`?
- What is the hash function for `unordered_map`?
- What is a bucket?
- What is load factor?
- What is rehashing?
- What is `std::deque`?
- What is `std::list`?
- What is `std::array`?
- What is `std::string_view`?
- What is placement new?
- What is an allocator?
- What is `std::allocator_traits`?
- What is a custom allocator?
- What is stack vs heap allocation?
- What is `alignas`?
- What is `alignof`?
- What is `sizeof`?
- What is `offsetof`?
- What is undefined behavior (UB)?
- What are common sources of UB in C++?
- What is address sanitizer (ASan)?
- What is thread sanitizer (TSan)?
- What is undefined behavior sanitizer (UBSan)?
- What is `valgrind`?

## Deep Dive Questions

- Describe the vtable layout for a class with virtual functions.
- How does dynamic dispatch work through a vtable?
- What is the cost of a virtual function call vs a non-virtual call?
- How does RAII ensure exception safety?
- Describe the copy-and-swap idiom.
- Why does copy-and-swap provide the strong exception guarantee?
- Describe the memory layout of `std::vector`.
- What is the amortized complexity of `push_back`?
- How does `reserve()` differ from `resize()`?
- Describe the memory layout of `std::string` (including SSO — Small String Optimization).
- How does `std::unordered_map` handle hash collisions (chaining vs open addressing)?
- Describe the memory layout of `std::shared_ptr` (control block, reference count, weak count).
- What is the `make_shared` optimization?
- How does `std::atomic<T>` work on x86 for 64-bit integers?
- What is the difference between `memory_order_seq_cst` and `memory_order_acq_rel`?
- What is a happens-before relationship?
- What is the C++ memory model?
- What is a sequence point?
- Describe how `std::condition_variable::wait()` works.
- Why must `condition_variable::wait()` always be called in a loop?
- What is a spurious wakeup?
- What is the difference between `notify_one()` and `notify_all()`?
- Describe the lifecycle of an object from construction to destruction.
- What is the order of destruction for member variables?
- What is the order of destruction for base classes?
- What is a trivially copyable type?
- What is a standard-layout type?
- What is a POD type?
- What is `std::launder`?
- What is structured binding?
- What is if constexpr?
- What is a fold expression?
- What is SFINAE?
- What is `std::enable_if`?
- What is `std::is_same`?
- What is a concept (C++20)?
- What is `requires`?
- What is coroutine (C++20)?
- What is `co_await`?
- What is `co_yield`?
- What is `co_return`?

## Why Questions

- Why use `unique_ptr` instead of raw pointers?
- Why use `shared_ptr` instead of `unique_ptr` when ownership is shared?
- Why is `shared_ptr` more expensive than `unique_ptr`?
- Why does move semantics exist?
- Why is `std::move` a cast and not a move?
- Why does copy elision (NRVO) matter for performance?
- Why is virtual dispatch slower than direct function calls?
- Why is the Rule of Five important when a class manages a resource?
- Why does `vector` double its capacity instead of growing by a fixed amount?
- Why should you use `memory_order_acquire`/`release` instead of `seq_cst` when possible?
- Why does `std::mutex` prevent data races?
- Why must `condition_variable` always be used with a mutex?
- Why is undefined behavior dangerous even if the code appears to work?
- Why use `string_view` instead of `const std::string&`?
- Why use `reserve()` before inserting many elements into a vector?
- Why use placement new for custom allocators?
- Why use RAII for file handles, sockets, and locks?

## Coding Questions

- Implement a thread pool using `std::thread` and a work queue.
- Implement a thread-safe queue using `std::mutex` and `std::condition_variable`.
- Implement an LRU cache using `unordered_map` and a doubly linked list.
- Implement a lock-free SPSC ring buffer using `std::atomic`.
- Implement a RAII wrapper for a file descriptor.
- Implement a RAII wrapper for a network socket.
- Implement `shared_ptr` from scratch (reference counting, control block).
- Implement `unique_ptr` from scratch.
- Implement a generic object pool using placement new.
- Implement a variadic template that prints all its arguments.
- Implement a compile-time Fibonacci using `constexpr`.
- Implement a type-safe event bus using templates.
- Implement a producer-consumer system using `std::thread` and `std::condition_variable`.
- Implement a rate limiter using `std::atomic` and `std::chrono`.
- Implement move semantics for a class that owns a heap-allocated buffer.
- Implement the Rule of Five for a class that wraps a raw pointer.
- Implement a custom allocator that uses a memory pool.

## Edge Cases

- What happens when a `shared_ptr` is copied in multiple threads without synchronization?
- What happens when a destructor throws?
- What happens when a copy constructor throws mid-copy?
- What happens when you access a dangling pointer?
- What happens when you double-free a pointer?
- What happens when `std::vector` iterator is invalidated after `push_back`?
- What happens when you call a pure virtual function from a constructor?
- What happens when a move constructor is called on a vector that is reallocating?
- What happens when a mutex is destroyed while locked?
- What happens when you forget to call `notify_one()` after modifying the condition variable predicate?

## Debugging Scenarios

- A program crashes with a segfault. How do you find the cause using gdb?
- A program has a memory leak. How do you find it using valgrind or ASan?
- A multithreaded program has a data race. How do you find it using TSan?
- A program has undefined behavior that only manifests in release builds. Why?
- A `shared_ptr` cycle is causing a memory leak. How do you detect it?
- A condition variable is causing a deadlock. How do you diagnose it?
- Heap corruption is causing crashes at unpredictable points. How do you investigate?

## System Design Questions

- Design a C++ coroutine-based async I/O framework.
- Design a zero-copy network buffer management system.
- Design a high-performance C++ logging library with minimal overhead.
- Design a C++ memory pool allocator for a network packet processing system.

## Related Topics

- [Lock-Free Queue](../lock-free-queue/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [System Design](../system-design/questions.md)
