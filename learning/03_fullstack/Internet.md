# Internet
## How Does The Internet Work
- [How the Internet Works in 5 Minutes](https://www.youtube.com/watch?v=7_LPdttKXPc) ✅
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
- Blog -> [CloudFlare what is http?](https://www.cloudflare.com/en-gb/learning/ddos/glossary/hypertext-transfer-protocol-http/) ✅
---
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

## What is domain name?
- Video (فيه موسيقى) -> [Hostinger Academy || Domain basics: What is a domain name?](https://www.youtube.com/watch?v=lMHzpBwPuG8)
- Blog -> [CloudFlare || What is a domain name?](https://www.cloudflare.com/en-gb/learning/dns/glossary/what-is-a-domain-name/) ✅
---
### Study Notes
#### What is a **Domain Name**?

- A **domain name** is a unique, human-readable address used to access websites, such as `cloudflare.com`.

- It maps to an **IP address**, allowing users to reach websites by typing easy-to-remember words instead of a complex sequence of numbers.

---
#### What is DNS (Domain Name System)?

- **DNS** is the system that translates *domain names* into their corresponding **IP addresses**.

- When a user enters a domain name in a browser, **DNS** enables the browser to locate and load the correct website.

---
#### What is a URL (Uniform Resource Locator)?

- A **URL** is a complete web address used to access a resource on the web.
- It includes: 
	- the **protocol** (such as `https://`) 
	- the **domain name**
	- the **path** to a specific page or resource on a website
	Example: `https://www.cloudflare.com/learning/dns/what-is-dns/`

---
#### Components of a Domain Name

- Domain names are divided into parts separated by dots.
	1. The **rightmost** part is the **Top-Level Domain (TLD)**
	2. The part directly to its left is the **Second-Level Domain (2LD)** 
	3. Any additional part to the left is a **Third-Level Domain (3LD)**, also called a **subdomain**

- **Example:** `blog.cloudflare.com`
	- `.com` → **TLD** - `cloudflare` → **2LD** - `blog` → **3LD** (subdomain)

---
#### What is Domain Registration?

- **Domain registration** is the process of reserving a domain name for exclusive use through a **domain registrar**.
- Once registered, the domain name is owned by the **registrant** for a specified period (usually 1–10 years).
- There are **hundreds of millions** of registered domain names worldwide.

---
#### IP Addresses and Domain Names

- An **IP address** is the numerical address (e.g. `104.16.123.96`) used by computers to identify and communicate with each other on the Internet.
- **Domain names** are mapped to **IP addresses** so users can access websites using readable names instead of remembering numeric identifiers.

---
#### Why is Domain Name Security Important?

- **Domain name security** is critical to protect **ownership** and **control** of a domain.
- Risks include:
	- **Domain squatting** (cybersquatting): expired domains are bought and resold at high prices 
	- **Domain hijacking**: a malicious party gains unauthorized control of a domain
- Using a **trustworthy registrar** (with strong security practices) helps prevent these issues — this is one of the points strongly emphasized by **Cloudflare**.

---
## What is hosting?
- Video (فيه موسيقى) -> [Different Types of Web Hosting Explained](https://www.youtube.com/watch?v=AXVZYzw8geg) ✅
- Blog -> [Namecheap || What is Web Hosting?](https://www.namecheap.com/hosting/what-is-web-hosting-definition/) ✅
---
### Study Notes
#### What is **Web Hosting**? 
- **Web hosting** is a service that allows individuals and organizations to *rent space* on a server to store website files, making the site accessible on the internet 24/7.
- When someone enters your **domain name** in a browser, the **web hosting server** responds by delivering your website’s files (HTML, CSS, images, etc.) to the visitor’s device.

---
#### How **Web Hosting** Works 
1. The **hosting provider** assigns disk space and resources on one or more servers for your website. 
2. You connect your **domain name** to the hosting account via **DNS** (usually by pointing nameservers or setting A/AAAA records).
3. You upload files manually (via FTP/SFTP) or install a **content management system** (CMS) like WordPress, Joomla, or Drupal. 
4. When a visitor requests your site, the server processes the request and sends the appropriate files back to the browser.
5. The quality of the experience depends on allocated server resources: **CPU**, **RAM**, **storage space**, and **monthly bandwidth**.

---
#### Types of **Web Hosting**

- **Shared Hosting** Many websites run on the same physical server, sharing CPU, RAM, and other resources. → *Cheapest* option, very beginner-friendly, but performance can slow if neighboring sites get heavy traffic.

- **VPS (Virtual Private Server) Hosting** A physical server is divided into several virtual servers; you get dedicated amounts of CPU, RAM, and storage. → More control (root access possible), better and more consistent performance than shared.

- **Dedicated Hosting** You rent an *entire physical server* for your website(s) alone — no sharing. → Highest performance, full customization, ideal for large sites, high traffic, or special software needs.

- **Cloud Hosting** Your site draws resources from a *cluster/network of interconnected servers* rather than one single machine. → Excellent scalability, great for handling traffic spikes, usually very high uptime.

- **Reseller Hosting** You purchase a large hosting package and divide/sell portions of it to clients under your own brand name. → Popular with web designers, developers, and people starting their own hosting business.
---
#### Choosing the Right **Web Host** – Important Factors

- **Uptime** → Aim for at least **99.9%** (many good hosts guarantee 99.95%+) 
- **Speed & Performance** → Faster load times improve user experience and help with **Google SEO** -
- **Security** → Free **SSL certificate**, **firewall**, malware scanner, **DDoS** protection, daily backups
- **Customer Support** → 24/7 availability (live chat + tickets), fast and knowledgeable responses 
- **Pricing** → Shared is usually the least expensive; dedicated and high-end cloud are pricier 
- **Scalability** → Easy upgrade path (shared → VPS → cloud/dedicated) as your site grows
- **Control Panel** → Intuitive interface such as **cPanel**, **Plesk**, DirectAdmin, or custom dashboards 
- **Extra Tools** → One-click **CMS** installers, website builder, free domain for first year, etc.

---
#### **Free** vs **Paid** Hosting

**Free Hosting** 
- Suitable for testing, learning, very small personal projects, or temporary landing pages
- Usually comes with **severe limitations**: low storage, very limited bandwidth, slow servers
- Often forces **advertisements** on your pages or uses a branded subdomain (yoursite.freehostexample.com) 
- Little to no real technical support; rarely includes **SSL**

**Paid Hosting** 
- Significantly better **resources** (storage, bandwidth, CPU), speed, and reliability 
- Almost always includes **free SSL**, custom domain support, better security features 
- Professional-grade infrastructure, regular backups, and actual 24/7 human support
- Essential for any **business website**, **e-commerce store**, serious blog, portfolio that represents you professionally, or site expected to receive meaningful traffic

---
## DNS and how it works
- Video (فيه موسيقى) -> [How DNS works: The animated video!](https://howdns.works/video/) الكوميك أمتع عمومًا
- Blog -> [How DNS works (comic)](https://howdns.works/) ✅ تحفة التحف
---
### Study Notes
#### No Notes Needed – Just Enjoy the Comics 😂
(LoL, now we have **comics** in studying web dev… who said learning has to be boring?)

#### Just kep in mind
##### DNS (Domain Name System) – Overview 
- **DNS** is basically the **phonebook of the internet**. It translates human-friendly domain names (like `google.com` or `cloudflare.com`) into machine-readable **IP addresses** (like `142.250.190.174`) so your browser can actually find and connect to websites.

- Without DNS → you'd have to remember and type IP addresses for every site.
---
##### How DNS Resolution Works – The Full Journey
- When you type a domain into your browser, a multi-step lookup happens (usually in milliseconds thanks to **caching**). 
- Here’s the classic uncached flow (worst-case / full resolution):
	1. **Browser / OS cache** → Checks if it already knows the IP (super fast, local). 
	2. **Stub resolver** (your device's tiny DNS client) → If not cached locally, asks the configured **recursive resolver** (usually your ISP’s or public like 8.8.8.8 / 1.1.1.1). 
	3. **Recursive resolver cache** → The resolver first checks *its own cache*. If hit → instant answer. 
	4. **Root name servers** (.) → If miss, asks one of the 13 root server clusters worldwide. → Root says: “I don’t know the IP, but here’s the address of the **TLD** server for .com / .org / etc.”
	5. **TLD name servers** (e.g. .com servers managed by Verisign) → Resolver asks the TLD. → TLD says: “I don’t have the IP, but here’s the **authoritative name server** for google.com.” 
	6. **Authoritative name servers** (set by the domain owner, e.g. Google’s own NS) → Final query. → They return the actual **IP address** (A record) or other records (CNAME, MX, etc.). 
	7. **Answer returned** → Resolver sends IP back to your device → browser connects → page loads.
- **Your shortcut reminder (perfect order!)**: **cache → os → resolver → root → TLD → Authoritative name servers → the answer (IP address)**
- Caching happens at **every step** — browser, OS, resolver, even sometimes upstream — so most real lookups are 1–2 steps max.

---
##### Quick Tips / Common Facts 
- Most people use **public resolvers** today: Cloudflare (1.1.1.1), Google (8.8.8.8), Quad9 (9.9.9.9) → faster + more private than ISP ones. 
- **TTL** (Time To Live) → Controls how long each cache layer keeps the record before asking again.
- Real lookups are usually **recursive** (resolver does all the work) vs **iterative** (client would have to ask each server — rare).
---
## Browsers and how they work?
- Video -> [How The Web Works - The Big Picture](https://www.youtube.com/watch?v=hJHvdBlSxug)
- Blog -> [ACADEMIND || How The Web Works](https://academind.com/tutorials/how-the-web-works)
---
### Study Notes

#### How the **Web** Works – Overview
The web enables **browsers** to request data from **servers** and display it to users in a readable, interactive way.

When you enter a **URL** (e.g., `https://academind.com`) in your browser, a chain of steps happens behind the scenes to fetch, process, and render the website.

---
##### Step 1: **URL Resolution** (DNS Lookup)
- The **domain name** part of the URL (e.g., `academind.com`) must be translated into an **IP address** (e.g., `104.18.26.123`).
- **DNS servers** (Domain Name System) act like internet phonebooks / dictionaries → they map human-readable domain names to numerical IP addresses.
- The browser (or OS/resolver) queries a **DNS server** to resolve the domain → gets the IP before any real request can be sent.

---
##### Step 2: **Sending a Request**
- Once the IP is known, the browser establishes a connection and sends an **HTTP** (or **HTTPS**) request to the server at that IP.
- Requests are structured packets containing:
	- **Method** (e.g., GET, POST)
	- **URL path** (e.g., `/blog/post-1`)
	- **Headers** (e.g., User-Agent, Accept, Authorization)
	- Optional body/data (for POST/PUT/etc.)
- **HTTPS** = encrypted/safe version of HTTP → uses TLS/SSL to protect data in transit (padlock icon!).

---
##### Step 3: **Server Response & Parsing**
- The **server** receives the request, processes it (runs code, queries database, etc.), and sends back an **HTTP response**.
- Response includes:
	- **Status code** (e.g., 200 OK, 404 Not Found, 500 Error)
	- **Headers** (e.g., Content-Type: text/html, Cache-Control)
	- **Body** (the actual content: HTML, JSON, image binary, etc.)
- Browser reads the **Content-Type** header → knows how to handle the body:
	- `text/html` → parse as HTML document
	- `application/json` → treat as data (for APIs)
	- `image/jpeg` → display as image

---
##### Step 4: **Rendering the Page**
- Browser parses the **HTML** to build the DOM (Document Object Model) → defines structure (headings, paragraphs, links, etc.).
- HTML alone has no style → browser looks for linked **CSS** files (via `<link>` tags) and fetches them → applies visual styling (colors, layouts, fonts).
- Additional requests are made for:
	- Images (`<img>`), fonts, videos, etc.
	- JavaScript files (`<script>`) → executed to add interactivity/dynamic behavior.
- JavaScript can run after initial load → fetch more data (AJAX/Fetch), update DOM, handle events, etc.

Modern browsers optimize this heavily (parallel downloads, caching, preloading, etc.).

---
#### **Server-side** vs **Browser-side** (Client-side)
Web apps involve two main environments:

- **Server-side** (Backend):
	- Code runs on the server (e.g., Node.js, PHP, Python/Django/Flask, Ruby, Java, Go).
	- Handles logic, databases, authentication, file storage.
	- Generates responses (HTML, JSON, etc.).

- **Browser-side** (Frontend / Client-side):
	- Core trio: **HTML** (structure) + **CSS** (presentation) + **JavaScript** (behavior).
	- Runs entirely in the user's browser.
	- Parses HTML/CSS/JS, renders visuals, handles user interactions.

Server-side code creates what the browser receives → browser-side code brings it to life on your screen.

---
#### Beyond Static Webpages: **Requests & APIs**
- Not every request returns a full HTML page.
- Many modern sites/apps use **API calls** (often JSON) → return data only (no layout).
- Examples:
	- Mobile apps fetch data via APIs.
	- Single-Page Applications (React/Vue/Angular/Svelte) load once → then use Fetch/AJAX to update parts dynamically without full reloads.
	- Background requests for likes, comments, live updates, search autocomplete, etc.

This is why sites feel fast/responsive today — less full-page reloads, more targeted data exchanges.

---