# تفعيل Remote Desktop (RDP)

## الوصف
السماح بالوصول عن بعد لجهازك من أجهزة أخرى.

## الطريقة 1: Settings (سهلة)

```
1. اضغط Win + I لفتح Settings
2. روح: System > Remote Desktop
3. Toggle "Enable Remote Desktop" إلى ON
4. اضغط "Confirm"
```

## الطريقة 2: PowerShell

```powershell
# تفعيل RDP
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -Value 0

# تفعيل Firewall للـ RDP
Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
```

## الطريقة 3: Group Policy

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections
3. ابحث عن: "Allow users to connect remotely using Remote Desktop Services"
4. اختر "Enabled"
```

## الاتصال من جهاز آخر

```
1. اضغط Win + R وكتب mstsc
2. أدخل IP address أو اسم الحاسوب
3. اضغط Connect
```

## الإيقاف

```powershell
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -Value 1
Disable-NetFirewallRule -DisplayGroup "Remote Desktop"
```
