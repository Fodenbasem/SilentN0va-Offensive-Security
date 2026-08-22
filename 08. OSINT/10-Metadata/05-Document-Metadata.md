# Document Metadata Investigation

## يعني إيه؟
تحليل metadata عبر document types مع provenance وhash.

## ليه مهم؟
يقارن نسخًا ويكشف تغيرات workflow.

## بيشتغل إزاي؟
استخرج fields، اربطها بالنسخة والتاريخ، ثم تحقق من content نفسه.

## مثال بسيط
نسختان لهما Producer مختلف؛ قد يكون السبب export pipeline، وليس مؤلفًا جديدًا.

## Cybersecurity
incident artifacts وpublic exposure review.

## Tools
ExifTool، `file`، hash.

## Common Mistakes
اعتبار field attribution، وتجاهل file conversion.

## Exercises
اعمل comparison table.

## Mini Challenge
اكتب ثلاث explanations بديلة.

## Summary
التحليل الجيد يناقش البدائل.
