# RTP

## Overview

Real-Time Transport Protocol (RTP) is an application-layer protocol (RFC 3550) used for delivering audio and video over IP networks. It runs over UDP and provides sequence numbering, timestamping, and payload type identification. RTP is commonly paired with RTCP (RTP Control Protocol) for quality reporting and session management.

## Conceptual Questions

- What is RTP?
- What problem does RTP solve?
- Why does RTP run over UDP instead of TCP?
- What is RTCP?
- What is the relationship between RTP and RTCP?
- What port does RTP typically use?
- What is a media session?
- What is a synchronization source (SSRC)?
- What is a contributing source (CSRC)?
- What is a payload type (PT)?
- What is a dynamic payload type?
- What is the RTP sequence number?
- What is the RTP timestamp?
- What is jitter in RTP?
- What is the marker bit?
- What is an RTP profile?
- What is the AVP profile (RFC 3551)?
- What is SRTP (Secure RTP)?
- What is SRTCP?
- What is DTLS-SRTP?
- What is WebRTC and how does it use RTP?
- What is the difference between RTP and RTSP?
- What is the difference between RTP and HLS?

## Deep Dive Questions

- Describe the RTP header format.
- What is the Version (V) field? What value does it have?
- What is the Padding (P) bit?
- What is the Extension (X) bit?
- What is the CC (CSRC count) field?
- What is the Marker (M) bit?
- What is the Payload Type (PT) field?
- What is the Sequence Number field?
- What is the Timestamp field?
- What is the SSRC field?
- What is the CSRC list?
- How is the RTP timestamp clock rate determined?
- What is the timestamp for audio versus video?
- What is the G.711 timestamp clock rate?
- What is the Opus clock rate?
- What is the H.264 timestamp clock rate?
- How does the sequence number wrap around?
- How do receivers detect sequence number wrap-around?
- How is jitter calculated per RFC 3550?
- What is the jitter estimation formula?
- What is an RTP extension header?
- What is the defined-by-profile field in the extension header?
- What are one-byte and two-byte header extensions (RFC 8285)?
- Describe the RTCP packet types.
- What is an SR (Sender Report)?
- What is an RR (Receiver Report)?
- What is an SDES (Source Description)?
- What is a BYE packet?
- What is an APP packet?
- Describe the SR fields: NTP timestamp, RTP timestamp, sender packet count, sender octet count.
- Describe the RR block fields: fraction lost, cumulative lost, highest sequence, jitter, LSR, DLSR.
- What is the RTCP timing algorithm?
- What is the RTCP bandwidth fraction (5% default)?
- How does SRTP encrypt RTP payloads?
- What is the SRTP key derivation process?
- What is the Master Key and Master Salt in SRTP?

## Why Questions

- Why does RTP use sequence numbers instead of relying on UDP ordering?
- Why does RTP use a timestamp instead of relying on the sequence number for timing?
- Why is SSRC needed?
- Why is jitter calculated at the receiver rather than the sender?
- Why is the marker bit needed?
- Why does RTCP exist separately from RTP?
- Why is the RTCP bandwidth limited to 5% of session bandwidth?
- Why use SRTP instead of running RTP over TLS?
- Why does WebRTC mandate SRTP?
- Why does RTP not guarantee delivery?

## Coding Questions

- Implement an RTP packet parser.
- Implement an RTP packet encoder.
- Parse the RTP header from a raw UDP payload.
- Extract the payload type, sequence number, timestamp, and SSRC from a raw RTP packet.
- Implement jitter calculation per RFC 3550.
- Implement sequence number wrap-around detection.
- Implement an RTP receiver that reorders out-of-order packets.
- Implement an RTCP SR parser.
- Implement an RTCP RR generator.
- Implement an SRTP packet encryptor using AES-128-CTR.
- Implement an RTP sender that paces packets according to a timestamp clock.

## Edge Cases

- What happens when the RTP sequence number wraps from 65535 to 0?
- What happens when the RTP timestamp wraps?
- What happens when the SSRC collides with another source?
- What does an SSRC collision require the sender to do?
- What happens when an RTP packet arrives out of order?
- What happens when an RTP packet is lost?
- What happens when the payload type changes mid-stream?
- What happens when the marker bit is set on a non-boundary packet?
- What happens when an RTCP BYE is received?
- How do you handle padding in RTP payloads?

## Debugging Scenarios

- Audio glitches during a VoIP call. What RTP fields do you examine?
- Video is freezing intermittently. What is the likely RTP-layer cause?
- RTCP receiver reports show high jitter. What does this imply about the network?
- RTCP RR shows packets lost is increasing. How do you investigate?
- SSRC collision detected. What must happen next?
- An RTP stream has gaps in sequence numbers. What could cause this?

## System Design Questions

- Design a real-time media server that receives and forwards RTP streams.
- Design a voice conference system using RTP mixing.
- Design an RTP packet loss concealment system.
- Design a recording system that archives RTP streams to storage.
- Design Discord's voice architecture.

## Related Topics

- [UDP](../udp/questions.md)
- [Jitter Buffer](../jitter-buffer/questions.md)
- [RFC6298](../rfc6298/questions.md)
- [WebSockets](../websockets/questions.md)
- [System Design](../system-design/questions.md)
