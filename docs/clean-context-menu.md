# تنظيف قائمة كليك يمين من PowerShell

هذا السكريبت يقوم بإزالة جميع اختصارات PowerShell المضافة يدوياً وإخفاء الاختصارات الافتراضية من قائمة الكليك يمين.

## الكود (PowerShell)

شغل PowerShell كمسؤول (Run as Administrator) ونفذ الأمر التالي:

```powershell
# 1) احذف أي Entries أنت ضايفها تحت حسابك (HKCU)
$hkcuShells = @(
  'HKCU:\Software\Classes\Directory\shell',
  'HKCU:\Software\Classes\Directory\Background\shell',
  'HKCU:\Software\Classes\Drive\shell'
)
foreach($p in $hkcuShells){
  if(Test-Path $p){
    Get-ChildItem $p -ErrorAction SilentlyContinue |
      Where-Object { $_.PSChildName -match 'powershell|pwsh|psadmin' } |
      Remove-Item -Recurse -Force -ErrorAction SilentlyContinue
  }
}

# 2) اخفِ PowerShell الافتراضي بتاع ويندوز (بدون ما تكسر النظام)
# الفكرة: إضافة ProgrammaticAccessOnly لتختفي من القائمة
$hkcrTargets = @(
  'Registry::HKEY_CLASSES_ROOT\Directory\shell\Powershell',
  'Registry::HKEY_CLASSES_ROOT\Directory\Background\shell\Powershell',
  'Registry::HKEY_CLASSES_ROOT\Drive\shell\Powershell',
  'Registry::HKEY_CLASSES_ROOT\Drive\Background\shell\Powershell'
)
foreach($t in $hkcrTargets){
  if(Test-Path $t){
    New-ItemProperty -Path $t -Name 'ProgrammaticAccessOnly' -PropertyType String -Value '' -Force -ErrorAction SilentlyContinue | Out-Null
  }
}

# 3) (اختياري) شيل "Run with PowerShell" من كليك يمين على ملفات .ps1
Remove-Item 'Registry::HKEY_CLASSES_ROOT\Microsoft.PowerShellScript.1\Shell\Run with PowerShell' -Recurse -Force -ErrorAction SilentlyContinue

# 4) ريستارت Explorer عشان التغييرات تظهر فوراً
Stop-Process -Name explorer -Force
Start-Process explorer
```

## ملاحظات

- السكريبت يحذف الإضافات من حسابك الشخصي (HKCU)
- يخفي اختصارات PowerShell الافتراضية دون حذفها
- يعيد تشغيل Explorer تلقائياً لتطبيق التغييرات
- آمن ولا يؤثر على ملفات النظام

---

*تم الإضافة بتاريخ: 2026-01-08*
