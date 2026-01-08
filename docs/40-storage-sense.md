# تفعيل Storage Sense

## عبر Settings
1. Settings → System → Storage
2. فعّل **Storage Sense**
3. Configure Storage Sense

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\StorageSense\Parameters\StoragePolicy" -Name "01" -Value 1
```

## ملاحظات
- يحذف الملفات المؤقتة تلقائياً
- يحرر مساحة