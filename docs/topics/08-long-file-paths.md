# تفعيل المسارات الطويلة (Long Path)

## الوصف
السماح بمسارات أطول من 260 حرف للملفات والمجلدات.

## الطريقة 1: Group Policy (Windows 10 1607+)

```
1. اضغط Win + R وكتب gpedit.msc
2. روح: Computer Configuration > Administrative Templates > System > Filesystem
3. ابحث عن: "Enable Win32 long paths"
4. اختر "Enabled"
5. اضغط OK
```

## الطريقة 2: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\FileSystem" /v LongPathsEnabled /t REG_DWORD /d 1 /f
```

## التحقق

```powershell
# اختبر المسارات الطويلة
$path = "C:\" + ("A" * 300) # 300 حرف
New-Item -ItemType Directory -Path $path -Force
```

## الإعادة

```powershell
Reg add "HKLM\SYSTEM\CurrentControlSet\Control\FileSystem" /v LongPathsEnabled /t REG_DWORD /d 0 /f
```

## ملاحظات
- بعض البرامج القديمة قد لا تعمل مع المسارات الطويلة
- مفيد للمطورين والملفات المتقدمة
