# Computer Networks

## 1. OSI Model & TCP/IP Model
### 1.1 The 7 Layers of OSI Model 
<img src="Pasted image 20251206181826.png" width="600" style="display: block; margin: auto auto;">

---
### 1.2 TCP/IP Model (4 Layers)
<img src="Pasted image 20251206183913.png" width="600" style="display: block; margin: 20px auto;">
### 1.3 Comparison with OSI
#### 1. Direct Layer Mapping & Key Functions
> The TCP/IP Model is a pragmatic, implementation-focused architecture that defines the communication protocols used on the Internet. Its four layers correspond to the seven layers of the theoretical OSI Reference Model as follows:

| TCP/IP Layer (4 Layers)               | Corresponding OSI Layers (7 Layers)         | Key Functions / Protocols                                                                                                                                                      |
| ------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **4. Application**                    | 7. Application, 6. Presentation, 5. Session | Provides services to the user and handles data formatting, encryption, and session management. **Protocols:** HTTP, FTP, SMTP, DNS.                                            |
| **3. Transport**                      | 4. Transport                                | Ensures reliable (TCP) or connectionless (UDP) end-to-end communication, segmentation, reassembly, and flow control. **Protocols:** TCP, UDP, SCTP.                            |
| **2. Internet**                       | 3. Network                                  | Responsible for **logical addressing (IP)**, routing data packets (datagrams) across different networks, and path determination. **Protocols:** IP (IPv4, IPv6), ICMP, ARP.    |
| **1. Network Link (Host-to-Network)** | 2. Data Link, 1. Physical                   | Manages physical transmission and data transfer on the local network (LAN/WAN). Handles hardware addressing (MAC) and signaling. **Protocols:** Ethernet, Wi-Fi (802.11), PPP. |
#### 2. Core Differences and Focus

While they describe similar functions, the models differ in their original purpose and structure.

- **Model Goal:**
    - **OSI:** A **conceptual reference model** used to standardize networking for developers. It is _protocol-independent_.
    - **TCP/IP:** An **implementation model** based on the actual, working protocols of the Internet. It is _protocol-dependent_.
- **Layer Count & Structure:**
    - **OSI:** Uses **7 layers**, which offer clearer distinction and separation of services, particularly in the top three layers.
    - **TCP/IP:** Uses **4 layers**, which is more efficient for real-world application but combines several functionalities into the Application and Network Link layers.
- **Adoption:**
    - **OSI:** Used for **teaching and theoretical discussion**.
    - **TCP/IP:** The **foundation of the modern Internet**, making it the practical standard.
---
#### 3. Summary of Comparison

| Feature          | OSI Model (7 Layers)            | TCP/IP Model (4 Layers)                 |
| ---------------- | ------------------------------- | --------------------------------------- |
| **Primary Use**  | Theoretical & Reference         | Implementation & Practice               |
| **Development**  | Developed before protocols      | Developed with the protocols            |
| **Flexibility**  | Less flexible; strict hierarchy | More flexible; designed for robustness  |
| **Key Protocol** | Protocol-independent            | Defined by the IP and TCP/UDP protocols |

---
### 1.4 Encapsulation & De-encapsulation
### 1.5 Protocols in Each Layer (Summary Table)

## 2. IP Basics 
### 2.1 IPv4 vs IPv6 – Header Comparison 
### 2.2 Subnetting & CIDR (Quick Cheat Sheet)
### 2.3 NAT & PAT
## 3. TCP vs UDP – Key Differences 
### 3.1 Full Comparison Table 

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
<img src="Pasted image 20251206164637.png" width="600" style="display: block; margin: auto auto;">

---
<img src="Pasted%20image%2020251206164654.png" align="right" width="430" style="margin: 0 0 20px 30px;">
### 3.2 How TCP Works (Connection-Oriented)

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
### 3.3 When to use TCP
- When **reliability is important**.
- When the **order of data matters**.
- When some delay is acceptable as long as the data is correct.
---
<img src="Pasted image 20251206164504.png" align="right" width="340" style="margin: 0 0 20px 30px;">
### 3.4 How UDP Works (Connectionless)

1. Application sends data as datagrams
2. Each datagram is independent
3. Sent directly to the destination (no handshake)
4. No acknowledgment, no retransmission, no ordering
5. Ideal when speed is critical and occasional packet loss is acceptable

**Perfect for real-time applications** where low latency > perfect reliability

---
### 3.5 When to use UDP
- When **speed is more important than reliability**.
- When **low latency** is critical.
- When the application can tolerate some data loss.

---
## 4. DNS Flow – From Query to Response 
### 4.1 Step-by-Step DNS Resolution (8 Steps Diagram)
### 4.2 Recursive vs Iterative Queries 
### 4.3 DNS Record Types (A, AAAA, CNAME, MX, TXT, NS, SOA, PTR) 
### 4.4 DNS Caching Hierarchy (Browser → OS → Router → ISP) 
### 4.5 DNS over HTTPS (DoH) & DNS over TLS (DoT)
## 5. HTTP Evolution 
### 5.1 HTTP/1.0   
- One request = One TCP connection
- No Keep-Alive
### 5.2 HTTP/1.1 (1997 – Still widely used)   
- Persistent Connections (Keep-Alive)  
- Pipelining (and its problems)   
- Host Header, Chunked Transfer Encoding 
### 5.3 HTTP/2 (2015)   
- Binary Protocol   
- Multiplexing (No Head-of-Line blocking)   
- Header Compression (HPACK)   
- Server Push
### 5.4 HTTP/3 (2022 – Now default in most browsers)   
-  Built on QUIC (UDP-based)   
- 0-RTT & 1-RTT Handshake   
- Built-in Encryption & Faster Connection Migration
## 6. TLS/SSL Handshake 
### 6.1 TLS 1.2 Handshake (Full Steps) 
### 6.2 TLS 1.3 Handshake (Simplified & Faster) 
### 6.3 Session Resumption (Session ID & Session Tickets) 
### 6.4 Difference Between TLS and HTTPS

## 7. WebSockets & Real-Time Communication 
### 7.1 WebSocket Handshake (101 Switching Protocols) 
### 7.2 Full-Duplex Communication 
### 7.3 WebSocket vs Long Polling vs Server-Sent Events (SSE) 
### 7.4 Use Cases (Chat, Live Notifications, Trading Platforms)

## 8. Load Balancing 
### 8.1 Layer 4 (Transport) vs Layer 7 (Application) Load Balancing 
### 8.2 Common Algorithms (Round-Robin, Least Connections, IP Hash) 
### 8.3 Health Checks & Sticky Sessions

## 9. Proxy vs Reverse Proxy 
### 9.1 Forward Proxy vs Reverse Proxy 
### 9.2 Common Tools (Nginx, HAProxy, Envoy, Cloudflare)

## 10. Caching Strategies 
### 10.1 HTTP Caching Headers (Cache-Control, ETag, Last-Modified) 
### 10.2 CDN & Edge Caching 
### 10.3 DNS Caching Recap

## 11. API Communication Styles #
## 11.1 REST vs gRPC vs GraphQL 
### 11.2 When to choose which?

## 12. Advanced & Modern Topics 
### 12.1 QUIC Protocol Deep Dive 
### 12.2 Rate Limiting & Throttling 
### 12.3 Circuit Breaker Pattern 
### 12.4 Connection Pooling & Backpressure