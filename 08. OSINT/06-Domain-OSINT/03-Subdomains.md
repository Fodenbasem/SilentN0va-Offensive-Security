# Subdomains

## يعني إيه؟
Subdomain اسم تحت Domain مثل `docs.example.org`.

## ليه مهم؟
قد يوضح environments أو services عامة، لكنه لا يعني أن كل name حي.

## بيشتغل إزاي؟
ابدأ CT logs وofficial links وDNS؛ تحقق يدويًا، ولا تعمل scanning بلا تصريح.

## مثال بسيط
Certificate يذكر `docs.example.org`؛ نتحقق من DNS ثم الصفحة العامة.

## Cybersecurity
asset inventory وexposure review.

## Tools
crt.sh، Subfinder في owned scope، `dig`.

## Common Mistakes
wildcard DNS، duplicate names، واعتبار certificate دليلًا على live service.

## Exercises
اربط ثلاثة subdomains بمصادر مختلفة.

## Mini Challenge
سجّل “seen in CT” بدل “active” عند غياب DNS.

## Summary
Presence وliveness وownership ثلاث claims مختلفة.
