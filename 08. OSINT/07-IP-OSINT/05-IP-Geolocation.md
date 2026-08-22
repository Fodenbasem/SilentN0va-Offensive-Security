# IP Geolocation

## يعني إيه؟
Geolocation databases تقدّر region/provider من IP، ولا تعطي عنوانًا دقيقًا عادة.

## ليه مهم؟
مفيد في anomaly context، لكنه ضعيف لإسناد شخص.

## بيشتغل إزاي؟
قارن database results، سجّل accuracy، ولا تستخدمه وحده لاتخاذ قرار.

## مثال بسيط
Cloud IP يظهر في بلد مختلف عن المستخدم بسبب routing.

## Cybersecurity
تجميع alerts لا enforcement منفرد.

## Tools
MaxMind demo، IPinfo، RDAP.

## Common Mistakes
خلط geolocation بـGPS، تجاهل VPN/NAT، واللغة القطعية.

## Exercises
سجل اختلاف مصدرين وحدود كل واحد.

## Mini Challenge
اكتب finding: “consistent with region” بدل “located at”.

## Summary
Geo estimate قرينة منخفضة إلى متوسطة.
