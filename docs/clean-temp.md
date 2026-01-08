# تنظيف الملفات المؤقتة

## عبر Disk Cleanup

1. اضغط `Win + R` واكتب `cleanmgr`
2. اختر البارتيشن المراد تنظيفه
3. اختر الملفات المراد حذفها
4. اضغط OK

## عبر PowerShell

```powershell
Remove-Item "$env:TEMP\*" -Force -Recurse
Remove-Item "C:\Windows\Temp\*" -Force -Recurse -ErrorAction SilentlyContinue
```