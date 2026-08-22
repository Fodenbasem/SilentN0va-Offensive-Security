# EXIF Metadata

## يعني إيه؟
EXIF حقول صور مثل camera، lens، orientation، GPS، وDateTimeOriginal.

## ليه مهم؟
قد يشرح provenance أو يكشف privacy exposure.

## بيشتغل إزاي؟
`exiftool -a -u -g1 image.jpg` ثم redaction للـGPS في التقرير.

## مثال بسيط
GPS absent لا يعني أن الصورة بلا location clues.

## Cybersecurity
privacy audit وattachment triage.

## Tools
ExifTool وhash utility.

## Common Mistakes
تفسير software date كوقت التصوير، أو نشر coordinates.

## Exercises
قارن original وsanitized copy.

## Mini Challenge
حدد ما الذي يمكن تغييره بسهولة.

## Summary
EXIF مفيد لكنه fragile وحساس.
