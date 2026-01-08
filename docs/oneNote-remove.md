# Remove OneNote

Open CMD as Administrator and run:

```cmd
takeown /F "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /A
```

Then: 

```cmd
icacls "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" /grant Administrators:F
```

Close OneNote and run:

```cmd
Remove-Item "C:\Program Files\Microsoft Office\root\Office16\ONENOTE.EXE" -Force
```
