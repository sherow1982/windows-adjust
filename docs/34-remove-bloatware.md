# حذف البرامج المثبتة مسبقاً

## حذف كل UWP Apps
```powershell
Get-AppxPackage -AllUsers | Where-Object {$_.Name -notlike "*Store*"} | Remove-AppxPackage
```

## حذف تطبيقات محددة
```powershell
Get-AppxPackage *3dbuilder* | Remove-AppxPackage
Get-AppxPackage *windowsmaps* | Remove-AppxPackage
Get-AppxPackage *zunemusic* | Remove-AppxPackage
Get-AppxPackage *windowscamera* | Remove-AppxPackage
```

## ملاحظات
- يحرر مساحة
- يحسن الأداء