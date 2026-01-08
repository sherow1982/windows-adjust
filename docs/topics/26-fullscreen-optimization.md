# تحسين الألعاب (Fullscreen Optimization)

## الوصف
تحسين أداء الألعاب بتفعيل وضع الشاشة الكاملة.

## الطريقة 1: Registry

```powershell
# PowerShell (Run as Admin)
# تفعيل Fullscreen Optimizations
Reg add "HKCU\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 0 /f
Reg add "HKCU\SOFTWARE\Microsoft\DirectX\UserGlobalSettings" /v DisableFullscreenOptimizations /t REG_DWORD /d 0 /f
```

## الطريقة 2: Program Properties

```
1. Right Click على .exe للعبة
2. اختر "Properties"
3. اذهب لـ "Compatibility"
4. انقر "Change fullscreen optimizations"
5. اختر "Full Screen Optimizations" إلى ON
6. اضغط "Apply" ثم "OK"
```

## تعطيل Game Bar

```powershell
# تعطيل Game Bar الذي يستهلك موارد
Reg add "HKCU\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 0 /f
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\GameDVR" /v AppCaptureEnabled /t REG_DWORD /d 0 /f
```

## تحسينات أخرى للألعاب

```powershell
# تعطيل التطبيقات في الخلفية
Reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications" /v GlobalUserDisabled /t REG_DWORD /d 1 /f

# زيادة الأولوية للعبة
# اذهب لـ Task Manager أثناء لعب اللعبة
# Right Click على العملية > Set Priority > High أو Realtime
```

## الإعادة

```powershell
Reg add "HKCU\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 1 /f
Reg add "HKCU\SOFTWARE\Microsoft\DirectX\UserGlobalSettings" /v DisableFullscreenOptimizations /t REG_DWORD /d 1 /f
```

## ملاحظات
- Fullscreen Optimization يقلل تأخير الإدخال
- تأكد من تحديث برامج التشغيل (Drivers)
