# RFC 6298 — TCP Retransmission Timeout

## Overview

RFC 6298 defines the algorithm for computing TCP's Retransmission Timeout (RTO). It specifies how TCP measures Round-Trip Time (RTT), maintains a smoothed RTT estimate (SRTT) and RTT variance (RTTVAR), and derives a RTO that adapts to changing network conditions while avoiding spurious retransmissions.

## Conceptual Questions

- What is RTT (Round-Trip Time)?
- What is RTO (Retransmission Timeout)?
- What problem does RFC 6298 solve?
- Why does TCP need to estimate RTT dynamically?
- What is SRTT (Smoothed RTT)?
- What is RTTVAR (RTT Variance)?
- What is the initial value of RTO per RFC 6298?
- What is the minimum RTO per RFC 6298?
- What is the maximum RTO per RFC 6298?
- What is the clock granularity (G) parameter?
- What is Karn's algorithm?
- Why does TCP not use RTT measurements from retransmitted segments?
- What is exponential backoff in the context of RTO?
- How many times can TCP retransmit before giving up?
- What is the relationship between RTO and the TCP hold timer?
- What happens to RTO after a successful retransmission?
- What is the Eifel algorithm (RFC 3522) and how does it relate to RFC 6298?

## Deep Dive Questions

- State the RFC 6298 initialization rules for SRTT, RTTVAR, and RTO.
- State the RFC 6298 update rules when the first RTT measurement R is obtained.
- State the RFC 6298 update rules for subsequent RTT measurements R'.
- What is the formula for updating SRTT?
- What is the alpha parameter in the SRTT update formula?
- What value does RFC 6298 specify for alpha?
- What is the formula for updating RTTVAR?
- What is the beta parameter in the RTTVAR update formula?
- What value does RFC 6298 specify for beta?
- What is the formula for computing RTO from SRTT and RTTVAR?
- What is the K parameter in the RTO formula?
- What value does RFC 6298 specify for K?
- Why does the formula use `max(G, 4 * RTTVAR)` instead of just `4 * RTTVAR`?
- What happens to RTO when a retransmission timeout fires?
- What is the backoff multiplier per RFC 6298?
- What is the restart rule (when TCP resumes after an idle period)?
- How does TCP measure RTT using the timestamp option (RFC 7323 / TSOPT)?
- How does the timestamp option allow more frequent RTT sampling?
- What is the RTTM (RTT Measurement) procedure with the timestamp option?
- Why is RTTVAR initialized to R/2 on the first measurement?
- Why is SRTT initialized to R on the first measurement?

## Why Questions

- Why use an exponentially weighted moving average (EWMA) for SRTT instead of a simple average?
- Why is alpha set to 1/8 (0.125)?
- Why is beta set to 1/4 (0.25)?
- Why is K set to 4?
- Why include RTTVAR in the RTO formula rather than just using SRTT + a fixed margin?
- Why use exponential backoff after a timeout?
- Why does Karn's algorithm exclude retransmitted segments from RTT measurements?
- Why does RFC 6298 specify a minimum RTO of 1 second?
- Why is the initial RTO 1 second (previously 3 seconds in older RFCs)?
- Why must RTO be restarted when TCP resumes from idle?
- Why is a high RTTVAR (jitter) bad for TCP throughput?

## Coding Questions

- Implement the RFC 6298 RTT estimator in C or your language of choice.
- Implement the SRTT update formula.
- Implement the RTTVAR update formula.
- Implement the RTO computation formula.
- Implement exponential backoff for retransmission.
- Implement Karn's algorithm to exclude retransmitted segments from RTT sampling.
- Implement a retransmission timer using the computed RTO.
- Simulate RTT estimation over a series of sample RTT measurements and plot SRTT and RTO.
- Implement a reliable-over-UDP layer that uses RFC 6298 RTO estimation.
- Write unit tests for RTT estimator initialization and update logic.

## Edge Cases

- What happens when RTTVAR is zero (RTT is perfectly stable)?
- What happens when RTT spikes suddenly?
- What happens when RTT decreases suddenly after a long period of high RTT?
- What happens when TCP retransmits and then the original packet's ACK arrives (spurious retransmission)?
- What happens when RTO reaches its maximum and the connection is still experiencing loss?
- What happens when clock granularity G is larger than the measured RTT?
- What happens when the timestamp option is not negotiated and RTT can only be sampled once per window?

## Debugging Scenarios

- TCP retransmissions are increasing even though the network RTT is stable. What could cause this?
- RTO is growing exponentially and the connection is effectively stalled. How do you investigate?
- SRTT is much higher than the actual RTT measured with ping. Why?
- A TCP connection recovers from packet loss but the throughput takes a long time to recover. What RFC 6298 behavior explains this?
- Spurious retransmissions are observed in Wireshark. What does that imply about the RTO estimate?

## System Design Questions

- Design a reliable transport protocol over UDP that implements RFC 6298 RTO estimation.
- Design a congestion control system that uses RTT measurements to adjust sending rate.
- Design a latency monitoring tool that tracks SRTT and RTTVAR per TCP flow.

## Related Topics

- [UDP](../udp/questions.md)
- [RTP](../rtp/questions.md)
- [Jitter Buffer](../jitter-buffer/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
