# Domain Investigation

## Objective
اعمل investigation دفاعية لنطاق تملكه أو `example.org`.

## Scenario
Nile Lantern Labs تريد inventory عام بدون scanning.

## Environment
RDAP، `dig`، CT، browser، evidence log.

## Information Given
Domain fictional ووقت بداية محدد.

## Tasks
اجمع registration context، DNS، CT names، ASN، وhistorical clue؛ تحقق من كل claim.

## Hints
ابدأ passive ثم صنّف current/old/unknown.

## Solution
أنشئ table للـrecords مع URL/command وtimestamp، وارفع confidence فقط مع مصدرين.

## Explanation
كل طبقة تجيب سؤالًا مختلفًا: registration، resolution، issuance، network، history.

## What We Learned
Domain pivots وحدود attribution.
