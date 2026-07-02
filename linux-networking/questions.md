# Linux Networking

## Overview

Linux provides a rich set of system calls and APIs for network programming, including BSD sockets for TCP and UDP, I/O multiplexing mechanisms (select, poll, epoll), and advanced features like sendmsg, recvmsg, and zero-copy. Understanding the Linux networking stack is essential for implementing high-performance networked systems.

## Conceptual Questions

- What is a socket?
- What is a file descriptor?
- What is the difference between a stream socket (SOCK_STREAM) and a datagram socket (SOCK_DGRAM)?
- What is the difference between blocking and non-blocking I/O?
- What is a blocking socket?
- What is a non-blocking socket?
- What is I/O multiplexing?
- What is `select()`?
- What is `poll()`?
- What is `epoll()`?
- What is edge-triggered (ET) epoll?
- What is level-triggered (LT) epoll?
- What is the difference between ET and LT?
- What is the C10K problem?
- How does epoll solve the C10K problem?
- What is `fork()`?
- What is `exec()`?
- What is a process?
- What is a thread?
- What is a mutex?
- What is a condition variable?
- What is a semaphore?
- What is `mmap()`?
- What is `sendfile()`?
- What is zero-copy?
- What is `splice()`?
- What is `vmsplice()`?
- What is a signal?
- What is `SIGPIPE`?
- How do you handle `SIGPIPE` in a TCP server?
- What is a Unix domain socket?
- What is `SO_REUSEADDR`?
- What is `SO_REUSEPORT`?
- What is `TCP_NODELAY`?
- What is the Nagle algorithm?
- What is `TCP_CORK`?
- What is `SO_KEEPALIVE`?
- What is `TCP_KEEPIDLE`?
- What is `TCP_KEEPINTVL`?
- What is `TCP_KEEPCNT`?
- What is `SO_RCVBUF`?
- What is `SO_SNDBUF`?
- What is `SO_LINGER`?
- What is `O_NONBLOCK`?
- What is `fcntl()`?
- What is `ioctl()`?
- What is `strace`?
- What is `gdb`?
- What is `perf`?
- What is `ss`?
- What is `netstat`?
- What is `tcpdump`?
- What is `Wireshark`?

## Deep Dive Questions

- Describe the steps to create a TCP server: socket, bind, listen, accept, recv, send, close.
- Describe the steps to create a TCP client: socket, connect, send, recv, close.
- Describe the steps to create a UDP server: socket, bind, recvfrom, sendto, close.
- Describe the steps to create a UDP client: socket, sendto, recvfrom, close.
- What does `socket()` return?
- What is the `domain` parameter in `socket()`?
- What is `AF_INET`?
- What is `AF_INET6`?
- What is `AF_UNIX`?
- What is the `type` parameter in `socket()`?
- What is the `protocol` parameter in `socket()`?
- What does `bind()` do?
- What does `listen()` do?
- What is the backlog parameter in `listen()`?
- What is the accept queue?
- What is the SYN queue?
- What does `accept()` return?
- What happens when the accept queue is full?
- What is a connection refused?
- Describe the `select()` system call.
- What is `fd_set`?
- What are the read, write, and except sets in `select()`?
- What is the timeout parameter in `select()`?
- What is the scalability problem with `select()`?
- Describe the `poll()` system call.
- What is `struct pollfd`?
- What are the events and revents fields?
- What is `POLLIN`?
- What is `POLLOUT`?
- What is `POLLERR`?
- What is `POLLHUP`?
- Describe the `epoll` API.
- What is `epoll_create()`?
- What is `epoll_ctl()`?
- What is `epoll_wait()`?
- What is `struct epoll_event`?
- What is `EPOLLIN`?
- What is `EPOLLOUT`?
- What is `EPOLLET`?
- What is `EPOLLONESHOT`?
- What is `EPOLLRDHUP`?
- Why is epoll O(1) per event while select/poll are O(n)?
- What is the thundering herd problem with `accept()` and how does `SO_REUSEPORT` help?
- What is `recvmsg()` and when would you use it over `recv()`?
- What is `sendmsg()` and when would you use it over `send()`?
- What is scatter-gather I/O (iovec)?
- What is `recvmmsg()`?
- What is `sendmmsg()`?
- What is the `MSG_WAITALL` flag?
- What is the `MSG_PEEK` flag?
- What is the `MSG_DONTWAIT` flag?
- What is the `MSG_TRUNC` flag?
- What is the `MSG_CMSG_CLOEXEC` flag?
- What is ancillary data (control message) in `recvmsg()`?
- How do you receive the destination IP of a UDP packet using `IP_PKTINFO`?
- How do you pass file descriptors over a Unix domain socket?
- What is `setsockopt()` and `getsockopt()`?
- What happens on `close()` of a TCP socket?
- What is the `TIME_WAIT` state?
- Why does `TIME_WAIT` exist?
- How does `SO_REUSEADDR` help with `TIME_WAIT`?
- What is a half-open connection?
- What is a half-close?
- What is `shutdown()`?
- What is the difference between `close()` and `shutdown()`?
- What is `fork()` and how does it interact with sockets?
- How do pre-fork servers work?
- What is a thread pool server?
- What is an event-driven server?

## Why Questions

- Why is epoll faster than select for large numbers of file descriptors?
- Why does select have an FD_SETSIZE limit?
- Why use edge-triggered epoll instead of level-triggered?
- Why is non-blocking I/O required for edge-triggered epoll?
- Why does the Nagle algorithm exist and when should you disable it?
- Why does `SO_REUSEPORT` improve multi-threaded server performance?
- Why does `TIME_WAIT` exist and what problems does it cause?
- Why use `sendfile()` for sending files over sockets?
- Why use scatter-gather I/O instead of assembling a single buffer?
- Why does SIGPIPE happen and how should you handle it?
- Why use Unix domain sockets instead of loopback TCP?

## Coding Questions

- Implement a TCP echo server using blocking I/O.
- Implement a TCP echo server using epoll (non-blocking, level-triggered).
- Implement a TCP echo server using epoll (edge-triggered).
- Implement a TCP client.
- Implement a UDP echo server.
- Implement a UDP client.
- Implement a poll-based chat server.
- Implement an epoll-based multi-client server.
- Implement a thread pool server using pthreads.
- Implement a pre-fork server.
- Implement a non-blocking connect with epoll.
- Implement a rate limiter using a token bucket with epoll timers.
- Implement a TCP server that reads a fixed-length header followed by a variable-length body.
- Implement a server that uses scatter-gather I/O for zero-copy responses.
- Implement `sendfile()` to serve a file over a TCP connection.
- Implement a Unix domain socket server.
- Implement a server that passes file descriptors to worker processes.

## Edge Cases

- What happens when `accept()` is called on a non-listening socket?
- What happens when `recv()` returns 0?
- What happens when `send()` returns a short write?
- What happens when `write()` is called on a closed TCP connection?
- What happens when epoll is used in edge-triggered mode but data is not fully read?
- What happens when `epoll_wait()` returns `EINTR`?
- What happens when a socket's receive buffer is full?
- What happens when you bind to port 0?
- What happens when `connect()` fails with `EINPROGRESS` on a non-blocking socket?
- What happens when a child process inherits a listening socket after `fork()`?

## Debugging Scenarios

- A TCP server stops accepting new connections. How do you investigate?
- `recv()` returns -1 with `EAGAIN` on a blocking socket. How is that possible?
- A server leaks file descriptors. How do you detect and find the source?
- High CPU usage on a server that uses busy-waiting with `EAGAIN`. How do you fix it?
- `bind()` fails with `EADDRINUSE`. Why and how do you fix it?
- `connect()` returns `ECONNREFUSED`. What does that mean?
- An epoll edge-triggered server stops receiving data after a burst. Why?
- `strace` shows the server is stuck in `epoll_wait()` but data is available. Why?

## System Design Questions

- Design a high-performance TCP proxy using epoll.
- Design an epoll-based HTTP server.
- Design a UDP-based game server using non-blocking sockets.
- Design a connection pool for outbound TCP connections.
- Design a zero-downtime server reload without dropping connections.

## Related Topics

- [UDP](../udp/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [CPP](../cpp/questions.md)
- [Lock-Free Queue](../lock-free-queue/questions.md)
- [Debugging](../debugging/questions.md)
