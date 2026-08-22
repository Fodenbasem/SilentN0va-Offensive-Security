# OSINT vs Reconnaissance

## يعني إيه؟
OSINT أوسع: جمع وتحليل Public Information. **Reconnaissance** مرحلة في Security Assessment هدفها فهم Target ضمن Authorization.

## ليه مهم؟
التمييز يمنع scope creep. بحث عام عن Domain قد يكون OSINT، لكن enumeration أو request متكرر قد يدخل Active Recon ويحتاج تصريحًا واضحًا.

## بيشتغل إزاي؟
حدد نوع النشاط: هل تقرأ مصدرًا موجودًا أم تتفاعل مع Target؟ سجّل حدود الـengagement، ثم اختبر بأقل تأثير.

## مثال بسيط
قراءة Certificate Transparency لـنطاق تملكه Passive OSINT؛ فحص endpoint بمئات الطلبات Recon نشط.

## Cybersecurity
Pentester يستخدم OSINT للتحضير، ثم يطلب موافقة قبل scanning. Analyst يستخدمه لبناء context بدون touching systems.

## Tools
Browser وRDAP للـpassive؛ أدوات scanning لا تُستخدم إلا بتصريح.

## Common Mistakes
تسمية كل شيء OSINT، أو اعتبار Public target موافقة ضمنية.

## Exercises
صنّف: قراءة صفحة، DNS query، port scan، Login test. اكتب مستوى التفاعل والـauthorization المطلوب.

## Mini Challenge
اعمل Scope sentence يسمح بقراءة DNS وCT فقط، ويمنع exploitation.

## Summary
افهم الحد الفاصل قبل تشغيل أي Tool.
