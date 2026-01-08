# إعادة تعيين الشبكة (Network Reset)

## الوصف
حل مشاكل الإنترنت بإعادة تعيين الشبكة.

## الطريقة 1: Settings

```
1. اضغط Win + I
2. روح: System > Troubleshooting
3. اضغط "Other troubleshooters"
4. ابحث عن "Network troubleshooter"
5. اضغط "Run"
```

## الطريقة 2: Network Reset

```
1. اضغط Win + I
2. روح: System > Troubleshooting
3. اضغط "Other troubleshooters"
4. اضغط "Network reset"
5. اضغط "Run"
```

## الطريقة 3: PowerShell

```powershell
# PowerShell (Run as Admin)
# إعادة تعيين Network Stack
ipconfig /release
ipconfig /renew
ipconfig /flushdns

# إعادة تعيين Winsock Catalog
netsh winsock reset catalog
netsh winsock reset resetall

# إعادة تعيين TCP/IP
netsh int ip reset resetall
```

## الطريقة 4: الطريقة الكاملة

```powershell
# 1. إغلاق الاتصالات
ipconfig /release
Start-Sleep -Seconds 2

# 2. إعادة الاتصال
ipconfig /renew

# 3. مسح DNS Cache
ipconfig /flushdns
Clear-DnsClientCache

# 4. إعادة تعيين Winsock
netsh winsock reset catalog
netsh int tcp reset all

# 5. إعادة تشغيل الشبكة
Restart-Computer -Force
```

## اختبار الاتصال

```powershell
# بعد الإعادة
Test-NetConnection -ComputerName 8.8.8.8 -Port 53
Test-NetConnection -ComputerName google.com
```

## ملاحظات
- قد تفقد الاتصال لبعض الثواني
- إعادة التشغيل قد تكون ضرورية
- تأكد من فصل الـ VPN أولاً
