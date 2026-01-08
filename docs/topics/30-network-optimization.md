# تحسين سرعة الشبكة

## الوصف
تحسين معايير TCP وسرعة نقل البيانات.

## الطريقة 1: Registry Tweaks

```powershell
# PowerShell (Run as Admin)
# زيادة TCP Window Size
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v TCPWindowSize /t REG_DWORD /d 65535 /f

# تفعيل Nagle's Algorithm Disable
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" /v DisableNagle /t REG_DWORD /d 1 /f

# زيادة MTU
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" /v MTUSize /t REG_DWORD /d 1500 /f
```

## الطريقة 2: NetSh Commands

```powershell
# تحسين TCP
netsh int tcp set global autotuninglevel=normal
netsh int tcp set global ecn=enabled
netsh int tcp set global timestamps=enabled
netsh int tcp set global chimney=enabled
netsh int tcp set global dca=enabled
netsh int tcp set global netdma=enabled
```

## الطريقة 3: QoS Disable

```powershell
# تعطيل QoS (Quality of Service)
Reg add "HKCU\Software\Policies\Microsoft\Windows\Psched" /v NonBestEffortLimit /t REG_DWORD /d 0 /f
```

## الطريقة 4: DNS Optimization

```powershell
# تحسين DNS Caching
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v DnsCacheSize /t REG_DWORD /d 65536 /f

# تحسين DNS Timeout
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v DnsTimeout /t REG_DWORD /d 5000 /f
```

## اختبار السرعة

```powershell
# اختبر سرعة الشبكة
Test-NetConnection -ComputerName google.com -Port 443

# اختبر Latency
Test-NetConnection -ComputerName 8.8.8.8 -TraceRoute
```

## الإعادة

```powershell
netsh int tcp set global autotuninglevel=restricted
netsh int tcp set global ecn=disabled
```

## ملاحظات
- النتائج تعتمد على جودة الاتصال
- تأكد من DSL/Router جيد
