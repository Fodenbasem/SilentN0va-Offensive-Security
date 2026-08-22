# Google Dorks بشكل مسؤول

## يعني إيه؟
Dork query مركبة للعثور على content عام بطريقة دقيقة. المصطلح لا يعني اختراقًا.

## ليه مهم؟
يفيد في defensive audit، لكنه قد يكشف بيانات حساسة بالصدفة.

## بيشتغل إزاي؟
استخدم نطاق lab، queries منخفضة الحساسية مثل policy وdocumentation، وبلّغ owner بدل تنزيل data.

## مثال بسيط
`site:example.org filetype:pdf intitle:guide` للملفات التعليمية العامة.

## Cybersecurity
يساعد inventory للـpublic exposure ضمن authorization.

## Tools
Search engine، notes، disclosure template.

## Common Mistakes
استهداف كلمات مثل password، تخزين نتائج حساسة، أو تشغيل آلاف queries آليًا.

## Exercises
صمم ثلاث dorks آمنة لا تبحث عن credentials.

## Mini Challenge
نتيجة تعرض secret بالخطأ: ما الذي لا تفعله؟ لا تفتح نسخًا إضافية، لا تنشر، وثّق وبلّغ.

## Summary
استخدم الدقة لتقليل المخاطر لا لزيادة الوصول.
