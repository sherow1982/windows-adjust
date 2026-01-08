# تعطيل Transparency Effects

## عبر Settings
1. Settings → Personalization → Colors
2. أغلق **Transparency effects**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" -Name "EnableTransparency" -Value 0
```

## ملاحظات
- يحسن الأداء على الأجهزة الضعيفة
- يقلل استهلاك GPU