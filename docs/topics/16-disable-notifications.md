# تعطيل الإشعارات المزعجة

## الوصف
إيقاف إشعارات النظام والتطبيقات.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: System > Notifications
3. عطل "Show notifications"
4. أو عطل التطبيقات المحددة التي تريد
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل الإشعارات
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\PushNotifications" /v ToastEnabled /t REG_DWORD /d 0 /f
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Windows Notifications
3. ابحث عن "Disable Notifications Network"
4. اختر "Enabled"
```

## تعطيل إشعارات معينة

```
1. في Settings > Notifications
2. مرر لـ "Notifications from apps and other senders"
3. اختر التطبيق وعطل "Notifications"
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\PushNotifications" /v ToastEnabled /t REG_DWORD /d 1 /f
```
