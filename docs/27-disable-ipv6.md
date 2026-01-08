# تعطيل IPv6

## عبر PowerShell
```powershell
Disable-NetAdapterBinding -Name "*" -ComponentID ms_tcpip6
```

## عبر GUI
1. Control Panel → Network and Sharing
2. Change adapter settings
3. كليك يمين → Properties
4. أزل علامة **Internet Protocol Version 6**

## ملاحظات
- يقلل استهلاك الموارد
- معظم المواقع مازالت IPv4