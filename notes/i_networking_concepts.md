# Section 1.0: Networking Concepts

## 1.1: Explain concepts related to the Open Systems Interconnection (OSI) reference model.

OSI Reference Model: describes a seven-layer model used in networking, where data moves from a source (e.g. computer, router, etc.) to a destination

<div align="center">

| Layer    | Name         |
| :---     | :---         |
| Layer 7  | Application  |
| Layer 6  | Presentation |
| Layer 5  | Session      |
| Layer 4  | Transport    |
| Layer 3  | Network      |
| Layer 2  | Data Link    |
| Layer 1  | Physical     |

</div>

- upper layers are application-related (e.g. user interface, data formatting)
- lower layers are transport-related (e.g. data routing, physical characteristics)
- data flows from Layer 7 -> Layer 1 on source device, then Layer 1 -> Layer 7 on destination device
- OSI model describes the tasks that each level of the network must achieve

Protocols: set of rules that network devices use to communicate with one another
- different network protocols exist at each OSI layer
- protocol suites refer to collections of protocols designed to work together as a layered hierarchy (e.g. TCP/IP)
- in the TCIP/IP protocol suite, Layer 5 to 7 are collectively referred to as the Application Layer

Application Layer (Layer 7)
- layer closest to end-user who interacts with a software application
- user may want to send email, load web pages, transfer files, or access remote devices
- example protocols: SMTP, POP3, HTTP, FTP, Telnet

Presentation Layer (Layer 6)
- makes sure data is understandable to the system
- example tasks: formatting, compression, encryption, character representation

Session Layer (Layer 5)
- establishes, manages, and terminates communication sessions between different devices
- tracks conversations using port numbers

Transport Layer (Layer 4)
- receives data from Session Layer and breaks it into transport segments
- ensures data will reach the destination free of errors and in proper order
- responsible for reliability, error checking/correction, data retransmission, flow control, sequenceing, and data multiplexing
- TCP (Transmission Control Protocol): reliable, connection-oriented protocol
- UDP (User Datagram Protocol): unreliable, low overhead, connectionless protocol

Network Layer (Layer 3)
- resposible for routing from source to destination
- controls logical addressing schemes (e.g. IP) that assigns an address to devices on the network

Data Link Layer (Layer 2)
- defines format of data transmitted across the physical network
- example protocols: Ethernet, Wi-Fi

Physical Layer (Layer 1)
- actual physical medium where data travels between devices
- data may travel over copper wires, fiber-optic, radio frequences, etc.

Encapsulation: process of sending data through each layer, each layer adds layer-specific header/trailer
- PDU (protocol data unit): basic block of data exchanged between OSI layers

<div align="center">

| Layer    | Name         | PDU                            |
| :---     | :---         | :---                           |
| Layer 7  | Application  | Data                           |
| Layer 6  | Presentation | Data                           |
| Layer 5  | Session      | Data                           |
| Layer 4  | Transport    | Segment (TCP) / Datagram (UDP) |
| Layer 3  | Network      | Packet                         |
| Layer 2  | Data Link    | Frame                          |
| Layer 1  | Physical     | Bits                           |

</div>

## 1.2: Compare and contrast networking appliances, applications, and functions.

Physical and Virtual Appliances
- physical appliances are dedicated hardware devices; virtual appliances run the same function as software on a hypervisor or in the cloud
- virtual appliances are cheaper and easier to scale, but share host resources and may have lower throughput than dedicated hardware

Router: forwards packets between different networks based on logical (IP) addresses
- operates at Layer 3 (Network)
- uses a routing table to pick the best path to the destination
- separates broadcast domains

Switch: forwards frames between devices on the same network based on MAC addresses
- operates at Layer 2 (Data Link); Layer 3 switches can also route
- learns which MAC addresses are on which ports (MAC address table)
- each port is its own collision domain
- supports VLANs to logically segment a network

Firewall: filters traffic entering or leaving a network based on a set of rules (ACLs)
- rules can allow/deny traffic based on IP address, port number, protocol, etc.
- stateful firewalls track active connections; next-generation firewalls (NGFW) can inspect up to Layer 7

Intrusion Detection System (IDS): monitors network traffic for suspicious activity and generates alerts
- passive: detects and reports, but does not block traffic
- detection methods: signature-based (known attack patterns) and anomaly/behavior-based (deviation from normal baseline)

Intrusion Prevention System (IPS): monitors network traffic and actively blocks malicious activity
- active: sits inline with traffic so it can drop packets, reset connections, or block sources
- false positives can block legitimate traffic

Load Balancer: distributes incoming traffic across multiple servers
- improves performance, availability, and fault tolerance
- if a server fails a health check, traffic is sent to the remaining servers
- example methods: round robin, least connections, weighted

Proxy: intermediary server that makes requests on behalf of clients
- forward proxy: sits in front of clients (e.g. content filtering, caching, hiding client IP)
- reverse proxy: sits in front of servers (e.g. load balancing, SSL offloading, hiding server identity)

Network-Attached Storage (NAS): storage device connected to the network that provides file-level access
- accessed using file-sharing protocols (e.g. SMB, NFS)
- simple to set up; appears as a shared folder/drive to users

Storage Area Network (SAN): dedicated high-speed network that provides block-level access to storage
- appears to servers as locally attached disks
- uses protocols like Fibre Channel, iSCSI, FCoE
- faster and more scalable than NAS, but more complex and expensive

Wireless
- Access Point (AP): device that allows wireless clients to connect to a wired network
    - bridges Wi-Fi (802.11) traffic onto the wired LAN
    - autonomous (standalone) APs are configured individually; lightweight APs are managed by a controller
- Controller (Wireless LAN Controller, WLC): centrally manages multiple lightweight APs
    - handles configuration, firmware updates, channel/power settings, roaming, and security policies

Applications:

Content Delivery Network (CDN): geographically distributed network of servers that cache and deliver content to users from the closest location
- reduces latency and load on the origin server
- commonly used for web pages, images, video streaming, software downloads

Functions:

Virtual Private Network (VPN): creates an encrypted tunnel over an untrusted network (e.g. the internet)
- site-to-site VPN: connects two networks (e.g. branch office to HQ)
- client-to-site (remote access) VPN: connects an individual user to a network
- split tunnel: only traffic for the private network goes through the VPN; full tunnel: all traffic goes through the VPN
- example protocols: IPsec, SSL/TLS

Quality of Service (QoS): prioritizes certain types of network traffic to guarantee performance
- important for latency-sensitive traffic like VoIP and video
- manages bandwidth, latency, jitter, and packet loss
- traffic can be marked/classified (e.g. DSCP at Layer 3, CoS at Layer 2)

Time to Live (TTL): limit on how long data can exist on a network before being discarded
- IP packets: TTL value is decremented by 1 at each router hop; packet is dropped when TTL reaches 0 (prevents routing loops)
- DNS: TTL defines how long (in seconds) a record can be cached before it must be refreshed

## 1.3: Summarize cloud concepts and connectivity options.

Network Functions Virtualization (NFV): replaces dedicated network hardware (e.g. routers, firewalls, load balancers) with software running on standard servers/virtual machines
- the virtual appliances are called virtual network functions (VNFs)
- reduces hardware costs and allows network services to be deployed and scaled quickly

Virtual Private Cloud (VPC): logically isolated, private section of a public cloud where you can launch and control your own resources
- you define your own IP address ranges, subnets, route tables, and gateways
- subnets can be public (reachable from the internet) or private (internal only)

Network Security Groups (NSG): virtual firewall applied to individual resources/instances (e.g. a VM or network interface)
- stateful: return traffic for an allowed connection is automatically allowed
- typically uses allow rules only

Network Security Lists (Network ACLs): virtual firewall applied at the subnet level
- stateless: inbound and outbound traffic must each be explicitly allowed
- supports both allow and deny rules, usually processed in numbered order
- often used together with security groups for layered security

Cloud Gateways: connect a VPC to other networks
- Internet Gateway: allows resources in a public subnet to communicate directly with the internet (both inbound and outbound)
- Network Address Translation (NAT) Gateway: allows resources in a private subnet to initiate outbound connections to the internet, while blocking inbound connections started from the internet
    - translates private IP addresses to a public IP address

Cloud Connectivity Options: ways to connect an on-premises network to a cloud network
- VPN: encrypted tunnel over the public internet
    - quick and inexpensive to set up, but performance depends on the internet connection
- Direct Connect: dedicated private physical connection between on-premises network and cloud provider (e.g. AWS Direct Connect, Azure ExpressRoute)
    - does not go over the public internet: more consistent bandwidth, lower latency, more secure
    - more expensive and takes longer to set up

Deployment Models: describe who owns the cloud infrastructure and who can access it
- public: infrastructure owned by a cloud provider and shared by multiple customers over the internet (e.g. AWS, Azure, Google Cloud)
    - pay-as-you-go, no hardware to manage, but less control
- private: infrastructure dedicated to a single organization, hosted on-premises or by a third party
    - more control and security, but higher cost
- hybrid: combination of public and private clouds that share data/applications
    - e.g. keep sensitive data in private cloud, use public cloud for extra capacity ("cloud bursting")

Service Models: describe how much of the stack the cloud provider manages vs. the customer
- Software as a Service (SaaS): provider manages everything; customer just uses the application (e.g. Microsoft 365, Gmail, Salesforce)
- Platform as a Service (PaaS): provider manages infrastructure and OS/runtime; customer develops and manages their own applications and data (e.g. Heroku, Google App Engine)
- Infrastructure as a Service (IaaS): provider manages physical hardware, networking, storage, and virtualization; customer manages the OS, applications, and data (e.g. AWS EC2, Azure VMs)
- customer responsibility: IaaS (most) > PaaS > SaaS (least)

Scalability: ability to increase (or decrease) resources to handle a change in workload
- vertical scaling (scale up): add more resources to an existing server (e.g. more CPU, RAM)
- horizontal scaling (scale out): add more servers/instances

Elasticity: ability to automatically add or remove resources in real time to match demand
- e.g. auto-scaling adds servers during traffic spikes and removes them when demand drops
- scalability is about handling growth; elasticity is about automatically adjusting to short-term changes

Multitenancy: multiple customers (tenants) share the same physical cloud infrastructure while their data and resources are kept logically isolated
- lowers costs through shared resources
- risks: noisy neighbor (one tenant affecting others' performance), data isolation/security concerns

## 1.4: Explain common networking ports, protocols, services, and traffic types.

<div align="center">

| Protocol                                               | Ports                | Description |
| :---                                                   | :---                 | :---        |
| File Transfer Protocol (FTP)                           | 20, 21 (TCP)         | transfers files between client and server; port 20 = data, port 21 = control; unencrypted |
| Secure File Transfer Protocol (SFTP)                   | 22 (TCP)             | encrypted file transfer that runs over SSH |
| Secure Shell (SSH)                                     | 22 (TCP)             | encrypted remote command-line access to devices |
| Telnet                                                 | 23 (TCP)             | unencrypted remote command-line access (replaced by SSH) |
| Simple Mail Transfer Protocol (SMTP)                   | 25 (TCP)             | sends email between mail servers and from clients to servers; unencrypted |
| Domain Name System (DNS)                               | 53 (TCP/UDP)         | resolves domain names to IP addresses; UDP for queries, TCP for zone transfers/large responses |
| Dynamic Host Configuration Protocol (DHCP)             | 67, 68 (UDP)         | automatically assigns IP addresses and network settings to clients; 67 = server, 68 = client |
| Trivial File Transfer Protocol (TFTP)                  | 69 (UDP)             | simple file transfer with no authentication or directory browsing (e.g. device firmware/config files) |
| Hypertext Transfer Protocol (HTTP)                     | 80 (TCP)             | transfers web pages; unencrypted |
| Network Time Protocol (NTP)                            | 123 (UDP)            | synchronizes clocks between network devices |
| Simple Network Management Protocol (SNMP)              | 161, 162 (UDP)       | monitors and manages network devices; 161 = queries to agents, 162 = traps sent to manager |
| Lightweight Directory Access Protocol (LDAP)           | 389 (TCP)            | accesses and manages directory services (e.g. Active Directory); unencrypted |
| Hypertext Transfer Protocol Secure (HTTPS)             | 443 (TCP)            | HTTP encrypted with TLS |
| Server Message Block (SMB)                             | 445 (TCP)            | Windows file and printer sharing |
| Syslog                                                 | 514 (UDP)            | sends log messages from devices to a central log server |
| Simple Mail Transfer Protocol Secure (SMTPS)           | 587 (TCP)            | SMTP encrypted with TLS (STARTTLS) for client mail submission |
| Lightweight Directory Access Protocol over SSL (LDAPS) | 636 (TCP)            | LDAP encrypted with SSL/TLS |
| Structured Query Language (SQL) Server                 | 1433 (TCP)           | Microsoft SQL Server database connections |
| Remote Desktop Protocol (RDP)                          | 3389 (TCP)           | graphical remote desktop access to Windows machines |
| Session Initiation Protocol (SIP)                      | 5060, 5061 (TCP/UDP) | sets up, manages, and ends VoIP/video calls; 5060 = unencrypted, 5061 = encrypted (TLS) |

</div>

Port Numbers: assigned to different protocol and services so a user knows how and what to access at the other end of specific applications
- 16-bit source/destination port, port number from 0 to 65535
- well-known port numbers generally under 1024 and are permanently assigned
- temporary port numbers are ephemeral and disappear when session is closed
- TCP port number are different from UDP port numbers

Internet Protocol (IP) types
- Internet Control Message Protocol (ICMP): network-layer protocol used by routers and OS's to send error messages and status information
- Transmission Control Protocol (TCP): connection-oriented, reliable delivery protocol
- User Datagram Protocol (UDP): connectionless, unreliable delivery protocol
- Generic Routing Encapsulation (GRE): tunnel between endpoints, encapsulates traffic inside of IP, not encrypted
- Internet Protocol Security (IPSec): security for OSI Layer 3 
    - provides authentication and encryption for every packet
    - headers can be built in transport and tunnel mode
        - transport mode: encrypts/authenticates payload only, original IP header is unchanged
        - tunnel mode: encrypts/encapsulates entire original IP packet with new IP header
    - Internet Key Exchange (IKE): how 2 devices agree on encryption/decryption keys (in order to set up authenticated, encrypted communication channels)
        - must not send key across network
        - builds a Security Association (SA)
        - Phase I: use Diffie-Hellman to create shared secret key
        - Phase II: coordinate ciphers and key sizes
    - Authentication Header (AH): provides data integrity, data origin authentication, and replay protection for IP packets
        - does not provide confidentiality, data is not encrypted
    - Encapsulating Security Payload (ESP): provides data confidentiality, integrity, origin authentication, and replay protection
        - encrypts the payload

Traffic types
- Unicast: one sender, one receiver
- Multicast: one sender, many receivers
- Anycast: one sender, one-of-many recievers (only 1 receiver gets message)
- Broadcast: one sender, everyone in network receives

## 1.5: Compare and contrast transmission media and transceivers.

Wireless
- 802.11 standards: wireless networking standard managed by IEEE

<div align="center">

| IEEE Standard | Generation Name | Frequencies | Maximum theoretical link rate |
| :-- | :-- | :-- | :-- |
| 802.11a | - | 5 GHz | 6 - 54 Mbps |
| 802.11b | - | 2.4 GHz | 1 - 11 Mbps |
| 802.11g | - | 2.4 GHz | 6 - 54 Mbps |
| 802.11n | Wi-Fi 4 | 2.4 GHz / 5 GHz | 72 - 600 Mbps |
| 802.11ac | Wi-Fi 5 | 5 GHz | 433 - 6933 Mbps |
| 802.11ax | Wi-Fi 6 and 6E | 2.4 GHz / 5 GHz / 6 GHz | 574 - 9608 Mbps |
| 802.11be | Wi-Fi 7 | 2.4 GHz / 5 GHz / 6 GHz | 1376 - 46120 Mbps |

</div>

- Cellular: distributed wireless telecommunications system that divides a geographic area into small zones called cells, each serviced by a fixed-location transceiver or base station
    - LTE (AKA 4G): fouther generation cellular networking, up to 150 Mbps
    - 5G: fifth generation cellular networking, up to 10 Gbps
        - due to increased speed, bandwidth becomes less of a constraint, more data con be processed in the cloud

- Satellite: communicate to satellite if no other networking options are available
    - high cost relative to terrestrial networking
    - 100 Mbps download, 5 Mbps upload
    - relatively high latency (approximately 250 ms, but Starlink advertises 40 ms)
    - requires line of sight, may lose connectivity during a storm

Wired: connects computers, switches, and routers using physical cables like Ethernet to provide fast, stable, and secure data transfer
- 802.3 standards: wired networking standards managed by IEEE
    - many standards have information in the standard name
    - speed: 10 Mbps, 100 Mbps, 1000 Mbps, 2.5G, 5G, etc..
    - signal types: baseband (modern Ethernet), broadband, passband
    - media types: twisted pair copper (T), fiber (F), short wavelength light (SX), etc..
    - e.g. 1000BASE-T: max data rate of 1000 Mbps, baseband signaling, twisted-pair copper cabling

- Fiber communication: transmission by light, no RF signal (hard to monitor), good for long distances because signal is slow to degrade
    - single-mode: long range communication (up to 100 km), expensive light source (e.g. laser beams)
    - multimode fiber: short range communication (up to 2 km), inexpensive light source (e.g. LED)

- Copper cabling: carries electrical signals for local area network and telephone systems
    - twisted pair copper cabling: two wires with equal and opposite signals
    - cables don't have speeds, electrical signal encodings determine data transfer rate
    - cables have categories, specific standards need different cable categories
    - direct attach copper (DAC) cable: cable with connector on both ends which link networking devices together
        - coaxial cable: has single central conducted for singled-ended signals
        - twinaxial cable: has two inner conductors, common on 10 Gbps Ethernet
    - Plenum: fake ceilings that connect every working space, used for air conditioning, pipes, and networking cables
        - since plenum cables share the air space, need to use specific cables in case of fires
        - these cables are more fire resistant but not as flexible

Transceivers: combines transmitter and receiver in a single component
- Protocol: transceivers are built to support a specific protocol, must match on both ends
    - Ethernet: the standard LAN protocol, transceivers connect switches, routers, and servers over copper or fiber
    - Fibre Channel (FC): high-speed protocol used in storage area networks (SANs) to connect servers to storage
        - lossless, in-order delivery, commonly 8/16/32/64 Gbps
    
- Form factors: physical size/shape of a modular transceiver that plugs into a port, allows swapping media types (copper, single-mode, multimode) without replacing the device
    - Small form-factor pluggable (SFP): compact, hot-swappable transceiver, single lane
        - SFP: up to 1 Gbps
        - SFP+: up to 10 Gbps
        - SFP28: up to 25 Gbps
    - Quad small form-factor pluggable (QSFP): four lanes in one module, higher bandwidth and higher port density
        - QSFP+: 4 x 10 Gbps = 40 Gbps
        - QSFP28: 4 x 25 Gbps = 100 Gbps

Fiber connectors:
- Subscriber connector (SC): square fiber connector with push-pull latching, 2.5 mm ferrule
    - nicknames: "square connector", "stick and click"
- Local connector (LC): small form factor fiber connector with a latch, 1.25 mm ferrule (half the size of SC)
    - common in SFP transceivers, usually in duplex pairs
    - nickname: "little connector", "lucent connector"
- Straight tip (ST): round fiber connector with a bayonet-style twist-lock
    - older, common in legacy multimode networks
    - nickname: "stick and twist"
- Multi-fiber push on (MPO): single connector holding many fibers (commonly 12 or 24) in a rectangular ferrule
    - used for high-density data center connections and 40/100 Gbps links

Copper connectors:
- RJ11: 6-position connector (usually 2 or 4 wires used), smaller than RJ45
    - used for telephone lines and DSL
- RJ45: 8-position, 8-conductor (8P8C) connector
    - used for twisted-pair Ethernet cabling
- F-type: threaded (screw-on) coaxial connector
    - used for cable TV, cable modems, and satellite
- Bayonet Neill–Concelman (BNC): coaxial connector with a quarter-turn bayonet lock
    - used for legacy 10BASE2 Ethernet, CCTV/video, and test equipment

## 1.6: Compare and contrast network topologies, architectures, and types.

Network design considerations
- Performance: throughput, latency, jitter, and packet loss
- Functionality: services and features the network support
- Flexibility: easy to adapt to new changes without redesigning the network
- Capacity: maximum amount of traffic
- Availability: how much time the network is reachable; needs redundancy, failover, and fault tolerance
- Scalability: how well the network works with more devices

Network Topology: physical/logical arrangeent of nodes, devices, and data flow
- Star/hub and spoke: all devices connect to central device (e.g. switch)
- Mesh: multiple links to same place, redundant, fault-tolerant, used in WANs
    - full mesh: every node is connected to all other nodes
    - partial mesh: critical nodes connected to each other, edge nodes connect to a critical node
- Hybrid: combination of one or more network topology
- Spine and leaf: spine switches connect to all leafs, spines/leafs not connected to each other
    - top-of-rack switching: used in data centers because it is redundant and fast
- Point to point: one-to-one connection

Network Architecture: defines overall design, functional goals, SW/HW components, communication protocols, security policies, and service models
- Three-tier hierarchical model
    - Core: center of network (e.g. web servers, databases, applications)
    - Distribution: midpoint between core and users, manage data flow
    - Access: where uses connect (e.g. end stations, printers)
- Collapsed core: two-tiers (collasped core and access layer)
    - good fit for small organiations, simpler to design and implement, but not as resilient
- Traffic flows
    - North-south: traffic between different locations, needs different security controls
    - East-west: traffic between devices in same data center, fast response times

## 1.7: Given a scenario, use appropriate IPv4 network addressing.

IPv4 networking concepts
- Public addresses: unique addresses used for external communication, can be accessed by every other device on the Internet
- Private addresses: used internally, not advertised on the Internet, can be the same as other private addresses
- Automatic Private IP Addressing (APIPA): 169.254.1.0 to 169.254.254.255, used by Microsoft OS to auto-assign an IP address if not given by DHCP server
- RFC1918: *Address Allocation for Private Internets*, IETF standard that defines reserved private IPv4 address blocks
- Loopback/localhost: 127.0.0.0/8, let computer talk to itself without sending data out to the network

IPv4 address classes

<div align="center">

| Name                | Prefix            | Network Size (bits) |
|---------------------|-------------------|---------------------|
| Class A             | 0                 | 8                   |
| Class B             | 10 (128 - 191)    | 16                  |
| Class C             | 110 (192 - 223)   | 24                  |
| Class D (multicast) | 1110 (224 - 239)  | 32                  |
| Class E (reserved)  | 1111 (240 - 255)  | 32                  |

</div>

Subnetting: process of dividing a large IP network range into smaller sub-networks
- `XXX.XXX.XXX.XXX/XX`, number after `/` is number of fixed bits
- Classless Inter-domain Routing (CIDR): standard that replaces rigid class boundaries
- Variable Length Subnet Mask (VLSM): practice of subnetting a network multiple times using different mask lengths

## 1.8: Summarize evolving use cases for modern network environments.

Software-defined network (SDN): makes networks more programmable and centrally manageable
- 3 layers:
    - data plane (process network frames/packets, forwarding, trunking, encrypting, NAT)
    - control plane (routing tables, session tables, NAT tables, dynamic routing updates)
    - management plane (configuration changes, SSH, browser, API)
- Change network behaviour through software instead of reconfiguring each device
- Software-defined wide area network (SD-WAN): WAN built for the cloud
    - Application aware: WAN knows which app is being used, makes routing decision based on application data
    - Zero-touch provisioning: remote equipment is automatically configured (e.g. routers can manage packet routing)
    - Transport agnostic: can use cable, fiber, 5G, etc..
    - Central policy management: all changes made on 1 central management console

Virtual Extensible Local Area Network (VXLAN): network virtualiation technology that extends Layer 2 Ethernet networks over Layer 3 infrastructure (sending encapsulated data through a VXLAN Tunnel on an IP network)
- Data center interconnect (DCI): connect multiple data centers together although they are geographically far away
- Layer 2 encapsulation: encapsulate Layer 2 frames inside Layer 4 UDP datagrams

Zero trust architecture (ZTA)
- Many networks are open past the firewall, however in ZTA, nothing is inherently trusted, everything must be verified
- E.g. multi-factor authentiction, encryption, system permissions, additional firewalls, monitoring and analytics, etc..
- Policy-based authentication
    - Adaptive identity: consider source and requested resources, risk indicators (e.g. location, IP address, etc..)
    - Policy-driven access control: combine adaptive identity with predetermined set of rules (e.g. time-of-day)
- Authorization: after authentication, authorization is figuring out what rights/permissions a user has
- Least privilege access: bare minimum rights and permissions for all user accounts

Secure Access Secure Edge (SASE): combines SSE security with SD-WAN networking into a cloud-based architecture

Security Service Edge (SSE): subset of SASE that secures access to the web, cloud services, and private applications

Infrastructure as code (IaC): define infrastructure (servers, networks, applications) as code, many benefits:
- Automation:
    - Playbooks/templates/reusable tasks: steps to follow in different situations
    - Configuration drift/compliance: ensure same configuration for all systems
    - Upgrades: easy to make changes in deployed systems
    - Dynamic inventories: query devices in real time and make changes based on results
- Source control: makes it easy to manage changes
    - Version control
    - Central repository
    - Conflict identification
    - Branching

IPv6 addressing
- Mitigating address exhaustion: ran out of addresses in IPv4, IPv6 has larger address space with 128-bit addresses
- groups of zeros can be abbreviated with double colon `::`
- Compatibility requirements: not all devices can use IPv6 (i.e. legacy devices, embedded systems)
    - Tunneling: encapsulate one protocol within another
    - Dual stack: have option to use both IPv4 and IPv6
    - NAT64: convert between IPv4 and IPv6 with NAT64 router in the middle
