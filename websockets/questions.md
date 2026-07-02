# WebSockets

## Overview

WebSocket (RFC 6455) is a full-duplex communication protocol over a single TCP connection. It starts with an HTTP/1.1 upgrade handshake and then switches to a framing protocol that allows both client and server to send data independently at any time, without the overhead of repeated HTTP request/response cycles.

## Conceptual Questions

- What is WebSocket?
- What problem does WebSocket solve?
- How is WebSocket different from HTTP polling?
- How is WebSocket different from HTTP long-polling (Comet)?
- How is WebSocket different from Server-Sent Events (SSE)?
- What is the WebSocket handshake?
- What HTTP version does the WebSocket handshake use?
- What is the `Upgrade` header?
- What is the `Connection: Upgrade` header?
- What is `Sec-WebSocket-Key`?
- What is `Sec-WebSocket-Accept`?
- How is `Sec-WebSocket-Accept` derived from `Sec-WebSocket-Key`?
- What is the magic GUID used in the WebSocket handshake?
- What is `Sec-WebSocket-Version`?
- What is `Sec-WebSocket-Protocol` (subprotocol negotiation)?
- What is `Sec-WebSocket-Extensions`?
- What is the WebSocket frame?
- What is masking in WebSocket?
- Why must the client mask frames?
- Why does the server not mask frames?
- What is a ping frame?
- What is a pong frame?
- What is a close frame?
- What is a text frame?
- What is a binary frame?
- What is a continuation frame?
- What is message fragmentation?
- What is the WebSocket close handshake?
- What are WebSocket close codes?
- What is `wss://`?
- How does WebSocket over TLS work?
- What is the `permessage-deflate` extension?
- What are the limitations of WebSocket?

## Deep Dive Questions

- Describe the full WebSocket opening handshake (client request and server response).
- What HTTP status code does the server return to accept a WebSocket upgrade?
- Describe the algorithm for computing `Sec-WebSocket-Accept`.
- What SHA-1 input is used?
- Why is SHA-1 used here even though it is cryptographically weak?
- Describe the WebSocket frame format bit by bit.
- What is the FIN bit?
- What is the RSV1, RSV2, RSV3 bits?
- What is the opcode field?
- What is the MASK bit?
- What is the Payload Length field?
- How does the 7-bit payload length encoding extend to 16-bit or 64-bit?
- What is the masking key?
- How is masking applied to the payload?
- Why is the masking key randomized per frame?
- What is the difference between a message and a frame?
- How does fragmentation work across multiple frames?
- How does the receiver reassemble a fragmented message?
- What is the maximum WebSocket frame size?
- Describe the WebSocket closing handshake.
- What is the close frame payload structure?
- What happens if only one side sends a close frame?
- What happens when a ping is not responded to with a pong?
- What is the `permessage-deflate` extension and how does it apply compression?
- What is context takeover in `permessage-deflate`?
- How does WebSocket interact with TCP's Nagle algorithm?
- How does HTTP/2 differ from WebSocket for bidirectional communication?

## Why Questions

- Why does WebSocket start with an HTTP handshake?
- Why is `Sec-WebSocket-Key` needed?
- Why must clients mask frames sent to the server?
- Why does masking prevent cache poisoning attacks?
- Why are close frames part of the protocol instead of just closing the TCP connection?
- Why does WebSocket support fragmentation?
- Why use WebSocket instead of HTTP/2 server push?
- Why use WebSocket instead of SSE for bidirectional communication?
- Why does `wss://` provide more security than `ws://`?

## Coding Questions

- Implement a WebSocket opening handshake on the server side.
- Implement `Sec-WebSocket-Accept` computation.
- Implement a WebSocket frame parser.
- Implement a WebSocket frame encoder (client-side with masking).
- Implement a WebSocket frame encoder (server-side without masking).
- Implement WebSocket message fragmentation.
- Implement WebSocket message reassembly from fragments.
- Implement a WebSocket ping/pong keepalive mechanism.
- Implement a WebSocket close handshake.
- Implement a simple WebSocket echo server in C or your language of choice.
- Implement a WebSocket client that connects, sends a message, and reads the response.
- Implement a WebSocket chat server that broadcasts messages to all connected clients.

## Edge Cases

- What happens when a server receives an unmasked frame from a client?
- What happens when a client receives a masked frame from the server?
- What happens when the FIN bit is not set on a non-continuation frame?
- What happens when a continuation frame arrives without a preceding start frame?
- What happens when the close frame payload is malformed?
- What happens when one side sends data after sending a close frame?
- What happens when the WebSocket upgrade request is missing required headers?
- What happens when the masking key is all zeros?
- What happens when a large message is fragmented into many frames?
- What happens when the TCP connection drops without a close handshake?

## Debugging Scenarios

- A WebSocket connection drops after exactly 60 seconds. Why?
- A WebSocket server receives garbled data from a client. What do you check?
- A WebSocket handshake fails with HTTP 400. What are the possible causes?
- A client sends a message but the server never receives it. How do you debug?
- WebSocket latency is high even for small messages. What could be the cause?
- A WebSocket server crashes when a client sends a large message. Why?

## System Design Questions

- Design a WebSocket-based real-time chat system.
- Design a WebSocket push notification service for a mobile app backend.
- Design a scalable WebSocket gateway that handles millions of concurrent connections.
- Design a WebSocket-based live sports score feed.
- Design a collaborative document editing backend using WebSocket.

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [OAuth PKCE](../oauth-pkce/questions.md)
- [JWT](../jwt/questions.md)
- [RTP](../rtp/questions.md)
- [System Design](../system-design/questions.md)
