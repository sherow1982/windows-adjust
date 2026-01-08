# إزالة مايكروسوفت ون نوت بالقوة (Force Remove OneNote)

## الوصف
أمر سطر واحد لإجبار حذف تطبيق OneNote (النسخة المكتبية) من جذوره في حال لم يتم حذفه بالطرق التقليدية.

## الكود (PowerShell)

قم بتشغيل PowerShell كمسؤول (Administrator) ونفض الأمر التالي:

```powershell
takeown /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /A; icacls "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /grant Administrators:F; Stop-Process -Name "OneNote*" -Force -EA 0; Remove-Item "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" -Force
```

## ملاحظات
- يجب تشغيل PowerShell بصلاحيات مسؤول
- الأمر يأخذ ملكية الملف ثم يحذفه نهائياً
- قد يتطلب إغلاق OneNote يدوياً إذا كان قيد التشغيل

---

*تم الإضافة بتاريخ: 2026-01-08*
