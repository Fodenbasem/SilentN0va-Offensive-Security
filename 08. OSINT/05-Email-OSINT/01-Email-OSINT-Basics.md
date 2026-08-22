# Email OSINT Basics

## يعني إيه؟
تحليل email address من ناحية format وdomain وpublic context، بدون الوصول لصندوق البريد.

## ليه مهم؟
يفيد في فهم organization naming وphishing exposure.

## بيشتغل إزاي؟
افصل local-part عن domain، تحقق من domain عبر RDAP/DNS، ولا تستنتج owner من string.

## مثال بسيط
`analyst@example.org` يثبت domain syntax، لا يثبت أن mailbox موجود.

## Cybersecurity
يستخدم في defensive awareness وauthorized inventory.

## Tools
RDAP، DNS، search، email header parser لرسالة تملكها.

## Common Mistakes
إرسال test mail، password reset probing، وتخزين addresses حقيقية.

## Exercises
حلل `person@example.org` دون أي interaction.

## Mini Challenge
اكتب ثلاث limitations لنتيجة domain-based.

## Summary
Email clue حساس؛ تعامل معه بأقل بيانات.
