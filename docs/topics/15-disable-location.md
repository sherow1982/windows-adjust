# تعطيل Location Tracking

## الوصف
إيقاف تتبع الموقع الجغرافي لجهازك.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: Privacy & Security > General
3. عطل "Let websites provide locally relevant content"
4. روح: Privacy & Security > Location
5. عطل "Location services"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل Location
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location" /v Value /t REG_SZ /d "Deny" /f

# تعطيل GPS
Reg add "HKLM\SYSTEM\CurrentControlSet\Services\lfsvc\Service\Configuration" /v Status /t REG_DWORD /d 0 /f
```

## الطريقة 3: Services

```powershell
# إيقاف خدمة الموقع
Stop-Service -Name lfsvc -Force
Set-Service -Name lfsvc -StartupType Disabled
```

## الطريقة 4: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Location
3. عطل "Location Notifications"
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location" /v Value /t REG_SZ /d "Allow" /f
Set-Service -Name lfsvc -StartupType Automatic
Start-Service -Name lfsvc
```
