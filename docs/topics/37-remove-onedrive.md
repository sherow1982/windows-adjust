# حذف OneDrive

## الوصف
إزالة التخزين السحابي OneDrive من الويندوز.

## الطريقة 1: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > OneDrive
3. ابحث عن: "Prevent the usage of OneDrive"
4. اختر "Enabled"
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# إيقاف OneDrive
Stop-Process -Name OneDrive -Force -ErrorAction SilentlyContinue

# الانتظار
Start-Sleep -Seconds 2

# حذف OneDrive
C:\Windows\System32\OneDriveSetup.exe /uninstall
```

## الطريقة 3: من Settings

```
1. اضغط Win + I
2. روح: System > Cloud and storage
3. عطل "Microsoft OneDrive"
```

## حذف البيانات

```powershell
# حذف مجلد OneDrive
Remove-Item "$env:OneDrive" -Recurse -Force
Remove-Item "$env:OneDriveCommercial" -Recurse -Force

# حذف من Registry
Reg delete "HKCU\Software\Microsoft\OneDrive" /f /s
```

## إعادة تفعيل OneDrive

```powershell
# إذا أردت استعادته
C:\Windows\System32\OneDriveSetup.exe
```

## الطريقة 4: حذف بدون تثبيت

```
1. Right Click على OneDrive في Taskbar
2. اختر "Settings"
3. اذهب لـ "Account"
4. اضغط "Unlink this PC"
```

## ملاحظات
- قد تحتاج حساب Microsoft للتحديثات
- تأكد من حفظ الملفات قبل الحذف
