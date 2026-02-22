# Internet
## How Does The Internet Work
- [How the Internet Works in 5 Minutes](https://www.youtube.com/watch?v=7_LPdttKXPc)
---
### Study Notes

معظم الناس بتستخدم الإنترنت يوميًا من غير ما تكون فاهمة هو بيشتغل إزاي، زي الكهرباء في البيت. مع إن الموضوع شكله معقد، لكنه في الحقيقة أبسط مما الناس متخيلة.

---
#### Internet ≠ Cloud

الإنترنت **مش Cloud** ومش حاجة في الهوا. فكرة الـ Cloud اتعملت علشان التبسيط، لكن الحقيقة إن:

**The Internet is a wire.**

السلك ده ممكن يكون:

- Fiber optics
    
- Copper
    
- Satellite links
    
- Cellular networks
    

بس في النهاية، **the internet is simply a wire**.

---
#### Server vs Client

الإنترنت بيبقى مفيد لأن **كمبيوترين متوصلين بالسلك ده يقدروا يتواصلوا مع بعض**.

- **Server**  
هو كمبيوتر خاص متوصل بالإنترنت بشكل مباشر، وبيكون عليه صفحات ويب أو ملفات مخزنة على الهارد.
    
- **Client**  
هو الكمبيوتر أو الموبايل اللي بنستخدمه كل يوم، وده مش متوصل بالإنترنت بشكل مباشر، لكنه بيعدي الأول على **مزود خدمة الإنترنت (ISP)**.
    

---
#### IP Address

كل Server ليه **IP address**، زي الpostal address بالنسبة للبيوت.
عنوان الـ IP بيساعد الأجهزة إنها تلاقي بعض.
بس علشان الأرقام صعبة، بنستخدم **domain names** زي:

- google.com
    
- facebook.com
    
- aol.com

---

#### Visiting a Website

لما تدخل موقع:  
- جهازك يطلع على الـ ISP
- من الـ ISP للإنترنت
- من الإنترنت لسيرفر الموقع
- السيرفر يبعتلك صفحات الموقع

Your computer → ISP → Internet → Server  

---

#### Email Example

لو بتبعت Email:

- الإيميل بيتكتب على سيرفر الإيميل بتاعك (زي Gmail)
    
السيرفر ده يبعت الرسالة لسيرفر الشخص التاني
    
الشخص التاني يدخل لاحقًا ويسحب الرسالة من السيرفر
    

---

#### Packets

أي حاجة بتمشي على الإنترنت (إيميل، صورة، صفحة ويب) بتتقسم لأجزاء صغيرة اسمها **Packets**.

لما الـ Packets توصل، الجهاز بيركبهم تاني بالترتيب الصح علشان تطلع:

- email
    
- image
    
- web page
    

---

#### إزاي البيانات متتلخبطش؟

لو أنت ومديرك online في نفس الوقت:

- أنت بتعمل Facebook update
    
- هو بيعمل market research

ازاي البيانات مش بتدخل في بعضها؟

---

#### الحل: IP Addresses & Routers

كل حاجة متوصلة بالإنترنت ليها **عنوان IP**:

- computers
    
- servers
    
- cell phones
    
- network equipment
    

أي مكان الشبكات بتتقاطع فيه، فيه جهاز اسمه **Router**.

Routers:

- direct packets
    
- move packets closer to destination
    

وأحيانًا البيانات بتعدي على **10 إلى 15 راوتر** قبل ما توصل.

---

#### تشبيه الـ Packet

الـ Packet شبه **حلوى متغلفة بطبقات**:

- أول طبقة: عنوان جهازك
    
- كل راوتر يضيف طبقة جديدة
    
- لحد ما الـ Packet توصل للسيرفر
    

ولما السيرفر يرد:

- يبعت الـ Packets بنفس التغليف
    
- وكل راوتر يشيل طبقة
    
- لحد ما البيانات توصل لجهازك أنت، مش لجهاز غيرك
    

---
## What is HTTP?
- Video (فيه موسيقى) -> [HTTP Explained in 3 minutes](https://www.youtube.com/watch?v=KvGi-UDfy00)
- Blog -> [Everything you need to know about HTTP](https://cs.fyi/guide/http-in-depth)
- Blog -> [CloudFlare what is http?](https://www.cloudflare.com/en-gb/learning/ddos/glossary/hypertext-transfer-protocol-http/)

### Study Notes

- HTTP = **Hypertext Transfer Protocol**  
- هو الأساس اللي بيشتغل عليه **الويب**
- HTTP is an **application layer protocol**
- Runs on top of other layers of the **network protocol stack**
- Communication happens as:
    - Client sends a **request**
    - Server sends a **response**

---
#### HTTP Request

HTTP request = طريقة المتصفح يطلب بيها data.

Contains:

- HTTP version
    
- URL
    
- HTTP method
    
- HTTP request headers
    
- Optional HTTP body

---
##### HTTP Methods

- **GET**
    - Requests information
    - Usually returns a webpage
- **POST**
    - Sends information to the server
    - Example: form data (username, password)

---

##### HTTP Request Headers

- Headers are **key-value pairs**
- Included in every HTTP request
- Provide information such as:
    - Browser type
    - Requested data
---

##### Request Body

- Contains the actual data being sent
- Examples:
    
    - Username
        
    - Password
        
    - Form data

---

#### HTTP Response

- An HTTP response is what the server sends back to the client.
- A typical HTTP response contains:
	- HTTP status code
	- HTTP response headers
	- Optional HTTP response body

---

#### HTTP Status Codes

- 3-digit numbers indicating request result
##### Status code categories:

- **1xx** – Informational
    
- **2xx** – Success
    
- **3xx** – Redirection
    
- **4xx** – Client Error
    
- **5xx** – Server Error
##### Examples:

- **200 OK** → Request successful
    
- **404 Not Found** → Client error
    
- **5xx** → Server-side error
---

#### HTTP Response Body

- Present in successful GET requests
    
- Usually contains **HTML**
    
- Browser converts it into a webpage

---

#### HTTP & DDoS

- HTTP is a **stateless protocol**
    
- Each request is independent
    
- Older HTTP versions:
    
    - Open and close a TCP connection per request
        
- HTTP 1.1 and above:
    
    - Use **persistent TCP connections**
        
- Large amounts of HTTP requests can be used in:
    
    - DoS attacks
        
    - DDoS attacks
        
- These are **application layer (Layer 7) attacks**