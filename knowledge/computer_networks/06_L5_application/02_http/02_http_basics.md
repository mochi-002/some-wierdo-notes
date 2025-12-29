## The HTTP Protocol

**Hypertext Transfer Protocol (HTTP)** <img src="../../../../media/images/Pasted image 20251228232907.png" align="right" width="280" style="margin: 20px 0 20px 20px;">

- HTTP is an **application layer** protocol
- Runs at **port 80** at the transport layer
- HTTP messages in **client/server model** are either:
    - **Request**
        - **Client Request**  
            Browser that requests, receives responses from web servers (using HTTP protocol) and "displays" Web objects
    - **Response**
        - **Server Response**  
            Web server sends (using HTTP protocol) objects in response to clients' requests

---

### Using HTTP with TCP<img src="../../../../media/images/Pasted image 20251228233740.png" align="right" width="220" style="margin: 0 0 20px 20px;">

- **TCP 3-Way Handshake**: TCP connection establishes in 3 steps:
    1. Client initiates TCP connection (creates socket) to server at port 80
    2. Server accepts TCP connection from client
    3. HTTP messages exchanged between browser (HTTP client) and Web server (HTTP server)
- HTTP is **stateless** → Server has **no information** about past client requests

---

### Round Trip Time (RTT)<img src="../../../../media/images/Pasted image 20251228234055.png" align="right" width="260" style="margin: 0 0 20px 20px;">

- **Round Trip Time (RTT)**: Time for a small packet to travel from client to server and back → _**RTT = 2 × propagation time**
	
- **Total transmission time** = initial request transmission time + web page objects transmission time
	
- **Initial request transmission time** = **2 RTT** (one for TCP connection request + one for the HTML base file)

---
### HTTP Versions
#### 5.1 HTTP/1.0   
- One request = One TCP connection
- No Keep-Alive
#### 5.2 HTTP/1.1 (1997 – Still widely used)   
- Persistent Connections (Keep-Alive)  
- Pipelining (and its problems)   
- Host Header, Chunked Transfer Encoding 
#### 5.3 HTTP/2 (2015)   
- Binary Protocol   
- Multiplexing (No Head-of-Line blocking)   
- Header Compression (HPACK)   
- Server Push
#### 5.4 HTTP/3 (2022 – Now default in most browsers)   
-  Built on QUIC (UDP-based)   
- 0-RTT & 1-RTT Handshake   
- Built-in Encryption & Faster Connection Migration