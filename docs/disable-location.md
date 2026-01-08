# تعطيل Location Tracking

## عبر PowerShell

```powershell
Set-ItemProperty -Path 'HKCU:\Software\Microsoft\Windows NT\CurrentVersion\Sensor\Overrides\{BFA794E4-F964-4FDB-90F6-51056BFE4B44}' -Name SensorPermissionState -Value 0
```

## عبر Settings

1. اذهب إلى **Settings** → **Privacy & Security** → **Location**
2. فعّل **Location services**: اختر **Off**
3. تأكد من تعطيل التطبيقات الفردية