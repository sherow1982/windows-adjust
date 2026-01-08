# حذف Microsoft Edge

## عبر PowerShell (Admin)
```powershell
cd "C:\Program Files (x86)\Microsoft\Edge\Application\*\Installer"
.\setup.exe --uninstall --system-level --verbose-logging --force-uninstall
```

## ملاحظات
⚠️ **تحذير**: قد يتم إعادة تثبيته عبر Windows Update
- لا ينصح به إلا لضرورة