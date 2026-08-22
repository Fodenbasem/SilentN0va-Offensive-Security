# False Positives

## يعني إيه؟
False Positive نتيجة تبدو مطابقة لكنها تخص كيانًا آخر أو سياقًا مختلفًا.

## ليه مهم؟
الهوية الخاطئة ممكن تضر شخصًا وتنتج قرارًا أمنيًا سيئًا.

## بيشتغل إزاي؟
استخدم أكثر من identifier: username، timezone، domain، writing style، وtime correlation؛ ولا تعتبر أي واحد كافيًا وحده.

## مثال بسيط
username `nile_dev` موجود في حسابين. اختلاف اللغة والتاريخ يمنع الربط.

## Cybersecurity
في Threat Intel لا تربط IOC بجهة من string similarity فقط؛ راجع context وindependent sources.

## Tools
Spreadsheet للـconfidence matrix، browser، وmanual review.

## Common Mistakes
confirmation bias، تجاهل evidence المخالف، ورفع confidence مع تكرار نفس المصدر.

## Exercises
اعمل جدول supporting وcontradicting evidence لشخصية fictional.

## Mini Challenge
ضع قاعدة: لا ترفع correlation إلى “likely” إلا بعد قرينتين مستقلتين.

## Summary
الشك المنهجي حماية للمحقق وللناس.
