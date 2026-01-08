# تفعيل وضع التوافق للبرامج القديمة

## الوصف
تشغيل البرامج القديمة على إصدارات جديدة من الويندوز.

## الطريقة 1: Program Compatibility (الأسهل)

```
1. انقر بـ Right Click على ملف .exe
2. اختر "Properties"
3. اذهب لـ "Compatibility" tab
4. اختر الويندوز القديم (Windows XP, 7, 8, إلخ)
5. اضغط "Apply" ثم "OK"
```

## الطريقة 2: Compatibility Troubleshooter

```
1. Right Click على البرنامج
2. اختر "Troubleshoot compatibility"
3. اختر "Troubleshoot program"
4. Windows سيجرب إعدادات مختلفة تلقائياً
5. جرب البرنامج وأخبر Windows إذا استغل أم لا
```

## الطريقة 3: Registry

```powershell
# مثال: تشغيل برنامج برو Windows XP
$path = "HKCU:\Software\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers"
New-Item -Path $path -Force | Out-Null
New-ItemProperty -Path $path -Name "C:\Program Files\Program.exe" -Value "WINXPSP3" -PropertyType String -Force | Out-Null
```

## الإعدادات المتقدمة

```
في Compatibility tab:
- Run this program in compatibility mode for: Windows XP/7/8/etc
- Run in 256 colors
- Run in 640×480 screen resolution
- Disable fullscreen optimizations
- Run this program as an administrator
```

## الحذف

احذف من:
```
HKCU\Software\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers
```
