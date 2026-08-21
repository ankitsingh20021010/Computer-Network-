# 🌐 WebSocket: Real-Time Communication

## 📖 Introduction

In modern web applications, users expect information to update instantly. For example, when someone sends a message on a chat application, the receiver should receive it immediately. Similarly, online games, live notifications, stock market dashboards, and collaborative applications require data to be exchanged in real time.

Traditional HTTP communication follows a **request-response model**. The client sends a request to the server, and the server sends a response back. If the server has new information, it cannot directly send it to the client unless the client makes another request.

To solve this problem, **WebSocket** provides a persistent and two-way communication channel between a client and a server.

WebSocket allows:

```text
Client  ↔  Server
```

Both the client and the server can send data whenever required.

This makes WebSocket useful for building **real-time applications**.

---

# 1. What is WebSocket?

**WebSocket is a communication protocol that provides full-duplex, bidirectional, and persistent communication between a client and a server.**

In simple words:

> WebSocket allows the client and server to stay connected and exchange data instantly without repeatedly creating new connections.

A simple representation is:

```text
┌──────────┐                    ┌──────────┐
│  Client  │  ◀──────────────▶  │  Server  │
│ Browser  │   Real-Time Data   │          │
└──────────┘                    └──────────┘
```

Unlike traditional HTTP communication, both sides can send messages independently.

For example:

```text
Client → Server : Hello

Server → Client : Welcome

Server → Client : New Notification

Client → Server : Send Message
```

The communication can happen in both directions.

---

# 2. Why Do We Need WebSocket?

Traditional web applications were mainly designed around the HTTP request-response model.

For example:

```text
Client → Request → Server

Client ← Response ← Server
```

The server usually sends data only after receiving a request.

Imagine a chat application without WebSocket.

The client would need to repeatedly ask:

```text
Client: Do I have a new message?

Server: No.
```

After a few seconds:

```text
Client: Do I have a new message?

Server: No.
```

Again:

```text
Client: Do I have a new message?

Server: Yes, you received "Hello".
```

This process creates unnecessary requests.

WebSocket solves this problem by keeping a connection open.

```text
Client ═════════════════ Server

       Persistent Connection
```

Now, if new data is available, the server can immediately send it to the client.

```text
Server → Client : New Message!
```

The client does not need to continuously ask for updates.

---

# 3. Important Features of WebSocket

WebSocket provides several important features.

## 3.1 Full-Duplex Communication

WebSocket supports **full-duplex communication**.

This means:

```text
Client  ◀══════════════▶  Server
```

Both the client and server can send and receive data simultaneously.

Example:

```text
Client → Server : Hello

At the same time

Server → Client : New Notification
```

Neither side has to wait for a request-response cycle.

---

## 3.2 Bidirectional Communication

Data can move in both directions.

```text
Client → Server

Server → Client
```

This is useful for applications such as chat systems.

Example:

```text
User A → Server → User B
```

Then:

```text
User B → Server → User A
```

---

## 3.3 Persistent Connection

Once a WebSocket connection is established, it remains open until either the client or server closes it.

```text
Client ========================== Server

         Connection remains open
```

This reduces the need to repeatedly establish new connections.

---

## 3.4 Low Latency

Because the connection is already established, data can be transferred quickly.

```text
Traditional HTTP:

Connect
↓
Request
↓
Response
↓
Close
```

WebSocket:

```text
Connect once
↓
Keep connection open
↓
Send data whenever needed
```

This makes WebSocket suitable for low-latency applications.

---

# 4. WebSocket Protocol

WebSocket is a communication protocol used for real-time communication.

WebSocket URLs use the following schemes:

```text
ws://
```

For secure WebSocket connections:

```text
wss://
```

Example:

```text
ws://example.com/chat
```

Secure version:

```text
wss://example.com/chat
```

The relationship is similar to:

```text
HTTP   → ws

HTTPS  → wss
```

`wss://` encrypts communication using TLS, similar to HTTPS.

---

# 5. HTTP vs WebSocket

One of the easiest ways to understand WebSocket is to compare it with HTTP.

| Feature                      | HTTP                                   | WebSocket                 |
| ---------------------------- | -------------------------------------- | ------------------------- |
| Communication                | Request-Response                       | Two-Way                   |
| Connection                   | Usually request-based                  | Persistent                |
| Server can send data anytime | No, normally requires a client request | Yes                       |
| Communication                | Half-duplex style request-response     | Full-duplex               |
| Real-time support            | Limited                                | Excellent                 |
| Common Use                   | Websites, APIs                         | Chat, games, live updates |

---

## HTTP Communication

A traditional HTTP flow looks like this:

```text
┌────────┐                   ┌────────┐
│ Client │ ─── Request ───▶ │ Server │
│        │ ◀── Response ─── │        │
└────────┘                   └────────┘
```

Example:

```text
GET /messages
```

Server:

```text
Response:
[
  "Hello",
  "How are you?"
]
```

If a new message arrives later, the client must send another request.

---

## WebSocket Communication

With WebSocket:

```text
┌────────┐  ══════════════  ┌────────┐
│ Client │  Persistent Link │ Server │
│        │ ◀══════════════▶ │        │
└────────┘                  └────────┘
```

The server can send data instantly.

Example:

```text
Server → Client

{
  "type": "message",
  "message": "Hello Ankit"
}
```

No new HTTP request is required for every message.

---

# 6. How Does WebSocket Work?

WebSocket communication begins with an HTTP request.

Initially:

```text
Client → HTTP Request → Server
```

The client requests the server to upgrade the connection to WebSocket.

The process is called the **WebSocket Handshake**.

The basic process is:

```text
1. Client sends HTTP request
          ↓
2. Client requests protocol upgrade
          ↓
3. Server accepts WebSocket upgrade
          ↓
4. WebSocket connection established
          ↓
5. Real-time communication begins
```

Diagram:

```text
CLIENT                         SERVER

   │                              │
   │ ─── HTTP Request ──────────▶ │
   │                              │
   │ ◀── Upgrade Accepted ─────── │
   │                              │
   │ ═══ WebSocket Connection ═══ │
   │                              │
   │ ◀════ Real-Time Data ══════▶ │
   │                              │
```

---

# 7. WebSocket Handshake

Before WebSocket communication begins, the client sends an HTTP request containing an upgrade request.

Conceptually:

```text
GET /chat HTTP/1.1

Upgrade: websocket

Connection: Upgrade
```

This tells the server:

> I want to upgrade this connection from HTTP to WebSocket.

If the server supports WebSocket, it accepts the request.

Conceptually:

```text
HTTP/1.1 101 Switching Protocols

Upgrade: websocket

Connection: Upgrade
```

The status code:

```text
101 Switching Protocols
```

means the connection has successfully switched to the WebSocket protocol.

After this, real-time communication begins.

---

# 8. WebSocket Architecture

A simple WebSocket architecture can look like this:

```text
                   ┌─────────────────┐
                   │ WebSocket Server│
                   │                 │
                   │ Real-Time Logic │
                   └────────┬────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              │             │             │
              ▼             ▼             ▼

          ┌───────┐     ┌───────┐     ┌───────┐
          │User A │     │User B │     │User C │
          │Client │     │Client │     │Client │
          └───────┘     └───────┘     └───────┘
```

All clients maintain connections with the WebSocket server.

If User A sends a message:

```text
User A
   │
   │ "Hello"
   ▼
WebSocket Server
   │
   ├────────────▶ User B
   │
   └────────────▶ User C
```

Depending on the application logic, the server can send the message to one user, multiple users, or everyone.

---

# 9. WebSocket Connection Lifecycle

A WebSocket connection generally follows four stages.

## 1. Connecting

The client attempts to connect to the server.

```text
Client → Server
```

Example:

```javascript
const socket = new WebSocket("ws://localhost:8080");
```

---

## 2. Connection Open

The connection is successfully established.

```text
Client  ═════════ Server
```

Now both sides can send and receive data.

---

## 3. Data Transfer

Messages are exchanged.

```text
Client → Server

Server → Client
```

Example:

```text
Client: Hello

Server: Message Received

Server: New Notification
```

---

## 4. Connection Close

When communication is finished, the connection can be closed.

```text
Client ───── X ───── Server
```

The client or server can close the connection.

---

# 10. WebSocket and Real-Time Chat

One of the most common examples of WebSocket is a real-time chat application.

Suppose there are two users.

```text
User A: Ankit

User B: Rahul
```

Ankit sends:

```text
Hello Rahul!
```

The flow is:

```text
Ankit
  │
  │ Hello Rahul!
  ▼
┌───────────────────┐
│ WebSocket Server  │
└─────────┬─────────┘
          │
          │ Hello Rahul!
          ▼
        Rahul
```

Rahul immediately receives the message.

Rahul replies:

```text
Hi Ankit!
```

The flow becomes:

```text
Rahul
  │
  │ Hi Ankit!
  ▼
┌───────────────────┐
│ WebSocket Server  │
└─────────┬─────────┘
          │
          │ Hi Ankit!
          ▼
        Ankit
```

Because the connection is already active, the communication happens in real time.

---

# 11. WhatsApp-Like Chat Architecture

A simplified chat architecture looks like this:

```text
        USER A
          │
          │ WebSocket
          ▼
   ┌───────────────┐
   │               │
   │   CHAT SERVER │
   │               │
   └───────┬───────┘
           │
           │ WebSocket
           ▼
         USER B
```

For multiple users:

```text
                  ┌──────────────┐
                  │ Chat Server  │
                  └──────┬───────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼

      User A           User B           User C
```

The server manages:

* Connected users
* Messages
* Chat rooms
* Online status
* Typing indicators
* Notifications

---

# 12. Example: Chat Message Flow

Suppose User A sends:

```text
Hello!
```

The complete flow:

```text
Step 1

User A
   │
   │ Send Message
   ▼

Step 2

WebSocket Server
   │
   │ Process Message
   ▼

Step 3

Server finds User B
   │
   │ Forward Message
   ▼

Step 4

User B receives:

"Hello!"
```

Diagram:

```text
USER A                 SERVER                 USER B

  │                       │                      │
  │──── "Hello" ─────────▶│                      │
  │                       │──── "Hello" ────────▶│
  │                       │                      │
```

This process can happen almost instantly.

---

# 13. Example: Typing Indicator

WebSocket is also useful for typing indicators.

Example:

```text
Ankit is typing...
```

The process:

```text
User A starts typing
        │
        ▼
WebSocket Server
        │
        ▼
User B sees:

"User A is typing..."
```

When User A stops typing:

```text
User A
  │
  │ Stop Typing Event
  ▼
Server
  │
  ▼
User B

Typing indicator removed
```

This is a real-time event.

---

# 14. Example: Online and Offline Status

WebSocket can also help manage online status.

When a user connects:

```text
User connects
      ↓
WebSocket connection established
      ↓
Server updates status
      ↓
User is Online 🟢
```

When the connection closes:

```text
Connection closed
      ↓
Server detects disconnect
      ↓
User is Offline ⚫
```

Other users can receive this update immediately.

---

# 15. Real-World Applications of WebSocket

WebSocket is used in many applications.

## 💬 1. Real-Time Chat

Examples include chat systems where users need instant messaging.

Features:

* Send messages
* Receive messages
* Typing indicators
* Online status
* Group chat

---

## 🔔 2. Live Notifications

WebSocket can send notifications instantly.

Example:

```text
Server → Client

"You received a new order."
```

The user does not need to refresh the page.

---

## 📈 3. Stock Market Applications

Stock prices change continuously.

```text
Stock Price

₹100
↓
₹102
↓
₹105
↓
₹101
```

WebSocket can push updated prices to users in real time.

---

## 🎮 4. Multiplayer Games

Players need real-time communication.

Example:

```text
Player A moves
       ↓
Server
       ↓
Player B sees movement
```

WebSocket can transfer game events quickly.

---

## 📊 5. Live Dashboards

WebSocket can update dashboards automatically.

Example:

```text
Active Users: 120
       ↓
Active Users: 125
       ↓
Active Users: 140
```

The dashboard updates without refreshing the page.

---

## 📝 6. Collaborative Applications

Applications where multiple users work together.

Example:

```text
User A edits document
        ↓
Server
        ↓
Changes sent to User B
```

This allows users to see updates in real time.

---

# 16. Simple JavaScript WebSocket Example

A browser can create a WebSocket connection using JavaScript.

```javascript
const socket = new WebSocket("ws://localhost:8080");
```

When the connection opens:

```javascript
socket.onopen = function () {
    console.log("Connected to WebSocket Server");
};
```

Sending a message:

```javascript
socket.send("Hello Server");
```

Receiving a message:

```javascript
socket.onmessage = function (event) {
    console.log("Message received:", event.data);
};
```

When the connection closes:

```javascript
socket.onclose = function () {
    console.log("WebSocket connection closed");
};
```

The basic flow is:

```text
Create Connection
       ↓
Connection Opens
       ↓
Send / Receive Messages
       ↓
Connection Closes
```

---

# 17. WebSocket Events

Common WebSocket events include:

| Event     | Purpose                             |
| --------- | ----------------------------------- |
| `open`    | Connection successfully established |
| `message` | Data received from server           |
| `error`   | An error occurs                     |
| `close`   | Connection is closed                |

Example:

```javascript
socket.onopen = () => {
    console.log("Connected");
};

socket.onmessage = (event) => {
    console.log(event.data);
};

socket.onerror = () => {
    console.log("Error occurred");
};

socket.onclose = () => {
    console.log("Disconnected");
};
```

---

# 18. WebSocket Message Example

Data can be sent as text or structured data.

For example, JSON:

```json
{
    "type": "message",
    "sender": "Ankit",
    "message": "Hello Rahul"
}
```

The server receives the data and processes it.

It can then forward the message:

```json
{
    "type": "message",
    "sender": "Ankit",
    "message": "Hello Rahul"
}
```

to the intended user.

---

# 19. WebSocket vs Polling

Before WebSocket, applications often used polling.

Polling means:

```text
Client → Server: Any update?

Server → Client: No
```

After some time:

```text
Client → Server: Any update?

Server → Client: No
```

Again:

```text
Client → Server: Any update?

Server → Client: Yes
```

This creates unnecessary network traffic.

WebSocket:

```text
Client ═══════════════ Server

Server automatically sends:

"New Update!"
```

The client does not need to continuously ask.

---

# 20. WebSocket vs Long Polling

Long polling is another technique used before WebSocket became widely available.

In long polling:

```text
Client sends request
        ↓
Server waits for new data
        ↓
New data available
        ↓
Server sends response
        ↓
Client sends another request
```

WebSocket is different:

```text
Connect once
       ↓
Keep connection open
       ↓
Exchange data continuously
```

---

# 21. Advantages of WebSocket

## 1. Real-Time Communication

Data can be delivered immediately.

```text
Server → Client
```

---

## 2. Two-Way Communication

Both sides can send messages.

```text
Client ↔ Server
```

---

## 3. Persistent Connection

The connection remains open.

This avoids repeatedly creating new connections.

---

## 4. Low Latency

Data can be transferred quickly.

This is useful for:

* Chat
* Gaming
* Live tracking
* Notifications

---

## 5. Reduced Communication Overhead

After the connection is established, WebSocket communication generally has less repetitive request/response overhead than repeatedly using HTTP requests for frequent updates.

---

# 22. Limitations of WebSocket

WebSocket is powerful, but it is not always the best choice.

## 1. Server Resource Usage

Each active connection consumes server resources.

If millions of users remain connected:

```text
1 User
10 Users
1,000 Users
1,000,000 Users
```

The server infrastructure must be designed to handle many simultaneous connections.

---

## 2. More Complex Infrastructure

A simple HTTP API can be easier to build and scale.

WebSocket applications may require handling:

* Connections
* Disconnections
* Reconnection
* Authentication
* Message routing
* Scaling
* Error handling

---

## 3. Connection Management

Internet connections can break.

For example:

```text
Client ═══════ X ═══════ Server
```

The application may need to reconnect automatically.

Example logic:

```text
Connection Lost
       ↓
Wait
       ↓
Try Reconnect
       ↓
Connection Restored
```

---

# 23. WebSocket Security

Secure applications should use:

```text
wss://
```

instead of:

```text
ws://
```

Secure WebSocket communication encrypts data during transmission.

Security considerations include:

* Authentication
* Authorization
* Secure connections
* Input validation
* Rate limiting
* Preventing unauthorized connections

Example:

```text
Client
   │
   │ Secure WebSocket
   ▼

wss://example.com
```

---

# 24. WebSocket and TCP

WebSocket communication runs over a TCP connection.

Simplified protocol structure:

```text
Application Layer
       │
   WebSocket
       │
       TCP
       │
       IP
       │
    Network
```

TCP provides reliable communication between systems.

WebSocket builds a persistent, message-oriented communication mechanism on top of the underlying connection.

---

# 25. WebSocket in Computer Networks

WebSocket is related to several Computer Network concepts.

Important concepts include:

```text
Client-Server Architecture
        ↓
Network Protocols
        ↓
HTTP
        ↓
TCP
        ↓
Persistent Connections
        ↓
Full-Duplex Communication
        ↓
Real-Time Communication
```

Because of these concepts, WebSocket can be studied as a topic under:

# 📚 Subject: Computer Networks

A suitable academic topic name is:

> **WebSocket Protocol and Real-Time Bidirectional Communication**

---

# 26. Technologies That Support WebSocket

WebSocket can be used with many programming languages and technologies.

Examples include:

### JavaScript

```text
Browser WebSocket API
```

### Node.js

WebSocket libraries and frameworks can be used to create real-time servers.

### Java

Java-based backend applications can support WebSocket communication.

### Python

Frameworks and libraries can be used for WebSocket servers.

### PHP

PHP applications can also support real-time WebSocket systems using suitable libraries or server implementations.

---

# 27. Simple Complete Communication Diagram

The complete WebSocket process can be visualized as:

```text
┌──────────────┐
│              │
│    CLIENT    │
│              │
└──────┬───────┘
       │
       │ 1. HTTP Request
       │    Upgrade: WebSocket
       ▼
┌─────────────────────┐
│                     │
│  WEBSOCKET SERVER   │
│                     │
└──────────┬──────────┘
           │
           │ 2. Connection Accepted
           │
           ▼

══════════════════════════════

   Persistent WebSocket Link

══════════════════════════════

CLIENT  ◀══════════════════▶ SERVER

       Real-Time Messages

══════════════════════════════

           │
           │ 3. Connection Close
           ▼

      Communication Ends
```

---

# 28. Real-Time Chat System Architecture

A more detailed chat architecture:

```text
                    INTERNET
                        │
                        ▼

              ┌─────────────────┐
              │                 │
              │ WebSocket Server│
              │                 │
              └───────┬─────────┘
                      │
        ┌─────────────┼──────────────┐
        │             │              │
        ▼             ▼              ▼

   ┌─────────┐   ┌─────────┐   ┌─────────┐
   │ User A  │   │ User B  │   │ User C  │
   │ Browser │   │ Browser │   │ Browser │
   └─────────┘   └─────────┘   └─────────┘
```

Message flow:

```text
User A
   │
   │ Send Message
   ▼
WebSocket Server
   │
   │ Process Message
   ▼
User B
```

---

# 29. Key Concepts

Important terms related to WebSocket:

### Client

The application that connects to the server.

Example:

```text
Web Browser
Mobile Application
Desktop Application
```

---

### Server

The system that accepts WebSocket connections and manages communication.

---

### Connection

The active communication link between client and server.

```text
Client ═══════════ Server
```

---

### Message

The data exchanged through the WebSocket connection.

Example:

```text
Hello!
```

or:

```json
{
    "message": "Hello"
}
```

---

### Full-Duplex

Both sides can communicate simultaneously.

```text
Client ↔ Server
```

---

### Real-Time Communication

Information is delivered immediately or with very low delay.

---

# 30. When Should We Use WebSocket?

WebSocket should be considered when an application requires:

* Instant data updates
* Continuous communication
* Two-way communication
* Low latency
* Real-time events

Examples:

```text
✔ Chat Application

✔ Online Multiplayer Game

✔ Live Notification System

✔ Stock Market Dashboard

✔ Live Tracking

✔ Collaborative Application

✔ Real-Time Monitoring
```

---

# 31. When WebSocket May Not Be Necessary

WebSocket is not required for every application.

For a simple website:

```text
User
  ↓
Requests a page
  ↓
Server sends page
```

Traditional HTTP is usually sufficient.

Examples:

```text
Portfolio Website

Blog

Static Website

Simple REST API

Product Information Website
```

WebSocket should be used when continuous or real-time communication provides an actual benefit.

---

# 32. Summary

WebSocket is a modern communication protocol designed for real-time, bidirectional communication between a client and server.

Unlike traditional HTTP request-response communication:

```text
HTTP:

Client → Request → Server

Client ← Response ← Server
```

WebSocket provides:

```text
Client  ◀══════════════▶  Server

     Persistent Connection
     Full-Duplex Communication
     Real-Time Data Transfer
```

The connection begins with an HTTP handshake and is upgraded to the WebSocket protocol.

After the connection is established:

```text
Client ↔ Server
```

Both sides can send data whenever required.

---

# 🎯 Conclusion

WebSocket is an important technology for building modern real-time applications.

It provides:

* Persistent connections
* Bidirectional communication
* Full-duplex data transfer
* Low-latency messaging
* Instant updates

A simple way to remember WebSocket is:

```text
HTTP:

"Client asks → Server answers"
```

while WebSocket is:

```text
"Client and Server stay connected
and either one can send data anytime."
```

This makes WebSocket highly suitable for applications such as:

```text
💬 Real-Time Chat
🔔 Live Notifications
🎮 Multiplayer Games
📈 Live Market Data
📊 Real-Time Dashboards
📝 Collaborative Applications
🟢 Online/Offline Status
```

---

## 📚 Subject Classification

```text
Subject: Computer Networks

Main Topic:
WebSocket Protocol and Real-Time Communication

Related Concepts:
- Client-Server Architecture
- HTTP
- TCP
- Network Protocols
- Persistent Connections
- Full-Duplex Communication
- Real-Time Systems
```

**Repository suggestion:**

```text
websocket-real-time-communication
```
