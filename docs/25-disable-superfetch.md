# تعطيل SuperFetch/SysMain

## عبر PowerShell
```powershell
Get-Service SysMain | Stop-Service -Force
Get-Service SysMain | Set-Service -StartupType Disabled
```

## ملاحظات
- مفيد للـ SSD
- يقلل استخدام القرص
- يحسن الأداء