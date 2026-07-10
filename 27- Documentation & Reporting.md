# Layer 1
الجزء ده من الـ CPTS من أهم الموديولز، والناس كتير بتستهين بيه لأنه "مش فيه هاكينج". لكن الحقيقة إن **التوثيق (Documentation) والـ Reporting هما اللي بيحولوا شغلك من مجرد واحد بيعرف يهاك إلى Pentester محترف**. ممكن تكون جبت Domain Admin في 10 دقايق، لكن لو معرفتش تشرح للعميل عملت إيه، ولا تكتب تقرير محترم، يبقى بالنسبة للعميل أنت معملتش حاجة.

---

## Introduction to Documentation and Reporting

## Strong documentation and reporting skills are incredibly beneficial...

بيقولك إن **مهارة كتابة الملاحظات (Documentation) وكتابة التقارير (Reporting)** من أهم المهارات في أي مجال من مجالات الـ IT أو الـ Information Security.

يعني مش بس في الـ Pentesting.

هتفيدك لو بقيت:

- System Administrator
    
- SOC Analyst
    
- DFIR
    
- Cloud Engineer
    
- DevOps
    
- Security Consultant
    
- Team Lead
    

لأن أي شغل بتعمله لازم حد بعدك يفهمه.

---

## mastering these skills can help us quickly progress in our careers

يعني لو اتعلمت المهارتين دول كويس هتترقى أسرع.

ليه؟

لأن الشركات مش بتدفعلك فلوس علشان تعرف تستخدم Nmap.

هي بتدفعلك علشان:

- تعرف تلاقي المشكلة
    
- تثبتها
    
- توثقها
    
- تشرحها
    
- وتقنع العميل يصلحها.
    

---

## Being highly technical is great and essential

يعني لازم تكون جامد تقنيا.

يعرف تستخدم

- Burp
    
- Metasploit
    
- BloodHound
    
- CrackMapExec
    
- Nmap
    
- وغيرها.
    

ده أساسي.

---

## but without soft skills...

لكن لو معندكش Soft Skills...

زي:

- الكتابة
    
- التواصل
    
- التنظيم
    
- شرح الأفكار
    

هتبقى أقل كفاءة.

---

## whether we are writing

سواء كنت بتكتب:

### Internal Policies

سياسات داخل الشركة.

مثلا:

ممنوع استخدام USB.

---

### Procedures

إجراءات.

مثلا:

لو الجهاز اتصاب Malware اعمل الخطوات دي.

---

### Technical Documentation

توثيق تقني.

يعني تشرح:

- السيرفرات
    
- الشبكة
    
- APIs
    
- Architecture
    

---

### Penetration Test Reports

وده اللي هنتعلمه.

يعني التقرير النهائي اللي بيتسلم للعميل.

---

## There is no "one size fits all"

يعني مفيش طريقة واحدة صح.

كل شركة ليها Style.

كل Pentester بيحب Tool مختلفة.

---

مثلا:

فيه ناس بتحب

Obsidian

وفيه

OneNote

وفيه

CherryTree

وفيه

Notion

وفيه Markdown Files

كله صح.

---

## but there are fundamental principles

لكن فيه قواعد أساسية لازم أي حد يمشي عليها.

زي مثلا:

- كل حاجة تتوثق
    
- كل Screenshot يتسمى صح
    
- كل Command يتحفظ
    
- كل Evidence يبقى موجود
    

---

## This module will explore

الموديول هيشرح:

---

## Different styles from notetaking tools

طرق مختلفة لكتابة الملاحظات.

---

## organizing our evidence

إزاي ترتب الأدلة.

يعني عندك Screenshots.

Logs.

Requests.

Responses.

Proofs.

كلهم يتحطوا بطريقة منظمة.

---

## writing Executive Summaries

دي أهم جزء في التقرير.

وده بيتكتب للـ Management.

يعني المدير.

الـ CEO.

الـ CTO.

مش للمهندس.

---

لأن المدير غالبا مش فاهم SQL Injection.

هو عايز يعرف:

- هل الشركة في خطر؟
    
- كام Vulnerability؟
    
- إيه الأولويات؟
    

---

## documenting Attack Chains

دي سلسلة الهجوم.

مثلا:

بدأت بـ

Anonymous FTP

↓

خدت Password

↓

دخلت SMB

↓

خدت User

↓

Privilege Escalation

↓

Domain Admin

دي كلها Attack Chain.

---

## technical findings

وده الجزء التقني.

كل Vulnerability لوحدها.

---

## We attempted to provide a generic formula

يعني المؤلفين بيقولوا:

إحنا عملنا Framework ينفع أي حد يستخدمه.

---

## tips, tricks and best practices

يعني مش مجرد شرح.

لا.

هيقولك Tricks من خبرة حوالي

25 سنة

في شغل Consulting.

---

## One crucial consideration

ودي نقطة مهمة جدا.

---

بيقول:

الـ Penetration Test

هو مجرد

Snapshot

---

يعني إيه Snapshot؟

يعني صورة في لحظة معينة.

مثال.

أنا عملت تست يوم

1 يناير.

لقيت:

- SQLi
    
- XSS
    

بعد أسبوع.

العميل قفلهم.

يبقى التقرير بتاعي بقى قديم.

---

أو العكس.

أنا عملت تست.

مفيش Vulnerabilities.

بعد يومين.

Developer رفع Code جديد.

طلع فيه RCE.

أنا ماليش دعوة.

لأن التقرير كان وقتها صحيح.

---

## We should include an overview section

لازم التقرير يبدأ بـ Overview.

وده بيشمل:

---

## type of work performed

نوع الاختبار.

مثلا:

Internal Penetration Test

أو

External

أو

Web Application

---

## who performed it

مين عمل التست.

اسم الشركة.

واسم الـ Pentester.

---

## source IP addresses

الـ IP اللي كنت بتهاجم منه.

مثلا

10.10.14.5

---

وده مهم.

علشان لو حصل مشكلة.

يعرفوا مين كان بيعمل Scan.

---

## testing performed remotely over VPN

هل كنت شغال:

- من VPN
    
- ولا داخل من الشبكة
    
- ولا Onsite
    

---

كل ده بيتكتب.

---

## This overview should also state

لازم تكتب تاريخ الاختبار.

مثلا:

من

7 يناير

إلى

19 يناير

---

وده معناه:

أي حاجة حصلت بعد التاريخ ده مش موجودة في التقرير.

---

## We could state

مثال:

All testing activities were performed between...

يعني كل الاختبارات تمت خلال الفترة دي.

---

## We could also add a disclaimer

Disclaimer

يعني إخلاء مسؤولية.

---

بيقول:

التقرير بيعبر عن حالة الشبكة وقت الاختبار فقط.

مش مسؤولين عن أي تغيير حصل بعد كده.

---

وده بيحمي الشركة.

---

## Documentation & Reporting in Practice

دلوقتي هيبدأ يحكيلك مواقف حقيقية.

---

## Scenario 1

## The Case of an Exploding VM

كان شغال في مشروع شهر كامل.

فتح الجهاز.

لقى الـ VM باظت تماما.

مش بتفتح.

Filesystem راح.

---

لو مكنش كاتب Notes؟

كان ضاع منه شهر شغل.

---

لكن هو كان بيستخدم

OneNote

وبيكتب كل حاجة.

---

وكان كل يوم يعمل Backup.

على Shared Storage.

---

يعني مثلا:

```
Evidence

Screenshots

Loot

Commands

Logs
```

كل ده بيتنسخ آخر اليوم.

---

فلما الـ VM باظت.

عمل VM جديدة.

Sync.

ورجع يكمل.

ولا كأن حاجة حصلت.

---

## لو معملش كده؟

هيخسر:

- أسابيع شغل
    
- العميل
    
- ويمكن وظيفته.
    

---

الدرس؟

اعمل Backup كل يوم.

---

## Scenario 2

## Ping of Death

كان بيعمل Internal Pentest.

---

فيه واحد من الـ IT

رخم جدا.

وشاكك في الفريق.

---

وكان فيه Servers حساسة.

---

بعد شوية العميل كلمه.

وقال:

وقفوا التست.

إنتوا وقعتم السيرفرات.

---

هو عمل إيه؟

طلع:

Logs

Timestamp

Scope File

Raw Scan Data

---

واتضح إن السيرفرات دي أصلا موجودة جوه الـ Scope.

والعميل بنفسه وافق عليها.

---

يعني الغلط مش منه.

---

لكن اتعلم درس.

من بعدها.

بقى يسأل العميل:

فيه أي IP معين

حتى لو داخل Scope

مش عايزينه يتعمله Scan؟

---

وده اسمه

Explicit Exclusion

---

الدرس؟

دايما خد موافقة مكتوبة.

---

## Scenario 3

## Slow as Molasses

كان شغال داخل مقر العميل.

جنب الـ IT.

---

وفيه Network Admin

مش طايقه.

---

بعد

20 دقيقة.

الراجل قال:

إنتوا بطأتوا الشبكة.

وقف التست.

وعمل Block للـ IP بتاعهم.

---

الفريق طلع:

كل Logs

وكل Scan Settings

---

وأثبتوا إنهم مستخدمين

Normal Nmap

مش Aggressive.

---

بعد التحقيق.

طلع السبب الحقيقي.

---

كان الـ Debug Mode

شغال على كل أجهزة الشبكة.

---

فالـ Debug Logs

Nmap

عملوا ضغط.

---

لما قفلوا الـ Debug.

كل حاجة رجعت طبيعية.

---

لو مكانش عندهم Documentation؟

كانوا هيتهموا إنهم السبب.

---

## These stories illustrate

القصص دي بتثبت أهمية التوثيق.

---

لازم تعرف تثبت:

إنت عملت إيه.

إمتى.

بأي Tool.

وبأي إعدادات.

---

## justify our actions

يعني لو حد سألك:

ليه عملت Scan؟

يبقى عندك دليل.

---

## produce evidence

تطلع الأدلة.

مش تقول:

"أنا فاكر إني عملت كذا."

---

لا.

تطلع Screenshot.

Log.

Command.

Timestamp.

---

## It is not uncommon

غالبا.

أي مشكلة تحصل أثناء الـ Pentest.

العميل هيقول:

أكيد الـ Pentester هو السبب.

---

علشان كده.

التوثيق بيحميك.

---

## We never want to scramble

يعني منبقاش بنجري.

ونعيد الشغل.

علشان ضيعنا الأدلة.

---

## About this Module

الموديول موفر:

---

## Sample Obsidian Notebook

دفتر Notes جاهز.

تتعلم منه.

---

## Sample Internal Penetration Test Report

تقرير Pentest كامل.

بصيغة:

- Word
    
- PDF
    

---

والباسورد:

```
hackthebox
```

---

## None of them are mandatory

التمارين اختيارية.

---

لكن بينصحك تعملها.

---

## taking detailed notes

ابدأ من دلوقتي.

وأنت بتحل Labs.

اكتب كل حاجة.

---

مثلا:

```
Target:

10.129.12.5

Nmap:

nmap -sC -sV

Ports:

22
80
445

Findings:

SMB Signing Disabled

Credentials:

guest:guest

Shell:

www-data

Privilege Escalation:

CVE-xxxx
```

---

مش تعتمد على ذاكرتك.

---

## reporting burden

الـ Reporting مرهق.

ومحدش بيحبه.

---

لكن لازم.

---

لو Notes بتاعتك منظمة.

هتكتب التقرير في ساعة.

---

لو مش منظمة.

ممكن تقعد يومين.

---

## pre-configured attack host

عاملين Lab صغير.

تتدرب عليه.

---

كأنك بتعمل Pentest حقيقي.

---

## develop a documentation style

اعمل Style يناسبك.

مثلا:

```
Projects/

Customer1/

Evidence/

Loot/

Screenshots/

Commands/

Notes.md

Report.docx
```

---

أو أي تنظيم يعجبك.

---

## Throughout the module

لما يقولوا:

> an internal

يقصدوا

Internal Penetration Test

---

ولما يقولوا

> an external

يقصدوا

External Penetration Test

---

## We've tried to make this topic more engaging

يعني بيقولوا:

إحنا عارفين إن الموديول ممل شوية.

بس حاولنا نخليه ممتع.

---

## الخلاصة المهمة جدًا

لو خرجت من الدرس بـ 10 نقاط، فهم دول:

1. **الهاكينج لوحده مش كفاية**؛ لازم تعرف توثق وتكتب تقرير احترافي.
    
2. **مفيش Tool واحدة صح** للتوثيق؛ المهم يكون شغلك منظم وقابل للرجوع إليه.
    
3. **دوّن كل حاجة**: الأوامر، الـ Screenshots، الـ Logs، الـ Credentials، والـ Evidence.
    
4. **اعمل Backup يوميًا** لملاحظاتك وأدلتك، لأن الـ VM أو الجهاز ممكن يتلف في أي وقت.
    
5. **اعتبر تقرير الـ Pentest Snapshot**؛ بيعكس حالة الأنظمة خلال فترة الاختبار فقط.
    
6. **اكتب دائمًا تفاصيل الاختبار**: نوعه، تاريخه، مين نفذه، ومن أي IP تم التنفيذ.
    
7. **احتفظ بموافقة العميل والـ Scope**؛ دي بتحميك لو حصل خلاف أو اتهام.
    
8. **التوثيق الجيد هو وسيلة دفاع عنك** لو العميل ادعى إنك سببت مشكلة في الشبكة.
    
9. **التقرير النهائي بيُقرأ من ناس تقنيين وغير تقنيين**، لذلك لازم يكون فيه جزء إداري وجزء تقني.
    
10. **كل ما تنظّم ملاحظاتك أثناء الاختبار، هتوفر وقت ومجهود كبير جدًا وقت كتابة التقرير النهائي.**

----
# Layer 2
الجزء ده يعتبر من أهم أجزاء الموديول كله، لأنه بيعلمك **إزاي تنظم شغلك أثناء الـ Pentest** بحيث لما تيجي تكتب التقرير متبدأش من الصفر. هشرحه بالتفصيل جدًا.

> الفقرة دي بتتكلم عن **Notetaking & Organization**.

---

## أولاً: Notetaking & Organization

يعني:

**كتابة الملاحظات وتنظيمها.**

ناس كتير وهي بتحل HTB أو بتشتغل Pentest بتقول:

> "أنا هفتكر."

وده أكبر غلط.

---

المؤلف بيقول:

> Thorough notetaking is critical during any assessment.

يعني:

كتابة ملاحظات بالتفصيل **شيء أساسي جدًا** أثناء أي Assessment.

ليه؟

لأن الملاحظات دي هي اللي هتتحول بعد كده للتقرير النهائي.

---

## Our notes... are the raw inputs to our draft report

يعني:

الملاحظات + الـ Logs + الـ Tool Output

دول المواد الخام للتقرير.

يعني بدل ما بعد 5 أيام تحاول تفتكر:

"أنا استغليت الـ SMB إزاي؟"

هتلاقي كل حاجة مكتوبة.

---

## العميل غالبًا مش هيشوف غير التقرير

ودي نقطة مهمة جدًا.

أنت ممكن تقضي أسبوع:

- تعمل Enumeration
    
- تستغل Vulnerabilities
    
- تجيب Domain Admin
    

لكن العميل غالبًا مش هيشوف كل ده.

هو هيشوف التقرير فقط.

فلو التقرير وحش...

بالنسبة للعميل أنت شغلك وحش.

---

## We must keep things organized

لازم كل حاجة تكون مترتبة.

مثلاً:

بدل ما يبقى عندك Desktop بالشكل ده:

```text
image1.png
final.png
newfinal.png
Screenshot (55).png
output.txt
aaa.txt
test.txt
```

يبقى عندك:

```text
Evidence/

    SMB/

    LLMNR/

    Kerberoast/

Scans/

Notes/

Logs/
```

هتلاقي أي حاجة في ثواني.

---

## Develop a repeatable process

يعني اعمل طريقة ثابتة.

كل Pentest تبدأ بنفس الشكل.

مثلاً:

```text
mkdir Client

Admin/

Evidence/

Notes/

Scans/

Logs/
```

كل مرة.

مش كل مشروع بشكل.

---

## Detailed notes are also a must

يعني لازم تكون مفصلة.

مثال.

بدل:

```text
عملت nmap
```

اكتب:

```text
2026-07-10

nmap -sC -sV 10.10.10.5

Open Ports

22 SSH

80 Apache

445 SMB
```

فرق كبير.

---

## لو العميل سألك

مثلاً بعد أسبوع.

يقولك:

هل عملت Scan على

10.10.20.15

يوم الخميس؟

لو معندكش Notes...

هتقوله:

"تقريبًا آه."

وده شكله وحش جدًا.

لكن لو عندك Activity Log.

هتفتح:

```text
Thursday

13:05

Started Nmap Scan

10.10.20.15
```

خلصت.

---

## Everyone will have their own style

يعني مفيش طريقة إجبارية.

كل واحد حر.

---

فيه ناس بتحب:

Obsidian

---

فيه ناس:

Notion

---

فيه ناس:

VS Code

---

فيه ناس:

Markdown

---

المهم التنظيم.

---

## Notetaking Sample Structure

دي بقى أهم صفحة في الدرس.

بيقولك:

إيه الصفحات اللي المفروض تبقى عندك.

---

## 1) Attack Path

دي أهم صفحة.

Attack Path

يعني:

إيه الطريق اللي وصلت بيه للـ Flag أو Domain Admin.

مثلاً:

```text
Nmap

↓

SMB

↓

Anonymous Login

↓

Found Password

↓

WinRM

↓

User Shell

↓

Privilege Escalation

↓

Administrator
```

ليه؟

علشان بعدين تحطها في التقرير.

---

## 2) Credentials

كل Password تلاقيها...

حطها هنا.

مثلاً:

```text
Administrator

Password123!

----------------

SQL

root

toor

----------------

FTP

guest

guest
```

بدل ما تفضل تدور.

---

## 3) Findings

كل Vulnerability.

اعمل Folder لوحدها.

مثلاً:

```text
Findings

    SMB Signing Disabled

    LLMNR Poisoning

    Weak Password

    Tomcat Default Credentials
```

وجوه كل Folder:

```text
Evidence

Commands

Screenshots

Narrative
```

---

## 4) Vulnerability Scan Research

دي للمحاولات.

مثلاً:

عملت Nessus.

طلع:

SMB Signing Disabled

فتبدأ تكتب.

جربت كذا.

وجربت كذا.

عشان متعيدش نفس الشغل.

---

## 5) Service Enumeration Research

دي أثناء الـ Enumeration.

مثلاً.

SSH

جربت:

Hydra

×

منفعش

---

SMB

Anonymous

✔

اشتغل.

---

LDAP

Anonymous Bind

×

مش شغال.

---

كل ده يتكتب.

---

## 6) Web Application Research

دي مخصوص للويب.

مثلاً.

لقيت:

```text
admin.example.com

login.example.com

dev.example.com
```

وتكتب:

جربت

admin:admin

×

جربت

tomcat:s3cret

×

لقيت لوحة Login.

كل ده يتكتب.

---

## 7) AD Enumeration Research

دي للـ Active Directory.

مثلاً.

عملت:

```text
BloodHound

LDAP

PowerView

SharpHound
```

ولقيت:

```text
Kerberoastable Users

ASREP Users

Interesting ACL
```

كل ده يتكتب.

---

## 8) OSINT

أي معلومات جمعتها من برة.

مثلاً.

LinkedIn

Employees

Emails

Subdomains

Leaks

---

## 9) Administrative Information

دي بيانات المشروع.

زي:

اسم الـ PM

اسم العميل

أرقام التليفونات

Objectives

Flags

Rules

حتى To-Do List.

---

مثلاً.

```text
Tomorrow

Check MSSQL

Run BloodHound Again

Try Responder
```

---

## 10) Scoping Information

دي مهمة جدًا.

يعني:

إيه اللي مسموح تهاجمه؟

مثلاً.

```text
In Scope

10.10.10.0/24

portal.company.com
```

---

Out Of Scope

```text
10.10.20.0/24
```

لو نسيت...

ممكن تهاجم حاجة ممنوعة.

وتعمل مشكلة كبيرة.

---

## 11) Activity Log

دي Diary.

يعني كل اللي عملته.

مثلاً:

```text
9:00

Started Scan

9:20

Found SMB

9:40

Responder

10:15

Got Credentials

10:30

BloodHound
```

---

## 12) Payload Log

دي للـ Payloads.

مثلاً:

```text
nc.exe

Uploaded To

C:\Temp

SHA256

xxxxxxxx

Deleted

Yes
```

وده مهم جدًا.

لأن العميل بعدين هيقولك:

إنت رفعت إيه؟

---

## Notetaking Tools

بعد كده بدأ يتكلم عن البرامج.

بيقول:

اختار اللي يريحك.

---

زي:

CherryTree

Notion

VS Code

OneNote

Obsidian

Standard Notes

Evernote

GitBook

---

## ليه Obsidian مشهور؟

لأنه:

- سريع
    
- Local
    
- Markdown
    
- مجاني
    
- يربط الصفحات ببعض
    
- مناسب جدًا للـ Pentest
    

عشان كده هتلاقي معظم الناس في المجال بتحبه.

---

## Cloud ولا Local؟

ودي نقطة مهمة جدًا.

لو بتلعب HTB.

اعمل Notes على Notion.

عادي.

لكن...

لو شغال مع Client حقيقي.

ومتفقين إن البيانات متخرجش برة الشركة.

يبقى مينفعش ترفع كل الـ Credentials على Cloud.

لازم تستخدم Local Tool.

---

## خلاصة الجزء ده

المؤلف عايز يقولك:

**مش مهم تستخدم أنهي برنامج، المهم يكون عندك نظام ثابت ومنظم.**

أي Pentest لازم يبقى عندك على الأقل:

- 📌 Attack Path
    
- 🔑 Credentials
    
- 🐞 Findings
    
- 🌐 Web Research
    
- 🖥️ AD Research
    
- 📡 OSINT
    
- 📅 Activity Log
    
- 💣 Payload Log
    
- 📋 Scope Information
    
- 📂 Folder Structure منظمة
    

---
## أولاً: يعني إيه Logging؟

Logging يعني:

**تسجيل كل حاجة أنت بتعملها أثناء الـ Pentest.**

مش بس الأوامر.

لا.

كمان:

- الـ Output
    
- الأخطاء
    
- الـ Payloads
    
- الـ Exploitation Attempts
    

يعني يبقى عندك سجل كامل.

---

المؤلف بيقول:

> It is essential that we log all scanning and attack attempts...

يعني لازم تسجل:

- كل Scan
    
- كل Exploit
    
- كل محاولة
    
- حتى المحاولات اللي فشلت
    

ليه؟

---

## ليه أسجل حتى المحاولات الفاشلة؟

تخيل العميل بعد أسبوع قالك:

> هل جربت تستغل SMB؟

لو أنت مجربتش تسجيل.

هتقول:

"أعتقد."

لكن لو عندك Logs.

هتفتحها.

وتلاقي:

```bash
crackmapexec smb ...
```

وتقول:

آه.

وده الـ Output.

---

## ليه الـ Logs مهمة؟

المؤلف قال:

ممكن أثناء كتابة التقرير تكتشف إنك نسيت Screenshot.

لكن عندك Log.

فتجيب منه الـ Output وتحطه في التقرير.

---

## Exploitation Attempts

يعني:

كل محاولة Exploit.

سواء نجحت أو لا.

تتسجل.

ليه؟

لأن ممكن العميل يقول:

> أنت عملت Testing قليل.

فتطلع الـ Logs.

وتقول:

أنا جربت:

- SMB
    
- LDAP
    
- FTP
    
- MSSQL
    
- Kerberoast
    

لكن مفيش Vulnerabilities.

وده يثبت إنك اشتغلت.

---

## Tmux Logging

وهنا بدأ يتكلم عن أفضل طريقة يعمل بيها Logging.

وهي:

## Tmux

---

## هو إيه Tmux؟

ناس كتير فاكرة إنه مجرد Terminal.

لا.

Tmux عبارة عن:

Terminal Multiplexer.

يعني يخليك تفتح أكتر من Terminal داخل Terminal واحدة.

مثلاً.

```
-------------------------
| responder | ntlmrelay |
|-----------|-----------|
| bloodhound| smbmap    |
-------------------------
```

كل دول جوه Session واحدة.

---

لكن ليه الناس بتحبه؟

مش علشان التقسيم.

علشان الـ Logging.

---

## المؤلف بيقول

> Tmux logging is an excellent choice

يعني:

أفضل حاجة لتسجيل الشغل.

---

## ليه؟

لأن Tmux هيكتب:

كل حرف أنت كتبته.

وكل Output ظهر.

في Log File.

---

يعني لو كتبت:

```bash
nmap -sV 10.10.10.5
```

هيتحفظ.

---

لو عملت:

```bash
evil-winrm
```

هيتحفظ.

---

لو ظهر Error.

يتحفظ.

---

لو Shell فتحت.

يتحفظ.

---

يعني بعد أسبوع.

تقدر ترجع لكل حاجة.

---

## إعداد Tmux Logging

المؤلف شرحها خطوة خطوة.

---

## أول خطوة

اعمل Clone للـ Plugin Manager.

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

يعني:

نزّل برنامج بيدير Plugins الخاصة بـ Tmux.

---

## بعد كده

اعمل ملف اسمه:

```bash
.tmux.conf
```

وده ملف الإعدادات.

زي:

```
.bashrc

.zshrc
```

---

## بعد كده

حط جواه:

```bash
set -g @plugin 'tmux-plugins/tpm'
```

يعني:

ثبت Plugin Manager.

---

بعدها:

```bash
set -g @plugin 'tmux-plugins/tmux-sensible'
```

وده Plugin بيظبط إعدادات Tmux.

---

بعدها:

```bash
set -g @plugin 'tmux-plugins/tmux-logging'
```

وده أهم واحد.

اللي بيعمل Logging.

---

وفي الآخر:

```bash
run '~/.tmux/plugins/tpm/tpm'
```

يعني:

شغل الـ Plugin Manager.

---

## بعد ما تحفظ الملف

لازم تقوله:

اقرأ الإعدادات الجديدة.

```bash
tmux source ~/.tmux.conf
```

يعني:

Reload للإعدادات.

---

## بعد كده

اعمل Session جديدة.

```bash
tmux new -s setup
```

يعني:

أنشئ Session اسمها:

setup

---

## تثبيت الـ Plugins

جوه Tmux.

اضغط:

```
Ctrl+B

ثم

Shift+I
```

خلي بالك.

مش مع بعض.

يعني:

Ctrl+B

سيبهم.

Shift+I

---

هيبدأ يحمل Plugins.

---

## تشغيل Logging

بعد ما يخلص.

اضغط:

```
Ctrl+B

Shift+P
```

هيقولك:

Logging Enabled.

---

من اللحظة دي.

كل حاجة بتعملها بتتسجل.

---

## إيقاف Logging

نفس الاختصار.

```
Ctrl+B

Shift+P
```

أو.

اقفل Session.

---

## فين الـ Log؟

هتلاقي File اتعمل.

جواه:

كل Commands.

وكل Output.

---

مثلاً:

```
nmap -sV

...

22/tcp open ssh

80/tcp apache

...

evil-winrm

...

*Evil-WinRM*

PS C:\Users\
```

كل ده محفوظ.

---

## لو نسيت تشغل Logging؟

ودي بتحصل كتير.

اشتغلت ساعتين.

وبعدين افتكرت.

---

المؤلف بيقول:

مفيش مشكلة.

اعمل:

```
Ctrl+B

Alt+Shift+P
```

وده اسمه:

Retroactive Logging.

---

## يعني إيه Retroactive؟

يعني:

يحفظ اللي فات.

---

لكن فيه مشكلة.

Tmux بيحتفظ بعدد معين من السطور.

مثلاً.

2000 سطر.

---

لو كتبت أكتر.

القديم هيتمسح.

---

علشان كده.

بيقولك.

زود الـ History.

---

حط في

.tmux.conf

```bash
set -g history-limit 50000
```

يعني:

احتفظ بـ

50000

سطر.

بدل الافتراضي.

وده مهم جدًا في اختبارات الـ Pentest الطويلة.

---

## Screen Capture

ودي ميزة جامدة جدًا.

تخيل عندك Window فيها Pane يمين وPane شمال.

```
---------------------
Responder | ntlmrelay
-----------|----------
```

وعايز تاخد Output من Responder بس.

لو Copy.

هتاخد النصين مع بعض.

شكله هيبقى وحش.

---

بدل كده.

اعمل:

```
Ctrl+B

Alt+P
```

هيطلعلك Output للـ Pane الحالية فقط.

مرتب جدًا.

---

## تقسيم الـ Panes

لو عايز تعمل Split.

رأسي.

```
Ctrl+B

Shift+%
```

هيبقى:

```
|     |
|     |
```

---

لو أفقي.

```
Ctrl+B

"
```

هيبقى:

```
--------
--------
```

---

## التنقل

بين الـ Panes.

```
Ctrl+B

O
```

يعني:

روح للـ Pane اللي بعدها.

---

## تنظيف الـ History

لو عايز تمسح الـ Scrollback.

اعمل:

```
Ctrl+B

Alt+C
```

---

## Plugins تانية

المؤلف رشح Plugins كويسة.

---

## tmux-sessionist

دي لإدارة Sessions.

مثلاً:

- تعمل Session جديدة.
    
- تبدل بينهم.
    
- تمسح Session.
    

---

## tmux-pain-control

بتسهل التحكم في الـ Panes.

بدل الاختصارات المعقدة.

---

## tmux-resurrect

ودي أسطورية.

تخيل.

الجهاز Restart.

كل Sessions راحت.

---

Plugin دي.

ترجعلك:

- الـ Sessions
    
- الـ Panes
    
- الـ Windows
    
- وحتى البرامج اللي كانت شغالة
    

كأن الجهاز مفيش حاجة حصلتله.

وده بيوفر وقت كبير جدًا لو شغال على مشروع طويل.

---

## الخلاصة

المؤلف عايز يوصلك فكرة مهمة جدًا:

**أي أمر بتكتبه أثناء الـ Pentest يعتبر دليل (Evidence)، فلا تعتمد على ذاكرتك. خلّي كل حاجة متسجلة تلقائيًا.**

لو حصل:

- Crash للـ VM.
    
- العميل سألك عن أمر معين.
    
- احتجت تضيف دليل للتقرير.
    
- احتجت تعرف إنت عملت إيه من 4 أيام.
    

هتفتح الـ Log، وهتلاقي كل حاجة قدامك.

وده من أهم العادات اللي بتميز الـ Pentester المحترف عن اللي بيشتغل بعشوائية.

---

## أولاً: Artifacts Left Behind

كلمة **Artifact** معناها:

> أي أثر أنت سيبته على جهاز العميل.

يعني إيه أثر؟

أي حاجة أنت رفعتها أو عملتها أثناء الـ Pentest.

مثلاً:

- Web Shell
    
- Reverse Shell
    
- nc.exe
    
- mimikatz.exe
    
- winPEAS.exe
    
- linpeas.sh
    
- SharpHound.exe
    
- أي Script أنت كتبته
    
- أي Payload من Metasploit
    

كل دول اسمهم Artifacts.

---

## ليه لازم أوثقهم؟

تخيل السيناريو ده.

رفعت:

```text
winPEAS.exe
```

في:

```text
C:\Temp\
```

خلصت الشغل.

ونسيت تمسحه.

بعد أسبوع.

الـ Antivirus مسكه.

الـ SOC شافه.

هيبدأوا يسألوا:

مين اللي رفع الملف ده؟

لو أنت موثقه.

هتعرف تجاوب.

---

## المؤلف بيقول

على الأقل لازم تكتب:

### 1- إمتى استخدمت الـ Payload؟

مثلاً.

```text
2026-07-10

13:20
```

---

### 2- على أنهي جهاز؟

مثلاً.

```text
DC01

10.10.10.5
```

---

### 3- اتحط فين؟

مثلاً.

```text
C:\Windows\Temp\

أو

/var/tmp/
```

---

### 4- هل مسحته؟

يعني.

```text
Deleted

YES
```

أو

```text
Needs Cleanup
```

---

### 5- File Hash

ودي ناس كتير بتتجاهلها.

---

## يعني إيه Hash؟

زي:

```text
SHA256

d3f67ab9....
```

ليه؟

لأن العميل ممكن يقول:

احنا لقينا الملف.

لكن اسمه اتغير.

---

طالما عندك Hash.

هيقدر يدور عليه.

حتى لو الاسم اتغير.

---

## ليه ده مهم؟

تخيل العميل عنده:

100 ألف File.

إزاي هيلاقي الملف؟

بالـ Hash.

---

## Best Practice

حتى لو مسحت الـ Payload.

اكتبه.

---

يعني:

```text
Payload

SharpHound.exe

Host

DC01

Path

C:\Temp

Hash

xxxxxxxx

Deleted

YES
```

---

## Account Creation / System Modifications

دي نقطة أخطر.

---

يعني:

لو عملت أي تعديل في سيستم العميل.

لازم تكتبه.

---

## أمثلة

عملت User جديد.

مثلاً.

```powershell
net user pentest Pass123 /add
```

يبقى لازم تكتب.

---

غيرت Registry.

اكتب.

---

فتحت Firewall Rule.

اكتب.

---

قفلت Defender.

اكتب.

---

عملت Scheduled Task.

اكتب.

---

شغلت RDP.

اكتب.

---

غيرت Password.

اكتب.

---

أي حاجة.

---

## المؤلف قال

اكتب:

---

### IP

أنهي جهاز؟

مثلاً.

```text
10.10.10.5
```

---

### Timestamp

امتى؟

---

### Description

عملت إيه؟

مثلاً.

```text
Created Local Admin Account
```

---

### Location

فين؟

مثلاً.

```text
C:\Users\
```

---

### Service

لو لعبت في Service.

اكتب اسمها.

---

### Account

لو عملت User.

اكتب:

اسمه.

والباسورد.

لو مطلوب.

---

## نقطة مهمة جدًا

المؤلف قال:

> لازم تاخد موافقة مكتوبة من العميل.

ليه؟

تخيل عملت:

```powershell
net user hacker pass /add
```

من غير إذن.

---

حتى لو هدفك نبيل.

أنت كده عدلت سيستم العميل.

وده ممكن يبقى مخالف للعقد.

---

عشان كده.

أي تعديل.

لازم Written Approval.

يعني Email.

أو Ticket.

أو موافقة مكتوبة.

---

## Evidence

ودي من أهم أجزاء التقرير.

---

المؤلف بيقول:

العميل...

مش مهتم.

إنك جبت Domain Admin.

😅

---

مستغرب؟

خليني أوضح.

هو أكيد مهتم إنك وصلت لـ Domain Admin، لكن اللي يهمه أكتر هو:

- **إزاي وصلت؟**
    
- **إيه الثغرة اللي سمحتلك؟**
    
- **إزاي يقدر يعيد التجربة ويتأكد إنها موجودة؟**
    
- **إزاي يصلحها؟**
    

وده كله اسمه:

Evidence.

---

## يعني إيه Evidence؟

الدليل.

مثلاً.

لقيت SQL Injection.

يبقى لازم يبقى عندك:

- Request
    
- Response
    
- Screenshot
    
- Payload
    
- Proof
    

---

مش تكتب:

> فيه SQL Injection.

وخلاص.

---

## ليه؟

لأن فريق الـ Blue Team.

أو الـ Developers.

هيقولوا:

ورينا.

---

لو معندكش إثبات.

ممكن يقولوا:

إحنا مش مصدقين.

---

## What to Capture

المؤلف بيقول:

كل Finding.

لازم يبقى ليها Evidence.

---

مثلاً.

لقيت:

LLMNR Poisoning.

يبقى تصور:

- Responder Output
    
- Hash
    
- Screenshot
    

---

لقيت:

Weak Credentials.

يبقى تصور:

- Login Page
    
- Successful Login
    
- Dashboard
    

---

لقيت:

Command Injection.

يبقى تصور:

```bash
id
```

والـ Output.

---

## هل أصور كل حاجة؟

لا.

صور الحاجات المهمة.

---

مثلاً.

بدل ما تصور.

```bash
ls
```

كل مرة.

---

صور:

- أول Shell
    
- أول Privilege Escalation
    
- أول DA
    
- الـ Proof
    

---

## المؤلف قال

Tmux Logs ممكن تكفي.

لكن...

شكلها ساعات يبقى وحش.

---

عشان كده.

خد Screenshot للحاجات المهمة.

أو انسخ الـ Output.

---

## Storage

بعد كده بدأ يتكلم عن التخزين.

ودي نقطة ناس كتير بتغلط فيها.

---

بيقول.

اعمل Folder Structure ثابت.

مثلاً:

```text
Project/

│

├── Admin/

├── Deliverables/

├── Evidence/

│     ├── Findings/

│     ├── Notes/

│     ├── Scans/

│     ├── Logs/

│     ├── OSINT/

│     ├── Misc/

│

└── Retest/
```

---

## يعني إيه كل Folder؟

### Admin

فيه:

- Scope
    
- Rules
    
- Emails
    
- Meeting Notes
    

---

### Deliverables

هنا التقرير النهائي.

مثلاً.

```text
Report.docx

Report.pdf
```

---

### Evidence

كل الأدلة.

---

### Findings

كل Vulnerability في Folder.

---

### Scans

كل:

Nmap

Nessus

Masscan

Exports

---

### Web

Burp

ZAP

EyeWitness

---

### AD Enumeration

BloodHound

PowerView

SharpHound

---

### Notes

كل الـ Notes.

---

### OSINT

أي حاجة من LinkedIn.

أو Google.

---

### Logging Output

Logs بتاعة:

Tmux

Metasploit

Responder

---

### Misc Files

أي Scripts.

أي Payloads.

أي Tools.

---

### Retest

لو العميل قالك بعد شهر:

تعالى اتأكد إننا قفلنا الثغرات.

يبقى تحط أدلة إعادة الاختبار هنا، وتفصلها عن الأدلة الأصلية.

---

## خلاصة الجزء ده

الرسالة الأساسية من المؤلف هي:

**أنت مش مجرد شخص بيهاجم الأنظمة، أنت مستشار (Consultant).**

وده معناه إنك لازم:

- توثق كل Payload رفعتها.
    
- توثق أي تعديل عملته على أجهزة العميل.
    
- تاخد موافقة قبل أي تغيير مؤثر.
    
- تجمع Evidence كافية لكل Finding.
    
- ترتب الأدلة في Folder Structure ثابتة ومنظمة.
    

لو عملت كده، كتابة التقرير في آخر المشروع هتبقى أسهل بكتير، ولو العميل رجع بعد شهور يسألك عن أي خطوة، هتقدر ترد عليه بدليل موثق بدل ما تعتمد على الذاكرة.

الجزء اللي بعده هيبدأ يتكلم عن **Formatting and Redaction**، وده هيشرح إزاي تعرض الـ Screenshots والـ Terminal Output بشكل احترافي، وإزاي تخفي البيانات الحساسة بطريقة صحيحة بدل الطرق اللي ممكن تتفك بسهولة.

عشان تسهل على نفسك
```shell
0xTroj6n@htb[/htb]$ mkdir -p ACME-IPT/{Admin,Deliverables,Evidence/{Findings,Scans/{Vuln,Service,Web,'AD Enumeration'},Notes,OSINT,Wireless,'Logging output','Misc Files'},Retest}
```

---

## أولاً: Formatting

يعني:

**تنسيق التقرير.**

---

ناس كتير وهي بتكتب التقرير تعمل حاجة زي كده:

```
Found SQLi

Payload:

'or 1=1--

Result:

worked

Then got shell

Then became root
```

ده شكله غير احترافي.

لكن المفروض يبقى بالشكل ده:

---

## عنوان واضح

مثلاً:

```
SQL Injection in Login Page
```

---

بعدها Description.

يعني:

الثغرة دي إيه؟

---

بعدها Impact.

يعني:

هتسبب إيه؟

---

بعدها Evidence.

يعني:

الـ Screenshot.

---

بعدها Remediation.

يعني:

إزاي تتصلح.

---

بعدها References.

مثلاً:

OWASP.

أو CVE.

---

يبقى أي Finding ليها نفس الشكل.

وده يخلي التقرير كله Professional.

---

## Consistency

المؤلف ركز جدًا على كلمة:

Consistency.

يعني:

الثبات.

---

لو أول Vulnerability كاتبها بالشكل ده:

```
Title

Description

Evidence

Impact

Fix
```

يبقى كل الـ Vulnerabilities بنفس الشكل.

---

مش أول واحدة بالألوان.

والتانية Font مختلف.

والتالتة بدون Screenshots.

---

العميل هيحس إن التقرير متلخبط.

---

## Screenshot Formatting

ودي نقطة مهمة جدًا.

---

ناس كتير تعمل Screenshot كده.

```
_____________________________________

Burp

History

Repeater

Proxy

Options

Intercept

HTTP History

..........

...............

..............
```

والثغرة أصلاً في سطر واحد.

---

ليه؟

الصورة بقت مليانة كلام ملوش لازمة.

---

المؤلف بيقول:

قص الصورة.

بحيث يبان الجزء المهم فقط.

---

يعني بدل:

```
_________________________

Burp بالكامل

Proxy

Target

Repeater

Logger

............

SQLi هنا

............
```

يبقى:

```
Username:

'

SQL Error
```

بس.

---

يبقى القارئ ركز على الثغرة.

---

## Highlighting

يعني:

اعمل Highlight.

---

مثلاً.

لو فيه Password.

بدل ما تخلي القارئ يدور عليه.

اعمل:

⬜ مستطيل أحمر.

أو.

سهم.

يشاور عليه.

---

مثلاً.

بدل الصورة دي.

```
Administrator

Password

Welcome
```

خليها.

```
Administrator

⬅ Login Successful
```

---

القارئ هيشوفها في ثانية.

---

## Terminal Output

ودي نقطة جميلة جدًا.

---

بدل ما تصور Terminal بالكامل.

انسخ الجزء المهم.

مثلاً.

بدل:

```bash
kali@box

pwd

cd Desktop

ls

id

whoami

hostname

uname

...
```

انسخ:

```bash
www-data

uid=33(www-data)

gid=33(www-data)
```

وده يكفي.

---

## ليه؟

لأن التقرير مش Tutorial.

---

هو تقرير.

---

## Redaction

ودي من أهم النقاط.

---

يعني إيه Redaction؟

إخفاء المعلومات الحساسة.

---

مثلاً.

لقيت Password.

```
Administrator

Password:

Summer2026!
```

مينفعش تحطها في التقرير.

---

ليه؟

لأن التقرير ساعات بيتبعت:

- للإدارة
    
- للمطورين
    
- لشركة تانية
    
- للمراجعة
    

---

مينفعش كل الناس تشوف Password.

---

يبقى تعمل.

```
Password:

***********
```

أو.

```
Summer********
```

---

## IP Addresses

برضو.

ممكن العميل يقولك.

متظهرش الـ IP الحقيقي.

---

يبقى.

```
10.10.xx.xx
```

---

## Usernames

مثلاً.

```
Mohamed Hassan
```

تبقى.

```
M******** H******
```

---

## Email

بدل.

```
admin@company.com
```

تبقى.

```
a****@company.com
```

---

## Internal Hostnames

بدل.

```
DC01.COMPANY.LOCAL
```

تبقى.

```
DCXX.COMPANY.LOCAL
```

---

## ليه؟

علشان التقرير ممكن يتشارك.

ومينفعش يطلع فيه معلومات حساسة.

---

## أهم تحذير في الدرس

المؤلف قال حاجة ناس كتير بتغلط فيها.

قال:

**متستخدمش Blur.**

---

ودي نقطة ناس كتير متعرفهاش.

---

ليه Blur غلط؟

لأن الـ Blur ساعات بيتفك.

أو باستخدام AI.

أو Image Processing.

أو حتى لو الـ Blur خفيف.

تقدر تقرأ الكلام.

---

كمان.

مينفعش تعمل.

```
Opacity
```

وتقللها.

برضو ممكن تتشاف.

---

ولا تعمل.

```
Semi Transparent Box
```

لأن الكلام بيبان من تحته.

---

## الصح إيه؟

استخدم.

مستطيل لونه:

أسود.

أبيض.

أو أي لون Solid.

مثلاً.

```
████████████
```

بحيث يمحي البيانات نهائي.

---

## Crop Carefully

لو هتقص Screenshot.

خلي بالك.

---

ممكن تقص الصورة.

لكن يبقى ظاهر.

```
admin@company.local
```

في الـ Tab فوق.

---

أو.

يبقى ظاهر.

اسم العميل.

---

أو.

اسم المشروع.

---

راجع الصورة كلها.

مش الجزء اللي في النص بس.

---

## Metadata

ودي نقطة محترفين.

---

الصورة نفسها.

بتحتوي Metadata.

زي.

- اسم الجهاز.
    
- تاريخ الالتقاط.
    
- أحيانًا اسم المستخدم.
    

---

بعض الشركات بتمسح Metadata.

قبل إرسال التقرير.

---

## Resolution

خلي الصور واضحة.

---

مش صورة.

```
400x200
```

ومتكبرها.

فتبقى مشوشة.

---

خد Screenshot بدقة كويسة.

---

## نفس الفكرة مع Burp

لو Screenshot من Burp.

قصها.

واظهر:

- Request
    
- Response
    
- Error
    

بس.

---

مش لازم كل الـ Interface.

---

## خلاصة الجزء

المؤلف عايز يقولك:

**شكل التقرير بيمثل احترافيتك بنفس قدر المحتوى.**

لو الـ Screenshots:

- صغيرة.
    
- مشوشة.
    
- فيها بيانات حساسة.
    
- بدون Highlight.
    
- مليانة أجزاء ملهاش لازمة.
    

القارئ هيتعب جدًا.

لكن لو كل صورة:

- مقصوصة كويس.
    
- واضحة.
    
- فيها Highlight.
    
- ومخفية منها البيانات الحساسة بطريقة صحيحة.
    

هيفهم الـ Finding في ثوانٍ.

---

## أهم النصائح اللي تطلع بيها من الجزء ده

- 📌 استخدم Template ثابت لكل Vulnerability.
    
- 📌 خلي ترتيب الأقسام ثابت في كل التقرير.
    
- 📌 قص الـ Screenshots بحيث تظهر الجزء المهم فقط.
    
- 📌 استخدم أسهم أو مربعات لتوجيه عين القارئ للمعلومة المهمة.
    
- 📌 انقل الـ Terminal Output المهم بدل ما تعرض شاشة مليانة أوامر.
    
- 📌 أخفِ أي بيانات حساسة (Passwords، Tokens، Emails، IPs...) باستخدام **مستطيلات بلون ثابت**.
    
- ❌ متستخدمش Blur أو تمويه لأنه ممكن يكون قابل للاسترجاع.
    
- 📌 راجع الصور قبل إدراجها للتأكد إن مفيهاش أسماء عملاء أو معلومات حساسة ظاهرة في الأطراف أو الـ Tabs.
    

الجزء اللي بعده هيبدأ يدخل في **Writing the Penetration Test Report**، وده يعتبر قلب الموديول كله، لأنه هيشرح بالتفصيل كل جزء من أجزاء التقرير الاحترافي: Executive Summary، Scope، Methodology، Findings، Risk Ratings، وRemediation. ده من أهم أجزاء الـ CPTS، وهنفصله سطر بسطر.

-------


# Layer 3
الجزء ده بيتكلم عن **أنواع الـ Reports** وإمتى تستخدم كل نوع، وإيه الفرق بين كل Assessment. ده من أهم الأجزاء لو هتشتغل Pentester أو Consultant، لأن مش كل شغل بيطلع بنفس التقرير

---
## Types of Reports

يعني:

**أنواع التقارير.**

المؤلف بيقول إن **شكل التقرير بيتغير حسب نوع الـ Assessment** اللي العميل طلبه.

يعني مش كل مرة هتسلم نفس التقرير.

---

## مثال

لو العميل طالب:

- Internal Pentest
    

غير

- External Pentest
    

غير

- Web Pentest
    

غير

- Vulnerability Assessment
    

كل واحد ليه Report مختلف شوية.

---

## في الكورس ده

إحنا هنركز على:

**Internal Penetration Test**

وفيه في النهاية وصلنا لـ

**Active Directory Domain Compromise**

يعني قدرنا نبقى Domain Admin.

وده أشهر سيناريو في الشركات.

---

## الفرق بين Internal و External Report

هو بيقول:

ممكن تلاقي تقرير External فيه نفس أجزاء Internal.

مثلاً:

- Attack Chain
    
- Executive Summary
    
- Findings
    

لكن فيه فرق مهم.

---

## External بيحتاج OSINT

يعني قبل ما تبدأ الهجوم هتجمع معلومات من الإنترنت.

زي:

- Emails
    
- Subdomains
    
- DNS Records
    
- Company Information
    

لكن في اللاب بتاع HTB مش هتعمل كده لأنه مش شركة حقيقية.

---

## أمثلة على معلومات الـ OSINT

المؤلف ذكر أمثلة:

---

## Public DNS

يعني معلومات الـ DNS العامة.

مثلاً:

```text
company.com

mail.company.com

vpn.company.com
```

---

## Email Addresses

إيميلات الموظفين.

مثلاً.

```text
ahmed@company.com
```

بعد كده ممكن تعمل عليهم:

- Breach Search
    
- Password Spraying
    
- Google Dorks
    

---

## Subdomains

مثلاً.

```text
portal.company.com

vpn.company.com

mail.company.com
```

---

## Third-party Vendors

الشركات اللي بتتعامل مع العميل.

ليه؟

ممكن يبقى الهجوم عليهم أسهل.

---

## Similar Domains

زي.

```text
google.com

g00gle.com
```

أو.

```text
company.org

company.net
```

ممكن تستخدم في Phishing.

---

## Public Cloud Resources

زي:

AWS

Azure

GCP

هل عندهم:

- S3 Bucket
    
- Blob Storage
    
- Public VM
    

كل ده بيتجمع أثناء الـ OSINT.

---

## Differences Across Assessment Types

يعني:

الفرق بين أنواع الاختبارات.

---

## أول نوع

## Vulnerability Assessment

ودي ناس كتير بتلخبط بينها وبين Pentest.

---

### يعني إيه Vulnerability Assessment؟

يعني:

أشغل Scanner.

مثلاً:

- Nessus
    
- OpenVAS
    
- Qualys
    

وخلاص.

---

هيعمل Scan.

ويطلع:

```text
SMB Signing Disabled

Critical

----------------

Apache Outdated

Medium

----------------

Weak Cipher

Low
```

---

## هل بنستغل الثغرات؟

لا.

وده أهم فرق.

---

المؤلف بيقول:

> No exploitation is attempted

يعني:

ممنوع تستغل الثغرة.

أنت بس تثبت إنها موجودة.

---

## طيب ممكن نعمل Validation؟

آه.

يعني.

لو Nessus قال:

Apache فيه CVE.

أنت تدخل تتأكد.

إن فعلاً Version ده موجود.

لكن متعملش Exploit.

---

## الهدف

هو:

تأكيد النتائج.

مش اختراق الشبكة.

---

## Internal vs External Vulnerability Assessment

---

## External Scan

الـ Scanner يبقى برة الشركة.

زي أي Hacker على الإنترنت.

هيشوف:

- Website
    
- VPN
    
- Mail Server
    

بس.

---

## Internal Scan

الـ Scanner جوه الشركة.

هيشوف:

- أجهزة الموظفين
    
- Domain Controllers
    
- Printers
    
- Servers
    

كل حاجة.

---

## Authentication

أوقات العميل يديك Username وPassword.

علشان الـ Scanner يدخل الأجهزة.

ويطلع نتائج أدق.

وده اسمه:

Authenticated Scan.

---

## Report Contents

تقرير الـ Vulnerability Assessment بيبقى مختلف.

هو غالبًا بيحتوي على:

- عدد الـ Critical
    
- عدد الـ High
    
- عدد الـ Medium
    
- عدد الـ Low
    

وبيحاول يجمع الثغرات المتشابهة.

مثلاً:

بدل ما يكتب:

500 جهاز فيهم SMB Signing Disabled.

يقول:

**يوجد ضعف في إعدادات SMB على 500 جهاز.**

وده أسهل للعميل.

---

## النوع التاني

## Penetration Testing

وده اللي إحنا بنتعلمه.

---

المؤلف بيقول:

Penetration Testing

بيبدأ من بعد الـ Vulnerability Scan.

لكن مش لازم يستخدم Scanner أصلاً.

---

يعني ممكن.

ولا تعمل Nessus.

ولا OpenVAS.

وتبدأ Manual.

---

## هنا بقى بنستغل الثغرات

مثلاً.

لقيت:

Weak Password.

هتجرب تدخل.

---

لقيت:

SQL Injection.

هتستغلها.

---

لقيت:

RCE.

هتاخد Shell.

---

لقيت:

SMB Signing Disabled.

هتعمل NTLM Relay.

---

يبقى.

الـ Pentest = Exploitation.

مش مجرد اكتشاف.

---

## أنواع الـ Pentest

المؤلف شرح 3 أنواع مشهورين.

---

## Black Box

يعني:

العميل مدالك.

اسم الشركة بس.

مثلاً.

```text
Acme Corp
```

ويقولك.

ابدأ.

زي الـ Hacker الحقيقي.

---

## Grey Box

يديك شوية معلومات.

مثلاً.

```text
10.10.10.0/24
```

ويقولك.

دول Scope.

---

## White Box

وده أسهلهم.

العميل يديك:

- Source Code
    
- Credentials
    
- Architecture
    
- Configurations
    

يعني كل حاجة.

وده بيبقى هدفه مراجعة أمنية شاملة، مش محاكاة مهاجم خارجي.

---

## Evasive Testing

ودي جميلة جدًا.

---

يعني:

تحاول متتكتشفش.

---

مثلاً.

بدل.

```bash
nmap -A
```

تستخدم.

```bash
nmap -T2
```

أبطأ.
---

بدل.

تعمل Password Spray بسرعة.

توزعه على أيام.

---

الهدف.

تشوف.

الـ Blue Team

هيلاحظك إمتى.

---

## Adversary Simulation

ودي أعلى مستوى.

---

ممكن تستمر:

شهر.

شهرين.

3 شهور.

---

وتتصرف.

كمهاجم حقيقي.

---

وده بيبقى مناسب للشركات الكبيرة جدًا.

---

## Internal vs External Pentest

## External

أنت برة الشركة.

بتهاجم:

- Website
    
- VPN
    
- Mail
    
- Public Services
    

وقد تستخدم معلومات OSINT علشان توصل لمدخل للشبكة.

---

## Internal

أنت جوه الشبكة.

أو معاك User عادي.

وهدفك:

- Initial Access
    
- Privilege Escalation
    
- Lateral Movement
    
- وفي الآخر Domain Compromise
    

وده السيناريو الأشهر في بيئات Active Directory.

---

## خلاصة الجزء

المؤلف عايزك تفرق كويس بين المصطلحات دي:

|النوع|هل فيه Exploitation؟|الهدف|
|---|---|---|
|**Vulnerability Assessment**|❌ لا|اكتشاف الثغرات والتحقق منها|
|**Penetration Test**|✅ نعم|استغلال الثغرات لإثبات تأثيرها|
|**External Pentest**|من خارج الشركة|اختبار الأنظمة المكشوفة على الإنترنت|
|**Internal Pentest**|من داخل الشبكة|الوصول لصلاحيات أعلى واختبار الشبكة الداخلية|
|**Black Box**|معلومات شبه معدومة|محاكاة مهاجم خارجي|
|**Grey Box**|معلومات محدودة|اختبار واقعي مع بعض المعلومات|
|**White Box**|كل المعلومات متاحة|مراجعة أمنية شاملة وعميقة|

الجزء اللي بعده في الموديول هيبدأ يتكلم عن **Inter-Disciplinary Assessments** (زي Purple Team، Cloud Pentest، IoT، Web Pentest)، وبعدها هيدخل في دورة حياة التقرير نفسها: **Draft Report → Final Report → Post-Remediation Report → Attestation Letter**، وده من أهم أجزاء الشغل مع العملاء.


--------
## Inter-Disciplinary Assessments

خلينا نفهم معنى الاسم الأول.

## Inter-Disciplinary

يعني:

**Assessment بيجمع أكتر من تخصص.**

يعني مش مجرد Pentest عادي.

مثلاً.

بدل ما تهاجم Website بس.

لأ.

تعمل:

- Web
    
- Active Directory
    
- Cloud
    
- Wireless
    
- Physical
    

كلهم مع بعض.

---

المؤلف بيقول إن دلوقتي معظم الشركات بقت كبيرة ومعقدة.

يعني الشركة الواحدة ممكن يبقى عندها:

- Active Directory
    
- Azure
    
- AWS
    
- Office 365
    
- Web Applications
    
- APIs
    
- VPN
    
- Mobile Apps
    

فمينفعش تعمل نوع واحد من الاختبارات.

لازم أكتر من تخصص.

---

## مثال

تخيل شركة شغالة على Azure.

الموظف يدخل على:

Office365

↓

يفتح VPN

↓

يوصل Active Directory

↓

يفتح Web Application

↓

الـ Database موجودة على AWS.

---

لو اختبرت الـ Web بس.

يبقى اختبرت جزء صغير جدًا.

---

## Purple Team Assessment

ودي من أشهر الأنواع.

---

احنا نعرف:

## Red Team

المهاجمين.

---

## Blue Team

المدافعين.

---

يبقى.

## Purple Team

الاتنين بيشتغلوا مع بعض.

---

يعني إيه؟

مثلاً.

أنا كـ Pentester.

أقول للـ Blue Team.

> دلوقتي هعمل Kerberoasting.

---

الـ Blue Team.

يبدأ يشوف.

هل الـ SIEM لاحظ؟

هل الـ EDR اكتشف؟

هل الـ Alert اشتغل؟

---

لو مشتغلش.

يبقى فيه مشكلة.

---

يبقى الهدف.

مش الاختراق.

الهدف.

تحسين الدفاعات.

---

## Cloud Assessment

وده بقى منتشر جدًا.

---

بدل ما الشركة عندها Servers.

بقى عندها.

AWS

Azure

GCP

---

فإنت هتراجع.

---

## IAM

مين يقدر يعمل إيه؟

---

## S3 Buckets

هل Public؟

---

## Azure Storage

هل مكشوف؟

---

## Security Groups

هل مفتوحة؟

---

## Secrets

هل فيه API Keys؟

---

يعني.

Cloud Pentest.

---

## Wireless Assessment

وده خاص بالـ WiFi.

---

بتراجع.

- WPA2
    
- WPA3
    
- Guest Network
    
- Rogue AP
    
- Evil Twin
    

---

هل حد يقدر يدخل الشبكة من برة؟

---

## Physical Assessment

ودي ممتعة جدًا.

---

الشركة تقولك.

جرب تدخل المبنى.

---

لو قدرت تدخل.

يبقى نجحت.

---

مثلاً.

تعمل.

Tailgating.

يعني.

تمشي ورا موظف.

يدخلك.

---

أو.

تحط.

Raspberry Pi.

في الشبكة.

---

وده يعتبر جزء من الـ Assessment.

---

## Web Application Assessment

وده اللي معظم الناس تبدأ بيه.

---

تركز على:

- SQL Injection
    
- XSS
    
- XXE
    
- SSTI
    
- SSRF
    
- IDOR
    

وغيرهم.

---

## Mobile Assessment

لو الشركة عندها App.

Android.

أو iPhone.

---

تراجع.

- Storage
    
- API
    
- Root Detection
    
- SSL Pinning
    
- Reverse Engineering
    

---

## API Assessment

ممكن الشركة متبقاش عندها Website.

كل شغلها APIs.

---

فتراجع.

- Authentication
    
- Authorization
    
- JWT
    
- Rate Limit
    
- Mass Assignment
    

---

## Social Engineering

ودي برضو Assessment.

---

يعني.

العميل يقولك.

جرب تخدع الموظفين.

---

تبعت.

Phishing Email.

---

أو.

تكلمهم.

---

أو.

تعمل USB Drop.

---

كل ده بيتوثق في التقرير.

---

## دلوقتي بدأ يتكلم عن أنواع الـ Reports

ودي بقى مهمة جدًا.

---

## أول نوع

## Draft Report

يعني.

المسودة.

---

إيه الفرق بينها وبين التقرير النهائي؟

---

لسه.

فيها:

- أخطاء.
    
- ملاحظات.
    
- ناقصة.
    
- تحت المراجعة.
    

---

الشركة بتراجعها.

---

QA Team

↓

Manager

↓

Senior Consultant

↓

وبعدين.

تطلع Final.

---

## ليه؟

علشان ميطلعش التقرير فيه:

- غلطات.
    
- Screenshots ناقصة.
    
- Severity غلط.
    

---

## Final Report

وده.

النسخة الرسمية.

---

دي اللي العميل بيستلمها.

---

بعدها.

مينفعش تغير فيها.

إلا لو العميل طلب Retest.

---

كل حاجة فيها لازم تكون:

- صحيحة.
    
- متراجعة.
    
- Professional.
    

---

## Retest Report

ودي بتحصل كتير.

---

العميل بعد شهر.

يقولك.

إحنا قفلنا الثغرات.

تعال اتأكد.

---

إنت.

ترجع.

وتختبر تاني.

---

مثلاً.

كانت.

SQL Injection.

---

تدخل.

تلاقيها اتقفلت.

---

يبقى.

في التقرير.

تكتب.

```text
Status

Resolved
```

---

ولو.

لسه موجودة.

تكتب.

```text
Still Vulnerable
```

---

## Partial Remediation

ودي ناس كتير بتتلخبط فيها.

---

يعني.

العميل قفل جزء.

وساب جزء.

---

مثلاً.

كان عنده.

10 سيرفرات.

فيهم SMB Signing Disabled.

---

راح قفل.7

وساب.3

---

يبقى.

مش.

Resolved.

---

ولا.

Unresolved.

---

اسمها.

Partial Remediation.

---

## Attestation Letter

ودي وثيقة صغيرة.

---

مش تقرير.

---

مجرد جواب.

---

بيقول.

إن.

الشركة.

عملت Pentest.

خلال الفترة.

من.

كذا.

إلى.

كذا.

---

وبيستخدموه.

في.

Compliance.

---

زي.

PCI DSS.

---

أو.

ISO27001.

---

أو.

SOC2.

---

بدل ما يبعث التقرير كله.

يبعت.

Attestation Letter.

---

## Executive Letter

أحيانًا العميل.

ميبقاش عايز.

100 صفحة.

---

الـ CEO.

مش هيقرا.

100 صفحة.

---

هو عايز.

صفحة.

أو اتنين.

---

فيهم.

- أهم المخاطر.
    
- مستوى الأمان.
    
- عدد الـ Critical.
    
- الأولويات.
    

---

وده.

غير.

Executive Summary.

---

لأن.

Executive Summary.

جزء من التقرير.

---

لكن.

Executive Letter.

وثيقة مستقلة.

---

## Deliverables

يعني.

إيه اللي العميل هيستلمه؟

غالبًا.

- PDF Report
    
- Word Report (أحيانًا)
    
- Raw Scan Results (لو اتفقوا)
    
- Screenshots
    
- Retest Report (لو موجود)
    
- Attestation Letter (حسب الحاجة)
    

---

## الخلاصة

المؤلف عايزك تفرق بين الحاجات دي كويس:

|النوع|معناه|
|---|---|
|**Draft Report**|مسودة أولية تحت المراجعة|
|**Final Report**|النسخة الرسمية اللي بتتسلم للعميل|
|**Retest Report**|تقرير إعادة الاختبار بعد إصلاح الثغرات|
|**Partial Remediation**|بعض الثغرات اتصلحت وبعضها لسه موجود|
|**Attestation Letter**|خطاب رسمي يثبت إن الاختبار تم، بدون تفاصيل فنية|
|**Executive Letter**|ملخص تنفيذي مستقل للإدارة العليا|

---

### نقطة مهمة من خبرة الشغل

في شركات الـ Pentesting، **كتابة التقرير غالبًا بتمر بمراحل**:

1. **أنت كـ Pentester** تكتب الـ Draft Report.
    
2. **Senior Pentester أو QA** يراجع كل Finding:
    
    - هل الـ Severity صح؟
        
    - هل الـ CVSS مناسب؟
        
    - هل الـ Evidence كافية؟
        
    - هل خطوات إعادة الاستغلال (Reproduction) واضحة؟
        
3. **Manager** يراجع اللغة والشكل العام.
    
4. يطلع **Final Report** ويتبعت للعميل.
    

وده السبب إن التقرير الاحترافي ممكن ياخد يوم أو يومين مراجعة، رغم إن الاختبار نفسه خلص. لأن التقرير هو المنتج النهائي اللي العميل بيدفع مقابله، ولازم يكون بنفس جودة الشغل التقني.


------
# Layer 4

## Components of a Report

## مكونات تقرير الـ Penetration Test

التقرير مش مجرد شوية Screenshots وكام Command.

التقرير هو المنتج النهائي (Deliverable).

يعني العميل مش اشترى منك إنك تعمل nmap أو تستغل RCE.

العميل اشترى:

- تحليل
    
- تقييم للمخاطر
    
- شرح للمشاكل
    
- حلول
    
- ترتيب أولويات الإصلاح
    

وده كله بيتجمع في التقرير.

---

المؤلف بيقول:

> التقرير لازم يكون فيه كل حاجة ليها قيمة.

يعني مينفعش تحط حاجات مالهاش لازمة.

مثال غلط:

تحط 80 صفحة Output بتاع nmap.

مين هيقراهم؟

ولا حد.

الأصح؟

تلخص.

مثلاً:

```
Found 17 hosts.

5 Critical
4 High
8 Informational
```

ولو محتاج الـ Output الكامل تحطه Appendix.

---

## الهدف من التقرير

التقرير بيجاوب العميل على 4 أسئلة:

1- إيه المشاكل؟

---

2- قد إيه المشاكل دي خطيرة؟

---

3- إزاي استغليتها؟

---

4- أعمل إيه عشان أصلحها؟

---

## Prioritizing Our Efforts

يعني:

ازاي نرتب أولوياتنا أثناء الـ Pentest.

ودي من أكتر الحاجات اللي المبتدئين بيغلطوا فيها.

---

تخيل إنك عملت

```
Nmap

Nessus

Nikto

BloodHound

Gobuster
```

وفجأة لقيت:

٢٠٠٠ نتيجة.

هل كلهم مهمين؟

لأ.

فيه:

False Positives

وفيه:

Informational

وفيه:

Critical

لازم تعرف تفرق.

---

مثلاً:

Nessus قالك:

```
SSL uses TLS1.0
```

دي Vulnerability.

لكن هل هتديك Shell؟

لأ.

---

وفي نفس الوقت لقيت:

```
Remote Code Execution
```

أكيد هتجري ورا الـ RCE الأول.

---

يعني ترتيب الأولويات غالباً:

```
RCE

↓

SQL Injection

↓

Authentication Bypass

↓

Privilege Escalation

↓

Sensitive Data

↓

Misconfiguration

↓

Info Findings
```

---

## Noise

Noise يعني دوشة.

يعني نتائج كتير ملهاش قيمة.

مثلاً:

Nessus طلعلك

```
40 SSL Findings
```

هل هتقعد تحقق في الأربعين؟

لأ.

تقدر تكتب Finding واحدة اسمها:

```
Weak SSL Configuration
```

وتقول:

Affected:

35 Hosts

بدل ما تعمل 35 Finding.

---

## لازم يكون عندك Process

يعني كل مرة تشتغل بنفس الخطوات.

مثلاً:

```
Scan

↓

Filter

↓

Validate

↓

Exploit

↓

Document
```

مش كل مرة تخترع طريقة.

---

## الخبرة مهمة

المؤلف بيقول:

المبتدئ ساعات يقعد

5 ساعات

يجرب Exploit.

وفي الآخر يطلع Fake.

بينما واحد خبرة يبص يقول:

```
دي False Positive.
```

في دقيقة.

---

عشان كده متتكسفش تسأل Senior.

وده طبيعي جداً.

---

## Writing an Attack Chain

ودي من أجمل أجزاء التقرير.

---

Attack Chain يعني:

رحلة الاختراق.

يعني تحكي للعميل:

أنا بدأت منين...

ووصلت لإيه...

خطوة خطوة.

---

يعني بدل ما تقول:

```
وجدنا 7 Vulnerabilities.
```

لأ.

قول:

```
بدأت بدون أي صلاحيات

↓

خدت Password

↓

دخلت Domain User

↓

عملت Kerberoasting

↓

بقيت Local Admin

↓

سرقت Ticket

↓

عملت DCSync

↓

بقيت Domain Admin
```

العميل هنا بيشوف الصورة كاملة.

---

ليه الـ Attack Chain مهمة؟

لأن أحياناً المشكلة لوحدها متبقاش خطيرة.

لكن لما تربطها بغيرها...

تبقى كارثة.

---

مثال

Finding 1

```
Weak Password
```

Medium.

Finding 2

```
SMB Signing Disabled
```

Medium.

لكن الاتنين مع بعض؟

Domain Compromise.

يبقوا عملياً High أو Critical.

---

الـ Attack Chain بتوضح ده.

---

## مثال الـ HTB

السيناريو كله بيقول:

بدأنا من User عادي.

ووصلنا لـ Domain Admin.

إزاي؟

---

## Step 1

Responder

التستر شغل:

```
Responder
```

عشان يلقط

NTLM Hash

---

لقى:

```
bsmith
```

---

## Step 2

Hashcat

كسر الـ Hash

وطلع Password.

دلوقتي بقى عنده:

Domain User.

---

## Step 3

Bloodhound

شاف العلاقات جوه الـ Domain.

مين Admin؟

مين يقدر يدخل فين؟

مين عنده Sessions؟

---

## Step 4

شاف Account اسمه

```
mssqlsvc
```

وعنده SPN.

يبقى ينفع عليه:

Kerberoasting.

---

## Step 5

جاب الـ TGS Ticket.

---

## Step 6

كسرها بـ Hashcat.

طلع Password.

---

## Step 7

دخل SQL Server.

---

## Step 8

طلع LSA Secrets.

لقى Password تاني.

```
srvadmin
```

---

## Step 9

دخل بيه Server تاني.

لقى User اسمه:

```
pramirez
```

عامل Login.

---

## Step 10

استعمل Rubeus.

وسرق الـ TGT.

---

## Step 11

عمل

```
Pass The Ticket
```

وبقى pramirez.

---

## Step 12

شاف إن

pramirez

عنده

```
DCSync Rights
```

---

## Step 13

شغل

```
Mimikatz
```

وعمل:

```
lsadump::dcsync
```

---

## Step 14

جاب Hash بتاع

Administrator.

---

## Step 15

دخل كـ

Administrator.

---

## Step 16

عمل

```
Secretsdump
```

وسحب كل Password Hashes.

---

دي كلها اسمها

Attack Chain.

---

لاحظ حاجة مهمة جداً.

هو مش مجرد بيقول:

```
عملت كذا.
```

لا.

كل خطوة معاها:

- Screenshot
    
- Command
    
- Output
    

يعني أي حد يراجع التقرير يقدر يتأكد.

---

## Writing a Strong Executive Summary

ودي أهم صفحة في التقرير كله.

ليه؟

لأن غالباً:

الـ CEO

ولا الـ CFO

ولا المدير التنفيذي

مش هيقرأ باقي التقرير.

هيقرأ صفحتين.

ويقفل.

---

فلو الـ Executive Summary وحش...

التقرير كله راح.

---

مين بيقرأه؟

- CEO
    
- CTO
    
- CIO
    
- Board
    
- مديرين
    
- Finance
    

يعني ناس غالباً مش Technical.

---

يبقى ممنوع تقول:

```
Kerberoasting
```

قول:

بدلها:

> تمكن المهاجم من سرقة بيانات المصادقة الخاصة بحسابات الخدمات ثم استخراج كلمات المرور الخاصة بها.

---

بدل:

```
Pass the Ticket
```

قول:

> استخدم بيانات المصادقة المسروقة للوصول إلى أنظمة أخرى دون الحاجة لمعرفة كلمة المرور.

---

## الكاتب بيقول

افتكر دايماً:

لو والدتك أو والدك مش فاهمين الكلام...

يبقى اكتب أبسط.

---

## Do

## 1)

خليك محدد.

متقولش

```
Several
```

قول:

```
23 Servers
```

---

## 2)

خليه Summary.

مش رواية.

من صفحة لصفحتين.

---

## 3)

اشرح وصلت لإيه.

بدل

```
Domain Admin
```

قول:

> أصبح بإمكان المهاجم الوصول إلى ملفات الموارد البشرية والأنظمة البنكية ورسائل البريد.

---

## 4)

قول الحلول العامة.

مش:

```
Install KB5004237
```

لا.

قول:

> تطوير عملية إدارة التحديثات.

---

## Don't

## متقولش

اشتري:

```
CrowdStrike
```

أو

```
Splunk
```

إنت مش Sales.

---

## متستخدمش Acronyms

بدل

```
LLMNR
```

اشرحها.

---

## متستخدمش كلمات معقدة

اكتب بسيط.

---

## متخلّيش التنفيذي يروح يدور في التقرير

مينفعش تكتب:

```
See Finding #8.
```

هو مش هيروح.

---

## Vocabulary Changes

دي جميلة جداً.

يعني بدل المصطلحات التقنية.

مثلاً:

VPN

بدلها

```
وسيلة للوصول الآمن إلى الأنظمة عن بعد
```

---

Password Spraying

بدل

```
Password Spraying
```

قول

```
محاولة استخدام كلمة مرور شائعة على عدد كبير من الحسابات
```

---

Password Cracking

بدل

```
Cracking
```

قول

```
تحويل كلمة المرور المشفرة إلى شكلها الحقيقي باستخدام قوة الحوسبة
```

---

SQL Injection

بدلها

```
إرسال بيانات غير متوقعة للتطبيق مما يسمح للمهاجم بتنفيذ أوامر أو الوصول إلى بيانات غير مصرح بها
```

---

OSINT

بدلها

```
جمع معلومات متاحة للعامة عن الشركة وموظفيها
```

---

## Anatomy of Executive Summary

يعني:

إزاي كتب الـ Executive Summary؟

---

أول حاجة:

جمع كل Findings.

مثلاً:

- Kerberoasting
    
- Weak Passwords
    
- File Shares
    
- Weak Credentials
    

---

بعدها بدأ يدور على Pattern.

لاحظ إن:

ولا واحدة بسبب Patch.

كلهم بسبب:

```
Misconfiguration
```

يعني المشكلة الأساسية:

Configuration Management ضعيف.

ودي الرسالة اللي عايز يوصلها.

---

## Summary of Recommendations

بعد الـ Executive Summary.

تحط جدول:

Short-term

Medium-term

Long-term

---

مثال:

Short

```
Disable LLMNR
```

---

Medium

```
Enable LAPS
```

---

Long

```
Create Secure Configuration Baselines
```

---

يعني العميل يبقى عنده Roadmap واضحة للإصلاح بدل ما يحتار يبدأ منين.

---

## Findings

بعد كده يبدأ الجزء التقني.

كل Vulnerability ليها صفحة أو أكثر، وفيها عادةً:

- اسم الثغرة.
    
- مستوى الخطورة.
    
- الوصف.
    
- التأثير (Impact).
    
- خطوات إعادة الاستغلال (Reproduction Steps).
    
- الأدلة (Screenshots / Commands).
    
- الأنظمة المتأثرة.
    
- طريقة الإصلاح (Remediation).
    
- مراجع مثل CVE أو CWE إذا كانت مناسبة.
    

وده الجزء اللي الفرق التقنية عند العميل هتعتمد عليه لإصلاح المشاكل.

---

## Appendices (الملاحق)

دي معلومات إضافية بتدعم التقرير من غير ما تزحمه.

## Static Appendices (ثابتة)

بتكون موجودة تقريبًا في كل تقرير:

- **Scope:** إيه اللي كان داخل نطاق الاختبار.
    
- **Methodology:** المنهجية اللي اتبعتوها أثناء الـ Pentest.
    
- **Severity Ratings:** إزاي بتحدد إن الثغرة Low أو Medium أو High أو Critical.
    
- **Biographies:** نبذة عن الأشخاص اللي نفذوا الاختبار لإثبات خبرتهم، خصوصًا في تقارير الامتثال مثل PCI.
    

---

## Dynamic Appendices (حسب المشروع)

ودي بتختلف من تقرير للتاني، زي:

- كل الـ Payloads اللي استخدمتها.
    
- الحسابات اللي اتعمل لها Compromise.
    
- أي Configuration غيرته أثناء الاختبار.
    
- قائمة كبيرة بالأجهزة المتأثرة لو كانت أطول من إنها تتحط داخل الـ Finding.
    
- نتائج الـ OSINT في الاختبارات الخارجية.
    
- تحليل كلمات المرور لو وصلت لـ Domain Admin وعملت Password Audit.
    

---

## اختلاف أنواع التقارير

المؤلف بيأكد إن مش كل التقارير شكلها واحد.

- **Internal Pentest:** هيكون فيه Attack Chain، وحركة داخل الشبكة، وامتيازات، وActive Directory.
    
- **External Pentest:** هيهتم أكثر بالخدمات المكشوفة، والـ OSINT، والمنافذ المفتوحة، وقد لا يكون فيه Attack Chain لو مفيش اختراق داخلي.
    
- **Web Application Assessment:** هيكون تركيزه على ثغرات الويب مثل حقن قواعد البيانات، وXSS، وOWASP Top 10.
    
- **Red Team أو Physical Assessment:** غالبًا يُكتب بشكل قصصي (Narrative) يوضح تسلسل العملية بالكامل.
    

لذلك، من الأفضل يكون عندك Templates جاهزة لكل نوع Assessment، بحيث متبدأش من الصفر كل مرة.

---

## الخلاصة اللي لازم تطلع بيها

أي **Pentest Report** احترافي غالبًا هيكون بالترتيب ده:

1. **Overview / Scope** — تعريف بالمشروع ونطاق الاختبار.
    
2. **Executive Summary** — ملخص بسيط لغير التقنيين.
    
3. **Attack Chain** (لو ينطبق) — رحلة الاختراق من البداية للنهاية.
    
4. **Summary of Recommendations** — خارطة طريق للإصلاح (قصير، متوسط، طويل المدى).
    
5. **Technical Findings** — شرح كل ثغرة بالتفصيل مع الأدلة والإصلاح.
    
6. **Appendices** — الملاحق مثل الـ Scope، والمنهجية، والـ Payloads، والحسابات المخترقة، وتحليل كلمات المرور.
    

وده يعتبر الهيكل القياسي اللي هتشوفه في أغلب شركات الـ Cyber Security والـ Consulting الكبيرة.


------
# Layer 5

## How to Write Up a Finding

يعني إزاي تكتب الـ Vulnerability نفسها داخل التقرير.

التقرير بيتقسم لأجزاء، لكن أهم جزء هو **Findings**.

يعني بدل ما تكتب

> لقيت Kerberoasting

لا.

لازم تشرح:

- إيه هي؟
    
- ليه خطيرة؟
    
- أثرت على مين؟
    
- إزاي كررتها؟
    
- أصلحها إزاي؟
    

وده اسمه Finding.

---

## الكاتب بيقول

> The Findings section is the "meat."

يعني دي "لحمة التقرير".

كل اللي قبله مجرد مقدمة.

أما هنا بقى أنت بتثبت إنك فعلاً عملت Pentest.

---

هو بيقول

> This is where we get to show off what we found

يعني هنا بتوري العميل شغلك.

مش علشان تتفاخر.

لكن علشان أي حد من فريق الـ IT يقدر يعيد نفس الخطوات ويتأكد إن المشكلة موجودة.

---

## كل Finding لازم يحتوي على إيه؟

---

## 1) Description

وصف المشكلة.

يعني تشرح:

المشكلة دي إيه؟

مثلاً

Weak Kerberos Authentication

ماينفعش تكتب

> Kerberoasting exists.

لا.

تكتب مثلاً

> توجد حسابات Service Accounts تستخدم Kerberos بطريقة تسمح لأي Domain User بطلب Ticket ثم محاولة كسر الباسورد Offline.

يعني تشرح المشكلة نفسها.

---

## كمان تقول

بتأثر على إيه؟

مثلاً

- Windows Server
    
- Active Directory
    
- Apache
    
- Tomcat
    
- SQL Server
    

---

## 2) Impact

دي أهم حاجة.

العميل عايز يعرف

طيب لو سيبتها...

هيحصل إيه؟

مثلاً

بدل ما تقول

> This is dangerous.

قول

> المهاجم يقدر يحصل على باسورد Service Account وبالتالي يعمل Privilege Escalation ويوصل Domain Admin.

يبقى شرحت الخطر.

---

## 3) Affected Systems

يعني الأجهزة المتأثرة.

مثلاً

```
DC01
SQL01
WEB01
```

أو

```
192.168.1.15
```

أو

```
Entire Domain
```

---

## 4) Recommendation

يعني أصلحها إزاي.

وده أهم جزء بعد الـ Impact.

---

بدل ما تقول

```
Fix the issue.
```

قول

```
Enable AES encryption

Rotate passwords

Use gMSA

Disable RC4

Increase password length
```

يعني خطوات واضحة.

---

## 5) References

يعني لينكات للمراجع.

مثلاً

Microsoft

MITRE

OWASP

NIST

مش تروح تجيب Blog عشوائي.

---

## 6) Reproduction Steps

دي أهم حاجة.

إزاي كررت المشكلة؟

يعني خطوة بخطوة.

---

مثلاً

```
1- Run Responder

2- Capture NTLMv2 Hash

3- Crack with Hashcat

4- Login using credentials
```

وبتحط Screenshots.

---

## Optional Fields

ممكن تضيف

---

## CVE

لو المشكلة ليها CVE.

مثلاً

```
CVE-2021-44228
```

---

## OWASP

مثلاً

```
A01 Broken Access Control
```

---

## MITRE ATT&CK

مثلاً

```
T1558 Kerberoasting
```

---

## CVSS Score

يعني درجة الخطورة.

مثلاً

9.8

---

## Ease of Exploitation

هل سهلة؟

ولا محتاجة خبرة؟

---

## Probability

هل غالباً هتحصل؟

ولا صعب؟

---

## Showing Finding Reproduction Steps

دي نقطة مهمة جداً.

الكاتب بيقول:

متفترضش إن العميل فاهم أدواتك.

يعني إيه؟

---

أنت شايف

```
Responder
```

حاجة عادية.

هو ممكن أول مرة يسمع عنها.

---

يعني متحطش Screenshot كبير وخلاص.

لا.

قسم كل خطوة.

---

مثلاً

## Figure 1

تشغيل Responder

---

بعدها

اكتب فقرة.

اشرح فيها.

```
قام المختبر بتشغيل Responder للاستماع إلى طلبات LLMNR.
```

---

بعدها

Figure 2

ظهر الـ Hash.

---

بعدها

اشرح.

---

بعدها

Figure 3

Hashcat.

---

بعدها

اشرح.

---

يعني كل Screenshot لوحده.

---

## الكاتب بيقول

Don't explain everything in captions.

يعني متكتبش تحت الصورة قصة.

اكتب الشرح في Paragraph.

---

## لو الأداة محتاجة Setup

مثلاً Metasploit.

بدل ما تصور النتيجة فقط.

صور

```
show options
```

وبعدين

```
exploit
```

علشان العميل يعرف الإعدادات.

---

## اقترح أدوات بديلة

مثلاً

أنت استخدمت

```
Hashcat
```

قول

برضو ممكن تستخدم

```
John the Ripper
```

---

استخدمت

Responder

قول

Inveigh

ممكن يعمل نفس الشغل.

---

## متستخدمش Screenshot لما النص أهم

دي نقطة ناس كتير بتغلط فيها.

---

مثلاً

عملت SQL Injection.

ومتصور Burp.

طيب هو هيكتب الـ Payload إزاي؟

مش هيعرف.

---

الأفضل

تحط الـ Payload كنص.

```
' OR 1=1 --
```

أسهل Copy/Paste.

---

## خلي الدليل قابل للدفاع

ودي من أهم الجمل في السيكشن.

Defensible Evidence.

يعني لو العميل قال

أنا مش مصدق.

لازم يبقى عندك دليل.

---

مثال.

أنت بتقول

Basic Authentication.

---

لو صورت Login Popup بس.

ده مش دليل.

ده بيثبت إن فيه Login.

---

لكن لو صورت

Wireshark

وشفت

Authorization:

وفيها

```
username:password
```

يبقى خلاص.

الدليل كامل.

---

مثال تاني.

أنت بتقول

لقيت صفحة Admin.

---

لو صورت الصفحة فقط.

ممكن تكون صورة من Google.

---

لكن لو صورت

الـ URL

أو

```
ipconfig
```

أو

```
ifconfig
```

يبقى أثبت إنها بتاعة العميل.

---

## اهتم بشكل الصور

الكاتب بيقول

اقفل

Bookmarks Bar

وشيل Extensions الغريبة.

ليه؟

تخيل العميل لقى عندك Extension اسمها

```
Free Movies Downloader
```

أو

```
Hack Facebook
```

شكل غير احترافي.

---

## Effective Remediation

ودي نقطة ناس كتير بتبوظ فيها.

---

## Bad

```
Configure Registry.
```

بس.

---

طب فين؟

إزاي؟

إيه القيمة؟

---

## Good

```
HKEY_LOCAL_MACHINE\....

Change

X

to

Y
```

يعني خطوات واضحة.

---

وكمان يقول

جرب الأول على أجهزة Test.

ليه؟

علشان متوقع إن تعديل Registry ممكن يكسر الدنيا.

وده احترافي.

---

## ليه أكتب التفاصيل؟

الكاتب بيقول ليها فايدتين.

---

## الأولى

أنت هتتعلم.

كل Report هتزود خبرتك.

---

## الثانية

العميل هيحب شغلك.

لأنك وفرت عليه ساعات بحث.

---

## Example 2

---

## Bad

اشتري المنتج الفلاني.

مثلاً

```
Install CrowdStrike.
```

---

العميل ممكن ميكونش معاه فلوس.

---

الأفضل

قول

فيه حل مجاني.

وفيه حل مؤقت.

وفيه Tool تجاري لو الميزانية تسمح.

سيب القرار للعميل.

---

## Selecting References

يعني تختار مراجع محترمة.

---

يفضل

Microsoft

OWASP

MITRE

NIST

Vendor Documentation

---

ومتحطش

Blog شخصي.

---

ومتحطش

مقال 40 صفحة.

---

ومتحطش

موقع كله Ads.

---

ومتحطش

Reference وراه Paywall.

---

## Example Findings

الكاتب وريك Examples جاهزة.

لاحظ إنها كلها فيها:

---

Description

↓

Impact

↓

Affected Hosts

↓

Remediation

↓

References

↓

Severity

---

يعني كل Finding نفس القالب.

---

## Poorly Written Finding

بعدها وريك مثال سيئ.

المشكلة كانت:

---

Formatting وحش.

---

CVSS فاضي.

---

الوصف ضعيف.

---

الـ Impact مبهم.

---

Remediation غامضة.

---

الـ Reader بعد ما يخلص

هيقول

طيب...

إيه المشكلة؟

وأصلحها إزاي؟

---

وده أسوأ Report ممكن تكتبه.

---

#$ Hands-on Practice

HTB عامل Tool اسمه

WriteHat.

وده معمول مخصوص لكتابة Reports.

تقدر تضيف فيه Findings.

وتولد Report كامل.

وتعمل Database للـ Findings.

وده شبيه بأدوات كتير الشركات بتستخدمها.

---

## الخلاصة المهمة جدًا

أي **Finding** احترافية لازم تجاوب على 6 أسئلة أساسية:

1. **إيه المشكلة؟** (Description)
    
2. **ليه خطيرة؟** (Impact)
    
3. **مين متأثر بيها؟** (Affected Assets)
    
4. **إزاي أثبت إنها موجودة؟** (Reproduction Steps + Evidence)
    
5. **أصلحها إزاي؟** (Remediation)
    
6. **فين المراجع الرسمية؟** (References)
    

ولو التزمت بالقالب ده في كل Vulnerability، هتطلع Reports منظمة وسهلة الفهم سواء لفريق الـ IT أو للإدارة، وده من أهم المهارات اللي بتميز الـ Penetration Tester المحترف.

# Layer 6
الجزئين دول من أهم أجزاء موديول **Reporting** في HTB CPTS، ولو استوعبتهم كويس هتكتب تقارير احترافية مش مجرد "أرفقت سكرين شوت وخلاص".  
ده ملخص مركز مع أهم النقاط اللي لازم تفتكرها للامتحان والشغل.

---

## 1. أثناء الـ Pentest ابدأ تكتب التقرير

أكبر غلطة إنك تخلص الـ Pentest وبعدها تبدأ التقرير.

الصح:

- أثناء الـ Scans اكتب بيانات العميل
    
- أثناء الـ Enumeration سجل النتائج
    
- أول ما تلاقي Vulnerability ابدأ تكتب الـ Finding
    
- خد Screenshots وقتها
    
- سجل Commands
    
- اكتب الـ Attack Chain
    

في الآخر هيبقى عليك مجرد مراجعة.

---

## 2. استخدم Templates

متبدأش تقرير من الصفر كل مرة.

اعمل Template جاهز فيه:

- Cover
    
- TOC
    
- Executive Summary
    
- Findings
    
- Appendices
    
- Contacts
    
- Scope
    

وكمان اعمل Template لكل نوع Assessment:

- Internal
    
- External
    
- Web
    
- Mobile
    
- Cloud
    

---

## 3. متستخدمش تقرير قديم وتعدله

بدل ما تاخد تقرير Client A وتغير اسمه.

ممكن تنسى:

- اسم العميل
    
- IPs
    
- Domain
    
- صور
    
- Findings
    

وده يعتبر كارثة احترافية.

استخدم Blank Template فقط.

---

## 4. اعمل Findings Database

بعد كام Assessment هتلاحظ إنك بتكتب نفس الـ Findings.

بدل كل مرة تكتبها من أول وجديد.

اعمل Database فيها:

مثلاً

Weak Password Policy

Description

Impact

Recommendation

References

وبعدين وقت التقرير تخصصها للعميل.

---

## 5. Reporting Tools

أشهر الأدوات:

Free

- Ghostwriter
    
- Dradis
    
- VECTR
    
- WriteHat
    

Paid

- PlexTrac
    
- AttackForge
    
- Rootshell Prism
    

وظيفتها:

- إدارة Findings
    
- Generate Reports
    
- Templates
    
- CVSS
    
- References
    
- PDF Generation
    

---

## 6. Word Tips

من أهم النصائح:

---

## استخدم Styles

بدل ما تعمل:

Bold

Size 20

Color Blue

كل مرة

اعمل Style اسمه

Heading 1

ولو غيرته مرة هيتغير في التقرير كله.

---

## استخدم Table Styles

نفس الفكرة.

---

## استخدم Captions

بدل

Figure 1

Figure 2

تكتبهم بإيدك.

Word هيعملهم أوتوماتيك.

ولو ضفت صورة جديدة هيرقمهم لوحده.

---

## Page Numbers

ضرورية جداً.

عشان العميل يقول:

راجع صفحة 18.

---

## Table of Contents

اعملها Auto.

---

## Bookmarks

تستخدمها في:

Hyperlinks

Macros

Jumping

---

## Custom Dictionary

لو دايماً بتغلط في كلمة.

Word يصلحها أوتوماتيك.

---

## Ignore Spell Check للكود

متخليش Word يعتبر

ipconfig

nmap

Responder

Hashcat

أخطاء لغوية.

---

## Custom Numbering

للـ Findings

مثلاً

Finding 1

Finding 2

Finding 3

---

## 7. Hotkeys

مهمة:

Ctrl + S

Save

---

Ctrl + A

Select All

---

F9

Update TOC

---

F4

كرر آخر Action

---

Ctrl + Alt + S

Split Window

---

Shift + F5

ارجع لآخر تعديل.

---

## 8. Automation

اعمل Macros.

مثلاً أول ما تفتح التقرير.

يسألك:

Client Name

Assessment Type

Date

Scope

ويملأ التقرير كله.

---

أو

يحذف Sections مش محتاجها.

---

## 9. Tell a Story

التقرير مش مجرد Vulnerabilities.

المفروض يحكي:

بدأت منين

وصلت لإيه

ليه ده خطر

إزاي استغليته

إيه النتيجة

---

## 10. Evidence

لا تزود Screenshots بدون داعي.

ولا تقلل.

كل Screenshot لازم يخدم هدف.

---

## 11. وضح الصور

استخدم:

- Arrows
    
- Boxes
    
- Highlights
    

عشان العميل يعرف تبص على إيه.

---

## 12. اخفي البيانات الحساسة

امسح:

- Passwords
    
- Hashes
    
- API Keys
    
- Tokens
    
- Secrets
    

استخدم Obfuscation.

مش Blur.

---

## 13. نظف Output الأدوات

مثلاً CrackMapExec بيكتب:

(Pwn3d!)

ممكن تشيله لأنه شكله غير احترافي.

---

## 14. راجع Hashcat

ممكن يطلع كلمات بذيئة من الـ Wordlist.

غيرها قبل التقرير.

---

## 15. راجع التقرير

قبل ما تبعته:

Grammar

Formatting

Fonts

Alignment

Spelling

Consistency

---

## 16. Screenshot احترافي

الميزة:

✔ واضحة

✔ مقصوصة صح

✔ مش Transparent

✔ مش فيها Discord

✔ مش فيها Desktop

✔ مش فيها Bookmarks

✔ Prompt محترم

بدل

```
azzkicker@root
```

خليها

```
tester@assessment
```

---

## 17. Backup

اعمل Backup للنوتس.

ومتخزنش كل حاجة على VM واحدة.

---

## 18. Automation

أي حاجة بتكررها:

اعملها Script.

---

## 19. Client Communication

طول الـ Engagement لازم تفضل تتواصل مع العميل.

---

## Start Notification

تبعتها أول يوم.

وتكتب:

- اسم الـ Tester
    
- Scope
    
- Source IP
    
- Dates
    
- Contacts
    

---

## Stop Notification

آخر كل يوم.

تقول:

خلصنا النهارده.

وأحياناً:

High-Level Findings

وموعد التقرير.

---

## لو لقيت Critical Vulnerability

زي:

SQL Injection

RCE

Domain Admin

لا تستنى التقرير.

بلغ العميل فوراً.

---

## لو السيرفر وقع

بلغ العميل.

متحاولش تخبي.

---

## لو خرج Scope جديد

مثلاً Subdomain جديدة.

اسأل العميل يدخلها ولا لأ.

---

## 20. احتفظ بالLogs

لو العميل قال:

إنت عملت Scan الساعة كام؟

لازم تعرف تثبت.

---

## 21. QA Process

كل تقرير لازم يراجع.

يفضل:

Author

↓

Technical Reviewer

↓

Formatting Reviewer

↓

Client

---

## 22. متراجعش تقريرك لوحدك

أفضل حاجة:

شخص تاني يراجعه.

لو مش موجود.

سيبه يوم كامل.

وارجع اقرأه.

---

## 23. QA Checklist

اعمل Checklist.

مثلاً:

☐ Grammar

☐ Spelling

☐ CVSS

☐ References

☐ Screenshots

☐ Captions

☐ Findings Numbering

☐ TOC Updated

☐ Executive Summary

☐ Client Name

☐ Scope

☐ Dates

☐ Recommendations

☐ Sensitive Data Redacted

☐ PDF Tested

---

## 24. استخدم Track Changes

أي تعديل يحصل.

يبقى ظاهر.

---

## 25. Draft ثم Final

الترتيب المعتاد:

Assessment

↓

Draft Report

↓

Client Review

↓

Meeting

↓

Questions

↓

Final Report

---

## 26. Report Review Meeting

بعد ما العميل يقرأ التقرير.

اعمل Meeting.

اشرح:

- Findings
    
- Impact
    
- Exploitation
    
- Recommendations
    

وأجاوب على الأسئلة.

---

## 27. بعد انتهاء المشروع

احتفظ بـ:

- Notes
    
- Evidence
    
- Reports
    
- Screenshots
    
- Logs
    

حسب سياسة الشركة.

---

## أهم النصائح الذهبية للامتحان وللشغل

- اكتب التقرير أثناء الاختبار، وليس بعده.
    
- استخدم Templates وFindings Database لتوفير الوقت.
    
- خصّص كل Finding بما يناسب بيئة العميل، ولا تنسخها كما هي.
    
- قدّم أدلة واضحة وقابلة لإعادة التنفيذ (Reproducible Evidence).
    
- أخفِ أي بيانات حساسة مثل كلمات المرور والـ Hashes والـ Tokens.
    
- استخدم أسلوبًا احترافيًا في الصور والمخرجات، وابتعد عن أي أسماء أو عبارات غير مناسبة.
    
- حافظ على تواصل مستمر مع العميل، خصوصًا عند اكتشاف ثغرات حرجة.
    
- مرّر التقرير عبر QA واحد على الأقل قبل تسليمه.
    
- سلّم نسخة **Draft** أولًا إذا كان ذلك ضمن عملية العمل، ثم أرسل النسخة **Final** بعد مراجعة العميل.
    
- التقرير هو المنتج النهائي الذي يراه العميل؛ جودة الكتابة والتنظيم لا تقل أهمية عن جودة الاختبار نفسه.

----
# Layer 7
Practice : 
الـ **Documentation & Reporting Practice Lab** ده يعتبر آخر تدريب عملي في موديول **Documentation & Reporting**، وهدفه إنه يخليك تشتغل كأنك Pentester في شركة حقيقية، مش مجرد تحل Box.

الفكرة إنك **مش مطلوب تكتشف الثغرات من الصفر**، لكن مطلوب تثبت إنك تعرف تعمل:

- Enumeration
    
- Evidence Collection
    
- Documentation
    
- Reporting
    

وده بالضبط اللي بيتقيم في امتحان **HTB CPTS**.

---

## السيناريو

أنت شغال في شركة اسمها:

> **Acme Security**

وعندكم عميل اسمه:

> **Inlanefreight**

كان فيه Pentester بدأ الـ Assessment لكن اضطر يمشي.

أنت هتكمل مكانه.

يعني هتلاقي:

- Notes
    
- Obsidian Notebook
    
- Folder Structure
    
- شوية Evidence
    
- Findings List
    

لكن مش كل الـ Findings متوثقة.

أنت مطلوب تكمل الشغل.

---

## Scope

```
172.16.5.0/24
```

والدومين

```
INLANEFREIGHT.LOCAL
```

---

## المطلوب

## 1) افتح الـ Notes

هتلاقي Obsidian فيه كل حاجة.

راجع:

```
Hosts

Users

Credentials

Loot

Attack Chain

Findings
```

---

## 2) شوف الـ Findings

هتلاقي مثلاً:

Finding 1

✓ Evidence

Finding 2

✗ ناقص

Finding 3

✗ ناقص

Finding 4

✓ موجود

...

إجمالي

13 Findings

---

## 3) ارجع استغل الثغرات

مثلاً لو مكتوب

```
Tomcat Weak Password
```

ارجع

```
hydra

manual login

Burp

curl
```

هات Evidence.

---

## 4) صور كل خطوة

مثلاً

```
nmap

↓

SMB

↓

enum4linux

↓

Responder

↓

NTLM

↓

Hashcat

↓

Password

↓

WinRM

↓

BloodHound

↓

DA
```

كل خطوة ليها Screenshot أو Output.

---

## 5) سجل كل الـ Commands

مثلاً

```bash
nmap

crackmapexec

bloodhound-python

netexec

evil-winrm

secretsdump.py

hashcat
```

كلها تتحفظ.

---

## 6) استخدم Tmux Logging

الموديول عايزك تتعود عليه.

مثلاً

```
tmux

pipe-pane

tee logs.txt
```

هيحفظ كل Terminal Output.

بدل ما تعمل Copy Paste.

---

## 7) اعمل Payload Log

مثلاً

```
Responder

SQL Payloads

PowerShell Payloads

Kerberoast Commands

Hashcat Commands

Impacket Commands
```

---

## 8) احتفظ بكل Scan Output

مثلاً

```
nmap

Rustscan

LDAP

SMB

DNS

Bloodhound

Kerberos
```

---

## 9) حدث الـ Obsidian

كل Host

كل User

كل Credential

كل Hash

كل Attack

كل خطوة

---

## 10) اكتب Findings

مثلاً

---

Description

Impact

Affected Hosts

Recommendation

References

Evidence

Reproduction

---

كل Finding يبقى كامل.

---

## 11) استخدم WriteHat

أو

Template Word

أو الاتنين.

الفكرة تتعلم.

---

## الهدف الحقيقي

هم مش مهتمين إنك تجيب DA فقط.

هم مهتمين تعرف توثق.

يعني لو جبت

```
Domain Admin
```

وكتبت

```
Got DA.
```

فده تقرير سيئ.

لكن لو كتبت

```
Enumeration

↓

SMB Shares

↓

Credentials

↓

Kerberoast

↓

Hashcat

↓

WinRM

↓

Privilege Escalation

↓

DA

↓

Impact

↓

Recommendations

↓

Evidence
```

فده تقرير احترافي.

---

## ليه اللاب مهم؟

لأنه أقرب حاجة لامتحان CPTS.

في الامتحان هتعمل تقريبًا نفس الخطوات:

- Enumeration
    
- Exploitation
    
- Evidence
    
- Notes
    
- Report
    

---

## نصيحتي قبل امتحان CPTS

لو هتدخل الامتحان قريب، اعمل اللاب ده بجد وكأنك في بيئة عميل:

1. اعمل Folder Structure منظم:
    
    ```
    Scans/
    Loot/
    Screenshots/
    Findings/
    Evidence/
    Report/
    Notes/
    Payloads/
    Logs/
    ```
    
2. استخدم Obsidian أو أي أداة تدوين ملاحظات وسجل كل خطوة أولًا بأول.
    
3. خُد Screenshot أو احتفظ بالـ Terminal Output لكل استغلال ناجح.
    
4. اكتب Draft لكل Finding أثناء الاختبار، ولا تؤجل الكتابة للنهاية.
    
5. في النهاية، راجع التقرير كما لو كنت الـ QA: تحقق من الأدلة، الإملاء، التنسيق، وإخفاء أي بيانات حساسة.
    

إذا التزمت بالطريقة دي في اللاب، هتكون قريب جدًا من أسلوب العمل المطلوب في بيئة احترافية وفي امتحانات HTB التي تتطلب تقريرًا كاملًا.