# تعطيل كلمة المرور عند التسجيل

## الوصف
الدخول للويندوز بدون كلمة سر (استخدم بحذر!).

## الطريقة 1: Settings (الأسهل)

```
1. اضغط Win + I
2. روح: Accounts > Sign-in options
3. تحت "Password" اضغط "Remove"
4. أدخل كلمتك الحالية للتأكيد
5. اضغط "Next" ثم "Finish"
```

## الطريقة 2: netplwiz

```
1. اضغط Win + R وكتب netplwiz
2. اختر حسابك
3. الغي اختيار "Users must enter a user name and password to use this computer"
4. اضغط OK
5. أدخل كلمتك الحالية
6. اضغط OK
```

## الطريقة 3: Registry

```powershell
# PowerShell (Run as Admin)
Reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device" /v DevicePasswordLessBuildVersion /t REG_DWORD /d 0 /f
```

## الإعادة - إضافة كلمة سر

```
1. اضغط Win + I
2. روح: Accounts > Sign-in options
3. تحت "Password" اضغط "Add"
4. أدخل كلمة سر جديدة
5. اضغط Next ثم Finish
```

## تحذير
⚠️ خطر جداً على الجهاز المشترك! أي شخص يمكنه الدخول.
