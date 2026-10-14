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
