# Metadata Sanitization

## يعني إيه؟
إزالة metadata غير المطلوبة قبل مشاركة file.

## ليه مهم؟
تقلل تسريب author وpaths وGPS، لكن لا تحمي content نفسه.

## بيشتغل إزاي؟
اعمل copy، استخدم tool، افحص الناتج مرة أخرى، واحتفظ بالأصل في storage مصرح.

## مثال بسيط
`exiftool -all= input.jpg -o sanitized.jpg` ثم verify tags.

## Cybersecurity
DLP وsafe evidence sharing.

## Tools
ExifTool وsandbox.

## Common Mistakes
sanitization بلا verification، أو حذف metadata المطلوبة قانونيًا.

## Exercises
قارن hashes وfields قبل/بعد.

## Mini Challenge
اكتب tradeoff بين provenance وprivacy.

## Summary
Sanitize intentionally ثم verify.
