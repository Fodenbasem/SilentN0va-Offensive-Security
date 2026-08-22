# Breach Awareness

## يعني إيه؟
التوعية بالتسريبات تعني فهم الخطر ومراقبة assets المصرح بها، لا البحث عن أو تنزيل leaked data.

## ليه مهم؟
بيانات breach قد تحتوي credentials وPII وتسبب ضررًا قانونيًا وأمنيًا.

## بيشتغل إزاي؟
استخدم notification services الرسمية، تحقق من incident، rotate credentials عبر owner، واحتفظ بأقل evidence.

## مثال بسيط
تنبيه رسمي يقول إن domain fictional ظهر في incident؛ لا نحاول login، بل نطبق reset وMFA.

## Cybersecurity
يخدم incident response وcredential hygiene.

## Tools
Have I Been Pwned domain verification للـdomain owner، password manager، SIEM.

## Common Mistakes
تصفح forums، اختبار passwords، أو إعادة نشر dumps.

## Exercises
اكتب playbook من خمس خطوات بعد تنبيه breach.

## Mini Challenge
ما الذي يثبت notification؟ المصدر والتاريخ، لا صحة كل record.

## Summary
راقب exposure بطريقة قانونية ودفاعية.

## References
[Have I Been Pwned](https://haveibeenpwned.com/)، [NIST Passwords](https://pages.nist.gov/800-63-4/sp800-63b.html).
