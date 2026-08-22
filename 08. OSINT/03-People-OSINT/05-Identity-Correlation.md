# Identity Correlation

## يعني إيه؟
Correlation ربط records محتملة بكيان واحد باستخدام عدة attributes.

## ليه مهم؟
يمنع أن username أو الاسم يتحول إلى accusation.

## بيشتغل إزاي؟
اعمل جدول: identifier، source، date، supporting، contradicting، confidence. احتفظ ببدائل.

## مثال بسيط
ثلاثة records تشترك في domain وproject date ورابط رسمي؛ ما زال label “likely” وليس “certain”.

## Cybersecurity
في IOC analysis استخدم scoring شفافًا ومراجعة بشرية.

## Tools
Spreadsheet أو graph tool في lab.

## Common Mistakes
double-counting نفس المصدر، confirmation bias، وعدم تسجيل negative evidence.

## Exercises
أنشئ scoring بسيط: مستقل=2، متكرر=0، تناقض=-2.

## Mini Challenge
ما الذي يخفض confidence؟ اختلاف timezone وغياب الرابط الرسمي.

## Summary
Correlation قابل للتدقيق وليس حدسًا.
