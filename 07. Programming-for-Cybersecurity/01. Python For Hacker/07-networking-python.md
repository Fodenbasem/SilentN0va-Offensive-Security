# Chapter 07: Networking with Python 🌐

## مقدمة بسيطة
بايثون بتديك القدرة إنك تتكلم لغة الشبكات. في الـ Chapter ده هنتعلم إزاي نبني Sockets ونتعامل مع الـ Web باستخدام أقوى مكتبة `requests`.

## شرح المفاهيم خطوة بخطوة

### 1. الـ Socket Module
دي الأساس لأدوات زي Port Scanners و Reverse Shells. بتسمحلك تعمل اتصال مباشر بأي IP و Port.

### 2. TCP vs UDP بشكل مبسط
- **TCP**: اتصال موثوق.
- **UDP**: اتصال سريع بس مش موثوق.

### 3. الـ `requests` Library
مكتبة بتخلي التعامل مع الـ Web (HTTP/HTTPS) سهل جداً. تقدر تبعت GET و POST، تقرأ الـ Headers، والـ Status Code في ثواني.

---

## أمثلة Python عملية

```python
import socket
import requests

# 1. Basic TCP Port Checker using Socket
def check_port_tcp(ip, port):
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(1.5)
    
    try:
        result = s.connect_ex((ip, port))
        if result == 0:
            print(f"[+] Port {port} is OPEN on {ip}")
        else:
            print(f"[-] Port {port} is CLOSED on {ip}")
    except socket.error as err:
        print(f"[!] Socket error: {err}")
    finally:
        s.close()

print("--- Socket Port Scanner ---")
check_port_tcp("8.8.8.8", 53)

# 2. Interacting with Web Servers using Requests
def check_website(url):
    print(f"\n--- HTTP Request to {url} ---")
    try:
        response = requests.get(url, timeout=3)
        print(f"Status Code: {response.status_code}")
        
        if response.status_code == 200:
            print("[+] Website is UP.")
            server = response.headers.get("Server", "Unknown")
            print(f"[*] Web Server: {server}")
            
    except requests.exceptions.RequestException:
        print("[!] Error connecting to the target.")

check_website("http://example.com")
```

---

## شرح للكود سطر بسطر
- `socket.socket(...)`: بنكريت سوكيت لبروتوكول TCP.
- `s.connect_ex(...)`: لو رجعت `0` يبقى نجحت (البورت مفتوح).
- `requests.get(url)`: بتبعت HTTP GET Request.
- `response.headers.get("Server")`: بنقرأ نوع السيرفر من الـ Headers بدون ما الكود يكراش لو مش موجود.

---

## أخطاء شائعة
1. **نسيان قفل الـ Socket**: دايماً استخدم `s.close()`.
2. **نسيان الـ Timeout**: لو معملتش `timeout=`، الكود هيفضل مستني للأبد لو السيرفر مبيردش.
3. **عدم كتابة `http://`**: الـ `requests` محتاجة رابط كامل مش اسم الموقع بس.

---

## Security/Hacking Use Case
- **socket**: لعمل Banner Grabbing أو Reverse Shell.
- **requests**: לבناء أدوات Directory Brute-forcing، Web Scrapers، واستغلال ثغرات الويب.

---

## تمارين
1. ابعت `requests.get()` لموقع.
2. اطبع الـ Status Code ومحتوى الـ HTML `response.text`.

---

## Mini Challenge 🏆
اعمل أداة **HTTP Header Analyzer**:
- الأداة تطلب من اليوزر يدخل URL كامل.
- تبعت Request.
- تلف (بـ `for` loop) على الـ `response.headers`.
- اطبع الـ Key والـ Value لكل Header.
