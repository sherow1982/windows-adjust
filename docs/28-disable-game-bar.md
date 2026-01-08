# تعطيل Xbox Game Bar

## عبر Settings
1. Settings → Gaming → Xbox Game Bar
2. أغلق **Enable Xbox Game Bar**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\GameDVR" -Name "AppCaptureEnabled" -Value 0
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_Enabled" -Value 0
```

## ملاحظات
- يحسن أداء الألعاب
- يقلل التأخير