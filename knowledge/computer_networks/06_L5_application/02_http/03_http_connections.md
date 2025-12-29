## HTTP Connections

### Types of HTTP Connections

- **Non-persistent HTTP**  
    → New TCP connection for **each object**
- **Persistent HTTP**  
    → Single TCP connection for **all objects**

---

### Non-persistent HTTP

- One TCP connection per object
- Each object requires:
    - **1 RTT** for _TCP_ connection setup
    - **1 RTT** for _HTTP_ request/response

#### Non-persistent HTTP Response Time

1. **Non-Persistent – Without parallel connections**
    - Each object takes **2 RTTs** (1 for TCP connection + 1 for HTTP request/response)
    - Sequential pattern (objects are requested one after another)
2. **Non-Persistent – With parallel connections**
    - Sending multiple objects in **separate and parallel connections**
    - Multiple TCP connections open simultaneously to fetch objects faster

---

<div align="center"> <img src="../../../../media/images/Pasted image 20251229000402.png" width="45%"> <img src="../../../../media/images/Pasted image 20251229000543.png" width="45%"> </div>

---

#### Advantages and Disadvantages of Non-Persistent Connections

**Advantages**

- No wasting of network resources because the connection opens only when there is some data to be sent.
- More secure because after sending the data, the connection gets terminated and nothing can be shared thereafter.

**Disadvantages**

- Requires greater CPU overhead for the transmission of data

---

### Persistent HTTP

- Single TCP connection for multiple objects
- Two main variants:
    - **Non-pipelined**: objects sent sequentially (1 RTT each after initial connection)
    - **Pipelined**: objects sent back-to-back (faster – only 1 RTT after initial connection for all)

---

#### Persistent HTTP Response Time<img src="../../../../media/images/Pasted image 20251228235146.png" align="right" width="480" style="margin: 10px 0 20px 20px;">

1. **Non-Pipelined Persistent Connection**
    - Establish one TCP connection → takes **2 RTTs** (handshake + initial request)
    - Send all the objects sequentially → **1 RTT for each object**
    - **No separate TCP connection** required for each object (saves handshakes)
2. **Pipelined Persistent Connection**
    - All objects sent **back-to-back** over the same connection
    - After the initial **2 RTTs** (for connection + base request), all remaining objects are transferred in **only 1 RTT** total (most efficient)

> Most modern browsers like **Chrome** and **Firefox** use **persistent connections** by default (usually with pipelining where supported).

---

#### Advantages and Disadvantages of Persistent Connections

**Advantages**

- Lower CPU and memory usage because there is less number of connections
- Reduced network congestion (fewer TCP connections)
- Reduced latency in subsequent requests (no handshaking)

**Disadvantages**

- Network resources may be kept occupied even when not needed and may not be available to others

---

### Comparison between HTTP Connections

|Feature|Non-persistent HTTP|Persistent HTTP|
|---|---|---|
|**Objects per TCP connection**|At most **one object** sent over TCP connection, then close connection|**Multiple objects** can be sent over single TCP connection between client and server|
|**Downloading multiple objects**|Requires **multiple connections**|Can use **single connection** (for all or none)|
|**Suitability**|Suitable for pages with **multiple objects**|Either displaying **all page's objects** or not|
|**Typical Behavior**|New TCP connection for each object|Single TCP connection remains open for multiple objects|
|**Overhead**|High (many TCP handshakes)|Low (one handshake for many objects)|

---
