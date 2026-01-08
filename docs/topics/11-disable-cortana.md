# تعطيل Cortana (مساعد مايكروسوفت)

## الوصف
إيقاف مساعد Cortana والبحث المتقدم.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: Privacy & Security > App permissions
3. اختر "Microphone" وأيقفه
4. اختر "Camera" وأيقفه
5. روح الخلف: Voice activation وأيقفه
```

## الطريقة 2: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Search
3. ابحث عن: "Allow Cortana"
4. اختر "Disabled"
```

## الطريقة 3: Registry

```powershell
# تعطيل Cortana
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v CortanaEnabled /t REG_DWORD /d 0 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v CanCortanaBeEnabled /t REG_DWORD /d 0 /f
Reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search" /v AllowCortana /t REG_DWORD /d 0 /f
```

## الطريقة 4: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Cortana
3. عطل كل المهام
```

## الإعادة

```powershell
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v CortanaEnabled /t REG_DWORD /d 1 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v CanCortanaBeEnabled /t REG_DWORD /d 1 /f
```
