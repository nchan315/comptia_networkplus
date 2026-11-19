# Section 2.0: Network Implementation

## 2.1: Explain characteristics of routing technologies.

Routing tables determine where to send packet
- destination IP on locally connected subnet, forward packet to local device
- destination IP on remote subnet, foward packet to next-hop router/gateway

Static routing: administratively defined routes
- pros: easy to configure, no overhead from routing protocols, easy to configure, more secure
- cons: difficult to administer on large networks, no automated way to prevent routing loops, no automatic rerouting, manually update routes if network changes

Dynamic routing: router tables are updated in real-time
- pros: no manual route calculation, new routes populated automatically, very scalable
- cons: some router overhead, requires initial configuration to work properly

Dynamic routing protocols: listen and provide subnet information to and from other routers, then determine best path based on this information
- Border Gateway Protocol (BGP)
- Enhanced Interior Gateway Routing Protocol (EIGRP)
- Open Shortest Path First (OSPF)

Route selection
- Administrative distance
- Prefix length
- Metric

Address translation
- NAT
- Port address translation (PAT)

First Hop Redundancy Protocol (FHRP)

Virtual IP (VIP)

Subinterfaces

## 2.2: Given a scenario, configure switching technologies and features.

 Virtual Local Area Network (VLAN) − VLAN database − Switch virtual interface (SVI)
•  Interface configuration − Native VLAN − Voice VLAN − 802.1Q tagging − Link aggregation − Speed − Duplex

Spanning tree
•  Maximum transmission unit (MTU) − Jumbo frames

## 2.3: Given a scenario, select and configure wireless devices and technologies.

Channels: groups of frequencies, numbered by IEEE
- Channel width: frequency range occpied by a single Wi-Fi channel
    - narrow channels are more stable, penetrate walls better, and allow more non-overlapping channels
    - wider channels are faster but less channels are available
- Non-overlapping channels: if channels are not spaced far enough, their signals will interfere with each other
- Regulatory impacts: national frequency allocations manage wireless spectrum
    - 802.11h: adds interoperability features to 802.11
        - Dynamic Frequency Selection (DFS): avoid frequency conflicts by having access point switch to unused frequencies
        - Transmit Power Control (TPC): access point determines power output of the client

Frequency options: tradeoffs between range and speed
- higher frequencies are faster with less interference, lower frequencies travel farther and penetrate walls better
- common frequencies: 2.4GHz, 5GHz, 6GHz
- Band steering: choose best frequency based on device's hardware capabilities and connection quality

Service set identifier (SSID): every wireless network has a name
- Basic service set identifier (BSSID): one SSID has multiple access points, each access point has unique ID
- Extended service set identifier (ESSID): network name shared across many access points, devices move access points seamlessly when device moves
- Autonomous AP: operates independently with local configuration and control
- Lightweight AP: relies on a centralized Wireless LAN Controller to manage policies, security, and roaming

Network types
- Mesh networks: full mesh (every nodes connected to all other nodes) and partial mesh
- Ad hoc: two devices communicate with each other using 802.11 without an access point (e.g. IoT device)
- Point to point: dedicated communication link that connects exactly 2 nodes directly
- Infrastructure: hardware, software, cabling, and services that enable networks to function

Encryption
- Wi-Fi Protected Access 2 (WPA2): uses AES-CCMP with 128-bit keys to encrypt Wi-Fi traffic
- WPA3: modern standard, uses AES-GCM/GCMP with 192-bit encryption

Guest networks
- Captive portals: allow users to authenticate on the network

Authentication
- Pre-shared key (PSK): password shared between 2 parties before encrypted communication
    - simplest is a Wi-Fi password that everyone uses
    - can also be used to authenticate endpoints before communicating (e.g. VPN)
- Enterprise: authenticate users individually with authentication server (e.g. RADIUS, LDAP)

Antennas
- Omnidirectional: signal distributed evenly on all sides
- Directional: signal focus on specific direction

## 2.4: Explain important factors of physical installations.

Important installation implications
- Locations
    - Main distribution frame (MDF): central point of the network, termination point for WAN links
    - Intermediate distribution frame (IDF): extension of MDF, connects the users to the network
- Rack size: racks generally are standard size
    - widths are 19"
    - heights measured in rack units, 1U is 1.75", generally 42U tall
    - depth is variable
- Port-side exhaust/intake: HVAC systems is very important
    - data centers optimize cooling (hot/cold aisles)
- Cabling: goal is to never touch cables after they are installed
    - Patch panel: hardware unit containing multiple ports used to organize and connect circuits
        - all cables are managed at the back of the patch panel
        - e.g. connect users to a switch, can be changed
    - Fiber distribution panel: fiber can't be bent too tightly otherwise wires will snap
- Lockable: some racks are locked but ventilation still can go through

Power
- Uninterruptible power supply (UPS): short-term backup power from batteries
- Power distribution unit (PDU): provide multiple power outlets, can monitor and control devices
- Power load: electrical load in a circuit (Watts = Volts $\times$ Amps)
- Voltage: difference in electric PE per unit charge between 2 points

Environmental factors
- Humidity: high humidity promotes condensation, low humidity promotes static discharge
    - ideal humidity is 40% - 60%
- Fire suppression: don't use water, use other chemicals/remove oxygen
- Temperature: optimal temperature is $17.7 \degree \text{C}$ to $27.2 \degree \text{C}$
