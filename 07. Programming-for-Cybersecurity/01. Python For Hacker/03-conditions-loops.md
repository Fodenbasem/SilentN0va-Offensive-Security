# Chapter 03: Conditions & Loops 🔄

## مقدمة بسيطة
الـ Hacking كله عبارة عن تكرار واتخاذ قرارات. يعني مثلاً: "لو (if) البورت مفتوح، اعمل كذا"، أو "جرب الباسوردات دي كلها واحدة ورا التانية (loop)". في الـ Chapter ده هنتعلم إزاي نخلي الكود بتاعنا يفكر وياخد قرارات ويكرر المهام.

## شرح المفاهيم خطوة بخطوة

### 1. Conditions (الشروط: if, elif, else)
بنستخدمها عشان نخلي الكود ينفذ حاجة معينة بناءً على شرط معين. 
- `if`: لو الشرط تحقق.
- `elif`: لو الشرط الأول متحققش، جرب الشرط ده.
- `else`: لو ولا شرط تحقق، اعمل ده.

### 2. Comparison & Logical Operators
- **Comparison**: `==` (يساوي)، `!=` (لا يساوي)، `>` (أكبر من)، `<` (أصغر من).
- **Logical**: `and` (الشرطين لازم يتحققوا)، `or` (واحد بس كفاية)، `not` (عكس الشرط).

### 3. `for` Loops
بنستخدمها لما نكون عايزين نلف (نعمل Iterate) على حاجة معروفة، زي إننا نلف على قائمة (List) فيها IPs أو باسوردات.

### 4. `while` Loops
بنستخدمها لما نكون عايزين الكود يفضل يشتغل طول ما فيه شرط معين متحقق (True).

### 5. `range()`, `break`, `continue`
- `range()`: بتولد لينا أرقام متسلسلة (مفيدة جداً لو بنعمل Scan على Range بورتات).
- `break`: بتكسر الـ Loop وتخرج منها فوراً.
- `continue`: بتعمل تخطي (Skip) للفة الحالية وتدخل في اللي بعدها.

---

## أمثلة Python عملية

```python
# 1. Conditions (Checking HTTP Status Code)
status_code = 403

if status_code == 200:
    print("[+] Page found! Access granted.")
elif status_code == 403:
    print("[-] Forbidden! We need a bypass.")
elif status_code == 404:
    print("[-] Page not found.")
else:
    print("[?] Unknown status.")

# 2. For Loop with range() (Port Scanning logic)
print("\n--- Starting Port Scan ---")
for port in range(20, 26):  # Will loop from 20 to 25
    if port == 22:
        print(f"[+] Port {port} is OPEN (SSH)")
    else:
        print(f"[-] Port {port} is CLOSED")

# 3. For Loop over a List with break/continue
passwords = ["123456", "password", "admin123", "root", "qwerty"]
target_pass = "admin123"

print("\n--- Bruteforce Started ---")
for pwd in passwords:
    if pwd == "password":
        continue  # Skip this specific password for some reason
        
    print(f"[*] Trying: {pwd}")
    if pwd == target_pass:
        print(f"[SUCCESS] Password found: {pwd}")
        break  # Stop the loop, we found it!
```

---

## شرح للكود سطر بسطر
- `if status_code == 403:`: بنسأل، هل الـ status code بيساوي 403؟ لو أيوة هنطبع رسالة الـ Forbidden.
- `for port in range(20, 26):`: الكود هيلف 6 مرات، كل مرة قيمة `port` هتتغير (20, 21, 22 لحد 25).
- `f"[*] Trying: {pwd}"`: ده بنسميه `f-string`، طريقة سهلة جداً عشان نحط Variables جوة الـ String مباشرة بين أقواس `{}`.
- `continue`: لما الباسورد كان "password"، عملنا تجاهل للفة دي ومطبعناش Trying.
- `break`: لما لقينا الباسورد الصح "admin123"، ملهاش لازمة نكمل الباقي، فكسرنا الـ Loop.

---

## أخطاء شائعة
1. **نسيان النقطتين `:`**: دايماً في نهاية سطر الـ `if` أو الـ `for` أو الـ `while` لازم تحط `:`.
2. **اللخبطة بين `=` و `==`**: علامة `=` عشان تدي قيمة لـ Variable، لكن `==` عشان تقارن قيمتين ببعض.
3. **Infinite Loop**: إنك تعمل `while True:` وتنسى تحط جواه شرط يعمل `break`، الكود هيفضل شغال للأبد ويهنج الجهاز.

---

## Security/Hacking Use Case
Brute-forcing! فكرة أي أداة Brute-force مبنية على `for` loop بتلف على Wordlist، و`if` condition بتتحقق هل الباسورد ده رجّع نجاح ولا فشل.

---

## تمارين
1. اكتب سكريبت بيطلب من اليوزر يدخل بورت، لو البورت 80 اطبع "HTTP"، لو 443 اطبع "HTTPS"، لو 21 اطبع "FTP"، غير كدة اطبع "Unknown".
2. اعمل `while` loop بتطبع الأرقام من 10 لـ 1 (عد تنازلي)، وفي الآخر تطبع "BOOM!".

---

## Mini Challenge 🏆
اعمل سكريبت بيفحص لستة IPs:
`ips = ["10.0.0.1", "192.168.1.5", "10.0.0.12", "127.0.0.1"]`
المطلوب:
- لف على الـ IPs دي.
- لو لقيت الـ IP هو `"127.0.0.1"` (Localhost)، اطبع "Skipping Localhost" واعمل `continue`.
- لو لقيت IP بيبدأ بـ `"192."`، اطبع "Target Found: [IP]" واعمل `break`.
