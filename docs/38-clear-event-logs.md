# مسح Event Logs

## مسح كل Logs
```powershell
wevtutil el | Foreach-Object {wevtutil cl "$_"}
```

## مسح Application Log فقط
```powershell
wevtutil cl Application
```

## ملاحظات
- يحرر مساحة
- ينظف النظام