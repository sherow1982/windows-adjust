# تسريع إقلاع الويندوز (Fast Boot)

## الوصف
تفعيل Fast Startup وتقليل وقت التشغيل بشكل ملحوظ.

## الطريقة 1: Power Options

```
1. اضغط Win وابحث عن "Control Panel"
2. روح: Power Options
3. اضغط "Choose what the power button does"
4. اضغط "Change settings that are currently unavailable"
5. ضع checkmark على "Turn on fast startup"
6. اضغط "Save changes"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /v HiberbootEnabled /t REG_DWORD /d 1 /f
```

## الطريقة 3: PowerShell

```powershell
# تفعيل Fast Boot
powercfg /h on

# تعطيل Fast Boot (للصيانة)
powercfg /h off
```

## تحسينات إضافية

```powershell
# تعطيل البرامج في بداية التشغيل
# اضغط Win + R وكتب msconfig
# اذهب لـ Startup tab
# الغي تحديد البرامج غير الضرورية
```

## قياس السرعة

```powershell
# اختبر سرعة الإقلاع
Get-CimInstance Win32_OperatingSystem | Select-Object LastBootUpTime
```

## ملاحظات
- Windows 11 لديه Fast Startup بشكل افتراضي
- قد تحتاج لحذف ملفات مؤقتة
