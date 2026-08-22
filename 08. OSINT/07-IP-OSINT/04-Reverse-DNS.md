# Reverse DNS

## يعني إيه؟
PTR record يربط IP باسم، إن وُجد.

## ليه مهم؟
قد يقدم naming clue، لكنه اختياري ويمكن تغييره.

## بيشتغل إزاي؟
`dig -x IP`، ثم تحقق من forward DNS ووقت النتيجة.

## مثال بسيط
PTR `mail.example.org` لا يثبت أن IP مخصص حصريًا للشركة.

## Cybersecurity
mail triage وlog enrichment.

## Tools
`dig -x`، `host`، RDAP.

## Common Mistakes
الثقة في hostname وحده، تجاهل mismatch، أو probing.

## Exercises
قارن forward وreverse result.

## Mini Challenge
فسّر mismatch بثلاثة احتمالات غير اتهامية.

## Summary
PTR clue يحتاج corroboration.
