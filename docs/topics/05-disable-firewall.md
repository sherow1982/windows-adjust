# تعطيل Windows Firewall

## الوصف
أوقف جدار الحماية المدمج في الويندوز.

## الطريقة 1: Windows Defender Firewall Interface

```
1. اضغط Win وابحث عن "Windows Defender Firewall"
2. في الجهة اليسرى: "Turn Windows Defender Firewall on or off"
3. اختر "Turn off Windows Defender Firewall"
4. اضغط OK
```

## الطريقة 2: PowerShell (الأسرع)

```powershell
# PowerShell (Run as Admin) - تعطيل كل الملفات الشخصية
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled $false

# أو لملف معين:
Set-NetFirewallProfile -Profile Private -Enabled $false
```

## الطريقة 3: Registry

```powershell
# تعطيل كل الملفات
Reg add "HKLM\SOFTWARE\Policies\Microsoft\WindowsFirewall\StandardProfile" /v EnableFirewall /t REG_DWORD /d 0 /f
Reg add "HKLM\SOFTWARE\Policies\Microsoft\WindowsFirewall\DomainProfile" /v EnableFirewall /t REG_DWORD /d 0 /f
Reg add "HKLM\SOFTWARE\Policies\Microsoft\WindowsFirewall\PublicProfile" /v EnableFirewall /t REG_DWORD /d 0 /f
```

## الإعادة

```powershell
# تفعيل الـ Firewall مجددا
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled $true
```

## تحذير
⚠️ يترك جهازك عرضة للهجمات! استخدم firewall بديل.
