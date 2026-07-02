# Juniper SRX

## Overview

The Juniper SRX is a line of next-generation firewalls and security gateways running Junos OS. The SRX combines routing, switching, security, and VPN in a single platform. Junos uses a commit-based, transactional configuration model that distinguishes it from Cisco IOS.

## Conceptual Questions

- What is a Juniper SRX?
- What is Junos OS?
- What is the difference between Junos and Cisco IOS?
- What is the Junos commit model?
- What is a candidate configuration?
- What is an active configuration?
- What is a commit?
- What is a commit confirmed?
- What is a rollback?
- What is a Junos configuration hierarchy?
- What is the `set` command in Junos?
- What is the `show` command in Junos?
- What is the `edit` command in Junos?
- What is a security zone?
- What is the difference between a security zone and a routing instance?
- What is a trust zone?
- What is an untrust zone?
- What is a security policy?
- What is a policy match condition?
- What is a policy action?
- What is a security address book?
- What is an application set in Junos?
- What is NAT on the SRX?
- What is source NAT?
- What is destination NAT?
- What is static NAT?
- What is a NAT pool?
- What is a NAT rule?
- What is a routing instance on the SRX?
- What is a virtual router?
- What is VRF (Virtual Routing and Forwarding)?
- What is the SRX flow engine?
- What is the flow-based forwarding model?
- What is the packet-based forwarding model?
- What is the SRX session table?
- What is a session?
- What is ALG (Application Layer Gateway)?
- What is IPS (Intrusion Prevention System) on SRX?
- What is AppSecure?
- What is Sky ATP (Advanced Threat Prevention)?
- What is HA (high availability) on SRX?
- What is chassis cluster on SRX?
- What is JSRPD (Junos SRX Redundancy Protocol Daemon)?
- What is an reth (redundant Ethernet) interface?
- What is the difference between SRX Series (branch) and SRX Series (data center)?

## Deep Dive Questions

- Describe the Junos commit process step by step.
- What is the difference between `commit` and `commit confirmed` with a timeout?
- What is `commit check`?
- What is `commit synchronize` in a chassis cluster?
- How does the SRX match a packet to a security policy?
- What is the order of policy evaluation (first match)?
- How does the SRX perform source NAT for outbound Internet traffic?
- How does the SRX perform destination NAT for inbound server traffic?
- How does the SRX handle NAT and security policy together?
- Describe the SRX flow table and how it tracks sessions.
- What fields make up a session key in the SRX flow table?
- What happens when an initial packet arrives and no session exists?
- What is a first-packet lookup?
- What is a fast-path lookup?
- What is the SRX route lookup order?
- How does the SRX handle ALG for protocols like SIP and FTP?
- What is the SRX chassis cluster control plane?
- What is the control link in a chassis cluster?
- What is the fabric link in a chassis cluster?
- What is the difference between control link and fabric link?
- What is JSRPD and how does it monitor node health?
- What is the priority and preemption in SRX chassis clustering?
- What is a reth interface and how does it provide active-passive redundancy?
- How does the SRX perform routing: what is the routing table hierarchy?
- What is `inet.0`?
- What is `inet6.0`?
- What is a routing instance of type `virtual-router`?
- What is a routing instance of type `vrf`?
- What is `import` and `export` policy in a VRF?
- How does OSPF or BGP interact with routing instances?
- What is the Junos policy framework?
- What is a routing policy (policy-options)?
- What is a term in a routing policy?
- What is a match condition?
- What is an action (accept, reject, next-term, next-policy)?
- How does a routing policy differ from a security policy on the SRX?

## Why Questions

- Why does Junos use a commit-based model instead of an immediate-apply model?
- Why is commit confirmed useful during remote configuration changes?
- Why does the SRX use a flow-based model instead of a packet-by-packet model?
- Why does the SRX security policy evaluation stop at the first match?
- Why does NAT interact with security policy in a specific order?
- Why use a chassis cluster instead of two independent SRX devices?
- Why use routing instances instead of a flat routing table?
- Why use ALGs and when should they be disabled?
- Why use Junos routing policies instead of ACLs for route filtering?

## Coding Questions

- Write Junos CLI commands to create a security zone and assign an interface.
- Write Junos CLI commands to create a security policy permitting HTTP from trust to untrust.
- Write Junos CLI commands to configure source NAT for a trust-to-untrust flow.
- Write Junos CLI commands to configure destination NAT for inbound HTTPS.
- Write Junos CLI commands to configure static NAT.
- Write Junos CLI commands to configure an address book entry and reference it in a policy.
- Write Junos CLI commands to configure a routing instance.
- Write Junos CLI commands to create a BGP session within a routing instance.
- Write Junos CLI commands to configure a chassis cluster on two SRX devices.
- Write Junos CLI commands to configure a reth interface.
- Write a Junos routing policy that only accepts a specific prefix from a BGP peer.

## Edge Cases

- What happens when `commit confirmed` timeout expires and no confirm is received?
- What happens when the control link in a chassis cluster fails?
- What happens when both nodes in a chassis cluster claim to be primary?
- What happens when a session exists in the flow table but the routing table changes?
- What happens when NAT pool exhaustion occurs?
- What happens when an ALG is enabled for a protocol but the port is non-standard?
- What happens when a security policy with `deny` action is matched before a `permit` policy?

## Debugging Scenarios

- Traffic is being dropped on the SRX and you don't know why. What tools do you use?
- `show security flow session` shows no matching session. What does that tell you?
- A NAT translation is not working for a specific host. How do you debug?
- The chassis cluster is in split-brain. How do you diagnose and recover?
- A BGP session within a routing instance is not establishing. How do you investigate?
- Commit fails with an error. How do you identify the conflicting configuration?
- IPS is false-positiving on legitimate traffic. How do you tune it?

## System Design Questions

- Design a data center edge firewall architecture using Juniper SRX chassis clusters.
- Design a multi-zone SRX security policy for a DMZ architecture.
- Design a multi-VRF SRX deployment for a managed service provider.
- Design an SRX-based site-to-site VPN architecture.

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [BGP](../bgp/questions.md)
- [OSPF](../ospf/questions.md)
- [Cisco](../cisco/questions.md)
- [Palo Alto](../palo-alto/questions.md)
- [Debugging](../debugging/questions.md)
