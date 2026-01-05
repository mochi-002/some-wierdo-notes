## IP Datagram Format

**Definition:**  
The IP datagram is the basic unit of information passed across an IP network. It consists of:
- **Header**: Control information for routing and delivery    
- **Payload**: Actual data being transported (e.g., TCP/UDP segment)    
<img src="../../../media/images/Pasted image 20260105053545.png" align="right" width="45%" style="margin: 85px 0 0px 20px;">
### 0.1 Key Fields in IPv4 Datagram

- **Version (ver):** IP protocol version number (4 for IPv4, 6 for IPv6)    
- **Header Length (IHL):** Length of header in bytes / 32-bit words    
- **Type of Service / Traffic Class:** Specifies priority and QoS for the packet    
- **Total Length:** Entire datagram size (header + payload)    
- **Identification:** For fragmentation / reassembly    
- **Flags (DF/MF):** Fragmentation control    
- **Fragment Offset:** Position of this fragment in original datagram    
- **Time to Live (TTL / Hop Limit):** Maximum number of hops a packet can traverse    
- **Protocol / Next Header:** Specifies payload type (TCP, UDP, ICMP, etc.)    
- **Header Checksum:** Error checking for header integrity (IPv6 removed)    
- **Source Address:** Sending host IP    
- **Destination Address:** Receiving host IP    
- **Options:** Optional info, e.g., timestamps, route recording (IPv6 uses Extension Headers)    
- **Padding:** Ensures header aligns to 32-bit boundary

**Notes:**

- The payload is typically a **TCP or UDP segment**, but could also be ICMP, routing messages, or other protocols.    
- IPv6 removed some fields (checksum, options, fragmentation info) to **simplify processing** and **increase speed**.

---
## IP Addressing
<img src="../../../media/images/Pasted image 20260105053748.png" align="right" width="25%" style="margin: -35px 0 0px 20px;">

### 0.1 Definition

- **IP address:** 32-bit identifier for host or router interface    
- **Interface:** Connection point between host/router and physical link    
	- **Routers:** Typically multiple interfaces    
	- **Hosts:** Usually 1-2 interfaces (Ethernet, Wi-Fi, etc.)    
- IP addresses are associated with each interface    
<img src="../../../media/images/Pasted image 20260105054037.png" align="left" width="8%" style="margin: 0px 30px 0px 0px;">

- **how are interfaces actually connected?**
	- wired Ethernet interfaces connected by Ethernet switches
	- wireless WiFi interfaces connected by WiFi base station


**Notes:**
- Two hosts in the same subnet can communicate directly; otherwise, packets go through a router.

---
### 0.2 Subnets

- **IP address structure:**    
    - Subnet part: High-order bits        
    - Host part: Low-order bits        
- **Subnet definition:**    
    - Devices with same subnet part can communicate directly        
    - Each isolated network = **subnet**        
- **Subnet mask example:** `/24`    
- **Determining subnets:** Separate interfaces into isolated groups; each group = subnet    

**Visual Example:** 3 subnets in a network
<div align="center">
	<img src="../../../media/images/Pasted image 20260105054422.png" width="30%" style="">
	<img src="../../../media/images/Pasted image 20260105054431.png" width="26%" style="">
</div>

---
### 0.3 CIDR (Classless Inter-Domain Routing)
<img src="../../../media/images/Pasted image 20260105054335.png" align="right" width="600" style="margin: -35px 0 ">

- Allows subnet portion of **arbitrary length**    
- Format: `a.b.c.d/x` (x = number of bits in subnet portion)    

**Example:**

```
11001000 00010111 00010000 00000000 → 200.23.16.0/23
Subnet part: first 23 bits
Host part: remaining 9 bits
```

---
### 0.4 IP Address Allocation

- **Manual assignment:**    
    - System admin / configuration files        
    - Windows: Control Panel → Network → TCP/IP properties        
    - UNIX: `/etc/rc.config`        
- **Dynamic assignment:**
    - DHCP (Dynamic Host Configuration Protocol) for automatic IP assignment        
