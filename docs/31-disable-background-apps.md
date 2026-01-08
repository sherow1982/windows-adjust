# تعطيل Background Apps

## عبر Settings
1. Settings → Privacy → Background apps
2. أغلق **Let apps run in the background**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications" -Name "GlobalUserDisabled" -Value 1
```

## ملاحظات
- يحسن عمر البطارية
- يقلل استهلاك CPU/RAM