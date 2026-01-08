# تنظيف Cache النظام

## الوصف
حذف ملفات الـ Cache المتراكمة.

## الطريقة 1: PowerShell

```powershell
# PowerShell (Run as Admin)
# حذف DNS Cache
Clear-DnsClientCache

# حذف System Cache
Clear-Item "$env:temp\*" -Recurse -Force -ErrorAction SilentlyContinue

# حذف Windows Update Cache
Remove-Item "C:\Windows\SoftwareDistribution\Download\*" -Recurse -Force
```

## الطريقة 2: Disk Cleanup

```
1. اضغط Win وابحث عن "Disk Cleanup"
2. ضع checkmark على:
   - Temporary Internet Files
   - Thumbnails
   - Windows Update Cleanup
3. اضغط "Delete Files"
```

## حذف Application Cache

```powershell
# Chrome Cache
Remove-Item "$env:LocalAppData\Google\Chrome\User Data\Default\Cache\*" -Recurse -Force

# Firefox Cache
Remove-Item "$env:LocalAppData\Mozilla\Firefox\Profiles\*\cache2\*" -Recurse -Force

# Microsoft Store Cache
Remove-Item "$env:LocalAppData\Packages\Microsoft.WindowsStore_*\LocalState\*" -Recurse -Force
```

## تنظيف Windows Cache

```powershell
# حذف Prefetch Cache
Remove-Item "C:\Windows\Prefetch\*" -Force -ErrorAction SilentlyContinue

# حذف .NET Cache
Remove-Item "$env:LocalAppData\Microsoft\.NET Framework\NGenAssemblies\*" -Recurse -Force
```

## الطريقة 3: Scripts للتنظيف الشامل

```powershell
# Script شامل
@(
    "$env:temp",
    "$env:windir\temp",
    "$env:LocalAppData\Temp"
) | ForEach-Object {
    Remove-Item "$_\*" -Recurse -Force -ErrorAction SilentlyContinue
}
```

## ملاحظات
- النظام قد يعيد إنشاء بعض الـ Cache
- آمن جداً للتنظيف المنتظم
