# Passive Recon vs Active Recon

## يعني إيه؟
**Passive Recon** يعتمد على مصادر موجودة دون تفاعل مباشر مؤثر. **Active Recon** يرسل requests أو probes إلى Target.

## ليه مهم؟
Active activity قد تُسجل أو تؤثر على الخدمة، لذلك authorization وrate limits أساسيين.

## بيشتغل إزاي؟
ابدأ بـPassive: search، RDAP، CT، public docs. لو احتجت Active، وثّق scope، الوقت، User-Agent، والحدود، واستخدم lab.

## مثال بسيط
قراءة سجل DNS منشور Passive؛ تشغيل `dig` قد يكون query مباشر لكنه منخفض التأثير، أما scanning فـActive واضح.

## Cybersecurity
المحلل يقلل الضوضاء والمخاطر. الـPentester يتأكد أن كل probe داخل Rules of Engagement.

## Tools
Search engines، RDAP، CT logs، و`dig` في بيئة مصرح بها.

## Common Mistakes
الاعتماد على كلمة Passive لتبرير أي تصرف، أو تجاهل caching ووقت البيانات.

## Exercises
صمم مرحلتين لتحقيق fictional: passive أولًا، ونقطة قرار تتطلب موافقة قبل active.

## Mini Challenge
ما الدليل الذي لا يكفي وحده لإثبات أن subdomain حي؟ اذكر سببين.

## Summary
Passive يقلل التفاعل؛ Active يحتاج تصريحًا وتشغيلًا محسوبًا.
