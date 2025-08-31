### SSH Workflows

## When you need a certain OS but can't access it.

```
wget -O C:/Windows/zrok.exe https://github.com/meownyaaa/ssh-workflows/releases/download/august2025/zrok.exe
C:/Windows/zrok.exe enable ----------
powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0
powershell.exe Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1

run next line in powershell itself then exit back to cmd
Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "@th1spmo" -Force)

C:/Windows/zrok.exe share private --backend-mode tcpTunnel localhost:3389
```
