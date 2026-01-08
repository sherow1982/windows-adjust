# تعطيل UAC

## الطريقة الأولى: GUI

1. اضغط `Win + R` واكتب `msconfig`
2. اذهب إلى **Tools**
3. ابحث عن **Change UAC Settings**
4. حرك السلايدر للأسفل
5. اضغط OK وأعد التشغيل

## الطريقة الثانية: Registry

```powershell
reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v ConsentPromptBehaviorAdmin /t REG_DWORD /d 0 /f
```