## Principles of Flow Control

### What is Flow Control?<img src="../../../media/images/Pasted image 20260103123946.png" align="right" width="20%" style="margin: 20px 0 20px 20px;">

**Flow control** ensures that:
- The receiver controls the sender so the sender does not overwhelm the receiver’s buffer by transmitting too much data too fast.

This situation arises because:
- The application may remove data from the TCP receive buffer **slower** than TCP delivers it.
- Without flow control, the receive buffer may overflow.

---
### Simple Flow Control Mechanisms

1. **Stop-and-Wait**
   - Sender transmits one frame.
   - Sender waits for ACK before sending the next frame.

2. **Sliding Window**
   - Sender may transmit multiple frames up to a window size.
   - Receiver advertises how much data it can accept until its window (*which is allocated initially by receiver*) is full.
   - ACK needed only after sender transmits data until window is full

> Flow control prevents the sender from overwhelming the receiver’s processing or buffer capacity.

---
### TCP Flow Control<img src="../../../media/images/Pasted image 20260103124340.png" align="right" width="20%" style="margin: 50px 0 20px 20px;">

TCP implements flow control using the **receiver window (rwnd)**.

- Receiver "advertises" free buffer space using **rwnd** field in TCP header.
- **RcvBuffer** is the size of the receiver buffer (default often ≈ 4096 bytes).
- Many OSes automatically adjust **RcvBuffer**.
- Sender limits unacknowledged (“in-flight”) data to **`rwnd`**.
- Guarantees that receiver buffer does not overflow.


---
## Principles of Congestion Control

### What is Congestion?

**Congestion** occurs when:
> Too many sources send too much data too fast for the network to handle.

**Manifestations of congestion:**
- Packet loss (router buffer overflow)
- Long delays (queueing in routers)

> Congestion is different from flow control: it concerns **network overload**, not receiver overload.

---
### TCP Congestion Control

TCP regulates how fast a sender injects data into the network using a **congestion window (cwnd)**.

- Network feedback controls sender behavior.
- If network cannot deliver data fast enough, sender must slow down.

---
### TCP Congestion Control Phases

1. **Slow Start**
   - Start with small `cwnd`.
   - `cwnd` grows exponentially until threshold.

2. **Congestion Avoidance**
   - `cwnd` grows linearly.
   - Uses Additive Increase.

3. **Congestion Detection**
   - On packet loss or timeout:
     - `cwnd` is reduced (Multiplicative Decrease).
     - Sender returns to slow start or avoidance.
<div align="center">
	<img src="../../../media/images/Pasted image 20260103124842.png" align="" width="50%" style="margin: 20px 0 20px 20px;">
</div>

> This strategy is known as **AIMD (Additive Increase, Multiplicative Decrease).**
---
## Flow Control vs Congestion Control
<div style="text-align: center; margin: 2em auto; max-width: 1000px;">
  <table border="1" cellpadding="12" cellspacing="0" style="border-collapse: collapse; width: 90%; font-family: Arial, Helvetica, sans-serif; margin: 0 auto;">
    <thead>
		<tr style="background-color: #f2f2f2;">
        <th style="text-align: center; font-weight: bold;">Aspect</th>
        <th style="text-align: center; font-weight: bold;">Congestion Control</th>
        <th style="text-align: center; font-weight: bold;">Flow Control</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="text-align: left; font-weight: bold;">Goal</td>
        <td>Traffic entering the network from a sender is controlled by reducing rate of packets.</td>
        <td>Traffic from sender to receiver is controlled, to avoid overloading the slow receiver.</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Layer</td>
        <td>Congestion control is applied in network and transport layer.</td>
        <td>Flow control is applied in transport and data link layer.</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Purpose</td>
        <td>In this, Network is prevented from congestion.</td>
        <td>In this, Receiver's data is prevented from being overloaded.</td>
      </tr>
      <tr>
        <td style="text-align: left; font-weight: bold;">Mechanism</td>
        <td>In this, many algorithms designed for transport layer/network layer define how endpoints should behave to avoid congestion.</td>
        <td>In flow control, sender needs to take measures to avoid receiver from being overloaded depending on feedback from receiver.</td>
      </tr>
    </tbody>
  </table>
</div>
