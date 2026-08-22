# Chapter 10: Final Hacker Project 💻💀

## مقدمة
وصلنا لنهاية الرحلة! إنت دلوقتي جاهز تبني الـ **Toolkit** الخاصة بيك. هنجمع الأدوات اللي اتعلمناها ونحطها في سكريبت واحد منظم ليه واجهة استخدام (CLI Menu). هنسمي الأداة دي **0xSN Security Toolkit**.

## 1. الـ Architecture (تقسيم الكود)
المشاريع الكبيرة بتتقسم:
- **Imports**: المكتبات.
- **Functions**: كل دالة بتعمل وظيفة واحدة.
- **Menu Function**: تعرض القائمة.
- **Main Block**: المكان اللي السكريبت بيبدأ منه.

## 2. الكود الكامل للمشروع (0xSN Security Toolkit)

```python
import socket
import requests
import hashlib
import sys
import time

def port_scanner(ip, ports):
    print(f"\n[*] Scanning {ip}...")
    for port in ports:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(1)
        if s.connect_ex((ip, port)) == 0:
            print(f"[+] Port {port}/TCP is OPEN")
        s.close()
    print("[*] Scan completed.")

def hash_calculator(text):
    md5_hash = hashlib.md5(text.encode()).hexdigest()
    print(f"\n[*] String: {text}\n[-] MD5: {md5_hash}")

def web_analyzer(url):
    print(f"\n[*] Analyzing {url}...")
    try:
        if not url.startswith("http"): url = "http://" + url
        response = requests.get(url, timeout=5)
        print(f"[+] Status Code: {response.status_code}")
        print(f"[+] Server Header: {response.headers.get('Server', 'Hidden')}")
    except requests.exceptions.RequestException as e:
        print(f"[!] Error: {e}")

def show_menu():
    print("\n" + "="*40)
    print("      0xSN Security Toolkit v1.0")
    print("="*40)
    print("[1] Quick Port Scanner")
    print("[2] Hash Calculator")
    print("[3] Web Analyzer")
    print("[99] Exit")
    print("="*40)

def main():
    while True:
        show_menu()
        choice = input("0xSN@toolkit:~# Select an option: ")
        
        if choice == '1':
            target = input("Enter Target IP: ")
            port_scanner(target, [21, 22, 80, 443, 8080])
            time.sleep(1)
        elif choice == '2':
            text = input("Enter text to hash: ")
            hash_calculator(text)
            time.sleep(1)
        elif choice == '3':
            url = input("Enter Target URL: ")
            web_analyzer(url)
            time.sleep(1)
        elif choice == '99':
            print("\n[*] Shutting down... Happy Hacking! 💀")
            sys.exit(0)
        else:
            print("\n[!] Invalid choice!")

if __name__ == "__main__":
    try:
        main()
    except KeyboardInterrupt:
        print("\n\n[!] Execution interrupted by user. Exiting...")
        sys.exit(0)
```

## 3. شرح المشروع والـ Security Considerations
- **`while True:`**: بتخلي المنيو تفضل شغالة علطول.
- **`time.sleep(1)`**: بتدي فرصة لليوزر يقرأ النتيجة.
- **`if __name__ == "__main__":`**: معناها "لو أنا شغلت الملف ده بنفسي نفذ دالة `main()`".
- **`KeyboardInterrupt`**: لو اليوزر داس `CTRL+C`، السكريبت بيقفل بشياكة بدون Error بشع.

## Final Challenge 🏆
ضيف خيار `[4]` في المنيو يكون **"IP Information Finder"**.
استخدم `requests.get("http://ip-api.com/json/" + ip).json()` عشان تقرأ بيانات الـ IP كـ Dictionary، واطبع البلد والشركة.

## Roadmap للانتقال من Python Basics للـ Pentesting
عاش يا بطل! الخطوة الجاية:
1. اتعلم Object Oriented Programming (OOP).
2. اتعلم مكتبة `Scapy` لصناعة الـ Packets والتلاعب في الشبكة.
3. اتعلم تتعامل مع الـ Web Scraping بـ `BeautifulSoup`.
4. ابدأ ادرس Exploit Development.

استمر في التحديات، مجالنا مبيقفش. Keep Hacking, Stay Legal! 🐍💀
