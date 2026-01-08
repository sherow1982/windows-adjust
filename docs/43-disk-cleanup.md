# Disk Cleanup المتقدم

## مسح Windows Update Cache
```powershell
Stop-Service wuauserv
Remove-Item "C:\Windows\SoftwareDistribution\*" -Force -Recurse
Start-Service wuauserv
```

## مسح Driver Store
```powershell
PNPUtil.exe /delete-driver oem*.inf /uninstall /force
```

## مسح Component Store
```powershell
Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase
```

## ملاحظات
- يحرر مساحة كبيرة جداً