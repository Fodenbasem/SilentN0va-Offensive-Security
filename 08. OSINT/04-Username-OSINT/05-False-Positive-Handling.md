# False Positive Handling

## يعني إيه؟
إدارة النتائج الخاطئة بدل حذفها بصمت أو نشرها كحقيقة.

## ليه مهم؟
كل match غير مؤكد قد يوجه investigation غلط.

## بيشتغل إزاي؟
احتفظ بالحالة، سجّل سبب الرفض، وابحث عن disconfirming evidence.

## مثال بسيط
نفس username لكن account dates متداخلة مع استحالة location؛ نضعه unrelated.

## Cybersecurity
يرفع جودة IOC triage ويقلل alert fatigue.

## Tools
Case notes وconfidence fields.

## Common Mistakes
حذف negative evidence، أو تغيير label بلا سبب.

## Exercises
أنشئ rejection log لثلاث نتائج.

## Mini Challenge
اكتب سببًا قابلًا للتدقيق لا يعتمد على شعور.

## Summary
النتيجة المرفوضة تعلمك بقدر المقبولة.
