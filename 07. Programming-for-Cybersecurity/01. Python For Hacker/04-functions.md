# Chapter 04: Functions 🛠️

## مقدمة بسيطة
تخيل إنك كتبت كود بيفحص بورت معين، الكود ده 10 سطور. لو حبيت تفحص 5 بورتات مختلفة، هل هتنسخ الـ 10 سطور 5 مرات؟ أكيد لأ! هنا بيجي دور الـ **Functions** (الدوال). الـ Function ببساطة هي بلوك من الكود بتديله اسم، ولما تحب تنفذه بتنادي على اسمه بس.

## شرح المفاهيم خطوة بخطوة

### 1. إنشاء Function (`def`)
بنعرف الـ Function باستخدام كلمة `def` (يعني Define)، وبعدين بنكتب اسم الـ Function وأقواس `()`.

### 2. Parameters & Arguments
- **Parameters**: دي المتغيرات اللي الـ Function متوقعاها.
- **Arguments**: دي القيم الحقيقية اللي بتبعتها للـ Function وإنت بتنادي عليها.

### 3. `return`
الـ Function ممكن تطبع حاجة مباشرة بـ `print`، بس الأفضل إنها ترجّع (Return) نتيجة، وإنت تاخد النتيجة دي تستخدمها براحتك.

### 4. Default Arguments
ممكن ندي قيمة افتراضية للـ Parameter بحيث لو اليوزر مبعتش حاجة، الـ Function تشتغل بالقيمة دي.

### 5. Scope
ده معناه "نطاق رؤية المتغير". المتغير اللي بتعمله جوة الـ Function مش بيتشاف براها.

### 6. `lambda` بشكل مبسط
طريقة مختصرة جداً لكتابة Function صغيرة في سطر واحد بدون `def`.

---

## أمثلة Python عملية

```python
import random
import string

# 1. Basic Function with parameters and return
def check_port(ip, port):
    if port in [22, 80, 443]:
        return True
    return False

# 2. Function with Default Argument
def generate_random_string(length=8):
    chars = string.ascii_letters + string.digits
    result = ""
    for _ in range(length):
        result += random.choice(chars)
    return result

# --- Main Code Execution ---
target = "10.10.10.20"

is_open = check_port(target, 22)
if is_open:
    print(f"[+] Port 22 is OPEN on {target}")

rand_pass = generate_random_string()
print(f"[*] Generated Payload (8 chars): {rand_pass}")

long_pass = generate_random_string(16)
print(f"[*] Generated Payload (16 chars): {long_pass}")

# 3. Lambda Function
format_ip = lambda ip, port: f"http://{ip}:{port}/"
print("Formatted URL:", format_ip("192.168.1.5", 8080))
```

---

## شرح للكود سطر بسطر
- `def check_port(ip, port):`: عملنا دالة بتاخد معلومتين (ip و port).
- `return True`: لو الشرط تحقق، الدالة بترجع قيمة `True` وبتقف.
- `def generate_random_string(length=8):`: الـ `length` هنا ليه قيمة افتراضية `8`. لو نادينا الدالة بدون ما نحدد طول، هتستخدم 8.
- `lambda ip, port: ...`: دالة سريعة بتاخد متغيرين وترجعهم بشكل URL منسق، من غير ما نحتاج نعمل `def` و `return`.

---

## أخطاء شائعة
1. **المناداة على الدالة بدون أقواس**: لو كتبت اسم الدالة بس من غير `()`، الدالة مش هتتنفذ.
2. **استخدام متغير Local بره الدالة**: لو عملت متغير جوة الدالة وحاولت تطبعه بره الدالة، هتاخد Error.
3. **نسيان الـ `return`**: لو دالة بتعمل حسبة ومفيهاش `return`، نتيجتها هتكون `None`.

---

## Security/Hacking Use Case
تخيل إنك بتعمل Tool كبيرة لـ Reconnaissance. هتعمل Function اسمها `scan_ports()`، و Function تانية `grab_banner()`، و Function تالتة `save_to_report()`. ده بيخلي كود الأداة بتاعتك منظم جداً (Modular).

---

## تمارين
1. اعمل Function اسمها `is_valid_ip` بتاخد String، وترجع `True` لو الـ String ده فيه 3 نقط (`.`)، وترجع `False` لو غير كدة.
2. نادي على الـ Function دي وجربها.

---

## Mini Challenge 🏆
اعمل Function اسمها `analyze_status_code(code)`.
- لو 200 ترجع `"[+] OK"`
- لو 301 أو 302 ترجع `"[*] Redirect"`
- لو 401 أو 403 ترجع `"[-] Unauthorized/Forbidden"`
- لو 500 ترجع `"[!] Server Error"`
- اعمل List فيها الـ Codes، واعمل `for` loop تمشي على الـ List وتطبع النتيجة لكل كود.
