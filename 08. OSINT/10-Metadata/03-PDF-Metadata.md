# PDF Metadata

## يعني إيه؟
PDF قد يحتوي Title، Author، Creator، Producer، dates، وembedded files.

## ليه مهم؟
يفيد document provenance وsecurity review.

## بيشتغل إزاي؟
افحص نسخة بـExifTool، راجع XMP وattachments، واحفظ hash.

## مثال بسيط
Producer يوضح software pipeline، لا identity مؤكدة.

## Cybersecurity
كشف internal naming أو outdated generator داخل public docs.

## Tools
ExifTool، `pdfinfo`.

## Common Mistakes
فتح embedded file مجهول على host شخصي، أو نشر metadata.

## Exercises
حلل PDF lab واربط field بسؤال مناسب.

## Mini Challenge
اكتب finding limited إلى “document reports”.

## Summary
PDF metadata technical context.
