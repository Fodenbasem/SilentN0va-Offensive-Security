# ExifTool

## What is it?
ExifTool أداة command-line لقراءة وكتابة metadata لملفات كثيرة.

## Installation
نزّل من [official site](https://exiftool.org/) أو package manager، وتحقق من checksum إن توفر.

## Basic Usage
```bash
exiftool file.jpg
exiftool -a -u -g1 file.jpg
exiftool -j file.jpg > report.json
```

## Important Options
`-a` duplicate tags، `-u` unknown، `-g1` groups، `-j` JSON. استخدم read-only أولًا.

## Practical Example
حلل sample image في lab، احفظ JSON، ثم قارنه بالسياق.

## Cybersecurity Use Case
privacy audit وforensic triage على artifacts مصرح بها.

## Limitations
Metadata يمكن تعديلها أو إزالتها ولا تثبت truth.

## Common Mistakes
تشغيل write commands على الأصل وتسريب GPS.

## Lab
استخدم صورة Wikimedia، hash الأصل، استخرج tags، واكتب field لا يمكن إثباته.
