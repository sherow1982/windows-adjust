<div dir="rtl">

# إزالة مكونات أوفيس الزيادة (Windows 11 IoT Enterprise LTSC)

بما إنك على **Windows 11 IoT Enterprise LTSC** (اللي مفهاش متجر Microsoft Store افتراضياً)، فيه طريقتين لإزالة مكونات أوفيس الزيادة:

## 1. الطريقة الأسرع (PowerShell - Remove All Bloat)

افتح PowerShell كمسؤول وانسخ الكود ده كله:

</div>

```powershell
# إزالة كل مكونات أوفيس اللي مش أساسية
$apps = @(
    "Microsoft.3DBuilder",
    "Microsoft.BingWeather",
    "Microsoft.GetHelp",
    "Microsoft.Getstarted",
    "Microsoft.MicrosoftOfficeHub",
    "Microsoft.MicrosoftSolitaireCollection",
    "Microsoft.MicrosoftStickyNotes",
    "Microsoft.MixedReality.Portal",
    "Microsoft.OneConnect",
    "Microsoft.People",
    "Microsoft.Print3D",
    "Microsoft.SkypeApp",
    "Microsoft.Wallet",
    "Microsoft.WebMediaExtensions",
    "Microsoft.WebpImageExtensions",
    "Microsoft.Xbox.TCUI",
    "Microsoft.XboxApp",
    "Microsoft.XboxGameOverlay",
    "Microsoft.XboxGamingOverlay",
    "Microsoft.XboxIdentityProvider",
    "Microsoft.XboxSpeechToTextOverlay",
    "Microsoft.YourPhone",
    "Microsoft.ZuneMusic",
    "Microsoft.ZuneVideo"
)

foreach ($app in $apps) {
    Get-AppxPackage -Name $app -AllUsers | Remove-AppxPackage -AllUsers -ErrorAction SilentlyContinue
    Get-AppxProvisionedPackage -Online | Where-Object DisplayName -like $app | Remove-AppxProvisionedPackage -Online -ErrorAction SilentlyContinue
}
Write-Host "تم إزالة مكونات أوفيس الزيادة." -ForegroundColor Green
```

<div dir="rtl">

تمت إضافة الكود أعلاه، زر النسخ سيظهر تلقائياً عند تمرير الماوس على الكود.

</div>
