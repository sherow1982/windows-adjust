# تعطيل Windows Firewall

## عبر PowerShell (Admin)

```powershell
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

## عبر GUI

1. اضغط `Win + R` واكتب `firewall.cpl`
2. اختر **Turn Windows Defender Firewall on or off**
3. اختر **Off** لجميع الخيارات
4. اضغط OK

⚠️ **تحذير**: تأكد من تثبيت برنامج حماية آخر!