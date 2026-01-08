# تعطيل Fullscreen Optimizations (للألعاب)

## عبر Registry (Global)
```powershell
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_FSEBehaviorMode" -Value 2
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_HonorUserFSEBehaviorMode" -Value 1
Set-ItemProperty -Path "HKCU:\System\GameConfigStore" -Name "GameDVR_DXGIHonorFSEWindowsCompatible" -Value 1
```

## Per Game
1. كليك يمين على .exe اللعبة
2. Properties → Compatibility
3. فعّل **Disable fullscreen optimizations**

## ملاحظات
- يحسن FPS
- يقلل Input Lag