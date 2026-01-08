# تعطيل المؤثرات البصرية

## عبر GUI
1. اضغط Win + R واكتب `sysdm.cpl`
2. Advanced → Performance Settings
3. اختر **Adjust for best performance**

## عبر Registry
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" -Name "VisualFXSetting" -Value 2
```

## ملاحظات
- يسرع النظام بشكل ملحوظ
- سيبدو الويندوز قديم شوية
- للأجهزة الضعيفة مهم جداً