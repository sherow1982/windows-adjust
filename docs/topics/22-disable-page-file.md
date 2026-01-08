# تعطيل صفحة الذاكرة الافتراضية (Page File)

## الوصف
حرر مساحة قرصك بتعطيل ملف الذاكرة الافتراضية.

## المتطلبات
- ذاكرة RAM كافية (16GB+)
- أجهزة سطح المكتب بشكل أساسي

## الطريقة 1: System Settings

```
1. اضغط Win + Pause لـ System Properties
2. اضغط "Advanced system settings"
3. في "Performance" اضغط "Settings"
4. اذهب لـ "Advanced" tab
5. تحت "Virtual memory" اضغط "Change"
6. الغي اختيار "Automatically manage paging file size"
7. اختر "No paging file"
8. اضغط "Set" ثم "OK"
9. أعد تشغيل الجهاز
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# عطل Page File
GET-WmiObject Win32_ComputerSystem | SET-WmiInstance -Arguments @{AutomaticManagedPagefile=$False}
$pagefile = Get-WmiObject Win32_PageFileSetting
if ($pagefile) { $pagefile.Delete() }
```

## الطريقة 3: Registry

```powershell
# تعطيل Page File
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v PagingFiles /t REG_MULTI_SZ /d "" /f
```

## تحذير
⚠️ تحتاج RAM كافية! بخلافه قد يتعطل النظام.

## الإعادة - إعادة تفعيل

```powershell
# استعد Page File
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v PagingFiles /t REG_MULTI_SZ /d "C:\pagefile.sys 0 0" /f
```

## قياس استخدام الذاكرة

```powershell
Get-Process | Sort-Object WorkingSet -Descending | Select-Object -First 10
```
