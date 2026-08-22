# Username Correlation

## يعني إيه؟
اختبار هل appearances المختلفة تخص نفس account owner أو brand.

## ليه مهم؟
يقلل false positives قبل أي finding.

## بيشتغل إزاي؟
ابنِ matrix من links، timestamps، topics، timezone، وcontradictions، مع مصدر مستقل.

## مثال بسيط
username + نفس project URL + نفس public bio أقوى من username فقط.

## Cybersecurity
تحليل brand abuse وCTF attribution المحدود.

## Tools
Spreadsheet، graph notes.

## Common Mistakes
scoring سري، circular source، وتجاهل aliases.

## Exercises
احسب confidence qualitatively: low/medium/high مع rationale.

## Mini Challenge
اكتب finding لا يكشف هوية: “قد تكون الحسابات مرتبطة بالمشروع”.

## Summary
استخدم لغة احتمالية ودليلًا قابلًا للمراجعة.
