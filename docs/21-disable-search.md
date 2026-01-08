# تعطيل Windows Search

## عبر Services
1. Win + R → `services.msc`
2. ابحث عن **Windows Search**
3. كليك يمين → Properties
4. Startup Type: **Disabled**
5. Stop

## عبر PowerShell
```powershell
Get-Service WSearch | Stop-Service -Force
Get-Service WSearch | Set-Service -StartupType Disabled
```

## ملاحظات
- يحرر موارد النظام
- قد يبطئ البحث في Start Menu