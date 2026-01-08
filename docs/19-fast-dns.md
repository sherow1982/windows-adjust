# تغيير DNS لتسريع الإنترنت

## Google DNS

### عبر PowerShell
```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses ("8.8.8.8","8.8.4.4")
```

## Cloudflare DNS (1.1.1.1)
```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses ("1.1.1.1","1.0.0.1")
```

## عبر GUI
1. Control Panel → Network and Sharing Center
2. Change adapter settings
3. كليك يمين على الاتصال → Properties
4. IPv4 → Properties
5. Use the following DNS
6. أدخل 8.8.8.8 و 8.8.4.4

## ملاحظات
- غير InterfaceAlias لاسم شبكتك (Ethernet / Wi-Fi)