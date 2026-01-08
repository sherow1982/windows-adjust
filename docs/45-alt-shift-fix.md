# إصلاح Alt+Shift للغة

## عبر Settings
1. Settings → Time & Language → Language
2. Keyboard → Advanced keyboard settings
3. Input language hot keys
4. غير الاختصار أو عطله

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Keyboard Layout\Toggle" -Name "Language Hotkey" -Value "3"
Set-ItemProperty -Path "HKCU:\Keyboard Layout\Toggle" -Name "Layout Hotkey" -Value "3"
```

## ملاحظات
- 3 = معطل
- 1 = Alt+Shift
- 2 = Ctrl+Shift