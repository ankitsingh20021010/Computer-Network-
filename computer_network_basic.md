# Computer Networks Basics

Computer Network ka matlab hai **do ya do se zyada computers/devices ko connect karna**, taaki wo aapas mein data aur resources share kar saken.

Example:

```text
Computer A  ─────┐
                 │
Computer B  ─────┼──── Switch ──── Router ──── Internet
                 │
Computer C  ─────┘
```

Network mein computers ke alawa smartphones, servers, printers, routers, switches, IoT devices etc. bhi connected ho sakte hain. .

Computer Networks ko samajhne ke liye humein kuch core concepts pata hone chahiye:

```text
1. Network Basics
2. OSI Model
3. TCP/IP Model
4. IP Address + Subnetting
5. MAC + ARP
6. Hub / Switch / Router
7. TCP vs UDP
8. TCP Handshake
9. DNS + DHCP
10. HTTP / HTTPS
11. NAT
12. Firewall
13. Common Ports
14. Troubleshooting
```

---

# 1. Network Basics

## Network kya hai?

Network devices ka ek group hai jo communication ke liye connected hota hai.

Example:

```text
Laptop ─── Wi-Fi Router ─── Internet ─── Web Server
```

Jab hum browser mein kisi website ko open karte hain, hamara laptop network ke through server se communicate karta hai.

## Network ke important types

### LAN — Local Area Network

Small geographical area mein use hota hai.

Example:

```text
Home
Office
School
Computer Lab
```

### WAN — Wide Area Network

Large geographical area cover karta hai.

Example:

```text
Internet
```

### MAN — Metropolitan Area Network

Ek city ya metropolitan area ke around network.

### PAN — Personal Area Network

Personal devices ka small network.

Example:

```text
Phone ─── Bluetooth ─── Earbuds
```

---

# 2. OSI Model

**OSI = Open Systems Interconnection**

OSI Model networking ko **7 layers** mein divide karta hai.

```text
7 → Application
6 → Presentation
5 → Session
4 → Transport
3 → Network
2 → Data Link
1 → Physical
```

## Layer 1 — Physical Layer

Ye actual physical transmission se related hai.

Examples:

```text
Cable
Electrical Signals
Radio Signals
Fiber Optic
Bits
```

Data yahan **bits** ke form mein travel karta hai.

---

## Layer 2 — Data Link Layer

Ye local network mein data delivery handle karta hai.

Important concept:

```text
MAC Address
Ethernet
Switch
Frame
```

Data Link Layer ka data unit:

```text
Frame
```

---

## Layer 3 — Network Layer

Different networks ke beech data ko route karta hai.

Important concept:

```text
IP Address
Routing
Router
Packet
```

Data unit:

```text
Packet
```

---

## Layer 4 — Transport Layer

End-to-end communication provide karta hai.

Important protocols:

```text
TCP
UDP
```

Data units:

```text
TCP → Segment
UDP → Datagram
```

---

## Layer 5 — Session Layer

Communication sessions ko establish, maintain aur terminate karne se related hai.

---

## Layer 6 — Presentation Layer

Data representation aur transformation se related hai.

Examples:

```text
Encryption
Compression
Data Formatting
```

---

## Layer 7 — Application Layer

User/application ke closest layer hai.

Examples:

```text
HTTP
HTTPS
DNS
FTP
SMTP
SSH
```

### OSI Interview Shortcut

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

Mnemonic:

```text
All People Seem To Need Data Processing
```

---

# 3. TCP/IP Model

TCP/IP Model practical Internet networking mein bahut important hai.

Commonly ise 4 layers mein samjha jata hai:

```text
Application
Transport
Internet
Network Access
```

OSI aur TCP/IP ka rough mapping:

```text
OSI                    TCP/IP

Application       ┐
Presentation      ├──→ Application
Session           ┘

Transport         ───→ Transport

Network           ───→ Internet

Data Link         ┐
Physical          ┴──→ Network Access
```

Important TCP/IP protocols:

```text
TCP
UDP
IP
ICMP
ARP
HTTP
HTTPS
DNS
DHCP
```

---

# 4. IP Address + Subnetting

## IP Address kya hai?

IP address network mein kisi device/interface ko identify karne ke liye use hota hai.

Example IPv4:

```text
192.168.1.10
```

IPv4 mein **32 bits** hote hain.

```text
192.168.1.10
```

Ye 4 octets mein divided hota hai.

Har octet:

```text
8 bits
```

Total:

```text
8 × 4 = 32 bits
```

---

## IPv4 vs IPv6

### IPv4

```text
32-bit
Example:
192.168.1.10
```

### IPv6

```text
128-bit
Example:
2001:db8::1
```

IPv6 ko large number of addresses provide karne ke liye design kiya gaya hai.

---

## Public IP vs Private IP

### Private IP

Local network mein use hota hai.

Common private ranges:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

Example:

```text
192.168.1.20
```

### Public IP

Internet par routable address hota hai.

---

## Subnet Mask

Subnet mask decide karne mein help karta hai ki IP address ka kaunsa part **network** hai aur kaunsa part **host**.

Example:

```text
IP:
192.168.1.10

Subnet Mask:
255.255.255.0
```

CIDR notation:

```text
192.168.1.10/24
```

`/24` ka matlab first 24 bits network portion ke liye hain.

Subnetting ka purpose:

```text
Large Network
     ↓
Smaller Networks
```

Benefits:

* IP addresses ka better management
* Network segmentation
* Broadcast domain control
* Security aur organization improve karna

---

# 5. MAC Address + ARP

## MAC Address

**MAC = Media Access Control**

MAC address generally network interface ko identify karne ke liye Data Link Layer par use hota hai.

Example:

```text
AA:BB:CC:11:22:33
```

IP aur MAC ka basic difference:

```text
IP  → Logical address
MAC → Data-link/hardware address
```

---

## ARP

**ARP = Address Resolution Protocol**

ARP local network mein **IPv4 address se corresponding MAC address find** karne ke liye use hota hai.

Example:

```text
Known:
192.168.1.20

Need:
MAC address
```

ARP request:

```text
"Who has 192.168.1.20?"
```

Jis device ke paas wo IP hota hai, wo apna MAC address reply karta hai.

```text
IP
 ↓
ARP
 ↓
MAC Address
```

Important interview point:

> ARP IPv4 ke liye local network par IP-to-MAC resolution karta hai.

IPv6 mein ARP use nahi hota; IPv6 Neighbor Discovery Protocol (NDP) use karta hai.

---

# 6. Hub / Switch / Router

## Hub

Hub ek basic networking device hai.

Agar data ek port se aata hai, hub use multiple ports par forward karta hai.

```text
       Hub
     /  |  \
   PC1 PC2 PC3
```

Hub mainly **Physical Layer (Layer 1)** device hai.

---

## Switch

Switch MAC address ke basis par frames forward karta hai.

```text
PC1 ──┐
PC2 ──┼── Switch
PC3 ──┘
```

Switch MAC address table maintain karta hai.

Example:

```text
MAC Address          Port

AA:AA:AA:AA:AA:AA → Port 1
BB:BB:BB:BB:BB:BB → Port 2
```

Switch primarily **Data Link Layer (Layer 2)** device hai.

---

## Router

Router different networks ko connect karta hai aur IP addresses ke basis par packets ko forward karta hai.

```text
LAN 1
  |
Router
  |
LAN 2
  |
Internet
```

Router primarily **Network Layer (Layer 3)** se associated hai.

### Quick Difference

```text
Hub    → Broadcasts/forwards to all ports
Switch → MAC address
Router → IP address
```

---

# 7. TCP vs UDP

## TCP

**TCP = Transmission Control Protocol**

TCP connection-oriented aur reliable transport protocol hai.

TCP:

* Connection establish karta hai
* Data delivery ko reliable banane ke mechanisms provide karta hai
* Data ordering maintain karta hai
* Lost data ko retransmit kar sakta hai
* Acknowledgement use karta hai
* Flow control aur congestion control provide karta hai

Example:

```text
A B C D
↓ ↓ ↓ ↓
A B C D
```

Agar data lost ho jaye, TCP recovery mechanisms use kar sakta hai.

---

## UDP

**UDP = User Datagram Protocol**

UDP connectionless aur best-effort transport protocol hai.

UDP:

* Connection establish nahi karta
* Delivery guarantee nahi deta
* Ordering guarantee nahi deta
* Protocol-level retransmission nahi karta
* Low overhead provide karta hai

Example:

```text
A B C D
↓ ↓ X ↓
A B   D
```

### TCP vs UDP

```text
TCP
→ Connection-oriented
→ Reliable
→ Ordered
→ More overhead

UDP
→ Connectionless
→ Best-effort
→ No ordering guarantee
→ Less overhead
```

Common use cases:

```text
TCP → Web, SSH, file transfer
UDP → DNS, gaming, real-time communication
```

---

# 8. TCP 3-Way Handshake

TCP connection establish karne ke liye **3-way handshake** use karta hai.

```text
Client                     Server

  SYN  -------------------->

       <-------------------- SYN + ACK

  ACK  -------------------->
```

Three steps:

```text
1. SYN
2. SYN + ACK
3. ACK
```

Iske baad TCP connection established hota hai aur data transfer start ho sakta hai.

### TCP Connection Termination

TCP connection close karne mein commonly FIN/ACK exchange hota hai aur typical termination ko **4-way termination** ke roop mein explain kiya jata hai.

```text
FIN
ACK
FIN
ACK
```

---

# 9. DNS + DHCP

## DNS

**DNS = Domain Name System**

DNS domain name ko IP address mein resolve karne mein help karta hai.

Human-friendly:

```text
example.com
```

Machine networking ke liye:

```text
IP Address
```

Basic flow:

```text
example.com
     ↓
   DNS
     ↓
IP Address
```

DNS ke common records:

```text
A     → IPv4 address
AAAA  → IPv6 address
CNAME → Alias
MX    → Mail server
NS    → Name server
PTR   → Reverse DNS
```

---

## DHCP

**DHCP = Dynamic Host Configuration Protocol**

DHCP network devices ko automatically configuration provide karta hai.

Common information:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
```

DHCP ka famous process:

```text
D → Discover
O → Offer
R → Request
A → Acknowledgement
```

Isko **DORA** process kehte hain.

```text
Client
  ↓
DHCP Discover
  ↓
DHCP Offer
  ↓
DHCP Request
  ↓
DHCP ACK
```

---

# 10. HTTP / HTTPS

## HTTP

**HTTP = HyperText Transfer Protocol**

Web browser aur web server ke beech communication ke liye HTTP use hota hai.

Example:

```text
Browser
   ↓
HTTP Request
   ↓
Web Server
   ↓
HTTP Response
   ↓
Browser
```

Common HTTP methods:

```text
GET
POST
PUT
PATCH
DELETE
```

Common status codes:

```text
200 → OK
201 → Created
301 → Moved Permanently
400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found
500 → Internal Server Error
```

---

## HTTPS

**HTTPS = HyperText Transfer Protocol Secure**

HTTPS HTTP communication ko TLS ke through secure karta hai.

Main benefits:

```text
Encryption
Authentication
Integrity
```

Common ports:

```text
HTTP  → 80
HTTPS → 443
```

---

# 11. NAT

**NAT = Network Address Translation**

NAT private IP addresses ko public network/Internet communication ke context mein translate karne ke liye commonly use hota hai.

Example:

```text
Laptop
192.168.1.10
     |
     ↓
  Router/NAT
     |
     ↓
Public IP
     |
  Internet
```

Isse multiple private devices ek public IP ke through Internet access kar sakte hain.

---

## PAT

**PAT = Port Address Translation**

PAT NAT ka commonly used form hai jahan ports ka use karke multiple internal connections ko ek public IP ke saath distinguish kiya ja sakta hai.

Home routers mein ye concept commonly use hota hai.

---

# 12. Firewall

Firewall ek security system hai jo network traffic ko predefined rules ke basis par **allow ya block** kar sakta hai.

```text
Internet
   ↓
Firewall
   ↓
Internal Network
```

Firewall rules different information par based ho sakte hain:

```text
Source IP
Destination IP
Port
Protocol
Connection state
```

Example:

```text
TCP Port 443 → Allow
Unknown/blocked traffic → Deny
```

Firewall ka main purpose:

```text
Traffic Control
+
Network Security
```

Firewall ke types ke examples:

```text
Network Firewall
Host-based Firewall
Next-Generation Firewall
```

---

# 13. Common Ports

Networking interviews mein common ports yaad hona useful hai.

```text
FTP       → 20/21
SSH       → 22
Telnet    → 23
SMTP      → 25
DNS       → 53
DHCP      → 67/68
HTTP      → 80
POP3      → 110
IMAP      → 143
HTTPS     → 443
```

Important:

```text
22  → SSH
53  → DNS
80  → HTTP
443 → HTTPS
```

Port number ek host par network service/application ko identify karne mein help karta hai.

Example:

```text
192.168.1.10:443
```

Yahan:

```text
192.168.1.10 → IP address
443           → Port
```

---

# 14. Network Troubleshooting

Interview mein sirf concepts nahi, troubleshooting bhi important hai.

Agar Internet nahi chal raha hai, randomly commands run karne ke bajay systematic approach follow karo.

## Step 1 — Physical connection check

Check:

```text
Cable connected?
Wi-Fi ON?
Network adapter enabled?
Link light?
```

---

## Step 2 — IP configuration check

Check karo device ko IP mila hai ya nahi.

Windows:

```text
ipconfig
```

Linux:

```text
ip addr
```

Check:

```text
IP Address
Subnet Mask
Default Gateway
DNS
```

---

## Step 3 — Loopback test

Common loopback address:

```text
127.0.0.1
```

Test:

```text
ping 127.0.0.1
```

Agar local TCP/IP stack test karna ho to ye useful hai.

---

## Step 4 — Gateway test

Default gateway ko ping karo:

```text
ping <gateway-ip>
```

Example:

```text
ping 192.168.1.1
```

Agar gateway reachable nahi hai, local network issue ho sakta hai.

---

## Step 5 — Internet connectivity test

Kisi known external IP ko test kar sakte ho:

```text
ping 8.8.8.8
```

Agar IP reachable hai lekin domain name resolve nahi ho raha:

```text
ping 8.8.8.8       → works
ping example.com   → fails
```

Toh DNS problem ho sakti hai.

---

## Step 6 — DNS check

DNS resolution test:

```text
nslookup example.com
```

Linux systems par:

```text
dig example.com
```

---

## Step 7 — Route check

Network path dekhne ke liye:

Windows:

```text
tracert example.com
```

Linux/macOS:

```text
traceroute example.com
```

Ye packets ke route/hops ko troubleshoot karne mein useful hain.

---

# Interview Quick Revision

## Important definitions

```text
IP
→ Logical network-layer address

MAC
→ Data-link layer address

ARP
→ IPv4 address se MAC resolution

DNS
→ Domain name resolution

DHCP
→ Automatic network configuration

TCP
→ Reliable, connection-oriented transport

UDP
→ Connectionless, best-effort transport

HTTP
→ Web communication protocol

HTTPS
→ HTTP secured with TLS

NAT
→ Network Address Translation

Firewall
→ Traffic filtering/security system
```

---

# Most Important Differences

## Hub vs Switch vs Router

```text
Hub
→ Layer 1
→ Broadcasts/forwards traffic broadly

Switch
→ Layer 2
→ MAC address

Router
→ Layer 3
→ IP address
→ Different networks connect karta hai
```

## TCP vs UDP

```text
TCP
→ Reliable
→ Connection-oriented
→ Ordered
→ ACK/retransmission mechanisms

UDP
→ Best-effort
→ Connectionless
→ No delivery/order guarantee
→ Low overhead
```

## HTTP vs HTTPS

```text
HTTP
→ Port 80
→ Not encrypted by HTTP itself

HTTPS
→ Port 443
→ HTTP over TLS
→ Secure communication
```

## Public IP vs Private IP

```text
Private IP
→ Internal/local network

Public IP
→ Internet-facing/routable address
```

---

# Final Interview Roadmap

Computer Networks ko interview ke liye is order mein revise karna useful hai:

```text
Network Basics
      ↓
OSI Model
      ↓
TCP/IP Model
      ↓
IP Address
      ↓
Subnetting
      ↓
MAC Address
      ↓
ARP
      ↓
Hub / Switch / Router
      ↓
TCP vs UDP
      ↓
TCP 3-Way Handshake
      ↓
DNS
      ↓
DHCP
      ↓
HTTP / HTTPS
      ↓
NAT / PAT
      ↓
Firewall
      ↓
Common Ports
      ↓
Network Troubleshooting
```
