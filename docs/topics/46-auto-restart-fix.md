# إيقاف إعادة التشغيل التلقائية

## الوصف
منع الويندوز من إعادة التشغيل بعد الأخطاء.

## الطريقة 1: System Properties

```
1. اضغط Win + Pause
2. في الجهة اليسرى: "Advanced system settings"
3. في "Startup and Recovery" اضغط "Settings"
4. الغي اختيار "Automatically restart"
5. اضغط "OK"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل Auto Restart
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\CrashControl" /v AutoReboot /t REG_DWORD /d 0 /f
```

## الطريقة 3: Registry - طريقة بديلة

```powershell
# تعطيل Auto Restart على الشاشة الزرقاء
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\CrashControl" /v CrashDumpEnabled /t REG_DWORD /d 1 /f
```

## الطريقة 4: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > System
3. ابحث عن: "Display Stop Error Screen"
4. اختر "Enabled"
```

## الإعادة - تفعيل Auto Restart

```powershell
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\CrashControl" /v AutoReboot /t REG_DWORD /d 1 /f
```

## ملاحظات
- مفيد لقراءة رسائل الخطأ
- يعطيك وقت للبحث عن الحل
- احفظ رمز الخطأ للبحث عنه
