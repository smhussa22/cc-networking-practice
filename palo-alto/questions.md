# Palo Alto

## Overview

Palo Alto Networks produces next-generation firewalls (NGFW) that use App-ID and User-ID to enforce security policies based on application and user identity rather than just port and protocol. PAN-OS is the operating system running on all Palo Alto physical and virtual firewalls. Panorama is the centralized management platform.

## Conceptual Questions

- What is a Palo Alto next-generation firewall (NGFW)?
- What is PAN-OS?
- What is Panorama?
- What is App-ID?
- What is User-ID?
- What is Content-ID?
- What is a security zone on Palo Alto?
- What is a security policy on Palo Alto?
- What is the difference between Palo Alto security zones and Cisco security zones?
- What is a profile (Security Profile) in PAN-OS?
- What is an Antivirus profile?
- What is a Vulnerability Protection profile?
- What is an Anti-Spyware profile?
- What is a URL Filtering profile?
- What is a File Blocking profile?
- What is a WildFire profile?
- What is WildFire?
- What is threat prevention?
- What is NAT on Palo Alto?
- What is source NAT?
- What is destination NAT?
- What is a virtual router on Palo Alto?
- What is a virtual system (vsys)?
- What is a shared gateway?
- What is a logical router?
- What is IPsec VPN on Palo Alto?
- What is GlobalProtect?
- What is a GlobalProtect gateway?
- What is a GlobalProtect portal?
- What is a HA pair on Palo Alto?
- What is active-passive HA?
- What is active-active HA?
- What is the HA1 link?
- What is the HA2 link?
- What is the election of the HA primary?
- What is a Panorama device group?
- What is a Panorama template?
- What is a pre-rule and post-rule in Panorama?
- What is a local rule?
- What is commit on Palo Alto?
- What is commit-and-push in Panorama?

## Deep Dive Questions

- Describe how App-ID identifies applications.
- What is the App-ID database?
- How does App-ID handle encrypted traffic (SSL decryption)?
- What is SSL Forward Proxy decryption?
- What is SSL Inbound Inspection?
- What is SSH Proxy decryption?
- How does User-ID map usernames to IP addresses?
- What are the User-ID mechanisms: Windows Security Event Log, syslog, XML API, client probe?
- What is User-ID redistribution?
- How does a security policy match in PAN-OS?
- What is the policy match order?
- How does PAN-OS handle the first packet of a session?
- How does PAN-OS handle subsequent packets in an established session?
- What is the App-ID timeout?
- What is the application default port?
- What is an application dependency?
- What is an application sub-application?
- What is an application filter?
- What is an application group?
- Describe how NAT and security policy interact in PAN-OS.
- Is NAT applied before or after security policy for inbound vs outbound traffic?
- What is the NAT policy lookup order?
- How does Palo Alto handle ALG for protocols like SIP and FTP?
- Describe the PAN-OS data plane processing pipeline.
- What is the signature engine?
- What is stream-based inspection?
- What is WildFire sandbox analysis?
- What is a WildFire verdict?
- How does Palo Alto synchronize sessions in HA active-passive mode?
- What is session synchronization?
- What is the HA1 link used for?
- What is the HA2 link used for?
- What is a HA3 link?
- How does Panorama push policy to managed firewalls?
- What is a device group hierarchy in Panorama?
- What is a shared object?
- What is log forwarding in PAN-OS?
- What is a log forwarding profile?
- What is syslog forwarding from PAN-OS?
- What is the Traffic log?
- What is the Threat log?
- What is the URL log?
- What is the Data log?
- What is the Decryption log?
- What is the Tunnel Inspection log?

## Why Questions

- Why use App-ID instead of port-based security policies?
- Why does App-ID see through port obfuscation?
- Why use User-ID instead of IP-based policies?
- Why does SSL decryption require certificate trust?
- Why is WildFire analysis performed asynchronously?
- Why use active-passive HA instead of active-active for stateful firewalling?
- Why use Panorama instead of managing each firewall independently?
- Why does Palo Alto require an application dependency to be permitted?
- Why does PAN-OS process NAT before or after security policy lookup?
- Why is threat prevention applied in the application layer rather than the network layer?

## Coding Questions

- Write PAN-OS CLI commands to create a security zone and assign an interface.
- Write PAN-OS CLI commands to create a security policy permitting a specific application.
- Write PAN-OS CLI commands to configure source NAT.
- Write PAN-OS CLI commands to configure destination NAT.
- Write PAN-OS XML API calls to retrieve the security policy.
- Write PAN-OS XML API calls to add an address object.
- Write Panorama CLI commands to push a policy to a device group.
- Write the CLI command to check App-ID for a specific session.
- Write the CLI commands to run a test policy match.
- Write the CLI commands to check the HA status.

## Edge Cases

- What happens when App-ID changes application mid-session?
- What happens when a security policy allows only the expected application but the port is non-standard?
- What happens when SSL decryption is enabled but the certificate is not trusted by the client?
- What happens when User-ID cannot resolve an IP to a username?
- What happens when HA failover occurs during an active session?
- What happens when WildFire analysis verdicts change after a file has already been allowed?
- What happens when the App-ID timeout expires before the application is identified?
- What happens when NAT pool exhaustion occurs?

## Debugging Scenarios

- Traffic is being blocked but you don't know by which policy. How do you investigate?
- App-ID is identifying traffic as unknown-tcp. How do you investigate?
- SSL decryption is causing certificate errors on clients. How do you debug?
- User-ID mappings are incorrect for a segment. How do you diagnose?
- WildFire is causing latency for file transfers. How do you tune it?
- HA failover is not happening as expected. How do you investigate?
- Panorama push fails to some devices. How do you diagnose?
- A specific application is being blocked even though a policy permits it. Why?

## System Design Questions

- Design a Palo Alto-based perimeter firewall architecture with HA.
- Design an SSL decryption architecture at scale.
- Design a User-ID deployment for a large Active Directory environment.
- Design a Panorama management architecture for 1,000 firewalls.
- Design a WildFire integration for a security operations center.
- Design a zero-trust network architecture using Palo Alto NGFWs.

## Related Topics

- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [Juniper SRX](../juniper-srx/questions.md)
- [Cisco](../cisco/questions.md)
- [Debugging](../debugging/questions.md)
- [System Design](../system-design/questions.md)
