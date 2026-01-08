# تفعيل High Performance CPU

## عبر Registry
```powershell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\54533251-82be-4824-96c1-47b60b740d00\0cc5b647-c1df-4637-891a-dec35c318583" -Name "ValueMax" -Value 0
```

## عبر Power Plan
1. Control Panel → Power Options
2. اختر High Performance
3. Change plan settings → Advanced
4. Processor power management
5. Minimum processor state: **100%**

## ملاحظات
- يستهلك طاقة أكثر
- يحسن الأداء بشكل كبير