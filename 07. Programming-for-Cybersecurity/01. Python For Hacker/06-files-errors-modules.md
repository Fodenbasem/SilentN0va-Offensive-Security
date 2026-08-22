# Chapter 06: Files, Errors & Modules 📂⚠️

## مقدمة بسيطة
في العالم الحقيقي للـ Hacking، البيانات بتيجي من ملفات (زي Wordlist)، ونتائج شغلك لازم تتسيف في ملف. كمان الكود لازم يكون "مقاوم للصدمات". وأخيراً، هنعرف إزاي نستخدم كود ناس تانية (Modules).

## شرح المفاهيم خطوة بخطوة

### 1. التعامل مع الملفات (`open`, `with`)
- بنفتح الملفات بـ `open()`.
- المود: `'r'` للقراءة، `'w'` للكتابة، `'a'` للإضافة.
- استخدام `with open(...)` أفضل طريقة لأنها بتقفل الملف أوتوماتيك.

### 2. Error Handling (`try`, `except`)
الـ `try/except` بتخليك تقول لبايثون: "جرب نفذ الكود ده، ولو حصل Error معين، متقفلش البرنامج، واعمل كذا بداله".

### 3. Modules & `import`
بايثون قوية بسبب الـ Modules. تقدر تستدعيها في الكود بـ `import`، زي `os` و `sys` أو أدوات خارجية بـ `pip`.

---

## أمثلة Python عملية

```python
import os

target_file = "targets.txt"

# Writing to a file
print("[*] Creating targets list...")
with open(target_file, 'w') as file:
    file.write("192.168.1.5\n")
    file.write("10.0.0.1\n")

# Reading from a file safely
print("[*] Reading targets...")
try:
    with open(target_file, 'r') as file:
        lines = file.readlines()
        for line in lines:
            ip = line.strip()
            print(f"Target loaded: {ip}")
except FileNotFoundError:
    print(f"[-] Error: File not found!")
except Exception as e:
    print(f"[-] An unexpected error occurred: {e}")
finally:
    print("[*] File operation completed.\n")

# Error Handling logic
def calc_rate(success, total):
    try:
        return (success / total) * 100
    except ZeroDivisionError:
        return 0

print("Success Rate:", calc_rate(5, 100))
print("Success Rate:", calc_rate(0, 0)) # No crash!
```

---

## شرح للكود سطر بسطر
- `with open(..., 'w') as file:`: افتح الملف في وضع الكتابة.
- `try:`: جرب تقرأ الملف.
- `except FileNotFoundError:`: لو الملف مش موجود، اطبع رسالة شيك بدل الـ Crash.
- `except Exception as e:`: شبكة تصطاد أي Error تاني.
- `finally:`: ده كود بيتنفذ في جميع الحالات.

---

## أخطاء شائعة
1. **نسيان `strip()`**: لما بتقرأ سطور، بيبقى في آخر كل سطر `\n`. لو مسحتهاش هتعمل مشاكل.
2. **الكتابة بـ `w` بدل `a`**: الـ `w` بيمسح الداتا القديمة كلها!
3. **Catch-all Exceptions صامتة**: `except:` وتحتها `pass` بيخفي الـ Errors ومش هتعرف لو في مشكلة.

---

## Security/Hacking Use Case
أداة Subdomain Enumeration بتعمل `import` لـ Wordlist (تقرأ ملف)، وبتحط الـ Requests جوة `try/except` عشان لو الـ Subdomain مش موجود الأداة متوقفش، وبتسيف النتائج في ملف Report.

---

## تمارين
1. اطلب من اليوزر يدخل نص `input()`.
2. احفظ النص في ملف باستخدام الـ Append mode `'a'`.

---

## Mini Challenge 🏆
اعمل سكريبت بـ **Log File Analyzer**.
1. افترض عندك ملف `logs.txt` فيه سطور `[INFO]` وسطور `[ERROR]`.
2. السكريبت بتاعك هيقرأ الملف ويطلع السطور اللي فيها `[ERROR]` بس.
3. استخدم `try/except` عشان لو الملف مش موجود تطبع تحذير.
