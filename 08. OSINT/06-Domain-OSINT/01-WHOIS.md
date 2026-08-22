# WHOIS

## يعني إيه؟
WHOIS يعرض registration information المتاحة عن Domain، مثل Registrar وdates وnameservers. بيانات كثيرة قد تكون redacted.

## ليه مهم؟
يساعد فهم lifecycle وownership context، لكنه لا يثبت الشخص المالك.

## بيشتغل إزاي؟
استخدم RDAP أو WHOIS، سجّل وقت الاستعلام، وقارن Registrar وexpiration مع مصدر رسمي.

## مثال بسيط
`whois example.org` في lab؛ لا تفسر privacy-protected record كإخفاء متعمد.

## Cybersecurity
يدعم domain triage وbrand abuse review.

## Tools
WHOIS client و[RDAP](https://rdap.org/).

## Common Mistakes
الاعتماد على email redacted، تجاهل timezone، أو استخدام data قديمة.

## Exercises
استخرج خمسة fields ودوّن معنى كل واحد.

## Mini Challenge
ما الذي لا يثبته WHOIS؟ identity وcurrent hosting غالبًا.

## Summary
WHOIS context تاريخي/تسجيلي، وليس proof.
