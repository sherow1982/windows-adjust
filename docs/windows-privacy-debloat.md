# إزالة Bloatware وتحسين الخصوصية (Windows Debloat & Privacy)

## حذف تطبيقات Windows المثبّتة مسبقاً

### حذف بشكل جماعي بـ PowerShell

في PowerShell كمسؤول:

```powershell
# حذف كل Bloatware المعروف

Get-AppxPackage *3dbuilder* | Remove-AppxPackage
Get-AppxPackage *windowsalarms* | Remove-AppxPackage
Get-AppxPackage *windowscommunicationsapps* | Remove-AppxPackage
Get-AppxPackage *windowscamera* | Remove-AppxPackage
Get-AppxPackage *officehub* | Remove-AppxPackage
Get-AppxPackage *skypeapp* | Remove-AppxPackage
Get-AppxPackage *getstarted* | Remove-AppxPackage
Get-AppxPackage *zunemusic* | Remove-AppxPackage
Get-AppxPackage *windowsmaps* | Remove-AppxPackage
Get-AppxPackage *solitairecollection* | Remove-AppxPackage
Get-AppxPackage *bingfinance* | Remove-AppxPackage
Get-AppxPackage *zunevideo* | Remove-AppxPackage
Get-AppxPackage *bingnews* | Remove-AppxPackage
Get-AppxPackage *onenote* | Remove-AppxPackage
Get-AppxPackage *people* | Remove-AppxPackage
Get-AppxPackage *windowsphone* | Remove-AppxPackage
Get-AppxPackage *photos* | Remove-AppxPackage
Get-AppxPackage *windowsstore* | Remove-AppxPackage
Get-AppxPackage *bingsports* | Remove-AppxPackage
Get-AppxPackage *soundrecorder* | Remove-AppxPackage
Get-AppxPackage *bingweather* | Remove-AppxPackage
Get-AppxPackage *xboxapp* | Remove-AppxPackage
```

---

### حذف OneDrive بالكامل

```cmd
REM في CMD كمسؤول

REM إيقاف OneDrive
taskkill /f /im OneDrive.exe

REM حذف OneDrive (64-bit)
%SystemRoot%\SysWOW64\OneDriveSetup.exe /uninstall

REM حذف OneDrive (32-bit)
%SystemRoot%\System32\OneDriveSetup.exe /uninstall

REM حذف مجلد OneDrive
rd "%UserProfile%\OneDrive" /s /q
rd "%LocalAppData%\Microsoft\OneDrive" /s /q
rd "%ProgramData%\Microsoft OneDrive" /s /q
rd "C:\OneDriveTemp" /s /q

REM حذف OneDrive من File Explorer
reg delete "HKEY_CLASSES_ROOT\CLSID\{018D5C66-4533-4307-9B53-224DE2ED1FE6}" /f
reg delete "HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{018D5C66-4533-4307-9B53-224DE2ED1FE6}" /f
```

---

## تعطيل Cortana

```cmd
REM تعطيل Cortana عبر Registry
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" /v AllowCortana /t REG_DWORD /d 0 /f

REM تعطيل Cortana Voice Activation
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 0 /f
```

---

## تعطيل تكامل Bing Search في Start Menu

```cmd
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search" /v CortanaConsent /t REG_DWORD /d 0 /f
```

---

## تعطيل Windows Copilot

```cmd
REM Windows 11 Copilot disable
reg add "HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\WindowsCopilot" /v TurnOffWindowsCopilot /t REG_DWORD /d 1 /f

REM إخفاء زر Copilot
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowCopilotButton /t REG_DWORD /d 0 /f
```

---

## تعطيل Windows Recall (AI Screenshots)

```cmd
REM تعطيل Recall في Windows 11
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsAI" /v DisableAIDataAnalysis /t REG_DWORD /d 1 /f
```

---

## تعطيل التتبع والخصوصية (Telemetry & Privacy)

### تعطيل كل خدمات التتبع

```cmd
REM تعطيل Telemetry
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f

REM تعطيل Advertising ID
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\AdvertisingInfo" /v Enabled /t REG_DWORD /d 0 /f

REM تعطيل Location Tracking
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location" /v Value /t REG_SZ /d Deny /f

REM تعطيل Activity History
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System" /v EnableActivityFeed /t REG_DWORD /d 0 /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System" /v PublishUserActivities /t REG_DWORD /d 0 /f

REM تعطيل Feedback Notifications
reg add "HKEY_CURRENT_USER\Software\Microsoft\Siuf\Rules" /v NumberOfSIUFInPeriod /t REG_DWORD /d 0 /f
```

---

### تعطيل خدمات التتبع

```cmd
REM DiagTrack (Connected User Experiences and Telemetry)
sc config DiagTrack start= disabled
sc stop DiagTrack

REM dmwappushservice (WAP Push Message Routing Service)
sc config dmwappushservice start= disabled
sc stop dmwappushservice

REM Data Collection Service
sc config DPS start= disabled
sc stop DPS
```

---

## تعطيل Windows Widgets (Windows 11)

```cmd
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Dsh" /v AllowNewsAndInterests /t REG_DWORD /d 0 /f

REM إخفاء Widgets من Taskbar
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarDa /t REG_DWORD /d 0 /f
```

---

## تعطيل Windows Tips & Suggestions

```cmd
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v SubscribedContent-338389Enabled /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v SubscribedContent-338393Enabled /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v SubscribedContent-353694Enabled /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ContentDeliveryManager" /v SubscribedContent-353696Enabled /t REG_DWORD /d 0 /f
```

---

## تعطيل Windows Update Automatic Restart

```cmd
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v NoAutoRebootWithLoggedOnUsers /t REG_DWORD /d 1 /f
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v AUOptions /t REG_DWORD /d 2 /f
```

---

## تعطيل Xbox Game Bar & DVR

```cmd
REM Game Bar
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\GameDVR" /v AppCaptureEnabled /t REG_DWORD /d 0 /f
reg add "HKEY_CURRENT_USER\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 0 /f

REM Xbox Services
sc config XblAuthManager start= disabled
sc config XblGameSave start= disabled
sc config XboxNetApiSvc start= disabled
sc config XboxGipSvc start= disabled
```

---

## تنظيف Taskbar (Windows 11)

```cmd
REM إخفاء Task View
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowTaskViewButton /t REG_DWORD /d 0 /f

REM إخفاء Chat (Teams)
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarMn /t REG_DWORD /d 0 /f

REM إخفاء Search Icon
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f
```

---

## Script شامل للتنفيذ السريع

احفظ هذا في ملف `debloat.cmd` وشغّله كمسؤول:

```cmd
@echo off
echo ==============================================
echo Windows Debloat Script
echo ==============================================
echo.

REM Disable Telemetry
echo [1/5] Disabling Telemetry...
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f >nul 2>&1
sc config DiagTrack start= disabled >nul 2>&1
sc stop DiagTrack >nul 2>&1

REM Disable Cortana
echo [2/5] Disabling Cortana...
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Windows Search" /v AllowCortana /t REG_DWORD /d 0 /f >nul 2>&1

REM Disable Windows Copilot
echo [3/5] Disabling Copilot...
reg add "HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\WindowsCopilot" /v TurnOffWindowsCopilot /t REG_DWORD /d 1 /f >nul 2>&1

REM Remove Bloatware
echo [4/5] Removing Bloatware Apps...
powershell -Command "Get-AppxPackage *3dbuilder* | Remove-AppxPackage" >nul 2>&1
powershell -Command "Get-AppxPackage *windowsalarms* | Remove-AppxPackage" >nul 2>&1
powershell -Command "Get-AppxPackage *zunemusic* | Remove-AppxPackage" >nul 2>&1
powershell -Command "Get-AppxPackage *xboxapp* | Remove-AppxPackage" >nul 2>&1

REM Clean Taskbar
echo [5/5] Cleaning Taskbar...
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarDa /t REG_DWORD /d 0 /f >nul 2>&1
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarMn /t REG_DWORD /d 0 /f >nul 2>&1

echo.
echo ==============================================
echo Done! Please restart your computer.
echo ==============================================
pause
```

---

## ملاحظات مهمة

⚠️ **تحذيرات:**
- بعض التعديلات قد تعطل ميزات تحتاجها
- حذف Microsoft Store سيمنعك من تثبيت بعض التطبيقات
- عمل Restore Point قبل التعديل
- Windows Update قد يعيد بعض الإعدادات

✅ **فوائد:**
- تحسين ملحوظ في الأداء
- زيادة الخصوصية
- توفير مساحة القرص
- تقليل استهلاك RAM

---

*تم الإضافة بتاريخ: 2026-01-08*
