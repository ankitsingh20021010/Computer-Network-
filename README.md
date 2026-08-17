# OSI Model and TCP/IP Model

## 1. OSI Model

**OSI (Open Systems Interconnection) Model** is a conceptual model used to understand how data is transmitted from one computer to another over a network.

The OSI Model has **7 layers**. Each layer performs a specific function and communicates with the layer above and below it.

### OSI Model – 7 Layers

| Layer No. | Layer Name   | Main Function                                | Examples / Protocols    |
| --------- | ------------ | -------------------------------------------- | ----------------------- |
| 7         | Application  | Provides network services to applications    | HTTP, FTP, SMTP, DNS    |
| 6         | Presentation | Data translation, encryption and compression | SSL/TLS, JPEG, MPEG     |
| 5         | Session      | Establishes and manages sessions             | RPC, NetBIOS            |
| 4         | Transport    | End-to-end delivery and reliability          | TCP, UDP                |
| 3         | Network      | Logical addressing and routing               | IP, ICMP                |
| 2         | Data Link    | MAC addressing and frame delivery            | Ethernet, ARP           |
| 1         | Physical     | Transmits raw bits through medium            | Ethernet, Wi-Fi, cables |

---

# 2. Application Layer

**Layer 7 – Application Layer**

The Application Layer is the **topmost layer** of the OSI Model. It provides network services directly to user applications.

It allows applications such as web browsers, email clients and file transfer programs to communicate over a network.

### Main Functions

* Provides network services to applications.
* Allows users to access network resources.
* Supports web browsing, email and file transfer.
* Provides services such as HTTP, FTP and DNS.

### Examples of Protocols

* **HTTP** – Used for web communication.
* **HTTPS** – Secure web communication.
* **FTP** – Used for file transfer.
* **SMTP** – Used for sending emails.
* **DNS** – Converts domain names into IP addresses.

### Example

When we open a website in a browser, the browser uses **HTTP or HTTPS** at the Application Layer.

---

# 3. Presentation Layer

**Layer 6 – Presentation Layer**

The Presentation Layer is responsible for the **format and representation of data**. It makes sure that data sent by one computer can be understood by another computer.

### Main Functions

* Data translation.
* Data encryption and decryption.
* Data compression and decompression.
* Converts data into a suitable format.

### Examples

* JPEG
* PNG
* MPEG
* ASCII
* SSL/TLS

### Example

If data is encrypted before transmission, the Presentation Layer can handle encryption and decryption.

---

# 4. Session Layer

**Layer 5 – Session Layer**

The Session Layer is responsible for **establishing, managing and terminating communication sessions** between two devices.

### Main Functions

* Establishes a communication session.
* Maintains the session.
* Terminates the session.
* Provides synchronization during communication.

### Examples

* RPC
* NetBIOS

### Example

When two systems communicate for a long period, the Session Layer helps maintain the communication session between them.

---

# 5. Transport Layer

**Layer 4 – Transport Layer**

The Transport Layer provides **end-to-end communication** between two devices. It is responsible for reliable delivery of data.

The two important Transport Layer protocols are:

* **TCP (Transmission Control Protocol)**
* **UDP (User Datagram Protocol)**

## TCP

TCP is a **connection-oriented and reliable protocol**.

It provides:

* Reliable data delivery.
* Error checking.
* Flow control.
* Sequencing of data.
* Retransmission of lost packets.

### Example

HTTP/HTTPS commonly uses TCP for reliable communication.

## UDP

UDP is a **connectionless and faster protocol**.

It provides:

* Faster communication.
* Less overhead.
* No guarantee of delivery.
* No retransmission of lost packets.

### Example

UDP is commonly used in:

* Online gaming.
* Live streaming.
* Voice and video communication.
* DNS queries.

---

# 6. Network Layer

**Layer 3 – Network Layer**

The Network Layer is responsible for **logical addressing and routing**. It determines the best path for data to travel from the source device to the destination device.

### Main Functions

* Logical addressing.
* Routing.
* Path selection.
* Packet forwarding.

### Important Protocols

* **IP (Internet Protocol)**
* **ICMP**

## IP Address

An **IP address** is a logical address assigned to a device on a network.

Example:

```text
192.168.1.10
```

IP addresses are mainly used at the **Network Layer**.

---

# 7. Data Link Layer

**Layer 2 – Data Link Layer**

The Data Link Layer is responsible for the **node-to-node delivery of data**. It converts packets into frames and uses MAC addresses for communication within a network.

### Main Functions

* Framing.
* MAC addressing.
* Error detection.
* Controls access to the transmission medium.

### MAC Address

A **MAC (Media Access Control) address** is a unique hardware address associated with a network interface.

Example:

```text
00:1A:2B:3C:4D:5E
```

MAC addresses are mainly used at the **Data Link Layer**.

---

## ARP – Address Resolution Protocol

**ARP** is used to find the **MAC address corresponding to an IP address** in a local network.

### Example

Suppose a computer knows:

```text
IP Address = 192.168.1.5
```

but it does not know the MAC address.

ARP helps find:

```text
192.168.1.5 → MAC Address
```

Therefore:

**ARP = IP Address → MAC Address**

---

## RARP – Reverse Address Resolution Protocol

**RARP (Reverse Address Resolution Protocol)** performs the reverse process of ARP.

It was used to find an **IP address from a MAC address**.

Therefore:

**RARP = MAC Address → IP Address**

RARP is now largely obsolete and has been replaced by protocols such as DHCP.

---

# 8. Physical Layer

**Layer 1 – Physical Layer**

The Physical Layer is the **lowest layer** of the OSI Model. It is responsible for transmitting raw **bits (0s and 1s)** through the physical communication medium.

### Main Functions

* Transmits raw bits.
* Defines cables and connectors.
* Defines electrical and physical signals.
* Defines data transmission speed.
* Handles physical connection between devices.

### Examples

* Ethernet cables.
* Fiber optic cables.
* Radio signals.
* Wi-Fi physical transmission.
* Hubs and repeaters.

### Example

When data is transmitted through a network cable as electrical or optical signals, the Physical Layer is involved.

---

# 9. OSI Layer Order

The seven OSI layers can be remembered from top to bottom as:

```text
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. Data Link
1. Physical
```

### Simple Memory Trick

**A P S T N D P**

> **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

---

# 10. Important Address and Protocol Concepts

## IP Address

IP is used for **logical addressing and routing**.

```text
IP → Network Layer
```

Example:

```text
192.168.1.10
```

## MAC Address

MAC is used for **hardware-level addressing** within a local network.

```text
MAC → Data Link Layer
```

Example:

```text
00:1A:2B:3C:4D:5E
```

## ARP

```text
IP Address → MAC Address
```

## RARP

```text
MAC Address → IP Address
```

## TCP

```text
Reliable + Connection-Oriented
```

## UDP

```text
Fast + Connectionless
```

---

# 11. Port Number

A **port number** is a logical number used to identify a specific application or service running on a device.

Port numbers help the Transport Layer deliver data to the correct application.

### Common Port Numbers

| Service / Protocol | Port Number |
| ------------------ | ----------: |
| HTTP               |          80 |
| HTTPS              |         443 |
| FTP                |          21 |
| SSH                |          22 |
| Telnet             |          23 |
| SMTP               |          25 |
| DNS                |          53 |
| POP3               |         110 |
| IMAP               |         143 |

### Example

When accessing a normal HTTP website:

```text
Protocol = HTTP
Port = 80
```

For HTTPS:

```text
Protocol = HTTPS
Port = 443
```

---

# 12. TCP/IP Model

The **TCP/IP Model** is a networking model used for communication over the Internet.

It was developed through the work of **Vint Cerf and Bob Kahn** in the 1970s. Bob Kahn and Vint Cerf are widely recognized for their major contributions to the development of the TCP/IP architecture and Internet protocols.

The TCP/IP model generally has **4 layers**.

| TCP/IP Layer   | Main Function                        | Examples             |
| -------------- | ------------------------------------ | -------------------- |
| Application    | Provides services to applications    | HTTP, FTP, DNS, SMTP |
| Transport      | End-to-end communication             | TCP, UDP             |
| Internet       | Addressing and routing               | IP, ICMP             |
| Network Access | Physical and data-link communication | Ethernet, Wi-Fi      |

---

# 13. OSI Model vs TCP/IP Model

| OSI Model                                          | TCP/IP Model                                   |
| -------------------------------------------------- | ---------------------------------------------- |
| Has 7 layers                                       | Usually has 4 layers                           |
| Developed by ISO                                   | Developed through ARPA/Internet research       |
| Mainly a reference model                           | Used as the practical Internet protocol model  |
| Application, Presentation and Session are separate | These are combined into Application            |
| Data Link and Physical are separate                | They are commonly combined into Network Access |

### Mapping

```text
OSI Model                  TCP/IP Model

Application      ┐
Presentation     ├──────→ Application
Session          ┘

Transport        ───────→ Transport

Network          ───────→ Internet

Data Link        ┐
Physical         ┴──────→ Network Access
```

---

# 14. Quick Revision

```text
OSI Model = 7 Layers

7 → Application    → HTTP, FTP, DNS
6 → Presentation   → Encryption, Compression
5 → Session        → Session Management
4 → Transport      → TCP, UDP
3 → Network        → IP, ICMP
2 → Data Link      → MAC, ARP
1 → Physical       → Cables, Signals, Bits
```

### Important Points

```text
IP       → Logical Address
MAC      → Hardware Address
ARP      → IP → MAC
RARP     → MAC → IP
TCP      → Reliable
UDP      → Fast / Connectionless
HTTP     → Port 80
HTTPS    → Port 443
TCP/IP   → Internet Protocol Model
Bob Kahn + Vint Cerf → Major contributors to TCP/IP

______________________________________________________________________


# Types of Network Topology

## What is Network Topology?

**Network Topology** refers to the physical or logical arrangement of devices such as computers, switches, routers, and other network devices in a network.

There are two main types:

* **Physical Topology** – How devices and cables are physically connected.
* **Logical Topology** – How data flows between devices.

---

## 1. Bus Topology

In **Bus Topology**, all devices are connected to a single main cable called the **Backbone Cable**.

### Features

* Uses a single backbone cable.
* Easy to install for small networks.
* Requires less cable.
* If the backbone cable fails, the entire network can be affected.

### Example

```text
Computer ── Computer ── Computer ── Computer
              |
        Main Backbone
```

---

## 2. Star Topology

In **Star Topology**, all devices are connected to a central device such as a **Switch or Hub**.

### Features

* Easy to install and manage.
* Failure of one cable affects only one device.
* Failure of the central device can affect the entire network.
* Commonly used in modern LAN networks.

### Example

```text
             Computer
                 |
Computer ─── Switch ─── Computer
                 |
             Computer
```

---

## 3. Ring Topology

In **Ring Topology**, every device is connected to two other devices, forming a circular structure.

### Features

* Data travels around the ring.
* Each device has two connections.
* Failure of one connection can affect the network.
* Can provide predictable data transmission.

### Example

```text
Computer ── Computer
   |           |
Computer ── Computer
```

---

## 4. Mesh Topology

In **Mesh Topology**, devices are connected to multiple or all other devices.

### Types

### Full Mesh

Every device is directly connected to every other device.

### Partial Mesh

Some devices are connected to multiple devices, but not every device is directly connected.

### Features

* Very reliable.
* Provides multiple paths for data.
* Expensive because it requires more cables and connections.
* Used where high reliability is important.

### Example

```text
Computer ───── Computer
   |\           /|
   | \         / |
   |  \       /  |
   |   \     /   |
Computer ───── Computer
```

---

## 5. Tree Topology

**Tree Topology** is a hierarchical topology that combines characteristics of **Star and Bus Topology**.

### Features

* Has a hierarchical structure.
* Easy to expand.
* Suitable for large networks.
* Failure in the main/root connection can affect multiple devices.

### Example

```text
              Main Switch
              /         \
        Switch           Switch
       /     \          /     \
   Computer Computer Computer Computer
```

---

## 6. Hybrid Topology

**Hybrid Topology** is a combination of two or more different network topologies.

For example:

* Star + Bus
* Star + Ring
* Star + Mesh

### Features

* Flexible and scalable.
* Can be designed according to network requirements.
* More complex to design and maintain.
* Commonly used in large organizations.

### Example

```text
       Star Network
          /   \
      Computer Computer
          |
      Main Network
          |
       Ring Network
      /    |     \
 Computer Computer Computer
```

---

## 7. Point-to-Point Topology

In **Point-to-Point Topology**, two devices are directly connected to each other.

### Features

* Simple connection.
* High-speed communication.
* Used between two network devices.
* Easy to configure.

### Example

```text
Computer A ───────── Computer B
```

---

# Comparison of Network Topologies

| Topology       | Structure            | Cost        | Reliability | Common Use             |
| -------------- | -------------------- | ----------- | ----------- | ---------------------- |
| Bus            | Single Backbone      | Low         | Low         | Small/old networks     |
| Star           | Central Switch/Hub   | Medium      | High        | LAN                    |
| Ring           | Circular             | Medium      | Medium      | Specialized networks   |
| Mesh           | Multiple Connections | High        | Very High   | Critical networks      |
| Tree           | Hierarchical         | Medium/High | High        | Large networks         |
| Hybrid         | Combination          | High        | High        | Large organizations    |
| Point-to-Point | Direct Connection    | Low         | High        | Device-to-device links |

---

# Advantages of Network Topology

* Helps organize network devices.
* Makes network design easier.
* Helps identify connection problems.
* Determines network performance and reliability.
* Helps in network expansion and maintenance.

# Conclusion

Network topology defines how devices are connected and how data moves through a network. **Star, Bus, Ring, Mesh, Tree, Hybrid, and Point-to-Point** are the major types of network topology.

> **Most commonly used in modern LANs:** Star Topology.

```
