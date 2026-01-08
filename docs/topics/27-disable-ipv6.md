# تعطيل IPv6

## الوصف
تعطيل بروتوكول IPv6 لتسريع الإنترنت.

## الطريقة 1: Network Settings

```
1. اضغط Win + I
2. روح: Network & Internet > Advanced network options
3. اضغط على شبكتك
4. اضغط "Edit"
5. عطل IPv6
```

## الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
# تعطيل IPv6 على جميع الواجهات
Disable-NetAdapterBinding -Name "*" -ComponentID ms_tcpip6

# أو على واجهة محددة
Disable-NetAdapterBinding -Name "Ethernet" -ComponentID ms_tcpip6
```

## الطريقة 3: Registry

```powershell
# تعطيل IPv6
Reg add "HKLM\SYSTEM\CurrentControlSet\Services\TCPIP6\Parameters" /v DisabledComponents /t REG_DWORD /d 255 /f
```

## الطريقة 4: Adapter Properties

```
1. اضغط Win وابحث عن "Network Connections"
2. Right Click على الشبكة
3. اختر "Properties"
4. الغي اختيار "Internet Protocol Version 6 (TCP/IPv6)"
5. اضغط "OK"
```

## التحقق من التعطيل

```powershell
ipconfig /all
# إذا لم تظهر IPv6 addresses فهو معطل
```

## الإعادة - تفعيل IPv6

```powershell
Enable-NetAdapterBinding -Name "*" -ComponentID ms_tcpip6

# أو من Registry
Reg add "HKLM\SYSTEM\CurrentControlSet\Services\TCPIP6\Parameters" /v DisabledComponents /t REG_DWORD /d 0 /f
```

## ملاحظات
⚠️ بعض المواقع قد تحتاج IPv6! تأكد قبل التعطيل.
