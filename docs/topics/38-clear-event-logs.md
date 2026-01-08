# مسح Event Logs (سجلات الأحداث)

## الوصف
حذف سجلات الأحداث والنظام.

## الطريقة 1: Event Viewer

```
1. اضغط Win وابحث عن "Event Viewer"
2. في الجهة اليسرى: Windows Logs
3. Right Click على كل log (System, Security, Application)
4. اختر "Clear Log"
5. اضغط "Clear"
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# حذف جميع Event Logs
Get-EventLog -LogName * | ForEach-Object { Clear-EventLog -LogName $_.Log }

# أو حذف log محدد
Clear-EventLog -LogName System
Clear-EventLog -LogName Application
Clear-EventLog -LogName Security
```

## الطريقة 3: Command Prompt

```batch
REM كحساب Admin
wevtutil cl System
wevtutil cl Application
wevtutil cl Security
```

## حذف Logs محددة

```powershell
# حذف PowerShell Logs
Clear-EventLog -LogName "Windows PowerShell"

# حذف Security logs
Clear-EventLog -LogName Security

# حذف Task Scheduler logs
Clear-EventLog -LogName "Microsoft-Windows-TaskScheduler/Operational"
```

## استعراض السجلات قبل الحذف

```powershell
# عرض حجم السجلات
Get-EventLog -LogName * | Select-Object Log, Entries

# عرض آخر 10 أحداث
Get-EventLog -LogName System -Newest 10
```

## تحذير
⚠️ لا يمكن استرجاع السجلات بعد الحذف! احفظ نسخة أولاً.
