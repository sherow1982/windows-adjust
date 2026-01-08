# استخدام Disk Cleanup للتنظيف العميق

## الوصف
استخدام أداة تنظيف القرص الرسمية من مايكروسوفت.

## الطريقة 1: Disk Cleanup Tool

```
1. اضغط Win وابحث عن "Disk Cleanup"
2. اختر القرص الذي تريد تنظيفه
3. سيفحص النظام لبضع ثواني
```

## الخيارات المتاحة

```
☑ Recycle Bin
☑ Temporary Internet Files
☑ Downloaded Program Files
☑ Temporary files
☑ Windows Update Cleanup (كبير جداً!)
☑ Thumbnails
☑ DirectX Shader Cache
☑ D3D Cache
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# تشغيل Disk Cleanup بدون واجهة
Clean-Volume -DriveLetter C -Force

# أو للتنظيف العميق
Clean-Volume -DriveLetter C -Force -DeepClean
```

## الطريقة 3: Command Line

```batch
REM تشغيل Disk Cleanup من Command Prompt
diskpart
del /q /f /s %systemroot%\Temp\*
```

## التنظيف العميق (Advanced)

```
1. في Disk Cleanup اضغط "Clean up system files"
2. بحاجة لصلاحيات Admin
3. حدد:
   - Previous Windows installations
   - Temporary Windows installation files
   - Windows Update Cleanup
```

## قياس المساحة المحررة

```powershell
# اعرض حجم المجلد قبل التنظيف
get-item C:\Windows\Temp | Select-Object -ExpandProperty FullName
ls -la C:\Windows\Temp | Measure-Object -Sum Length
```

## ملاحظات
- آمنة جداً - لا حذف مهم
- يمكن تشغيلها بانتظام
- قد تحتاج عدة دقائق
