# تفعيل وضع الإله (God Mode)

## الوصف
الدخول لصندوق تحكم يحتوي على كل إعدادات الويندوز في مكان واحد.

## الطريقة 1: مجلد سريع (الأسهل)

```
1. اضغط Win + D للذهاب لسطح المكتب
2. اضغط Ctrl + Shift + N لإنشاء مجلد جديد
3. أعطه الاسم: {ED7BA470-8E54-465E-825C-99712043E01C}
4. اضغط Enter
5. سيتحول المجلد لأيقونة تحكم خاصة
6. افتحه للدخول للوضع الإله
```

## الطريقة 2: Registry

```powershell
New-Item -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\CommandStore\shell\GodMode" -Force | Out-Null
New-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\CommandStore\shell\GodMode" -Name "(Default)" -Value "{ED7BA470-8E54-465E-825C-99712043E01C}" -PropertyType String -Force | Out-Null
```

## المحتوى
يحتوي على 200+ أداة تحكم:
- Device Manager
- Network Settings
- Sound Settings
- Display Settings
- Power Options
- وأكثر...

## الحذف
احذف المجلد عادي أو:

```powershell
Reg delete "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\CommandStore\shell\GodMode" /f
```
