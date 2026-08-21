# الدليل الشامل والاحترافي لإدارة حملات التصيد بالـ GoPhish (Phishing Infrastructure & GoPhish Mastery)

هذا الدليل يغطي كيفية بناء وتصميم وبناء البنية التحتية لحملات الهندسة الاجتماعية والاختبار الميداني للهجوم عبر البريد الإلكتروني (Phishing) باستخدام منصة GoPhish، بدءاً من حجز الدومينات وحتى تجاوز فلاتر الحماية وتصميم صفحات الهبوط.

---

## 1. بناء البنية التحتية للهجوم (Phishing Infrastructure Setup)

لكي تضمن وصول رسائل البريد الإلكتروني إلى صندوق الوارد (Inbox) بدلاً من بريد المباشر للمخلفات (Spam)، يجب إعداد السيرفر وسجلات الـ DNS بعناية فائقة.

### 1.1 حجز وشراء الدومينات المماثلة (Typosquatting & Lookalike Domains)
* **الفكرة:** حجز اسم نطاق يشبه النطاق الأصلي للمؤسسة المستهدفة.
* **الأدوات:** استخدام أداة `dnstwist` لاكتشاف واستخراج الدومينات المتاحة.
```bash
dnstwist --registered targetcompany.com
```
* **الأمثلة:**
  * النطاق الأصلي: `company.com`
  * النطاق المزيف: `comраny.com` (Cyrillic homograph) أو `company-portal.com`

### 1.2 إعداد سجلات مصادقة البريد الإلكتروني (SPF, DKIM, DMARC)
يجب ربط السيرفر الهجومي بهذه السجلات داخل لوحة تحكم الـ DNS لمنع السيرفرات المستقبلة من رفض الرسائل.

* **سجل SPF (Sender Policy Framework):**
  يحدد الآي بي المسموح له بإرسال البريد نيابة عن الدومين.
  ```text
  v=spf1 ip4:YOUR_ATTACKER_IP ~all
  ```

* **سجل DKIM (DomainKeys Identified Mail):**
  يضيف توقيعاً رقمياً تشفيرياً للرسالة لتأكيد أنها لم تتغير أثناء النقل.
  ```text
  v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQ...
  ```

* **سجل DMARC (Domain-based Message Authentication):**
  يحدد كيفية التعامل مع الرسائل التي تفشل في اختبارات SPF و DKIM.
  ```text
  v=DMARC1; p=none; rua=mailto:dmarc-reports@yourdomain.com
  ```

---

## 2. تثبيت وإعداد منصة GoPhish

أداة GoPhish هي إطار عمل مفتوح المصدر مصمم خصيصاً للمؤسسات والفرق الهجومية لترتيب واختبار الـ Phishing.

### 2.1 التثبيت والتجهيز على Kali Linux
```bash
# تحميل النسخة المجمعة جاهزة التشغيل
wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip
unzip gophish-v0.12.1-linux-64bit.zip
chmod +x gophish

# تشغيل المنصة
./gophish
```

### 2.2 تعديل بصمة GoPhish لتجاوز الحماية (Anti-GoPhish Detection)
تكتشف أنظمة الـ EDR وسيرفرات البريد منصة GoPhish من خلال الهيدرز الافتراضية والتوقيعات الخاصة بها. يتم إزالة هذه البصمات بتعديل ملف `config.json` وإعادة بناء السورس كود:
* تغيير اسم الهيدر `X-Gophish-Contact` إلى اسم عشوائي.
* تغيير اسم الهيدر `X-Gophish-Signature`.
* تغيير مسار الـ Server Header الافتراضي من `gophish` إلى `Apache` أو `nginx`.

---

## 3. خطوات بناء الحملة بالتفصيل (Campaign Components)

### 3.1 إعداد ملف الإرسال (Sending Profiles)
يقوم بربط السيرفر الهجومي بمنصة GoPhish عبر بروتوكول SMTP:
* **Host:** `smtp.yourdomain.com:587`
* **Username / Password:** بيانات الحساب المخصص للإرسال.
* **Custom Headers:** إضافة هيدرز وهمية لتبدو الرسالة صادرة من نظام إداري مثل Microsoft 365.

### 3.2 تصميم قوالب البريد (Email Templates)
يجب أن تتضمن الرسالة صياغة تثير استجابة سريعة من الضحية (Urgency, Authority, Fear of Loss).

```html
<html>
<head>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f4f4f4; padding: 20px; }
        .container { background-color: #ffffff; padding: 30px; border-radius: 5px; }
        .btn { background-color: #d9534f; color: white; padding: 10px 20px; text-decoration: none; border-radius: 3px; display: inline-block; }
    </style>
</head>
<body>
    <div class="container">
        <h2>تنبيه أمني عاجل: تعليق حسابك الإداري</h2>
        <p>عزيزي الموظف،</p>
        <p>لاحظ نظام الأمان لدينا محاولات دخول مشبوهة إلى حسابك المؤسسي من موقع جغرافي غير معروف.</p>
        <p>يرجى تأكيد ملكيتك للحساب وتحديث كلمة المرور فوراً لتجنب إيقاف الخدمة خلال 24 ساعة.</p>
        <p><a href="{{.URL}}" class="btn">تأكيد الحساب وتحديث البيانات</a></p>
        <p>مع تحيات،<br>فريق أمن المعلومات والشبكات</p>
    </div>
</body>
</html>
```

### 3.3 تصميم صفحة الهبوط واستيلاء البيانات (Landing Pages & Credential Harvesting)
الصفحة المزيفة التي يصل إليها الضحية بعد الضغط على الرابط. يفضل استخدام خيار **Import Page** داخل GoPhish لسحب كود HTML من صفحة الدخول الحقيقية للشركة.

مثال لكود استقبال وبيانات السجل (Capture Credentials & Redirect):
```html
<form action="" method="POST">
    <input type="email" name="email" placeholder="اسم المستخدم / البريد" required>
    <input type="password" name="password" placeholder="كلمة المرور" required>
    <button type="submit">تسجيل الدخول</button>
</form>
```
* **ملاحظة تكتيكية:** بعد استلام البيانات من الضحية، يفضل عمل **Redirect** تلقائي للضحية إلى صفحة الدخول الحقيقية أو صفحة توعية أمنية لعدم إثارة الشكوك.

---

## 4. قياس النتائج وتحليل الحملة (Analytics & Reporting)

بعد إطلاق الحملة، يوفر GoPhish لوحة تحكم شاملة تقوم بتتبع الآتي:
1. **Email Sent:** عدد الرسائل التي تم إرسالها بنجاح.
2. **Email Opened:** عدد الأشخاص الذين فتحوا الرسالة (عن طريق تتبع صورة بيجسل شافة Tracking Pixel).
3. **Clicked Link:** عدد الأشخاص الذين ضغطوا على الرابط المرفق.
4. **Submitted Data:** عدد الأشخاص الذين قاموا بإدخال بياناتهم وبيانات الدخول.
5. **Reported Email:** عدد الموظفين الذين قاموا بالإبلاغ عن الرسالة لفريق الـ SOC.
