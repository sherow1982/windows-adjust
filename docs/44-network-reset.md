# إعادة تعيين الشبكة

## عبر Settings
1. Settings → Network & Internet → Status
2. Network reset
3. Reset now

## عبر PowerShell
```powershell
ipconfig /release
ipconfig /renew
ipconfig /flushdns
netsh winsock reset
netsh int ip reset
```

## ملاحظات
- يحل معظم مشاكل الإنترنت
- يحتاج إعادة تشغيل