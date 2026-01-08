# حذف متصفح Edge

## الوصف
إزالة متصفح Edge بشكل نهائي من الويندوز.

## الطريقة 1: Settings (محاولة)

```
1. اضغط Win + I
2. روح: Apps > Apps and features
3. ابحث عن "Microsoft Edge"
4. قد لا يكون قابل للحذف!
```

## الطريقة 2: PowerShell Script

```powershell
# PowerShell (Run as Admin)
# إغلق Edge
Stop-Process -Name msedge -Force -ErrorAction SilentlyContinue

# الانتظار
Start-Sleep -Seconds 3

# حذف مجلد Edge
Remove-Item "C:\Program Files\Microsoft\Edge\*" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item "C:\Program Files (x86)\Microsoft\Edge\*" -Recurse -Force -ErrorAction SilentlyContinue

# حذف من Registry
Reg delete "HKCU\Software\Microsoft\Edge" /f /s /va
Reg delete "HKLM\Software\Microsoft\Edge" /f /s /va
```

## الطريقة 3: استخدام Script من GitHub

```powershell
# تحميل وتشغيل script متقدم
iwr -useb https://raw.githubusercontent.com/W4RH4WK/Debloat-Windows-10/master/scripts/remove-ms-edge.ps1 | iex
```

## استعادة Edge

```powershell
# إذا غيرت رأيك
Powershell -Command "& { $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri 'https://aka.ms/edge-installer-download' -OutFile 'edge-installer.exe'; .\edge-installer.exe }"
```

## تحذير
⚠️ Edge مدمج في النظام! قد لا يكون حذفه كاملاً ممكناً.
- بعض الوظائف قد تعتمد عليه
- Windows قد يحاول إعادة تثبيته
