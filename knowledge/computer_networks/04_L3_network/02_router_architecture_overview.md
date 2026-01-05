## Router Architecture Overview
<img src="../../../media/images/Pasted image 20260105034030.png" align="right" width="35%" style="margin: 20px 0 20px 20px;">

- **High-level view of generic router architecture:**
	- **Control plane (software)**
		- Routing Processor
		- Operates in **millisecond time frame**
	- **Forwarding data plane (hardware)**
		- Router input ports
		- High-speed Switching Fabric
		- Router output ports
		- Operates in **nanosecond time frame**

---
## Input Port Functions
<img src="../../../media/images/Pasted image 20260105034427.png" align="right" width="35%" style="margin: 20px 0 20px 20px;">

### Physical Layer
**Main responsibility:** Bit-level reception  

**Key tasks:**
- Receive raw electrical/optical/wireless signal from incoming link
- Clock recovery / synchronization
- Signal amplification and noise filtering
- Convert analog signals back to digital bits
- Line coding/decoding (e.g., Manchester, 8b/10b, 64b/66b)
- Serial-to-parallel conversion for high-speed interfaces

### Data Link Layer
**Example:** Ethernet  

**Main responsibilities:**
- Frame delineation / synchronization
- Error detection (CRC/checksum)
- MAC address handling: discard if not for this router
- Strip data link headers/trailers
- Pass payload (usually IP datagram) to next stage

### Decentralized Switching
**Core principle:** Each input port makes forwarding decisions **independently** → line-rate forwarding at 40/100/400 Gbps+  

**Historical Comparison:**
- **Old (Centralized) Approach** — Inefficient at high speed 
	- Single central CPU performs lookup for **every** incoming packet 
	- Creates a severe performance bottleneck as link speeds increase<img src="../../../media/images/Pasted image 20260105035937.png" align="right" width="35%" style="margin: 20px 0 20px 20px;">

- **Modern (Decentralized) Approach** — Dominant since ~2000 
	- Each input port contains its own fast lookup engine 
	- Complete **forwarding table** is stored **inside each input port** 
	- Lookups happen locally and in parallel across all ports → massive scalability

**Forwarding Decision Process (Input Port):**
The input port uses **header field values** to perform a lookup and determine the output port(s):
1. **Destination-based forwarding** (traditional/classic style) 
	- Forwarding decision based **only** on destination IP address
	- Uses standard longest-prefix match (conventional IP routing table)
2. **Generalized forwarding** (modern/flexible style)
	- Forwarding decision based on **any set** of header field values 
	- Examples: source IP, destination IP, ports, protocol, VLAN tags, MPLS labels, OpenFlow matches, ACL rules, etc.

### Input Buffer (Queueing)

**Purpose:** Temporary storage when packets arrive faster than switch fabric can handle  


**Situations causing input queueing:**
- Multiple input ports targeting same output port simultaneously
- Bursty traffic
- Temporary overload of switch fabric

**Consequence:** Without input buffers → packet loss even if output link is free

<div style="text-align: center;">
  <table style="width: 100%; max-width: 960px; margin: 0 auto; border-collapse: collapse;">
    <thead>
      <tr style="padding: 10px; text-align: ; background-color: #f4f6f8; border-bottom: 1px solid #ccc;">
        <th >Block</th>
        <th >Layer</th>
        <th >Main Tasks</th>
        <th>Color in slides</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Line Termination</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Physical</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Bit-level reception, clock recovery, signal decoding</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Green</td>
      </tr>
      <tr>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Link Layer Protocol</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Data Link</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Frame delineation, CRC check, MAC filtering, Ethernet / PPP</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Orange</td>
      </tr>
      <tr>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Lookup + Forwarding</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Network</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Header parsing → lookup → output port(s)</td>
        <td style="padding: 10px; border-bottom: 1px solid #ddd;">Red</td>
      </tr>
      <tr>
        <td style="padding: 10px;">Input Buffer</td>
        <td style="padding: 10px;">—</td>
        <td style="padding: 10px;">Temporary queue when packets arrive too fast</td>
        <td style="padding: 10px;">Red (bars)</td>
      </tr>
    </tbody>
  </table>
</div>

---
### Destination-Based Forwarding
<img src="../../../media/images/Pasted image 20260105041128.png" align="right" width="45%" style="margin: 20px 0 20px 20px;">

**Description:**  
Destination-Based Forwarding is the process routers use to **send packets to the correct next hop** based solely on the **destination IP address**.  
The router **looks up the destination in its forwarding table** and determines the output port or next hop for the packet.

**Algorithm (Step-by-Step):**
1. Extract **destination IP** from the packet header.
2. Compare the destination against entries in the forwarding table.
3. Select the **matching entry** (or entries) to determine the **output port**.
4. Forward the packet to the next hop/router or directly to the destination.

**Note**
Routers forward packets based only on the **destination IP address** in the packet header.  
They do not consider the source, payload, or application — only *where the packet should go next*.

### Longest Prefix Matching

**Description:**  
Longest Prefix Matching is used when multiple forwarding table entries **could match the destination IP**.  
The router chooses the entry with the **longest matching prefix**, representing the most specific route.
<img src="../../../media/images/Pasted image 20260105041200.png" align="right" width="45%" style="margin: 20px 0 20px 20px;">

**Algorithm (Step-by-Step):**
1. Extract **destination IP** from the packet header.
2. Check **all entries in the forwarding table** whose prefix matches the destination.
3. Compare matching prefixes and **select the longest prefix**.
4. Forward the packet according to that entry’s **output port or next hop**.

**Example:**  
- Forwarding table contains `128.0.0.0/16` and `128.0.1.0/24`.  
- Packet destination = `128.0.1.5`.  
- Both entries match, but `/24` is longer → select `128.0.1.0/24`.

**Note:**  
- Longest Prefix Matching ensures that packets take the **most precise route**, reducing ambiguity in routing.
- If multiple prefixes match the destination address, the router chooses the one with the **most specific (longest) prefix**, because it represents the most precise route.

### Input Port Queuing
<img src="../../../media/images/Pasted image 20260105044456.png" align="right" width="40%" style="margin: 50px 0 20px 20px;">

**1. Why Queuing Happens**
- When **incoming traffic rate exceeds the switching fabric capacity**, packets must wait in **input buffers**.

**Example :**
- A router has **4 input ports**, each sending traffic at **5 Gbps**.
- The **switching fabric can handle only 12 Gbps** in total.    
- Since the combined input rate is **20 Gbps > 12 Gbps**, packets **must wait in input buffers**, forming queues.

**2. Queuing Delay**
- Packets experience **extra latency** while waiting in the buffer.
- Depends on **buffer size** and **current traffic load**.

**3. Packet Loss**
- If the **input buffer fills up**, new incoming packets are **dropped** → data loss.
- This is critical in high-speed networks where **bursty traffic** is common.

**4. Head-of-the-Line (HOL) Blocking**
- **Definition:** The **first packet** in the input queue blocks others behind it, even if their **output ports are free**.
- Example:
    - Front packet wants **output port 1**, but it is busy.
    - Second packet in the queue wants **output port 2**, which is free.
    - It **cannot move forward** until the first packet is sent → reduced throughput.

---
## Switching Fabrics
- **Transfers packet** from input buffer to appropriate output buffer.

- **Switching rate:** Rate at which packets can be transferred from inputs to outputs.  
  - Often measured as a **multiple of input/output line rate**.  
  - With N inputs: Switching rate **N × line rate** is desirable.

- **Three types of switching fabrics:**
  1. Memory
  2. Bus
  3. Crossbar (Interconnection Network)

---

### Switching via Memory (First Generation Routers)
- Traditional computers with switching under **direct CPU control**.  
- Packet is **copied to system memory** before forwarding.  
- **Limitation:** Speed is restricted by **memory bandwidth**.

**Note:** Simple, but not suitable for high-speed routers due to memory bottleneck.

---

### Switching via a Bus
- Datagram moves from **input port memory → shared bus → output port memory**.  
- **Bus contention:** Multiple inputs compete for the same bus → limits switching speed.  
- Example: **32 Gbps bus** in Cisco 5600 is sufficient for **access and enterprise routers**.

**Note:** Works better than memory switching, but cannot scale to very high speeds.

---

### Switching via Interconnection Network (Crossbar)
- Designed to **overcome bus bandwidth limitations**.  
- Crossbar connects **multiple input ports directly to multiple output ports** simultaneously.  
- Example: **Cisco 12000** can switch **60 Gbps** through the interconnection network.

**Note:** High performance, scales well for high-speed backbone routers, but hardware is more complex.

<div align="center">
	<img src="../../../media/images/Pasted image 20260105042353.png" width="800" style="">
</div>

## Output Ports
<img src="../../../media/images/Pasted image 20260105045756.png" align="left" width="35%" style="margin:0px 50px 20px 20px;">

- Datagram buffering is required when datagrams arrive from the **switching fabric faster than the transmission rate** of the output link.  
- **Scheduling discipline** chooses which queued datagram is sent next.  
- Datagrams (packets) can be **lost due to congestion or lack of buffers**.  
- **Priority scheduling:** Determines which packets get best performance; raises questions about **network neutrality**.

---

## Scheduling Mechanisms
<img src="../../../media/images/Pasted image 20260105050048.png" align="right" width="35%" style="margin: 30px 0 0px 20px;">

- **Scheduling:** Mechanism to choose the next packet to send on the output link.  
- **FIFO (First In First Out) scheduling:**  
	- Send packets in order of arrival to the queue.  
- **Discard policies** (if a packet arrives to a full queue):  
	- **Tail drop:** Drop the arriving packet.  
	- **Priority drop:** Remove packets based on priority.  
	- **Random drop:** Remove packets randomly.

**Note:** Proper discard policies are critical for fairness and congestion management.

---
## Scheduling Policies: 
### Priority
<img src="../../../media/images/Pasted image 20260105050339.png" align="right" width="15%" style="margin: -15px 0 0px 20px;">

- **Priority scheduling:** Send the highest priority queued packet first.  
- Supports **multiple classes**, each with different priorities.  
- Packet class may depend on header info, e.g.:  
  - IP source/destination address  
  - Port numbers  
  - VLAN tags, DSCP, or other QoS markings  
- **Example:** Voice traffic might be high priority over bulk file transfers to reduce latency.  

### Still More
<img src="../../../media/images/Pasted image 20260105050541.png" align="right" width="25%" style="margin: -45px 0 0px 20px;">

- **Round Robin (RR) scheduling:**  
	- Works with **multiple classes** of packets.  
	- Cyclically scans class queues, sending **one complete packet from each class** (if available).  
- **Example:** Weighted RR can ensure fair bandwidth distribution among multiple flows.  
- RR avoids **starvation** of lower-priority classes (unlike strict priority scheduling).

---
#### Quick Comparison of Scheduling Policies

| Policy | How it Works | Pros | Cons | Example |
|--------|-------------|------|------|---------|
| FIFO | Send packets in order of arrival | Simple, easy to implement | No differentiation, may delay high-priority traffic | Basic router queues |
| Priority | Send highest priority packet first | Ensures critical traffic gets through | Can starve low-priority packets | VoIP traffic over bulk traffic |
| Round Robin | Cycle through multiple class queues, one packet per class | Fair bandwidth distribution | Slightly more complex | Weighted Fair Queuing in enterprise routers |
