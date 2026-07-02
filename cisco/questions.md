# Cisco

## Overview

Cisco Systems is the dominant vendor in enterprise networking. Their devices — Catalyst switches, Nexus data center switches, ISR routers, and ASR routers — run Cisco IOS or IOS-XE (and NX-OS for Nexus). Understanding Cisco concepts is essential for network engineering roles and for interpreting network diagrams in most enterprise environments.

## Conceptual Questions

- What is Cisco IOS?
- What is Cisco IOS-XE?
- What is Cisco IOS-XR?
- What is Cisco NX-OS?
- What is the difference between IOS and IOS-XE?
- What is the difference between IOS and NX-OS?
- What is a Catalyst switch?
- What is a Nexus switch?
- What is an ISR (Integrated Services Router)?
- What is an ASR (Aggregation Services Router)?
- What is the Cisco CLI?
- What is enable mode (privileged EXEC)?
- What is global configuration mode?
- What is interface configuration mode?
- What is a VLAN?
- What is VLAN tagging (802.1Q)?
- What is a trunk port?
- What is an access port?
- What is a native VLAN?
- What is VTP (VLAN Trunking Protocol)?
- What is a PortChannel (EtherChannel)?
- What is LACP (Link Aggregation Control Protocol)?
- What is PAgP?
- What is an SVI (Switched Virtual Interface)?
- What is inter-VLAN routing?
- What is a routed port?
- What is an ACL (Access Control List)?
- What is a standard ACL?
- What is an extended ACL?
- What is a named ACL?
- What is HSRP (Hot Standby Router Protocol)?
- What is VRRP?
- What is GLBP?
- What is HSRP priority?
- What is HSRP preemption?
- What is CDP (Cisco Discovery Protocol)?
- What is LLDP?
- What is spanning tree?
- What is STP root bridge election?
- What is the bridge priority?
- What is a BPDU?
- What is PortFast?
- What is BPDU Guard?
- What is loop guard?
- What is root guard?
- What is QoS?
- What is DSCP?
- What is CoS (Class of Service)?
- What is NetFlow (on Cisco devices)?
- What is SNMP on Cisco devices?
- What is Syslog on Cisco?
- What is AAA (Authentication, Authorization, Accounting)?
- What is TACACS+?
- What is RADIUS?
- What is SSH on Cisco devices?
- What is NTP?

## Deep Dive Questions

- Describe how a Cisco switch builds its MAC address table.
- What is a CAM table?
- What is a TCAM?
- How does the TCAM enable wire-speed ACL lookups?
- Describe how an EtherChannel load balances traffic across member links.
- What hashing algorithms can be used for EtherChannel load balancing?
- Describe the HSRP state machine.
- What are the HSRP states (Initial, Learn, Listen, Speak, Standby, Active)?
- How does HSRP use hello messages and hold timers?
- How does HSRP preemption work?
- Describe the STP root bridge election process.
- How is the root bridge selected (bridge ID = priority + MAC)?
- What are root port, designated port, and blocked port?
- Describe how RSTP achieves faster convergence than STP.
- What are the RSTP port roles?
- What are the RSTP port states?
- Describe how inter-VLAN routing works with an SVI.
- Describe how inter-VLAN routing works with a router-on-a-stick.
- How does an extended ACL match packets?
- What is the implicit deny at the end of every ACL?
- How does standard ACL placement differ from extended ACL placement?
- What is a wildcard mask and how does it differ from a subnet mask?
- How does Cisco implement NetFlow on a router?
- What is the difference between ingress and egress NetFlow on a Cisco interface?
- What is Flexible NetFlow (FNF)?
- Describe the NX-OS VPC (Virtual Port Channel) feature.
- What is the VPC peer link?
- What is the VPC keepalive link?
- What is the VPC peer-gateway feature?

## Why Questions

- Why use HSRP instead of a single default gateway?
- Why use EtherChannel instead of STP-blocked redundant links?
- Why use RSTP instead of classic STP?
- Why use TACACS+ instead of local authentication?
- Why use extended ACLs close to the source?
- Why use standard ACLs close to the destination?
- Why use VPC on Nexus instead of classic STP for dual-homing?
- Why does a trunk port carry multiple VLANs?
- Why is the native VLAN a security concern?
- Why use SNMP v3 instead of v1/v2c on Cisco devices?

## Coding Questions

- Write the IOS commands to create a VLAN and assign it to an access port.
- Write the IOS commands to configure a trunk port with specific allowed VLANs.
- Write the IOS commands to configure an EtherChannel with LACP.
- Write the IOS commands to configure HSRP on an SVI.
- Write the IOS commands to configure a standard ACL to block a host.
- Write the IOS commands to configure an extended ACL to permit HTTP from one subnet to another.
- Write the IOS commands to configure NetFlow on an interface and export to a collector.
- Write the IOS commands to configure SNMPv3.
- Write the IOS commands to configure NTP.
- Write the IOS commands to enable SSH and disable Telnet.

## Edge Cases

- What happens when two routers have the same HSRP priority and preemption is enabled?
- What happens when the HSRP active router loses connectivity to the network but not to the standby?
- What happens when native VLANs mismatch on a trunk?
- What happens when a loop is introduced on a port with PortFast enabled?
- What happens when ACL entries are exhausted in TCAM?
- What happens when VTP domain mismatch causes VLAN database corruption?
- What happens when an EtherChannel hashing algorithm produces uneven distribution?

## Debugging Scenarios

- Users on a VLAN cannot reach the default gateway. How do you investigate?
- HSRP is flapping. What are the likely causes?
- A port is in STP blocking state and should be forwarding. How do you investigate?
- An ACL is blocking traffic that should be permitted. How do you debug?
- NetFlow is not exporting to the collector. How do you troubleshoot?
- SNMP polls are timing out from the management server. How do you investigate?
- EtherChannel is not forming. What do you check?

## System Design Questions

- Design a campus network with redundant Cisco switches and HSRP.
- Design a Cisco-based data center access layer with VPC and EtherChannel.
- Design a network monitoring architecture using Cisco NetFlow and SNMP.
- Design a QoS policy for a Cisco network that prioritizes VoIP traffic.

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [NetFlow](../netflow/questions.md)
- [SNMP](../snmp/questions.md)
- [BGP](../bgp/questions.md)
- [OSPF](../ospf/questions.md)
- [Debugging](../debugging/questions.md)
