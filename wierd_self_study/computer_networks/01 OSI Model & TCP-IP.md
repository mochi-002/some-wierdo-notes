## 1.1 The 7 Layers of OSI Model 
> The **OSI (Open Systems Interconnection)** model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven abstraction layers.
<img src="Pasted image 20251206181826.png"  align="right" width="430" style="margin: 50px 0 20px 30px;">
### OSI Layers (bottom → top) 
1. **Physical**
2. **Data Link**
3. **Network** 
4. **Transport**
5. **Session**
6. **Presentation**
7. **Application**

---
## 1.2 TCP/IP Model (4 Layers)
> The **TCP/IP model** (also called Internet protocol suite) is the practical model actually used on the Internet.
<img src="Pasted image 20251206183913.png" align="right" width="430" hight="200px" style="margin: 50px 0 20px 30px;">
### TCP/IP Layers (bottom → top)
1. **Network Link** (Host-to-Network)
2. **Internet** 
3. **Transport** 
4. **Application**



---
## 1.3 Comparison with OSI
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
## 1.4 Application Layer – Detailed View

### Application Layer Programs
>Run exclusively on **end systems** (hosts/clients/servers).  
>Network-core devices (routers, switches) **do not** run user applications.

Examples:
- Web browsing
- Email
- File sharing
- Text messaging
- Multi-user network games
- Streaming stored video (YouTube, Netflix…)

### Common Application Layer Protocols
- **HTTP / HTTPS** – Web browsing
- **FTP** – File transfer
- **SMTP** – Sending email
- **IMAP / POP3** – Receiving email
- **DNS** – Domain name resolution

### Two Main Application Architectures

#### 1. Client-Server Architecture

| Feature                     | Server                              | Client                              |
|-----------------------------|-------------------------------------|-------------------------------------|
| Always-on                   | Yes                                 | No (intermittent)                   |
| IP address                  | Permanent / static                  | Usually dynamic                     |
| Scalability                 | Server must scale                   | Clients don’t scale the system      |
| Data management             | Centralized                         | Distributed                         |
| Communication pattern       | Clients ↔ Server                    | Clients **do not** talk directly    |
| Examples                    | Web servers, YouTube, email servers | Browsers, email clients, apps       |

#### 2. Peer-to-Peer (P2P) Architecture

| Feature                        | Description                                           |
|--------------------------------|-------------------------------------------------------|
| Node role                      | Every node is both **client** and **server**          |
| Communication                  | **Direct** peer-to-peer communication                 |
| Always online                  | No – nodes connect intermittently                     |
| IP address                     | Usually dynamic & frequently changing                 |
| Scalability                    | Self-scalable (more users = more resources)           |
| Data management                | Fully distributed                                     |
| Complexity                     | Higher (peer discovery, security, churn management)  |
| Examples                       | BitTorrent, early Skype, some blockchain networks     |

## Quick Architecture Comparison Summary

| Feature                  | Client-Server               | Peer-to-Peer (P2P)              |
|--------------------------|-----------------------------|----------------------------------|
| Always-on server         | Yes                         | No                               |
| Centralized control      | Yes                         | No                               |
| Direct peer communication| No                          | Yes                              |
| Self-scalability         | Limited                     | Excellent                        |
| Management complexity    | Lower                       | Higher                           |
| Typical real-world use   | Web, Email, Streaming       | File sharing, decentralized apps |

---
## 1. Encapsulation & De-encapsulation
## 1. Protocols in Each Layer (Summary Table)
![[Pasted image 20251228210130.png]]