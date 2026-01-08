# حذف الملفات المؤقتة

## الوصف
تنظيف مجلدات Temp والملفات المؤقتة.

## الطريقة 1: Disk Cleanup Tool

```
1. اضغط Win وابحث عن "Disk Cleanup"
2. اختر القرص الذي تريد تنظيفه
3. ضع checkmark على:
   - Temporary Internet Files
   - Temporary files
   - Recycle Bin
   - Thumbnails
4. اضغط "Delete Files"
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# حذف الملفات المؤقتة
Remove-Item -Path "$env:temp\*" -Recurse -Force -ErrorAction SilentlyContinue

# حذف Windows Temp
Remove-Item -Path "C:\Windows\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue

# حذف Prefetch
Remove-Item -Path "C:\Windows\Prefetch\*" -Recurse -Force -ErrorAction SilentlyContinue

# حذف System Temp
Remove-Item -Path "$env:SystemRoot\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue
```

## الطريقة 3: Command Prompt

```batch
REM كحساب Admin
Del /q /f /s %temp%\*
Del /q /f /s C:\Windows\Temp\*
Del /q /f /s C:\Windows\Prefetch\*
```

## تنظيف المتصفح

```powershell
# حذف Internet Explorer Cache
Remove-Item -Path "$env:LocalAppData\Microsoft\Windows\Temporary Internet Files\*" -Recurse -Force

# حذف Chrome Cache
Remove-Item -Path "$env:LocalAppData\Google\Chrome\User Data\Default\Cache\*" -Recurse -Force
```

## الطريقة 4: Storage Sense (تلقائي)

```
1. اضغط Win + I
2. روح: System > Storage
3. فعّل "Storage Sense"
4. اضغط "Automatic user content cleanup"
```

## ملاحظات
- احذر من حذف الملفات المهمة
- أغلق البرامج قبل الحذف
- قد يحتاج إعادة تشغيل
