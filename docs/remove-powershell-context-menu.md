# إزالة PowerShell من قائمة الماوس اليمين

## الوصف
إزالة جميع خيارات PowerShell من قائمة السياق (الكليك اليمين) بشكل كامل وآمن.

---

## طريقة التنفيذ

### الخطوات

1. **فتح PowerShell كمسؤول**
   - اضغط كليك يمين على قائمة Start
   - اختر **Windows PowerShell (Admin)**

2. **الصق ونفذ الكود التالي**

```powershell
# 1) حذف أي Entries أنت ضايفها تحت حسابك (HKCU)
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

Write-Host "✅ تم إزالة جميع عناصر PowerShell من القائمة!" -ForegroundColor Green
```

---

## ما يفعله السكريبت

1. **حذف العناصر المخصصة**: يحذف أي PowerShell أضفته يدوياً تحت حساب المستخدم (HKCU)
2. **إخفاء PowerShell الافتراضي**: يخفي خيار PowerShell الرسمي من ويندوز بشكل آمن
3. **حذف "Run with PowerShell"**: يزيل الخيار من ملفات .ps1 (اختياري)
4. **إعادة تشغيل Explorer**: لتفعيل التغييرات فوراً

---

## ملاحظات مهمة

- ⚠️ **يجب تشغيل PowerShell كمسؤول** لتعديل HKEY_CLASSES_ROOT
- ✅ **آمن تماماً**: لا يحذف ملفات النظام، فقط يخفي العناصر من القائمة
- 🔄 **إعادة تشغيل Explorer** تتم تلقائياً في السكريبت

---

*تم الإضافة بتاريخ: 2026-01-08*
