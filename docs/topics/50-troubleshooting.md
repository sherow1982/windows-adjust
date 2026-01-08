# دليل استكشاف الأخطاء والمشاكل

## المشاكل الشائعة وحلولها

### 1. تحطل النظام بعد تعديل

```
1. أعد تشغيل الجهاز في Safe Mode
2. استخدم System Restore
3. إسترجع من نقطة استعادة
4. في الأسوأ: استخدم Live USB لإصلاح
```

### 2. بطء النظام الشديد

```
1. افتح Task Manager (Ctrl + Shift + Esc)
2. شاهد العمليات التي تستهلك كثيراً
3. أغلق البرامج غير الضرورية
4. فحص Startup programs
5. تشغيل Disk Cleanup
6. فحص الفيروسات
```

### 3. عدم الاتصال بالإنترنت

```powershell
# جرب هذه الأوامر
ipconfig /release
ipconfig /renew
ipconfig /flushdns

# أو
netsh winsock reset catalog
netsh int ip reset resetall
```

### 4. لا تظهر أيقونات على سطح المكتب

```powershell
# PowerShell (Run as Admin)
kill -ProcessName explorer
Start-Process explorer
```

### 5. لا يوجد صوت

```
1. اضغط Win + I
2. روح: System > Sound
3. اختبر الصوت
4. تحقق من Volume
5. فحص Drivers
```

### 6. تجميد النظام (Freeze)

```
1. اضغط Ctrl + Shift + Esc (Task Manager)
2. جد العملية المسببة
3. اضغط "End Task"
4. إذا لم يفلح: Ctrl + Alt + Delete ثم Sign Out
```

## الملفات المهمة للنسخ الاحتياطية

```
- C:\Users\[YourUsername]\Desktop
- C:\Users\[YourUsername]\Documents
- C:\Users\[YourUsername]\Pictures
- %AppData% (البيانات الأخرى)
- %LocalAppData% (إعدادات التطبيقات)
```

## Safe Mode - الوضع الآمن

```
1. اضغط Win + I
2. روح: System > Recovery
3. اضغط "Restart now" تحت Advanced startup
4. اختر Troubleshoot > Advanced options > Startup Settings
5. اختر Safe Mode
```

## System Restore - استعادة النظام

```
1. اضغط Win وابحث عن "System Restore"
2. اختر نقطة استعادة قديمة
3. اضغط "Next" ثم "Finish"
4. سيعود النظام للحالة السابقة
```

## الملفات المؤقتة المهمة

```
آمنة للحذف:
- C:\Windows\Temp
- C:\Users\[YourUsername]\AppData\Local\Temp
- Recycle Bin
- Browser Cache

خطيرة (لا تحذفها):
- C:\Windows\System32
- C:\Windows\SysWOW64
- Registry Files
```

## تحديث البرامج والـ Drivers

```
1. Device Manager (Win + R ثم devmgmt.msc)
2. Right Click على الجهاز
3. اختر "Update driver"
4. اختر "Search automatically for drivers"
```

## عند حدوث خطأ

```
1. اكتب رمز الخطأ كاملاً
2. ابحث عنه في Google
3. اتبع الحلول الموثوقة
4. جرب حل واحد في المرة
5. اختبر بعد كل خطوة
```

## تحذيرات مهمة

⚠️ **لا تحذف أبداً:**
- Windows System Files
- Active Applications
- Registry unless you know exactly what you're doing
- Boot Files

## الحصول على الدعم

- Microsoft Support Center
- Windows Official Forums
- Reddit Tech Communities
- Tech Support YouTube Channels
