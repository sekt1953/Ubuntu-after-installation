# Ubuntu 24.04 after Installations

## Update

```code
sudo apt update && sudo apt full-upgrade && sudo apt autoremove
```

## ESPHome interface for ESP32 MCU

```code
sudo usermod -a -G dialout $USER
```

## Some apt Extra Programs

```code
sudo apt install -y rpi-imager gparted putty filezilla fritzing dia handbrake brasero solaar 
```

## Some snap Extra Programs

```code
sudo killall snap-store && sudo snap refresh
```

```code
sudo snap install -y pinta telegram-desktop
```

## Wayland vs. X11

```code

```

## Samba setup

```code
sudo apt update && sudo apt install -y samba
```

```code
mkdir ~/sambashare
```

```code
sudo nano /etc/samba/smb.conf
```

###  Edit /etc/samba/smb.conf

```txt
[global]

### Browsing/Identification ###

# Change this to the workgroup/NT-domain name Samba server will part of
   workgroup = WORKGROUP
   server min protocol = NT1
```

```txt
[sambashare]
   comment = A Samba share on Ubuntu 24.04LTS
   path = /home/<userneme>/sambashare
   read only = no
   browsable = yes
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

### Set Samba password

```code
sudo smbpasswd -a <username>
```

### Restart Samba

```code
sudo service smbd restart
```

## AppImage

### Where to place my AppImages files

```code
mkdir -p ~/.local/bin && mkdir -p ~/.local/share/icons
```

```code
PATH="$PATH:$HOME/bin"
```

### AppImages Fuse

```code
sudo apt install libfuse2t64
```

### Add AppImages Icons

```code
mv ~/Hentet/*.png ~/.local/share/icons
```

### AppImages Desktop Files:

#### FreeCAD 0.22.0dev-Linux-x86_64

```txt

```

#### UltiMaker-Cura-55.8.0-linux-X64

```txt

```
