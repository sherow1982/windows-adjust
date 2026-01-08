# إصلاح Microsoft Store

## Reset Store
```powershell
wsreset.exe
```

## إعادة تثبيت Store
```powershell
Get-AppXPackage *WindowsStore* -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
```

## مسح Cache
```powershell
Remove-Item "$env:LOCALAPPDATA\Packages\Microsoft.WindowsStore_*\LocalState\cache" -Force -Recurse
```

## ملاحظات
- يحل معظم مشاكل Store