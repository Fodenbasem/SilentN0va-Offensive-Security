# Hosting Information

## يعني إيه؟
تحليل provider وDNS وTLS headers لفهم أين تُستضاف خدمة عامة.

## ليه مهم؟
يساعد incident triage وvendor contact، لكنه لا يكشف backend الحقيقي دائمًا.

## بيشتغل إزاي؟
اجمع A/AAAA وASN وresponse headers من نطاق مصرح، ثم افصل observation عن inference.

## مثال بسيط
CDN IP لا يعني origin server IP.

## Cybersecurity
تحديد قناة abuse أو مراجعة third-party risk.

## Tools
RDAP، `dig`، `curl -I`، SecurityTrails وفق Terms.

## Common Mistakes
تجاوز CDN، scanning provider، أو اعتبار header ثابتًا.

## Exercises
اكتب ثلاثة possible explanations لـIP مشترك.

## Mini Challenge
حدد ما يحتاج تصريحًا قبل active verification.

## Summary
Hosting attribution احتمالي ومتغير.
