# تعطيل Windows Update

## الطريقة الأولى: عبر Services

1. اضغط `Win + R` واكتب `services.msc`
2. ابحث عن **Windows Update**
3. اضغط كليك يمين → Properties
4. اختر Startup Type: **Disabled**
5. اضغط Stop
6. اضغط Apply و OK

## الطريقة الثانية: عبر PowerShell

```powershell
Get-Service wuauserv | Stop-Service -Force
Get-Service wuauserv | Set-Service -StartupType Disabled
```

## ملاحظات
- قد تحتاج إعادة تشغيل
- تأكد من تثبيت التحديثات الحرجة يدوياً