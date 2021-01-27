# Sort out the wireless drivers 

sudo apt install wpasupplicant


```yaml
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp2s0:
      dhcp4: true
  wifis:
    wlp5s0:
      dhcp4: yes
      access-points:
        "<wifi SSID>":
          password: "<password>"                        
  version: 2

```

# Dependencies for DWM

```
sudo apt install xorg stterm suckless-tools build-essential libx11-dev libxinerama-dev libxft-dev git vim libwebkit2gtk-4.0-dev
reboot
```

Uninstall gdm3 to stop collisions with dwm (gdm3 is the lightweight desktop env)

```
sudo apt remove gdm3
reboot
```


# setup dwm and compile


```
git clone https://git.suckless.org/dwm
cd dwm
sudo make clean install
```

make generates config.h, settings can now be applied.


# setup .xinitrc

xrandr is used to set resolution. Using scale as im on a tv monitor. 

```
cat <<EOF > vi .xinitrc
xrandr --output HDMI-1 --scale 0.6x0.6
exec dwm
EOF

echo 'startx' >  vi ~/.bash_profile
reboot
```

# setup st

```
git clone https://git.suckless.org/st
cd st/
sudo make clean install
sudo vi config.h 
sudo make clean install
```

# install google-chrome

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb 
```

# set sound device

```
pactl list sinks | less
pactl set-default-sink 3
pactl set-sink-volume 3 25000
```

# configure bat

```
sudo apt install bat
mkdir -p ~/.local/bin
ln -s /usr/bin/batcat ~/.local/bin/bat
``` 

# configure github
