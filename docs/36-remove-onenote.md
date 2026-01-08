# حذف Microsoft OneNote

## عبر PowerShell
```powershell
Get-AppxPackage *OneNote* | Remove-AppxPackage
```

## عبر Settings
1. Settings → Apps → Apps & features
2. ابحث عن OneNote
3. Uninstall

## ملاحظات
- يحرر مساحة
- لا يؤثر على Office