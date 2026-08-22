# Search Engine CTF

## Objective
تدرب على finding clue داخل content fictional بدون dorks حساسة.

## Scenario
شركة fictional نشرت ثلاثة announcements في `example.org`: واحد يذكر project codename، وآخر يذكر الشهر.

## Tasks
1. استخدم exact phrase آمنة. 2. اربط codename بالشهر. 3. وثّق مصدرين. 4. اكتب confidence.

## Hints
ابدأ بـsite ثم phrase؛ لا تبحث عن credentials أو admin.

## Solution
ابحث عن اسم الشركة ثم phrase من العنوان، استخرج codename، وأعد query داخل نفس domain.

## Explanation
القيمة في pivot من clue إلى clue، وليس في أول hit.

## Common Mistakes
اعتبار repost مصدرًا ثانيًا، أو تجاهل date.

## What We Learned
Search operators، pivoting، وsource validation.

## Safety
استبدل `example.org` بـCTF target معلن فقط.
