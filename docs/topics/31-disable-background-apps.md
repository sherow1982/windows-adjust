# تعطيل تطبيقات الخلفية

## الوصف
إيقاف التطبيقات التي تعمل في الخلفية.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: System > Battery saver
3. تحت "Background apps" عطل ما تريد
4. أو روح: Apps > Running apps
5. اختر التطبيق واضغط "Terminate"
```

## الطريقة 2: Task Manager

```
1. اضغط Ctrl + Shift + Esc
2. اذهب لـ "Startup" tab
3. Right Click على البرنامج
4. اختر "Disable"
```

## الطريقة 3: Registry

```powershell
# PowerShell (Run as Admin)
# تعطيل التطبيقات من الخلفية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications" /v GlobalUserDisabled /t REG_DWORD /d 1 /f
```

## تعطيل برامج محددة

```powershell
# تعطيل Skype في الخلفية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications\Microsoft.SkypeApp_kzf8qxf38zg5c" /v Disabled /t REG_DWORD /d 1 /f

# تعطيل Photos
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications\Microsoft.Windows.Photos_8wekyb3d8bbwe" /v Disabled /t REG_DWORD /d 1 /f
```

## Task Manager - تعطيل البرامج

```
1. Ctrl + Shift + Esc
2. تحت كل تطبيق:
   - Windows Terminal
   - OneDrive
   - Microsoft Teams
3. Right Click > Disable
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications" /v GlobalUserDisabled /t REG_DWORD /d 0 /f
```

## ملاحظات
- بعض التطبيقات مهمة! لا تعطل كلها
- Windows Update و Windows Defender يجب أن تبقى
