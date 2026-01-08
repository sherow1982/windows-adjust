# فحص القرص والملفات (CHKDSK + SFC)

## الوصف
فحص واصلاح أخطاء القرص والملفات النظام.

## الطريقة 1: CHKDSK - فحص القرص

```powershell
# PowerShell (Run as Admin)
# فحص القرص (بدون إصلاح)
chkdsk C:

# فحص وإصلاح (يحتاج إعادة تشغيل)
chkdsk C: /F

# فحص شامل
chkdsk C: /F /R
```

## الطريقة 2: CHKDSK - الجدولة

```
1. اضغط Command Prompt كـ Admin
2. اكتب: chkdsk C: /F
3. اضغط Y لإعادة التشغيل
4. سيفحص عند الإقلاع
```

## الطريقة 3: SFC - فحص ملفات النظام

```powershell
# PowerShell (Run as Admin)
# فحص فقط
sfc /scannow

# فحص وإصلاح
sfc /scannow

# فحص وإصلاح مع offline files
sfc /scannow /offbootdir=C: /offwindir=C:\Windows
```

## الطريقة 4: DISM - إصلاح شامل

```powershell
# PowerShell (Run as Admin)
# فحص Windows Image
DISM /Online /Cleanup-Image /ScanHealth

# إصلاح Windows Image
DISM /Online /Cleanup-Image /RestoreHealth

# إصلاح شامل
DISM /Online /Cleanup-Image /StartComponentCleanup
```

## الطريقة 5: الأوامر الكاملة

```powershell
# 1. فحص SFC
sfc /scannow

# 2. إذا فشل، استخدم DISM
DISM /Online /Cleanup-Image /RestoreHealth

# 3. ثم فحص CHKDSK
chkdsk C: /F

# 4. إعادة التشغيل
Restart-Computer -Force
```

## قراءة النتائج

```
Found x bad clusters
Found x corrupt files
```

## ملاحظات
- قد يستغرق وقتاً طويلاً
- لا تغلق الـ terminal
- تأكد من نسخة احتياطية
