# WHOIS وRDAP

## What is it?
Registration lookup لـDomain أو IP.

## Installation
WHOIS client اختياري؛ RDAP يعمل عبر browser أو curl.

## Basic Usage
`whois example.org` أو `curl -s https://rdap.org/domain/example.org`.

## Important Options
احفظ JSON وtimestamp، ولا تعتمد على redacted contact.

## Practical Example
حلل `example.org` وسجل registrar وnameservers.

## Cybersecurity Use Case
domain triage وabuse contact.

## Limitations
privacy، stale data، وproxy registration.

## Common Mistakes
identity attribution.

## Lab
استخدم [Domain Lab](../../13-Practical-Labs/01-Domain-Investigation.md).
