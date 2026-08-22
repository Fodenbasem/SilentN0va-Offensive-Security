# DNS Records

## يعني إيه؟
DNS يربط names بـrecords مثل A/AAAA وMX وNS وTXT وCNAME.

## ليه مهم؟
يكشف service architecture العامة وmail providers، مع ملاحظة أن records تتغير.

## بيشتغل إزاي؟
استخدم `dig TYPE domain`، سجّل TTL ووقت الاستعلام، وقارن أكثر من resolver عند الحاجة.

## مثال بسيط
`dig MX example.org` يوضح mail routing وليس محتوى البريد.

## Cybersecurity
يدعم inventory وDMARC review داخل نطاق مصرح.

## Tools
`dig`، `host`، DNSViz.

## Common Mistakes
خلط CNAME وA، تجاهل caching، واعتبار TXT secret.

## Exercises
اقرأ A وMX وNS وTXT من domain training.

## Mini Challenge
ما الفرق بين current DNS وhistorical DNS؟ الأول لقطة حالية فقط.

## Summary
DNS map متغير وليس ownership certificate.
