# Chapter 02: Variables & Data Types 📦

## مقدمة بسيطة
البيانات في الـ Hacking مش كلها شكل واحد. ساعات بيكون عندك IP Address (ودا نص/String)، وساعات بيكون عندك Port (رقم/Integer)، وساعات بيكون عندك لستة طويلة من الباسوردات عايز تجربها (List). في الـ Chapter ده هنتعمق أكتر في إزاي بنتعامل مع البيانات دي ونشكلها زي ما إحنا عايزين.

## شرح المفاهيم خطوة بخطوة

### 1. Strings بالتفصيل
الـ String هو أي نص. بنقدر نعمل عليه عمليات كتير زي إننا نخلي الحروف كلها كابيتال (Uppercase) أو نفصل النص لأجزاء (Split).

### 2. Indexing & Slicing
تخيل الـ String أو الـ List كأنها عمارة، كل حرف أو عنصر ساكن في دور (Index). في Python بنبدأ العد من صفر `0`.
- **Indexing**: بنجيب عنصر واحد (مثلاً الحرف الأول).
- **Slicing**: بنقطع جزء من البيانات (مثلاً من الحرف الأول للرابع).

### 3. Lists (القوائم)
الـ List ببساطة هي صندوق كبير جواه صناديق صغيرة، بتقدر تخزن فيها أكتر من قيمة مع بعض. قابلة للتعديل (ممكن تضيف وتمسح منها).

### 4. Tuples
زي الـ List بالظبط، بس مقفولة بقفل! يعني بمجرد ما تعملها، مينفعش تعدل عليها (Immutable). بنستخدمها للحاجات الثابتة.

### 5. Dictionaries (القواميس)
دي عبارة عن Key و Value (مفتاح وقيمة). زي القاموس الحقيقي، بتدور بكلمة (Key) تلاقي معناها (Value). مفيدة جداً في تخزين بيانات معقدة زي معلومات الـ Target.

### 6. Sets
زي الـ List بس مفيهاش أي عناصر متكررة. مفيدة جداً لو عندك ملف فيه IPs متكررة وعايز تطلع الـ Unique بس.

---

## أمثلة Python عملية

```python
# 1. String Methods
target_url = "http://admin.target.com/login"
domain = target_url.split("//")[1].split("/")[0]  # Extracting domain
print("Extracted Domain:", domain.upper())

# 2. Lists
open_ports = [22, 80, 443, 3306]
open_ports.append(8080)  # Adding a new port
print("First open port:", open_ports[0])

# 3. Tuples (Fixed data)
credentials = ("admin", "P@ssw0rd123")
# credentials[0] = "root"  # This will cause an error!

# 4. Dictionaries
target_info = {
    "ip": "10.10.10.15",
    "os": "Linux",
    "is_up": True
}
print("Target OS is:", target_info["os"])

# 5. Sets (Removing duplicates)
found_ips = {"192.168.1.1", "192.168.1.5", "192.168.1.1"}
print("Unique IPs:", found_ips)
```

---

## شرح للكود سطر بسطر
- `split("//")`: بتقسم الـ String لجزئين بناءً على الـ `//`، وبعدين أخدنا الجزء التاني `[1]` وعملناله Split تاني بالـ `/` عشان نطلع الـ Domain الصافي.
- `open_ports.append(8080)`: ضفنا بورت جديد للستة الـ `open_ports`.
- `credentials = ("admin", ...)`: عملنا Tuple فيه اليوزر والباسورد، ومينفعش نغيرهم عشان نضمن إن البيانات دي متتعدلش بالغلط.
- `target_info["os"]`: جبنا القيمة الخاصة بالـ Key اللي اسمه `os` من الـ Dictionary.
- `found_ips`: برغم إننا كتبنا الـ IP مرتين، الـ Set هتحتفظ بنسخة واحدة بس.

---

## أخطاء شائعة
1. **Out of Range Index**: لو عندك List فيها 3 عناصر وتطلب العنصر رقم 10، هيضرب Error (`IndexError`).
2. **KeyError**: إنك تحاول تجيب Value من Dictionary بـ Key مش موجود أساساً.

---

## Security/Hacking Use Case
استخراج البيانات (Parsing). تخيل إنك بتعمل أداة بتقرأ نتائح أداة تانية (زي Nmap). هتحتاج تستخدم الـ String methods زي `split` عشان تطلع الـ IP أو البورتات، وتخزنها في `Lists`، وتحفظ معلومات كل تارجت في `Dictionary`.

---

## تمارين
1. اعمل String فيه الجملة دي: `"user:root,password:toor"`. استخدم String methods عشان تطلع كلمة `root` لوحدها وكلمة `toor` لوحدها.
2. اعمل Dictionary يمثل بيانات سيرفر (IP, Port, Service Name)، واطبعهم.

---

## Mini Challenge 🏆
عندك الـ String ده:
`raw_data = "192.168.1.1,192.168.1.2,192.168.1.1,10.0.0.5"`
المطلوب:
1. حوّله لـ List.
2. شيل منه الـ IPs المتكررة.
3. اطبع عدد الـ IPs المتبقية (استخدم دالة `len()`).
