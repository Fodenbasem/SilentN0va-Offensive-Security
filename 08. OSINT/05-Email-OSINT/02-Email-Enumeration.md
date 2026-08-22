# Email Enumeration

## يعني إيه؟
اكتشاف email patterns أو addresses منشورة Public داخل organization scope.

## ليه مهم؟
قد يكشف exposure أو impersonation، لكنه لا يبرر mailbox testing.

## بيشتغل إزاي؟
اجمع من official pages وdocuments العامة، mask local-parts في notes، وسجل المصدر.

## مثال بسيط
صفحتان public تعرضان `a.surname@example.org` و`s.surname@example.org`؛ نستنتج pattern محتمل لا mailbox validity.

## Cybersecurity
يساعد phishing simulation المصرح به وbrand protection.

## Tools
Search operators آمنة، PDF metadata، RDAP.

## Common Mistakes
بناء قائمة ضخمة، إرسال رسائل اختبار، أو شراء breach data.

## Exercises
استنتج pattern من ثلاثة أسماء fictional.

## Mini Challenge
ما الحد الأخلاقي؟ لا تختبر وجود mailbox ولا تجمع personal addresses.

## Summary
Pattern analysis ليس account verification.
