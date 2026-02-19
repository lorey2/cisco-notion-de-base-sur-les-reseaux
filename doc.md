ipconfig

SOHO

Small office Home Office

Protocol
- Message format
- Message size
- Timing
- Encoding
- Encapsulation
- Message patern

Ethernet a frame is typically 64 to 1518 bytes

# Protocols

Physically connect device to network Ethernet/WLAN
  DHCP/ICMPv6
    IP address info
    What network I belong to
    Adress of default gateway
      where I send packet that are destined for a different network
    IP address of the DNS server
      If I now domain name but not associated IP address
      www.example.com -> dns -> ip
  IP/TCP
    IP delivery of the packets
    TCP Reliability
  ...

Network Standards Organizations
  IEEE IETF IANA ICANN ITU TIA

  new standard -> Request for Comments (RFC) tracks evolution and gives doc
    IETF are published and managed by IETF

Ethernet: network interface card to network inface card in the same network
IP: from original source to final destination. Make sure that router know where the next hop is
TCP: transmission control protocol reliability and correct sequence order
HTTP: I know


# THE PROTOCOL STACK

tcp/ip:
  - application     HTTP:     data to user, plus encoding and dialog control
  - transport       TCP:      communication between devices in diverse networks
  - internet        IP:       best path through the network
  - network access  Ethernet: control hardware devices and media

# OSI
7. Application    process-to-process comunication
6. Presentation   data transferred between application layer services
5. Session        provides services to the presentation layer to organize its dialogue and to manage data exchage
4. Transport      segment, transfer and reassemble data 
3. Network        provides services to exchange the individual pieces of data over the network bwn identified end devices
2. Data Link      describe methods for exchanging data frames between devices over a common media
1. Physical       mechanical, electrical, fucntional, procedural means to activate maintain deactivete physical connections

link OSI TCP/I{
7/6/5 Application
4     Transport
3     Internet
2/1   Network Access

# Network Media Types
- Unshielded twisted pair (utt) ex: rj45 twister is to reduce interference
- coaxial tv single solid copper cord (metal mesh for shielding)
- fiber optic cable. Glass or plastic surrounded by a second layer of glass or plastic to prevent reflexion
  - No worry about electromagnetic interference bc only light. Can have long distance too. Different types...
- Wireless...

# The access layer
## ETHERNET frame
- 7       bytes preamble                   get the nics in sync
- 1       byte  start frame delimiter(sfd) after that information associated with the ethernet frame 
- 6       bytes destination mac address    destination mac address ON THIS NETWORK
- 6       bytes source mac address         original mac adress
- 2       bytes length type                legth of payload OR what kind of data it is (ipv4 ipv6?,...)
- 46-1500 bytes DATA                       could be IPV4 IPV6 with tcp header and http header,...
- 4       bytes frame check sequence(fcs)  error checking

## ETHERNET switches
Layer 2 of OSI because they make decision based on header of ethernet frame

They have mac address tables that bind a mac adress and the physical ascociated port

### How to build this address table

When the first packet is sent

It can add the source mac adress logically cause it knows the provider
For the destination mac address if it is not in the table it is an unknown unicast.
It will send the packet to every port (but the incoming one). The ones that are not concerned ignore the packet
The switch ONLY adds SOURCE mac address to it's table 

# IPV4 ADDRESS

network   |host
192.168.54.10

255.255.255.0

# IPV4 Unicast Broadcast Multicast

Unicast: 1->1 source must be unicast and destination too
Broadcast: 1-> everyone in the lan (we send to x.x.x.255 or MAC FF:...:FF)
Multicast: 1->everyone that listen to the ip chosen by the sender that must be in this range 224.0.0.0 to 239.255.255.255. It cannot be use through internet

# reserved ip ranges
## private ip range

10.0.0.0/8
172.16.0.0/12 (172.16.0.0 -> 172.31.255.255)
192.168.0.0/16

NAT (Network Address Translation) allows to translate private ip to public so it can go on internet

## loopback address

127.0.0.0/8 or 127.0.0.1 to 127.255.255.254
use to send a packet to myself

## link-local addresses

169.254.0.0 /16 or 169.254.0.1 to 169.254.255.254
Automatic Private IP Addressing (APIPA) addresses or self-assigned addresses.
They are used by a Windows/(linux mac android too) client to self-configure in the event that the client cannot obtain an IP 

# Class of public ip (deprecated)

- Class A (0.0.0.0/8 to 127.0.0.0/8)         for large networks (/8) 16 mio hosts
- Class B (128.0.0.0 /16 - 191.255.0.0 /16)  for moderate to large (/16) 65'000 hosts
- Class C (192.0.0.0 /24 - 223.255.255.0 /24)for small network (/24) 256 hosts

- Note: There is also a Class D multicast block consisting of 224.0.0.0 to 239.0.0.0 and a Class E experimental address block consisting of 240.0.0.0 - 255.0.0.0.

# Assignement of IP Adresses

Internet Assigned Numbers Authority (IANA) manages and allocates blocks of IP addresses to the Regional Internet Registries (RIRs)

<img width="652" height="313" alt="image" src="https://github.com/user-attachments/assets/12ae58d3-83fd-452a-84a1-c76673a38873" />

the router stops propagation of broadcast (arp request or dhcp discover messages) 
arp is address resolution protocol. used to locate other devices
Dynamic Host Configuration Protocol (DHCP) automatically gives private address

# Static or Dynamic IPv4 Address Assignement

to configure network for a host we need at minimum
- ip address
- subnet mask
- default gateway: This identifies the networking device that the host uses to access the internet or another remote network. Usually it is the router ip. (it is used to chose the way if there is two routers)

static addresses are usefull for printers servers,... with ip that should not change
we should keep a list of these static ip

DHCP is for host that can change frequently. Dynamic Host Configuration Protocol
It automatically assign ipn4 address subnet mask default gateway. If ip no longer used it return to the pool

# DHCv4 Configuration

Host send DHCP Discover with broadcast (source 0.0.0.0 destination 255.255.255.255)
DHCP servers respond with a DHCP OFFER with ip address subnet mask and default gateway
Host send DHSC REQUEST to DHCP server
DHCP server send back DHCP ACK







