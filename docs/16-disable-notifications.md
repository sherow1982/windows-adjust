# تعطيل الإشعارات

## عبر Settings
1. اذهب إلى Settings → System → Notifications
2. أغلق **Get notifications from apps and other senders**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\PushNotifications" -Name "ToastEnabled" -Value 0
```

## ملاحظات
يحسن الأداء ويقلل المقاطعات