# إصلاح Microsoft Store

## الوصف
حل مشاكل متجر مايكروسوفت والتطبيقات.

## الطريقة 1: Reset Store

```
1. اضغط Win + I
2. روح: Apps > Apps and features
3. ابحث عن "Microsoft Store"
4. اضغط عليه وأختر "Reset"
5. اضغط "Reset" للتأكيد
```

## الطريقة 2: PowerShell Repair

```powershell
# PowerShell (Run as Admin)
# إصلاح Windows Store
Get-AppxPackage -AllUsers Microsoft.WindowsStore | Remove-AppxPackage -AllUsers
Get-AppXPackage -AllUsers Microsoft.WindowsStore | Add-AppxPackage -Register -DisableDevelopmentMode
```

## الطريقة 3: Clear Store Cache

```powershell
# PowerShell (Run as Admin)
# إيقاف Store
Stop-Process -Name "WinStore.App" -Force -ErrorAction SilentlyContinue

# حذف Cache
Remove-Item "$env:LocalAppData\Packages\Microsoft.WindowsStore_*\LocalState\*" -Recurse -Force
```

## الطريقة 4: Re-register Store

```powershell
# PowerShell (Run as Admin)
# إعادة تسجيل Store
Get-AppxPackage Microsoft.WindowsStore -AllUsers | ForEach-Object { Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml" }
```

## حل مشاكل معينة

```powershell
# إذا لم تفتح تطبيقات من Store
Get-AppxPackage -AllUsers | Where-Object {$_.InstallLocation -ne $null} | % { Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml" }
```

## الخطوات الشاملة

```
1. فتح PowerShell كـ Admin
2. تشغيل الأوامر أعلاه
3. إعادة تشغيل الجهاز
4. فتح Microsoft Store والتحقق
```

## ملاحظات
- قد تحتاج عدة دقائق
- تأكد من الاتصال بالإنترنت
- حاول مرة أخرى بعد الإعادة
