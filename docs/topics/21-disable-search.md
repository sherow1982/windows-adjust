# تعطيل Windows Search

## الوصف
إيقاف فهرسة الملفات المستمرة والبحث البطيء.

## الطريقة 1: Services

```powershell
# PowerShell (Run as Admin)
Stop-Service -Name WSearch -Force
Set-Service -Name WSearch -StartupType Disabled
```

## الطريقة 2: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > Windows Search
3. عطل كل المهام
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Search
3. ابحث عن: "Do not allow locations on removable drives"
4. اختر "Disabled"
```

## الطريقة 4: Registry

```powershell
# تعطيل Windows Search
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f
```

## تنظيف ملفات الفهرسة

```powershell
# حذف قاعدة بيانات الفهرسة
Reg add "HKLM\SYSTEM\CurrentControlSet\Services\WSearch" /v Start /t REG_DWORD /d 4 /f

# احذف المجلد
Remove-Item -Path "$env:ProgramData\Microsoft\Search\Data" -Recurse -Force
```

## الإعادة

```powershell
Set-Service -Name WSearch -StartupType Automatic
Start-Service -Name WSearch
```

## ملاحظات
⚠️ البحث عن الملفات سيكون بطيء جداً بدون Windows Search!
