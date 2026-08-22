# يعني إيه OSINT؟

## يعني إيه؟
**OSINT** هو جمع وتحليل معلومات متاحة قانونيًا من Public Sources عشان نجاوب سؤال محدد. مش معناه تصفح عشوائي ولا جمع كل حاجة عن شخص.

## ليه مهم؟
بيساعد Security Team تفهم Attack Surface، تتحقق من خبر، أو تلاقي Context لبلاغ. القيمة في التحليل والربط، مش في كثرة الروابط.

## بيشتغل إزاي؟
بصياغة Objective، جمع Initial Facts، Search، Pivot، Correlate، Validate، ثم توثيق الدليل. فرّق بين observation وinference.

## مثال بسيط
شركة fictional اسمها Nile Lantern Labs نشرت PDF فيه تاريخ إصدار واسم فريق. نسجل URL والتاريخ، ونقارن صفحة الشركة نفسها قبل استنتاج أي علاقة.

## استخدامه في Cybersecurity
يُستخدم في defensive exposure review وThreat Intelligence ضمن Scope مكتوب. لا تستخدمه لاستهداف أفراد حقيقيين.

## Tools
متصفح، notes، `curl -I`، `sha256sum`، وSpreadsheet للـEvidence Log.

## Common Mistakes
اعتبار snippet دليلًا، الخلط بين Public وAuthorized، وعدم تسجيل وقت الوصول.

## Exercises
اكتب Objective عن `example.org` في جملة قابلة للقياس، ثم حدد مصدرين مناسبين.

## Mini Challenge
عندك claim من blog وclaim من Official page. أيهما تبدأ به؟ اشرح سببك وحدودك.

## Summary
OSINT منهج أسئلة وأدلة، وليس Tool أو مراقبة أشخاص.

## References
[OWASP](https://owasp.org/)، [NIST](https://www.nist.gov/).
