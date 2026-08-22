# WHOIS وRDAP للـIP

## يعني إيه؟
RDAP API حديث ومنظم يعرض registration data وcontacts redacted حسب policy.

## ليه مهم؟
يساعد معرفة RIR وnetwork allocation بطريقة machine-readable.

## بيشتغل إزاي؟
استعلم عن IP، اقرأ `entities` و`startAddress` و`remarks`، وسجّل timestamp.

## مثال بسيط
`curl -s https://rdap.org/ip/192.0.2.1` يستخدم documentation range.

## Cybersecurity
تحديد abuse contact وprovider، لا تحديد مستخدم نهائي.

## Tools
[RDAP bootstrap](https://data.iana.org/rdap/)، curl.

## Common Mistakes
خلط registrant مع end user، وتجاهل redaction.

## Exercises
اقرأ JSON وحدد fields المهمة.

## Mini Challenge
قارن WHOIS text وRDAP structured output.

## Summary
RDAP structured context وليس identity proof.
