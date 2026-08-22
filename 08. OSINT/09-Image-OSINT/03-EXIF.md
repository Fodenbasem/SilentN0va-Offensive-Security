# EXIF

## يعني إيه؟
EXIF metadata قد تحمل camera model وtimestamps وGPS.

## ليه مهم؟
قد تدعم provenance، لكنها قابلة للمسح أو التغيير.

## بيشتغل إزاي؟
استخدم `exiftool image.jpg` على نسخة، قارن metadata بسياق الصورة، ولا تنشر GPS.

## مثال بسيط
صورة lab فيها date قديم؛ لا يثبت وقت الالتقاط دون corroboration.

## Cybersecurity
تحليل attachments وprivacy sanitization.

## Tools
ExifTool و`file`.

## Common Mistakes
الثقة في timestamp، نسيان timezone، وتسريب coordinates.

## Exercises
صنف fields إلى safe/sensitive.

## Mini Challenge
اكتب finding “metadata states” بدل “photo taken at”.

## Summary
EXIF clue قابل للتغيير وحساس.
