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

## LaserWeb/CNCWeb:

```txt
https://github.com/LaserWeb/LaserWeb4/wiki
```

```txt
https://github.com/LaserWeb/LaserWeb4/wiki/1.3-Installation-on-Linux
```

## Change to X11 from Wayland

```code
sudo nano /etc/gdm3/custom.conf
```

* Within this file, look for the line that says #WaylandEnable=false. You can uncomment this line and either set it to true or false, depending on whether you want Wayland enabled or not.  

* Disable Wayland:

```text
WayLandEnable=false
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

* After you have made the desired changes, save this file and exit it. You will need to restart GDM3 or reboot your Ubuntu 22.04 desktop for the changes to take effect.

```code
sudo systemctl restart gdm3
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

```code
nano ~/.local/share/applications/FreeCAD_0.22.0dev-Linux-x86_64.desktop
```

```txt
[Desktop Entry]
Type=Application
Name=FreeCAD_0.22.0dev-Linux-x86_64
Comment=FreeCAD_0.22.0dev-Linux-x86_64
Categories=Graphics;Science;Engineering;
Icon=FreeCAD_0.22.png
Exec=FreeCAD_weekly-builds-38555-conda-Linux-x86_64-py311.AppImage
Terminal=false
Name[da_DK]=FreeCAD_0.22.0dev-Linux-x86_64
StartupNotify=true
GenericName[da_DK]=CAD-program
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

#### UltiMaker-Cura-55.8.0-linux-X64

```code
nano ~/.local/share/applications/UltiMaker-Cura-5.8.0-linux-X64.desktop
```

```txt
[Desktop Entry]
Type=Application
Name=UltiMaker-Cura-5.8.0-linux-X64
Comment=UltiMaker-Cura-5.8.0-linux-X64
Exec=UltiMaker-Cura-5.8.0-linux-X64.AppImage
Name[da_DK]=UltiMaker-Cura-5.8.0-linux-X64
Icon=Cura.png
Categories=Categories=Graphics;2DGraphics;3DGraphics;RasterGraphics;GTK;
Terminal=false
StartupNotify=true
GenericName[da_DK]=CAD-program
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

### How to run an AppImage:

```code
chmod a+x ~/.local/bin/*.AppImage
```

```code
chmod a+x ~/.local/share/applications/*.desktop
```