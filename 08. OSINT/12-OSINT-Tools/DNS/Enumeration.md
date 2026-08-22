# DNS Enumeration

استخدم `dig A/AAAA/MX/NS/TXT/CNAME domain` على نطاق مصرح. ابدأ records معروفة، ثم CT أو official docs للـsubdomains، ولا تستخدم brute-force أو scanning خارج scope. سجّل TTL وresolver والتاريخ. TXT قد يحتوي policy مثل SPF/DMARC، وليس مكانًا للبحث عن secrets. تمرين: ابنِ table للـrecords في `example.org` مع observation وlimitation.
