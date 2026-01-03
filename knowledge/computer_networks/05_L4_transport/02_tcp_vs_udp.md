## TCP vs UDP 
<img src="../../../media/images/Pasted image 20260103021809.png" align="right" width="45%" style="margin: 20px 0 20px 20px;">

**TCP features:**

- Reliable data transfer
- In-order data segments delivery
- Congestion control
- Flow control
- Connection setup

**UDP features:**

- Unreliable data transfer
- Unordered delivery

**Services not available in both UDP and TCP:**

- Determined delay guarantees
- Security of data transfer

## Full Comparison Table 

| **Feature**                  | **TCP (Transmission Control Protocol)**                                           | **UDP (User Datagram Protocol)**                                        |
| ---------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **Type of Protocol**         | Connection-oriented                                                               | Connectionless (Datagram-oriented)                                      |
| **Connection Establishment** | Requires a connection (3-way handshake: SYN → SYN-ACK → ACK) before data transfer | No connection establishment — sends data directly                       |
| **Reliability**              | Reliable — guarantees delivery of data                                            | Unreliable — no guarantee of delivery                                   |
| **Data Ordering**            | Maintains sequence — packets arrive in the correct order                          | No sequencing — packets may arrive out of order or be duplicated        |
| **Acknowledgment**           | Uses acknowledgment (ACK) segments to confirm receipt                             | No acknowledgment mechanism                                             |
| **Error Control**            | Detects and retransmits lost or corrupted packets                                 | No retransmission — error checking is left to the application layer     |
| **Flow Control**             | Yes — uses sliding window mechanism                                               | No flow control                                                         |
| **Speed**                    | Slower due to overhead (connection setup, acknowledgments, retransmissions)       | Faster and more efficient due to minimal overhead                       |
| **Header Size**              | 20–60 bytes (larger header)                                                       | 8 bytes (very small header)                                             |
| **Handshaking**              | Uses SYN, SYN-ACK, ACK for connection setup and FIN/RST for termination           | No handshaking                                                          |
| **Use Cases**                | Web browsing (HTTP/HTTPS), email (SMTP/IMAP), file transfer (FTP), SSH            | DNS, video streaming, online gaming, VoIP, live broadcasts, IoT devices |
| **Broadcast/Multicast**      | Not supported                                                                     | Fully supported                                                         |
<img src="../../../media/images/Pasted image 20251206164637.png" width="600" style="display: block; margin: auto auto;">

---
## How TCP Works (Connection-Oriented)<img src="../../../media/images/Pasted%20image%2020251206164654.png" align="right" width="430" style="margin: 0 0 20px 30px;">

1. **Connection Establishment** (3-way handshake)  
   → Client sends **SYN**  
   → Server responds with **SYN-ACK**  
   → Client sends **ACK** → Connection established  

2. **Data Transfer**  
   - Data is broken into segments  
   - Each segment has a sequence number  
   - Receiver sends ACK for received segments  
   - Lost packets are retransmitted  

3. **Connection Termination** (4-way handshake)  
   → FIN → ACK → FIN → ACK  
---
## When to use TCP
- When **reliability is important**.
- When the **order of data matters**.
- When some delay is acceptable as long as the data is correct.
---
## How UDP Works (Connectionless)<img src="../../../media/images/Pasted image 20251206164504.png" align="right" width="340" style="margin: 0 0 20px 30px;">

1. Application sends data as datagrams
2. Each datagram is independent
3. Sent directly to the destination (no handshake)
4. No acknowledgment, no retransmission, no ordering
5. Ideal when speed is critical and occasional packet loss is acceptable

**Perfect for real-time applications** where low latency > perfect reliability

---
## When to use UDP
- When **speed is more important than reliability**.
- When **low latency** is critical.
- When the application can tolerate some data loss.
