**Penetration Testing Overview**

- The process consists of: **Pre-Engagement → Information Gathering → Vulnerability Assessment → Exploitation → Post-Exploitation → Lateral Movement → Proof-of-Concept → Post-Engagement.**
    
- **Information gathering** is the cornerstone of penetration testing and recurs throughout all stages. It involves collecting details about the company, employees, infrastructure, and services to guide further testing.
    

---

**Main Categories of Information Gathering**

1. **Open-Source Intelligence (OSINT)**
    
    - Uses publicly available sources (social media, job postings, repositories) to find sensitive information (passwords, keys, tokens).
        
    - Exposes misconfigurations and critical security gaps that administrators must review immediately.
        
2. **Infrastructure Enumeration**
    
    - Maps internet- and intranet-facing components (DNS, mail/web servers, cloud instances).
        
    - Identifies security measures like firewalls to plan ==evasive testing==.
        
    - Internal scans may reveal targets for password spraying or overlooked services.
        
3. **Service Enumeration**
    
    - Discovers running services, their purpose, and version history to spot vulnerabilities.
        
    - Outdated or unpatched services are common due to administrators fearing operational disruption.
        
4. **Host Enumeration**
    
    - Examines each host’s OS, services, and configuration.
        
    - Finds internal services or misconfigurations not visible externally.
        
    - Determines each host’s role and communication with other components.
        
    - After exploitation, this stage overlaps with privilege escalation by analyzing sensitive files, scripts, and local services.
        

---

**Pillaging**

- Occurs **after exploiting a host** to collect sensitive information (employee data, configs, keys).
    
- Not a separate stage—integrated into **information gathering** and **privilege escalation**.
    
- Covered across multiple modules such as **Nmap enumeration, AD attacks, Linux/Windows privilege escalation, and attacking common services.**
    

---

**Key Takeaways**

- Information gathering drives all subsequent penetration testing steps.
    
- Every target must be assessed using **OSINT, infrastructure, service, and host enumeration.**
    
- Sensitive information is often unintentionally exposed by employees or misconfigurations.
    
- Internal systems are frequently assumed to be secure but may contain critical vulnerabilities.
    
- Pillaging shows the real impact of attacks and helps escalate privileges or move laterally.![[0-PT-Process-VA.webp]]



---

### **Vulnerability Assessment Phase Overview**

- Follows **Information Gathering** in the penetration testing process:  
    _Pre-Engagement → Information Gathering → Vulnerability Assessment → Exploitation → Post-Exploitation → Lateral Movement → Proof-of-Concept → Post-Engagement_
    
- Focuses on **analyzing collected information** to identify vulnerabilities, assess risks, and plan potential attack vectors.
    
- This phase is **analytical and iterative**—often requiring revisiting information gathering for deeper insights.
    

---

### **Types of Analysis Used**

1. **Descriptive** – Describes data, detects errors and outliers.
    
2. **Diagnostic** – Identifies causes and effects of vulnerabilities.
    
3. **Predictive** – Uses past and current data to forecast future issues or attack paths.
    
4. **Prescriptive** – Suggests actions to prevent or mitigate vulnerabilities.
    

---

### **Key Activities**

- **Vulnerability Research:**
    
    - Match discovered services, versions, or components with known vulnerabilities (CVEs).
        
    - Use sources like CVEdetails, ExploitDB, Vulners, Packet Storm, NIST.
        
- **Practical Analysis:**
    
    - Confirm assumptions through testing (e.g., checking non-standard ports or disguised services).
        
    - Adapt Proof-of-Concept (POC) exploits to match target configurations.
        
- **Attack Vector Assessment:**
    
    - Test discovered services or applications locally or on the target system.
        
    - If stealth is required, replicate the target environment to avoid detection.
        
    - Use diagnostic and predictive analysis to evaluate how vulnerabilities can be exploited.
        

---

### **Iterative Nature**

- If no vulnerabilities are found, **return to information gathering** for deeper analysis.
    
- **Information Gathering and Vulnerability Assessment frequently overlap**, requiring back-and-forth refinement.
    

---

### **Key Takeaway**

- **Real penetration tests prioritize depth and accuracy**, unlike CTF challenges where speed matters more.
    
- Thorough analysis ensures that no simple attack vector is missed, protecting clients from real-world threats.
    

---

### Exploitation Stage in Penetration Testing

**Goal:** Adapt identified weaknesses to gain a foothold or escalate privileges (e.g., reverse shell, access). Exploits may require modifying proof-of-concept (PoC) code to work against the specific target.

**Process Context:**  
Penetration testing involves interconnected stages:

- Pre-Engagement → Information Gathering → Vulnerability Assessment → Exploitation → Post-Exploitation → Lateral Movement → Proof-of-Concept → Post-Engagement  
    Although the stages overlap, tracking which phase you’re in prevents confusion during long or complex tests.
    

---

### Attack Prioritization Factors

When multiple vulnerabilities are found, rank attacks by:

1. **Probability of Success** – How likely is the exploit to work (CVSS/NVD scoring helps)?
    
2. **Complexity** – How much effort, time, and research are needed? (Easy/Medium/Hard weighting)
    
3. **Probability of Damage** – Avoid service disruption or crashes (DoS generally excluded unless requested).
    

**Example:** Remote File Inclusion scored higher than Buffer Overflow due to lower complexity and risk.

---

### Preparing for Exploitation

- If PoC code is missing or unreliable, replicate the target environment locally (matching OS and service versions).
    
- Test exploits on VMs first to ensure stability and safety.
    
- For common misconfigurations or well-known vulnerabilities, use familiar tools and techniques.
    
- If there’s any doubt about risk, **communicate with the client** and document findings rather than exploit unsafely.
    

---

### Transition to Later Stages

- After successful exploitation, carefully log every action for reporting.
    
- Next steps are **Post-Exploitation** and **Lateral Movement** to expand access while maintaining operational stability.

---------
### **1. Evasive Testing**

- **What it is:** Running tests in a way that avoids detection by security tools (EDR, SOC monitoring).
- - **Why it matters:** Even small commands can raise alerts. If detected, you may lose access, but this also shows your client that their defenses are working.

----

## **Proof of Concept (PoC) – إثبات الفكرة أو المبدأ**

الـ PoC مصطلح جاي من إدارة المشروعات، ومعناه إنك بتعمل **إثبات عملي إن المشروع أو الفكرة ممكن تتنفذ**.  
في الأمن السيبراني والاختبارات الاختراقية، الـ PoC يعني:  
**نثبت للعميل إن الثغرات اللي لقيناها حقيقية وممكن استغلالها، مش كلام نظري.**

---

### **ليه الـ PoC مهم؟**

1. **بيأكد وجود الثغرة فعلاً.**
    
2. **بيخلي المسؤولين (Admins/Developers) يشوفوا التأثير الحقيقي.**
    
3. **بيساعدهم يجرّبوا الحلول ويشوفوا لو قفلت الثغرة صح.**
    
4. **بيكون أساس لاتخاذ قرارات إصلاحية.**
    

---

### **أمثلة عملية:**

- أشهر مثال: **تشغيل برنامج calc.exe** على جهاز الضحية → الهدف هنا مش فتح الآلة الحاسبة بالذات، الهدف إثبات إنك قدرت تنفذ كود على الجهاز.
    
- ممكن كمان الـ PoC يكون:
    
    - **تقرير موثق بالخطوات والنتايج.**
        
    - **سكربت أو كود جاهز بيستغل الثغرة تلقائياً.**
        

---

### **المشكلة اللي بتحصل ساعات**

لما بتسلم سكربت PoC للـ Admins أو الـ Developers:

- ممكن يركزوا بس على تعطيل السكربت بتاعك نفسه.
    
- يعني يغيروا شوية إعدادات تخلي السكربت ما يشتغلش، لكن الثغرة نفسها **لسه موجودة** وممكن حد تاني يستغلها بطريقة تانية.
    

**الخلاصة:** لازم تشرح لهم إن السكربت مجرد طريقة واحدة للاستغلال، مش الحل إنك تمنع السكربت نفسه. الحل هو **تصليح أصل المشكلة.**

---

### **ربط الموضوع بالـ Attack Chain (سلسلة الهجوم)**

أحياناً بتكون الثغرات متصلة ببعض:

- مثلاً: باسورد ضعيف → يسمح باختراق جهاز → يسمح بجمع بيانات → يسمح بالتنقل في الشبكة → يوصلنا لحساب Domain Admin.
    
- لو العميل قفل الثغرة الأخيرة بس، السلسلة ممكن تتكرر بطريقة تانية.
    
- لازم نوضح في التقرير **إن كل نقطة ضعف لازم تتصلح، مش آخر نقطة بس.**
    

---

### **مثال واضح:**

- لو فيه يوزر باسورد بتاعه: **Password123**
    
- لو غيرنا الباسورد بتاع اليوزر ده بس، المشكلة لسه موجودة: سياسة الباسورد ضعيفة.
    
- لو الشركة كانت بتفرض باسوردات قوية من الأول، ماكانش هيقدر يحط باسورد ضعيف أصلاً.  
    **يعني أصل المشكلة → سياسة الباسورد، مش الباسورد نفسه.**
    

---

### **الهدف النهائي من الـ PoC والتقرير**

- نخلي العميل شايف **الصورة الكبيرة** مش بس تفاصيل سكربت معين.
    
- نديهم **خطوات واضحة لإصلاح الثغرات**.
    
- نوضح إن **جودة الأنظمة = معايير عالية في الأمان**.
    
- نأكد عليهم إن الـ Developers والـ Admins مسؤولين عن **جودة وأمان الأنظمة** زي ما هما مسؤولين عن وظيفتها.

-------

## المعنى العام

بعد ما نِكمّل: Recon → VA → Exploitation → Post-Exploitation → Lateral Movement → PoC… نخش على **Post-Engagement** عشان نقفل المشروع صح: ننضّف، نوثّق، نسلّم، نراجع، نعيد اختبار الإصلاحات، ونقفل البيانات.

---

## 1) Cleanup (تنظيف الآثار)

- امسح أي أدوات/سكربتات رفعتها على أجهزة العميل.
    
- ارجّع أي تغييرات بسيطة عملتها (يوزر أدمن مؤقت، سياسة، خدمة… إلخ).
    
- لو في حاجة مش قادر توصل لها عشان ترجعها → **نبّه العميل** وسجّلها في **الملحق** (Appendix).
    
- حتى لو رجّعت كل حاجة، **وثّق** إنك عملت تغييرات واتشالت؛ عشان لو اتطلعت Alerts عندهم يبقوا عارفين السبب.
    

---

## 2) Documentation & Reporting (التوثيق والتقرير)

قبل ما تعلن نهاية الاختبار:

- اجمع كل الأدلة: أوامر وخروجها، Screenshots، لستة الأجهزة المتأثرة، ملفات اللوج والاسكانات…
    
- ما تحتفظش بـ **بيانات حسّاسة** (PII/أسرار) على جهازك بعد التسليم.
    
- جهّز **تقرير مسوّدة (DRAFT)** مخصص لبيئة العميل ويشمل:
    
    1. **Attack Chain** لو حصل اختراق داخلي/انتقال من خارجي لداخلي.
        
    2. **Executive Summary** يفهمه المدير غير التقني.
        
    3. **Findings مفصّلة**: درجة الخطورة، الأثر، توصيات إصلاح، ومراجع قوية.
        
    4. **Steps to Reproduce** لكل Finding.
        
    5. **توصيات قصيرة/متوسطة/طويلة المدى** مناسبة لبيئتهم.
        
    6. **ملحقات**: النطاق، OSINT (لو مهم)، تحليل كلمات السر (لو اتعمل)، بورتات/خدمات، أجهزة وحسابات تم اختراقها، ملفات نُقلت، تعديلات/حسابات اتخلقت، تحليل AD (لو ينطبق)، ونتايج الاسكان وأي مستند داعم.
        

---

## 3) Report Review Meeting (اجتماع مراجعة التقرير)

- تبعت الـ **DRAFT**؛ العميل يراجع داخليًا.
    
- تعملوا جلسة مراجعة: تمشي على كل Finding باختصار، تشرح منظورك، وتجاوب أسئلتهم.
    
- عادةً بيركّزوا على العالي والحرِج مش كل التفاصيل.
    

---

## 4) Deliverable Acceptance (اعتماد المُخرجات)

- النطاق يوضح آلية الاعتماد.
    
- السيناريو المعتاد: **DRAFT → تعليقات العميل → FINAL**.
    
- بعض الجهات التدقيقية ما تقبلش تقرير عليه كلمة DRAFT.
    

---

## 5) Post-Remediation Testing (إعادة الاختبار بعد الإصلاح)

- ضمن التكلفة غالبًا.
    
- تعيد الوصول، وتختبر كل Finding: اتقفل صح ولا لأ؟
    
- تِصدر **تقرير ما قبل/ما بعد**. مثال جدول:
    

|#|الشدة|العنوان|الحالة|
|---|---|---|---|
|1|High|SQL Injection|Remediated|
|2|High|Broken Authentication|Remediated|
|3|High|Unrestricted File Upload|Remediated|
|4|High|Inadequate Web/Egress Filtering|Not Remediated|
|5|Medium|SMB Signing Not Enabled|Not Remediated|
|6|Low|Directory Listing Enabled|Not Remediated|

- قدّم **دليل** إن الاستغلال القديم بقى بيفشل أو أن الفحص بقى نظيف.
    

---

## 6) دور المختبِر في الإصلاح (الحياد)

- إحنا **مدققين محايدين**: نوصّف المشكلة وننصح **بشكل عام** (زي “عقّم مُدخلات المستخدم” في SQLi)؛  
    ما نكتبش كود بديل، ولا نطبّق باتشات، ولا نغيّر إعدادات نيابةً عنهم.
    
- كده نحافظ على الاستقلالية وما نخلقش **تضارب مصالح**.
    

---

## 7) Data Retention (الاحتفاظ بالبيانات)

- سياسة الاحتفاظ/الإتلاف تتحدّد في **العقد وRoE** ووفق القوانين المحلية وتنظيمات العميل.
    
- احتفظ بالأدلة فترة مناسبة (مشفّرة وعلى بنية مملوكة للشركة)، لمسائلة لاحقة أو لإعادة الاختبار.
    
- امسح كل الداتا من أجهزة المختبرين عند الخِتام.
    
- لأي إعادة اختبار لاحق: استخدم **VM جديدة** مخصّصة للعميل.
    

---

## 8) Close-Out (الإقفال النهائي)

- بعد تسليم **FINAL**، الرد على الاستفسارات، وإصدار تقرير Post-Remediation:
    
    - امسح/أتلف الأنظمة المستخدمة للاتصال، وخزّن أي آثار لازم تحفظها **بأمان وتشفير** وفق السياسة.
        
    - فوّتير/تحصيل.
        
    - أرسل **استبيان رضا**، ودوّن فرص التحسين.
        
    - راجع نفسك: التواصل، الوضوح، احترام الوقت—العميل غالبًا بيفتكر **تجربة التعامل** أكتر من سلسلة الاستغلال “الجامدة”.
        

---

## Checklist سريع قبل القفل

-  مسحت الأدوات وأرجعت التغييرات؟
    
-  جمّعت كل الأدلة والتقارير والاسكانات؟
    
-  سلّمت DRAFT مخصص ومرتب؟
    
-  عقدت مراجعة ودمجت ملاحظاتهم في FINAL؟
    
-  عملت Post-Remediation واختبرت الإصلاحات؟
    
-  طبّقت سياسة الاحتفاظ/الإتلاف ومسحت من أجهزة الاختبار؟
    
-  أرشفت كل حاجة المشفّرة حسب السياسة، وفوّتّرت، وبعت استبيان؟
    

-----
