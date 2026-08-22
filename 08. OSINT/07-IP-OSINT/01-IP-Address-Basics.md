# IP Address Basics

## يعني إيه؟
IP عنوان منطقي IPv4 أو IPv6، وقد يكون public/private أو shared.

## ليه مهم؟
يحدد routing context، لا يساوي شخصًا أو جهازًا دائمًا.

## بيشتغل إزاي؟
صنّف address، اعرف scope وtime، ثم اربطه بـDNS/RDAP.

## مثال بسيط
`127.0.0.1` localhost؛ لا يمكن استخدامه لإسناد نشاط خارجي.

## Cybersecurity
تحليل logs وIOC context داخل authorized environment.

## Tools
`ipconfig`، `ip addr`، RDAP.

## Common Mistakes
كشف private IP، تجاهل NAT، واعتبار address ثابتًا.

## Exercises
صنّف addresses fictional إلى private/public/loopback.

## Mini Challenge
اشرح لماذا shared CDN IP لا يحدد customer.

## Summary
افهم network context قبل attribution.
