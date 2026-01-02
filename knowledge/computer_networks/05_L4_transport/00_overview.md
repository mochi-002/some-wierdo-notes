## 1. Introduction

### Transport Layer vs Network Layer

- **Network layer**: logical communication between **hosts**
- **Transport layer**: logical communication between **application processes** running on different hosts

**Analogy** (12 kids in Ann’s house sending letters to 12 kids in Bill’s house):

- hosts = houses
- processes = kids
- app messages = letters in envelopes
- transport protocol = Ann and Bill who collect and distribute letters from/to kids
- network-layer protocol = postal service

### Transport Layer Responsibilities

- Provides **logical communication** between application processes on different hosts
- Responsible for **data transfer between processes**
- Transport layer protocols run in **end systems**
- **Client side**: breaks app messages into **segments** then passes them to the network layer
- **Server side**: reassembles the received segments into messages then passes them to the application layer

<div align="center">
	<img src="Pasted image 20260103015712.png"
</div>

### Transport Layer Functionalities

- Multiplexing and demultiplexing
- Reliable data transfer
- Flow control
- Congestion control

### Transport Layer Protocols

- **UDP**: connectionless / unreliable transport
- **TCP**: connection-oriented reliable transport

## 2. Connection-Oriented vs Connectionless Protocols

### Connection-Oriented Protocols (TCP)

- Establishes a **dedicated connection** between the devices in a network before transmitting data
- This connection is terminated once the communication is over
- **Reliable protocols** that transmit segments or packets to the receiver in the same order the sender has sent them
- Make sure that all data packets are delivered without any errors
- Use a **handshake process** to establish the connection between the devices

### Connectionless Protocols (UDP)

- Doesn’t establish a dedicated connection between devices before transmitting data
- Sends each packet as an **independent unit** and transmits them separately

## 3. TCP vs UDP – Detailed Comparison

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

## 4. Multiplexing and Demultiplexing

**Multiplexing** at sender: The technique of collecting messages from multiple sockets and adding transport headers info (now called **segments** instead of messages) to be used later in demultiplexing.

**Demultiplexing** at receiver: Delivering the received segments at the receiver side to the correct application layer processes using header info

Here are the classic textbook diagrams showing multiplexing and demultiplexing:

### Segment Structure (Common to TCP/UDP)

text