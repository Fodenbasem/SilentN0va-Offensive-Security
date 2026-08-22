# Certificate Transparency

## يعني إيه؟
CT logs سجلات عامة لشهادات TLS صادرة، وقد تحتوي SANs وsubdomains.

## ليه مهم؟
تكشف أسماء ظهرت في certificates حتى لو لم تعد مستخدمة.

## بيشتغل إزاي؟
ابحث عن domain في log monitor، deduplicate، ثم تحقق من DNS والـdate.

## مثال بسيط
شهادة fictional تسجل `api.example.org` في 2025؛ لا نستنتج أنها حية في 2026.

## Cybersecurity
early asset discovery وdefensive monitoring.

## Tools
[crt.sh](https://crt.sh/) وCertificate Transparency monitors.

## Common Mistakes
اعتبار SAN ownership، تجاهل wildcard، وعدم ملاحظة revocation.

## Exercises
صنف results إلى current/old/unknown.

## Mini Challenge
اكتب limitation لكل CT finding.

## Summary
CT historical clue قوي نسبيًا، لكنه يحتاج corroboration.
