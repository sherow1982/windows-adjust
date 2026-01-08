# إزالة Microsoft OneNote نهائياً

## الوصف
حذف تطبيق Microsoft OneNote بشكل كامل من النظام (للإصدار Desktop المدمج مع Office).

---

## طريقة التنفيذ

### الخطوات

1. **فتح CMD كمسؤول**
   - اضغط `Win + X`
   - اختر **Command Prompt (Admin)** أو **Windows PowerShell (Admin)**

2. **انسخ والصق الأمر التالي**

```cmd
takeown /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /A & icacls "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /grant Administrators:F & taskkill /F /IM "OneNote*" 2>nul & del /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE"
```

3. **اضغط Enter**

---

## ما يفعله الأمر

| الخطوة | الوصف |
|---------|--------|
| `takeown /F` | أخذ ملكية ملف ONENOTE.EXE |
| `icacls /grant` | إعطاء صلاحية التحكم الكامل |
| `taskkill /F` | إغلاق أي عملية OneNote قيد التشغيل |
| `del /F` | حذف ملف OneNote بشكل نهائي |

---

## ملاحظات مهمة

- ⚠️ **يجب تشغيل CMD كمسؤول**
- 📁 **المسار الافتراضي**: `C:\Program Files\Microsoft Office\root\Office16\`
- 🔄 **إذا كان Office 2019/2021**: قد يختلف المسار (تحقق من مجلد Office16 أو Office15)
- ✅ **آمن تماماً**: لا يؤثر على بقية تطبيقات Office

---

### للتحقق من المسار الصحيح

إذا لم يعمل الأمر، افتح File Explorer وابحث عن:

```
C:\Program Files\Microsoft Office\root\
```

ثم ادخل على المجلدات الموجودة لتحديد رقم إصدار Office وعدّل الأمر بناءً عليه.

---

*تم الإضافة بتاريخ: 2026-01-08*
