# تعطيل Windows Update

## الوصف
أوقف التحديثات التلقائية بشكل نهائي والتحكم الكامل فيها.

## الطريقة 1: Group Policy (Pro/Enterprise فقط)

```powershell
# اضغط Win + R وكتب gpedit.msc
# ثم روح:
# Computer Configuration > Administrative Templates > Windows Components > Windows Update
# ابحث عن: "Configure Automatic Updates"
# اختر: "Disabled" أو "2 - Notify for download and auto install"
```

## الطريقة 2: Registry (All Editions)

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoUpdate /t REG_DWORD /d 1 /f
```

## الطريقة 3: Services

```powershell
# تعطيل خدمة Windows Update
Stop-Service -Name wuauserv -Force
Set-Service -Name wuauserv -StartupType Disabled
Set-Service -Name WaaSMedicSvc -StartupType Disabled
```

## الطريقة 4: Task Scheduler

1. اضغط `Win + R` وكتب `taskschd.msc`
2. روح: `Microsoft > Windows > UpdateOrchestrator`
3. عطل كل المهام

## الإعادة

```powershell
# تفعيل التحديثات مجددا
Reg delete "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /f
Start-Service -Name wuauserv
Set-Service -Name wuauserv -StartupType Automatic
```

## ملاحظات
⚠️ تحديثات الأمان مهمة! استخدم هذا بحذر.
