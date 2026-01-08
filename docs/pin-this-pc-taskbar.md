# تثبيت أيقونة This PC على شريط المهام (Pin This PC to Taskbar)

## الوصف
سكريبت PowerShell لإنشاء اختصار لـ "This PC" على سطح المكتب ومحاولة تثبيته تلقائياً على شريط المهام.

## الكود (PowerShell)

قم بتشغيل PowerShell كمسؤول (Administrator) ونفض الأمر التالي:

```powershell
$Desktop = [Environment]::GetFolderPath('Desktop'); $ShortcutPath = "$Desktop\This PC.lnk"; $WshShell = New-Object -ComObject WScript.Shell; $Shortcut = $WshShell.CreateShortcut($ShortcutPath); $Shortcut.TargetPath = 'explorer.exe'; $Shortcut.Arguments = 'shell:MyComputerFolder'; $Shortcut.IconLocation = '%SystemRoot%\System32\imageres.dll,-107'; $Shortcut.Save(); Start-Sleep 2; $shell = New-Object -ComObject Shell.Application; $Pinned = $shell.Namespace("$env:APPDATA\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar"); $Item = $Pinned.ParseName((Split-Path $ShortcutPath -Leaf)); if ($Item) { $Item.InvokeVerb('taskbarpin') } else { Write-Host 'اختصار موجود بس مش مثبت، ثبت يدوي' }; Write-Host 'تم الإنشاء والتثبيت!'
```

## الخطوات الإضافية

بعد تشغيل السكريبت:

1. ستظهر أيقونة **This PC** على سطح المكتب
2. انقر عليها بزر الماوس الأيمن وغير الأيقونة لأي أيقونة تحبها (اختياري)
3. انقر كليك يمين مرة أخرى واختر **Pin to taskbar** (إذا لم يتم التثبيت تلقائياً)

## ملاحظات
- السكريبت يحاول التثبيت تلقائياً لكن قد يتطلب تثبيت يدوي
- يمكن تخصيص الأيقونة بعد إنشائها
- يعمل مع ويندوز 10 و 11

---

*تم الإضافة بتاريخ: 2026-01-08*
