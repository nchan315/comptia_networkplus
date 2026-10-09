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


