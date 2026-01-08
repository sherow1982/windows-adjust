# مسح Cache

## مسح DNS Cache
```powershell
ipconfig /flushdns
```

## مسح Icon Cache
```powershell
ie4uinit.exe -show
```

## مسح Thumbnail Cache
```powershell
Remove-Item "$env:LOCALAPPDATA\Microsoft\Windows\Explorer\thumbcache_*.db" -Force
```

## ملاحظات
- يحل مشاكل كثيرة
- يحسن الأداء