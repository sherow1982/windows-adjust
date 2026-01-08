# تعطيل Windows Backup

## الوصف
إيقاف النسخ الاحتياطية التلقائية.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: System > Backup
3. عطل "Automatically back up my files"
```

## الطريقة 2: Services

```powershell
# PowerShell (Run as Admin)
Stop-Service -Name "Backup" -Force
Set-Service -Name "Backup" -StartupType Disabled
```

## الطريقة 3: Task Scheduler

```
1. اضغط Win + R وكتب taskschd.msc
2. روح: Microsoft > Windows > WindowsBackup
3. عطل كل المهام
```

## الطريقة 4: Registry

```powershell
# تعطيل Backup
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Backup" /v BackupEnabled /t REG_DWORD /d 0 /f
```

## حذف النسخ القديمة

```powershell
# احذف النسخ المحفوظة
Remove-Item "$env:LocalAppData\Microsoft\Windows\Backup\*" -Recurse -Force
```

## الإعادة - إعادة تفعيل

```powershell
Set-Service -Name "Backup" -StartupType Automatic
Start-Service -Name "Backup"
```

## ملاحظات
⚠️ تأكد من عمل نسخ احتياطية يدوية!
- النسخ الاحتياطية مهمة جداً
- استخدم برنامج backup بديل
