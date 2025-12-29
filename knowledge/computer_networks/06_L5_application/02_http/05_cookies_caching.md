## User-Server State: Cookies

- HTTP is **stateless** → Cookies solve this problem
- Small piece of data sent by server to browser
- Browser stores it and sends it back in future requests

**Typical Cookie Usage Steps**:<img src="../../../../media/images/Pasted image 20251229010937.png" align="right" width="500" style="margin: 10px 0px 20px 20px;">

1. Client requests page for the first time
2. Server creates unique ID and sends cookie
3. Cookie is stored on client (browser)
4. Client includes cookie in future requests
5. Server uses cookie to identify returning user

**Example**:

- You always access Internet from your PC
- By visiting specific e-commerce site for first time
- when initial HTTP requests arrives at site, site creates:
    - unique ID
    - entry in backend database for ID
- Cookie is sent in the response message and will be sent with further requests.

---

## Web Caching: Proxy Server

- **Proxy server** = gateway between users and the Internet.
- **Proxy server** (web cache) acts as both client and server
    - server for original requesting client
    - client to origin server
- **Goal**: Satisfy client requests **without involving origin server** <img src="../../../../media/images/Pasted image 20251229011754.png" align="right" width="450" style="margin: 0px 0px 20px 20px;">

**How it works**:

- User configures browser to access web via cache
- Browser sends **all HTTP requests** to cache
    - If **object in cache** → cache returns it immediately
    - Else → cache requests object from origin server, stores it, then returns to client

**Benefits**:

- Reduce **response time** for client request
- Reduce **traffic** on institution's access link
- Prevent cyber attackers from entering a private network

> Installed by ISP (university, company, residential)

---