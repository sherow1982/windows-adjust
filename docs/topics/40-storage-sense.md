# تفعيل Storage Sense (تنظيف تلقائي)

## الوصف
تنظيف تلقائي للملفات المؤقتة والقديمة.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: System > Storage
3. في "Storage Sense" اختر "On"
4. اضغط "Advanced storage options"
5. في "Automatic user content cleanup" فعّل الخيارات
```

## الطريقة 2: تفاصيل الإعدادات

```
1. في Storage Sense Settings
2. اختر:
   - Delete temporary files that my apps aren't using
   - Delete files in my Downloads folder
   - Empty the Recycle Bin
   - Delete previous versions of Windows
3. اختر الجدولة: Daily/Weekly/Monthly
```

## الطريقة 3: Registry

```powershell
# PowerShell (Run as Admin)
# تفعيل Storage Sense
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\StorageSense\Parameters\StoragePolicy" /v 01 /t REG_DWORD /d 1 /f

# تفعيل حذف الملفات المؤقتة
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\StorageSense\Parameters\StoragePolicy" /v 04 /t REG_DWORD /d 1 /f
```

## تنظيف يدوي مباشر

```
1. في Storage Sense Settings
2. اضغط "Clean now" للتنظيف الفوري
```

## الخيارات المتقدمة

```
- Delete temporary Windows installation files
- Delete Windows Update Cleanup files
- Delete previous versions of Windows after 10 days
- Empty Recycle Bin automatically
```

## الإعادة - تعطيل Storage Sense

```
1. في Storage Sense Settings
2. اختر "Off"
```

## ملاحظات
- آمن جداً للتفعيل
- يوفر وقت كبير من التنظيف اليدوي
- مراقب صحة القرص الصلب
