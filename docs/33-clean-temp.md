# تنظيف الملفات المؤقتة

## عبر PowerShell
```powershell
Remove-Item "$env:TEMP\*" -Force -Recurse -ErrorAction SilentlyContinue
Remove-Item "C:\Windows\Temp\*" -Force -Recurse -ErrorAction SilentlyContinue
Remove-Item "C:\Windows\Prefetch\*" -Force -Recurse -ErrorAction SilentlyContinue
```

## عبر Disk Cleanup
1. Win + R → `cleanmgr`
2. اختر C:
3. حدد كل الخيارات
4. OK

## ملاحظات
- يحرر مساحة كبيرة
- يحسن الأداء