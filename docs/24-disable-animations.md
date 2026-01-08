# تعطيل Animations

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop\WindowMetrics" -Name "MinAnimate" -Value "0"
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" -Name "TaskbarAnimations" -Value 0
```

## عبر Settings
1. Settings → Ease of Access → Display
2. فعّل **Show animations in Windows**

## ملاحظات
- يسرع فتح وإغلاق النوافذ
- الويندوز يبقى أسرع