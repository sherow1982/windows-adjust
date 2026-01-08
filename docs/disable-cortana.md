# تعطيل Cortana

## عبر PowerShell (Admin)

```powershell
Get-AppxPackage Microsoft.Windows.Cortana | Remove-AppxPackage
```

## عبر Group Policy

1. اضغط `Win + R` واكتب `gpedit.msc`
2. اذهب إلى: Computer Configuration → Administrative Templates → Windows Components → Search
3. فعّل **Allow Cortana**: اختر **Disabled**