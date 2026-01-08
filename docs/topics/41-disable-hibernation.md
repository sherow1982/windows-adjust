# تعطيل Hibernation (السبات)

## الوصف
حرر مساحة بتعطيل ملف hiberfil.sys.

## الطريقة 1: Command Prompt

```batch
REM كحساب Admin
powercfg /h off
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
powercfg /h off
```

## الطريقة 3: Settings

```
1. اضغط Win + I
2. روح: System > Power
3. اضغط "Sleep and hibernation"
4. عطل "Hibernation"
```

## الطريقة 4: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Power" /v HibernateEnabled /t REG_DWORD /d 0 /f
```

## التحقق من الملف

```powershell
# اعرض حجم hiberfil.sys
get-item C:\hiberfil.sys -Force | Select-Object Length

# إذا كان 0 فهو معطل
```

## الإعادة - إعادة تفعيل Hibernation

```powershell
powercfg /h on

# أو من Registry
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Power" /v HibernateEnabled /t REG_DWORD /d 1 /f
```

## ملاحظات
- يحرر مساحة = حجم الذاكرة
- مفيد إذا كنت لا تستخدم Sleep
- يقلل استهلاك الطاقة
