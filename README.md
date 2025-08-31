# Setting up RDP for the workflow

<br>

Fork this repository (or ploosh's repository) and run the Windows Runner workflow, then ssh in using the command it gives you.
<br>
After you have done that, run these commands in the runner.
```
wget -O C:/Windows/zrok.exe https://github.com/meownyaaa/ssh-workflows/releases/download/august2025/zrok.exe
C:/Windows/zrok.exe enable ----------
powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0
powershell.exe Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1


run this command in powershell by executing "powershell" then pasting the line below;

Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "@th1spmo" -Force)

now run "exit" to go back to command prompt and run the last command.


C:/Windows/zrok.exe share private --backend-mode tcpTunnel localhost:3389
```

<br>

Commands taken from [here.](https://github.com/CYB3RKING/RDP?tab=readme-ov-file#rdp-code)
# Connecting to RDP (you will need zrok on your machine too!)
<br>

## Run this on the machine you're connecting from

`zrok access private replacewithtokenfromrunner --bind localhost:33389`

<br>

## Now, open RDP and connect using localhost:33389 and input the credentials.
<br>
Username: runneradmin
<br>
Password: @th1spmo
<br>
You should now be in the runner's desktop!
<br>
<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/3e89a05e-70dc-490d-bf6e-0674f78374fe" />

