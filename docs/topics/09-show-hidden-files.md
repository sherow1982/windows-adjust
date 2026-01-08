# إظهار الملفات والامتدادات المخفية

## الوصف
عرض الملفات المخفية والامتدادات لكل الملفات.

## الطريقة 1: File Explorer (الأسهل)

```
1. افتح File Explorer
2. اضغط Ctrl + H لتبديل الملفات المخفية
# أو:
1. في File Explorer اضغط View من الأعلى
2. اختر "Hidden items" لإظهار الملفات المخفية
3. اختر "File name extensions" لإظهار الامتدادات
```

## الطريقة 2: Registry

```powershell
# إظهار الملفات المخفية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v Hidden /t REG_DWORD /d 1 /f

# إظهار الامتدادات
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v HideFileExt /t REG_DWORD /d 0 /f
```

## الطريقة 3: PowerShell

```powershell
# إظهار الملفات المخفية والنظام
(Get-Item -Path "C:\" -Force).Attributes = "Hidden"

# عرض الملفات المخفية
Get-ChildItem -Path C:\ -Force -Hidden
```

## الإعادة - إخفاء

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v Hidden /t REG_DWORD /d 2 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v HideFileExt /t REG_DWORD /d 1 /f
```
