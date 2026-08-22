# Data Collection

## يعني إيه؟
جمع البيانات هو التقاط أقل معلومات لازمة للإجابة عن Objective بطريقة قابلة لإعادة الإنتاج.

## ليه مهم؟
الـnotes المرتبة تمنع إعادة العمل وتكشف أين دخل الافتراض.

## بيشتغل إزاي؟
أنشئ Evidence ID، URL، timestamp UTC، query، observation، وhash للملف إن وجد. لا تنسخ بيانات شخصية بلا ضرورة.

## مثال بسيط
`E-01` يسجل TXT record مع command ووقت التنفيذ، بدل صورة بلا سياق.

## Cybersecurity
Analyst يحافظ على chain of custody مبسطة، ويفصل raw evidence عن analyst notes.

## Tools
Markdown، CSV، `tee`، `sha256sum`، screenshot مع timestamp.

## Common Mistakes
عدم تسجيل timezone، تعديل الأصل، أو حفظ secrets داخل repository.

## Exercises
اكتب ثلاثة Evidence records عن `example.org` باستخدام بيانات عامة فقط.

## Mini Challenge
صمم naming convention لا يكشف أسماء أشخاص حقيقيين.

## Summary
اجمع قليلًا، وثّق جيدًا، واحفظ الأصل منفصلًا.
