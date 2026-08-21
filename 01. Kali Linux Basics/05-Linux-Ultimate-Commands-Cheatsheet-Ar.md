# مرجع أوامر لينكس الشامل (Master Linux Commands Cheat Sheet)

هذا الملف يحتوي على أهم أوامر نظام تشغيل لينكس (Linux) المستخدمة في إدارة الأنظمة، التعامل مع الملفات، الشبكات، والمراقبة، بالإضافة لأوامر اختبار الاختراق والأمن السيبراني.

---

## 1. إدارة الملفات والمجلدات (File and Directory Management)

### 1. pwd (Print Working Directory)
- **الشرح:** يعرض المسار الحالي الكامل للمجلد الذي تقف عليه الآن.
- **مثال:**
```bash
pwd
```

### 2. ls (List)
- **الشرح:** عرض قائمة الملفات والمجلدات الموجودة في المجلد الحالي.
- **مثال:**
```bash
ls -la /var/log
```

### 3. cd (Change Directory)
- **الشرح:** التنقل بين المجلدات والمسارات المختلفة.
- **مثال:**
```bash
cd /var/www/html
```

### 4. mkdir (Make Directory)
- **الشرح:** إنشاء مجلد جديد.
- **مثال:**
```bash
mkdir -p project/notes/screenshots
```

### 5. rmdir (Remove Directory)
- **الشرح:** حذف مجلد فارغ فقط.
- **مثال:**
```bash
rmdir empty_folder
```

### 6. rm (Remove)
- **الشرح:** حذف الملفات أو المجلدات بشكل دائم.
- **مثال:**
```bash
rm -rf project_folder
```

### 7. cp (Copy)
- **الشرح:** نسخ الملفات أو المجلدات من مكان إلى آخر.
- **مثال:**
```bash
cp -r /var/www/html /backup/html_backup
```

### 8. mv (Move / Rename)
- **الشرح:** نقل ملف أو تغيير اسمه.
- **مثال:**
```bash
mv old_name.txt new_name.txt
```

### 9. touch (Touch File)
- **الشرح:** إنشاء ملف فارغ جديد أو تحديث تاريخ التعديل الخاص بملف موجود.
- **مثال:**
```bash
touch test.txt
```

### 10. tree (Directory Tree)
- **الشرح:** عرض المجلدات والملفات داخلها على شكل شجرة متفرعة.
- **مثال:**
```bash
tree -L 2
```

### 11. stat (Status)
- **الشرح:** عرض تفاصيل دقيقة جداً عن الملف (الحجم، الصلاحيات، تاريخ الإنشاء والتعديل).
- **مثال:**
```bash
stat /etc/passwd
```

### 12. ln (Link)
- **الشرح:** إنشاء اختصار (Symbolic Link) أو رابط صلب (Hard Link) لملف.
- **مثال:**
```bash
ln -s /var/log/syslog ~/syslog_link
```

---

## 2. قراءة وعرض محتوى الملفات (Viewing File Contents)

### 13. cat (Concatenate)
- **الشرح:** عرض محتوى الملف كاملاً على الشاشة.
- **مثال:**
```bash
cat /etc/passwd
```

### 14. tac (Reverse Cat)
- **الشرح:** عرض محتوى الملف بشكل معكوس (من آخر سطر إلى أول سطر).
- **مثال:**
```bash
tac /var/log/auth.log
```

### 15. less (Less Viewer)
- **الشرح:** فتح الملف واستعراضه بالصفحات بسهولة وسرعة دون تحميله كاملاً بالذاكرة.
- **مثال:**
```bash
less /var/log/syslog
```

### 16. head (Head Lines)
- **الشرح:** عرض الأسطر الأولى من بداية الملف (افتراضياً 10 أسطر).
- **مثال:**
```bash
head -n 20 /etc/passwd
```

### 17. tail (Tail Lines)
- **الشرح:** عرض الأسطر الأخيرة من الملف، وتُستخدم بكثرة لمتابعة اللوجات مباشرة.
- **مثال:**
```bash
tail -f /var/log/syslog
```

### 18. nl (Number Lines)
- **الشرح:** عرض محتوى الملف مع ترقيم الأسطر.
- **مثال:**
```bash
nl /etc/hosts
```

### 19. xxd (Hex Dump)
- **الشرح:** عرض المحتوى الباينري للملف بصيغة Hexadecimal (الستة عشرية).
- **مثال:**
```bash
xxd binary_file
```

### 20. strings (Printable Strings)
- **الشرح:** استخراج النصوص المطبوعة والواضحة من داخل الملفات المبرمجة والباينري.
- **مثال:**
```bash
strings /bin/ls
```

---

## 3. البحث وتحديد الأماكن (Search & Locate)

### 21. find (Find Files)
- **الشرح:** البحث الشامل عن الملفات والمجلدات حسب الاسم، الحجم، الصلاحيات، أو المالك.
- **مثال:**
```bash
find /var -name "*.log" -type f
```

### 22. locate (Locate Database)
- **الشرح:** البحث السريع جداً عن الملفات باستخدام قاعدة بيانات النظام المسجلة.
- **مثال:**
```bash
locate id_rsa
```

### 23. which (Which Executable)
- **الشرح:** إظهار المسار الكامل للبرنامج أو الأمر المستدعى.
- **مثال:**
```bash
which nmap
```

### 24. whereis (Where is Binary/Source)
- **الشرح:** عرض مسار ملف الباينري، السورس كود، وملف المساعدة (Man page) الخاص بالأمر.
- **مثال:**
```bash
whereis python3
```

---

## 4. معالجة النصوص والفلترة (Text Processing & Filtering)

### 25. grep (Global Regular Expression)
- **الشرح:** البحث عن كلمة أو نمط معين داخل النص أو الملفات.
- **مثال:**
```bash
grep -rn "root" /etc/
```

### 26. awk (Pattern Scanning)
- **الشرح:** لغة معالجة واستخراج الأعمدة والبيانات المنسقة من النص.
- **مثال:**
```bash
awk -F':' '{print $1, $6}' /etc/passwd
```

### 27. sed (Stream Editor)
- **الشرح:** تعديل واستبدال النصوص داخل الملفات تلقائياً.
- **مثال:**
```bash
sed -i 's/http/https/g' config.txt
```

### 28. cut (Cut Out Fields)
- **الشرح:** قص جزء معين أو عمود من أسطر النص بناءً على فاصلة محددة.
- **مثال:**
```bash
cut -d':' -f1 /etc/passwd
```

### 29. sort (Sort Lines)
- **الشرح:** ترتيب أسطر الملفات أبجدياً أو رقمياً.
- **مثال:**
```bash
sort -n numbers.txt
```

### 30. uniq (Report Unique Lines)
- **الشرح:** إزالة الأسطر المكررة أو حساب تكرارها (يجب استخدام sort قبله).
- **مثال:**
```bash
sort ips.txt | uniq -c
```

### 31. wc (Word Count)
- **الشرح:** حساب عدد الأسطر، الكلمات، أو الأحرف في الملف.
- **مثال:**
```bash
wc -l /etc/passwd
```

### 32. tr (Translate/Delete)
- **الشرح:** استبدال أو حذف أحرف معينة من النص.
- **مثال:**
```bash
cat text.txt | tr 'a-z' 'A-Z'
```

### 33. diff (Difference)
- **الشرح:** مقارنة ملفين ونصين وإظهار الفروقات بينهما سطر بسطر.
- **مثال:**
```bash
diff file1.txt file2.txt
```

### 34. xargs (Build Command Arguments)
- **الشرح:** أخذ المخرجات وتحويلها كمدخلات وأوامر لأوامر أخرى.
- **مثال:**
```bash
find . -name "*.tmp" | xargs rm -f
```

---

## 5. الصلاحيات والملكية (Permissions and Ownership)

### 35. chmod (Change Mode)
- **الشرح:** تغيير صلاحيات القراءة، الكتابة، والتشغيل للملفات والمجلدات.
- **مثال:**
```bash
chmod 755 script.sh
```

### 36. chown (Change Owner)
- **الشرح:** نقل ملكية الملف أو المجلد لمستخدم أو مجموعة أخرى.
- **مثال:**
```bash
sudo chown -R kali:kali /var/www/html
```

### 37. chgrp (Change Group)
- **الشرح:** تغيير المجموعة المالكة للملف.
- **مثال:**
```bash
sudo chgrp www-data index.php
```

### 38. umask (User Mask)
- **الشرح:** تحديد الصلاحيات الافتراضية للملفات والمجلدات الجديدة عند إنشائها.
- **مثال:**
```bash
umask 022
```

### 39. getfacl (Get File ACL)
- **الشرح:** عرض قائمة التحكم بالوصول المتقدمة (ACL) للملف.
- **مثال:**
```bash
getfacl /var/www/
```

### 40. setfacl (Set File ACL)
- **الشرح:** إعطاء صلاحيات مخصصة لمستخدمين محددين على ملف أو مجلد بدون تغيير مالك الملف.
- **مثال:**
```bash
setfacl -m u:kali:rwx /var/www/
```

---

## 6. إدارة المستخدمين والمجموعات (Users & Groups Management)

### 41. whoami (Who Am I)
- **الشرح:** إظهار اسم المستخدم الحالي المنفذ للأمر.
- **مثال:**
```bash
whoami
```

### 42. id (Identify User)
- **الشرح:** عرض المعرف الرقمي للمستخدم (UID) والمجموعات المسجل بها (GID).
- **مثال:**
```bash
id kali
```

### 43. useradd (Add User)
- **الشرح:** إنشاء حساب مستخدم جديد بالنظام.
- **مثال:**
```bash
sudo useradd -m -s /bin/bash newuser
```

### 44. userdel (Delete User)
- **الشرح:** حذف حساب مستخدم ومجلده الخاص.
- **مثال:**
```bash
sudo userdel -r olduser
```

### 45. usermod (Modify User)
- **الشرح:** تعديل بيانات وصلاحيات والمجموعات الخاصة بمستخدم معين.
- **مثال:**
```bash
sudo usermod -aG sudo kali
```

### 46. groupadd (Add Group)
- **الشرح:** إنشاء مجموعة مستخدمين جديدة.
- **مثال:**
```bash
sudo groupadd developers
```

### 47. passwd (Password)
- **الشرح:** تغيير كلمة السر الخاصة بملك الحساب أو لمستخدم آخر.
- **مثال:**
```bash
sudo passwd kali
```

### 48. su (Switch User)
- **الشرح:** التبديل لحساب مستخدم آخر أو حساب الـ Root.
- **مثال:**
```bash
su - root
```

### 49. sudo (Superuser Do)
- **الشرح:** تنفيذ أمر مع صلاحيات المدير (Root).
- **مثال:**
```bash
sudo apt update
```

### 50. w (Who is Logged in)
- **الشرح:** عرض قائمة المستخدمين المتصلين بالنظام حالياً مع المهام التي ينفذونها.
- **مثال:**
```bash
w
```

### 51. last (Last Logged In Users)
- **الشرح:** عرض سجل بعمليات تسجيل الدخول الأخيرة للمستخدمين في النظام.
- **مثال:**
```bash
last -n 10
```

---

## 7. مراقبة وإدارة العمليات والذاكرة (Process & Memory Management)

### 52. ps (Process Status)
- **الشرح:** عرض قائمة بالعمليات والبرامج الشغالة حالياً على النظام.
- **مثال:**
```bash
ps aux
```

### 53. top (Table of Processes)
- **الشرح:** شاشة تفاعلية حية تظهر العمليات واستهلاك الـ CPU والذاكرة.
- **مثال:**
```bash
top
```

### 54. htop (Interactive Process Viewer)
- **الشرح:** أداة تفاعلية متطورة وملونة لمراقبة النظام والعمليات بشكل أسهل من top.
- **مثال:**
```bash
htop
```

### 55. pgrep (Process Grep)
- **الشرح:** البحث عن معرف العملية (PID) باسم البرامج.
- **مثال:**
```bash
pgrep apache2
```

### 56. kill (Kill Process)
- **الشرح:** إيقاف وإنهاء عملية معينة باستخدام الرقم الخاص بها (PID).
- **مثال:**
```bash
kill -9 1234
```

### 57. killall (Kill All Processes)
- **الشرح:** إنهاء جميع العمليات التي تحمل اسماً معيناً دفعة واحدة.
- **مثال:**
```bash
sudo killall python3
```

### 58. pkill (Process Kill)
- **الشرح:** إرسال إشارة إيقاف للعمليات بناءً على الاسم أو مالك العملية.
- **مثال:**
```bash
pkill -u kali
```

### 59. bg (Background)
- **الشرح:** إرسال أداة أو عملية معطلة مؤقتاً لتعمل في الخلفية.
- **مثال:**
```bash
bg %1
```

### 60. fg (Foreground)
- **الشرح:** سحب وإرجاع عملية شغالة في الخلفية للعمل في الواجهة المباشرة.
- **مثال:**
```bash
fg %1
```

### 61. jobs (List Jobs)
- **الشرح:** عرض المهام التي تعمل حالياً في خلفية الطرفية الحالية.
- **مثال:**
```bash
jobs
```

### 62. nohup (No Hang Up)
- **الشرح:** تشغيل أمر في الخلفية ويضمن استمراريته حتى لو أغلقت الـ Terminal.
- **مثال:**
```bash
nohup python3 script.py &
```

### 63. free (Free Memory)
- **الشرح:** عرض المساحة المستخدمة والمتبقية من الـ RAM والـ Swap.
- **مثال:**
```bash
free -h
```

### 64. uptime (System Uptime)
- **الشرح:** إظهار مدة تشغيل النظام ومتوسط الحمل (Load Average).
- **مثال:**
```bash
uptime
```

---

## 8. الشبكات والفحص (Networking & Reconnaissance)

### 65. ip (IP Route/Address)
- **الشرح:** التحكم وعرض العناوين والمنافذ والمسارات الخاصة بالشبكة.
- **مثال:**
```bash
ip a
```

### 66. ifconfig (Interface Configuration)
- **الشرح:** الأمر الكلاسيكي لعرض وتعديل إعدادات أجهزة الشبكة والـ IP.
- **مثال:**
```bash
ifconfig eth0
```

### 67. ping (Packet Internet Groper)
- **الشرح:** اختبار الاتصال بين جهازك وجهاز أو سيرفر آخر عن طريق حزم ICMP.
- **مثال:**
```bash
ping -c 4 8.8.8.8
```

### 68. netstat (Network Statistics)
- **الشرح:** عرض المنافذ (Ports) المفتوحة والاتصالات الحية للشبكة.
- **مثال:**
```bash
netstat -tulpn
```

### 69. ss (Socket Statistics)
- **الشرح:** البديل الحديث والسريع لأمر netstat لعرض المنافذ المفتوحة والـ Connections.
- **مثال:**
```bash
ss -tulpn
```

### 70. traceroute (Trace Route)
- **الشرح:** تتبع مسار الحزم والموجهات (Routers) التي تمر بها للوصول للهدف.
- **مثال:**
```bash
traceroute google.com
```

### 71. dig (Domain Information Groper)
- **الشرح:** استعلام وتتبع سجلات الـ DNS الخاصة بالدومين.
- **مثال:**
```bash
dig example.com ANY
```

### 72. nslookup (Name Server Lookup)
- **الشرح:** أداة سريعة لمعرفة الـ IP الخاص بأي موقع أو العكس.
- **مثال:**
```bash
nslookup google.com
```

### 73. host (Host Lookup)
- **الشرح:** أداة تحويل اسم الموقع إلى IP أو IP إلى اسم الموقع بشكل مبسط.
- **مثال:**
```bash
host 8.8.8.8
```

### 74. curl (Client URL)
- **الشرح:** إرسال واستقبال البيانات والطلبات عبر بروتوكولات الشبكة المختلفة (HTTP, HTTPS, FTP).
- **مثال:**
```bash
curl -I https://example.com
```

### 75. wget (Web Get)
- **الشرح:** تحميل الملفات والمستندات مباشرة من الإنترنت عبر Terminal.
- **مثال:**
```bash
wget https://example.com/file.zip
```

### 76. nc / netcat (Netcat)
- **الشرح:** سكين السويسري للشبكات، يُستخدم لقراءة وكتابة البيانات عبر اتصالات الشبكة، فتح بورتات، والـ Reverse Shells.
- **مثال:**
```bash
nc -nvlp 4444
```

### 77. socat (Socket Cat)
- **الشرح:** أداة شبكات متطورة جداً تشبه netcat لكنها تدعم التشفير والـ TTY Shells.
- **مثال:**
```bash
socat TCP-LISTEN:4444 STDOUT
```

### 78. nmap (Network Mapper)
- **الشرح:** أشهر أداة لفحص الشبكات والمنافذ المفتوحة والخدمات وشغور الثغرات.
- **مثال:**
```bash
nmap -sV -sC -p- 192.168.1.1
```

### 79. tcpdump (Dump TCP Traffic)
- **الشرح:** التقاط وتحليل حركة الترافيك المتداولة بالشبكة (Packet Sniffer).
- **مثال:**
```bash
sudo tcpdump -i eth0 port 80
```

---

## 9. ضغط وأرشفة الملفات والنقل (Archiving, Compression & Transfer)

### 80. tar (Tape Archive)
- **الشرح:** أرشفة وضغط أو فك ضغط مجموعة من الملفات في حزمة واحدة.
- **مثال:**
```bash
tar -czvf archive.tar.gz /path/to/folder
```

### 81. gzip (GNU Zip)
- **الشرح:** ضغط الملفات الفردية لتقليل حجمها.
- **مثال:**
```bash
gzip logfile.txt
```

### 82. gunzip (GNU Unzip)
- **الشرح:** فك ضغط الملفات المضغوطة باستخدام gzip.
- **مثال:**
```bash
gunzip logfile.txt.gz
```

### 83. zip / unzip (Zip Compression)
- **الشرح:** ضغط وفك ضغط الملفات بصيغة zip واسعة الانتشاء.
- **مثال:**
```bash
unzip archive.zip
```

### 84. scp (Secure Copy)
- **الشرح:** نقل الملفات بأمان بين الأجهزة عبر بروتوكول SSH المشفّر.
- **مثال:**
```bash
scp file.txt user@192.168.1.50:/home/user/
```

### 85. rsync (Remote Sync)
- **الشرح:** مزامنة ونقل الملفات الذكي محلياً أو عن بعد مع حفظ الصلاحيات.
- **مثال:**
```bash
rsync -avz /local/folder/ user@192.168.1.50:/remote/folder/
```

---

## 10. القرص الصلب وأنظمة الملفات (Disk & File Systems)

### 86. df (Disk Free)
- **الشرح:** عرض المساحة الفارغة والمستخدمة على أجهزة التخزين والبارتيشنات.
- **مثال:**
```bash
df -h
```

### 87. du (Disk Usage)
- **الشرح:** عرض حجم استهلاك مجلد أو ملف معين على الهارد ديسك.
- **مثال:**
```bash
du -sh /var/log/*
```

### 88. lsblk (List Block Devices)
- **الشرح:** عرض أقسام التخزين (Disks and Partitions) الشغالة على الجهاز بنظام شجري.
- **مثال:**
```bash
lsblk
```

### 89. fdisk (Format Disk / Partition)
- **الشرح:** أداة للتحكم وإنشاء وتعديل وتقسيم الهارد ديسك (Partition Table).
- **مثال:**
```bash
sudo fdisk -l
```

### 90. mount (Mount Filesystem)
- **الشرح:** ربط البارتيشن أو الفلاشة بمجلد معين بالنظام لتتمكن من الوصول لملفاتها.
- **مثال:**
```bash
sudo mount /dev/sdb1 /mnt/usb
```

### 91. umount (Unmount Filesystem)
- **الشرح:** فصل الجهاز أو الفلاشة بأمان بعد الانتهاء من استخدامه.
- **مثال:**
```bash
sudo umount /mnt/usb
```

---

## 11. إدارة حزم البرامج والخدمات (Package Management & Services)

### 92. apt / apt-get (Advanced Package Tool)
- **الشرح:** الأداة الرسمية لإدارة وتثبيت وتحديث البرامج على توزيعات دبيان وكالي.
- **مثال:**
```bash
sudo apt update && sudo apt install -y nmap
```

### 93. dpkg (Debian Package)
- **الشرح:** تثبيت وإدارة ملفات البرامج المنتهية بـ `.deb` مباشرة.
- **مثال:**
```bash
sudo dpkg -i package.deb
```

### 94. systemctl (System Control)
- **الشرح:** التحكم في تشغيل، إيقاف، وإعادة تشغيل الخدمات التابعة لنظام Systemd.
- **مثال:**
```bash
sudo systemctl restart apache2
```

### 95. journalctl (Journal Control)
- **الشرح:** استعراض وقراءة سجلات اللوجات المجمعة بواسطة Systemd.
- **مثال:**
```bash
journalctl -u sshd -f
```

---

## 12. أوامر التشفير وأمان المعلومات (Security & Encryption Essentials)

### 96. base64 (Base64 Encode/Decode)
- **الشرح:** تشفير وتفكيك النصوص والبيانات باستخدام نظام التشفير Base64.
- **مثال:**
```bash
echo "hello" | base64
```

### 97. md5sum / sha256sum (Checksum Hash)
- **الشرح:** حساب البصمة الرقمية (Hash) للملفات للتأكد من سلامتها وعدم التلاعب بها.
- **مثال:**
```bash
sha256sum kali.iso
```

### 98. ssh (Secure Shell)
- **الشرح:** الاتصال الآمن بالسيرفرات والأجهزة عن بعد عبر تشفير SSH.
- **مثال:**
```bash
ssh -i key.pem user@192.168.1.100
```

### 99. chroot (Change Root)
- **الشرح:** تشغيل بيئة عمل وتغيير المجلد الرئيسي (Root Directory) بعيداً عن باقي النظام لأسباب أمنية.
- **مثال:**
```bash
sudo chroot /mnt/target_system
```

### 100. history (Command History)
- **الشرح:** عرض قائمة بالأوامر التي تم تنفيذها سابقاً في الـ Terminal.
- **مثال:**
```bash
history | grep "chmod"
```
