# تفعيل خطة الأداء القصوى (Ultimate)

## الوصف
تفعيل الأداء الأقصى على حساب استهلاك الطاقة.

## الطريقة 1: Power Options

```
1. اضغط Win وابحث عن "Control Panel"
2. روح: Power Options
3. اضغط "Show additional plans"
4. اختر "Ultimate Performance"
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# أولاً، أنشئ خطة Ultimate Performance
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749e978 | ForEach-Object { $guid = $_ -replace 'Power Scheme GUID: (.*) \(.*', '$1'; $guid }

# أو استخدم GUID الموجود
powercfg -setactive 8c5e7fda-e8bf-45a9-a30d-e0db009fd481
```

## الطريقة 3: Registry

```powershell
# تفعيل Ultimate Performance
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffectPreferences" /v VisualFXSetting /t REG_DWORD /d 3 /f
```

## الإعدادات المتقدمة

```
1. في Power Options اختر "Ultimate Performance"
2. اضغط "Change plan settings"
3. اضغط "Change advanced power settings"
4. فعّل:
   - High performance for all components
   - Maximum processor state: 100%
   - Turn off hard disk after: Never
```

## تحذير
⚠️ يزيد استهلاك الطاقة والحرارة بشكل كبير! استخدم على أجهزة سطح المكتب.

## العودة للإعدادات العادية

```powershell
powercfg -setactive 381b4222-f694-41f0-9685-ff5bb260df2e  # Balanced
```
