
# Layer 1
## **أولًا: يعني إيه Web Reconnaissance؟**

تقدر تقول إنها أول خطوة بيعملها أي حد قبل ما يبدأ اختبار اختراق أو يهاجم ويب سايت.  
يعني زي ما بتذاكر قبل الامتحان… هنا بتجمع معلومات عن الهدف (الموقع أو التطبيق) قبل ما تبدأ أي هجوم فعلي.  
دي مرحلة اسمها **Information Gathering** في الـ **Penetration Testing Process**.
![[PT-process.webp]]

### **مراحل اختبار الاختراق (باختصار):**

1. **Pre-Engagement** – اتفاق مع العميل وتحديد النطاق.
    
2. **Information Gathering (Recon)** – جمع معلومات عن الهدف.
    
3. **Vulnerability Assessment** – تحديد الثغرات.
    
4. **Exploitation** – استغلال الثغرات.
    
5. **Post-Exploitation** – التحكم في السيستم بعد الاختراق.
    
6. **Lateral Movement** – التحرك بين الأجهزة أو السيرفرات.
    
7. **Proof-of-Concept** – إثبات إن الثغرة حقيقية.
    
8. **Post-Engagement** – تسليم التقرير والنتائج.
    

---

## **أهداف الـ Web Recon بالضبط**

1. **تحديد الأصول (Assets)**
    
    - تجيب كل حاجة ظاهرة أونلاين عن الهدف: صفحات، دومينات فرعية، IPs، التقنيات المستخدمة.
        
2. **اكتشاف معلومات مخفية**
    
    - زي ملفات الباك أب، ملفات الإعدادات، أو مستندات داخلية متسربة.
        
3. **تحليل سطح الهجوم (Attack Surface)**
    
    - تعرف نقاط الضعف والـ configurations الغلط والتقنيات اللي ممكن تستغلها.
        
4. **جمع معلومات مفيدة (Intelligence)**
    
    - زي أسماء موظفين، إيميلاتهم، أو سلوك ممكن تستخدمه في Social Engineering.
        

**المهاجمين** بيستخدموا المعلومات دي عشان يضربوا نقطة ضعف معينة.  
**الديفندرز (المدافعين)** بيعملوا نفس الخطوة دي عشان يسدوا الثغرات قبل ما حد يستغلها.

---

## **أنواع الـ Recon:**

### 1. **Active Reconnaissance** – نشيط

- هنا بتتعامل مع الهدف مباشرة (بتلمسه يعني).
    
- مخاطره عالية لأنه ممكن يتسجل أو يتكشف.
    

**أشهر التقنيات والأدوات:**

- **Port Scanning:** تعرف البورتات المفتوحة (أداة: Nmap).
    
- **Vulnerability Scanning:** تشوف الثغرات المعروفة (أدوات: Nessus – OpenVAS – Nikto).
    
- **Network Mapping:** تحدد الأجهزة المتصلة (Traceroute – Nmap).
    
- **Banner Grabbing:** تعرف إصدار السيرفر من البانر (Netcat – curl).
    
- **OS Fingerprinting:** تحدد نظام التشغيل (Nmap -O).
    
- **Service Enumeration:** تعرف إصدار الخدمات (Nmap -sV).
    
- **Web Spidering:** تزحف على الموقع تجيب الصفحات والفايلات (Burp Spider – ZAP Spider).
    

**الميزة:** معلومات مباشرة وكاملة.  
**العيب:** مخاطرة عالية، ممكن تتكشف بسهولة.

---

### 2. **Passive Reconnaissance** – سلبي

- هنا بتجمع معلومات **من غير ما تلمس الهدف نفسه**، بس بتعتمد على الحاجات اللي موجودة علنًا.
    
- المخاطرة فيها قليلة جدًا لأنها طبيعية.
    

**أشهر الطرق:**

- **Search Engine Queries:** تدور على معلومات في جوجل أو شونودان.
    
- **WHOIS Lookups:** تجيب بيانات تسجيل الدومين.
    
- **DNS Analysis:** تعرف الـ subdomains والسيرفرات.
    
- **Web Archive Analysis:** تشوف الموقع زمان كان عامل إزاي (Wayback Machine).
    
- **Social Media Analysis:** تجيب معلومات من LinkedIn وTwitter.
    
- **Code Repositories:** تدور على أكواد مسربة أو credentials في GitHub.
    

**الميزة:** صعب جدًا تتكشف.  
**العيب:** ممكن المعلومات ما تكونش كاملة زي الـ Active Recon.

---

## **الخلاصة**

- الـ **Web Recon** هو أول خطوة مهمة قبل أي اختبار اختراق أو أي هجوم.
    
- فيه نوعين: **Active (مخاطرة عالية)** و **Passive (مخاطرة قليلة)**.
    
- بنبدأ غالبًا بالـ **Passive Recon** لأنه آمن وبعد كده ننتقل للـ Active لو محتاجين تفاصيل أكتر.
    
- أول أداة بنتعلمها في الكورس دا هي **WHOIS** عشان نفهم ملكية الدومينات ونشوف البيانات الأساسية.
    

---
# Layer 2
---

## **أولًا: يعني إيه WHOIS؟**

تقدر تعتبره **دفتر تليفونات الإنترنت**.  
هو بروتوكول (query/response) بيخليك تسأل قاعدة بيانات عشان تجيب معلومات عن:

- **الدومينات (Domain Names)**
    
- **بلوكات الـ IP (IP Blocks)**
    
- **الأنظمة المستقلة (Autonomous Systems – ASNs)**
    

بمعنى تاني: لو عايز تعرف مين صاحب موقع معين أو مين مسؤول عن IP معين… بتستخدم WHOIS.

---

## **إزاي بيشتغل WHOIS؟**

أنت بتكتب أمر بسيط في التيرمنال:

`whois inlanefreight.com`

وهيطلع لك بيانات زي:

- اسم الدومين
    
- الشركة اللي سجلت الدومين (Registrar)
    
- بيانات الشخص أو الشركة اللي مسجلين الدومين (Registrant Contact)
    
- بيانات مسؤول الإدارة (Administrative Contact)
    
- بيانات مسؤول التقنية (Technical Contact)
    
- تاريخ إنشاء الدومين وتاريخ الانتهاء
    
- السيرفرات اللي بتحل اسم الدومين (Name Servers)
    

---

## **مثال على النتايج:**

```
```Domain Name: inlanefreight.com
 Registrar WHOIS Server: whois.registrar.amazon 
 Registrar URL: https://registrar.amazon.com 
 Updated Date: 2023-07-03
  Creation Date: 2019-08-05`
```
![[Pasted image 20250902120856.png]]

---

## **حكاية WHOIS – لمحة تاريخية**

- الفضل في الـ WHOIS بيرجع لـ **Elizabeth Feinler**، عالمة كمبيوتر في السبعينات.
    
- أيام الـ **ARPANET** (قبل ما الإنترنت يتولد)، كانوا محتاجين نظام يتتبع الموارد والشبكات اللي بتكبر بسرعة.
    
- فريقها في **Stanford Research Institute NIC** عمل قاعدة بيانات بسيطة وقتها لتخزين معلومات عن المستخدمين والدومينات والهوست نيمز.
    
- النظام دا هو اللي اتطور وبقى WHOIS اللي بنستخدمه النهارده.
    

---

## **ليه WHOIS مهم في Web Recon؟**

1. **تحديد الأشخاص الأساسيين (Key Personnel)**
    
    - ممكن WHOIS يطلع لك أسامي أو إيميلات أو تليفونات الناس اللي ماسكين الدومين.
        
    - دا ممكن يخدمك في الـ **Social Engineering** أو الـ **Phishing**.
        
2. **اكتشاف بنية الشبكة (Network Infrastructure)**
    
    - الـ Name Servers والـ IPs بتوضح لك شكل البنية الداخلية وممكن تكشف Misconfigurations.
        
3. **تحليل البيانات التاريخية (Historical Data)**
    
    - مواقع زي **WhoisFreaks** بتوريك WHOIS زمان كان شكله إيه.
        
    - تقدر تشوف الدومين كان ملك مين زمان أو حصل تغيير في الشركة أو البيانات.
        

---

## **الخلاصة**

- WHOIS أداة أساسية جدًا في الـ **Passive Recon**.
    
- بتجمع منها معلومات بدون ما تلمس الهدف.
    
- المعلومة ممكن تبان بسيطة بس ساعات بتفتح لك أبواب كبيرة جدًا للهجوم.
  

------
# Layer 3
## **استخدام WHOIS في جمع المعلومات (Information Gathering)**

WHOIS 

مش بس بيديك بيانات عن ملكية الدومينات، لكن كمان بيساعدك في **تحليل التهديدات** وفهم البنية التحتية لأي جهة أو هجوم.  
هنا 3 سيناريوهات عملية بتوضح قد إيه WHOIS مفيد:

---

### **السيناريو الأول: تحقيق في Phishing (الإيميلات الاحتيالية)**

- شركة الأمن بتلاحظ إيميل مشبوه بيقول إنه من بنك الشركة وبيطلب من الموظفين يدخلوا على لينك ويحدثوا بياناتهم.
    
- محلل الأمن بيعمل **WHOIS Lookup** على الدومين الموجود في الإيميل.
    
- النتائج:
    
    - الدومين متسجل من أيام قليلة (غالبًا موقع مزيف جديد).
        
    - بيانات المالك متخبية ورا Privacy Service.
        
    - الـ Name Servers تخص استضافة مشبوهة (Bulletproof Hosting) معروفة في الجرائم الإلكترونية.
        

**الخلاصة:**  
دي علامات قوية على إنه هجوم Phishing.

- يتم تنبيه قسم الـ IT يحظر الدومين فورًا.
    
- يتم تحذير الموظفين.
    
- كمان ممكن يتم التحقيق في الـ IPs أو السيرفرات المرتبطة بالدومين عشان يكشفوا مواقع إضافية للهجوم.
    

---

### **السيناريو الثاني: تحليل Malware (برمجيات خبيثة)**

- باحث أمني بيحلل Malware بيتصل بسيرفر خارجي (C2 Server).
    
- بيعمل WHOIS على الدومين بتاع السيرفر.
    
- النتائج:
    
    - الدومين متسجل بإيميل مجاني مجهول.
        
    - الدولة اللي متسجل فيها الدومين معروفة بكثرة الجرائم الإلكترونية.
        
    - الـ Registrar (الشركة المسجل فيها الدومين) معروف بتراخي سياسات مكافحة سوء الاستخدام.
        

**الخلاصة:**

- السيرفر غالبًا مستضاف على **Bulletproof Hosting** أو سيرفر مخترق.
    
- الباحث بيستخدم البيانات عشان يبلغ مزود الخدمة ويوقف النشاط الضار.
    

---

### **السيناريو الثالث: إعداد تقرير Threat Intelligence**

- شركة أمن سيبراني بتراقب مجموعة هجمات متطورة على البنوك.
    
- بيجمعوا WHOIS Data عن مجموعة دومينات استخدمتها المجموعة في الهجمات.
    
- بعد التحليل يلاقوا:
    
    - الدومينات بتتسجل في مجموعات (Clusters) قبل الهجمات مباشرة.
        
    - نفس الأشخاص أو أسماء وهمية بيتكرروا.
        
    - الـ Name Servers مشتركة (بنية تحتية واحدة للهجوم).
        
    - الدومينات القديمة تم إيقافها قبل كده بواسطة جهات أمنية.
        

**الخلاصة:**

- المحللين بيعملوا **ملف كامل عن أسلوب المجموعة** (TTPs).
    
- بيطلعوا **Indicators of Compromise (IOCs)** عشان الشركات التانية تعرف تكتشف الهجمات المشابهة.
    

---

## **إزاي تستخدم WHOIS على لينكس؟**

لو مش متسطب:

`sudo apt update sudo apt install whois -y`

بعدها تقدر تسأل أي دومين:

`whois facebook.com`

---

## **تحليل مثال WHOIS – facebook.com**

**النتايج المهمة:**

1. **بيانات التسجيل:**
    
    - Registrar: RegistrarSafe, LLC
        
    - إنشاء الدومين: 1997
        
    - انتهاء التسجيل: 2033  
        → دا بيوضح إنه دومين قديم وموثوق ومش بيتجدد بسرعة زي الدومينات المشبوهة.
        
2. **مالك الدومين:**
    
    - الشركة: Meta Platforms, Inc.
        
    - المسؤول: Domain Admin  
        → طبيعي جدًا لأن فيسبوك شركة كبيرة تحت Meta.
        
3. **حماية الدومين (Domain Status):**
    
    - clientDeleteProhibited / clientTransferProhibited / clientUpdateProhibited … إلخ  
        → كل دي قيود ضد أي تعديل أو نقل أو حذف غير مصرح.
        
4. **Name Servers:**
    
    - كلها ضمن facebook.com → الشركة بتدير الـ DNS بنفسها لضمان الأمان والثبات.
        

**الخلاصة:**

- البيانات كلها منطقية لشركة كبيرة.
    
- WHOIS هنا مفيد في **التأكد من ملكية الدومين**، بس مش هيكشف لك أسماء موظفين أو ثغرات مباشرة.
    
- لازم تستخدم WHOIS مع أساليب Recon تانية عشان تبني صورة كاملة.
    

---
# Layer 4
## **DNS – نظام أسماء النطاقات**

DNS هو **دليل الإنترنت** أو **GPS المواقع**:

- بدل ما نحفظ أرقام الـ IP (زي 192.0.2.1)، بنستخدم أسماء سهلة (زي [www.example.com](http://www.example.com?utm_source=chatgpt.com)).
    
- DNS بيترجم الاسم إلى IP عشان جهازك يعرف يتواصل مع السيرفر الصحيح.
    

**بدون DNS:** تخيل إنك لازم تحفظ إحداثيات كل مكان تزوره – صعب جدًا وغير عملي.  
**مع DNS:** تكتب الاسم، وهو يوصلك للعنوان تلقائيًا.

---

## **إزاي بيشتغل DNS؟** _(العملية خطوة بخطوة)_

![[Pasted image 20250710142811.png]]

1. **DNS Query – جهازك يسأل أولًا:**
    
    - الجهاز بيشوف لو العنوان محفوظ عنده (Cache).
        
    - لو مش موجود، بيسأل **DNS Resolver** (عادة بتاع الـ ISP).
        
2. **Recursive Lookup – الـ Resolver يبدأ الرحلة:**
    
    - لو الـ Resolver مش عنده الإجابة، بيبدأ يسأل في تسلسل الـ DNS:
        
    - **Root Server** → بيعرف أي TLD مسؤول (.com, .org…)
        
    - **TLD Server** → يعرفك بالسيرفر المسؤول عن الدومين نفسه
        
    - **Authoritative Server** → بيرجع الـ IP النهائي.
        
3. **الـ Resolver يرجع النتيجة للجهاز:**
    
    - ويحفظها مؤقتًا (Cache) لتسريع المرات الجاية.
        
4. **الجهاز يتصل بالسيرفر:**
    
    - دلوقتي جهازك عارف الـ IP، فيوصل مباشرة للموقع.

![[Pasted image 20250707153432.png]]

---

## **ملف الـ Hosts – اختصار يدوي لـ DNS**

- موجود في:
    
    - **Windows:** `C:\Windows\System32\drivers\etc\hosts`
        
    - **Linux/Mac:** `/etc/hosts`
        
- بيسمح لك تربط اسم دومين بـ IP معين يدويًا.
    
- بيشتغل قبل DNS (يعني بيعمل Override).
    

**أمثلة:**

`127.0.0.1   localhost 
`192.168.1.10 devserver.local 
`0.0.0.0 unwanted-site.com`

**الاستخدامات:**

- تطوير المواقع (توجّه دومين لسيرفر محلي).
    
- اختبار اتصال جهاز معين.
    
- حظر مواقع مزعجة.
    

---

## **ملفات DNS Zone – الخريطة الكاملة**

DNS Zone 
هي **جزء من مساحة أسماء الإنترنت** يديره مسؤول واحد.  
**Zone File** هو الملف اللي فيه كل الـ DNS Records.

**مثال بسيط:**

```
```$TTL 3600 @ IN SOA ns1.example.com. admin.example.com. (2024060401 3600 900 604800 86400) @ IN NS  ns1.example.com. @ IN NS  ns2.example.com. @ IN MX 10 mail.example.com. www IN A 192.0.2.1 mail IN A 198.51.100.1 ftp  IN CNAME www.example.com.
```

**الملف دا يحدد:**

- السيرفرات الرئيسية (NS Records)
    
- السيرفرات المسؤولة عن البريد (MX Record)
    
- عناوين الأجهزة (A Records)
    
- الأسماء البديلة (CNAME Records)
    

---

## **أشهر أنواع DNS Records**

| النوع     | الوصف                         | مثال                                                                                      |
| --------- | ----------------------------- | ----------------------------------------------------------------------------------------- |
| **A**     | يربط دومين بـ IPv4            | [www.example.com](http://www.example.com?utm_source=chatgpt.com) → 192.0.2.1              |
| **AAAA**  | يربط دومين بـ IPv6            | [www.example.com](http://www.example.com?utm_source=chatgpt.com) → 2001:db8::1            |
| **CNAME** | اسم مستعار لدومين آخر         | blog.example.com → webserver.example.net                                                  |
| **MX**    | بريد إلكتروني                 | example.com → mail.example.com                                                            |
| **NS**    | سيرفرات الـ DNS               | example.com → ns1.example.com                                                             |
| **TXT**   | نصوص عشوائية (تحقق أو سياسات) | SPF records                                                                               |
| **SOA**   | معلومات إدارية عن الدومين     | السيرفر الرئيسي، البريد المسؤول…                                                          |
| **SRV**   | خدمة على دومين وبورت معين     | _sip._udp.example.com → sipserver.example.com                                             |
| **PTR**   | عكس الـ DNS (IP → Domain)     | 1.2.0.192.in-addr.arpa → [www.example.com](http://www.example.com?utm_source=chatgpt.com) |

---

## **ليه DNS مهم في Web Recon؟**

1. **كشف الأصول المخفية (Uncovering Assets):**
    
    - ممكن تلاقي Subdomains أو سيرفرات بريد أو أجهزة قديمة عن طريق Records زي CNAME أو A.
        
2. **رسم خريطة الشبكة (Mapping Infrastructure):**
    
    - NS Records بتكشف مزود الخدمة.
        
    - A Records ممكن تحدد Load Balancers أو مناطق معينة من الشبكة.
        
3. **متابعة التغييرات (Monitoring Changes):**
    
    - ظهور Subdomain جديد زي vpn.example.com → ممكن يبقى مدخل للشبكة.
        
    - TXT Records
    - فيها بيانات عن استخدام خدمات معينة (زي 1Password) → مفيدة للهندسة الاجتماعية.
-----------
# Layer 5
## **Digging DNS – التنقيب داخل DNS**

بعد ما فهمنا أساسيات الـ DNS وأنواع الـ Records، دلوقتي ندخل في الجزء العملي:  
**إزاي نستخدم أدوات لاستخراج معلومات مهمة عن الدومينات والسيرفرات؟**

---

## **أشهر أدوات DNS Recon**

| الأداة                | المميزات                                             | الاستخدام                                          |
| --------------------- | ---------------------------------------------------- | -------------------------------------------------- |
| **dig**               | قوي ومرن – يدعم كل أنواع الاستعلام (A, MX, NS, TXT…) | تحليل عميق، Zone Transfer (لو مسموح)، حل مشاكل DNS |
| **nslookup**          | بسيط – أساسي في أي نظام تشغيل                        | استعلام سريع عن A و MX Records                     |
| **host**              | مخرجات مختصرة وسريعة                                 | استعلام سريع عن عناوين IP                          |
| **dnsenum**           | تلقائي – يدعم Brute Force و Zone Transfer            | اكتشاف Subdomains بكفاءة                           |
| **fierce**            | سهل الاستخدام – يدعم Recursive Search                | فحص شامل للـ Subdomains                            |
| **dnsrecon**          | شامل – مخرجات بعدة صيغ                               | Enumeration متقدم ومخططات كاملة                    |
| **theHarvester**      | OSINT – يجمع بيانات من مصادر مختلفة                  | جمع إيميلات وموظفين وسجلات DNS                     |
| **Online DNS Lookup** | واجهة رسومية سهلة الاستخدام                          | بحث سريع بدون سطر الأوامر                          |



|الأداة|المميزات الأساسية|متى تستخدمها؟|مستوى التفاصيل|
|---|---|---|---|
|**dig**|- أقوى وأشمل أداة- يدعم كل أنواع السجلات- مخرجات قابلة للتخصيص بالكامل|- تحليل متقدم- تتبع عملية حل الدومين- مشاكل DNS المعقدة|عالي جدًا|
|**nslookup**|- بسيط ومتوفر في كل الأنظمة- مخرجات واضحة وسريعة|- فحص سريع لـ A / MX Records- استخدام يومي بدون تعقيد|متوسط|
|**host**|- خفيف جدًا ومباشر- مخرجات مختصرة للغاية|- استعلامات بسيطة- الحصول على IP أو Mail Server بسرعة|منخفض|


---

## **أداة dig – Domain Information Groper**

- **الأداة الأقوى والأكثر مرونة** لعمل استعلامات DNS متقدمة.
    
- **تُظهر نتائج تفصيلية قابلة للتخصيص.**
    

### **أوامر شائعة:**

```
dig domain.com           ← استعلام A Record افتراضي
dig domain.com A         ← استعلام IPv4 فقط
dig domain.com AAAA      ← استعلام IPv6 فقط
dig domain.com MX        ← معرفة سيرفرات البريد
dig domain.com NS        ← معرفة السيرفرات المسؤولة عن الدومين
dig domain.com TXT       ← جلب TXT Records
dig domain.com SOA       ← معرفة بيانات المسؤول الرئيسية عن الدومين
dig @1.1.1.1 domain.com  ← استعلام من DNS Server محدد
dig +trace domain.com    ← تتبع كامل لعملية حل الدومين
dig -x 192.168.1.1       ← Reverse Lookup (IP → Domain)
dig +short domain.com    ← مخرجات مختصرة – فقط الإجابة
dig +noall +answer domain.com ← إظهار قسم الإجابة فقط
dig domain.com ANY       ← جلب كل الـ Records (ممكن بعض السيرفرات ترفض)

```
**تحذير:**

- بعض السيرفرات تراقب وتمنع الاستعلامات المفرطة.
    
- دايمًا لازم تاخد إذن قبل عمل DNS Recon موسّع.
    

---

## **تحليل مثال dig لـ google.com**

![[Pasted image 20250902123819.png]]

الأمر:

`dig google.com`

**الناتج بيظهر 4 أقسام رئيسية:**

### **1. Header (الرأس)**

`;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16449`

- **opcode: QUERY** → نوع الطلب هو Query
    
- **status: NOERROR** → مفيش أخطاء، الرد سليم
    
- **id: 16449** → رقم مميز للاستعلام
    

`;; flags: qr rd ad; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0`

- **qr:** هذا رد (Query Response)
    
- **rd:** طلب تكراري (Recursion Desired)
    
- **ad:** البيانات موثوقة (Authentic Data)
    
- الأرقام: سؤال واحد، جواب واحد، بدون سجلات سلطة أو إضافية
    

`;; WARNING: recursion requested but not available`

- السيرفر لا يدعم الاستعلام التكراري (Recursive).
    

---

### **2. Question Section**

`;google.com. IN A`

- بيسأل عن **عنوان IPv4 (A Record)** للدومين google.com
    

---

### **3. Answer Section**

`google.com. 0 IN A 142.251.47.142`

- **IP هو 142.251.47.142**
    
- **0 TTL:** يعني النتيجة ما تتخزنش طويل في الكاش.
    

---

### **4. Footer (التذييل)**

`;; Query time: 0 msec       ← الاستعلام كان سريع جدًا
`;; SERVER: 172.23.176.1#53  ← السيرفر اللي رجّع النتيجة (UDP) 
`;; WHEN: Thu Jun 13 ...      ← وقت تنفيذ الاستعلام 
`;; MSG SIZE  rcvd: 54        ← حجم الرد 54 بايت`

---

## **ملاحظات إضافية**

- **EDNS (Extension Mechanisms for DNS):** 
- ممكن يظهر قسم إضافي (opt pseudosection) لدعم ميزات زي DNSSEC أو زيادة حجم الردود.
    
- **لو عايز الإجابة بس:**
    
    `dig +short google.com`
    
    → النتيجة هتكون بس:
    
    `142.251.47.142`
    

---
# Layer 6
## **أهمية البحث عن الـ Subdomains**

- **بيئات تطوير واختبار (Dev/Staging):** غالبًا أقل أمانًا وقد تكشف معلومات حساسة.
    
- **بوابات تسجيل دخول مخفية:** قد تحتوي لوحات تحكم أو صفحات غير مخصصة للعامة.
    
- **تطبيقات قديمة (Legacy Apps):** برامج غير مُحدَّثة بها ثغرات معروفة.
    
- **معلومات حساسة:** مثل ملفات إعدادات أو وثائق داخلية يمكن الوصول إليها.
    

---

## **طرق اكتشاف الـ Subdomains**

### **1. Active Enumeration**

- **الوصف:** تتفاعل مباشرة مع خوادم DNS الخاصة بالهدف.
    
- **الطرق الشائعة:**
    
    - **Zone Transfer:** إذا كان السيرفر مُهيأ بشكل خاطئ، يمكن الحصول على كل السجلات.
        
    - **Brute Force:** تجربة قائمة كلمات (Wordlist) لأسماء Subdomains.
        
- **الأدوات:**
    
    - `dnsenum`
        
    - `ffuf`
        
    - `gobuster`
        

> **المميزات:** دقة عالية وتحكم كامل.  
> **العيوب:** أكثر وضوحًا وقابل للكشف.

---

### **2. Passive Enumeration**

- **الوصف:** تعتمد على مصادر خارجية بدون التواصل مع سيرفر الهدف مباشرة.
    
- **الطرق الشائعة:**
    
    - **Certificate Transparency Logs:** الشهادات تكشف أسماء Subdomains في SAN Field.
        
    - **محركات البحث (site:domain.com):** لجمع روابط غير مكشوفة رسميًا.
        
    - **قواعد بيانات DNS عامة:** مثل خدمات تجمع سجلات DNS من مصادر مختلفة.
        

> **المميزات:** أكثر سرية وصعوبة في الاكتشاف.  
> **العيوب:** قد لا تعثر على كل Subdomains.

---

## **أفضل استراتيجية**

- **الجمع بين الطريقتين Active + Passive** للحصول على صورة شاملة ودقيقة.

-------
# Layer 7
## **ما هو Subdomain Bruteforcing؟**

- **تعريف:** تقنية نشطة (Active) لاكتشاف الـ Subdomains من خلال تجربة أسماء محتملة مسبقًا باستخدام Wordlists.
    
- **الهدف:** العثور على Subdomains مخفية أو غير موثقة يمكن أن تكشف معلومات حساسة أو نقاط دخول محتملة.
    

---

## **خطوات العملية**

1. **اختيار الـ Wordlist:**
    
    - **عام (General):** كلمات شائعة مثل `dev`, `mail`, `admin`
        
    - **مستهدف (Targeted):** أسماء مرتبطة بالصناعة أو الشركة
        
    - **مخصص (Custom):** إنشاء قائمة خاصة اعتمادًا على معلومات سابقة
        
2. **Iteration and Querying:**
    
    - يتم تجربة كل كلمة مع الدومين (مثال: `dev.example.com`)
        
3. **DNS Lookup:**
    
    - التحقق مما إذا كان Subdomain يحلّ (Resolve) إلى عنوان IP (A أو AAAA Record).
        
4. **Filtering and Validation:**
    
    - حفظ الـ Subdomains الصالحة
        
    - أحيانًا اختبار الوصول عبر المتصفح للتحقق من وجود خدمة فعليًا
        

---

## **أشهر الأدوات**

- **dnsenum** – شاملة، تدعم Zone Transfer وBruteforce وWHOIS
    
- **fierce** – سهلة الاستخدام مع Recursive Search
    
- **dnsrecon** – متعددة المميزات مع دعم مخرجات مخصصة
    
- **amass** – قوية ومتكاملة مع أدوات OSINT أخرى
    
- **assetfinder** – سريعة وخفيفة لفحص سريع
    
- **puredns** – فعالة جدًا في الـ Brute-force مع فلترة ممتازة
    

---

## **dnsenum – نظرة تفصيلية**

**وظائف رئيسية:**

- استخراج سجلات DNS المختلفة (A, AAAA, NS, MX, TXT)
    
- محاولة Zone Transfer تلقائيًا
    
- دعم Brute-Force لاكتشاف Subdomains باستخدام Wordlist
    
- البحث عبر Google (Google Scraping) لاكتشاف روابط إضافية
    
- Reverse DNS Lookup للكشف عن دومينات أخرى على نفس الـ IP
    
- WHOIS Lookup لجمع بيانات الملكية والتسجيل
    

**مثال عملي:**

`dnsenum --enum inlanefreight.com \   -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt \   -r`

- `--enum` = تشغيل مجموعة خيارات مُهيأة مسبقًا
    
- `-f` = تحديد مسار الـ Wordlist
    
- `-r` = Recursive Bruteforcing لاكتشاف Subdomains متداخلة
    

**مخرجات نموذجية:**

- `www.inlanefreight.com → 134.209.24.248`
    
- `support.inlanefreight.com → 134.209.24.248`
    

---

## **الخلاصة**

- **Bruteforcing = فعال لكنه صاخب ويمكن اكتشافه**
    
- **dnsenum = أداة قوية تجمع بين عدة تقنيات (DNS Records + Zone Transfer + Bruteforce + WHOIS + Google)**
    
- **أفضل الممارسات:** الجمع بين **Active** و **Passive Enumeration** لضمان تغطية شاملة

-----
# Layer 8
## **ما هو DNS Zone Transfer؟**
![[Pasted image 20250902132632.png]]

- **تعريف:**  
    آلية تُستخدم لمزامنة سجلات DNS بين خوادم الـ DNS الأساسية (Primary) والثانوية (Secondary).
    
- **الوظيفة الأساسية:**
    
    - ضمان تطابق جميع بيانات الدومين والـ Subdomains بين الخوادم.
        
    - يستخدم نوع الاستعلام **AXFR (Full Zone Transfer)** لنقل جميع السجلات.
        

---

## **كيف تتم عملية Zone Transfer؟**

1. **طلب النقل (AXFR Request):**  
    الخادم الثانوي يطلب نسخة من البيانات من الخادم الأساسي.
    
2. **نقل سجل SOA (Start of Authority):**  
    يحتوي على رقم التسلسل لمراجعة حداثة البيانات.

	```
	example.com.  3600  IN  SOA  ns1.example.com. admin.example.com. (
                 2025090201 ; serial
                 7200       ; refresh (2 hours)
                 3600       ; retry (1 hour)
                 1209600    ; expire (2 weeks)
                 3600       ; minimum TTL (1 hour)
)

	```
3. **إرسال السجلات (A, AAAA, MX, CNAME, NS...):**  
    الخادم الأساسي يرسل جميع بيانات الدومين والـ Subdomains.
    
4. **إكمال النقل (Zone Transfer Complete):**  
    الخادم الأساسي يؤكد انتهاء النقل.
    
5. **إقرار الاستلام (ACK):**  
    الخادم الثانوي يرسل رسالة تؤكد استلام البيانات بنجاح.
    

---

## **أين تكمن الثغرة؟**

- **المشكلة:**  
    إذا كان الخادم الأساسي **يسمح لأي عميل بطلب Zone Transfer** (بدون تقييد)، يمكن لأي شخص تحميل ملف الـ Zone بالكامل.
    
- **النتيجة:**  
    يحصل المهاجم على:
    
    - قائمة كاملة بالـ Subdomains
        
    - عناوين الـ IP المرتبطة بها
        
    - تفاصيل عن Name Servers والبنية التحتية

		`dig @ns1.example.com example.com AXFR
`

---

## **لماذا يُعتبر خطيرًا؟**

- كشف بيئات تطوير أو إدارة غير معلنة.
    
- تحديد عناوين IP مباشرة لاستهدافها.
    
- التعرف على مزوّد الخدمة ومشاكل التهيئة.
    

---

## **كيف يتم منعه؟**

- السماح بعملية Zone Transfer **فقط لخوادم DNS الثانوية الموثوقة**.
    
- تحديث إعدادات الـ DNS لمنع الوصول العام (Access Control).
    

---

## **استغلال Zone Transfer عمليًا**

**باستخدام dig:**

`dig axfr @nsztm1.digi.ninja zonetransfer.me`

- **axfr** = طلب نقل كامل للمنطقة.
    
- **@nsztm1.digi.ninja** = الخادم المسؤول عن الدومين.
    
- **zonetransfer.me** = الدومين الهدف.
    

**إذا كان السيرفر مُهيأ بشكل خاطئ:**

- سيُرجع قائمة شاملة بكل السجلات (A, MX, TXT, NS, PTR, SRV…).
    
- مثال من الإخراج:
    
    - `zonetransfer.me. IN A 5.196.105.14`
        
    - `www.zonetransfer.me. IN PTR 14.105.196.5`
        
    - `canberra-office.zonetransfer.me. IN A 202.14.81.230`
        

---

## **الخلاصة**

- **Zone Transfer = أداة إدارية مشروعة** لكن إذا كانت مفتوحة للعامة تصبح **ثغرة حرجة**.
    
- **قيمة عالية في جمع المعلومات:** توفر خريطة كاملة للدومين.
    
- **الحماية:** قصر الوصول على خوادم موثوقة فقط.
    
- **حتى لو فشل الطلب:** يفيد في تقييم إعدادات أمان الـ DNS.
-----------------
# Layer 9

## يعني إيه Virtual Hosts وليه تهمّنا في الويب ركون؟

بعد الـ DNS بيوصّل الطلب على الـ IP الصح، **الويب سيرفر** (Apache/Nginx/IIS) هو اللي بيقرر يقدّم لك أنهي موقع على نفس السيرفر.  
السيرفر يقدر يستضيف **مواقع/دومينات كتير على نفس الـ IP** عن طريق حاجة اسمها **Virtual Hosting**، والتمييز بيكون أساسًا من **HTTP Host header** اللي المتصفح بيبعته في كل طلب.

## Subdomain vs VHost — الفرق باختصار

- **Subdomain (زي blog.example.com):**  
    جزء من الدومين، ليه **سجل DNS** غالبًا (A/AAAA/CNAME)، ممكن يروح لنفس الـ IP بتاع الـ root domain أو IP مختلف.
    
- **VHost (إعداد داخل السيرفر):**  
    تعريف جوّه الويب سيرفر بيقول: **لو Host header = كذا → قدّم ملفات كذا**.  
    الـ VHost ممكن يكون لدومين تاني خالص أو Subdomain، وممكن **ما يكونش له DNS record أصلاً** (دا اللي بنسميه “غير مُعلن” / internal).
    

> مهمة للمختبر الأمني: ممكن يكون عندك **VHosts متخفية** مش ظاهرة في DNS. تقدر توصل لها إمّا بتعديل **hosts file** محليًا، أو بفزّة الـ Host header (VHost fuzzing) على الـ IP.

---

## إزاي السيرفر بيختار الموقع الصح؟ (VHost Lookup Flow)

1. **المتصفح يطلب عنوان** (مثال: `www.inlanefreight.com`) بعد ما DNS يجيب الـ IP.
    
2. الطلب بيحتوي **Host: [www.inlanefreight.com](http://www.inlanefreight.com/)**.
    
3. الويب سيرفر يطابق الـ Host header مع الكونفيج:
    
    - لو لقى VHost مطابق → يقدّم **DocumentRoot** الخاص بيه.
        
    - لو مفيش مطابق → يقدّم **الـ default vhost** (ساعات صفحة عامة أو Error).
        

> الـ Host header هنا زي “المفتاح” اللي بيختار أي موقع يتقدّم من نفس السيرفر.

---

## أنواع الـ Virtual Hosting

| النوع          | الفكرة                               | المزايا                       | العيوب / ملاحظات                                                 |
| -------------- | ------------------------------------ | ----------------------------- | ---------------------------------------------------------------- |
| **Name-Based** | تمييز بالمجال عبر **Host header**    | أوفر IPs، أسهل إعداد          | قيود قديمة مع SSL/TLS؛ بس حاليًا مع **SNI** المشكلة اتحلت غالبًا |
| **IP-Based**   | لكل موقع **IP مختلف**                | عزل أفضل، يعمل مع أي بروتوكول | يكلف IPs أكتر، أقل قابلية للتوسع                                 |
| **Port-Based** | نفس IP لكن بورتات مختلفة (80, 8080…) | بديل لو IP قليل               | غير عملي للمستخدمين (لازم يكتبوا بورت في الـ URL)                |

> **SNI (Server Name Indication):** 
> للـ HTTPS، السيرفر يختار الشهادة حسب **الاسم** أثناء Handshake. لو بتفزّ HTTPS على IP، لازم الأداة/الطريقة تبعت **الاسم** كـ SNI؛ وإلا هتشوف شهادة غلط أو vhost غلط.

---

## اكتشاف الـ VHosts (Virtual Host Discovery)

فيه مواقع كتير على نفس الـ IP، بعضها:

- **مُعلن في DNS** (subdomain طبيعي).
    
- **غير مُعلن في DNS** (internal/test/admin/stage) ومش هتلاقيه بالبحث العادي.
    

## الطرق والأدوات

- **يدوي (للفهم والـ baseline):**
    
    - `curl -H "Host: اسم" http://IP/ -i` وشوف **Status/Headers/Length**.
        
    - للـ HTTPS واستخدام SNI الصح:  
        `curl --resolve اسم:443:IP https://اسم/ -k -i`  
        (`--resolve` بيعمل DNS+SNI محليًا للطلب دا بس).
        
- **أدوات فزّة جاهزة:**
    
    - **gobuster vhost** (سريع وعملي للـ Host header fuzzing).
        
    - **ffuf** (مرن جدًا: `-H "Host: FUZZ.example.com"`).
        
    - **feroxbuster** (سريع، فيلترز كويسة، يقدر يعمل vhost بأسلوب شبيه).
        

---

## Gobuster VHost — الاستخدام العملي

## قبل ما نبدأ

1. **هات الـ IP المستهدف** (من DNS أو من مسح سابق).
    
2. **اختار wordlist** مناسبة (مثال: من SecLists) أو اعمل واحدة مخصصة حسب نمط الشركة (`dev, stage, admin, portal, api, intranet, legacy…`).
    
3. لو مفيش DNS record للـ base domain، استخدم:
    
    - **/etc/hosts** لإجبار الاسم للـ IP، أو
        
    - `curl --resolve`/أداة تدعم SNI بالاسم المتجرّب.
        

## أمر شائع:

```bash
gobuster vhost \
  -u http://<TARGET_IP> \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt \
  --append-domain \
  -t 10 \
  -o vhosts.txt
```

**شرح الفلاجز:**

- `-u` : الـ URL على **IP** (ممكن بورت غير 80: `http://IP:81`).
    
- `-w` : الـ wordlist.
    
- `--append-domain` : يضيف **base domain** لكل كلمة (لازم في الإصدارات الحديثة).
    
- `-t` : عدد الثريدز (زَوِّد بحذر).
    
- `-o` : حفظ النتائج.
    

**مثال زي اللي في سؤالك:**

```bash
gobuster vhost -u http://inlanefreight.htb:81 \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt \
  --append-domain
```

**مخرجات متوقعة:**

```
Found: forum.inlanefreight.htb:81  Status: 200  [Size: 100]
```

## فلاتر ونصايح أثناء الفحص

- ركّز على اختلافات: **Status code**، **Content-Length**، **Redirect Location**، **Cookies مميزة**.
    
- لو السيرفر بيرد 200 لأي Host (Wildcard/Default VHost):
    
    - اعمل **baseline** بطلبات عشوائية، وفلتر النتائج اللي طولها زي الـ baseline.
        
    - مع **ffuf** مثلًا تقدر تستخدم فلترة بالطول/الكلمات.
        
- للـ HTTPS اللي فيه شهادات mismatch: استخدم `-k` (تجاهل أخطاء TLS) بحذر.
    
- قلّل الضوضاء: حدّد **status codes** المهمة (200/301/302/401/403) واستبعد الباقي.
    
- راعي الـ **Rate Limits** عشان متتَحظرش، وزوّد **Timeout** لو الشبكة بطيئة.
    

---

## ffuf / feroxbuster — بدائل مرنة

**ffuf (VHost عبر Header FUZZ):**

```bash
ffuf -u http://<IP>/ \
  -H "Host: FUZZ.example.com" \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt \
  -mc 200,301,302,401,403 \
  -o ffuf_vhosts.json
```

- للـ HTTPS وسني صحيح: استخدم `https://<IP>/` مع `--ignore-body` + فلترة على الحجم/الكلمات، أو اعتمد `--resolve` بنسخة curl لتأكيد النتائج المشكوك فيها.
    

**feroxbuster (Header Injection):**

```bash
feroxbuster -u http://<IP>/ \
  -H "Host: FUZZ.example.com" \
  -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt \
  -x '' --silent
```

> الفكرة واحدة: بنجرّب قيم مختلفة للـ **Host** على نفس الـ IP ونقارن الردود.

---

## لو مفيش DNS Record — أوصل إزاي؟

- **hosts file** (محليًا):
    
    - Linux/Mac: `/etc/hosts`
        
    - Windows: `C:\Windows\System32\drivers\etc\hosts`  
        مثال:
        
    
    ```
    10.10.10.10  dev.example.com
    ```
    
    بعدها جرّب `http://dev.example.com/` عادي.
    
- **curl --resolve** (جلسة واحدة):
    
    ```
    curl --resolve dev.example.com:443:10.10.10.10 https://dev.example.com/ -k -I
    ```
    
    دا بيظبط **DNS + SNI** للطلب دا فقط—ممتاز للتحقق السريع.
    

---

## أمثلة كونفيج (Apache) عشان تتخيّل الصورة

```apache
<VirtualHost *:80>
  ServerName www.example1.com
  DocumentRoot /var/www/example1
</VirtualHost>

<VirtualHost *:80>
  ServerName www.example2.org
  DocumentRoot /var/www/example2
</VirtualHost>

<VirtualHost *:80>
  ServerName www.another-example.net
  DocumentRoot /var/www/another-example
</VirtualHost>
```

كل **ServerName** هنا موقع مختلف بيتقدّم من نفس الـ IP وبورت 80، والسيرفر بيختار على أساس **Host header**.

---

## استراتيجيات ووردليستس (عشان تمسك “المستخبي”)

- ابدأ بقوائم عامة (SecLists)، وبعدين خصّص:  
    `dev, stage, test, uat, admin, portal, intranet, legacy, old, backup, beta, qa, dashboard, api, auth, sso, vpn …`
    
- استنتج من الـ **OSINT**: أسماء منتجاتهم، مشاريعهم، فرقهم، تكنولوجياتهم.
    
- ما تنساش البورتات الغريبة: **:8080, :8081, :81, :8000, :8443** … إلخ.
    

---

## إشارات نجاح (Valid VHost Indicators)

- **Status = 200** بمحتوى “مختلف جوهريًا” عن الافتراضي.
    
- **301/302** بوجهة (Location) فيها الاسم اللي جرّبته.
    
- **401/403** لمحتوى محمي (أحيانًا علامة ممتازة).
    
- **Set-Cookie** أو **Server header** غريب أو **Title** مختلف.
    
- حجم/عدد كلمات الصفحة مختلف عن baseline.
    

---

## أخطاء شائعة وحلول

- **Wildcard/Default VHost بيرد 200 لكل حاجة:**  
    اعمل **baseline** وردود عشوائية، وفلتر النتائج اللي شبهه (طول/كلمات).
    
- **HTTPS وشهادة غلط:**  
    استخدم `-k` للتحقق، وبعدين ثبّت بالـ `curl --resolve` عشان تتأكد من الـ SNI.
    
- **Rate Limiting/حظر:**  
    قلّل `-t`، زوّد `--delay` لو الأداة بتدعم، وخلي الـ Timeout مناسب.
    
- **نتايج كتير/ضوضاء:**  
    فلترة على Status codes/Size، واحفظ كل حاجة في ملف (`-o`) للمراجعة.
    

---

## أمان وقانونية (مهم جدًا)

- كل اللي فوق **للاستخدام المصرّح به فقط** (Engagement رسمي/مختبر أمن/بيئتك).
    
- الفزّة على سيرفرات عامة بدون إذن ممكن تسبب **مشاكل قانونية** أو حظر.
    

---

# Layer 10
## **ما هي Certificate Transparency Logs؟**

- **CT Logs**
- عبارة عن سجلات عامة تُسجل كل شهادة SSL/TLS يتم إصدارها لأي موقع.
    
- تُدار هذه السجلات من قبل جهات مستقلة، وهي **append-only** (لا يمكن تعديلها أو حذف البيانات منها).
    
- أي **Certificate Authority (CA)** يجب أن يسجل أي شهادة جديدة تصدرها في هذه السجلات.
    

---

## **أهمية CT Logs**

1. **كشف الشهادات المزورة أو المُصدرة بالخطأ (Rogue Certificates)**
    
    - يمكن اكتشاف شهادات غير مصرح بها قبل استغلالها.
        
2. **زيادة شفافية الـ CAs**
    
    - أي خطأ أو تجاوز يظهر علنًا، ما يزيد المساءلة.
        
3. **تعزيز الثقة في Web PKI**
    
    - النظام الذي يدير الاتصال الآمن على الإنترنت يصبح أكثر قوة وموثوقية.
        

---

## **CT Logs في جمع المعلومات (Web Recon)**

- تمنحك **سجلًا حقيقيًا ودقيقًا لجميع الشهادات الصادرة لدومين معيّن**، بما في ذلك الـ **Subdomains**.
    
- **أفضل من الـ Brute Force أو Wordlists:**
    
    - لا تعتمد على التخمين.
        
    - تكشف Subdomains قديمة أو منتهية الشهادة (قد تكون أهداف ضعيفة).
        
    - تعطي صورة تاريخية كاملة للبنية التحتية للموقع.
        

---

## **طرق البحث في CT Logs**

### **1. crt.sh**

- **واجهة بسيطة مجانية بدون تسجيل.**
    
- تبحث باسم الدومين وتعرض كل الشهادات.
    
- تعرض:
    
    - تفاصيل الشهادة
        
    - أسماء النطاقات (SAN entries)
        

### **2. Censys**

- **أداة أقوى مع بحث متقدم وفلاتر كثيرة.**
    
- تحتاج تسجيل (Free tier متاح).
    
- تُستخدم لتحليل عميق وربط شهادات مختلفة مع مضيفين آخرين.
    

---

## **مثال عملي باستخدام crt.sh API**

البحث عن كل الـ Subdomains التي تحتوي كلمة "dev" في facebook.com:

`curl -s "https://crt.sh/?q=facebook.com&output=json" \ | jq -r '.[] | select(.name_value | contains("dev")) | .name_value' \ | sort -u`

**نتيجة مختصرة:**

- `*.dev.facebook.com`
    
- `dev.facebook.com`
    
- `secure.dev.facebook.com`
    
- `newdev.facebook.com`
    
- `facebook-amex-dev.facebook.com`
    
- ... إلخ
    

---

## **الخلاصة**

- **CT Logs = خريطة كاملة للـ Subdomains عبر الزمن**
    
- تساعدك في اكتشاف نطاقات فرعية غير مكشوفة أو قديمة بدون تخمين.
    
- أفضل استراتيجية: **دمج CT Logs مع طرق أخرى مثل Brute Force أو DNS Enumeration للحصول على نتائج شاملة.**
    

---
# Layer 10
## **Fingerprinting إيه؟**

Fingerprinting 
معناه "أخذ البصمة" لكن مش بصمة إيد ولا وش، دي بصمة رقمية للموقع أو للسيرفر أو للسوفتوير اللي شغال عليه. الهدف منها إنك تعرف كل التفاصيل التقنية عن الموقع، زي:

- نوع السيرفر (Apache, Nginx…)
    
- نسخة السيرفر (مثلاً Apache 2.4.41)
    
- نظام التشغيل (Ubuntu, Windows…)
    
- التكنولوجيا أو السوفتوير اللي الموقع شغال عليه (WordPress, Joomla…)
    
- أي حماية موجودة زي Web Application Firewall (WAF)
    

ليه ده مهم؟ لأن معرفة التفاصيل دي بتخلي الهجوم على الموقع مركز ودقيق:

- لو عارف نسخة البرنامج، ممكن تستخدم ثغرات معروفة في النسخة دي.
    
- لو عارف إعدادات غلط أو قديمة، تقدر تستغلها.
    
- لو فيه أكتر من هدف، Fingerprinting يخليك تحدد مين أكتر عرضة للاختراق.
    
- وبالدمج مع معلومات تانية، تقدر تعمل صورة كاملة للبنية التحتية للموقع (Infrastructure) وتعرف نقاط ضعفه.
    

---

## **طرق Fingerprinting**

في كذا طريقة نقدر نعرف بيها التفاصيل التقنية للموقع:

### **أ. Banner Grabbing**

دي ببساطة إنك تطلب من السيرفر يديك معلوماته، زي نوع السيرفر والنسخة.

مثال عملي:

`curl -I inlanefreight.com`

ده هيجيبلك HTTP Headers بس، مش الصفحة كلها. ممكن يظهرلك حاجة زي:

`Server: Apache/2.4.41 (Ubuntu)`
![[Pasted image 20250903101125.png]]

ده معناه إن السيرفر Apache ونسخته 2.4.41 وبيشتغل على Ubuntu.

لو الموقع بيعمل Redirect (يعني بيوديك على URL تاني) لازم تعمل Banner Grabbing على العنوان الجديد كمان:

`curl -I https://inlanefreight.com curl -I https://www.inlanefreight.com`

هتلاقي أحياناً تلميحات إن الموقع شغال على WordPress عن طريق Header زي:

`X-Redirect-By: WordPress`

---

### **ب. HTTP Headers Analysis**

- كل صفحة على الويب بيكون معاها Headers فيها معلومات مهمة.
    
- مثال:
    
    - `Server` → نوع السيرفر والنسخة.
        
    - `X-Powered-By` → ممكن يوريك لغة البرمجة أو الإطار المستخدم (PHP, ASP.NET…).
        

---

### **ج. Probing for Specific Responses**

- تبعت طلبات معينة وتشوف رد السيرفر.
    
- أحياناً Error Message أو Response معين يوريك النسخة أو نوع السيرفر.
    

---

### **د. Page Content Analysis**

- تشوف الصفحة نفسها، الكود وScripts اللي فيها.
    
- لو لقيت حاجة زي `wp-json` أو `wp-login.php` ده دليل قوي إن الموقع WordPress.
    

---

## **Tools بتساعد في Fingerprinting**

| Tool       | وظيفة                        | مميزاته                                 |
| ---------- | ---------------------------- | --------------------------------------- |
| Wappalyzer | Extension للبراوزر أو Online | يحدد CMS، Framework، أدوات Analytics…   |
| BuiltWith  | Online Web Profiler          | تقرير كامل عن تكنولوجيا الموقع          |
| WhatWeb    | CLI tool                     | قاعدة بيانات كبيرة لتحديد التقنيات      |
| Nmap       | Network Scanner              | Fingerprinting للسيرفرات وأنظمة التشغيل |
| Netcraft   | Web security service         | تقرير كامل عن تكنولوجيا واستضافة الموقع |
| wafw00f    | CLI tool لفحص WAF            | يحدد نوع الـ WAF لو موجود               |

---

## **Practical Example على inlanefreight.com**

### **أ. Banner Grabbing عملي**

`curl -I inlanefreight.com`

- بيكشف إن السيرفر Apache/2.4.41 على Ubuntu
    
- الموقع بيعمل Redirect، فلزم نعمل Curl على العنوان الجديد كمان:
    

`curl -I https://www.inlanefreight.com`

- ظهر header: `X-Redirect-By: WordPress` → دليل على WordPress
    

---

### **ب. WAF Detection باستخدام wafw00f**

- WAF → حماية إضافية للموقع تمنع هجمات معينة.
    
- نثبت wafw00f:
    

`pip3 install git+https://github.com/EnableSecurity/wafw00f`

- ونشغله على الموقع:
    

`wafw00f inlanefreight.com`

- النتيجة: الموقع محمي بـ Wordfence WAF من Defiant
    
- مهم نعرف ده لأنه ممكن يمنع بعض محاولات Fingerprinting أو الاختراق.
    
![[Pasted image 20250903101154.png]]

---

### **ج. Nikto Fingerprinting**

- Nikto أداة قوية لفحص السيرفر والثغرات. فيها Fingerprinting modules.
    
- تثبيت وتشغيل:
    

```
sudo apt update && sudo apt install -y perl git clone https://github.com/sullo/nikto cd nikto/program chmod +x ./nikto.pl nikto -h inlanefreight.com -Tuning b

```

- ده هيكشف:
    
    - IP الموقع (IPv4 و IPv6)
        
    - السيرفر (Apache/2.4.41 Ubuntu)
        
    - وجود WordPress (`/wp-login.php`)
        
    - ملفات ممكن تكشف معلومات (`license.txt`)
        
    - بعض الـ Headers غير آمنة أو ناقصة (مثل: `Strict-Transport-Security`)
        
    - مشاكل محتملة في التشفير (مثل Content-Encoding)
        
![[Pasted image 20250903101324.png]]

---

## **خلاصة Fingerprinting**

- Fingerprinting جزء أساسي من الـ Recon على الويب.
    
- بيدي معلومات دقيقة عن السيرفر، السوفتوير، CMS، الحماية.
    
- بيساعد في تحديد أهداف سهلة وفعالة للاختراق.
    
- أدوات مهمة: `curl`, `wafw00f`, `Nikto`, `Wappalyzer`, `WhatWeb`, `Nmap`.

------
# Layer 12
## 1) Crawling يعني إيه بالظبط؟

Crawling أو Spidering 
هو عملية آلية بتتصفّح صفحات الويب بشكل منهجي. الكراولر بيبدأ من **Seed URL** (رابط بداية)، يجيب الصفحة، يحلل الـ HTML ويطلع كل الروابط (links)، يحطهم في قائمة انتظار (queue) ويكمل عليهم واحد واحد. الهدف: يبني خريطة للموقع، يلاقي صفحات مخفية، ويجمّع بيانات (URLs, metadata, ملفات، تعليقات...).
![[Pasted image 20250903111409.png]]

---

## 2) ازاي الCrawler بيشتغل (ببساطة)

1. **Seed URL**: تبدأ برابط واحد أو شوية روابط.
    
2. **Fetch**: تجيب الصفحة (HTTP request).
    
3. **Parse**: تخرج كل الـ href, src, action في الفورمز، JSON endpoints، الخ.
    
4. **Normalize**: تنظف الـ URLs (تحذف utm params، تحط scheme، تتعامل مع relative links).
    
5. **Enqueue**: تضيف الروابط الجديدة للـ frontier لو مش متشافه قبل كده.
    
6. **Repeat**: تكمل لحد ما تخلص الـ queue أو توصل لحد عمق معين.
    

مهم: فيه **visited set** علشان تمنع الcrawler من الlooping أو زيارة نفس الصفحة ألف مرة.

---

## 3) استراتيجيات الزحف (Crawling strategies)

- **Breadth-First (BFS)**: 
- بتزور كل الروابط على صفحة البداية، بعدين كل الروابط بتاع الصفحات دي، وهكذا. مفيد لو عايز خريطة عرضية للموقع.
    ![[Pasted image 20250903111526.png]]
    
- **Depth-First (DFS)**: تمشي في مسار واحد لأبعد حد قبل ما ترجع لمسارات تانية. مفيد لو عايز توصل
- صفحات عميقة بسرعة.
![[Pasted image 20250903111541.png]]

- **Focused / Priority crawling**:
- تعطي أولوية لروابط بمواصفات معينة (مثلاً أي رابط فيه `/admin` أو JSON/REST endpoints).
    
- **Polite crawling**:
- تحترم قواعد الـ robots.txt، تحط delay بين الريكوستس، وتقلل الـ concurrency.
    

---

## 4) إيه اللي نقدر نجمّعه من عملية الـ Crawling؟

- **Links**: داخلية وخارجية — بنبني خريطة الموقع (site map).
    
- **Form endpoints**: action URLs، hidden inputs، token names.
    
- **API endpoints**: ملفات JSON، endpoints مخفية في JS.
    
- **Metadata**: عناوين الصفحات، meta description، keywords، author.
    
- **Comments**: تعليقات HTML أو تعليقات المستخدمين — ممكن تفضح بيانات حساسة.
    
- **Sitemaps & robots.txt**: بتوريك قنوات وأماكن مهمة.
    
- **Static assets**: js, css — ممكن تلاقي فيه أكواد فيها مفاتيح أو endpoints.
    
- **Sensitive files**: backup (.bak .old .sql), config (.env, web.config), logs, zip/tar, .git, .svn.
    
- **Directory listing**: لو Enabled، تلاقي ملفات كثيرة جاهزة للتحميل.
    

---

## 5) أدوات مفيدة وأوامر عملية (cheat-sheet)

### فحص بسيط وعزل الروابط

`# جلب الهدرز بس curl -I https://example.com  # جلب الصفحة واستخراج الروابط (مش كامل لكن مفيد) curl -s https://example.com | grep -Eo 'href="[^"#]+' | sed -E 's/href="//' | sort -u`

### mirror موقع بالكامل (offline copy)

`wget --mirror --convert-links --adjust-extension --page-requisites --no-parent https://example.com`

### فحص كلمات/ديركتوريز (bruteforce directories)

`gobuster dir -u https://example.com -w /usr/share/wordlists/dirb/common.txt -x php,html,txt,bak,old -t 50 -o gobuster.txt`

### جلب URLs من Wayback / archives / crawling history

`echo "example.com" | gau | sort -u > urls.txt   # gau = getallurls`

### قراءة robots.txt و sitemap

`curl -s https://example.com/robots.txt curl -s https://example.com/sitemap.xml | grep -oP '(?<=<loc>).*?(?=</loc>)'`

### استخراج HTML comments

`curl -s https://example.com | grep -oP '(?s)<!--.*?-->'`

---

## 6) مثال عملي: Scrapy spider بسيط (يجمع URLs وعناوين الصفحات)

```
```py: simplespider.py
import scrapy  class SimpleSpider(scrapy.Spider):     name = 'simplespider'     allowed_domains = ['example.com']     start_urls = ['https://example.com/']     custom_settings = {         'DEPTH_LIMIT': 3,         'DOWNLOAD_DELAY': 0.5,   # polite crawling         'CONCURRENT_REQUESTS': 4     }      def parse(self, response):         yield {             'url': response.url,             'title': response.xpath('//title/text()').get() or ''         }         for href in response.css('a::attr(href)').getall():             url = response.urljoin(href)             if self.allowed_domains[0] in url:                 yield response.follow(url, self.parse)`

تشغله بـ: `scrapy runspider simplespider.py -o results.json`
```


---

## 8) التعامل مع محتوى JS (Single Page Apps)

الـ crawlers التقليديين مش هيشوفوا اللي الـ JS يولده بعد الـ DOM render. الحلول:

- **Headless browser**: 
- Puppeteer / Playwright / Selenium — بيشغّل الصفحة وبيجيب الـ DOM بعد تنفيذ الـ JS.
    
- **Burp/ZAP spider with DOM rendering**: 
- Burp Pro عنده Spider/Scanner بيقدر يجلب محتوى JS-rendered.
    
- مثال Playwright (فكرة عامة): تشغّل page.goto(url) وبعدين page.content() وتعمل parsing زي ما عملنا.
    

---

## 9) Normalization و deduplication

- لازم تنفّذ normalize للـ URLs (lowercase host, إزالة `#fragment`, إزالة tracking params).
    
- تعامل مع trailing slash `/path` و`/path/`.
    
- صفّي الـ query params أو احتفظ باللي مهم منها (مثلاً id, page).
    
- مهم علشان تخفف الضوضاء وتمنع زيارة صفحات مكررة.
    

---

## 10) البحث على ملفات حساسة — أمثلة (extensions & paths)

**Extensions**: bak, old, sql, tar.gz, zip, rar, env, config, log, backup, gz, tgz  
**Paths**: /backup/, /db/, /config/, /uploads/, /admin/, /.git/, /.env, /wp-content/uploads/  
**أوامر Gobuster مثال:**

`gobuster dir -u https://example.com -w /usr/share/wordlists/dirb/common.txt -x php,html,txt,bak,sql,env -t 40 -o found.txt`

**فحص .git**:

`curl -s https://example.com/.git/config`

---

## 11) Context مهم ليه؟ (مثال عملي)

لو لقيت comment: "using file server on /files/", مع إنه وحده مش خطير، لكن لو لقيت تاني إن `/files/` بيسمح directory listing — يبقى ده كارثة: ممكن تلاقي backups وملفات داخلية. الربط بين الـ findings هو اللي بيحول معلومة بسيطة لمخترق.

---

## 12) أخلاقيات وقانون + أمنية

- **لو انت بتعمل Recon أو Scanning** على موقع مش بتاعك: لازم إذن صريح (Scope/Authorization). غير كده ممكن تدخل تحت بند مخالفة وقانون.
    
- **احترم robots.txt** لو بتحترم الـ web crawl etiquette. (لكن robots.txt ممكن يحتوي على دلائل لصفحات حساسة — لازم تتعامل معها أخلاقياً وتبلّغ المالك بدل ما تنشر أو تستغل).
    
- لو الموقع محمي بـ WAF/IDS، أي محاولة لتجاوزها يمكن تُعتبر هجوم — خلي بالك.
    

---

## 13) نصائح عملية وخلاصة (checklist)

1. ابدأ بـ: `robots.txt` و `sitemap.xml` و `curl -I` لفحص الهيدرز.
    
2. استخرج كل الروابط (simple curl+grep أو scrapy).
    
3. نضّف الـ URLs وعمّمها (normalize).
    
4. اعمل brute-force للـ directories (gobuster) على نطاق محدود وباحترام.
    
5. استخدم Wayback / gau / waybackurls للـ URLs القديمة.
    
6. لو فيه JS محتوى مهم، استخدم Playwright/Selenium أو Burp/ZAP.
    
7. دور على ملفات backup، config، .env، .git، logs.
    
8. دوّن كل النتائج وركّب الصورة مع نتائج Fingerprinting (مثلاً: WordPress + Apache قد يعني ثغرات WP أو plugins).
    
9. احرص على Rate-limit و User-Agent محترم، واستخدم proxies بس بحذر.


-------
# Layer 13

---

### **إيه هو robots.txt؟**

تخيل نفسك في حفلة كبيرة في فيلا فخمة. أنت حر تتفرج وتلف، بس فيه أوض عليها لافتة مكتوب عليها "خاص" ومش المفروض تدخلها.  
**ده بالظبط دور robots.txt** — فايل بسيط بيتحط في جذر الموقع ([www.example.com/robots.txt](http://www.example.com/robots.txt)) بيقول للـ bots (زي Googlebot أو Bingbot): "دخل هنا، بس ماتدخلش هنا".

---

### **الفايل ده بيشتغل إزاي؟**

- الفايل عبارة عن **سطرين أساسيين:**
    
    1. **User-agent** → بيحدد اسم البوت اللي القواعد دي ليه (ممكن تحط * يعني كل البوتات).
        
    2. **Directives** → القواعد نفسها، زي:
        
        - **Disallow**: ماتدخلش هنا
            
        - **Allow**: ينفع تدخل هنا
            
        - **Crawl-delay**: كل زيارة وسيب ثانية/وقت معين
            
        - **Sitemap**: مكان خريطة الموقع
            

---

### **مثال عملي:**

```txt
User-agent: *
Disallow: /admin/
Disallow: /private/
Allow: /public/

User-agent: Googlebot
Crawl-delay: 10

Sitemap: https://www.example.com/sitemap.xml
```

- أي بوت **مش مسموح** يدخل على `/admin/` أو `/private/`.
    
- أي بوت **مسموح** يدخل على `/public/`.
    
- بوت جوجل بس، **ينتظر 10 ثواني** بين كل زيارة.
    
- فيه **خريطة موقع** علشان البوتات تعرف تفهرس بسهولة.
    

---

### **طب ليه الملف ده مهم؟**

1. **بيحمي السيرفر** من ضغط البوتات الكتير.
    
2. **بيخلي الداتا الحساسة بعيد** عن جوجل (على الأقل للبوتات المحترمة).
    
3. **بيحافظ على الخصوصية** وممكن كمان يبقى جزء من اتفاق قانوني.
    

---

### **طب في الـ Recon (استكشاف المواقع)؟**

- الملف ده **كنز معلومات**:
    
    - ممكن يكشف **أماكن حساسة** زي `/admin/` أو `/backup/` اللي المالك مش عايز حد يشوفها.
        
    - ممكن يوريك **خريطة أولية** للموقع.
        
    - أحيانًا أصحاب المواقع بيحطوا **فخاخ (Honeypots)** يجذبوا بيها الهاكرز علشان يعرفوا مين بيخالف القواعد.
        

**يعني حتى لو البوتات المحترمة مش هتدخل… إنت كمختبر أمني ممكن تاخد فكرة عن نقاط مهمة في الموقع.**

---

# Layer 14


## مفهوم عام — إيه هو `.well-known`؟

`.well-known` هو مسار موحَّد على أي دومين بيبقى تحت الجذر:  
`https://example.com/.well-known/`  
الفكرة إنه مكان مركزي تحط فيه ملفات تعريفية/إعدادات/معلومات للخدمات (meta/config) علشان البراوزرز، التطبيقات، أو بروتوكولات تانية تعرف تلاقيها بسهولة. المعيار متحدد في RFC (مثلاً RFC 8615) وفيه registry عند IANA للـ suffixes المعتمدة.

---

## أمثلة مهمة من `.well-known` وليه كل واحدة تهمّنا

- `/ .well-known/security.txt`
- — ملف تواصل للأمن السيبراني (RFC 9116). فيه إيميل تواصل، مفتاح تشفير، سياسة الإفصاح عن الثغرات. كنز لمُخبرين الأمن.
    
- `/.well-known/openid-configuration` — OpenID Connect Discovery:
- بيديك JSON فيه كل نقاط النهاية (authorization, token, jwks_uri, userinfo...) — مهم للحصول على نقاط الـ OAuth/OpenID.
    
- `/.well-known/jwks.json` أو أي `jwks_uri` — مجموعة المفاتيح العامة (JWKS) اللي بتستعمل لتوقيع JWTs. بتوريك الـ key ids، الخوارزميات، نوع المفتاح.
    
- `/.well-known/mta-sts.txt` + TXT سجل DNS `_mta-sts` — سياسة MTA-STS للبريد (SMTP strict TLS). مهم لو بتراجع أمان الإيميلات.
    
- `/.well-known/assetlinks.json` — للتحقق من ملكية التطبيقات (Digital Asset Links) للأندرويد. بيحتوي على package_name وsha256_cert_fingerprints.
    
- `/.well-known/change-password` — رابط موحّد لصفحة تغيير الباسورد.
    
- `/.well-known/acme-challenge/` — تحديات إنشاء شهادات (Let's Encrypt).
    
- غيرهم: `webfinger`, `host-meta`, `nodeinfo`, `matrix` endpoints، الخ.
    

---

## إزاي بنستخدمهم في Web Recon — خطوة بخطوة عملية

1. **ابدأ دايمًا بجلب الملفات المعروفة**:
    
    ```bash
    curl -sS https://example.com/.well-known/security.txt
    curl -sS https://example.com/.well-known/openid-configuration | jq .
    ```
    
    لو ما عندكش `jq`:  
    `curl -sS URL | python -m json.tool`
    
2. **اقرأ الـ openid-configuration** علشان تطلع:
    
    - `issuer`, `authorization_endpoint`, `token_endpoint`, `userinfo_endpoint`, `jwks_uri`  
        بعدين افتح `jwks_uri` عشان تشوف المفاتيح العامة.
    ![[Pasted image 20250903113004.png]]
        
3. **افحص محتوى jwks**:
    
    - بتهتم بـ `kty`, `kid`, `use`, `alg`, `n` و `e` (لـ RSA).
        
    - لاحظ إن المفاتيح عامة بالطبيعة — لكن شوف الخوارزميات المدعومة (مثلاً وجود `HS256` قد يلفت الانتباه لو في مشكلة في التنفيذ) أو `e` غير قياسي (مثلاً 3 بدل 65537) — ده مؤشر لمراجعة أمني.
        
4. **اقرأ security.txt**:
    
    - بتلاقي `Contact`, `Encryption` (مفتاح PGP), `Acknowledgments`, `Policy`, `Hiring`.
        
    - ممكن تلاقي إيميلات، صفحات سياسة الإفصاح vulnerability disclosure، أو PGP key لتحويل تقارير مؤمنة.
        
5. **افحص mta-sts**:
    
    - افتح `https://example.com/.well-known/mta-sts.txt` وشوف `version`, `mode` (test/enforce), `mx:`، `max_age`
        
    - كمان شوف الـ DNS TXT `_mta-sts.example.com` (بيحتوي id/version).
        
6. **assetlinks.json**:
    
    - لو موجود، هتلاقي `relation` و `target` مع `package_name` و `sha256_cert_fingerprints` — تفيد لو بتدور على تطبيق مرتبط بالدومين.
        
7. **فكر دايمًا بالـ context**:
    
    - كل ملف لوحده مش دايمًا مهم، لكن لو _اتّفق_ مع حاجات تانية (مثلاً openid endpoint موجود و jwks فيها مفاتيح قديمة، أو security.txt فيه contact بس مفيش سياسة) — ممكن يبقى مؤشر لخطوة قادمة في الاختبار الأمني.
        

---

## أوامر عملية مفيدة (cheat-sheet)

```bash
# جلب security.txt
curl -sS https://example.com/.well-known/security.txt

# جلب openid-configuration وتهيئته بجيك
curl -sS https://example.com/.well-known/openid-configuration | jq .

# لو عندك JWKS URI من الـ openid config
curl -sS "https://example.com/oauth2/jwks" | jq .

# mta-sts
curl -sS https://example.com/.well-known/mta-sts.txt
# + DNS TXT
dig +short TXT _mta-sts.example.com

# assetlinks
curl -sS https://example.com/.well-known/assetlinks.json | jq .

# acme-challenge listing (لو مسموح)
curl -sS https://example.com/.well-known/acme-challenge/
```

---

## سكربت بايثون صغير يعمل enumeration لـ مجموعة well-known شائعة

```python
# file: well_known_enum.py
import requests
from urllib.parse import urljoin

WELL_KNOWN = [
    "security.txt",
    "openid-configuration",
    "jwks.json",            # sometimes at /.well-known/jwks.json
    "mta-sts.txt",
    "assetlinks.json",
    "change-password",
    "acme-challenge/",
    "webfinger",
    "host-meta"
]

def fetch(base):
    for w in WELL_KNOWN:
        url = urljoin(base, f".well-known/{w}")
        try:
            r = requests.get(url, timeout=8, allow_redirects=True)
            print(f"{r.status_code}\t{url}\t{r.headers.get('content-type')}")
            if r.headers.get('content-type','').startswith('application/json'):
                print(r.text[:1000])  # print a small preview
        except Exception as e:
            print("ERR", url, e)

if __name__ == "__main__":
    fetch("https://example.com/")
```

- النتيجة: حالة كل URI (200/404/403) ومعاها نوع المحتوى preview. مفيد للأتمتة السريعة.
    

---

## إيه اللي تدور عليه — دلائل ومؤشرات مهمة

- **authorization/token endpoints** → مهم لفهم مسار المصادقة.
    
- **jwks_uri** → فتح باب لفهم آلية التوقيع (alg). لو الخوارزمية ضعيفة أو مذكورة `none` في إعدادات النظام ده مؤشر لمشكلة (مش هتلاقي `none` في jwks لكن ممكن يذكر في supported algs).
    
- **security.txt** → لو فيه contact email مع مفتاح PGP يبقى ممتاز للتبليغ؛ لو فيه عنوان ftp أو مسارات قديمة يبقى ممكن تلاقي data.
    
- **mta-sts mode: enforce** → دليل إن صاحب الدومين مهتم بأمان الإيميلات.
    
- **assetlinks.json** → لو فيه package_name يشير لتطبيق رسمي — تقدر تراجع الـ app إذا كان متاح وتشوف تكامل الدومين مع الأندرويد.
    
- **acme-challenge tokens** → عادة مؤقتة، لكن لو لاقيتها ممكن تكون مفيدة لمعرفة آليات إصدار الشهادات.
    

---

## مخاطر/حاجات لازم تاخد بالك منها (ولأصحاب المواقع: best practices)

**لمختبري الأمان / الباحثين:**

- عدم استغلال المعلومات بطريقة غير مرخّصة — لو بتشتغل على موقع مش بتاعك، لازم authorization أو يكون في نطاق Bug Bounty.
    
- `.well-known` ممكن يكون فخ (honeypot). لو لقيت رد غريب أو ردود 403/429 مستمرة، خد بالك.
    
- احترم الـ rate limits و Crawl-delay لو مذكور.
    

**لملاك المواقع / مطورين:**

- **ما تحطش معلومات حساسة** في `.well-known` أو تترك ملفات config داحلها.
    
- لو بتحط `security.txt` خليها واضحة: contact + PGP public key + سياسة افصاح.
    
- رتب الـ JWKS وتأكد من التدوير (key rotation) وصلاحيات المفاتيح.
    
- `mta-sts` و DNS records لازم تكون صحيحة ومُختبرة.
    
- راقب الطلبات على `.well-known` — لو في محاولات ماسخة أو probing كتير، فكر تعمل rate-limit أو حماية.
    

---

## أمثلة واقعية (نصائح تفسير النتايج بسرعة)

- شفت `/.well-known/openid-configuration` و`token_endpoint` موجود؟ → ده دليل قوي إن في OAuth flow ممكن تختبر عليه (داخل نطاق اختبار مرخّص).
    
- `security.txt` فيه `Contact: mailto:sec@example.com` + PGP link → استخدمها للتبليغ الرسمي عن مشكلة، واحتفظ بسجل تواصلك.
    
- `assetlinks.json` فيه `sha256_cert_fingerprints` → تقدر تأكد إن التطبيق الأصلي متوافق مع الدومين.
    
- `/.well-known/acme-challenge/` فيه ملفات قديمة أو معرضة للعرض → ممكن تلاقي تذكار عن شهادات سابقة لكن عادي معظمها مؤقت.
    

---

# Layer 15

---

### **Creepy Crawlies – أدوات الـ Web Crawling**

الـ Web Crawling زي إنك عندك جيش من النمل الصغير بيتحرك في كل زاوية في موقع الويب علشان يجمعلك معلومات. بس بدل ما تشتغل يدوي وتدوخ، فيه أدوات جاهزة بتعمل الشغل ده بسرعة وكفاءة.

---

### **أشهر أدوات الـ Crawling:**

1. **Burp Suite Spider**
    
    - جزء من Burp Suite المشهور في اختبار التطبيقات.
        
    - بيعمل خريطة للموقع ويكشف الصفحات المخفية والنقط الضعيفة.
        
2. **OWASP ZAP Spider**
    
    - أداة مجانية ومفتوحة المصدر.
        
    - تقدر تشغلها يدوي أو أوتوماتيك.
        
    - بتعمل Crawl وتكشف الـ Vulnerabilities.
        
3. **Scrapy (Python)**
    
    - فريمورك مرن وقوي بلغة بايثون.
        
    - تقدر تبني بيه سبايدر مخصص يجمع داتا منظمة.
        
    - مثالي لو عايز تتحكم في كل تفصيلة.
        
4. **Apache Nutch (Java)**
    
    - سبايدر ضخم ومصمم للـ Large Scale Crawling.
        
    - محتاج خبرة تقنية أعلى شوية.
        
    - ممتاز لو عايز تعمل Crawl على نطاق كبير جدًا.
        

---

### **نصيحة مهمة:**

مهما استخدمت أداة لازم **تلتزم بالأخلاقيات**:

- خد إذن قبل ما تعمل Crawl على موقع مش بتاعك.
    
- متضغطش السيرفر بطلبات كتير جدًا.
    
- اتجنب الـ Scans اللي ممكن تسبب مشاكل.
    

---

### **ليه هنستخدم Scrapy هنا؟**

- لأنه مرن وسهل التخصيص.
    
- هنشغل **سبايدر جاهز اسمه ReconSpider** على موقع تجريبي اسمه inlanefreight.com.
    
- السبيدر هيجمع داتا مهمة زي:
    
    - إيميلات موجودة في الصفحات
        
    - روابط وصور وملفات خارجية
        
    - أكواد جافاسكريبت وتعليقات HTML
        

---

### **الخطوات العملية:**

1. **تثبيت Scrapy:**
    

```bash
pip3 install scrapy
```

2. **تحميل ReconSpider:**
    

```bash
wget -O ReconSpider.zip https://academy.hackthebox.com/storage/modules/144/ReconSpider.v1.2.zip
unzip ReconSpider.zip
```

3. **تشغيله:**
    

```bash
python3 ReconSpider.py http://inlanefreight.com
```

---

### **إيه اللي هيطلع؟**

- كل الداتا هتتحفظ في فايل اسمه **results.json**.
    
- الملف بيكون بالشكل ده مثلًا:
    
![[Pasted image 20250903114414.png]]

- **كل Key بيمثل نوع معين من الداتا:**
    
    - `emails` → الإيميلات اللي لقاها
        
    - `links` → الروابط اللي بالموقع
        
    - `external_files` → ملفات خارجية زي PDF
        
    - `js_files` → ملفات الجافاسكريبت
        
    - `form_fields` → حقول إدخال المستخدم (لو موجودة)
        
    - `images` → صور الموقع
        
    - `videos / audio` → وسائط لو موجودة
        
    - `comments` → التعليقات اللي في الـ HTML
        

---

### **الهدف من النتائج دي؟**

- تفهم **هيكلة الموقع** بالكامل.
    
- تحدد **صفحات حساسة** أو **ملفات مهمة**.
    
- تعرف **نقط ممكن تبدأ منها اختبار الاختراق**.
    

---

# Layer 16
## **Search Engine Discovery – استكشاف المواقع باستخدام محركات البحث**

محركات البحث زي Google و Bing مش بس بتجاوبك لما تدور على "أحلى مطاعم في القاهرة" – دي كمان **كنز معلومات ضخم** ينفعك جدًا في مرحلة الـ Recon أو جمع المعلومات (OSINT).

---

### **ليه Search Engine Discovery مهم؟**

1. **مفتوح المصدر (Open Source)** → كل الداتا دي علنية وموجودة للعامة.
    
2. **كمية معلومات رهيبة** → محركات البحث بتفهرس ملايين الصفحات.
    
3. **سهولة الاستخدام** → مش محتاج تكون خبير علشان تستخدمها.
    
4. **تكلفة صفر** → مجاني تمامًا.
    

---

### **بيستخدم في إيه؟**

- **Security Assessment:** تكشف بيانات حساسة أو صفحات تسجيل دخول أو ملفات مهمة.
    
- **Competitive Intelligence:** تعرف معلومات عن المنافسين.
    
- **Investigative Journalism:** تكشف روابط أو فضائح أو تعاملات مالية.
    
- **Threat Intelligence:** تتبع المهاجمين أو تكتشف تهديدات جديدة.
    

> **مهم تعرف:** مش كل حاجة متفهرسة في Google، وفي داتا بتكون محمية أو متعمدة إنها تختفي (Deep Web / Dark Web).

---

## **Search Operators – الأكواد السرية لجوجل**

الموضوع هنا شبه الـ Cheat Codes اللي بتستخدمها في الألعاب. الأوبريتورز دي بتخليك تدور بدقة وتوصل للي انت عايزه بالظبط:

|**Operator**|**بيعمل إيه؟**|**مثال**|**النتيجة**|
|---|---|---|---|
|`site:`|البحث داخل موقع محدد|`site:example.com`|كل الصفحات العامة في example.com|
|`inurl:`|كلمة موجودة في اللينك|`inurl:login`|صفحات تسجيل الدخول|
|`filetype:` أو `ext:`|تبحث عن نوع ملف معين|`filetype:pdf`|ملفات PDF|
|`intitle:`|كلمة في عنوان الصفحة|`intitle:"confidential report"`|مستندات حساسة|
|`intext:`|كلمة داخل النص|`intext:"password reset"`|صفحات بتتكلم عن Reset Password|
|`cache:`|تعرض نسخة جوجل القديمة|`cache:example.com`|تشوف المحتوى قبل التعديل|
|`link:`|مواقع بتعمل لينك للموقع|`link:example.com`|مين بيربط بموقعك|
|`related:`|مواقع مشابهة|`related:example.com`|مواقع قريبة في المحتوى|
|`info:`|معلومات عن الموقع|`info:example.com`|عنوان ووصف الموقع|
|`define:`|تعريف كلمة|`define:phishing`|تعريف المصطلح|
|`allintext:`|كل الكلمات في النص|`allintext:admin password reset`|صفحات فيها كل الكلمات معًا|
|`allinurl:`|كل الكلمات في اللينك|`allinurl:admin panel`|لينكات فيها الكلمتين|
|`allintitle:`|كل الكلمات في العنوان|`allintitle:confidential report 2023`|صفحات عنوانها فيه كل الكلمات|
|`" "`|جملة مطابقة بالظبط|`"information security policy"`|نتائج بنفس الجملة|
|`-`|استبعاد كلمة|`site:news.com -sports`|صفحات بدون رياضة|
|`AND` / `OR`|دمج شروط|`site:example.com AND inurl:admin`|صفحات Admin بس|
|`..`|نطاق أرقام|`"price" 100..500`|منتجات بين 100 و500|

---

## **Google Dorking – البحث المتقدم (Google Hacking)**

دي طريقة بتستخدم الأوبريتورز دي بشكل احترافي علشان تلاقي:

- صفحات تسجيل دخول:
    
    `site:example.com inurl:login site:example.com (inurl:login OR inurl:admin)`
    
- ملفات حساسة:
    
    `site:example.com filetype:pdf site:example.com (filetype:xls OR filetype:docx)`
    
- ملفات إعدادات:
    
    `site:example.com inurl:config.php site:example.com (ext:conf OR ext:cnf)`
    
- نسخ قواعد بيانات Backup:
    
    `site:example.com inurl:backup site:example.com filetype:sql`
    

---

### **الخلاصة:**

- **Search Engine Discovery = استخدام جوجل كأداة Recon قوية.**
    
- **Google Dorking = استغلال البحث المتقدم لاكتشاف حاجات حساسة بسرعة.**
    
- **الأوبريتورز = أدواتك السرية للوصول لنتايج دقيقة جدًا.**

------
# Layer 17
## **Web Archives – أرشيف الإنترنت**

الإنترنت بيتغير بسرعة رهيبة، مواقع بتتحدث كل يوم ومواقع بتختفي فجأة. هنا بيجي دور **Wayback Machine** – أداة بتخليك ترجع بالزمن وتشوف شكل المواقع زمان ومحتواها القديم.

---

### **إيه هو الـ Wayback Machine؟**

- تابع لـ **Internet Archive** (مؤسسة غير ربحية).
    
- بدأ من **سنة 1996** وبيخزن نسخ من المواقع بانتظام.
    
- بيعرض لك **نسخ قديمة (Snapshots)** لأي موقع تقريبًا، بكل تفاصيله: تصميم – صور – نصوص – ملفات.
    

---

### **إزاي بيشتغل؟**

العملية بتتم في 3 خطوات أساسية:

1. **Crawling (التجميع):**
    
    - روبوتات (Bots) بتزور المواقع وتجمع كل الصفحات واللينكات.
        
    - مش بس بتفهرس زي Google، دي كمان **بتحفظ نسخة كاملة** من الصفحة.
        
2. **Archiving (الأرشفة):**
    
    - كل نسخة محفوظة بتاريخ ووقت محدد.
        
    - ممكن يتعمل Snapshot يوميًا أو أسبوعيًا أو حتى كل كام شهر حسب شهرة الموقع أو سرعة تحديثه.
        
3. **Accessing (الوصول):**
    
    - تقدر تدخل على الموقع archive.org/web
        
    - تكتب الـ URL وتختار التاريخ وتشوف الموقع كان عامل إزاي وقتها.
        
    - كمان ممكن تبحث داخل المحتوى المؤرشف أو تنزل نسخة كاملة للتحليل.
        

---

### **ملاحظات مهمة**

- مش كل المواقع محفوظة بالكامل.
    
- فيه مواقع أصحابها بيطلبوا عدم الأرشفة (Robots.txt أو طلبات حذف).
    
- الأرشيف بيركز على المواقع المهمة ثقافيًا أو تاريخيًا أو بحثيًا.
    

---

### **ليه الأداة دي مهمة في الـ Recon؟**

1. **كشف ملفات أو صفحات مخفية:**
    
    - ممكن تلاقي Subdomains أو صفحات تسجيل قديمة أو ملفات حساسة مش موجودة دلوقتي.
        
2. **متابعة التغييرات:**
    
    - تشوف الموقع اتغير إزاي – المحتوى – التصميم – الـ Tech Stack.
        
3. **جمع معلومات (OSINT):**
    
    - تعرف استراتيجيات قديمة – موظفين ظهروا في الماضي – حملات تسويق سابقة.
        
4. **Recon بدون ما حد يحس:**
    
    - مش بتلمس السيرفر الحالي → بالتالي مفيش أي Log يبان فيه نشاطك.
        

---

### **مثال عملي (HackTheBox)**

- أول نسخة محفوظة لـ HackTheBox كانت بتاريخ **2017-06-10 الساعة 04:23:01**.
    
- لو دخلت Wayback Machine وكتبت hackthebox.com → هتلاقي الـ Snapshot ده وتقدر تشوف شكل الموقع أول ما بدأ.
    

---

### **الخلاصة:**

- **Wayback Machine = آلة زمن للمواقع.**
    
- **أداة مثالية للـ Recon السلبي (Passive Recon).**
    
- **تكشف حاجات مش موجودة دلوقتي وممكن تساعدك في اختبارات الاختراق أو جمع المعلومات.**
----
# Layer 18

## **Automating Recon – الأتمتة في جمع المعلومات**

الـ Recon اليدوي (Manual) قوي ومهم، بس بياخد وقت طويل وممكن يحصل فيه أخطاء بشرية.  
الحل؟ **نخلي الأدوات تشتغل لوحدها بدل ما نعمل كل حاجة بإيدنا.**

---

### **ليه نعمل Recon أوتوماتيك؟**

1. **السرعة (Efficiency):**  
    الأدوات بتعمل نفس المهمة أسرع بعشرات المرات.
    
2. **التوسّع (Scalability):**  
    بدل ما تجمع معلومات عن موقع واحد، تقدر تفحص **عشرات أو مئات المواقع في نفس الوقت**.
    
3. **الثبات (Consistency):**  
    الأدوات بتمشي على خطوات ثابتة → مفيش غلطات بشرية.
    
4. **التغطية الشاملة (Comprehensive Coverage):**  
    الأدوات تقدر تعمل حاجات كتير أوتوماتيك: DNS Enum – Subdomain Discovery – Port Scan – Web Crawling – الخ.
    
5. **التكامل (Integration):**  
    تقدر تربط أدوات الـ Recon مع أدوات فحص الثغرات أو حتى الاستغلال (Exploitation).
    

---

## **أشهر أدوات وأُطر (Frameworks) للـ Recon**

- **FinalRecon:** أداة Python Modular شاملة.
    
- **Recon-ng:** فريمورك كامل للـ Recon، تقدر تستخدمه زي Metasploit بس لجمع المعلومات.
    
- **theHarvester:** بيركز على الإيميلات – الساب دومينات – الموظفين – الـ Banners.
    
- **SpiderFoot:** أداة OSINT Automation قوية، بتجمع كل حاجة عن الهدف من مصادر مختلفة.
    
- **OSINT Framework:** مش أداة، لكنه دليل شامل لكل أدوات الـ OSINT المتاحة.
    

---

## **تفاصيل FinalRecon (All-in-One Tool)**

### **إيه اللي بتعمله الأداة؟**

- **Header Info:** تعرف السيرفر – الـ CMS – الـ Cookies – الـ Security Headers.
    
- **Whois:** معلومات تسجيل الدومين (مين صاحبه – تاريخ الإنشاء – الـ Registrar).
    
- **SSL Info:** تفحص شهادة SSL – هل شغالة – صادرة منين – فيها مشاكل ولا لأ.
    
- **Crawler:**
    
    - بيجيب كل اللينكات الداخلية والخارجية.
        
    - بيجمع ملفات HTML, CSS, JS → ممكن تكشف Secrets.
        
    - بيقرأ robots.txt و sitemap.xml → تعرف إيه اللي مخفي.
        
    - بيرجع بيانات قديمة من **Wayback Machine**.
        
- **DNS Enumeration:** بيشوف أكتر من 40 نوع من الـ DNS Records.
    
- **Subdomain Enumeration:** بيستخدم مصادر زي crt.sh – VirusTotal – Shodan – ThreatMiner.
    
- **Directory Enumeration:** بكلمة سر Custom Wordlist أو جاهزة → يكشف فولدرات مخفية.
    
- **Fast Port Scan:** يفحص البورتات المهمة بسرعة.
    
- **Full Scan:** يعمل كل حاجة مرة واحدة.
    

---

### **تنزيل وتشغيل FinalRecon**

```bash
git clone https://github.com/thewhiteh4t/FinalRecon.git
cd FinalRecon
pip3 install -r requirements.txt
chmod +x ./finalrecon.py
./finalrecon.py --help
```

### **أمثلة أوامر مهمة**

- فحص Headers و Whois مع URL محدد:
    

```bash
./finalrecon.py --headers --whois --url http://inlanefreight.com
```

- فحص شامل (Full Recon):
    

```bash
./finalrecon.py --full --url http://example.com
```

### **خيارات إضافية مهمة**

- `-w` → مسار Wordlist.
    
- `-e` → الامتدادات اللي تدور عليها (txt, php, xml...).
    
- `-o` → نوع ملف التصدير (txt).
    
- `-k` → تضيف API Key زي Shodan.
    
- `-pt` → عدد الـ Threads لمسح البورتات.
    
- `-dt` → عدد الـ Threads لمسح الديركتوريز.
    

---

## **الخلاصة**

- **Manual Recon → دقة أعلى بس وقت أطول.**
    
- **Automated Recon → سرعة وكفاءة وتغطية أوسع.**
    
- **FinalRecon = كل حاجة في أداة واحدة.**
    
- **أفضل أسلوب → تدمج Manual + Automated عشان تطلع أفضل نتيجة.**
    

---


