# إظهار الملفات المخفية

## عبر File Explorer

1. افتح File Explorer
2. اضغط على **View** tab
3. فعّل **Hidden items**
4. فعّل **File name extensions**

## عبر Registry

```powershell
Set-ItemProperty -Path 'HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced' -name Hidden -Value 1
Set-ItemProperty -Path 'HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced' -name HideFileExt -Value 0
```