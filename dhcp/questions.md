# DHCP

## Core Concepts

- What is DHCP?
- Why does DHCP exist?
- Explain DHCP from device boot to internet access.
- Explain the DORA process.
  - DISCOVER
  - OFFER
  - REQUEST
  - ACK

## Packet Fields

- What is xid?
- What is ciaddr?
- What is yiaddr?
- What is giaddr?
- What is the flags field?
- What is the broadcast bit?

## Lease Management

- What is a lease?
- What is lease expiration?
- What is T1?
- What is T2?
- Explain renewal.
- Explain rebinding.
- Explain RELEASE.
- Explain DECLINE.
- Explain INFORM.

## Networking

- Why is DISCOVER broadcast?
- Why isn't OFFER always broadcast?
- What is a DHCP relay?
- Why is relay needed?
- How does DHCP work across subnets?

## Options

- What are DHCP options?
- What is Option 53?
- What is Option 50?
- What is Option 54?
- What is Option 51?

## Coding

- Serialize a DHCP DISCOVER packet.
- Parse a DHCP REQUEST packet.
- Build a DHCP packet parser.
- Build a lease allocator.
- Handle concurrent lease requests.

## Edge Cases

- Pool exhausted.
- Duplicate MAC.
- Client crashes.
- Relay agent.
- Multiple interfaces.