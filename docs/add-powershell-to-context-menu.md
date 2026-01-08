# إضافة PowerShell كمسؤول في قائمة الماوس اليمين

## الهدف
إضافة خيار "PowerShell Admin Here" في قائمة كليك اليمين على المجلدات والدرايفات والخلفية.

## الحل

### 1. إضافة PowerShell Admin

افتح **PowerShell** واكتب الأمر التالي:

```powershell
$MenuKeyName = "PSAdminHere"
$MenuText    = "PowerShell Admin Here"
$Icon        = "$env:WINDIR\System32\WindowsPowerShell\v1.0\powershell.exe"

# للمجلدات (كليك يمين على فولدر)
$dir1 = "HKCU:\Software\Classes\Directory\shell\$MenuKeyName"
New-Item -Path $dir1 -Force | Out-Null
New-Item -Path "$dir1\command" -Force | Out-Null
Set-ItemProperty -Path $dir1 -Name '(Default)' -Value $MenuText -Force
Set-ItemProperty -Path $dir1 -Name 'Icon' -Value $Icon -Force
Set-ItemProperty -Path "$dir1\command" -Name '(Default)' -Value 'powershell.exe -NoProfile -Command "Start-Process powershell.exe -Verb RunAs -WorkingDirectory ''%V'' -ArgumentList ''-NoExit'',''-NoProfile'',''-Command'',''Set-Location -LiteralPath \"\"%V\"\"''"' -Force

# للخلفية (كليك يمين في مساحة فارغة داخل فولدر)
$dir2 = "HKCU:\Software\Classes\Directory\Background\shell\$MenuKeyName"
New-Item -Path $dir2 -Force | Out-Null
New-Item -Path "$dir2\command" -Force | Out-Null
Set-ItemProperty -Path $dir2 -Name '(Default)' -Value $MenuText -Force
Set-ItemProperty -Path $dir2 -Name 'Icon' -Value $Icon -Force
Set-ItemProperty -Path "$dir2\command" -Name '(Default)' -Value 'powershell.exe -NoProfile -Command "Start-Process powershell.exe -Verb RunAs -WorkingDirectory ''%V'' -ArgumentList ''-NoExit'',''-NoProfile'',''-Command'',''Set-Location -LiteralPath \"\"%V\"\"''"' -Force

# للدرايفات (كليك يمين على C:, D:, إلخ)
$dir3 = "HKCU:\Software\Classes\Drive\shell\$MenuKeyName"
New-Item -Path $dir3 -Force | Out-Null
New-Item -Path "$dir3\command" -Force | Out-Null
Set-ItemProperty -Path $dir3 -Name '(Default)' -Value $MenuText -Force
Set-ItemProperty -Path $dir3 -Name 'Icon' -Value $Icon -Force
Set-ItemProperty -Path "$dir3\command" -Name '(Default)' -Value 'powershell.exe -NoProfile -Command "Start-Process powershell.exe -Verb RunAs -WorkingDirectory ''%V'' -ArgumentList ''-NoExit'',''-NoProfile'',''-Command'',''Set-Location -LiteralPath \"\"%V\"\"''"' -Force

Write-Host "✅ تم! افتح Explorer واضغط F5" -ForegroundColor Green
```

---

## إزالة PowerShell من القائمة

إذا أردت إزالة أي PowerShell من قائمة كليك اليمين:

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

---

*تم الإضافة بتاريخ: 2026-01-08*
