## HTTP Request Message

> **Two types of HTTP messages**: request or response
### HTTP request message:

- ASCII (human-readable format)

**Example of HTTP Request Message:**

```
GET /index.html HTTP/1.1\r\n
Host: www-net.cs.umass.edu\r\n
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:91.0) Gecko/20100101 Firefox/91.0\r\n
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8\r\n
Accept-Language: en-US,en;q=0.5\r\n
Accept-Encoding: gzip, deflate\r\n
Connection: keep-alive\r\n
Keep-Alive: 115\r\n
\r\n
```

**Key Parts Explained**:<img src="../../../../media/images/Pasted image 20251229005351.png" align="right" width="480" style="margin: -20px 0px 20px 20px;">

- **Request line**: `GET /index.html HTTP/1.1`
- **Header lines**: Host, User-Agent, Accept, Accept-Language, Accept-Encoding, Connection, Keep-Alive, etc.
- **Carriage return + line feed (`\r\n`)**: Marks the end of each line
- Blank line (`\r\n`) after headers indicates the **end of header lines**

---

### General Format of HTTP Request Message

```
method sp URL sp version cr lf
header field name : value cr lf
header field name : value cr lf
...
header field name : value cr lf
cr lf
entity body
```

- <img src="../../../../media/images/Pasted image 20251229005851.png" align="right" width="300" style="margin: -50px 0px 20px 20px;">**Request line**: method + URL + version
- **Header lines**: field name : value
- **Blank line** (cr lf): separates headers from body
- **Entity body** (optional): used in POST, PUT, etc.

---

### HTTP Request Message Methods

**GET**:

- Open the web page **POST**:
- Web page often includes form input
- Input is uploaded to server in **entity body** **HEAD**:
- Asks server to leave requested object out of response **DELETE**:
- Deletes file specified in the URL field

#### **HTTP Versions and Supported Methods**

- **HTTP/1.0**:
    - GET
    - POST
    - HEAD
- **HTTP/1.1**:
    - GET, POST, HEAD
    - DELETE

---

### Quick Reference Table – HTTP Request Methods Summary

|Method|Purpose|Entity Body?|HTTP Version|
|---|---|---|---|
|**GET**|Retrieve/open the web page|No|1.0 & 1.1|
|**POST**|Submit form data/input to server|Yes|1.0 & 1.1|
|**HEAD**|Get headers only (no object in response)|No|1.0 & 1.1|
|**DELETE**|Delete resource specified in URL|No|1.1 only|

---

## HTTP Response Message

**Structure**:<img src="../../../../media/images/Pasted image 20251229010349.png" align="right" width="480" style="margin: 10px 0px 20px 20px;">

- Status line: `HTTP/1.1 200 OK`
- Header lines: `Date:`, `Server:`, `Content-Length:`, etc.
- Blank line
- Entity body (requested object)

**Common Status/Response Codes**:

- _(200)_ OK
- _(301)_ Moved Permanently
- _(400)_ Bad Request
- _(404)_ Not Found
- _(505)_ HTTP Version Not Supported

---

