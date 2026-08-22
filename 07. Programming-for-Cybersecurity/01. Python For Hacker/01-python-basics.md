# Chapter 01: Python Basics 🐍💀

## مقدمة بسيطة
أهلاً بيك في أول خطوة ليك في عالم الـ Python for Security. لغة Python بتعتبر السلاح الأساسي لأي حد شغال في الـ Cybersecurity أو الـ Penetration Testing. ليه؟ لأنها سهلة، سريعة، وفيها مكتبات جاهزة بتعملك أي حاجة تتخيلها. في الـ Chapter ده هنتعلم الأساسيات اللي هتبني عليها كل شغلك الجاي.

## شرح المفاهيم خطوة بخطوة

### 1. Python Syntax & `print()`
عشان تخلي Python تتكلم وتطبع لك حاجة على الشاشة، بنستخدم الـ `print()`. دي أول حاجة بتعملها عشان تطلع Output للـ User.

### 2. Comments (التعليقات)
الـ Comments دي سطور Python بتتجاهلها تماماً ومش بتنفذها. بنستخدمها عشان نشرح الكود لنفسنا أو لغيرنا، وبتبدأ بعلامة `#`.

### 3. Variables (المتغيرات)
الـ Variable ببساطة هو مكان بنخزن فيه قيمة معينة في الـ Memory، زي إنك تعمل صندوق وتحط جواه اسم المستخدم، أو الـ IP Address بتاع التارجت.

### 4. Data Types (أنواع البيانات الأساسية)
- **String**: نصوص (حروف وكلمات) ولازم تكون بين علامتين تنصيص `" "`.
- **Integer**: أرقام صحيحة (زي 80, 443).
- **Float**: أرقام عشرية (زي 3.14).
- **Boolean**: قيمة منطقية، يا إما `True` (صح) أو `False` (غلط).

### 5. `input()`
بناخد بيها بيانات من المستخدم وهو بيشغل السكريبت، زي إننا نطلب منه يدخل الـ IP.

### 6. `type()` & Type Conversion
الـ `type()` بتعرفنا نوع الـ Variable. وساعات بنحتاج نحول من نوع للتاني، مثلاً من String لـ Integer عشان نقدر نعمل عمليات حسابية.

---

## أمثلة Python عملية

```python
# 1. Printing a basic banner for our tool
print("="*30)
print("   0xSN Basic Scanner v1.0   ")
print("="*30)

# 2. Variables & Data Types
target_ip = "192.168.1.100"  # String
target_port = 80             # Integer
is_vulnerable = False        # Boolean
timeout = 1.5                # Float

# 3. Taking input from the user
user_ip = input("Enter the Target IP: ")

# 4. Type conversion (input always returns a String, we need Integer for ports)
port_input = input("Enter the Port to scan: ")
port_number = int(port_input)  # Converting String to Integer

print("Scanning IP:", user_ip, "on port:", port_number)
```

---

## شرح للكود سطر بسطر
- `print("="*30)`: طبعنا علامة اليساوي 30 مرة عشان نعمل شكل جمالي (Banner) للسكريبت بتاعنا.
- `target_ip = "..."`: عملنا Variable اسمه `target_ip` وحطينا جواه String يمثل الـ IP.
- `target_port = 80`: خزنّا رقم البورت كـ Integer.
- `input(...)`: طلبنا من اليوزر يكتب الـ IP والنتيجة اتخزنت في `user_ip`.
- `int(...)`: حولنا النص اللي اليوزر دخله لرقم صحيح عشان ينفع نستخدمه كـ Port حقيقي بعدين.

---

## أخطاء شائعة (Common Mistakes)
1. **نسيان الأقواس في `print`**: في Python 3 لازم `print("Hello")` مش `print "Hello"`.
2. **جمع String مع Integer**: مينفعش تقول `"Port: " + 80`. لازم تحول الرقم لنص الأول: `"Port: " + str(80)`.
3. **المسافات (Indentation)**: بايثون حساسة جداً للمسافات في أول السطر، متعملش مسافة بدون سبب.

---

## Security/Hacking Use Case
في الـ Penetration Testing، أول حاجة بتعملها هي الـ Reconnaissance، وساعات بتحتاج تبني Tool بسيطة تطلب من اليوزر يدخل الـ Target IP والـ Ports اللي عايز يعملها Scan، وتطبعله رسالة تأكيد. ده بالضبط اللي الأساسيات دي بتعمله.

---

## تمارين (Exercises)
1. اعمل سكريبت يطبع Banner باسمك.
2. اطلب من اليوزر يدخل اسمه، الـ IP، ورقم الـ Port.
3. اطبع رسالة بتقول: `Starting scan on [IP] at port [Port] for user [Name]`.

---

## Mini Challenge 🏆
اكتب سكريبت بيحسب الوقت المتوقع للـ Scan.
- اطلب من اليوزر يدخل عدد الـ Ports (باستخدام `input`).
- افترض إن كل Port بياخد 0.5 ثانية (Float).
- احسب الوقت الإجمالي (عدد الـ Ports * 0.5).
- اطبع النتيجة للمستخدم: `Estimated scan time: ... seconds`.
