# Setting up RDP for the runner

<br>

Fork this repository and run the Windows Runner workflow, then ssh in using the command it gives you.
<br>
After you have done that, execute cmd in the runner and run these commands.
```
wget -O C:/Windows/zrok.exe https://github.com/meownyaaa/rdp-windows-workflow/releases/download/august2025/zrok.exe#

C:/Windows/zrok.exe enable PUTYOURACCOUNTTOKENHERE

powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0

powershell.exe Enable-NetFirewallRule -DisplayGroup 'Remote Desktop'

powershell.exe Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1

powershell.exe Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText '@th1spmo' -Force)

C:/Windows/zrok.exe share private --backend-mode tcpTunnel localhost:3389
```

<br>

Commands taken from [here](https://github.com/CYB3RKING/RDP?tab=readme-ov-file#rdp-code).
<br>
Feel free to upload zrok somewhere else. 
# Connecting to RDP (you will need zrok on the connecting machine too!)
<br>

Run this on the machine you wish to connect from.
<br>

`zrok access private PUTRUNNERSTOKENHERE --bind localhost:33389`

<br>

Now, open RDP and connect using localhost:33389 and input the credentials.

<br>

Username: runneradmin
<br>
Password: @th1spmo

<br>

### You should now be in the runner's desktop, if you have done everything correctly!
<br>
<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/3e89a05e-70dc-490d-bf6e-0674f78374fe" />

<br>

Be aware that the windows runner only has 360 minutes of runtime (or 6 hours exactly)
<br><img width="155" height="89" alt="image" src="https://github.com/user-attachments/assets/2393cebe-4cbd-41df-9b6e-ccfb54a62557" />

# If you're confused with the token part

### "PUTYOURACCOUNTTOKENHERE"
<br>

Zrok should give you the enable command when you sign up. If you accidentally closed out of it or have used zrok before and have forgotten where it is;
<img width="1524" height="475" alt="image" src="https://github.com/user-attachments/assets/b66a8625-77a5-4442-8cd6-a0a330d69dfe" />#

### "PUTRUNNERSTOKENHERE"
<br>

The last characters on the "access your share" is the runner's token.
<img width="711" height="100" alt="image" src="https://github.com/user-attachments/assets/a72587b3-e059-4f7e-95dc-2cba0f8a3223" />











