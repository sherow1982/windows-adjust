# تحسين SSD

## تفعيل TRIM
```powershell
fsutil behavior set DisableDeleteNotify 0
```

## تعطيل Defragmentation
```powershell
Schtasks /Change /TN "\Microsoft\Windows\Defrag\ScheduledDefrag" /Disable
```

## تعطيل Indexing
```powershell
Get-Service WSearch | Stop-Service -Force
Get-Service WSearch | Set-Service -StartupType Disabled
```

## ملاحظات
- TRIM مهم جداً للـ SSD
- Defrag يضر الـ SSD بشكل كبير
- يطيل عمر الـ SSD