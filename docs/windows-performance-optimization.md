# تحسين أداء ويندوز 10/11 (Windows Performance Optimization)

## تعديلات Registry لتحسين الأداء

### 1. تسريع إغلاق النظام (Faster Shutdown)

هذه التعديلات تقلل الوقت اللي ينتظره النظام قبل إغلاق البرامج:

```cmd
REM فتح CMD كمسؤول أولاً

REM 1. تفعيل إغلاق تلقائي للبرامج
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v AutoEndTasks /t REG_SZ /d 1 /f

REM 2. تقليل وقت الانتظار لإغلاق التطبيقات (2 ثانية)
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v WaitToKillAppTimeout /t REG_SZ /d 2000 /f

REM 3. تقليل وقت انتظار البرامج المتوقفة
reg add "HKEY_CURRENT_USER\Control Panel\Desktop" /v HungAppTimeout /t REG_SZ /d 2000 /f

REM 4. تقليل وقت إغلاق الخدمات
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control" /v WaitToKillServiceTimeout /t REG_SZ /d 2000 /f
```

---

### 2. تحسين أداء الشبكة (Network Performance)

```cmd
REM تعطيل Network Throttling Index
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v NetworkThrottlingIndex /t REG_DWORD /d 0xffffffff /f

REM تحسين TCP Ack Frequency
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces" /v TcpAckFrequency /t REG_DWORD /d 1 /f
```

---

### 3. تحسين استجابة النظام (System Responsiveness)

```cmd
REM تحسين System Responsiveness (10 = أفضل للاستخدام اليومي)
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v SystemResponsiveness /t REG_DWORD /d 10 /f

REM تفعيل Large System Cache (للأجهزة برام 8 جيجا فما فوق)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v LargeSystemCache /t REG_DWORD /d 1 /f
```

---

### 4. تحسين أولوية البرامج (Process Priority)

```cmd
REM تحسين أولوية البرامج النشطة (26 = مثالي للأداء العام)
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\PriorityControl" /v Win32PrioritySeparation /t REG_DWORD /d 26 /f
```

**قيم Win32PrioritySeparation:**
- `26` (0x1A) = أفضل للاستخدام اليومي
- `38` (0x26) = أفضل للألعاب

---

### 5. تعطيل خدمات Telemetry والتتبع (Disable Telemetry)

```cmd
REM تعطيل DiagTrack service
sc config DiagTrack start= disabled
sc stop DiagTrack

REM تعطيل dmwappushservice
sc config dmwappushservice start= disabled
sc stop dmwappushservice

REM تعطيل Telemetry عبر Registry
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f
```

---

### 6. تعطيل تأثيرات Windows البصرية (Disable Visual Effects)

```cmd
REM تعطيل كل التأثيرات للأداء الأقصى
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" /v VisualFXSetting /t REG_DWORD /d 2 /f
```

---

### 7. تفعيل Ultimate Performance Power Plan

في PowerShell كمسؤول:

```powershell
# تفعيل Ultimate Performance Plan (مخفي بشكل افتراضي)
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61

# تفعيل High Performance Plan
powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
```

---

### 8. تعطيل Windows Search Indexing (اختياري)

```cmd
REM إيقاف خدمة Windows Search
sc config WSearch start= disabled
sc stop WSearch
```

**ملحوظة:** سيبطئ البحث في قائمة Start لكن سيحسّن الأداء.

---

### 9. تعطيل Hibernate (لتوفير مساحة)

```cmd
powercfg /hibernate off
```
سيحذف ملف `hiberfil.sys` الكبير.

---

### 10. تنظيف ملفات Temp تلقائياً

```cmd
REM حذف ملفات Temp المستخدم
rd /s /q %temp%
mkdir %temp%

REM حذف ملفات Windows Temp
rd /s /q C:\Windows\Temp
mkdir C:\Windows\Temp

REM تنظيف Prefetch
rd /s /q C:\Windows\Prefetch
mkdir C:\Windows\Prefetch
```

---

## أوامر الصيانة (Maintenance Commands)

### فحص وإصلاح ملفات النظام

```cmd
REM فحص سلامة ملفات النظام
sfc /scannow

REM إصلاح DISM
DISM /Online /Cleanup-Image /RestoreHealth

REM فحص القرص وإصلاح الأخطاء
chkdsk C: /f /r
```

---

### إعادة ضبط Windows Update

```cmd
net stop wuauserv
net stop cryptSvc
net stop bits
net stop msiserver

ren C:\Windows\SoftwareDistribution SoftwareDistribution.old
ren C:\Windows\System32\catroot2 catroot2.old

net start wuauserv
net start cryptSvc
net start bits
net start msiserver
```

---

### إصلاح Microsoft Store

```powershell
# في PowerShell كمسؤول
Get-AppXPackage *WindowsStore* -AllUsers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}

# أو في CMD
wsreset.exe
```

---

## ملاحظات مهمة

⚠️ **تحذيرات:**
- عمل Backup للـ Registry قبل التعديل (`File > Export` في regedit)
- تشغيل CMD/PowerShell كمسؤول ضروري
- إعادة تشغيل الجهاز بعد التعديلات
- لا تعدّل أي شيء إذا كنت غير متأكد

✅ **نصائح:**
- اختبر على جهاز افتراضي أولاً
- لا تطبّق كل التعديلات دفعة واحدة
- راقب الأداء بعد كل تغيير

---

*تم الإضافة بتاريخ: 2026-01-08*
