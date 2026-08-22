# Timeline Analysis

## يعني إيه؟
ترتيب events زمنيًا لاكتشاف sequence وتناقضات.

## ليه مهم؟
التاريخ قد يفسر domain change أو announcement، لكنه لا يثبت causality.

## بيشتغل إزاي؟
استخدم UTC، سجّل published/updated/captured، وافصل inferred order.

## مثال بسيط
Post 10:00 ثم status update 10:15؛ لا نستنتج سبب outage بلا مصدر.

## Cybersecurity
incident timeline وresponse review.

## Tools
Spreadsheet، timeline diagram، hashes.

## Common Mistakes
خلط timezone، ترتيب repost كأصلي، وتجاهل clock skew.

## Exercises
ابنِ timeline من خمس fictional events.

## Mini Challenge
حدد event confidence وسبب uncertainty.

## Summary
الـtimeline يحسن السياق، لا يصنع قصة من نفسه.
