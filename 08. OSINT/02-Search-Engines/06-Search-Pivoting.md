# Search Pivoting

## يعني إيه؟
Pivot هو تحويل clue إلى identifier جديد: title، author، date، domain، أو phrase.

## ليه مهم؟
التحقيق لا يقف عند أول query؛ pivot يكشف connections ويقلل التخمين.

## بيشتغل إزاي؟
استخرج clue، صنفه، ابحث به منفردًا وبتركيب مختلف، ثم تحقق من identity والسياق.

## مثال بسيط
من PDF نأخذ `document-id NL-2026-04` ونبحث عنه في official domain فقط.

## Cybersecurity
يربط advisory بـCVE أو asset بدون scanning.

## Tools
Search engines، URL parser، evidence log.

## Common Mistakes
pivot من clue عام جدًا، circular sourcing، أو حذف query الفاشلة.

## Exercises
اعمل pivot chain من page title إلى author إلى تاريخ، مع stop condition.

## Mini Challenge
أين تتوقف؟ عندما لا يضيف pivot جديد evidence مستقلًا أو يقترب من بيانات حساسة.

## Summary
Pivot جيد قابل للتفسير والتراجع.
