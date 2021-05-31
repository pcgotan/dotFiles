# Initial Setup
## Install i3wm
```
sudo apt-get install i3
```
## Enable TouchPad
```
# make a file -> /etc/X11/xorg.conf.d/90-touchpad.conf
# and paste code below

Section "InputClass"
        Identifier "touchpad"
        MatchIsTouchpad "on"
        Driver "libinput"
        Option "Tapping" "on"
        Option "TappingButtonMap" "lrm"
        Option "NaturalScrolling" "on"
        Option "ScrollMethod" "twofinger"
EndSection
```

## Install Feh
```
sudo apt-get install feh
```
## Install xbacklight
```
sudo apt-get install xbacklight

# A little configuration needs to be done
# Make sure the output of "sudo cat /etc/X11/xorg.conf" should be

Section "Device"
    Identifier  "Intel Graphics" 
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection

# Find the directory for the backlight settings
sudo find /sys/ -type f -iname '*brightness*'

# Now link the output to /sys/class/backlight as given below
sudo ln -s /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight  /sys/class/backlight
```
For more details visit [here](https://askubuntu.com/questions/715306/xbacklight-no-outputs-have-backlight-property-no-sys-class-backlight-folder)  

## Enable the media buttons
```
# Install libplayerctl and playerctl from the given links or packages available in the playerctl directory

wget http://ftp.nl.debian.org/debian/pool/main/p/playerctl/libplayerctl2_2.0.1-1_amd64.deb
wget http://ftp.nl.debian.org/debian/pool/main/p/playerctl/playerctl_2.0.1-1_amd64.deb
sudo dpkg -i libplayerctl2_2.0.1-1_amd64.deb playerctl_2.0.1-1_amd64.deb
```

## Increase the swap (virtual memory)
```
# check how much you have
free -h

# if needs to be incresed then
sudo swapoff /swapfile
sudo fallocate -l 8G /swapfile
# check it
ls -lh /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

# To utilise the maximum RAM, decrease the swapiness
# Check it how much it is
cat /proc/sys/vm/swappiness

# if it is 60, decrease it to 10
# insert the following line at the end of the /etc/sysctl.conf
vm.swappiness=10

# Reboot
```

## Things to remember
- Don't forget to sudo chmod +x [net-speed.sh](../i3status/net-speed.sh)