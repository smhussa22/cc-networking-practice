# Jitter Buffer

## Overview

A jitter buffer (playout buffer) is a mechanism used in real-time media systems to absorb network jitter — variation in packet arrival times — before passing audio or video frames to the decoder. It delays playout by a controlled amount to allow out-of-order or delayed packets to arrive before they are needed.

## Conceptual Questions

- What is jitter?
- What is network jitter?
- What is a jitter buffer?
- What problem does a jitter buffer solve?
- What is playout delay?
- What is a fixed jitter buffer?
- What is an adaptive jitter buffer?
- What is the difference between fixed and adaptive jitter buffers?
- What is buffer underflow?
- What is buffer overflow?
- What happens when a packet arrives after its playout deadline?
- What is a late packet?
- What is packet reordering?
- What is clock drift?
- What is packet loss concealment (PLC)?
- What is comfort noise generation (CNG)?
- What is the relationship between jitter buffer delay and perceived call quality?
- What is a target delay?
- What is the RTCP jitter estimate and how does it relate to the jitter buffer?
- What is the difference between jitter and latency?
- Why can't you simply increase the jitter buffer size to solve all jitter problems?

## Deep Dive Questions

- Explain how a fixed jitter buffer works step by step.
- Explain how an adaptive jitter buffer works step by step.
- What algorithm does an adaptive jitter buffer use to update its target delay?
- What is the EWMA (Exponentially Weighted Moving Average) approach to delay estimation?
- How does the adaptive jitter buffer decide when to shrink its buffer?
- How does the adaptive jitter buffer decide when to grow its buffer?
- What is the relationship between RTTVAR (from RFC 6298) and jitter buffer sizing?
- How does the jitter buffer handle RTP sequence number ordering?
- How does the jitter buffer detect and handle RTP timestamp discontinuities?
- What is timestamp extrapolation and when is it used?
- How does clock drift between sender and receiver affect the jitter buffer?
- What is the drift compensation mechanism?
- Describe the playout scheduling loop: how does the receiver know when to pull a frame?
- What happens when the jitter buffer is empty and a frame is needed (underflow)?
- What happens when the jitter buffer is full and a new packet arrives (overflow)?
- What is the late-discard threshold?
- How does PLC work for voice (linear interpolation, waveform substitution)?
- How does PLC work for video (repeat last frame)?
- What is codec-level PLC (as in Opus)?
- What is DTX (Discontinuous Transmission)?
- What is VAD (Voice Activity Detection)?
- How does the jitter buffer interact with DTX?
- What is time-scale modification (TSM) and how is it used to shrink a jitter buffer without perceived quality loss?
- What is WSOLA (Waveform Similarity Overlap-Add)?

## Why Questions

- Why does a real-time media system need a jitter buffer at all?
- Why is a fixed jitter buffer simpler but suboptimal?
- Why does an adaptive jitter buffer produce better perceived quality?
- Why can't you just use TCP for real-time audio and skip the jitter buffer?
- Why does jitter buffer depth directly trade off against latency?
- Why is PLC necessary even with a jitter buffer?
- Why does clock drift cause jitter buffer issues over long calls?
- Why is TSM/WSOLA preferred to simply dropping or duplicating frames for buffer adjustment?

## Coding Questions

- Implement a fixed-delay jitter buffer for RTP audio.
- Implement a packet reordering buffer keyed by RTP sequence number.
- Implement a playout deadline calculator from RTP timestamps and clock rate.
- Implement adaptive delay estimation using EWMA.
- Implement buffer underflow handling with silence insertion.
- Implement buffer overflow handling with late-packet discard.
- Implement RTP timestamp discontinuity detection.
- Implement jitter estimation per RFC 3550.
- Implement clock drift compensation using a phase-locked loop (PLL).
- Implement a simple PLC that repeats the last received audio frame.

## Edge Cases

- What happens when a packet arrives with a sequence number far in the future (large gap)?
- What happens when duplicate packets arrive?
- What happens when packets arrive in reverse order (e.g., 5, 4, 3)?
- What happens when a long burst of loss occurs and the buffer is empty for many frames?
- What happens when the sender pauses (DTX) and then resumes?
- What happens when there is a sudden change in network path and jitter characteristics change abruptly?
- What happens when the RTP timestamp wraps around?
- What happens when jitter buffer growth causes unacceptable end-to-end latency?

## Debugging Scenarios

- Users report audio glitching during calls. What jitter buffer metrics do you examine?
- Audio is choppy with regular gaps every few hundred milliseconds. What is the likely cause?
- The jitter buffer is growing unboundedly during a long call. Why?
- PLC is being invoked frequently even though packet loss is low. What could cause this?
- End-to-end latency increases over the course of a call. What buffer behavior is responsible?
- A jitter buffer implementation works well on LAN but degrades on high-jitter WAN paths. How do you adapt it?

## System Design Questions

- Design a jitter buffer for a WebRTC-based voice application.
- Design a jitter buffer for a video conferencing system.
- Design an adaptive jitter buffer that uses RTCP feedback to adjust its target delay.
- Design a system that monitors jitter buffer statistics and alerts on quality degradation.
- Design Discord's voice infrastructure including jitter buffering and PLC.

## Related Topics

- [RTP](../rtp/questions.md)
- [UDP](../udp/questions.md)
- [RFC6298](../rfc6298/questions.md)
- [WebSockets](../websockets/questions.md)
- [System Design](../system-design/questions.md)
