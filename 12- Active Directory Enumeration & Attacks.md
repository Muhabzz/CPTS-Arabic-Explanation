# Layer 1
## أولًا: يعني إيه Active Directory (AD)؟

تخيل إنك عندك شركة فيها:

- 500 موظف
    
- 1000 جهاز كمبيوتر
    
- طابعات
    
- سيرفرات
    
- ملفات
    
- صلاحيات
    
- إيميلات
    

لو كل جهاز بيتدار لوحده، هتبقى كارثة.

هنا بيجي دور **Active Directory**.

## تعريفه

Active Directory أو اختصارًا **AD** هو نظام عملته Microsoft علشان يدير كل الشركة من مكان واحد.

يعني بدل ما تروح لكل جهاز تغير الباسورد أو تضيف يوزر...

كل ده بيتعمل من سيرفر واحد.

يعني يعتبر:

> هو قاعدة بيانات كبيرة فيها كل معلومات الشركة.

زي:

- الموظفين
    
- الأجهزة
    
- الجروبات
    
- الصلاحيات
    
- الشيرد فولدرز
    
- الطابعات
    
- السيرفرات
    

---

## اتعمل إمتى؟

بيقول:

> officially implemented in 2000 with Windows Server 2000

يعني ظهر رسميًا سنة 2000 مع Windows Server 2000.

ومن وقتها كل نسخة ويندوز سيرفر كانت بتضيفله Features جديدة.

---

## هو مبني على إيه؟

بيقول:

> AD is based on x.500 and LDAP

يعني AD معتمد على بروتوكولات قديمة اسمها

- X.500
    
- LDAP
    

---

## يعني إيه LDAP؟

دي من أهم الحاجات.

LDAP = Lightweight Directory Access Protocol

ببساطة...

هو البروتوكول اللي بيخليك تسأل الـ Active Directory.

يعني بدل ما تقول

"فين الموظف أحمد؟"

أنت بتبعت LDAP Query.

مثال:

```
هاتلي كل اليوزرز

```

أو

```
هاتلي اليوزر Mohab

```

أو

```
مين في جروب Domain Admins؟

```

يبقى LDAP هو لغة الكلام مع الـ AD.

---

## كلمة Distributed معناها إيه؟

بيقول

> distributed

يعني البيانات مش شرط تبقى على سيرفر واحد.

ممكن يبقى عندك:

القاهرة

↓

Domain Controller

والإسكندرية

↓

Domain Controller

والاتنين متزامنين.

---

## Hierarchical Structure

يعني البيانات مترتبة في شكل شجرة.

مثلاً

```
Company

    Egypt

        IT

            Ahmed

            Ali

        HR

            Sara

    UAE

        IT
		        Karim

```

كل حاجة تحت حاجة.

زي فولدرات.

---

## Centralized Management

دي أهم ميزة.

يعني بدل ما تعدي على 1000 جهاز...

كل حاجة من مكان واحد.

مثلاً:

تغير باسورد موظف

↓

مرة واحدة

يقفله الإيميل

↓

مرة واحدة

تمسحه

↓

مرة واحدة

---

## Resources يعني إيه؟

بيقول

Resources

ويقصد:

أي حاجة الشركة بتملكها.

زي

Users

↓

الموظفين

Computers

↓

الأجهزة

Groups

↓

الجروبات

Network Devices

↓

راوترات وسويتشات

File Shares

↓

الفولدرات المشتركة

Group Policies

↓

سياسات الويندوز

Devices

↓

أي أجهزة

Trusts

↓

العلاقات بين Domains.

---

## يعني إيه Trust؟

دي مهمة جدًا.

لو عندك شركتين

```
Company A

Company B

```

وعامل بينهم Trust

يبقى يوزر من الشركة الأولى ممكن يدخل موارد الشركة التانية حسب الصلاحيات.

وده هتشوفه كتير في الاختراق.

---

## Authentication

بيقول

AD provides Authentication

يعني التأكد إنك مين.

مثلاً

أنت كتبت

```
Mohab

Password123

```

الـ AD بيقول

هل فعلاً ده Mohab؟

لو آه

يبقى دخل.

---

## Authorization

غير Authentication.

Authentication

↓

مين أنت؟

Authorization

↓

تعمل إيه؟

مثال

Mohab

↓

مسموح يفتح HR Folder؟

لا

مسموح يفتح IT Folder؟

آه

---

## Accounting

يعني تسجيل كل العمليات.

مثلاً

Mohab عمل Login

↓

اتسجل.

فتح File

↓

اتسجل.

غير باسورد

↓

اتسجل.

---

## ليه إحنا نهتم بالـ AD؟

بيقول

Microsoft Active Directory حوالي 43% من سوق الشركات.

يعني تقريبًا نص الشركات الكبيرة شغالة بيه.

وده معناه...

لو عايز تبقى Pentester

أو Red Teamer

لازم تعرف AD.

---

## Azure AD

بيقول

Microsoft blending with Azure AD

يعني Microsoft بقت تربط الـ Active Directory التقليدي مع الـ Cloud.

دلوقتي اسمه غالبًا Microsoft Entra ID.

---

## CVE

بيقول

Microsoft has over 2000 CVEs

يعني فيه أكتر من 2000 ثغرة منشورة.

---

يعني إيه CVE؟

Common Vulnerabilities and Exposures

رقم بيميز كل ثغرة.

زي

```
CVE-2021-34527

```

ودي PrintNightmare.

---

## ليه الـ AD بيتخترق بسهولة؟

بيقول

مش لأنه وحش.

لكن لأنه ضخم جدًا.

فيه:

Users

Computers

Permissions

Services

DNS

LDAP

Kerberos

SMB

GPO

Certificates

Delegation

Trusts

....

فغلط صغير

↓

يبقى Domain كله وقع.

---

## Misconfiguration

يعني سوء إعداد.

مثلاً

User واخد صلاحيات زيادة.

أو

Folder Everyone Full Control.

أو

Service Account باسورده ضعيف.

كل دي Misconfigurations.

---

## Enumeration

دي أهم كلمة في الموديول.

Enumeration

يعني

جمع معلومات.

مش اختراق.

لسه.

يعني أعرف:

- اليوزرز
    
- السيرفرات
    
- الجروبات
    
- الدومين
    
- الصلاحيات
    

---

## Native Tools

يعني أدوات موجودة أصلًا في ويندوز.

مش محتاج تنزل حاجة.

---

## Sysinternals

دي مجموعة Tools من Microsoft.

زي

PsExec

Autoruns

Process Explorer

---

## WMI

Windows Management Instrumentation

تقدر تسأل الويندوز عن أي حاجة.

مثلاً

```
كام رامات؟

```

```
إيه البرامج؟

```

```
مين Logged in؟

```

---

## DNS

عارفه.

لكن في الـ AD ليه دور ضخم.

لأن الأجهزة بتلاقي بعض عن طريق DNS.

---

## Password Spraying

ودي هتسمعها كتير.

مش معناها أجرب مليون باسورد على يوزر واحد.

دي اسمها Brute Force.

Password Spraying

↓

باسورد واحد

على كل اليوزرز.

مثلاً

```
Welcome123

```

على

Ahmed

Ali

Sara

Mohab

...

علشان متعملش Lockout.

---

## Kerberoasting

واحدة من أشهر هجمات الـ AD.

الفكرة ببساطة:

فيه Service Accounts.

تقدر تطلب Ticket ليهم.

وبعدين تكسر الـ Ticket Offline.

ولو الباسورد ضعيف

↓

عرفت الباسورد.

---

## Responder

أداة بتسرق NetNTLM Hashes.

بتستنى أي جهاز يطلب Authentication.

وتاخد الـ Hash.

---

## Kerbrute

بتستخدمه تعرف

هل Username موجود؟

بدون Password.

---

## BloodHound

أهم Tool في AD تقريبًا.

بيعمل Map.

ويرسم العلاقات.

مثلاً

```
Mohab

↓

Member Of

↓

IT Support

↓

GenericAll

↓

Server01

↓

Session

↓

Domain Admin

```

ويقولك

أهو الطريق اللي هيوصلك للدومين أدمن.

---

## الهدف من Pentest في AD

بيقول

مش شرط Domain Admin.

ممكن العميل يقولك:

هاتلي:

- Database
    
- Email
    
- Server معين
    
- File Share
    

أو

هاتلي Domain Admin.

---

## Foothold

يعني أول رجل ليك جوه الشركة.

مثلاً

اخترقت جهاز واحد.

ده اسمه

Foothold.

---

## Lateral Movement

يعني تتحرك أفقيًا.

من جهاز

↓

جهاز.

---

## Vertical Movement

يعني تطلع صلاحيات.

User

↓

Local Admin

↓

Server Admin

↓

Domain Admin.

---

## Living Off The Land

ودي مهمة جدًا.

يعني تستخدم أدوات ويندوز نفسها.

بدل

Mimikatz

تستخدم

PowerShell

أو

wmic

أو

net

أو

dsquery

علشان الـ AV ميكشفكش.

---

## ليه لازم تتعلم Manual Enumeration؟

لأن الأدوات ممكن:

- تقع
    
- تتمنع
    
- الـ AV يمنعها
    
- العميل يمنع رفع ملفات
    

فساعتها لازم تعرف تعمل كل حاجة بإيدك.

---

## Scenario 1

بيقول:

اخترق جهاز.

أخد SYSTEM.

## يعني SYSTEM؟

أعلى صلاحية على الجهاز.

أعلى من Administrator.

---

بعدها عمل Enumeration.

ملقاش حاجة.

فجرب Kerberoasting.

جاب Tickets.

كسرها بـ Hashcat.

---

## Hashcat

أداة كسر Password Hashes.

---

لقى Password.

لكن اليوزر مش مهم.

عمل إيه؟

استغل صلاحياته على File Share.

ورمى ملفات SCF.

---

## SCF File

ملف لما حد يفتحه

يحاول يعمل Authentication.

فتطلع الـ Hash للـ Attacker.

---

شغل Responder.

استنى.

لقى Hash.

طلع Domain Admin.

خلصت.

---

## Scenario 2

لقى SMB NULL Session.

---

## SMB

بروتوكول مشاركة الملفات.

---

## NULL Session

يعني دخل بدون Username أو Password.

وده Misconfiguration.

جاب:

Users

Password Policy

---

عرف:

Minimum Password

8

وعرف Complexity.

---

جرب Password Spraying.

لقى User.

---

بعدها BloodHound.

لقى Local Admin.

دخل الجهاز.

لقى Domain Admin فاتح Session.

---

استخدم

Rubeus.

---

## Rubeus

Tool للـ Kerberos.

استخرج TGT.

---

## TGT

Ticket Granting Ticket.

دي أول Ticket بتاخدها لما تعمل Login.

---

بعدها عمل

Pass The Ticket.

---

## Pass The Ticket

بدل الباسورد

تستخدم الـ Ticket نفسه.

---

وبعدين سيطر على دومين تاني بسبب Trust.

---

## Scenario 3

كل الطرق فشلت.

راح استخدم

Kerbrute.

طلع Username صحيح.

---

جاب Usernames من LinkedIn.

يعني الموظفين.

---

عمل Password Spraying.

لقى يوزر.

---

شغل BloodHound.

لقى كل الناس تقدر تعمل RDP.

---

## RDP

Remote Desktop.

يعني تدخل الجهاز كأنك قاعد قدامه.

---

دخل.

استعمل

DomainPasswordSpray.

ميزة الأداة إنها متقفّلش الحسابات (بتستبعد اللي قربت توصل لحد الـ Lockout).

---

لقى User في Help Desk.

Help Desk عنده

GenericAll.

---

## GenericAll

يعني تحكم كامل.

---

على Enterprise Key Admins.

ودي لها تحكم على Domain Controller.

---

أضاف نفسه.

وراح عامل

Shadow Credentials.

---

## Shadow Credentials

هجوم بيضيف Credential جديد للـ Account بدون ما يعرف الباسورد.

---

جاب NT Hash.

---

## NT Hash

الـ Hash بتاع باسورد الويندوز.

---

بعدها عمل

DCSync.

---

## DCSync

من أخطر هجمات الـ AD.

بتخدع الـ Domain Controller إنه يعملك Replication.

فيديك Hashes كل المستخدمين.

ومن ضمنهم Domain Admin.

---

## الرسالة الأساسية من المقدمة

المؤلف عايز يقولك 3 حاجات مهمين جدًا:

1. **الـ Enumeration أهم من الهجوم نفسه.** لو عرفت تجمع معلومات صح، غالبًا هتعرف توصل لهدفك بسهولة.
    
2. **الـ Active Directory مليان علاقات وصلاحيات معقدة.** أوقات حساب عادي جدًا يوصلك لـ Domain Admin بسبب Misconfiguration بسيطة.
    
3. **اتعلم الأساس قبل الأدوات.** BloodHound وResponder وKerbrute ممتازين، لكن لو الأداة وقعت أو اتمنعت، لازم تبقى فاهم إيه اللي بيحصل وتعرف تعمله بإيدك.
    

---

دي مجرد **المقدمة** للموديول. بعد كده كل Tool وكل Attack (زي Kerberoasting وBloodHound وPassword Spraying وDCSync) هيتشرح بالتفصيل العملي، وإزاي تستخدمه في اللابات.


----------------
# Layer 2
 الجزء ده عبارة عن **أدوات الشغل (Tools of the Trade)**، يعني الأدوات اللي أي **Pentester أو Red Teamer** بيستخدمها وهو بيشتغل على Active Directory. 
 
---

## أولًا: يعني Tools of the Trade؟

يعني:

> الأدوات الأساسية اللي هنستخدمها طول الموديول.

الموديول بيقول:

- لو بتشتغل من Windows هتلاقي الأدوات في:
    

```text
C:\Tools
```

- لو بتشتغل من Linux هيديك Parrot OS جاهز.
    

يعني مش هتقعد تنزل حاجة.

كل الأدوات موجودة.

---

## PowerView / SharpView

دي من أهم الأدوات.

## PowerView

عبارة عن PowerShell Script.

يعني بتشغله على Windows.

## SharpView

نفس PowerView

لكن معمول بلغة C#.

يعني Executable.

---

## بيعملوا إيه؟

يجمعوا معلومات عن الـ Active Directory.

مثلاً

- مين اليوزرز؟
    
- مين الأدمن؟
    
- مين واخد صلاحيات؟
    
- مين داخل دلوقتي؟
    
- مين عنده SPN؟
    
- مين ينفع نعمله Kerberoast؟
    

---

مثال

بدل ما تكتب

```powershell
net user
```

PowerView يجيبلك معلومات أكتر بكتير.

---

## ليه الناس بتحبه؟

لأنه بيشتغل باستخدام PowerShell.

وده يعتبر

Living Off The Land.

يعني مش محتاج تنزل Tool كبيرة.

---

## BloodHound

أشهر Tool في الـ AD.

ودي لازم تحفظها.

---

بدل ما يبقى عندك آلاف اليوزرز والجروبات...

BloodHound يعملهم Graph.

مثلاً

```text
Mohab

↓

Member Of

↓

IT Support

↓

GenericAll

↓

Server01

↓

Session

↓

Domain Admin
```

فيقولك

أهو الطريق اللي يخليك توصل لـ Domain Admin.

---

يعني هو مش بيخترق.

هو بيرسم العلاقات.

---

## SharpHound

ناس كتير بتتلخبط بينه وبين BloodHound.

لازم تفرق بينهم.

## SharpHound

هو Collector.

يعني يجمع المعلومات.

---

## BloodHound

هو Viewer.

يعني يعرض المعلومات.

---

تخيلهم بالشكل ده

```text
SharpHound

↓

يجمع البيانات

↓

JSON

↓

BloodHound

↓

يعرضها في Graph
```

---

SharpHound بيجمع

- Users
    
- Groups
    
- Sessions
    
- ACL
    
- GPO
    
- Computers
    

وغيرهم.

---

## BloodHound.py

دي نسخة Python.

---

ليه موجودة؟

لو أنت على Linux.

أو

الجهاز بتاعك مش داخل الدومين.

---

بدل SharpHound

تشغل

BloodHound.py

ويطلع نفس JSON تقريبًا.

---

## Kerbrute

أداة مكتوبة بلغة Go.

بتستخدم Kerberos.

---

بتعمل 3 حاجات.

## أولًا

User Enumeration.

يعني تعرف

هل اليوزر موجود؟

---

مثلاً

```text
Ahmed

Ali

Mohab

Sara
```

تجرب.

اللي موجود هيقولك.

---

## ثانيًا

Password Spray.

---

يعني

```text
Welcome123
```

على كل اليوزرز.

---

## ثالثًا

Brute Force.

لكن ده أقل استخدامًا.

---

## Impacket Toolkit

دي مش أداة.

دي مكتبة.

فيها أدوات كتير جدًا.

تقريبًا نص أدوات الـ AD جاية منها.

---

زي

```text
psexec.py

wmiexec.py

secretsdump.py

GetNPUsers.py

lookupsid.py

ticketer.py

...
```

---

كلهم Python.

---

## Responder

دي من أشهر الأدوات.

---

بتعمل

LLMNR Poisoning

NBT-NS Poisoning

MDNS Poisoning

---

يعني إيه Poisoning؟

يعني تخدع الأجهزة.

---

مثلاً

جهاز بيسأل

```text
فين السيرفر FILE01؟
```

Responder يرد

```text
أنا FILE01
```

الجهاز يبعتله Username والـ Hash.

---

وبالتالي

تسرق

NetNTLM Hash.

---

## Inveigh.ps1

Responder

لكن PowerShell.

---

بيستخدم على Windows.

---

## InveighZero

نسخة C#.

أسرع.

وأحسن في البيئات الحديثة.

---

## rpcinfo

RPC

يعني Remote Procedure Call.

---

الأداة دي تسأل الجهاز

إيه خدمات الـ RPC اللي شغالة؟

---

مثلاً

```bash
rpcinfo -p 10.0.0.1
```

هيقولك

- Port
    
- Service
    
- Protocol
    

---

## rpcclient

جزء من Samba.

بيستخدم RPC.

---

ومن خلاله تقدر

تجيب

Users

Groups

Policies

Shares

وغيرهم.

---

## CrackMapExec (CME)

دي من أقوى الأدوات.

ناس كتير بتسميها

Swiss Army Knife.

---

بتعمل

Enumeration

Authentication

Password Spray

Command Execution

Post Exploitation

---

بتشتغل على

SMB

WMI

WinRM

MSSQL

---

يعني Tool واحدة

بتعمل نص الشغل.

---

## Rubeus

أداة متخصصة في Kerberos.

---

بتعمل

Kerberoasting

Pass The Ticket

Pass The Key

TGT

TGS

S4U

Delegation

وغيرهم.

---

## GetUserSPNs.py

من Impacket.

---

بيجيب

Service Principal Names.

---

ليه؟

علشان تعمل

Kerberoasting.

---

## Hashcat

أشهر Password Cracker.

---

مثلاً

عندك

NTLM Hash

أو

Kerberos Hash

تحطه فيه.

يحاول يجيب الباسورد.

---

## enum4linux

أداة Enumeration قديمة.

---

بتجيب

Users

Shares

OS

Groups

Policy

من Samba أو Windows.

---

## enum4linux-ng

نسخة أحدث.

أسرع.

وأدق.

---

## ldapsearch

موجودة في Linux.

---

بتكلم LDAP مباشرة.

مثلاً

```text
هات كل اليوزرز
```

أو

```text
هات كل الجروبات
```

---

## windapsearch

سكريبت Python.

---

بيسهل كتابة LDAP Queries.

بدل ما تكتب LDAP معقد.

---

## DomainPasswordSpray.ps1

PowerShell Tool.

---

بيعمل Password Spray.

---

ميزته

يحترم Password Policy.

ويبعد عن Lockout.

---

# LAPSToolkit

أداة خاصة بـ

LAPS.

---

يعني

Local Administrator Password Solution.

---

LAPS

Microsoft بتخلي كل جهاز

له Local Admin Password مختلف.

---

الأداة دي تشوف

هل فيه مشاكل في إعدادات LAPS؟

---

# smbmap

بيجيب

كل SMB Shares.

---

ويقولك

دي Read

ولا Write

ولا No Access.

---

# psexec.py

من Impacket.

---

زي PsExec.

---

لو عندك Username وPassword

تدخل Shell.

---

# wmiexec.py

زي psexec

لكن باستخدام

WMI.

---

أوقات بيكون أقل Detect.

---

# Snaffler

اسمه غريب 😂

---

يدور في الشيرد فولدرز.

على

Passwords

VPN Files

Config Files

Certificates

Secrets

---

# smbserver.py

يشغل SMB Server عندك.

---

ليه؟

لو عايز تنقل ملف للويندوز.

---

بدل FTP.

---

# setspn.exe

أداة من Microsoft.

---

تقرأ

SPNs

أو تضيفها

أو تمسحها.

---

# Mimikatz

ملك أدوات الويندوز.

---

بيعمل

Pass The Hash

Pass The Ticket

Credential Dumping

LSASS Dump

Kerberos Extraction

Plaintext Passwords

Golden Ticket

Silver Ticket

تقريبًا أي حاجة.

---

# secretsdump.py

من Impacket.

---

يسحب

SAM

LSA Secrets

NTLM Hashes

من الجهاز.

---

# evil-winrm

لو WinRM مفتوح.

---

يديك Interactive Shell.

---

مفضل جدًا في الـ Labs.

---

# mssqlclient.py

يدخل على

Microsoft SQL Server.

---

ممكن تنفذ Commands.

أو تقرأ الداتا.

---

# noPac.py

Exploit مشهور.

---

بيستغل

CVE-2021-42278

CVE-2021-42287

---

علشان يرفع User عادي

إلى

Domain Admin.

---

# rpcdump.py

يعرض

RPC Endpoints.

---

بيفيد في Enumeration.

---

# CVE-2021-1675.py

PoC

لثغرة

PrintNightmare.

---

# ntlmrelayx.py

أداة Relay.

---

يعني بدل ما تكسر الـ Hash.

تنقله مباشرة لسيرفر تاني.

---

# PetitPotam.py

أداة بتجبر جهاز ويندوز

يبعت Authentication.

---

بعدها تعمل

NTLM Relay.

---

# gettgtpkinit.py

تتعامل مع

Certificates.

وتطلع

TGT.

---

# getnthash.py

لو معاك TGT.

تجيب

NT Hash.

---

# adidnsdump

يطلع كل

DNS Records

في الدومين.

---

زي

DNS Zone Transfer.

---

# gpp-decrypt

زمان

Group Policy

كانت بتحفظ Password مشفر.

---

الأداة دي

تفك التشفير.

---

# GetNPUsers.py

دي خاصة بـ

ASREPRoasting.

---

تجيب

AS-REP Hash

لليوزرز اللي

Kerberos Preauthentication

متقفلة عندهم.

---

بعدها

Hashcat.

---

# lookupsid.py

يعمل

SID Brute Force.

---

يعرف

Users

Groups

عن طريق SID.

---

# ticketer.py

يصنع

Kerberos Tickets.

---

زي

Golden Ticket

Silver Ticket.

---

# raiseChild.py

لو فيه

Child Domain

و

Parent Domain.

---

يحاول يرفع صلاحياتك

من Child

إلى Parent.

---

# Active Directory Explorer

برنامج GUI.

---

يفتحلك الـ AD

زي File Explorer.

---

تشوف

Users

Groups

ACL

Attributes

بسهولة.

---

ممكن كمان

تاخد Snapshot

للـ AD.

وتحلله Offline.

---

# PingCastle

من أشهر أدوات

Security Audit.

---

يطلع Report.

ويقولك

المخاطر الموجودة.

ويرتبها حسب الخطورة.

---

# Group3r

خاص بالـ GPO.

---

يدور على

Misconfigurations

داخل

Group Policy.

---

# ADRecon

يجمع معلومات ضخمة عن الدومين.

---

ويطلعها في

Excel.

---

فيه:

- Users
    
- Groups
    
- Computers
    
- Trusts
    
- GPO
    
- Password Policy
    
- ACL
    
- Delegation
    

وغيرهم.

مفيد جدًا لما تبقى عايز تعمل تقرير عن بيئة الـ Active Directory.

---

# ملخص سريع (احفظه)

|الأداة|وظيفتها الأساسية|
|---|---|
|**PowerView**|جمع معلومات عن الـ AD من PowerShell|
|**BloodHound**|رسم العلاقات واكتشاف مسارات الهجوم|
|**SharpHound**|جمع بيانات لـ BloodHound|
|**Kerbrute**|User Enumeration + Password Spraying|
|**Impacket**|مجموعة أدوات هجوم على بروتوكولات ويندوز|
|**Responder**|سرقة NetNTLM Hashes|
|**CrackMapExec**|Enumeration وهجمات متعددة على SMB/WMI/WinRM|
|**Rubeus**|هجمات Kerberos|
|**Hashcat**|كسر الـ Hashes|
|**Mimikatz**|استخراج كلمات المرور والتذاكر والهاشات|
|**evil-winrm**|Interactive Shell عبر WinRM|
|**secretsdump.py**|استخراج SAM وLSA وNTLM Hashes|
|**GetNPUsers.py**|تنفيذ ASREPRoasting|
|**GetUserSPNs.py**|تنفيذ Kerberoasting|
|**Snaffler**|البحث عن كلمات مرور وملفات حساسة داخل الـ Shares|
|**PingCastle**|تدقيق أمان بيئة الـ Active Directory|
|**ADRecon**|جمع معلومات شاملة وإخراجها في تقرير Excel|

💡 **نصيحة للمذاكرة:** مش مطلوب تحفظ كل الأوامر دلوقتي. ركز الأول على **وظيفة كل أداة**، ولما تبدأ اللابات العملية هتستخدم كل أداة في وقتها، وساعتها الأوامر هتثبت معاك تلقائيًا.


------
# Layer 3
 الجزء ده مهم جدًا لأنه بيحطك في **سيناريو حقيقي** كأنك شغال Pentester في شركة. يعني من أول هنا، الموديول مش هيبقى مجرد شرح أدوات، لأ، هيخليك تمشي في Assessment كامل خطوة بخطوة.

---

## Scenario

بيقول:

> We are Penetration Testers working for CAT-5 Security

يعني من دلوقتي اعتبر نفسك موظف في شركة اسمها

**CAT-5 Security**

ودي شركة بتقدم خدمات

- Penetration Testing
    
- Red Team
    
- Security Assessment
    

---

## بعدين بيقول

> After a few successful engagements

### يعني إيه Engagement؟

دي كلمة هتسمعها كتير في الشركات.

Engagement = مشروع أو عملية اختبار أمن كاملة.

يعني الشركة جالها عميل وقالها:

> تعالى اختبرلي الشبكة.

ده اسمه Engagement.

---

هو بيقول:

أنت اشتغلت مع الفريق في كام مشروع قبل كده.

وكان أداؤك كويس.

---

## shadowing with the team

يعني

كنت شغال مع Senior Pentester.

بتتفرج عليه.

وتساعده.

وتتعلم.

---

دلوقتي قالوا:

خلينا نشوف هتعرف تشتغل لوحدك ولا لأ.

---

## Team Lead

بيقول

> Team Lead sent us an email

يعني قائد الفريق بعتلك Email.

فيه المطلوب.

---

## Tasking Email

دي أهم حاجة.

هي فيها المطلوب منك في الاختبار.

---

## أول Task

> Domain Enumeration

يعني

اجمع معلومات عن الـ Domain.

وده أول خطوة في أي Pentest.

---

يعني تعرف

- اسم الدومين
    
- اليوزرز
    
- الجروبات
    
- السيرفرات
    
- الـ DC
    
- الـ Shares
    
- الـ Trusts
    
- الـ GPO
    
- Password Policy
    

---

## Credential Discovery

يعني

دور على Credentials.

يعني

Username

Password

Hash

Kerberos Ticket

Certificate

API Keys

Secrets

أي حاجة تدخل بيها.

---

## Lateral Movement

دي اتكلمنا عنها.

يعني

من جهاز

↓

جهاز تاني.

---

مثلاً

```text
PC01

↓

Server01

↓

FileServer

↓

DC
```

---

## Privilege Escalation

يعني

ترفع صلاحياتك.

مثلاً

```text
User

↓

Local Admin

↓

Server Admin

↓

Domain Admin
```

---

## Acquire Domain Admin Credentials

يعني

الهدف النهائي.

إنك تجيب Credentials بتاعة

Domain Admin.

مش شرط الباسورد.

ممكن

Hash

أو

Ticket.

---

## Findings will guide further actions

يعني

كل معلومة هتجمعها

هتحدد هتعمل إيه بعد كده.

وده مهم جدًا.

---

مثلاً

لقيت

```text
Password Never Expires
```

يبقى ممكن تعمل

Password Spray.

---

لقيت

SPN.

يبقى

Kerberoasting.

---

لقيت

Sessions.

يبقى

Pass The Ticket.

---

## This module will allow us to practice

يعني

كل اللي هنتعلمه

هنطبقه.

---

## Final Assessment

دي الامتحان النهائي.

---

هيخليك تعمل

Internal Penetration Test

مرتين.

---

## أول مرة

بيقول

> Starting from an external breach position

يعني

كأنك Hacker

اخترقت الشركة من بره.

ودخلت جهاز.

---

يبقى البداية

جهاز واحد.

---

بعدها

تحاول توصل للدومين.

---

## ثاني مرة

بيقول

> attack box inside the internal network

يعني

العميل مديلك

جهاز

جوه الشركة.

---

يعني أنت بالفعل داخل الشبكة.

---

وده بيحصل فعلًا.

مثلاً

شركة تقول

"احنا عاوزين نعرف لو موظف خبيث موجود جوه الشركة."

---

## Skills Assessment

يعني

الامتحان العملي.

---

لما تخلصه

يبقى أنت عرفت

- Enumeration
    
- Exploitation
    
- Privilege Escalation
    
- Lateral Movement
    

---

## Automated and Manual

دي نقطة مهمة.

بيقول

مش عايزينك تعرف تشغل Tools بس.

لا.

عايزينك تعرف تعمل الحاجة بإيدك.

---

يعني

BloodHound

كويس.

لكن تعرف تجيب نفس المعلومات بـ LDAP؟

---

Responder

كويس.

لكن فاهم هو بيعمل إيه؟

---

## Attack Concepts

يعني

طرق الهجوم.

---

مش مجرد Commands.

لكن

ليه بنستخدمها؟

وإمتى؟

---

## Interpret Data

دي من أهم مهارات الـ Pentester.

يعني

تعرف تفسر البيانات.

---

مثلاً

جبت Users.

طيب بعدين؟

---

جبت Sessions.

طيب تعمل بيها إيه؟

---

جبت ACL.

طيب مين Vulnerable؟

---

دي اسمها

Interpretation.

---

## Assessment Scope

دي من أهم الوثائق.

---

Scope

يعني

إيه المسموح تختبره.

---

وده قانونيًا مهم جدًا.

---

	## In Scope

يعني

مسموح.

---

## أول حاجة

```text
INLANEFREIGHT.LOCAL
```

ده

Main Domain.

---

وفيه

- Active Directory
    
- Web Services
    

---

## ثاني حاجة

```text
LOGISTICS.INLANEFREIGHT.LOCAL
```

Subdomain.

---

يعني

دومين تابع للدومين الأساسي.

---

## ثالث حاجة

```text
FREIGHTLOGISTICS.LOCAL
```

شركة تابعة.

---

بيقول

> Subsidiary Company

يعني

شركة مملوكة للشركة الأساسية.

---

## External Forest Trust

دي مهمة جدًا.

---

يعني

فيه Trust

بين

```text
INLANEFREIGHT

↓

FREIGHTLOGISTICS
```

---

وده معناه

لو اخترقت واحدة

ممكن تروح للتانية.

---

وده هتشوفه بعدين.

---

## 172.16.5.0/23

ده

Subnet.

---

يعني

كل الأجهزة

اللي IP بتاعها

في الرينج ده

مسموح تختبرها.

---

## Out Of Scope

يعني

ممنوع.

---

مثلاً

أي دومين تاني.

---

أي Subdomain تاني.

---

أي IP مش مكتوب.

---

# ممنوع تعمل

Phishing.

---

يعني

مينفعش تبعت Email مزيف.

---

ولا

Social Engineering.

---

يعني

متتصلش بالموظفين.

---

ولا تخدع حد.

---

# Real Website

بيقول

ممنوع

تهاجم

```text
inlanefreight.com
```

---

ليه؟

لأنه

موقع حقيقي.

---

مسموح فقط

Passive Enumeration.

---

# Passive Enumeration

يعني

جمع معلومات

بدون لمس السيرفر.

---

زي

Google

LinkedIn

GitHub

WHOIS

DNS

Certificate Transparency

Shodan

Archive.org

---

كل ده

Passive.

---

## Active Enumeration

عكسه.

---

يعني

Port Scan

Nmap

Dirsearch

Nikto

Gobuster

Burp

---

كل ده

يبعت Packets.

---

وده ممنوع.

---

## Internal Testing

ده الجزء العملي.

---

بيقول

هنختبر

الأجهزة الداخلية.

---

خصوصًا

Active Directory.

---

## Emulate Attack

يعني

نحاكي

هاكر حقيقي.

---

مش مجرد

Run Tool.

---

# Untrusted Insider Perspective

يعني

اعتبر نفسك

موظف عادي.

---

مش Admin.

---

مش معاك Passwords.

---

ولا أي معلومات.

---

وده أقرب للحقيقة.

---

# No advance information

يعني

مش هيدوك

Network Diagram.

---

ولا Users.

---

ولا Password.

---

أنت هتكتشف كل حاجة.

---

# Goal

الهدف.

---

أولًا

Get Domain User.

---

يعني

جيب أي User.

---

بعدها

Enumeration.

---

بعدها

Foothold.

---

يعني

امسك جهاز.

---

بعدها

Lateral Movement.

---

بعدها

Vertical Movement.

---

لحد

Domain Admin.

---

# Computer systems will not be interrupted

يعني

مينفعش

توقع الشبكة.

---

ولا تعمل

Denial of Service.

---

ولا تمسح ملفات.

---

ولا توقف Services.

---

لأن الهدف

اختبار

مش تخريب.

---

# Password Testing

بيقول

لو لقينا Hashes.

---

مسموح

ناخدها

ونكسرها

Offline.

---

## Offline Cracking

يعني

تاخد الـ Hash.

---

تروح

على جهازك.

---

وتشغل

Hashcat.

---

مش على سيرفر العميل.

---

وده أسرع.

وأأمن.

---

# Confidentiality

بيقول

أي Password

هنعرفه

مش هيتقال

لحد بره الفريق.

---

وده مهم جدًا.

---

كل الداتا

تتحفظ

بشكل آمن.

---

# ليه ورانا الـ Scope ده؟

بيقول

علشان

تتعود.

---

لأن أي شغل Pentest

هيبقى فيه

- Scope
    
- Rules of Engagement (RoE)
    
- NDA
    
- Timeline
    
- Objectives
    

---

## يعني إيه Rules of Engagement (RoE)؟

دي "قواعد الاشتباك".

يعني وثيقة بتحدد:

- إيه المسموح تعمله.
    
- إيه الممنوع تعمله.
    
- إمتى تشتغل.
    
- مين تبلغ لو لقيت مشكلة خطيرة.
    
- إزاي تتعامل مع البيانات اللي تجمعها.
    

وجودها بيحمي العميل وبيحمي فريق الاختبار قانونيًا.

---

# The Stage Is Set

دي جملة معناها

> كل حاجة بقت جاهزة.

---

يعني

عرفنا

- الهدف
    
- الـ Scope
    
- الأدوات
    
- القوانين
    

---

دلوقتي هنبدأ

أول مرحلة.

---

# Passive External Enumeration

ودي أول خطوة.

---

هنجمع معلومات

من بره الشركة.

بدون

أي Scan.

---

زي ما أي Hacker هيبدأ.

---

# ملخص السيناريو كله

تخيل نفسك دخلت أول يوم شغل في شركة **CAT-5 Security**، ومدير الفريق قالك:

> "قدامك عميل اسمه **Inlanefreight**. دي حدود الشغل (Scope)، ودي قواعد الاختبار (RoE). مطلوب تبدأ من الصفر، تجمع معلومات عن البيئة، تلاقي أي بيانات دخول، تدخل الشبكة، تتحرك بين الأجهزة، ترفع صلاحياتك، وفي الآخر توصل إلى **Domain Admin**—كل ده من غير ما تخرج برا النطاق المسموح أو تعطل أنظمة العميل."

وده بالضبط هو السيناريو اللي هتمشي عليه طوال الموديول. كل أداة وهجوم هتتعلمه بعد كده هيكون هدفه تنفيذ واحدة من المراحل دي لحد ما تنهي الـ Assessment بالكامل.


----
# Layer 4
## External Recon and Enumeration Principles

أول كلمة هنا:

## External

يعني **من بره الشركة**.

لسه مخدتش Access.

لسه معندكش User.

لسه مدخلتش الشبكة.

---

## Recon

Recon اختصار

**Reconnaissance**

يعني

> استطلاع أو استكشاف.

زي الجيش قبل الحرب.

قبل ما يدخل المعركة.

يبعت ناس تشوف:

- في كام جندي؟
- فين الأسلحة؟
- فين المداخل؟

إحنا بنعمل نفس الكلام.

---

## Enumeration

دي خطوة بعد الـ Recon.

الـ Recon بيقول

> أعرف إن فيه سيرفر.

الـ Enumeration يقول

> طب السيرفر ده عليه إيه؟  
> مين اليوزرز؟  
> إيه الخدمات؟

يعني Enumeration = جمع معلومات بالتفصيل.

---

## Before kicking off any pentest...

بيقول

قبل ما تبدأ أي Penetration Test...

اعمل External Recon.

---

## ليه؟

الموديول قال 3 أسباب.

---

## 1) Validate Information

يعني

**تتأكد إن المعلومات اللي العميل اداهالك صح.**

مثلاً

العميل قالك

```
Domain:
company.local
```

أنت تتأكد.

---

أو قال

```
Website

company.com
```

تتأكد.

---

ليه؟

لأن أوقات العميل نفسه بيبقى ناسي.

أو فيه Subdomain جديد.

---

## 2) Ensure Scope

دي مهمة جدًا.

يعني

تتأكد إنك مش بتهاجم حاجة برا الـ Scope.

---

مثلاً

الشركة مستضافة على AWS.

وعلى نفس السيرفر

شركة تانية.

---

لو عملت Scan غلط.

ممكن تضرب الشركة التانية.

وده Illegal.

---

عشان كده لازم تعرف

مين بتاع العميل

ومين مش بتاعه.

---

## 3) Looking for Public Information

يعني

تشوف

هل فيه معلومات موجودة على الإنترنت؟

---

زي

Passwords

Emails

Documents

GitHub

Leaks

Credentials

---

كل دي ممكن تساعدك.

---

## Lay of the Land

الجملة دي معناها

> افهم البيئة الأول.

زي واحد رايح بلد جديدة.

أول حاجة

يبص على الخريطة.

---

إحنا بنعمل نفس الكلام.

---

## Information Leaks

يعني

تسريب معلومات.

---

مثلاً

موظف رفع

```
config.php
```

على GitHub.

---

جواه

Password.

---

أو

رفع PDF.

---

الميتاداتا فيها

```
Username

Mohab.Nasser
```

---

كل ده Information Leak.

---

## Username Format

دي نقطة مهمة جدًا.

---

الشركات كلها عندها Naming Convention.

مثلاً

```
Mohab Nasser
```

يبقى

```
mohab.nasser
```

أو

```
mnasser
```

أو

```
mn
```

---

لو عرفتها.

هتعرف تعمل Password Spray.

---

## GitHub

ليه بندور فيه؟

---

لأن Developers أوقات يرفعوا

```
Password

API Key

Token

AWS Secret
```

بالغلط.

---

وده بيبقى Jackpot.

---

## Intranet

يعني

الموقع الداخلي للشركة.

---

مثلاً

```
intranet.company.local
```

---

مش بيظهر للعامة.

لكن ممكن PDF يكون فيه Link ليه.

---

## Enterprise Environment

يعني

بيئة الشركة.

---

يعني

إيه السيرفرات؟

إيه البرامج؟

إيه الدومين؟

إيه الأمن؟

---

## What Are We Looking For?

هنا بيقولك

إحنا بندور على إيه؟

---

## أول حاجة

## IP Space

يعني

كل الـ IPs

بتاعة الشركة.

---

زي

```
192.168.x.x

172.16.x.x

10.x.x.x
```

أو Public IP.

---

## ASN

يعني

Autonomous System Number.

---

كل شركة كبيرة

بيبقى ليها رقم على الإنترنت.

---

زي

Google

Amazon

Microsoft

---

لو الشركة صغيرة

غالبًا

هتبقى مستضافة على AWS.

---

## Netblocks

يعني

رينجات الـ IP.

---

مثلاً

```
134.209.24.0/24
```

---

يعني

كل الـ IPs

دي تبع الشركة.

---

## Cloud Presence

يعني

الشركة على

AWS؟

Azure؟

Google Cloud؟

DigitalOcean؟

---

وده مهم جدًا.

---

## Hosting Provider

يعني

مين مستضيف الموقع.

---

مثلاً

Cloudflare.

---

AWS.

---

Azure.

---

## DNS Records

كل البيانات

بتاعة الدومين.

---

زي

A Record

MX

TXT

NS

CNAME

---

#0# Domain Information

يعني

كل المعلومات

عن الدومين.

---

مين مالكه؟

---

مين بيديره؟

---

هل فيه

Subdomains؟

---

زي

```
vpn.company.com

mail.company.com

dev.company.com
```

---

## Public Services

يعني

الخدمات المفتوحة للعالم.

---

زي

Mail

VPN

Website

OWA

DNS

---

## Defenses

يعني

الشركة بتستخدم

إيه للحماية؟

---

SIEM

يعني

Security Monitoring.

---

AV

Antivirus.

---

IPS

Intrusion Prevention.

---

IDS

Intrusion Detection.

---

## Schema Format

دي من أهم الحاجات.

---

يعني

شكل اليوزر.

---

مثلاً

```
first.last
```

---

أو

```
flast
```

---

أو

```
firstl
```

---

لو عرفته.

هتعرف تولد آلاف اليوزرز.

---

## Password Policy

يعني

الشركة بتحط Password إزاي.

---

مثلاً

لازم

8 Characters.

---

Special Character.

---

Expiry.

---

History.

---

## Data Disclosures

يعني

ملفات الشركة المنشورة.

---

زي

PDF

DOCX

PPTX

XLSX

---

ليه؟

---

لأنها ممكن تحتوي

Metadata.

---

مثلاً

Author

Mohab.Nasser

---

أو

Link

```
https://sharepoint.company.local
```

---

أو

File Share.

---

## Breach Data

يعني

الشركة

اتسربت قبل كده؟

---

لو آه.

---

يمكن

Passwords

لسه شغالة.

---

## Where Are We Looking?

يعني

هندور فين؟

---

## ASN Registrars

زي

IANA

ARIN

RIPE

---

ودي تعرفك

مين مالك الـ IP.

---

## Domain Registrars

زي

ICANN

DomainTools

---

يعرفوك

مين مالك الدومين.

---

## Social Media

ليه؟

---

من LinkedIn

أعرف

Employees.

---

من Twitter

أعرف

Projects.

---

من Facebook

أعرف

Offices.

---

## Job Posts

دي كنز.

---

مثلاً

الشركة منزلة

Job

بيقول

```
SharePoint 2013
```

---

يبقى

لسه عندهم

SharePoint 2013.

---

وده قديم.

---

يبقى

أبدأ أدور

على ثغراته.

---

أو

بيقول

```
VMware Horizon
```

---

عرفت

بيستخدموا VMware.

---

أو

```
Fortinet
```

---

عرفت

نوع الفايروول.

---

## Company Website

الموقع الرسمي.

---

هنجيب منه

Emails

Phones

PDFs

Contacts

News

---

## Cloud Storage

زي

AWS S3

Azure Blob

GitHub

---

أوقات

يبقى Public بالغلط.

---

## Google Dorks

دي Search Queries

ذكية.

---

مثلاً

```
site:company.com filetype:pdf
```

---

أو

```
site:company.com ext:xlsx
```

---

أو

```
intext:"password"
```

---

كل دي

Google Dorks.

---

## Breach Sources

زي

HaveIBeenPwned.

---

ودي تقولك

الإيميل ده

اتسرب؟

---

## DeHashed

دي أقوى.

---

بتجيب

Email

Password

Hash

Database.

---

مثلاً

```
Mohab

↓

Password123
```

---

يمكن

لسه بيستخدمه.

---

## Finding Address Spaces

الموديول استخدم

Hurricane Electric

BGP Toolkit.

---

دي تعرف منها

الـ IPs.

---

# ليه مهم؟

---

علشان تعرف

إيه

بتاع العميل.

---

# Smaller Companies

الشركات الصغيرة

غالبًا

على AWS.

---

مش عندها

ASN.

---

# Scope

لو لقيت

IP

على AWS.

---

متهاجموش

إلا لو العميل قال.

---

# Third Party

يعني

شركة تانية.

---

ممكن تحتاج

Approval.

---

مثلاً

Oracle.

---

AWS.

---

Azure.

---

# DNS

الموديول بيقول

DNS

كنز.

---

ليه؟

---

ممكن تلاقي

Subdomains.

---

Mail.

---

VPN.

---

Internal Hostnames.

---

# Example

لقى

```
mail1.inlanefreight.com
```

---

يبقى فيه

Mail Server.

---

لقى

```
ns1
```

---

يبقى

DNS Server.

---

# nslookup

الأمر

```
nslookup ns1.domain.com
```

---

يسألك

الـ DNS.

---

ويرجع

الـ IP.

---

وده عمله

ولقى

IP جديد.

---

لكن

قال

متهجموش.

---

تأكد الأول

إنه

In Scope.

---

# Public Data

زي

LinkedIn.

---

Job Posts.

---

Facebook.

---

GitHub.

---

كلهم

OSINT.

---

# SharePoint Example

لقي

إعلان وظيفة.

---

بيطلب

SharePoint 2013.

---

يبقى

الشركة

لسه عندها

SharePoint.

---

وده

بيفيدنا.

---

# PDF Hunting

عمل

Google Dork

```
filetype:pdf inurl:inlanefreight.com
```

---

يعني

هات كل PDF.

---

ليه؟

---

الميتاداتا.

---

اللينكات.

---

الـ Author.

---

الـ Software.

---

كلها معلومات.

---

# نصيحة مهمة جدًا

الموديول قال:

أول ما تلاقي

أي ملف

نزله.

---

ليه؟

---

يمكن

يتحذف.

---

أو

تنسى مكانه.

---

احتفظ بكل الأدلة.

---

# Email Hunting

عمل

```
intext:"@inlanefreight.com"
```

---

طلعله

الإيميلات.

---

عرف

Naming Convention.

---

طلع

```
Emma.Williams

John.Smith

David.Jones
```

---

يبقى

الشركة

بتستخدم

first.last.

---

# Username Harvesting

يعني

تجمع Usernames.

---

من LinkedIn.

---

بأداة

linkedin2username.

---

وتطلع

```
first.last

flast

f.last

firstl
```

---

# Credential Hunting

باستخدام

DeHashed.

---

لقى

```
Roger

↓

Ilovefishing!
```

---

ولقى

```
Jane

↓

Starlight1982_!
```

---

هل لازم يشتغلوا؟

لا.

---

لكن

نجرب.

---

يمكن

اليوزر

لسه بيستخدم

نفس الباسورد.

---

# ليه كل ده مهم؟

المؤلف بيقول عن تجربة:

أوقات كنت مش عارف أدخل الشركة نهائي.

---

رجعت

لـ

Google

LinkedIn

GitHub

DeHashed

---

عملت Password Spray.

---

دخلت.

---

وده فعلاً بيحصل كتير.

---

# أهم جملة في الصفحة كلها

> **بمجرد ما تجيب Credentials حتى لو Domain User عادي، تقدر تعمل معظم عمليات الـ Active Directory Enumeration، بل وكمان تنفذ عدد كبير من الهجمات.**

يعني **أصعب مرحلة غالبًا هي إنك تجيب أول User**. بعد كده، الـ Active Directory بيفتحلك أبواب كتير جدًا: تقدر تجمع معلومات أكتر، تدور على Misconfigurations، وتبدأ تتحرك داخل الشبكة لحد ما توصل لهدفك.

---

## الخلاصة العملية (احفظ التسلسل ده)

أي Pentester محترف بيبدأ بالشكل ده:

1. **راجع الـ Scope** → أعرف المسموح والممنوع.
2. **اعمل Passive OSINT** → Google Dorks، LinkedIn، GitHub، DNS، WHOIS، BGP.
3. **اجمع Emails وUsernames** → اعرف Naming Convention.
4. **دور على ملفات ووثائق** → PDF، DOCX، PPTX، Metadata.
5. **ابحث عن Breach Data** → HaveIBeenPwned، DeHashed.
6. **استنتج معلومات مفيدة** → أنواع السيرفرات، البرامج، الخدمات، وسائل الحماية.
7. **كوّن Wordlists** → أسماء مستخدمين وكلمات مرور محتملة.
8. **بعد كده فقط** تبدأ الـ **Active Enumeration** والهجمات المسموح بيها داخل الـ Scope.