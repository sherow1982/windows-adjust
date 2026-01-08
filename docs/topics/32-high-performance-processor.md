# تفعيل وضع الأداء العالي للمعالج

## الوصف
تشغيل المعالج بأقصى سرعة دائماً.

## الطريقة 1: Power Options

```
1. اضغط Win وابحث عن "Control Panel"
2. روح: Power Options
3. اختر "High performance"
4. أو اختر "Ultimate Performance" (إن توفرت)
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# تفعيل Maximum Performance
powercfg -setactive 8c5e7fda-e8bf-45a9-a30d-e0db009fd481

# أو High Performance
powercfg -setactive 381b4222-f694-41f0-9685-ff5bb260df2e
```

## الطريقة 3: Registry

```powershell
# تفعيل High Performance
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffectPreferences" /v VisualFXSetting /t REG_DWORD /d 3 /f

# تفعيل Processor
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\DeviceAccess" /v Performance /t REG_DWORD /d 1 /f
```

## تفعيل Maximum Processor Speed

```
1. في Power Options اختر High Performance
2. اضغط "Change plan settings"
3. اضغط "Change advanced power settings"
4. روح: Processor power management > Maximum processor state
5. أضبطها على 100%
```

## الإعادة - العودة للإعدادات الموازنة

```powershell
powercfg -setactive 381b4222-f694-41f0-9685-ff5bb260df2e

# أو Balanced Plan
powercfg -setactive 381b4222-f694-41f0-9685-ff5bb260df2e
```

## التحقق من الأداء الحالي

```powershell
# اعرض النقطة الحالية
powercfg /query

# اعرض سرعة المعالج
Get-CimInstance Win32_Processor | Select-Object Name, MaxClockSpeed, CurrentClockSpeed
```

## ملاحظات
⚠️ يزيد استهلاك الطاقة والحرارة! استخدم على سطح المكتب.
