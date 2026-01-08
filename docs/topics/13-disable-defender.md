# تعطيل Windows Defender

## الوصف
إيقاف برنامج الحماية المدمج بشكل نهائي.

## الطريقة 1: Windows Security

```
1. اضغط Win وابحث عن "Windows Security"
2. اضغط "Virus & threat protection"
3. اضغط "Manage settings"
4. عطل "Real-time protection"
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v "Windows Defender" /t REG_SZ /d "" /f
Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f
Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection" /v DisableRealtimeMonitoring /t REG_DWORD /d 1 /f
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus
3. اضغط "Turn off Windows Defender Antivirus"
4. اختر "Enabled"
```

## الطريقة 4: Services

```powershell
# إيقاف الخدمات
Stop-Service -Name WinDefend -Force
Set-Service -Name WinDefend -StartupType Disabled
Stop-Service -Name SecurityHealthService -Force
Set-Service -Name SecurityHealthService -StartupType Disabled
```

## الإعادة

```powershell
Set-Service -Name WinDefend -StartupType Automatic
Start-Service -Name WinDefend
Set-Service -Name SecurityHealthService -StartupType Automatic
Start-Service -Name SecurityHealthService
```

## تحذير
⚠️ خطر جداً! استخدم برنامج حماية بديل موثوق.
