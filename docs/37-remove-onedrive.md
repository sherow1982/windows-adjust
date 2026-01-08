# حذف OneDrive

## عبر PowerShell
```powershell
taskkill /f /im OneDrive.exe
%SystemRoot%\System32\OneDriveSetup.exe /uninstall
```

## حذف بقايا OneDrive
```powershell
Remove-Item "$env:USERPROFILE\OneDrive" -Force -Recurse
Remove-Item "C:\OneDriveTemp" -Force -Recurse -ErrorAction SilentlyContinue
```

## ملاحظات
- قد يعود بعد Windows Update