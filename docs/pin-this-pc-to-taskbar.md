# تثبيت This PC (الكمبيوتر) على شريط المهام

## الوصف
إنشاء اختصار "This PC" وتثبيته على Taskbar بشكل أوتوماتيكي.

---

## طريقة التنفيذ

### الخطوة 1: تنفيذ سكريبت PowerShell

1. **افتح PowerShell**
   - اضغط `Win + X`
   - اختر **Windows PowerShell**

2. **انسخ والصق الكود التالي**

```powershell
$Desktop = [Environment]::GetFolderPath('Desktop')
$ShortcutPath = "$Desktop\This PC.lnk"
$WshShell = New-Object -ComObject WScript.Shell
$Shortcut = $WshShell.CreateShortcut($ShortcutPath)
$Shortcut.TargetPath = 'explorer.exe'
$Shortcut.Arguments = 'shell:MyComputerFolder'
$Shortcut.IconLocation = '%SystemRoot%\System32\imageres.dll,-107'
$Shortcut.Save()

Start-Sleep 2

$shell = New-Object -ComObject Shell.Application
$Pinned = $shell.Namespace("$env:APPDATA\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar")
$Item = $Pinned.ParseName((Split-Path $ShortcutPath -Leaf))

if ($Item) { 
    $Item.InvokeVerb('taskbarpin') 
} else { 
    Write-Host 'اختصار موجود بس مش مثبت، ثبت يدوي' 
}

Write-Host '✅ تم الإنشاء والتثبيت!' -ForegroundColor Green
```

3. **اضغط Enter**

---

### الخطوة 2: تخصيص الأيقونة (اختياري)

1. **ابحث عن الاختصار على سطح المكتب**
   - ستجد ملف `This PC.lnk`

2. **غيّر الأيقونة**
   - كليك يمين على الاختصار
   - اختر **Properties**
   - اضغط على **Change Icon**
   - اختر الأيقونة اللي تحبها
   - اضغط **OK** ثم **Apply**

3. **ثبّت على Taskbar**
   - كليك يمين على الاختصار
   - اختر **Pin to taskbar**

---

## ما يفعله السكريبت

1. ينشئ اختصار `This PC.lnk` على سطح المكتب
2. يربط الاختصار بـ `explorer.exe` مع `shell:MyComputerFolder`
3. يحدد الأيقونة الافتراضية للكمبيوتر من `imageres.dll`
4. يحاول تثبيته على Taskbar تلقائياً

---

## ملاحظات

- 📁 **سيظهر الاختصار على Desktop** بعد التنفيذ
- ⚡ **التثبيت التلقائي** قد لا يعمل في Windows 11 → ثبّت يدوياً
- 🎨 **يمكن تغيير الأيقونة** لأي أيقونة تفضلها
- ✅ **آمن تماماً**: لا يعدل أي إعدادات نظام

---

### بدائل للأيقونات

يملك ويندوز مجموعة كبيرة من الأيقونات المدمجة:

- `%SystemRoot%\System32\imageres.dll` (أيقونات عامة)
- `%SystemRoot%\System32\shell32.dll` (أيقونات نظام)
- `%SystemRoot%\explorer.exe` (أيقونات Explorer)

---

*تم الإضافة بتاريخ: 2026-01-08*
