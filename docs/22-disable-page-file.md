# تعطيل Page File (لل RAM العالية)

## عبر GUI
1. Win + R → `sysdm.cpl`
2. Advanced → Performance Settings
3. Advanced → Change
4. أزل علامة Automatically manage
5. اختر **No paging file**
6. Set → OK
7. أعد التشغيل

## عبر PowerShell
```powershell
wmic computersystem set AutomaticManagedPagefile=False
wmic pagefileset delete
```

## ملاحظات
⚠️ **تحذير**: فقط للأجهزة بـ RAM أكثر من 16GB
- يحرر مساحة على القرص
- قد يسبب أخطاء إذا امتلأ الرام