# إضافة PowerShell Admin للقائمة اليمين

## الهدف
إضافة "Open PowerShell as Administrator" في قائمة Context Menu (الزر اليمين)

## عبر Registry

### الخطوة 1: إضافة المفتاح
```powershell
New-Item -Path "HKCR:\Directory\Background\shell\PowerShellAdmin" -Force
New-ItemProperty -Path "HKCR:\Directory\Background\shell\PowerShellAdmin" -Name "MUIVerb" -Value "PowerShell Admin Here" -Force
New-ItemProperty -Path "HKCR:\Directory\Background\shell\PowerShellAdmin" -Name "Icon" -Value "powershell.exe" -Force
New-Item -Path "HKCR:\Directory\Background\shell\PowerShellAdmin\command" -Force
New-ItemProperty -Path "HKCR:\Directory\Background\shell\PowerShellAdmin\command" -Name "(default)" -Value 'powershell.exe -NoExit -Command "Set-Location -Path \"%V\""' -Force
```

### الخطوة 2: فحص النتيجة
اضغط كليك يمين على أي مجلد وشوف "فتح PowerShell كمسؤول"

## ملاحظات
- يعمل على Windows 10/11
- يحتاج صلاحية Administrator