# This PC on Taskbar

PowerShell:

```ps1
$D = [Environment]::GetFolderPath('Desktop')
$P = "$D\PC.lnk"
$W = New-Object -ComObject WScript.Shell
$S = $W.CreateShortcut($P)
$S.TargetPath = 'explorer.exe'
$S.Arguments = 'shell:MyComputerFolder'
$S.IconLocation = '%SystemRoot%\System32\imageres.dll,-107'
$S.Save()
Start-Sleep 1
$A = New-Object -ComObject Shell.Application
$Pinned = $A.Namespace("$env:APPDATA\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar")
$Item = $Pinned.ParseName((Split-Path $P -Leaf))
if ($Item) { $Item.InvokeVerb('taskbarpin') }
Write-Host 'OK'
```
