# Internet
## How Does The Internet Work
- [Video](https://www.youtube.com/watch?v=7_LPdttKXPc)
### Transcript

**How does the internet work?**

Most of us know how to use the internet without actually understanding how it works, sort of like electricity in your home. You use it every day but may not understand the mechanics behind it. And if the electric grid is difficult to understand, then the internet must be impossible, right?

Wrong.

In the next few minutes, I’ll put you in the top 10 percent of people who understand how the internet actually works. For Security Catalyst dot com, I’m Aaron Titus.

Whenever most people think of the internet, this is what comes to mind: the internet is not a bubble or a cloud. Even in the new age of cloud computing, the whole fuzzy cloud picture was created by people more concerned about job security than education.

This is the internet.

The internet is a wire actually buried in the ground. It might be fiber optics, copper, or occasionally beamed to satellites or through cell phone networks, but the internet is simply a wire.

The internet is useful because two computers connected directly to this wire can communicate. A server is a special computer connected directly to the internet and has web pages or files on that server’s hard drive.

Every server has a unique Internet Protocol address, or IP address, just like a postal address. IP addresses help computers find each other. But since 72.14.205.100 doesn’t exactly roll off the tongue, we also give them names like google.com, facebook.com, or securitycatalyst.com.

This is how it works: your computer at home is not a server because it’s not connected directly to the internet. Computers you and I use every day are called clients because they’re connected indirectly to the internet through an internet service provider.

Here we’ll pretend this is my home laptop and I’m using DSL. Now let’s pretend I want to visit aol.com, which is coincidentally both a server and an ISP. I hop onto my laptop, go through my ISP onto the internet, connect to aol.com, and I can look at its web pages.

Now let’s say I want to send an email to Aunt Ruth. Ruth has AOL dial-up from home, and I’ve got a Gmail account. I log onto gmail.com and compose a message to Aunt Ruth at [ruth@aol.com](mailto:ruth@aol.com). Once I click send, gmail.com sends the email to aol.com. The next day, Aunt Ruth dials into AOL servers and retrieves the email.

Whenever an email, picture, or web page travels across the internet, computers break the information into smaller pieces called packets. When information reaches its destination, the packets are reassembled in their original order to make a picture, email, web page, or tweet.

Now imagine you’re at work sitting next to your boss, and you’re both surfing online. Your boss is doing market research, and you’re updating your Facebook profile. You’re both sending packets back and forth over the internet. What keeps your packets from accidentally ending up on your boss’s screen?

The solution is IP addresses and routers.

Everything connected directly or indirectly to the internet has an IP address — everything. That includes your computer, servers, cell phones, and all of the equipment in between.

Anywhere two or more parts of the internet intersect, there’s a piece of equipment called a router. Routers direct your packets around the internet, helping each packet get one step closer to its destination. Every time you visit a website, upwards of 10 to 15 routers may help your packets find their way to and from your computer.

Imagine each packet as a piece of candy wrapped in several layers. The first layer is your computer’s IP address. Your computer sends the packet to the first router, which adds its own IP address. Each time the packet reaches a new router, another layer is added until it reaches the server.

When the server sends information back, it creates packets with an identical wrapping. As the packet makes its way back over the internet, each router unwraps a layer to discover where to send the packet next, until it reaches your computer — and not your boss’s.

And that’s how the internet works in five minutes or less. You’re now easily in the top 10 percent of people who understand the basics of the internet. If you found this video helpful, check out securitycatalyst.com. I’m Aaron Titus.

---

### Study Notes
---

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
