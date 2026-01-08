# تعطيل الحركات والانتقالات

## الوصف
إيقاف حركات فتح النوافذ والقوائم.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: System > Display
3. اضغط "Advanced display"
4. عطل "Show animations when minimizing and maximizing windows"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل الحركات
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewAlphaImageBlending /t REG_DWORD /d 0 /f

# تعطيل انتقالات المنطقة
Reg add "HKCU\Software\Microsoft\Windows\DWM" /v AnimationAttributionEnabled /t REG_DWORD /d 0 /f
```

## تعطيل تأثيرات محددة

```powershell
# تعطيل الكشط (Swiping)
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewWatermark /t REG_DWORD /d 0 /f

# تعطيل الـ Fade effects
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewShadow /t REG_DWORD /d 0 /f
```

## الطريقة 3: PowerShell

```powershell
# تعطيل كل الحركات
$animation = @(
    'HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced'
)

foreach ($path in $animation) {
    Set-ItemProperty -Path $path -Name ListviewAlphaImageBlending -Value 0 -Force
}
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewAlphaImageBlending /t REG_DWORD /d 1 /f
Reg add "HKCU\Software\Microsoft\Windows\DWM" /v AnimationAttributionEnabled /t REG_DWORD /d 1 /f
```
