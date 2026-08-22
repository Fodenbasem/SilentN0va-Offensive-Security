# Chapter 08: Security Automation ⚙️

## مقدمة بسيطة
الـ Hacker الشاطر مش بيعمل المهام المتكررة بإيده. في الـ Chapter ده هنتعلم نستخدم مكتبات بايثون عشان ننفذ أوامر النظام، نحلل النصوص، ونتعامل مع التشفير.

## شرح المفاهيم خطوة بخطوة

### 1. مكتبة `subprocess`
بتخليك تفتح التيرمنال من جوة بايثون وتنفذ أوامر (زي `ping` أو `nmap`) وتاخد النتيجة.

### 2. مكتبة `argparse` و `sys`
عشان السكريبت بتاعك يقبل أوامر من الـ Command Line زي `-u` للرابط.

### 3. مكتبة `hashlib` & `base64`
للـ Hashing (MD5, SHA-256) وفك وتشفير الـ Base64 اللي الـ Malware بيستخدمه كتير.

### 4. الـ Regex (`re` module)
للبحث عن Pattern معين (زي شكل الـ IP Address) جوة نص كبير.

---

## أمثلة Python عملية

```python
import subprocess
import hashlib
import base64
import re

# 1. Running System Commands (subprocess)
def ping_target(ip):
    print(f"[*] Pinging {ip}...")
    result = subprocess.run(['ping', '-c', '1', ip], capture_output=True, text=True)
    if result.returncode == 0:
        print("[+] Host is UP!")

# 2. Hashing Passwords (hashlib)
def generate_sha256(clear_text):
    encoded_text = clear_text.encode('utf-8')
    hash_object = hashlib.sha256(encoded_text)
    return hash_object.hexdigest()

print("SHA-256 for 'admin':", generate_sha256("admin"))

# 3. Base64 Encoding/Decoding
secret_payload = "<script>alert(1)</script>"
b64_payload = base64.b64encode(secret_payload.encode('utf-8')).decode('utf-8')
print(f"Encoded Payload: {b64_payload}")

# 4. Regex (Extracting IP)
dirty_log = "Error on 192.168.1.53 at midnight."
ip_pattern = r'\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b'
found_ips = re.findall(ip_pattern, dirty_log)
print("Found IPs:", found_ips)
```

---

## شرح للكود سطر بسطر
- `subprocess.run([...])`: نفذنا أمر `ping` كأننا في التيرمنال بأمان `shell=False`.
- `.encode('utf-8')`: الـ Hashing والـ Base64 بيتعاملوا مع Bytes مش Strings.
- `.hexdigest()`: بتطلع نتيجة الـ Hash كـ نص مقروء.
- `re.findall(...)`: بتدور على أي حاجة بتطابق نمط الـ IP وبترجعها.

---

## أخطاء شائعة
1. **Command Injection**: لو استخدمت `shell=True` مع إدخال مستخدم، ممكن يخترق جهازك. دايماً استخدمها كـ List.
2. **نسيان تحويل الـ String لـ Bytes**: هيطلعلك `TypeError`.

---

## Security/Hacking Use Case
تقدر تكتب سكريبت بيقرأ ملف وتدور بـ Regex على Base64، وتفكه بـ `base64.b64decode` وتطلع الـ Payload الحقيقي اللي كان مخفي عن الـ Antivirus.

---

## تمارين
1. اكتب سكريبت بيحول كلمة `root123` لـ MD5 Hash.
2. اعمل سكريبت بيفك تشفير `SGFja2Vk`.

---

## Mini Challenge 🏆
اعمل سكريبت **Hash Cracker**:
- `target_hash = "73868cb1848a216984dca156d6272bf9"`
- `words = ["apple", "banana", "orange", "admin"]`
- اعمل loop، حول كل كلمة لـ MD5، ولو طابقت التارجت، اطبع "[SUCCESS] Password cracked" واعمل break.
