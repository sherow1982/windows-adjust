# تعطيل التأثيرات البصرية

## الوصف
إيقاف الرسومات والظلال والتأثيرات المرئية.

## الطريقة 1: System Settings

```
1. اضغط Win وابحث عن "Advanced system settings"
2. في "Performance" اضغط "Settings"
3. اختر "Adjust for best performance"
4. أو انتقِ ما تريد تعطيله
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل كل التأثيرات البصرية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v VisualFXSetting /t REG_DWORD /d 2 /f
```

## تعطيل تأثيرات محددة

```powershell
# تعطيل شفافية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 1 /f

# تعطيل الرسومات المتحركة
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewAlphaImageBlending /t REG_DWORD /d 0 /f

# تعطيل الظلال
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewShadow /t REG_DWORD /d 0 /f
```

## الخيارات في Performance Settings

```
☑ Animate controls and elements inside windows
☑ Animate windows when minimizing and maximizing
☑ Animations in the taskbar
☑ Enable Peek
☑ Show shadows under mouse pointer
☑ Show thumbnails instead of icons
☑ Show translucent selection rectangle
☑ Show window contents while dragging
☑ Smooth-scroll list boxes
☑ Use drop shadows for icon labels on the desktop
```

## الإعادة

```powershell
# استعيد التأثيرات
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v VisualFXSetting /t REG_DWORD /d 3 /f
```
