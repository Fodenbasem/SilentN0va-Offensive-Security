# OSINT Cheatsheet

## Search Operators
- `site:example.org phrase` حصر النتائج في Domain.
- `"exact phrase"` بحث مطابق.
- `filetype:pdf` نوع ملف محدد.
- `intitle:report` داخل العنوان.
- `-term` استبعاد كلمة.
- استخدم operators على نطاق تملكه أو نطاق تدريب فقط.

## DNS Commands
```bash
 dig A example.org
 dig MX example.org
 dig NS example.org
 dig TXT example.org
 host example.org
```

## WHOIS/RDAP
```bash
whois example.org
curl -s https://rdap.org/domain/example.org
```
RDAP قد يعرض بيانات redacted؛ سجّل وقت الاستعلام ومصدره.

## Linux Commands
```bash
curl -I https://example.org
traceroute example.org
sha256sum evidence.bin
file image.jpg
```

## Useful Tools
- Search: Google، Bing، DuckDuckGo.
- Domain: RDAP، `dig`، Amass، Subfinder.
- Exposure context: Shodan، Censys، VirusTotal.
- Graphing: Maltego، SpiderFoot.
- Metadata: ExifTool.

## Metadata
```bash
exiftool -a -u -g1 image.jpg
exiftool -all= input.pdf -o sanitized.pdf
```
اشتغل على نسخة، وراجع إن sanitization أزال البيانات المطلوبة فعلًا.

## Workflow
`Objective -> Initial facts -> Search -> Pivot -> Correlate -> Validate -> Evidence -> Report`.

## Evidence Collection
سجّل URL، timestamp، query، screenshot أو hash، وسبب ارتباط الدليل بالفرضية. لا تجمع بيانات زيادة.

## Source Validation
قارن مصدرين مستقلين، راجع التاريخ والسياق، وافصل fact عن inference. Official source أقوى من repost مجهول، لكن لا يعني إنه كامل.

## Common Mistakes
Username واحد مش Identity proof، DNS الحالي مش تاريخ كامل، geolocation من صورة مش يقين، وTool output مش Evidence نهائي.
