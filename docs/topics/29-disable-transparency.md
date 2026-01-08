# تعطيل التأثيرات الشفافة والضبابية

## الوصف
إيقاف تأثيرات Glass والضبابية في الواجهة.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: System > Display
3. اسحب لـ "Transparency effects"
4. عطل أو قلل التأثيرات
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل Acrylic blur
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v DisableAcrylicBackgroundImageFallback /t REG_DWORD /d 1 /f

# تعطيل Transparency
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableTransparency /t REG_DWORD /d 0 /f
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Desktop > Windows Aero
3. ابحث عن: "Do not use Aero Glass on taskbar"
4. اختر "Enabled"
```

## تعطيل تأثيرات محددة

```powershell
# تعطيل Blur
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 1 /f

# تعطيل Mica (Windows 11)
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableMicaBackground /t REG_DWORD /d 0 /f
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableTransparency /t REG_DWORD /d 1 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 0 /f
```

## ملاحظات
- تقليل التأثيرات يحسن الأداء
- مفيد على أجهزة بطيئة
