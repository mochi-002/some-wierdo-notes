## 1. Electronic Mail (Email)

### Main Components of the Electronic Mail System

- **User Agents** (UA) — e.g., any installed "mail reader" application or webmail in browser
- **Mail Servers**
- **Simple Mail Transfer Protocol (SMTP)**

**Key points:**

- SMTP is the **application-layer protocol** responsible for the connection **between mail servers**.
- SMTP uses **TCP** for reliable transfer on **port 25**.

Here are some typical diagrams showing the overall email architecture with user agents, mail servers, and SMTP connections:
<div align="center"> 
	<img src="../../../../media/images/Pasted image 20260102220137.png" align="" width="45%" style="margin: 0 0 20px 20px;"> 
	<img src="../../../../media/images/Pasted image 20260102220146.png" align="" width="45%" style="margin: 0 0 20px 20px;">
</div>

### User Agent Responsibilities

- Composing, editing, and reading mail messages
- Examples: Outlook, Thunderbird, Gmail web interface, etc.

### Mail Servers Responsibilities

- Contain user's **mailbox** (stores all received messages)
- Maintain **message queue** of outgoing (to-be-sent) mail messages

### How SMTP Works: Sending an Email (Alice → Bob Scenario)

1. Alice uses her **user agent** to compose message  
    → "To: bob@someschool.edu"
2. Alice's UA sends message to her **mail server** → message placed in **message queue**
3. Client side of SMTP opens **TCP connection** with Bob's mail server
4. SMTP client sends Alice's message over the TCP connection
5. Bob's mail server places the message in **Bob's mailbox**
6. Bob invokes his **user agent** to read the message

Here is the classic step-by-step diagram (very common in Kurose & Ross):<div align="center"><img src="../../../../media/images/Pasted image 20260102220208.png" align="" width="" style="margin: 0 0 0 0;"></div>

### SMTP Protocol Details

**Communication phases:**

- Handshaking
- Transfer of message
- Closure

**Messages types:**

- **Commands** (7-bit ASCII): `HELO`, `MAIL FROM`, `RCPT TO`, `DATA`, `QUIT`
- **Responses** (status codes): e.g., `220`, `250`, `354`, `221`

**Example SMTP session:**

```
S: 220 hamburger.edu
C: HELO crepes.fr
S: 250 Helo crepes.fr, pleased to meet you
C: MAIL FROM:<alice@crepes.fr>
S: 250 alice@crepes.fr... Sender ok
C: RCPT TO:<bob@hamburger.edu>
S: 250 bob@hamburger.edu ... Recipient ok
C: DATA
S: 354 Enter mail, end with "." on a line by itself
C: Do you like ketchup?
C: How about pickles?
C: .
S: 250 Message accepted for delivery
C: QUIT
S: 221 hamburger.edu closing connection
```

Here are visual examples of SMTP interaction/handshake:
<div align="center"><img src="../../../../media/images/Pasted image 20260102220224.png" align="" width="850" style="margin: 0 0;"></div>

**Additional SMTP characteristics:**

- Uses **persistent connections**
- Message (header + body) is written in **7-bit ASCII**
- End of message is marked by **CRLF . CRLF** (carriage return/line feed + dot on its own line)

### SMTP Message Format

- **Header lines**: `To:`, `From:`, `Subject:`, etc.
- **Body**: the actual message content

```
header
body
```

### Comparison: SMTP vs HTTP

|Feature|HTTP|SMTP|
|---|---|---|
|Primary usage|Webpages|Mail services|
|Default port|80|25|
|Protocol type|Primarily pull|Primarily push|
|Data transfer|Between web server & client|Via mail servers|
|Connection type|Persistent & non-persistent|Persistent|

### Email Access Protocols (Retrieving Emails)

SMTP is used for **sending** and delivering to receiver's mail server.

For **retrieving** emails from server, use:

- **POP** (Post Office Protocol)
- **IMAP** (Internet Mail Access Protocol)
- **HTTP** (Gmail, Outlook.com, Yahoo! Mail, etc.)

**POP features:**

- Supports authorization
- **Stateless** across sessions (usually downloads and deletes from server)

**IMAP features:**

- Keeps all messages **on server**
- Allows organizing messages in **folders**
- Maintains **user state** across sessions

## 2. Domain Name System (DNS)

**Purpose**  
Translates human-readable domain names (e.g., www.amazon.com) to machine-readable **IP addresses** (e.g., 192.0.2.44)

**Key characteristics:**

- Operates at the **application layer**
- Implemented as a **hierarchy** of many distributed servers (not centralized)

**Why not centralized?**

- Single point of failure
- Traffic volume
- Maintenance difficulty

### DNS Hierarchy / Types of Servers

1. **DNS Resolver** (Recursive resolver) — first receiver of the request; does most of the work
2. **Root Server** — returns address of appropriate TLD server
3. **TLD Server** (Top-Level Domain) — e.g., .com, .org, .edu — returns authoritative server
4. **Authoritative Name Server** — contains the actual IP address for the domain

Here are clear diagrams showing the DNS hierarchy and resolution process:
<div align="center">
	<img src="../../../../media/images/Pasted image 20260102220302.png" align="" width="45%" style="margin: 0 0 ;"> 
	<img src="../../../../media/images/Pasted image 20260102220310.png" align="" width="50%" style="margin: 0 0 ;">
</div>

## 3. Streaming Multimedia

### Video Basics

- Video = sequence of images displayed at constant rate (e.g., 24 images/sec)
- **Video encoding** — compressing raw video content into digital format
- **CBR** (Constant Bit Rate) — fixed encoding rate
- **VBR** (Variable Bit Rate) — variable encoding rate

**Facts:**

- Video traffic is the major consumer of Internet bandwidth
- Netflix ~37% and YouTube ~16% of downstream traffic (at the time of the book)

**Solution for efficient bandwidth usage:**  
**DASH** (Dynamic Adaptive Streaming over HTTP)

### DASH: Dynamic Adaptive Streaming over HTTP
<img src="../../../../media/images/Pasted image 20260102220414.png" align="right" width="500" style="margin: 0 0 20px 20px;">
**At server side:**

- Video file divided into multiple **chunks**
- Each chunk encoded at **different bit rates**
- Stored (often in CDNs)
- **Manifest file** provides URLs for different chunks/qualities

**At client side:**

- Periodically measures current **server-to-client bandwidth**
- Chooses the **maximum sustainable coding rate**




## 4. Content Distribution Networks (CDNs)

**Purpose**  
Stores copies of content at **CDN nodes** (edge servers) located close to users → reduces latency and server load

**Example:**  
Netflix stores copies of shows (e.g., Mad Men) in many CDN locations worldwide

<div align="center">
	<img src="../../../../media/images/Pasted image 20260102220438.png" align="" width="50%" style="margin: 0 0 20px 20px;">
	<img src="../../../../media/images/Pasted image 20260102223218.png" align="" width="45%" style="margin: 0 0 20px 20px;">	
</div>
