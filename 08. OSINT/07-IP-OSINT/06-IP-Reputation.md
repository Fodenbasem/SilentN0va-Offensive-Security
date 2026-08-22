# IP Reputation

## يعني إيه؟
Reputation feeds تجمع reports عن abuse أو malware أو spam.

## ليه مهم؟
تساعد prioritization، لكن false positives وshared infrastructure شائعة.

## بيشتغل إزاي؟
قارن أكثر من feed، راجع evidence والتاريخ، وافصل “reported” عن “malicious”.

## مثال بسيط
IP shared عليه report قديم؛ لا تحظر بلا context.

## Cybersecurity
SOC triage وincident response.

## Tools
VirusTotal، AbuseIPDB وفق policy، internal telemetry.

## Common Mistakes
قرار آلي من feed واحد، تجاهل expiration، ونشر raw reports.

## Exercises
اعمل confidence matrix لثلاثة reports.

## Mini Challenge
ما الذي يرفع الثقة؟ reports مستقلة حديثة مع behavior داخلي.

## Summary
Reputation signal يحتاج correlation.
