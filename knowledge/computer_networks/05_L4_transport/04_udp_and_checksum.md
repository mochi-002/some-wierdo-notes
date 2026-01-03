## UDP – User Datagram Protocol

**UDP is connectionless which means:**

- **No handshaking** between UDP sender and receiver
- Each UDP segment handled **independently** of others (no order in delivery)
- **Unreliable** data transfer protocol

**Question**: How to ensure reliable data transfer? 
	**Answer**: Checksum

### UDP Segment Header Format
<div align="center">
	<img src="../../../media/images/Pasted image 20260103024200.png" align="" width="25%" style="margin: 20px 0 20px 20px;">
</div>

- **length**: in bytes of UDP segment, including header
---
## UDP Checksum – Error Detection

**Purpose**: Detecting errors (e.g., flipped bits) in transmitted segment.

**At sender:**

- Divide the original data into the `m` number of blocks with `n` data bits in each block
- Adding all the `m` data blocks
- The addition result is complemented using **1’s complement**
- Sender puts checksum value into **UDP checksum field**

**At receiver:**

- Compute checksum of received segment
	1. Divide the original data into the `m` number of blocks with `n` data bits in each block
	2. Adding all the `m` data blocks
	3. The addition result is complemented using **1’s complement**
- Check if computed checksum equals checksum field value:
	- If **YES** = no error detected 
	- If **NO** = error detected

##### **Very Very Important Note** 🚨
**IMPORTANT NOTE** (pay close attention – this is critical for correct UDP checksum calculation)
- When adding numbers, a carryout from the most significant bit (carryout) needs to be added to the result (wrap-around addition).
### Example on Checksum

Compute the 16-bit integers checksum of:

<div align="center">
	<img src="../../../media/images/Pasted image 20260103025208.png" align="" width="75%" style="margin: 20px 0 20px 20px;">
</div>

**Steps shown in the lecture:**
1. Dividing data into blocks
2. Adding them
3. Carryout
4. 1's Complement after adding the carryout
5. Ensures this process done for both *sender* & *receiver*
6. Complement the result = **checksum**