# SNMP

## Overview

Simple Network Management Protocol (SNMP) is an application-layer protocol used to monitor and manage network devices. Agents running on managed devices expose a Management Information Base (MIB), and managers poll or receive traps from those agents. SNMP uses BER encoding over UDP.

## Conceptual Questions

- What is SNMP?
- What problem does SNMP solve?
- What is a manager in SNMP?
- What is an agent in SNMP?
- What is a MIB?
- What is an OID?
- What is a varbind?
- What is a community string?
- What are the SNMP operations?
- What is a GET request?
- What is a GETNEXT request?
- What is GETBULK?
- What is a SET request?
- What is a TRAP?
- What is an INFORM?
- What is the difference between TRAP and INFORM?
- What port does SNMP use?
- What transport protocol does SNMP use?
- Why does SNMP use UDP?
- What is SNMP v1?
- What is SNMP v2c?
- What is SNMP v3?
- What are the main differences between v1, v2c, and v3?
- What security features does SNMPv3 add?
- What is the USM (User-based Security Model) in SNMPv3?
- What is the VACM (View-based Access Control Model)?
- What is an SNMP walk?
- How does GETNEXT enable a walk?
- What is GETBULK and how does it differ from GETNEXT?
- What is the max-repetitions field in GETBULK?
- What is the non-repeaters field in GETBULK?

## Deep Dive Questions

- Describe the structure of an SNMPv1 PDU.
- Describe the structure of an SNMPv2c PDU.
- What fields does an SNMP message header contain?
- What is the request-id field?
- What is the error-status field?
- What is the error-index field?
- What is the variable-bindings list?
- Describe the BER encoding of an SNMP GET request byte by byte.
- How is a varbind encoded in BER?
- How is an OID encoded in BER?
- What is the structure of a TRAP PDU in v1?
- What is the structure of a TRAP PDU in v2c?
- How does SNMPv3 structure its message (msgVersion, msgGlobalData, msgSecurityParameters, scopedPDU)?
- What is the scopedPDU in SNMPv3?
- What is the contextName and contextEngineID?
- How does the USM handle authentication?
- How does the USM handle privacy (encryption)?
- What authentication protocols does SNMPv3 support?
- What privacy protocols does SNMPv3 support?
- How does the MIB tree structure map to OID arcs?
- What is the enterprises OID subtree (1.3.6.1.4.1)?
- What is the mib-2 subtree?

## Why Questions

- Why does SNMP use BER encoding instead of JSON or plain text?
- Why does SNMP use UDP instead of TCP?
- Why do community strings in v1/v2c provide weak security?
- Why was SNMPv3 introduced?
- Why use GETNEXT instead of GET for walking a MIB?
- Why use GETBULK instead of multiple GETNEXT requests?
- Why does TRAP not get acknowledged while INFORM does?
- Why is SNMP still widely used despite its age?

## Coding Questions

- Implement an SNMP GET request serializer using BER.
- Implement an SNMP GET response parser using BER.
- Implement a varbind encoder.
- Implement a varbind decoder.
- Implement an OID encoder in BER.
- Implement an OID decoder from BER.
- Implement a basic SNMP agent that responds to GET requests.
- Implement an SNMP manager that sends GET requests and parses responses.
- Implement an SNMP walk using repeated GETNEXT requests.
- Implement an SNMP TRAP receiver.
- Parse a raw SNMP packet from a byte buffer.

## Edge Cases

- What happens when a GET request references an OID that does not exist in the agent's MIB?
- What happens when the community string is wrong?
- What happens when a GETBULK response exceeds the maximum message size?
- What happens when a varbind value type does not match the expected MIB type?
- How do you handle an agent that returns noSuchObject vs noSuchInstance?
- What happens when SNMP UDP packets are dropped?
- What happens when a TRAP is received but the manager has no MIB to decode it?
- How do you handle version mismatches between manager and agent?

## Debugging Scenarios

- An SNMP GET returns a timeout. How do you debug it?
- An SNMP walk stops partway through a table. Why might this happen?
- A GETBULK returns fewer rows than expected. What could cause this?
- A TRAP receiver receives malformed packets. How do you diagnose the encoding issue?
- SNMPv3 authentication fails even though credentials are correct. What do you check?
- An agent returns `tooBig` error. What does that mean and how do you handle it?

## System Design Questions

- Design an SNMP monitoring system that polls 10,000 devices every 60 seconds.
- Design an SNMP trap receiver that ingests traps and triggers alerts.
- Design a scalable MIB browser.

## Related Topics

- [BER](../ber/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [UDP](../udp/questions.md)
- [Debugging](../debugging/questions.md)
