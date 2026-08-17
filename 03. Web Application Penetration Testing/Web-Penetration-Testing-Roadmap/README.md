# Web Application Penetration Testing Labs & Roadmap

This document contains a structured list of web application security labs, challenges, and the capstone project organized by vulnerability type.

---

## Access Control Labs

- [Unprotected Admin Functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)
- [Unprotected Admin Functionality with Unpredictable URL](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url)
- [User Role Controlled by Request Parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter)
- [User Role Can Be Modified in User Profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)
- [User ID Controlled by Request Parameter](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter)
- [User ID Controlled by Request Parameter with Unpredictable User IDs](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids)
- [User ID Controlled by Request Parameter with Data Leakage in Redirect](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect)
- [User ID Controlled by Request Parameter with Password Disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)
- [Insecure Direct Object References (IDOR)](https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references)

---

## Authentication Labs

- [Username Enumeration via Different Responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)
- [2FA Simple Bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)
- [Password Reset Broken Logic](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic)
- [Username Enumeration via Subtly Different Responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses)
- [Username Enumeration via Response Timing](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing)
- [Broken Brute-Force Protection, IP Block](https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block)
- [Username Enumeration via Account Lock](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-account-lock)
- [2FA Broken Logic](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-broken-logic)
- [Offline Password Cracking](https://portswigger.net/web-security/authentication/other-mechanisms/lab-offline-password-cracking)
- [Password Brute-Force via Password Change](https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-brute-force-via-password-change)

---

## OS Command Injection Labs

- [Simple Case](https://portswigger.net/web-security/os-command-injection/lab-simple)
- [Blind OS Command Injection with Output Redirection](https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection)
- [Blind OS Command Injection with Out-of-Band Interaction](https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band)
- [Blind OS Command Injection with Time Delays](https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays)

---

## Information Disclosure Labs

- [Information Disclosure in Error Messages](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-error-messages)
- [Information Disclosure on Debug Page](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page)
- [Source Code Disclosure via Backup Files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)
- [Authentication Bypass via Information Disclosure](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass)
- [Information Disclosure in Version Control History](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)

---

## File Upload Labs

### PortSwigger
- [Remote Code Execution via Web Shell Upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload)
- [Web Shell Upload via Content-Type Restriction Bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass)
- [Web Shell Upload via Path Traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal)
- [Web Shell Upload via Extension Blacklist Bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass)
- [Web Shell Upload via Obfuscated File Extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension)
- [Remote Code Execution via Polyglot Web Shell Upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-polyglot-web-shell-upload)
- [Web Shell Upload via Race Condition](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-race-condition)

### Root-Me
- [File Upload - Double Extensions](https://www.root-me.org/en/Challenges/Web-Server/File-upload-Double-extensions)
- [File Upload - MIME Type](https://www.root-me.org/en/Challenges/Web-Server/File-upload-MIME-type)
- [File Upload - Null Byte](https://www.root-me.org/en/Challenges/Web-Server/File-upload-Null-byte)

---

## Cross-Site Scripting (XSS) Labs

### PortSwigger
- [Reflected XSS into Attribute with Angle Brackets HTML-Encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-attribute-angle-brackets-html-encoded)
- [Stored XSS into Anchor href Attribute with Double Quotes HTML-Encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded)
- [Reflected XSS into JavaScript String with Angle Brackets HTML-Encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded)
- [Reflected XSS into HTML Context with Most Tags and Attributes Blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)
- [Reflected XSS into HTML Context with All Standard Tags Blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)
- [Reflected XSS with Some SVG Markup Allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)
- [Reflected XSS in Canonical Link Tag](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-canonical-link-tag)
- [Reflected XSS into JavaScript String with Single Quote and Backslash Escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-single-quote-backslash-escaped)
- [Reflected XSS in onclick Event](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)
- [Reflected XSS into Template Literal](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped)
- [Exploiting XSS to Steal Cookies](https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-stealing-cookies)
- [CSTI - Angular Sandbox Escape and CSP](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp)
- [Reflected XSS with Event Handlers and href Attributes Blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-event-handlers-and-href-attributes-blocked)
- [Reflected XSS in JavaScript URL with Some Characters Blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-url-some-characters-blocked)
- [Very Strict CSP with Dangling Markup Attack](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-very-strict-csp-with-dangling-markup-attack)
- [CSP Bypass](https://portswigger.net/web-security/cross-site-scripting/content-security-policy/lab-csp-bypass)

### TryHackMe
- [Advanced XSS Room](https://tryhackme.com/room/axss)
- [XSS Room](https://tryhackme.com/room/xss)

### Root-Me
- [XSS - Stored 1](https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-1)
- [XSS - Reflected](https://www.root-me.org/en/Challenges/Web-Client/XSS-Reflected)
- [XSS - Stored 2](https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-2)
- [XSS - Stored Filter Bypass](https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-filter-bypass)

---

## SQL Injection (SQLi) Labs

### PortSwigger
- [SQLi Union Attack - Determining Number of Columns](https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns)
- [SQLi Union Attack - Finding Column Containing Text](https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text)
- [SQLi Union Attack - Retrieving Data from Other Tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables)

### Root-Me
- [SQL Injection Authentication Bypass](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-authentication)
- [SQL Injection String](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-String)

### TryHackMe
- [SQL Injection LM Room](https://tryhackme.com/room/sqlinjectionlm)

---

## Business Logic Flaws Labs

- [Excessive Trust in Client-Side Controls](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-low-level)
- [Inconsistent Handling of Exceptional Input](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-handling-of-exceptional-input)
- [Weak Isolation on Dual-Use Endpoint](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-weak-isolation-on-dual-use-endpoint)
- [Insufficient Workflow Validation](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-insufficient-workflow-validation)
- [Authentication Bypass via Flawed State Machine](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-flawed-state-machine)
- [Authentication Bypass via Encryption Oracle](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-authentication-bypass-via-encryption-oracle)
- [Bypassing Access Controls using Email Parsing Discrepancies](https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-bypassing-access-controls-using-email-address-parsing-discrepancies)

---

## Penetration Testing Project: OWASP Juice Shop

- **Target:** OWASP Juice Shop (`https://juice-shop.herokuapp.com/`)
- **Objective:** Perform a structured penetration testing assessment covering Authentication, Authorization, Injections, XSS, Business Logic, and APIs.
- **Rules of Engagement:** Test provided target only, no third-party attacks, no permanent disruption, use Burp Suite, validate findings before reporting.
- **Deliverable Requirements:** Final penetration testing report in PDF format (`Name_Surname.pdf`).
- **Report Contents:**
  1. Cover Page (Full Name, Task Name, Target, Date)
  2. Executive Summary
  3. Scope & Methodology
  4. Tools Used
  5. Findings Summary
  6. Detailed Findings (CVSS v3 Score/Vector, Title, Severity, Affected Component, Description, Steps to Reproduce, Technical Evidence, Impact, Remediation, References)
  7. Remediation Recommendations & Conclusion