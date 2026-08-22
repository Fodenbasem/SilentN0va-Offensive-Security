# Chapter 05: Data Structures 🗂️

## مقدمة بسيطة
تخيل إنك عملت Scan لـ 100 جهاز، وكل جهاز ليه IP وليه مجموعة بورتات مفتوحة وليه نظام تشغيل (OS). مستحيل تخزن كل البيانات دي في Variables عادية. هنا بنحتاج الـ **Data Structures** (هياكل البيانات) المتقدمة.

## شرح المفاهيم خطوة بخطوة

### 1. مراجعة وتعمق في Lists & Dictionaries
الـ List بتشيل بالترتيب، والـ Dictionary بيشيل بالـ Key-Value.

### 2. Nested Structures (الهياكل المتداخلة)
ده السر الحقيقي! إنك تعمل List جواها Dictionaries، أو Dictionary جواه Lists.

### 3. List Comprehension
دي طريقة "Ninja" في بايثون، بتخليك تعمل `for` loop وتفلتر الـ List وتطلع List جديدة في سطر واحد بس!

### 4. Dictionary Comprehension
نفس فكرة الـ List Comprehension بس عشان تبني Dictionary بسرعة.

---

## أمثلة Python عملية

```python
# 1. Nested Data Structures
scan_results = [
    {
        "ip": "192.168.1.10",
        "hostname": "win-server",
        "open_ports": [80, 445, 3389]
    },
    {
        "ip": "192.168.1.20",
        "hostname": "linux-db",
        "open_ports": [22, 3306]
    }
]

print("--- Scan Report ---")
for target in scan_results:
    ip = target["ip"]
    ports = target["open_ports"]
    if len(ports) > 0:
        print(f"[+] {ip} has open ports: {ports}")

# 2. List Comprehension
all_ports = [21, 22, 80, 443, 445, 8080]
web_ports = [80, 443, 8080]

found_web_ports = [port for port in all_ports if port in web_ports]
print("\nWeb Ports found:", found_web_ports)

# 3. Dictionary Comprehension
headers = {"server": "nginx", "cookie": "session=123"}
upper_headers = {key.upper(): value for key, value in headers.items()}
print("\nUppercase Headers:", upper_headers)
```

---

## شرح للكود سطر بسطر
- `scan_results`: دي عبارة عن List جواها عناصر، كل عنصر Dictionary. جوة كل Dictionary بنشيل List للبورتات.
- `[port for port in all_ports if port in web_ports]`: معناها "هاتلي كل `port` موجود في `all_ports` بشرط إنه يكون في `web_ports`، وحطهم في List جديدة".

---

## أخطاء شائعة
1. **لخبطة الأقواس**: `[]` للـ List، `{}` للـ Dictionary أو Set، `()` للـ Tuple.
2. **تعديل List أثناء اللف عليها**: مينفعش تعمل `for item in my_list:` وجوة الـ Loop تمسح عناصر من `my_list`.
3. **KeyError في Nested Dictionaries**: لو طلبت `target["os"]` وهو مش موجود، الكود هيضرب.

---

## Security/Hacking Use Case
معظم الـ APIs بترجعلك البيانات بصيغة JSON، اللي بيتحول في بايثون لـ Nested Dictionaries & Lists. قدرتك على استخراج البيانات منها مهارة أساسية لأي أداة Automation.

---

## تمارين
1. عندك `users = {"admin": "root123", "0xSN": "nova_pass"}`.
2. اكتب `for` loop تطبع كل يوزر والباسورد بتاعه.

---

## Mini Challenge 🏆
عندك `subdomains = [{"url": "api.target.com", "status": 200}, {"url": "test.target.com", "status": 404}]`.
المطلوب باستخدام الـ **List Comprehension**: اعمل List جديدة يكون فيها الـ `url` للـ subdomains اللي الـ `status` بتاعها `200` واطبعها.
