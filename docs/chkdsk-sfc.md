# فحص وإصلاح النظام

## فحص القرص (CHKDSK)

```powershell
chkdsk C: /F /R
```

## فحص ملفات النظام (SFC)

```powershell
sfc /scannow
sfc /restorehealth
```

## تشغيلهما معاً

```powershell
Dism.exe /online /Cleanup-Image /RestoreHealth
```