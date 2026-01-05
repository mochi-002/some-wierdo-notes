## What is Reliability?

**Reliability means:**
- No data loss  
- No bit errors  

---
## The rdt Abstraction

We assume a function called **Reliable Data Transfer (rdt)**.

This is a **conceptual abstraction**: instead of thinking about packets, errors, or losses, we imagine a function that transfers data from sender to receiver **perfectly**.

This abstraction allows us to:
- First define **what service we want** (perfect, reliable communication),
- Then later design **how to implement it** over an unreliable network.

This naturally leads to the **service model**, where we separate:
- **What the application expects** → *Provided service*,  
- **What the protocol actually does** → *Service implementation*.  

---
## Service Model

### 0.1 Provided Service (What the application sees)
The application layer sees a **perfectly reliable channel** between sending and receiving processes.

> Abstraction: a reliable channel is provided, regardless of underlying reality.

<div align="center">
	<img src="../../../media/images/Pasted image 20260103111141.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div> 

---

### 0.2 Service Implementation (What actually happens)
- The underlying channel is **unreliable**
- The reliable data transfer protocol makes it *appear* reliable

<div align="center">
	<img src="../../../media/images/Pasted image 20260103111149.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

---

## How rdt Is Designed

- Build sender and receiver incrementally.
- Use **Finite State Machines (FSMs)** to specify behavior.

**FSM concepts:**
- **State:** Current situation of sender/receiver
- **Event:** Triggers a transition
- **Action:** What happens on transition

<div align="center">
	<img src="../../../media/images/Pasted image 20260103112237.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

---

## rdt Versions

### 0.1 rdt1.0 — Reliable Channel

**Assumptions:**
- No packet loss
- No bit errors

**Behavior:**
- separate FSMs for sender, receiver:
	- Sender sends data into underlying channel
	- Receiver delivers data from underlying channel
<div align="center">
	<img src="../../../media/images/Pasted image 20260103112341.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

---
### 0.2 rdt2.0 — Channel with Bit Errors

**New problem:** bits can be corrupted (may be *fliped*).

**New mechanisms:**
- Error detection using **checksum**
- Receiver feedback:
	- **ACK** (acknowledgements) → packet received correctly
	- **NAK** (negative acknowledgements) → packet corrupted
- Sender retransmits on NAK

**Human analogy:** repeating words when misunderstood.

---
#### 0.21 rdt2.0 FSM
##### Sender FSM <img src="../../../media/images/Pasted image 20260103113927.png" align="right" width="15%" style="margin: 20px 0 20px 20px;">

The sender has two states: "Wait for call from above" (initial state, waiting for data from the application layer) and "Wait for ACK or NAK" (waiting for feedback from the receiver after sending a packet).

- **State: Wait for call from above**
    - This is the idle state where the sender is ready to receive data to send.
    - **Event**: `rdt_send(data)` (call from the upper layer to send data).
    - **Actions**:
		- Create a packet: `sndpkt = make_pkt(data, checksum)` (encapsulates the data with a checksum for error detection).
        - Send the packet over the unreliable channel: `udt_send(sndpkt)`.
    - **Transition**: Moves to "Wait for ACK or NAK".
- **State: Wait for ACK or NAK**
    - Here, the sender waits for the receiver's response to confirm if the packet was received correctly.
    - **Event**: `rdt_rcv(rcvpkt) && isNAK(rcvpkt)` (receives a packet that is a NAK, indicating errors).
        - **Action**: Resend the original packet: `udt_send(sndpkt)` (retransmit to recover from the error).
        - **Transition**: Loops back to "Wait for ACK or NAK" (keeps waiting for a valid response).
    - **Event**: `rdt_rcv(rcvpkt) && isACK(rcvpkt)` (receives a packet that is an ACK, indicating success).
        - **Action**: None (the packet is confirmed as delivered correctly).
        - **Transition**: Returns to "Wait for call from above" (ready for the next data).

This FSM ensures the sender only proceeds after confirmation, retransmitting if needed. However, note that rdt2.0 has a flaw: it doesn't handle corrupted or lost ACK/NAK messages well, which could lead to duplicates (addressed in later versions like rdt2.1).

##### Receiver FSM<img src="../../../media/images/Pasted image 20260103113950.png" align="right" width="15%" style="margin: 20px 0 20px 20px;"> 

The receiver has a single state: "Wait for call from below" (waiting for packets from the unreliable channel). It's simpler because the receiver doesn't need to track multiple packets—it's always ready to process incoming data.

- **State: Wait for call from below**
    - This is the only state, as the receiver is continuously listening.
    - **Event**: `rdt_rcv(rcvpkt) && corrupt(rcvpkt)` (receives a packet but the checksum indicates bit errors).
        - **Action**: Send a NAK back to the sender: `udt_send(NAK)` (requests retransmission).
        - **Transition**: Loops back to itself (continues waiting).
    - **Event**: `rdt_rcv(rcvpkt) && notcorrupt(rcvpkt)` (receives a packet with no errors).
        - **Actions**:
            - Extract the data: `extract(rcvpkt.data)`.
            - Deliver the data to the upper layer: `deliver_data(data)`.
            - Send an ACK back to the sender: `udt_send(ACK)` (confirms successful receipt).
        - **Transition**: Loops back to itself (ready for the next packet).

The receiver's FSM focuses on error detection via checksum and providing feedback. It discards corrupted packets without delivering them and only passes valid data upward.

---

#### 0.22 Operation Without Errors
<img src="../../../media/images/Pasted image 20260103114358.png" align="right" width="50%" style="margin: 20px 0 20px 20px;"> 

1. Sender gets data from the app layer 
	- `rdt_send(data)`
2. Sender creates packet + checksum 
	- `sndpkt = make_pkt(data, checksum)`
3. Sender sends it 
	- `udt_send(sndpkt)`
4. Sender now waits for response (moves to state: **Wait for ACK or NAK**)
5. Receiver gets the packet 
	- `rdt_rcv(rcvpkt)`
6. Receiver checks checksum → **perfect, no errors!** 
	1. extracts data 
	2. delivers data to its app layer `deliver_data(data)` 
	3. sends back **ACK** 
	4. `udt_send(ACK)`
7. Sender receives the ACK 
	1. sees `isACK(rcvpkt)` → great! 
	2. goes back to **Wait for call from above** 
	3. ready to send the next piece of data

**Result**: One clean packet delivered → ready for the next one

---

#### 0.23 Error Scenario
<img src="../../../media/images/Pasted image 20260103114413.png" align="right" width="50%" style="margin: 20px 0 20px 20px;"> 

1. Sender gets data 
	1. same as above 
	2. creates packet with checksum 
	3. sends it `udt_send(sndpkt)` → waits (**Wait for ACK or NAK**)
2. Receiver gets the packet 
	- `rdt_rcv(rcvpkt)`
3. Receiver checks checksum → **corrupt!** (error detected)
4. Receiver **throws away** the bad packet 
	1. sends **NAK** back 
	2. `udt_send(NAK)`
5. Sender receives the NAK 
	1. sees `isNAK(rcvpkt)` → oh no! 
	2. **re-sends the exact same packet** 
	3. `udt_send(sndpkt)` (again) 
	4. stays in **Wait for ACK or NAK** (still waiting)
6. Receiver gets the **retransmitted** packet → this time checksum is good (no error)
7. Receiver now: 
	1. extracts & delivers data 
	2. sends **ACK** 
	3. `udt_send(ACK)`
8. Sender receives the ACK → success! 
	1. goes back to **Wait for call from above** 
	2. ready for next data

**Result**: The error was detected → packet was retransmitted → eventually delivered correctly

---
## Fatal Flaw in rdt2.0

### 0.1 The Problem
What if **ACK or NAK is lost or corrupted**?

- Sender doesn’t know receiver’s state
- Cannot safely retransmit (might create duplicates)

---

### 0.2 The Solution

**Add:**
- **Sequence numbers** to packets
- Receiver discards duplicates
- Sender retransmits if no response

This introduces [Stop-and-Wait Protocol](06_flow_and_congestion_control.md):
- Send one packet
- Wait for ACK before sending next

---
## rdt2.1
#### Quick Summary: What rdt2.1 Fixes
- Problem in rdt2.0 → If ACK or NAK is corrupted/lost, sender might retransmit → receiver gets duplicate data.
- Solution in rdt2.1 → Add **1-bit sequence number** (0 or 1) → receiver remembers what it last got → discards duplicates and re-sends the correct ACK.

### 1. rdt2.1 Sender (very simplified flow)
<img src="../../../media/images/Pasted image 20260103120722.png" align="right" width="50%" style="margin: 20px 0 20px 20px;">

The sender now has **four** states because it alternates between seq# 0 and seq# 1.

**No error flow (everything perfect):**

1. App gives data → sender is in **Wait for call 0 from above**
2. Sender creates packet: seq=**0**, data, checksum
3. Sends it → goes to **Wait for ACK0 or NAK0**
4. Receiver gets it → replies **ACK0** (success)
5. Sender sees **ACK0** → great! → goes back to **Wait for call 1 from above** (next packet will use seq=1)
6. Pattern repeats → next packet seq=1 → waits for **ACK1** → and so on

**Error flow (corrupted packet or corrupted ACK):**

- Sender sends seq=0 packet
- Receiver gets it corrupted → sends **NAK** (or ACK is corrupted/lost)
- Sender gets NAK (or timeout) → **re-sends** the same packet with **seq=0**
- Receiver eventually gets a good copy of seq=0 → sends **ACK0**
- Sender gets **ACK0** → moves to next state (ready for seq=1)

Important: Sender **never** sends a new packet until it gets the correct ACK for the current sequence number.

### 2. rdt2.1 Receiver (very simplified flow)
<img src="../../../media/images/Pasted image 20260103120837.png" align="right" width="50%" style="margin: 20px 0 20px 20px;">

Receiver has **two** states: expecting seq=0 or expecting seq=1.

**Normal good flow:**

1. Receiver is in **Wait for 0 from below**
2. Gets packet → seq=0 → not corrupt
3. Extracts data → delivers to app
4. Sends **ACK0**
5. Switches to **Wait for 1 from below**
6. Next time expects seq=1 → sends **ACK1** when good → switches back, etc.

**Duplicate / error handling (this is the magic!):**

- Receiver is expecting seq=0
- Gets packet seq=0 → but **already delivered it before** (duplicate) → **does NOT** deliver again → **re-sends ACK0** (tells sender: "I already have it, calm down")
- Gets corrupted packet → sends **NAK**
- Gets wrong sequence (e.g. expecting 0 but gets seq=1) → usually means previous ACK was lost → **re-sends last good ACK** (keeps sender in sync)

<div style="text-align: center; margin: 2em auto; max-width: 1000px;">
  <table border="1" cellpadding="12" cellspacing="0" style="border-collapse: collapse; width: 90%; font-family: Arial, Helvetica, sans-serif; margin: 0 auto;">
    <thead>
		<tr style="background-color: #f2f2f2;">
        <th style="text-align: center; font-weight: bold;">Situation</th>
        <th style="text-align: center; font-weight: bold;">rdt2.0</th>
        <th style="text-align: center; font-weight: bold;">rdt2.1 (improved)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="text-align: left; font-weight: bold;">Packet arrives good</td>
        <td>Deliver + ACK</td>
        <td>Deliver + correct ACK (0 or 1)</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Packet corrupted</td>
        <td>Discard + NAK</td>
        <td>Discard + NAK</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">ACK/NAK corrupted or lost</td>
        <td>Big problem → possible duplicate delivery</td>
        <td>Receiver re-sends last correct ACK → no duplicate delivery</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Sender retransmits same packet</td>
        <td>Receiver may deliver twice (duplicate)</td>
        <td>Receiver sees same seq# → discards + re-ACKs → safe</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Uses sequence numbers?</td>
        <td>No</td>
        <td>Yes (just 0 and 1)</td>
      </tr>
    </tbody>
  </table>
</div>

---
## RDT Versions Summary
<div style="text-align: center; margin: 2em auto; max-width: 900px;">
  <table border="1" cellpadding="12" cellspacing="0" style="border-collapse: collapse; width: 100%; font-family: Arial, Helvetica, sans-serif; margin: 0 auto;">
    <thead>
      <tr style="background-color: #f2f2f2;">
        <th style="text-align: center;">Version</th>
        <th style="text-align: center;">Channel Assumptions</th>
        <th style="text-align: center;">Main Problems Handled</th>
        <th style="text-align: center;">Key New Features / Mechanisms</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="text-align: center;"><strong>rdt1.0</strong></td>
        <td>Perfectly reliable<br>(no bit errors, no loss)</td>
        <td>—</td>
        <td>Simple send/receive over ideal channel</td>
      </tr>
      <tr>
        <td style="text-align: center;"><strong>rdt2.0</strong></td>
        <td>Bit errors possible<br>(but no packet loss)</td>
        <td>Bit corruption in data packets</td>
        <td>• Checksum for error detection<br>• ACK and NAK feedback<br>• Retransmission on NAK</td>
      </tr>
      <tr>
        <td style="text-align: center;"><strong>rdt2.1</strong></td>
        <td>Bit errors possible<br>+ feedback (ACK/NAK) can be corrupted or lost</td>
        <td>Bit corruption + duplicate delivery risk from garbled ACK/NAK</td>
        <td>• 1-bit sequence numbers (0 and 1)<br>• Receiver detects & discards duplicates<br>• Re-ACK previous correct packet</td>
      </tr>
      <tr>
        <td style="text-align: center;"><strong>rdt3.0</strong><br>(to your info)</td>
        <td>Bit errors + packet loss possible</td>
        <td>All previous problems + packet loss</td>
        <td>• Sequence numbers<br>• Checksum<br>• ACK/NAK<br>• **Timers** + retransmission on timeout</td>
      </tr>
    </tbody>
  </table>
</div>
