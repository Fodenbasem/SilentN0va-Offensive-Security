# OSINT Roadmap

امشِ بالترتيب، وكل Level لازم يطلع منه Evidence Log صغير وتفسير لحدود النتيجة.

## Level 1 — OSINT Fundamentals
- **What to learn:** Objective، Sources، Validation، OPSEC، Ethics.
- **What to practice:** فرّق بين fact وassumption وابنِ source log.
- **Prerequisites:** أساسيات Web.
- **Mini Challenge:** قيّم ثلاث نتائج عن شركة fictional وحدد مصدرين مستقلين.
- **Recommended next step:** [Search Engines](./02-Search-Engines/README.md).

## Level 2 — Search
- **What to learn:** Operators، exact phrases، filetype، pivoting.
- **What to practice:** ابحث في نطاق تدريب بدون جمع بيانات حساسة.
- **Prerequisites:** Level 1.
- **Mini Challenge:** استخرج معلومة من ثلاث صفحات عامة مع توثيق URL والتاريخ.
- **Recommended next step:** [People OSINT](./03-People-OSINT/README.md).

## Level 3 — People & Username OSINT
- **What to learn:** aliases، correlation، false positives.
- **What to practice:** شخصية fictional بثلاثة aliases.
- **Prerequisites:** Search.
- **Mini Challenge:** ارفض تطابقًا مبنيًا على username فقط.
- **Recommended next step:** [Email OSINT](./05-Email-OSINT/README.md).

## Level 4 — Email OSINT
- **What to learn:** patterns، domains، metadata، breach awareness.
- **What to practice:** بيانات تجريبية غير حقيقية.
- **Prerequisites:** Identity correlation.
- **Mini Challenge:** استنتج format محتمل بدون إرسال رسائل أو تجربة كلمات مرور.
- **Recommended next step:** [Domain OSINT](./06-Domain-OSINT/README.md).

## Level 5 — Domain & IP OSINT
- **What to learn:** WHOIS/RDAP، DNS، CT، ASN، reputation.
- **What to practice:** نطاق مملوك لك أو documentation domain.
- **Prerequisites:** DNS basics.
- **Mini Challenge:** اربط subdomain بـcertificate ثم تحقق من DNS.
- **Recommended next step:** [Social Media](./08-Social-Media-OSINT/README.md).

## Level 6 — Social Media & Image OSINT
- **What to learn:** timelines، visual clues، geolocation، public exposure.
- **What to practice:** صور ومشاركات تدريبية.
- **Prerequisites:** Validation.
- **Mini Challenge:** حدد ما يمكن إثباته وما لا يمكن إثباته من صورة.
- **Recommended next step:** [Tools](./12-OSINT-Tools/README.md).

## Level 7 — OSINT Tools
- **What to learn:** اختيار الأداة، scope، rate limits، output validation.
- **What to practice:** قارن نتيجتين يدويًا.
- **Prerequisites:** Domain/IP.
- **Mini Challenge:** اعثر على false positive في output آلي.
- **Recommended next step:** [Practical Labs](./13-Practical-Labs/README.md).

## Level 8 — Practical Investigations
- **What to learn:** end-to-end workflow وEvidence.
- **What to practice:** Labs fictional.
- **Prerequisites:** Levels 1-7.
- **Mini Challenge:** اكتب تقرير صفحة واحدة.
- **Recommended next step:** [CTF OSINT](./14-CTF-OSINT/README.md).

## Level 9 — CTF OSINT
- **What to learn:** clue chaining وpivoting under time.
- **What to practice:** Search، DNS، image وmulti-source challenges.
- **Prerequisites:** Practical Labs.
- **Mini Challenge:** حل challenge بدون الاعتماد على نتيجة واحدة.
- **Recommended next step:** [Reporting](./15-Reporting/README.md).

## Level 10 — Reporting
- **What to learn:** source reliability، confidence، timeline.
- **What to practice:** report قابل لإعادة الإنتاج.
- **Prerequisites:** كل المستويات السابقة.
- **Mini Challenge:** حوّل notes غير مرتبة إلى findings موثقة.
- **Recommended next step:** كرر Labs بفرضيات أصعب.
