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

## LAPSToolkit

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

## smbmap

بيجيب

كل SMB Shares.

---

ويقولك

دي Read

ولا Write

ولا No Access.

---

## psexec.py

من Impacket.

---

زي PsExec.

---

لو عندك Username وPassword

تدخل Shell.

---

## wmiexec.py

زي psexec

لكن باستخدام

WMI.

---

أوقات بيكون أقل Detect.

---

## Snaffler

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

## smbserver.py

يشغل SMB Server عندك.

---

ليه؟

لو عايز تنقل ملف للويندوز.

---

بدل FTP.

---

## setspn.exe

أداة من Microsoft.

---

تقرأ

SPNs

أو تضيفها

أو تمسحها.

---

## Mimikatz

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

## secretsdump.py

من Impacket.

---

يسحب

SAM

LSA Secrets

NTLM Hashes

من الجهاز.

---

## evil-winrm

لو WinRM مفتوح.

---

يديك Interactive Shell.

---

مفضل جدًا في الـ Labs.

---

## mssqlclient.py

يدخل على

Microsoft SQL Server.

---

ممكن تنفذ Commands.

أو تقرأ الداتا.

---

## noPac.py

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

## rpcdump.py

يعرض

RPC Endpoints.

---

بيفيد في Enumeration.

---

## CVE-2021-1675.py

PoC

لثغرة

PrintNightmare.

---

## ntlmrelayx.py

أداة Relay.

---

يعني بدل ما تكسر الـ Hash.

تنقله مباشرة لسيرفر تاني.

---

## PetitPotam.py

أداة بتجبر جهاز ويندوز

يبعت Authentication.

---

بعدها تعمل

NTLM Relay.

---

## gettgtpkinit.py

تتعامل مع

Certificates.

وتطلع

TGT.

---

## getnthash.py

لو معاك TGT.

تجيب

NT Hash.

---

## adidnsdump

يطلع كل

DNS Records

في الدومين.

---

زي

DNS Zone Transfer.

---

## gpp-decrypt

زمان

Group Policy

كانت بتحفظ Password مشفر.

---

الأداة دي

تفك التشفير.

---

## GetNPUsers.py

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

## lookupsid.py

يعمل

SID Brute Force.

---

يعرف

Users

Groups

عن طريق SID.

---

## ticketer.py

يصنع

Kerberos Tickets.

---

زي

Golden Ticket

Silver Ticket.

---

## raiseChild.py

لو فيه

Child Domain

و

Parent Domain.

---

يحاول يرفع صلاحياتك

من Child

إلى Parent.

---

## Active Directory Explorer

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

## PingCastle

من أشهر أدوات

Security Audit.

---

يطلع Report.

ويقولك

المخاطر الموجودة.

ويرتبها حسب الخطورة.

---

## Group3r

خاص بالـ GPO.

---

يدور على

Misconfigurations

داخل

Group Policy.

---

## ADRecon

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

## ملخص سريع (احفظه)

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

## ممنوع تعمل

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

## Real Website

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

## Passive Enumeration

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

## Untrusted Insider Perspective

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

## No advance information

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

## Goal

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

## Computer systems will not be interrupted

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

## Password Testing

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

## Confidentiality

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

## ليه ورانا الـ Scope ده؟

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

## The Stage Is Set

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

## Passive External Enumeration

ودي أول خطوة.

---

هنجمع معلومات

من بره الشركة.

بدون

أي Scan.

---

زي ما أي Hacker هيبدأ.

---

## ملخص السيناريو كله

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

## ليه مهم؟

---

علشان تعرف

إيه

بتاع العميل.

---

## Smaller Companies

الشركات الصغيرة

غالبًا

على AWS.

---

مش عندها

ASN.

---

## Scope

لو لقيت

IP

على AWS.

---

متهاجموش

إلا لو العميل قال.

---

## Third Party

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

## DNS

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

## Example

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

## nslookup

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

## Public Data

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

## SharePoint Example

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

## PDF Hunting

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

## نصيحة مهمة جدًا

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

## Email Hunting

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

## Username Harvesting

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

## Credential Hunting

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

## ليه كل ده مهم؟

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

## أهم جملة في الصفحة كلها

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


# Layer 5
---

## أولًا: إحنا بنعمل إيه أصلًا؟

إنت داخل تعمل **Internal Penetration Test** على شركة اسمها:

> **Inlanefreight**

يعني الشركة سمحتلك تدخل جوه الشبكة الداخلية بتاعتها وتشوف لو فيه ثغرات.

الهدف مش إنك تخترق وخلاص.

الهدف إنك تعرف:

- الأجهزة الموجودة
    
- السيرفرات
    
- الـ Domain Controller
    
- المستخدمين
    
- الخدمات
    
- الثغرات
    
- إزاي تقدر تاخد أول Access
    

وده اسمه:

> Initial Enumeration

يعني أول مرحلة فى اختبار الاختراق.

---

## Setting Up

الجزء ده بيقول العميل ممكن يديلك البيئة بأكتر من شكل.

زى مثلًا:

---

## 1) Linux VM

يعنى يديلك VM جاهز جوه الشبكة.

زى Kali أو Parrot.

إنت هتدخل عليه SSH.

---

## 2) جهاز حقيقى

يحط جهاز صغير فى الشركة.

زى Raspberry Pi.

يوصل بالنت ويربط عندك VPN.

---

## 3) تروح الشركة بنفسك

توصل اللاب بتاعك فى سويتش الشركة.

---

## 4) AWS أو Azure VM

يعنى فيه سيرفر فى كلاود لكن داخل على الشبكة الداخلية.

---

## 5) VPN

يديك VPN تدخل بيه.

وده أقل صلاحيات شوية.

لأن فيه حاجات مش هتقدر تعملها زى:

LLMNR Poisoning

---

## 6) جهاز الموظف نفسه

يديك Windows Workstation.

تشتغل منه.

---

## Grey Box ولا Black Box؟

دى أنواع الاختبارات.

---

## Black Box

يعنى متعرفش أى حاجة.

زى الهاكر الحقيقى.

---

## Grey Box

يعطوك شوية معلومات.

زى:

Network Range

أو

IP Range

وده اللى حصل هنا.

---

## العميل إدالك إيه؟

العميل قالك:

عندك:

Linux VM

Windows VM

Network Range

```
172.16.5.0/23
```

وبس.

---

يعنى معرفكش:

- الدومين
    
- أسماء الأجهزة
    
- اليوزرز
    
- السيرفرات
    

كل ده هتكتشفه بنفسك.

---

## المطلوب منك

المطلوب تعمل Enumeration.

يعنى تعرف:

## Hosts

مين موجود؟

---

## Services

كل جهاز فاتح Ports إيه؟

---

## Vulnerabilities

فى ثغرات؟

---

## Users

مين موجود فى الدومين؟

---

## Domain Controller

فين؟

---

## ليه بنبدأ من غير Credentials؟

علشان ده واقعى.

لو هاكر دخل الشركة.

هيكون معاه Username؟

لا.

هيبدأ من الصفر.

---

## الحاجات المهمة اللى لازم تدورها عليها

الكاتب عامل جدول.

---

## AD Users

ليه؟

علشان بعدين تعمل

Password Spraying

---

## AD Joined Computers

زى

Domain Controller

File Server

Exchange

SQL

---

## Key Services

زى

Kerberos

LDAP

DNS

SMB

---

## Vulnerable Hosts

يعنى جهاز قديم.

أو عليه ثغرة.

---

## لازم يبقى عندك Methodology

يعنى متشتغلش عشوائى.

الكاتب بيقول:

لو دخلت Active Directory بدون خطة...

هتتايه.

لأن البيانات ضخمة جدًا.

---

فبيعمل ترتيب.

---

## الأول

Passive Enumeration

---

بعدها

Active Enumeration

---

بعدها

Analyze

---

بعدها

Attack

---

## Passive Enumeration

يعنى تجمع معلومات

بدون ما تكلم الأجهزة.

زى إنك تسمع الترافيك.

---

الأدوات:

Wireshark

tcpdump

Responder

---

## Wireshark

الكاتب قال:

شغل Wireshark.

```
sudo wireshark
```

---

ليه؟

علشان تسمع الشبكة.

---

إيه اللى ظهر؟

ARP

MDNS

---

## يعنى إيه ARP؟

ARP

هو بروتوكول بيقول:

> مين صاحب الـ IP ده؟

لو جهاز بيسأل:

```
مين عنده
172.16.5.25؟
```

يبقى فيه جهاز اسمه

172.16.5.25

موجود.

---

يبقى من غير ما تعمل Scan

عرفت Host موجود.

---

ظهر مثلًا:

```
172.16.5.5
172.16.5.25
172.16.5.50
```

---

## MDNS

ده بروتوكول Local Name Resolution.

يعنى بدل ما يقول:

```
172.16.5.125
```

يقول:

```
ACADEMY-EA-WEB01
```

فأنت كده عرفت:

اسم الجهاز.

---

وده مهم جدًا.

---

## لو مفيش GUI؟

استعمل:

tcpdump

```
sudo tcpdump -i ens224
```

---

وده بيعمل نفس الفكرة.

يسمع الترافيك.

---

## ليه نحفظ PCAP؟

علشان:

ترجعله بعدين.

يمكن تلاقى معلومات فاتتك.

وكمان تحطه فى التقرير.

---

## بعد كده استخدم Responder

Responder مشهور جدًا.

لكن هنا

مش بنعمل Poisoning.

---

احنا بنستخدم

Analyze Mode

```
sudo responder -I ens224 -A
```

لاحظ:

```
-A
```

يعنى

Analyze فقط.

---

يعنى:

يسمع.

لكن ميبعتش Responses.

---

وده آمن.

---

Responder اكتشف Hosts جديدة.

يبقى عمل Target List أكبر.

---

## بعد Passive

نبدأ Active

---

## باستخدام fping

```
fping -asgq 172.16.5.0/23
```

تعالى نشرح كل Flag.

---

### -a

اعرض الأجهزة الحية فقط

Alive

---

### -s

اعرض Statistics

---

### -g

Generate Range

يعنى

```
172.16.5.0/23
```

يبقى يعمل Scan لكل الـ Range.

---

### -q

Quiet

ميطبعش كل محاولة.

---

الناتج:

```
172.16.5.5

172.16.5.25

172.16.5.50
```

...

يعنى دول ردوا.

---

بعدها قال:

```
9 alive
```

يبقى فيه

9 أجهزة.

---

## بعد كده

Nmap

---

```
sudo nmap -A -iL hosts.txt
```

---

يعنى إيه؟

---

## -A

Aggressive Scan

وده بيعمل كذا حاجة مرة واحدة.

زى:

OS Detection

Version Detection

Scripts

Traceroute

---

## -iL

يعنى اقرأ الـ IPs

من ملف.

---

## -oN

احفظ النتيجة.

---

## النتيجة

شاف الجهاز:

```
172.16.5.5
```

فاتح Ports كتير.

---

## 53

DNS

---

## 88

Kerberos

---

وجود Kerberos مع LDAP

غالبًا

ده Domain Controller.

---

## 389

LDAP

---

## 636

Secure LDAP

---

## 445

SMB

---

## 3268

Global Catalog

---

## 3389

RDP

---

## 5357

HTTP API

---

## منين عرف إنه Domain Controller؟

بص على:

```
DNS:
ACADEMY-EA-DC01
```

وكمان:

```
LDAP
```

وكمان:

```
Kerberos
```

كلهم موجودين.

يبقى ده DC.

---

## Host تانى

```
172.16.5.100
```

لقى عليه:

IIS

SQL Server

SMB

---

لكن لاحظ:

```
Windows Server 2008
```

وده قديم جدًا.

---

إيه المشكلة؟

أنظمة قديمة.

يبقى ممكن تكون مصابة بثغرات قديمة.

زى:

- EternalBlue
    
- MS08-067
    
- BlueKeep
    

---

لكن الكاتب بيحذر.

متستغلهاش مباشرة.

لازم العميل يوافق.

لأن ممكن السيرفر يقع.

---

## بعد كده

بدأ يدور على Users

---

لأن مفيش Credentials.

---

هيستخدم

Kerbrute.

---

## Kerbrute

دى أداة

بتسأل الـ Domain Controller:

```
هل اليوزر ده موجود؟
```

---

من غير Password.

---

وده اسمه

Username Enumeration

---

الميزة؟

هادئة.

---

ليه؟

لأن

Kerberos Pre-auth Failures

غالبًا

مش بتتسجل فى Logs.

---

يبقى تقدر تجرب آلاف اليوزرز.

---

## حمل الأداة

```
git clone
```

---

بعدها

```
make all
```

---

علشان يبنى نسخة Linux

Windows

Mac

---

بعدها

```
mv
```

يحطها فى

```
/usr/local/bin
```

علشان تشتغل من أى مكان.

---

## الاستخدام

```
kerbrute userenum
```

---

```
-d
```

اسم الدومين

---

```
--dc
```

IP بتاع Domain Controller

---

بعدها

```
jsmith.txt
```

Wordlist

---

طلع:

```
VALID USERNAME
```

```
jjones
```

```
sbrown
```

...

---

فى الآخر قال:

```
56 valid users
```

---

يعنى عرف

56 يوزر حقيقى.

---

ودول هيستخدمهم بعدين فى

Password Spraying.

---

## بعد كده بيتكلم عن SYSTEM

لو قدرت تجيب

```
NT AUTHORITY\SYSTEM
```

على جهاز Join فى الدومين.

يبقى تقريبًا كأن معاك User فى الدومين.

---

ليه؟

لأن الجهاز نفسه عنده

Computer Account

يقدر يكلم Active Directory.

---

## إزاى أوصل لـ SYSTEM؟

أمثلة:

- EternalBlue
    
- BlueKeep
    
- Juicy Potato
    
- PsExec
    
- Local Privilege Escalation
    

---

لو وصلت لـ SYSTEM

تقدر:

- تشغل BloodHound
    
- تعمل Kerberoasting
    
- تعمل ASREPRoasting
    
- تجمع NTLM Hashes
    
- Token Impersonation
    
- ACL Abuse
    

---

## آخر نقطة مهمة جدًا

الكاتب بيحذر:

متستخدمش أى Tool وخلاص.

لازم تعرف:

هل هى:

- هادية؟
    
- بتعمل DoS؟
    
- بتوقع السيرفر؟
    
- بتشغل Exploits؟
    

لأن ممكن توقف Production Server عند العميل.

وده كارثة.

---

## الميثودولوجي الكامل للجزء ده

1. **ابدأ من غير Credentials.**
    
2. **اعمل Passive Enumeration** باستخدام Wireshark أو tcpdump أو Responder (Analyze Mode).
    
3. **اجمع الـ IPs وأسماء الأجهزة** من ARP وMDNS.
    
4. **اعمل Active Discovery** باستخدام `fping` لمعرفة الأجهزة الحية.
    
5. **اعمل Nmap Scan** لمعرفة الـ Ports والخدمات وأنظمة التشغيل.
    
6. **حدد الأجهزة المهمة** مثل Domain Controller وSQL وWeb وFile Servers.
    
7. **ابحث عن الأجهزة القديمة أو الضعيفة** التى قد توفر نقطة دخول.
    
8. **اعمل Username Enumeration** باستخدام Kerbrute للحصول على قائمة مستخدمين صحيحة.
    
9. **وثّق كل حاجة** (IPs، أسماء الأجهزة، الخدمات، النتائج) لأنك هترجع لها فى المراحل التالية.
    
10. **بعد ما يبقى عندك Users أو Foothold** تبدأ مرحلة استغلال الدومين (Password Spraying، LLMNR Poisoning، BloodHound، Kerberoasting... إلخ).

# Layer 6
## LLMNR / NBT-NS Poisoning from Linux

بعد ما خلصنا مرحلة الـ Initial Enumeration وبقينا عارفين شوية معلومات عن الدومين (زي الـ Users، الـ Groups، الأجهزة الموجودة، والـ Domain Controller)، هنبدأ أول خطوة فعلية للحصول على Credentials.

في الجزء ده هنستخدم طريقتين:

- Network Poisoning
- Password Spraying (هيتشرح بعدين)

الهدف الأساسي هو إننا نحصل على Username و Password أو Password Hash لمستخدم داخل الدومين، بحيث يبقى عندنا Foothold (أول نقطة دخول) ونقدر نكمل الـ Enumeration باستخدام Credentials حقيقية.

---

## يعني إيه Foothold؟

الـ Foothold هو أول Access بنحصل عليه داخل الشبكة.

بدل ما نبقى Anonymous ومش معانا أي صلاحيات، يبقى معانا User حقيقي نقدر نستخدمه في باقى الهجوم.

---

## Man In The Middle (MITM)

الهجوم ده يعتبر Man In The Middle Attack.

يعني بدل ما الاتصال يكون:

User → Server

يبقى:

User → Attacker → Server

إنت بتقف في النص وتخدع الضحية بحيث تبعتلك بياناتها بدل السيرفر الحقيقي.

---

## LLMNR & NBT-NS

الاتنين دول بروتوكولات موجودين في Windows.

وظيفتهم تحويل اسم الجهاز إلى IP Address.

يعني شبه DNS، لكن بيستخدموا لما الـ DNS يفشل.

---

## LLMNR

LLMNR اختصار:

Link Local Multicast Name Resolution

معناها:

- Link Local → داخل نفس الشبكة فقط.
- Multicast → الرسالة بتتبعت لكل الأجهزة الموجودة على الشبكة.
- Name Resolution → تحويل اسم الجهاز إلى IP.

بيشتغل على:

UDP Port 5355

---

## NBT-NS

NBT-NS اختصار:

NetBIOS Name Service

وده بروتوكول أقدم من LLMNR.

لو الـ DNS فشل، وبعده LLMNR فشل، الجهاز بيستخدم NBT-NS.

بيشتغل على:

UDP Port 137

---

## ترتيب عملية الـ Name Resolution

غالبًا الجهاز بيعمل الآتي:

1. يسأل DNS.
2. لو فشل يستخدم LLMNR.
3. لو فشل يستخدم NBT-NS.

---

## فين المشكلة؟

المشكلة إن LLMNR و NBT-NS بيسمحوا لأي جهاز على نفس الشبكة إنه يرد.

مش لازم يكون:

- DNS Server
- Domain Controller

أي جهاز يقدر يقول:

"أنا السيرفر اللي إنت بتدور عليه."

وده هو أصل الثغرة.

---

## إيه هو الـ Poisoning؟

الـ Poisoning معناه إنك ترد على طلبات الأجهزة بمعلومات مزيفة.

يعني الضحية تسأل:

"حد يعرف printer01؟"

إنت ترد:

"أيوه أنا printer01."

الضحية هتصدقك وتبدأ تتعامل معاك.

وده اسمه Spoofing أو Impersonation.

---

## Responder

Responder هي أشهر أداة بتستخدم لتنفيذ LLMNR و NBT-NS Poisoning.

هي بتسمع أي Broadcast Request على الشبكة، ولما تلاقي جهاز بيدور على Host مش موجود، ترد بسرعة وتقول إنها هي الجهاز المطلوب.

	وبالتالي الضحية تبدأ تبعت Authentication للـ Attacker.

---

## مثال عملي للهجوم

الموظف كتب:

\\printer01.inlanefreight.local

بدل:

\\print01.inlanefreight.local

DNS حاول يلاقي الجهاز.

ملقهوش.

الجهاز بعت Broadcast لكل الشبكة وقال:

"مين يعرف printer01؟"

Responder رد بسرعة:

"أنا printer01."

الضحية صدقته.

وبعتت Authentication Request.

الـ Attacker استقبل:

- Username
- NetNTLM Hash

---

## إيه اللي بنسرقه؟

إحنا مش بناخد Password مباشرة.

إحنا بناخد:

NetNTLMv1

أو

NetNTLMv2 Hash

بعدها نحاول نكسره Offline.

---

## يعني إيه Hash؟

الـ Hash عبارة عن بصمة مشفرة لكلمة المرور.

مثال:

Password:

Mohab123

يتحول إلى قيمة طويلة جدًا اسمها Hash.

إنت مش بتشوف الباسورد الحقيقي.

لكن ممكن تحاول تكسر الـ Hash باستخدام Wordlists.

---

## Offline Cracking

يعني بعد ما تاخد الـ Hash، متكلمش الضحية تاني.

تاخده عندك على جهازك وتحاول تكسره باستخدام أدوات زى:

- Hashcat
- John The Ripper

ودي ميزة لأنها مبتعملش Traffic إضافي على الشبكة.

---

## SMB Relay

مش لازم كل مرة تكسر الـ Hash.

في بعض الحالات تقدر تستخدم الـ Hash مباشرة علشان تعمل Authentication على جهاز تاني.

وده اسمه:

SMB Relay Attack

وده هيتشرح في Module تاني.

---

## TTPs

TTPs اختصار:

- Tactics
- Techniques
- Procedures

يعني الطريقة اللي المهاجم بينفذ بيها الهجوم.

في الجزء ده الهدف هو جمع:

- NTLMv1 Hashes
- NTLMv2 Hashes

وبعدها محاولة كسرها للحصول على Password الحقيقي.

---

## NTLMv1 vs NTLMv2

NTLMv1

- قديم.
- ضعيف.
- بيتكسر بسهولة.

NTLMv2

- أحدث.
- أكثر أمانًا.
- أصعب وأبطأ في الكسر.

---

## الأدوات المستخدمة

### Responder

أشهر أداة لعمل:

- LLMNR Poisoning
- NBT-NS Poisoning
- MDNS Poisoning

---

### Inveigh

أداة MITM شبيهة بـ Responder.

مكتوبة بـ:

- C#
- PowerShell

وتستخدم غالبًا على Windows.

---

### Metasploit

فيه Modules جاهزة تساعد في Spoofing و Poisoning.

---

## البروتوكولات اللي يقدر Responder يتعامل معاها

- LLMNR
- DNS
- MDNS
- NBNS
- DHCP
- ICMP
- HTTP
- HTTPS
- SMB
- LDAP
- WebDAV
- Proxy Authentication

وكمان يدعم:

- MSSQL
- DCE-RPC
- FTP
- POP3
- IMAP
- SMTP

وده بيخليه أداة قوية جدًا في الـ Internal Pentest.

---

## Responder Analysis Mode

في مرحلة الـ Enumeration كنا استخدمنا:

```bash
sudo responder -I ens224 -A
```

الـ `-A` معناها Analyze Mode.

يعني:

- يسمع فقط.
- يعرض Requests.
- لا يرد عليها.
- لا يعمل Poisoning.

كان مجرد مراقب للشبكة.

---

## دلوقتي هنبدأ Poisoning

هنشيل:

```bash
-A
```

ونشغل Responder عادي.

وقتها هيبدأ يرد على الطلبات بنفسه ويخدع الأجهزة.

---

## أهم Flags في Responder

### -I

تحديد الـ Network Interface.

مثال:

```bash
-I ens224
```

---

### -A

Analyze Mode.

يسمع فقط بدون أي رد.

---

### -w

يشغل WPAD Rogue Proxy Server.

وده يساعد في الحصول على Authentication من المتصفحات.

---

### -f

يحاول يعمل Fingerprint للجهاز اللي بعت الطلب.

يعرف نوع الـ Operating System وإصداره.

---

### -v

Verbose Mode.

يعرض تفاصيل أكتر أثناء التشغيل.

---

### -F

يجبر الضحية على Authentication.

قد يظهر Login Prompt.

---

### -P

يجبر الـ Proxy Authentication.

ويستخدم غالبًا مع WPAD.

---

## WPAD

WPAD اختصار:

Web Proxy Auto Discovery

بعض أجهزة Windows والمتصفحات بتحاول تدور تلقائيًا على Proxy داخل الشبكة.

Responder يقدر ينتحل شخصية الـ Proxy.

ولو المستخدم استخدمه، هيبعت Authentication للـ Attacker.

وده بيكون مفيد جدًا داخل الشركات الكبيرة.

---

## لو Responder نجح

هيطبع الـ Hash مباشرة على الشاشة.

وكمان هيحفظه داخل:

```text
/usr/share/responder/logs
```

كل Host هيكون ليه Log مستقل.

مثال:

```text
SMB-NTLMv2-SSP-172.16.5.25.txt
```

وده معناه:

- البروتوكول: SMB
- نوع الـ Hash: NTLMv2
- IP الضحية: 172.16.5.25

---

## تشغيل Responder

أبسط تشغيل للأداة:

```bash
sudo responder -I ens224
```

الأفضل تسيبه شغال في tmux أو Screen أثناء ما تكمل Enumeration.

كل ما جهاز يغلط في Name Resolution هيجيلك Hash جديد.

---

## البورتات المطلوبة

Responder محتاج يقدر يفتح عدة Ports، أهمها:

- UDP 137
- UDP 138
- UDP 53
- UDP 5355
- UDP 5353
- TCP 80
- TCP 135
- TCP 139
- TCP 445
- TCP 389
- TCP 1433
- TCP 21
- TCP 25
- TCP 110
- TCP 587
- TCP 3128

ولو في Service مش محتاجها، تقدر تقفلها من:

Responder.conf

---

## كسر الـ Hash

لو حصلنا على NetNTLMv2 Hash، نستخدم Hashcat.

```bash
hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt
```

### شرح الأمر

- `-m 5600` → Hash Mode الخاص بـ NetNTLMv2.
- `hash.txt` → الملف اللي فيه الـ Hash.
- `rockyou.txt` → أشهر Wordlist لتجربة كلمات المرور.

---

## مثال من الملف

الـ Hash الخاص بالمستخدم:

FOREND

اتكسر.

وكلمة المرور كانت:

```text
Klmcargo2
```

وده معناه إن كلمة المرور كانت ضعيفة، وقدر Hashcat يجيبها.

---

## بعد كده؟

بمجرد ما يبقى معانا:

- Username
- Password

يبقى عندنا Foothold داخل الدومين.

ومن هنا نبدأ مرحلة الـ Credentialed Enumeration، ونجمع معلومات أكتر عن الـ Active Directory، أو نتحرك جانبيًا (Lateral Movement)، أو نرفع الصلاحيات لو الحساب يسمح بكده.


# Layer 7
## LLMNR / NBT-NS Poisoning from Windows

في الجزء اللي فات استخدمنا أداة **Responder** على Linux علشان نعمل LLMNR و NBT-NS Poisoning ونلتقط الـ Hashes.

لكن لو جهاز الـ Attacker كان Windows، أو العميل مدينا Windows Machine نشتغل منها، أو قدرنا نوصل لجهاز Windows داخل الشبكة كـ Local Administrator، هنستخدم أداة اسمها **Inveigh** لأنها بتؤدي نفس وظيفة Responder تقريبًا. :contentReference[oaicite:0]{index=0}

---

## Inveigh

**Inveigh** هي أداة مكتوبة بـ:

- PowerShell
- C#

وظيفتها تنفيذ هجمات:

- LLMNR Poisoning
- NBT-NS Poisoning
- DNS Spoofing

وكمان تقدر تلتقط الـ Authentication Requests وتحفظ الـ NTLM Hashes.

الأداة تقدر تتعامل مع بروتوكولات كتير منها:

- LLMNR
- DNS
- mDNS
- NBNS
- DHCPv6
- ICMPv6
- HTTP
- HTTPS
- SMB
- LDAP
- WebDAV
- Proxy Authentication

وفي لابات HTB بتكون موجودة داخل:

```text
C:\Tools
```

---

## استخدام نسخة PowerShell

أول حاجة بنعمل Import للـ Module:

```powershell
Import-Module .\Inveigh.ps1
```

بعدها نعرض كل الـ Parameters اللي الأداة بتدعمها:

```powershell
(Get-Command Invoke-Inveigh).Parameters
```

هيظهر ليستة كبيرة جدًا فيها كل الـ Options اللي نقدر نستخدمها أثناء تشغيل Inveigh.

---

## تشغيل Inveigh

لتشغيل الأداة مع تفعيل:

- LLMNR Spoofing
- NBNS Spoofing
- Console Output
- File Output

نستخدم:

```powershell
Invoke-Inveigh -LLMNR Y -NBNS Y -ConsoleOutput Y -FileOutput Y
```

### شرح الـ Parameters

### `-LLMNR Y`

يفعل LLMNR Spoofing.

يعني الأداة ترد على طلبات LLMNR.

---

### `-NBNS Y`

يفعل NetBIOS Name Service Spoofing.

---

### `-ConsoleOutput Y`

يعرض كل الأحداث مباشرة على الشاشة.

---

### `-FileOutput Y`

يحفظ النتائج داخل ملفات Log.

---

## أول ما الأداة تشتغل

هتظهر معلومات كتير، أهمها:

```text
Primary IP Address = 172.16.5.25
```

وده عنوان الـ IP بتاع جهاز الـ Attacker.

---

بعدها:

```text
Spoofer IP Address = 172.16.5.25
```

وده الـ IP اللي هيستخدمه أثناء الرد على الضحايا.

---

بعدها هيعرض البروتوكولات المفعلة والمعطلة.

مثلاً:

```text
LLMNR Spoofer = Enabled
```

يعني هيعمل Spoofing على LLMNR.

---

```text
NBNS Spoofer = Enabled
```

يعني هيعمل Spoofing على NBNS.

---

```text
DNS Spoofer = Enabled
```

هيقدر يرد على بعض طلبات DNS.

---

```text
SMB Capture = Enabled
```

هيجمع Authentication اللي تيجي عن طريق SMB.

---

```text
HTTP Capture = Enabled
```

هيجمع Authentication الخاصة بـ HTTP.

---

```text
WPAD Response = Enabled
```

هيستجيب لطلبات WPAD.

---

## رسالة الخطأ

هيظهر:

```text
Error starting HTTP listener
```

وده معناه إن Port 80 مستخدم بالفعل أو Windows مانع الأداة تفتحه.

وده طبيعي ومش بيمنع باقي الهجوم من إنه يشتغل.

---

## بعد ثواني

هنبدأ نشوف Requests جاية من أجهزة الضحايا.

مثلاً:

```text
LLMNR request for academy-ea-web0
```

وده معناه إن جهاز داخل الشبكة بيدور على Host اسمه:

```text
academy-ea-web0
```

---

بعدها مباشرة:

```text
response sent
```

يعني Inveigh رد على الضحية وقاله:

"أنا الـ Host اللي بتدور عليه."

وبكده يبدأ الـ Authentication.

---

## بعدها

هنلاقي:

```text
SMB negotiation request detected
```

يعني الضحية بدأت تعمل اتصال SMB.

---

بعدها:

```text
NTLM challenge sent
```

وده بداية عملية الـ NTLM Authentication.

ومن هنا الأداة تبدأ تجمع الـ Hash.

---

## نسخة C#

الكاتب بيقول إن نسخة PowerShell مبقاش بيتم تطويرها.

أما النسخة اللي بيتضافلها تحديثات باستمرار فهي:

**InveighZero**

المكتوبة بـ C#.

ودي هي النسخة الموصى باستخدامها.

---

## تشغيل نسخة C#

بعد ما تكون Compile أو موجودة جاهزة:

```powershell
.\Inveigh.exe
```

---

## أول تشغيل

الأداة هتعرض كل الخدمات اللي شغالة افتراضيًا.

أي خدمة قدامها:

```text
[+]
```

يبقى مفعلة.

وأي خدمة قدامها:

```text
[ ]
```

تبقى غير مفعلة.

---

مثال:

```text
[+] LLMNR Packet Sniffer
```

يعني بيسمع Requests الخاصة بـ LLMNR.

---

```text
[+] LDAP Listener
```

يعني عامل Listener على LDAP.

---

```text
[+] SMB Packet Sniffer
```

بيتابع اتصالات SMB.

---

```text
[ ] NBNS
```

يعني NBNS مش شغال بالإعدادات الافتراضية.

---

```text
[ ] HTTPS
```

يعني HTTPS Listener مش شغال.

---

## أثناء التشغيل

هنشوف رسائل زي:

```text
LLMNR(A) request
```

يعني جهاز بيسأل عن IPv4 Address.

---

ولو ظهر:

```text
LLMNR(AAAA)
```

فده معناه إنه بيسأل عن IPv6 Address.

وفي المثال الأداة تجاهلت النوع ده لأنه غير مفعل.

---

## Interactive Console

أثناء تشغيل Inveigh هيظهر:

```text
Press ESC to enter/exit interactive console
```

لو ضغطنا:

ESC

هندخل Console داخلي خاص بالأداة.

منه نقدر نشوف:

- الـ Hashes
- الـ Logs
- الـ Credentials
- نوقف الأداة
- نعدل بعض الإعدادات

بدون ما نقفل البرنامج.

---

## HELP

لو كتبنا:

```text
HELP
```

هيظهر كل أوامر الـ Console.

---

## أهم أوامر الـ Console

### GET NTLMV2

يعرض كل الـ NTLMv2 Hashes اللي اتجمعت.

---

### GET NTLMV2UNIQUE

يعرض Hash واحد فقط لكل User.

وده مفيد علشان متشوفش نفس الـ User مكرر عشرات المرات.

---

### GET NTLMV2USERNAMES

يعرض:

- Username
- Host
- Source IP

بدون عرض الـ Hash بالكامل.

وده مفيد لو عايز تعرف المستخدمين الموجودين في الشبكة.

---

### GET CLEARTEXT

يعرض أي Credentials وصلت بصيغة واضحة (Plaintext) لو تم التقاطها.

---

### GET LOG

يعرض الـ Logs الخاصة بالأداة.

---

### STOP

يقفل Inveigh.

---

## مثال على Hash

الأداة عرضت:

```text
backupagent::INLANEFREIGHT:...
```

وده NetNTLMv2 Hash خاص بالمستخدم:

```text
backupagent
```

وبرضه ظهر Hash تاني للمستخدم:

```text
forend
```

يعني قدرنا نجمع أكتر من User.

---

## عرض أسماء المستخدمين فقط

لما استخدمنا:

```text
GET NTLMV2USERNAMES
```

ظهر:

- backupagent
- forend
- clusteragent
- wley
- svc_qualys

وده بيساعدنا نحدد أي الحسابات تستحق نحاول نكسر الـ Hash الخاص بيها باستخدام Hashcat.

---

## Remediation

علشان نمنع الهجوم ده، الكتاب اقترح أكتر من حل.

---

## تعطيل LLMNR

من خلال:

```text
Group Policy

Computer Configuration
→ Administrative Templates
→ Network
→ DNS Client
→ Turn OFF Multicast Name Resolution
```

وبعدين نفعل الخيار.

وبكده Windows مش هيستخدم LLMNR.

---

## تعطيل NBT-NS

مش بيتقفل من Group Policy مباشرة.

لازم يتقفل من كل جهاز.

الخطوات:

1. Network and Sharing Center.
2. Change Adapter Settings.
3. Properties.
4. Internet Protocol Version 4.
5. Advanced.
6. WINS.
7. Disable NetBIOS over TCP/IP.

---

## تعطيل NBT-NS باستخدام PowerShell

بدل ما تعمل ده يدويًا على كل جهاز، ممكن تستخدم Script:

```powershell
$regkey = "HKLM:SYSTEM\CurrentControlSet\Services\NetBT\Parameters\Interfaces"

Get-ChildItem $regkey | ForEach {
    Set-ItemProperty -Path "$regkey\$($_.PSChildName)" -Name NetbiosOptions -Value 2
}
```

السكريبت بيغير قيمة Registry الخاصة بكل Network Interface ويعطل NetBIOS.

---

## نشر الـ Script على كل أجهزة الدومين

نقدر نحط الـ Script داخل:

```text
SYSVOL
```

ونربطه بـ Group Policy Startup Script.

ولما الأجهزة تعمل Restart، السكريبت يشتغل تلقائيًا ويعطل NBT-NS على كل الأجهزة.

---

## حلول إضافية

الكتاب ذكر كمان:

- فلترة Traffic الخاصة بـ LLMNR و NetBIOS.
- تفعيل SMB Signing لمنع NTLM Relay.
- استخدام IDS/IPS لمراقبة الشبكة.
- تقسيم الشبكة (Network Segmentation).

---

## Detection

لو مش قادرين نعطل LLMNR أو NBT-NS، لازم نراقب وجود الهجوم.

من طرق الاكتشاف:

- مراقبة Traffic على:

```text
UDP 5355
```

و

```text
UDP 137
```

---

- مراقبة Event IDs:

```text
4697
7045
```

---

- مراقبة قيمة Registry:

```text
HKLM\Software\Policies\Microsoft\Windows NT\DNSClient
```

ولو:

```text
EnableMulticast = 0
```

يبقى LLMNR متعطل.

---

## بعد كده؟

بعد ما نجمع الـ Hashes، مش بنجري نكسرهم كلهم.

الأفضل الأول نستخدم أدوات زي:

- BloodHound

علشان نعرف أي المستخدمين عندهم صلاحيات مهمة.

بعدها نحاول نكسر الـ Hashes الخاصة بالحسابات المهمة فقط باستخدام Hashcat.

ولو قدرنا نجيب Password لحساب مميز، نبدأ نوسع سيطرتنا داخل الـ Active Directory.

ولو مقدرناش نكسر أي Hash، يبقى ننتقل للمرحلة اللي بعدها وهي:

**Password Spraying**.
