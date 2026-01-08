# تفعيل Long Path Support

## عبر PowerShell (Admin)

```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name LongPathsEnabled -Value 1 -PropertyType DWORD -Force
```

## عبر Group Policy (Windows Pro+)

1. اضغط `Win + R` واكتب `gpedit.msc`
2. اذهب إلى: Computer Configuration → Administrative Templates → System → Filesystem
3. فعّل **Enable Win32 long paths**