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
Device turns on -> network interface, either ethernet or wifi initializes -> device sends a DHCP discover message to find the DHCP server's address -> DHCP responds with a DHCP Offer message, which contains an available IP address from its IP address pool, a subnet mask, default gateway, length of its lease before the IP must be renewed, and DNS server or servers, i.e., the IP address or addresses of DNS servers that translate domain names into IP addresses. -> device sends a DHCP request saying it wants the address and settings -> DHCP server sends a DHCP ACK, confirming the lease -> device receives all of the previously mentioned settings -> devices can now join the local network and communicate on LAN -> device uses DNS server to translate domain names when accessing website, for example -> since website is outside local network, packets sent to default gateway -> router replaces device's private IP with the home's public IP via Network Address Translation (NAT) -> router forwards packets until they readch destination -> server sends responses back through router, which uses NAT to forward them to correct device

- Explain the DORA process.
  - DISCOVER -> what a device will broadcast (send to every device on LAN) in order to discover the DHCP server
  - OFFER    -> DHCP server responds to a DISCOVER with an offer containing IP address, subnet mask, default gateway, dns servers, and lease length
  - REQUEST  -> device responds to OFFER with a request for those network configurations
  - ACK      -> if successfull, DHCP server responds back with ACK confirming the settings were given

## Packet Fields

- What is xid?                -> "Transaction ID", a 32 bit int set by client to match incoming server replies like offers or acks with its own pending requests; prevents client from confusing responses if multiple reuqests are sent at the same time. In short, it just is used to pair a DHCP request with the correct response; this offer or ack is for the request i just sent.

- What is ciaddr?             -> "Client IP Address", 32 bit IP address the client is currently using if it has one, else 0. Used if client is renewing lease, rebinding, or trying to extend its IP if its alreayd configured. It is only empty during a DISCOVER.
- What is yiaddr?             -> "Your IP  Address", a 32 bit IP address the DHCP server is offering/assigning to the client. Set by DHCP server, not client, appears in OFFER or ACK. Essentially tells client this is your new IP address. Not redundant with ciaddr; initially the ciaddr starts at 0.0.0.0/unset. After device sends out a DISCOVER, server sends a OFFER and sets yiaddr to say `192.168.1.25`. Then, if client sends REQUEST and server ACKs, client configures itself (OS applies network settings) with yiaddr.
- What is giaddr?             -> "Gateway IP Address", 32 bit IP address of the DHCP relay agent, the router, that forwarded the DHCP request. Set by the DHCP relay agent. In home networks the DHCP server is usually inside of a router, so giaddri is typically unused or zero since no need for a relay. But in general network setups, routers act as relay agents, using giaddr to tell the external DHCP server which subnet the request came form. 
- What is the flags field?    -> 16 bits, but under current DHCP specification the leftmost bit is defined and the other 15 are reserved.
- What is the broadcast bit?  -> The leftmost bit in flags. Set by the client to request that the DHCP server broadcast its reply instead of sending it as a unicast packet, useful when the client doesn't have a configured IP address or cant reliably receive the unicast packet. Unicast would be to the clients mac address. For the initial DHCP exchange. broadcasting replies are the norm.

## Lease Management

- What is a lease?
A set amount of time that a device (dhcp client) is allowed to have its IP address assignedb y dhc pserver before it must renew it or have it relinquished back to the DHCP server's pool.
- What is lease expiration?
Occurs when the lease timer runs out and the client has not successfully renewed its lease. DHCP server returns the IP address to the available pool and the client must stop using that address.
- What is T1?
Renewal Time. The point i which the client begins trying to renew its lease with the DHCP server that originally assigned the address, usually at around ~50% of lease duration.
- What is T2?
Rebinding Time. The point in which the client beigns trying to rebind with any available DHCP server if the original server did not respond during renewal. Typically ~87.5% of leasue duration.
- Explain renewal.
At T1,  the client will send a DHCPREQUEST directly to the DHCP server that originally leased the address via unicast. If the server replies with DHCPACK, ten the lease is extended and the lease tiemrs are reset. If there is no response, it continues using its current IP address and will periodically retry until T2. 
- Explain rebinding.
At T2, if the renewal has failed ,the client sends a DHCPREQUEST via broadcast because ti assumes the original server it got a leased address from is not available anymore. Any DHCP server can validate the lease and respond with a DHCPACK, but if no server responds, the client stops using the IP and retries the usual DHCP process of DISCOVER -> OFFER -> REQUEST -> ACK again.
- Explain RELEASE.
DHCPRELEASE; sent by a client voluntarily giving up its IP address. e.g. graceful shtudown or disconnecting from the network. The server immediately returns it sIP address to the avialable pool and no acknowledgement is required.
- Explain DECLINE. 
DHCPDECLINE; sent by a client when it detects that the offered IP address is already in use on the network, usually via ARP (Address Resolution Protocol). The device broadcasts an ARP probe to see if the network responds to that specific IP. If a device responds with its MAC address, the device knows its taken. After this inform, the server marks the address unusable until it can verify it is safe to reassign.
- Explain INFORM.
DHCPINFORM; used by a client that already hasa valid IP but wants additional network config from the DHCP server. The server responds with DHCPACK containing config info like subnet mask, defualt gateway, dns servers, domain name, etc. THe server doesn't modify the client's IP address in this response

## Networking

- Why is DISCOVER broadcast?
In short, because the device does not know where if any DHCP servers exist. The client doesn't have an IP address yet and doesn't know the IP addr of the DHCP server; it needs to broadcast DHCPDISCOVER to allow any potential DHCP server on the LAN to receive it and respond with DHCPOFFER.
- Why isn't OFFER always broadcast?
Because the DHCP server knows the client's MAC address which it sent with DHCPDISCOVER; it cant send the DHCPOFFERR via unicast using that. However, it can still be broadcast if the client requests it via the broadcast bit in DISCOVER, or the client cant receive unicast poackets before its network stack is fully configured.
- What is a DHCP relay?
Usually a router or some form of a layer 3 device that forwards DHCP messages between clients and a DHCP server located on a different subnet. On home networks the DHCP server is usually baked into a router but this is not always the case.
- Why is relay needed?
DHCP clients initially send broadcast messages like DISCOVER, adn routers don't forward these between subnets. If a DHCP server was on a different subnet, then the client cant communicate with it.
- How does DHCP work across subnets?
client broadcasts dhcpdiscover -> relay receives broadcast -> relay forwards DHCPDISCOVER as unicast packet to DHCP server, adds gateway IP (giaddr) to indicate which subnet it came from -> DHCP server uses giaddr to determine which subnet's adderss pool to get an IP from -> server unicast DHCPOFFER back to relay -> relay forwards OFFER to client on local subnet -> remaining DHCPREQUEST AND DHCP ACK messages follow same tpath
## Options

- What are DHCP options?
additional pieced of info included in DHCP messages to provide config details to clients, examples are a default gateway, subnet mask, dns servers, lease time, message type, dns servers, etc. Each option is identified by an option number:

- What is Option 53?
DHCP Message Type. Tells recipient what kind of DHCP message is being sent, e.g. DISCOVER, OFFER, REQUEST, DECLINE, RELEASE, INFORM, ACK, NACK.
- What is Option 50?
Requested IP Address. Used by the client to request a specific IP address. E.g. requesting the IP adddress from the DHCPOFFER or requesting its previous IP after reconnecting to a network.
- What is Option 54?
DHCP Server Identifier. Contaits IP address of DHCP server involved in the transaction, used by cients to identify what server its communicate with especially when multiple respond to a DHCPDISCOVER. 
- What is Option 51?
IP Address Lease Time. 

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