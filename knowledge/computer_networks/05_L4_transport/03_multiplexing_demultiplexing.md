## Multiplexing and Demultiplexing

**Multiplexing** at sender: The technique of collecting messages from multiple sockets and adding transport *headers info* (now called **segments** instead of messages) to be used later in demultiplexing.

**Demultiplexing** at receiver: Delivering the received segments at the receiver side to the correct application layer processes using *header info*

<div align="center">
	<img src="../../../media/images/Pasted image.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

### Segment Structure (Common to TCP/UDP)
<img src="../../../media/images/Pasted image 20260103022931.png" align="right" width="17%" style="margin: -20px 0 20px 20px;">

- **Segments** are created at the hosts/clients side by Covering data messages with **transport layer information**
- Each segment has:
    - **Source IP address** and **destination IP address**
    - **Source port number** and **destination port number**
- The **network layer** uses **client sockets** (source IP address & source port number) to direct the segment to the appropriate **server sockets** (destination IP address and destination port number).

### Connectionless Demultiplexing (UDP)

- Server receives all data segments with **same destination port number** even from multiple hosts/clients (different source IP addresses) on the **same server socket**
- No need to open socket connection to each client → one server socket for all clients
<div align="center">
	<img src="../../../media/images/Pasted image 20260103023718.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

### Connection-Oriented Demultiplexing (TCP)

- Server receives data segments on **different server sockets** from multiple hosts/clients
- Web servers have different sockets for each connecting client
- TCP socket identified by **4-tuple**: 
	1. source IP address 
	2. source port number 
	3. dest IP address 
	4. dest port number


<div align="center">
	<img src="../../../media/images/Pasted image 20260103023549.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>