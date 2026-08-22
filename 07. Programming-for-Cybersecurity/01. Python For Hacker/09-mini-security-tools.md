# Chapter 09: Building Mini Security Tools 🛠️🔥

## مقدمة بسيطة
دلوقتي وقت التجميع! إحنا مش بنتعلم بايثون عشان نبقى مبرمجين ويب، إحنا بنتعلمها عشان نبني Security Tools. هنبني أدوات مصغرة مفيدة جداً وتقدر تستخدمها في الـ Labs أو CTFs.

---

## Tool 1: HTTP Header Analyzer
**الفكرة**: أداة بتجيب الـ HTTP Headers وتدور على الـ Security Headers المفقودة.

```python
import requests

def analyze_headers(url):
    print(f"\n[*] Analyzing Security Headers for: {url}")
    try:
        headers = {"User-Agent": "Mozilla/5.0"}
        response = requests.get(url, headers=headers, timeout=5)
        
        security_headers = ["Strict-Transport-Security", "X-Frame-Options"]
        for header in security_headers:
            if header in response.headers:
                print(f"[+] Found: {header}")
            else:
                print(f"[-] Missing: {header} (Potential Misconfiguration!)")
    except Exception as e:
        print(f"[!] Error: {e}")
```

---

## Tool 2: Password Strength Checker
**الفكرة**: أداة بتفحص قوة الباسوورد.

```python
def check_password_strength(password):
    score = 0
    if len(password) >= 8: score += 1
    if any(char.isdigit() for char in password): score += 1
    if any(char.isupper() for char in password): score += 1
    
    special_chars = "!@#$%^&*()-+"
    if any(char in special_chars for char in password): score += 1
        
    print(f"[*] Analyzing Password: {'*' * len(password)}")
    if score == 4:
        print("[+] Strength: STRONG")
    elif score >= 2:
        print("[!] Strength: MEDIUM")
    else:
        print("[-] Strength: WEAK")
```

---

## Tool 3: Subdomain Wordlist Checker
**الفكرة**: أداة بتاخد دومين ولستة كلمات وتعمل Request تشوفه شغال ولا لأ.

```python
import requests

def discover_subdomains(domain, wordlist):
    print(f"\n[*] Starting Enumeration for: {domain}")
    for word in wordlist:
        subdomain = f"http://{word}.{domain}"
        try:
            response = requests.get(subdomain, timeout=2)
            if response.status_code == 200:
                print(f"[+] Discovered: {subdomain}")
        except requests.exceptions.RequestException:
            pass
```

---

## Mini Challenge 🏆
طوّر أداة **Tool 3**:
بدل ما تقرأ الكلمات من List عادية، خلي الكود يقرأ الكلمات من ملف `subdomains.txt`.
(Hint: افتح الملف، اقرأ السطور بـ `readlines()`، واعمل `.strip()` لكل سطر).
