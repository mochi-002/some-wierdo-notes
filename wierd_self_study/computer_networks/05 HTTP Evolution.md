### 5.1 HTTP/1.0   
- One request = One TCP connection
- No Keep-Alive
### 5.2 HTTP/1.1 (1997 – Still widely used)   
- Persistent Connections (Keep-Alive)  
- Pipelining (and its problems)   
- Host Header, Chunked Transfer Encoding 
### 5.3 HTTP/2 (2015)   
- Binary Protocol   
- Multiplexing (No Head-of-Line blocking)   
- Header Compression (HPACK)   
- Server Push
### 5.4 HTTP/3 (2022 – Now default in most browsers)   
-  Built on QUIC (UDP-based)   
- 0-RTT & 1-RTT Handshake   
- Built-in Encryption & Faster Connection Migration