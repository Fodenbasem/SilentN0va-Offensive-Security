# Shodan Usage

حدد scope، ابحث بـhostname مملوك، ثم تحقق من timestamp وsource. لا تعمل exploit أو port probe من نتيجة. قارن banner مع `curl -I` المصرح، وأخفِ IPs في التقرير عند عدم الحاجة. تمرين: فسّر لماذا banner قديم أو cloud-shared. Limitation أساسية: Shodan يرى service وقت crawl وليس الحالة الحالية.
