# Email Metadata

## يعني إيه؟
Headers تحتوي routing fields مثل `Date` و`Received` و`Message-ID`، وقد تكشف مسارًا تقنيًا.

## ليه مهم؟
تفيد في phishing analysis، لكن timestamps وIPs قد تكون proxies أو forged جزئيًا.

## بيشتغل إزاي؟
حلل رسالة تملكها أو sample lab، اقرأ من آخر Received إلى أقدم، واحفظ نسخة redacted.

## مثال بسيط
رسالة fictional تمر عبر mail gateway؛ نتحقق من SPF/DKIM/DMARC result.

## Cybersecurity
تساعد triage، لا تعطي تلقائيًا هوية المرسل الحقيقي.

## Tools
Mail client “show original”، header analyzer محلي، و`grep`.

## Common Mistakes
نشر full headers، الخلط بين sender وreturn-path، واعتبار IP origin مؤكدًا.

## Exercises
ضع labels للحقول الآتية: authentication، routing، content.

## Mini Challenge
اكتب limitation واحدة لكل header تعتمد عليه.

## Summary
Headers technical evidence تحتاج context وredaction.
