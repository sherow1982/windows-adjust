# تعيين DNS سريع (Cloudflare/Google)

## الوصف
استبدال DNS الافتراضي بـ Cloudflare أو Google لسرعة أفضل.

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: Network & Internet > WiFi (أو Ethernet)
3. اضغط على شبكتك
4. اضغط "Edit" بجانب DNS server assignment
5. اختر "Manual"
6. أدخل DNS addresses
```

## الطريقة 2: Control Panel

```
1. اضغط Win وابحث عن "Network Connections"
2. Right Click على الشبكة
3. اختر "Properties"
4. اختر "Internet Protocol Version 4 (TCP/IPv4)"
5. اضغط "Properties"
6. اختر "Use the following DNS server addresses"
7. أدخل:
   - Preferred DNS: 8.8.8.8 (Google)
   - Alternate DNS: 8.8.4.4 (Google)
```

## الطريقة 3: PowerShell

```powershell
# PowerShell (Run as Admin)
# استبدال DNS بـ Cloudflare
Set-DnsClientServerAddress -InterfaceIndex (Get-NetAdapter | Where-Object {$_.Status -eq "Up"}).InterfaceIndex -ServerAddresses ("1.1.1.1", "1.0.0.1")

# أو Google DNS
Set-DnsClientServerAddress -InterfaceIndex (Get-NetAdapter | Where-Object {$_.Status -eq "Up"}).InterfaceIndex -ServerAddresses ("8.8.8.8", "8.8.4.4")
```

## خيارات DNS المختلفة

| الخدمة | DNS أساسي | DNS ثانوي |
|--------|---------|----------|
| Google | 8.8.8.8 | 8.8.4.4 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 |
| OpenDNS | 208.67.222.222 | 208.67.220.220 |
| Quad9 | 9.9.9.9 | 149.112.112.112 |

## اختبار السرعة

```powershell
# اختبر DNS الجديد
Resolve-DnsName google.com

# قياس وقت الاستجابة
Measure-Command { Resolve-DnsName google.com }
```

## الإعادة - استخدام DHCP

```powershell
Set-DnsClientServerAddress -InterfaceIndex (Get-NetAdapter | Where-Object {$_.Status -eq "Up"}).InterfaceIndex -ResetServerAddresses
```
