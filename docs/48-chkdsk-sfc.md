# فحص وإصلاح القرص

## CHKDSK
```powershell
chkdsk C: /F /R /X
```

## SFC (System File Checker)
```powershell
sfc /scannow
```

## DISM
```powershell
Dism /Online /Cleanup-Image /RestoreHealth
```

## ملاحظات
- CHKDSK يحتاج إعادة تشغيل
- SFC يأخذ وقت طويل
- DISM قبل SFC