# تعطيل SuperFetch (Sysmain)

## الوصف
وقف الخدمة التي تستهلك الرام والمعالج.

## الطريقة 1: Services

```powershell
# PowerShell (Run as Admin)
Stop-Service -Name SysMain -Force
Set-Service -Name SysMain -StartupType Disabled
```

## الطريقة 2: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Superfetch
3. عطل كل المهام
```

## الطريقة 3: Registry

```powershell
# تعطيل SuperFetch
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v PrefetchParameters /t REG_DWORD /d 0 /f
```

## التحقق من الخدمة

```powershell
Get-Service -Name SysMain

# يجب أن تكون Stopped و Disabled
```

## الإعادة

```powershell
Set-Service -Name SysMain -StartupType Automatic
Start-Service -Name SysMain
```

## ملاحظات
- مفيد للأجهزة بـ RAM قليل
- على أجهزة SSD قد لا تحتاج SuperFetch
- قد تلاحظ تحسن في الأداء العام
