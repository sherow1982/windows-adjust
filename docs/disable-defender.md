# تعطيل Windows Defender

## عبر PowerShell (Admin)

```powershell
Set-MpPreference -DisableRealtimeMonitoring $true
Set-MpPreference -DisableBehaviorMonitoring $true
```

## عبر Group Policy

1. اضغط `Win + R` واكتب `gpedit.msc`
2. اذهب إلى: Computer Configuration → Administrative Templates → Windows Components → Windows Defender Antivirus
3. اختر **Turn off Windows Defender Antivirus**
4. اختر **Enabled**

⚠️ **تحذير**: تثبيت برنامج حماية آخر إلزامي!