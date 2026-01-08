# حذف OneNote

## الوصف
إزالة OneNote من الويندوز بالقوة.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: Apps > Apps and features
3. ابحث عن "Microsoft OneNote"
4. اضغط "Uninstall" ثم "Uninstall" مرة ثانية
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# حذف OneNote
Get-AppxPackage *onenote* | Remove-AppxPackage

# أو استخدم المسار المباشر
Remove-Item "C:\Program Files\Microsoft Office\root\Office*\OneNote*" -Recurse -Force
```

## الطريقة 3: حذف من Registry

```powershell
# حذف مفاتيح OneNote
Reg delete "HKCU\Software\Microsoft\Office\16.0\OneNote" /f /s
Reg delete "HKLM\Software\Microsoft\Office\OneNote" /f /s
```

## حذف البيانات المحفوظة

```powershell
# حذف ملفات OneNote
Remove-Item "$env:LocalAppData\Microsoft\OneNote" -Recurse -Force
Remove-Item "$env:OneDrive\Documents\OneNote" -Recurse -Force
```

## من قائمة البداية

```
1. Right Click على OneNote من Start Menu
2. اختر "Uninstall"
3. اضغط "Uninstall"
```

## استعادة OneNote

```powershell
# إذا أردت استعادته
# عبر Microsoft Store
```

## ملاحظات
- قد تجده متعلق بـ Microsoft Office
- تأكد قبل الحذف إذا كنت تستخدمه
