# ASN and IP Ranges

## يعني إيه؟
ASN يعرّف Autonomous System يدير prefixes على Internet.

## ليه مهم؟
يساعد فهم provider وnetwork ownership، لا يحدد جهازًا أو شخصًا بمفرده.

## بيشتغل إزاي؟
اربط IP بـRDAP/BGP data، راجع prefix وorigin ASN، وسجّل وقت اللقطة.

## مثال بسيط
A record يشير إلى cloud range؛ هذا لا يثبت أن الشركة تدير كل الـrange.

## Cybersecurity
asset attribution وallowlist review.

## Tools
BGPView، RDAP، Team Cymru services.

## Common Mistakes
الخلط بين hosting provider وowner، واعتبار geolocation دقيقة.

## Exercises
قارن IPs fictional واكتب provider/uncertainty.

## Mini Challenge
ما claim الآمن؟ “الـIP معلن تحت ASN X وقت الفحص”.

## Summary
ASN context شبكي، لا هوية بشرية.
