# إزالة Microsoft OneNote بالقوة

هذا الأمر يقوم بأخذ الملكية (Ownership) ومنح صلاحيات كاملة، ثم حذف ملف `ONENOTE.EXE` بشكل نهائي.

## الكود (CMD)

افتح CMD كمسؤول (Run as Administrator) والصق الأمر التالي:

```cmd
takeown /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /A & icacls "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /grant Administrators:F & taskkill /F /IM OneNote.exe 2>nul & del /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE"
```

## بديل PowerShell

إذا كنت تفضل PowerShell:

```powershell
takeown /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /A; icacls "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /grant Administrators:F; Stop-Process -Name "OneNote*" -Force -EA 0; Remove-Item "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" -Force
```

## ملاحظات

- يجب تشغيل CMD أو PowerShell كمسؤول
- يغلق OneNote قبل الحذف تلقائياً
- الأمر يحذف ملف التنفيذ فقط (OneNote لن يعمل)
- مناسب لإصدارات Office المثبتة مع Windows 11 IoT LTSC

---

*تم الإضافة بتاريخ: 2026-01-08*
