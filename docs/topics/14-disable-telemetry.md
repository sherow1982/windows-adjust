# تعطيل Telemetry (جمع البيانات)

## الوصف
منع مايكروسوفت من جمع بيانات الاستخدام والتطبيقات.

## الطريقة 1: Services

```powershell
# PowerShell (Run as Admin) - عطل خدمات جمع البيانات
Stop-Service -Name DiagTrack -Force
Set-Service -Name DiagTrack -StartupType Disabled

Stop-Service -Name dmwappushservice -Force
Set-Service -Name dmwappushservice -StartupType Disabled

Stop-Service -Name TelemetryService -Force
Set-Service -Name TelemetryService -StartupType Disabled
```

## الطريقة 2: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds
3. اختر "Allow Diagnostic Data"
4. اختر "Diagnostic data off"
```

## الطريقة 3: Registry

```powershell
# تعطيل Telemetry
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Privacy" /v TailoredExperiencesWithDiagnosticDataEnabled /t REG_DWORD /d 0 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Diagnostics\DiagTrack" /v IsScheduledTaskEnabled /t REG_DWORD /d 0 /f
```

## الطريقة 4: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Application Experience
3. عطل كل المهام
4. روح: Microsoft > Windows > AutoChk
5. عطل كل المهام
6. روح: Microsoft > Windows > Customer Experience Improvement Program
7. عطل كل المهام
```

## الطريقة 5: Settings

```
1. اضغط Win + I
2. روح: Privacy & Security
3. عطل جميع الخيارات
```
