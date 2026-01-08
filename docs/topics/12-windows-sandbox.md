# تفعيل Windows Sandbox

## الوصف
تشغيل بيئة معزولة لاختبار البرامج بأمان.

## المتطلبات
- Windows 10/11 Pro, Enterprise أو Education
- معالج 64-bit يدعم Virtualization
- 4GB RAM كحد أدنى (8GB موصى به)
- 1GB مساحة قرص صلب

## التفعيل - الطريقة 1: Control Panel

```
1. اضغط Win وابحث عن "Turn Windows features on or off"
2. ابحث عن "Windows Sandbox"
3. ضع الـ checkmark
4. اضغط OK
5. أعد تشغيل الجهاز
```

## التفعيل - الطريقة 2: PowerShell

```powershell
# PowerShell (Run as Admin)
Enable-WindowsOptionalFeature -FeatureName Containers-DisposableClientVM -All -Online
```

## الاستخدام

```
1. اضغط Win وابحث عن "Windows Sandbox"
2. افتحه - سيأخذ بعض الوقت
3. بيئة محاكاة كاملة ستظهر
4. في الإغلاق، كل التغييرات ستُحذف
```

## حالات الاستخدام
- اختبار برامج غريبة
- فحص الملفات المريبة
- اختبار تثبيتات جديدة
- عزل البرامج الخطرة

## الإيقاف

```powershell
Disable-WindowsOptionalFeature -FeatureName Containers-DisposableClientVM -Online
```
