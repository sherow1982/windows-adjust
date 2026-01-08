# تعطيل UAC (رسائل التأكيد)

## الوصف
إزالة النوافذ المزعجة التي تطلب إذن صلاحيات.

## الطريقة 1: Control Panel (سهلة)

```
1. اضغط Win وابحث عن "User Account Control"
2. افتح "Change User Account Control settings"
3. اسحب الـ slider لـ "Never Notify"
4. اضغط OK
5. أعد تشغيل الجهاز
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v EnableLUA /t REG_DWORD /d 0 /f
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options
3. ابحث عن: "User Account Control: Run all administrators in Admin Approval Mode"
4. اختر "Disabled"
```

## الإعادة

```powershell
# تفعيل UAC مجددا
Reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v EnableLUA /t REG_DWORD /d 1 /f
```

## تحذير
⚠️ تعطيل UAC يقلل من الحماية الأمنية! استخدم فقط على جهاز شخصي آمن.
