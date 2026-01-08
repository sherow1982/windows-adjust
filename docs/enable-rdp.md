# تفعيل Remote Desktop

## الخطوات

1. اضغط `Win + Pause Break`
2. اختر **Advanced system settings**
3. اذهب إلى **Remote** tab
4. فعّل **Allow remote connections to this computer**
5. اضغط OK

## عبر PowerShell

```powershell
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name fDenyTSConnections -Value 0
```