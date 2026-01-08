# تعطيل Game Bar

## الوصف
إيقاف شريط الألعاب الذي يستهلك الموارد.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: Gaming > Game Bar
3. عطل "Open Game Bar using this button on a controller"
4. عطل "Record game clips, screenshots, and broadcast"
5. روح: Gaming > Game Mode
6. فعّل "Game Mode"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل Game Bar
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\GameDVR" /v AppCaptureEnabled /t REG_DWORD /d 0 /f
Reg add "HKCU\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 0 /f
```

## الطريقة 3: Services

```powershell
# تعطيل خدمة Game Bar
Stop-Service -Name XblAuthManager -Force
Set-Service -Name XblAuthManager -StartupType Disabled

Stop-Service -Name XboxNetApiSvc -Force
Set-Service -Name XboxNetApiSvc -StartupType Disabled
```

## الطريقة 4: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Xbox
3. عطل كل المهام
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\GameDVR" /v AppCaptureEnabled /t REG_DWORD /d 1 /f
Reg add "HKCU\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 1 /f

Set-Service -Name XblAuthManager -StartupType Automatic
Start-Service -Name XblAuthManager
```

## ملاحظات
- Game Bar يستهلك RAM و CPU
- تفعيل Game Mode بدلاً منه أفضل
