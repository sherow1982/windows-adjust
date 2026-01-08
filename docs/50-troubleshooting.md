# استكشاف الأخطاء

## المشكلة: ما يعمل Restore Point
```powershell
Enable-ComputerRestore -Drive "C:\"
Checkpoint-Computer -Description "نقطة استعادة" -RestorePointType "MODIFY_SETTINGS"
```

## المشكلة: Registry ما يشتغل
استخدم Restore Point أو:
```powershell
reg export HKLM backup.reg /y
```

## المشكلة: PowerShell ما يشتغل
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force
```

## ملاحظات
- دايماً عمل Backup
- اقرا الآمر قبل التنفيذ