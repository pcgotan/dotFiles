# Windows configurations
To enable i3wm alike keyboard shortcuts.  

## Installation
```
AutoHotkey_1.1.33.09_setup.exe
```
## Usage
- **WindowsDesktopSwitcher** enables shortcut keys. Have a look at `user_config.ahk` file.
- **VirtualDesktopManager** shows which virtual desktop is currently showing in the taskbar.



## Run
Run `windowsDesktopSwitcher/desktop_switcher.ahk` and `VirtualDesktopManager/VirtualDesktopManager.exe`

## Startup
- Create a shortcut of `windowsDesktopSwitcher/desktop_switcher.ahk` and `VirtualDesktopManager/VirtualDesktopManager.exe`.
- Run (Win+R) shell:startup and paste those shortcuts in this directory. You are good to go.



# WSL2
WSL2 has separate network interface. That's why services running on Windows, are not accessible through localhost:port in wsl.
IP1 = (cat /etc/resolv.conf | grep nameserver)    # run on wsl2     
IP2 = ipconfig -> IPV4      # run on powershell    
Those services can be accessible by IP1:port or IP2:port     
But these ports must be allowed through firewall security    
To create a new inbound rule, open "Windows defender firewall with advanced security"   
Go to inbound rules -> New Rule -> port, tcp, specify port with comma (local), remote port (All), save
Second (Alternative) option -> "Allow an app through windows firewall" -> select app in C:\Program Files\**\bin\asdf.exe
restart the system
