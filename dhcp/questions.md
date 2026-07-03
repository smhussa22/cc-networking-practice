# DHCP

## Core Concepts

- What is DHCP?

DHCP is a network protocol that stands for Dynamic Host Configuration Protocol. DHCP is used mainly to automatically assign IP addresses to a device, but it also assignes other things like subnet masks, default gateways, & DNS servers.

- Why does DHCP exist?
DHCP exists in order to make connection to a network convenient and easy. Without DHCP, every device that wants to connect to a network, including the network, would have to haev a user manually configure it with a valid IP address (which would be static in this case), subnet mask (defines which part of an IP address identifies network and which part identifies device), and default gateway (the actual device, usually a router, that forwards traffic from local network to other networks, which is required for the internet).

There is a few reasons that this is an issue. The first and most obvious is that it is very time consuming, especially if a network administrator has to manually configure hundreds and maybe even thousands of devices by hand, which also leaves this process open to human error. If any of the configurations (IP address, subnet mask, default gateway) are incorrect, the user can not connect to the network. If two devices share the same IP address, many issues like inconsistent data traffic and crashes occur.

A configuration being "wrong" means that it is incompatible with the network you are trying to join. Here are examples for the three:

### Wrong IP

Suppose on your LAN, it uses router (default gateway) `192.168.1.1`, with devices as `192.168.1.x` and thus a subnet mask of `255.255.255.0`. If a user manually set a device to IP `10.0.0.5`, the device would think it is on the `10.0.0.x` LAN, but every other device would be on `192.168.1.x`. Thus, it would not be able to communicate with other devices, crucially the router, correctly. Router connection is required to connect to the internet, a WAN.

### Wrong Subnet Mask

The subnet mask tells your device which IP addresses are considered local and which would require a router, so if your IP was `192.168.1.50` and a friends is `192.168.1.128`, a subnetm ask of `255.255.255.0` correctly tells your computer the friend is on the same local network and don't need a default gateway (LAN). But if the subnet mask was `255.255.255.128`, your comptuer would think only addresses `192.168.1.0` to `192.168.1.127` are local, cauising communication issues.

You may think that this would only cause the devices to communicate over WAN instead, but teh issue is that the subnet mask is used to decied whether to send packets directly using local network communication (MAC addresses) or to send them to default gateway, and if the subnet mask is incorrect, some devices on LAN are treated as different network.

As a result, teh comptuer may try to sedn traffic to a rotuer that doesn't need to be involved, or it may fail to resolve the device's MAC address, causing packets to get dropped or never delivered. So, instead of just becoming slightly slower, communication usually fails.

### Wrong Default Gateway

Since the default gateway is the device, usually router, that your computer sends traffic to when the destination is ouitside the LAN, if there exists no device at the IP address set as the default gateway, nothing will answer your traffic. LAN is still possible, but it is not possible to reach the internet.

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