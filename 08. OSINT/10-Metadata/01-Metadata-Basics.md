# Metadata Basics

## يعني إيه؟
Metadata هي data عن file أو record: creator، timestamps، software، dimensions، وidentifiers.

## ليه مهم؟
تفيد provenance وprivacy review، لكن قد تكون ناقصة أو قابلة للتعديل.

## بيشتغل إزاي؟
حلل نسخة، احفظ hash للأصل، افصل extracted fields عن conclusions.

## مثال بسيط
PDF يحمل Producer وCreationDate؛ هذا لا يثبت من كتب المحتوى فعليًا.

## Cybersecurity
تحليل artifacts وتسريب معلومات المؤسسة.

## Tools
ExifTool، `file`، PDF readers.

## Common Mistakes
تسريب GPS، الثقة في dates، وتعديل الأصل.

## Exercises
صنف fields إلى identifying/technical/benign.

## Mini Challenge
اكتب limitation لكل field.

## Summary
Metadata قرينة، وليست قصة كاملة.
