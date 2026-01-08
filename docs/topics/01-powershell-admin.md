# إضافة PowerShell Admin في قائمة الماوس

## الوصف
أضف PowerShell Admin بمجرد النقر الأيمن على المجلد أو سطح المكتب.

## المتطلبات
- Windows 10/11
- صلاحيات Admin

## الطريقة 1: Registry (الأسرع)

```powershell
# انسخ هذا في PowerShell (Run as Admin)
New-Item -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin" -Force | Out-Null
New-ItemProperty -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin" -Name "(Default)" -Value "Open PowerShell here (Admin)" -PropertyType String -Force | Out-Null
New-ItemProperty -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin" -Name "Icon" -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force | Out-Null
New-Item -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin\command" -Force | Out-Null
New-ItemProperty -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin\command" -Name "(Default)" -Value "powershell.exe -noexit -Command Set-Location '%V'" -PropertyType String -Force | Out-Null
```

## الطريقة 2: تفعيل يدوي عبر Registry Editor

1. اضغط `Win + R` وكتب `regedit`
2. روح لـ: `HKEY_CURRENT_USER\Software\Classes\Directory\Background\shell`
3. كليك يمين → `New` → `Key` واسمه `PowerShellAdmin`
4. في اليمين اضغط كليك يمين → `New` → `String Value`
5. الاسم: `(Default)` والقيمة: `Open PowerShell here (Admin)`
6. اضغط كليك يمين تاني → `String Value`
7. الاسم: `Icon` والقيمة: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
8. اضغط كليك يمين → `New` → `Key` واسمه `command`
9. في `command` اضغط كليك يمين → `New` → `String Value`
10. الاسم: `(Default)` والقيمة: `powershell.exe -noexit -Command Set-Location '%V'`

## الإلغاء

```powershell
# اذا بتندم على الخطوة:
Remove-Item -Path "HKCU:\Software\Classes\Directory\Background\shell\PowerShellAdmin" -Recurse -Force
```

## ملاحظات
- إعادة تشغيل الجهاز ليست ضرورية
- قد تحتاج لإغلاق File Explorer وفتحه مجددا
- الخيار يظهر فقط على الخلفية، ليس على الملفات