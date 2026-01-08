# حل مشكلة Alt+Shift لتبديل اللغة

## الوصف
إصلاح مشكلة تبديل اللغة بـ Alt+Shift.

## الطريقة 1: Language Settings

```
1. اضغط Win + I
2. روح: Time & Language > Language & region
3. اضغط "Language options" بجانب اللغة
4. اضغط "Keyboards"
5. تأكد من وجود لوحة المفاتيح المطلوبة
```

## الطريقة 2: Registry Fix

```powershell
# PowerShell (Run as Admin)
# فعّل تبديل اللغة بـ Alt+Shift
Reg add "HKCU\Keyboard Layout\Toggle" /v "Hotkey" /t REG_SZ /d "1" /f
Reg add "HKCU\Keyboard Layout\Toggle" /v "Language Hotkey" /t REG_SZ /d "1" /f
Reg add "HKCU\Keyboard Layout\Toggle" /v "Layout Hotkey" /t REG_SZ /d "2" /f
```

## الطريقة 3: تعيين Hotkey مباشر

```
1. في Language Settings
2. اضغط على اللغة المطلوبة
3. اضغط "Options"
4. اختر Keyboard
5. اضغط "Keyboard options"
6. اختر Hotkey المطلوب
```

## الطريقة 4: حل شامل

```powershell
# PowerShell (Run as Admin)
# إزالة وإعادة تثبيت لوحة المفاتيح
Reg delete "HKCU\Keyboard Layout\Preload" /f
Reg add "HKCU\Keyboard Layout\Preload" /v "1" /t REG_SZ /d "00000409" /f
Reg add "HKCU\Keyboard Layout\Preload" /v "2" /t REG_SZ /d "00000401" /f
```

## استخدام Language Switcher

```
1. اضغط Win وابحث عن "Language settings"
2. اختر اللغة من القائمة
3. أو استخدم Windows + Space (الافتراضي)
```

## تحذير
⚠️ بعض الألعاب والتطبيقات قد تتضارب مع هذه الإعدادات!
