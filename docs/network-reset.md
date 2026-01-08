# إعادة تعيين الشبكة

## عبر Settings

1. اذهب إلى **Settings** → **Network & Internet** → **Status**
2. اختر **Network reset**
3. اختر **Reset now**
4. أعد التشغيل

## عبر PowerShell

```powershell
ipconfig /release
ipconfig /renew
ipconfig /flushdns
```