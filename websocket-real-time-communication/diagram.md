# WebSocket Real-Time Communication Diagram

```mermaid
flowchart TD
    A[User A Browser]
    S[WebSocket Server<br/>Real-Time Data]
    B[User B Browser]

    A <-->|WebSocket Connection| S
    S <-->|WebSocket Connection| B
