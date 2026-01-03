### Transport Layer vs Network Layer
<img src="../../../media/images/Pasted image 20260103015712.png" align="right" width="25%" style="margin: 20px 0 20px 20px;">

- **Network layer**: logical communication between **hosts**
- **Transport layer**: logical communication between **application processes** running on different hosts

**Analogy** (12 kids in Ann’s house sending letters to 12 kids in Bill’s house):

- hosts = houses
- processes = kids
- app messages = letters in envelopes
- transport protocol = Ann and Bill who collect and distribute letters from/to kids
- network-layer protocol = postal service


### Transport Layer Responsibilities
<img src="../../../media/images/Pasted image 20260103023130.png" align="right" width="30%" style="margin: 20px 0 20px 20px;">

- Provides **logical communication** between application processes on different hosts
- Responsible for **data transfer between processes**
- Transport layer protocols run in **end systems**
- **Client side**: breaks app messages into **segments** then passes them to the network layer
- **Server side**: reassembles the received segments into messages then passes them to the application layer

### Transport Layer Functionalities

- Multiplexing and demultiplexing
- Reliable data transfer
- Flow control
- Congestion control

### Transport Layer Protocols

- **UDP**: connectionless / unreliable transport
- **TCP**: connection-oriented reliable transport

## Connection-Oriented vs Connectionless Protocols

### Connection-Oriented Protocols (TCP)

- Establishes a **dedicated connection** between the devices in a network before transmitting data
- This connection is terminated once the communication is over
- **Reliable protocols** that transmit segments or packets to the receiver in the same order the sender has sent them
- Make sure that all data packets are delivered without any errors
- Use a **handshake process** to establish the connection between the devices

### Connectionless Protocols (UDP)

- Doesn’t establish a dedicated connection between devices before transmitting data
- Sends each packet as an **independent unit** and transmits them separately
