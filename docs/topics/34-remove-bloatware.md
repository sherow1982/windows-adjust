# حذف Bloatware (برامج مايكروسوفت الزيادة)

## الوصف
إزالة البرامج غير المستخدمة من مايكروسوفت.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: Apps > Apps and features
3. ابحث عن البرنامج
4. اضغط عليه واختر "Uninstall"
5. اضغط "Uninstall" مرة ثانية
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# حذف Microsoft News
Get-AppxPackage *msn* | Remove-AppxPackage

# حذف Weather
Get-AppxPackage *weather* | Remove-AppxPackage

# حذف Alarms
Get-AppxPackage *alarms* | Remove-AppxPackage

# حذف Camera
Get-AppxPackage *camera* | Remove-AppxPackage

# حذف Photos
Get-AppxPackage *photos* | Remove-AppxPackage

# حذف Microsoft Store
Get-AppxPackage *store* | Remove-AppxPackage
```

## حذف برامج محددة

```powershell
# قائمة كاملة
$apps = @(
    "Microsoft.WindowsMaps",
    "Microsoft.WindowsSound",
    "Microsoft.WindowsAlarms",
    "Microsoft.WindowsCalculator",
    "Microsoft.ZuneMusic",
    "Microsoft.ZuneVideo",
    "Microsoft.People",
    "Microsoft.WindowsCamera",
    "Microsoft.BingNews",
    "Microsoft.GetHelp",
    "Microsoft.Getstarted"
)

foreach ($app in $apps) {
    Get-AppxPackage $app | Remove-AppxPackage -ErrorAction SilentlyContinue
}
```

## استعادة البرامج

```powershell
# استعيد تطبيق محذوف
Get-AppxPackage -AllUsers -Name *camera* | Add-AppxPackage -Register -DisableDevelopmentMode
```

## ملاحظات
- بعض البرامج قد تكون ضرورية!
- عمل نقطة استعادة أولاً موصى به
