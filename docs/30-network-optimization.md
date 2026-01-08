# تحسين الشبكة

## تعطيل Auto-Tuning
```powershell
netsh int tcp set global autotuninglevel=disabled
```

## تعطيل Network Throttling
```powershell
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" -Name "NetworkThrottlingIndex" -Value 0xffffffff
```

## تحسين TCP
```powershell
netsh int tcp set global chimney=enabled
netsh int tcp set global dca=enabled
netsh int tcp set global netdma=enabled
```

## ملاحظات
- يحسن سرعة الإنترنت
- يقلل Ping