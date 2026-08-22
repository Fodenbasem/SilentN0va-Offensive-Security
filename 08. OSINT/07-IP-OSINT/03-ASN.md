# ASN

## يعني إيه؟
ASN رقم لنظام مستقل يعلن routes عبر BGP.

## ليه مهم؟
يربط IP بـnetwork operator وقت معين.

## بيشتغل إزاي؟
اعمل lookup، راجع announced prefix وdate، ثم corroborate مع RDAP.

## مثال بسيط
IP في `192.0.2.0/24` documentation لا يمثل خدمة حقيقية.

## Cybersecurity
triage وprovider escalation.

## Tools
BGPView، Hurricane Electric، RDAP.

## Common Mistakes
اعتبار ASN company ownership مطلقًا، أو تجاهل cloud multi-tenancy.

## Exercises
حوّل ASN result إلى finding محدود.

## Mini Challenge
اكتب uncertainty statement.

## Summary
ASN يشرح route ownership لا behavior.
