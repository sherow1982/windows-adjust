# إيقاف Auto Restart بعد الأخطاء

## عبر GUI
1. Win + R → `sysdm.cpl`
2. Advanced → Startup and Recovery → Settings
3. أزل علامة **Automatically restart**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\CrashControl" -Name "AutoReboot" -Value 0
```

## ملاحظات
- يسمح لك بقراءة رسالة الخطأ