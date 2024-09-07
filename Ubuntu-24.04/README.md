# Ubuntu 24.04 after Installations

## Update

```code
sudo apt update && sudo apt full-upgrade && sudo apt autoremove
```

## ESPHome interface for ESP32 MCU

```code
sudo usermod -a -G dialout $USER
```

## Some Extra Programs

### APT

```code
sudo apt install -y rpi-imager gparted putty filezilla fritzing dia handbrake brasero solaar 
```

### Snap

```code
sudo killall snap-store && sudo snap refresh
```

```code
sudo snap install -y pinta telegram-desktop
```

### LaserWeb/CNCWeb:

* Link:
  * [https://github.com/LaserWeb/LaserWeb4/wiki](https://github.com/LaserWeb/LaserWeb4/wiki)
  * [https://github.com/LaserWeb/LaserWeb4/wiki/1.3-Installation-on-Linux](https://github.com/LaserWeb/LaserWeb4/wiki/1.3-Installation-on-Linux)
* Short guide

Open the terminal window and enter:

```code
sudo apt-get update && sudo apt install npm
```

You can verify that npm and node are installed then by entering the following:

```code
npm -v 
```

```code
node -v 
```
The following were the version numbers returned at the time of this writing:

```code
npm - 8.5.1
node - 12.22.9
```

Then install Chromium by entering:

```code
sudo apt install chromium

```

Install git:

```code
sudo apt install git
```

Clone and build the latest lw.comm-server:

```code
cd /usr/local
```

```code
sudo git clone https://github.com/LaserWeb/lw.comm-server.git
```

```code
cd lw.comm-server
```

```code
sudo npm audit fix
```

```code
sudo npm install 
```

You can then test that the sever is working with:

```code
node server
```

Type CTRL-C to stop the server:

Then create a bash script for launchng the server and the browser:

```code
sudo nano startlw.sh
```

Copy and paste or type the following into the nano editor. Note that this script can be used with Chromium (recommended) or Firefox by uncommenting the correct line:

```txt
#!/bin/bash

# Start the Node.js server in the background
node /usr/local/lw.comm-server/server &

# Store the PID of the last background command (Node.js server)
server_pid=$!

#ONLY UNCOMMENT ONE OF THE FOLLOWING BROWSERS
# Uncomment the next line to launch Chromium browser pointing to localhost:8000
chromium --app=http://localhost:8000/ --start-maximized
# Uncomment the next line to launch Firefox browser pointing to localhost:8000
#firefox -new-window http://localhost:8000/

# Terminate the Node.js server
kill $server_pid
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

Then make the script executable and change the owner to your username (replace all the <username> below with your own Linux username):

```code
sudo chmod u+x startlw.sh 
```

```code
sudo chown <username>:<username> startlw.sh 
```

```code
sudo usermod -a -G dialout <username>
```

You should be able to launch LaserWeb fro the terminal then by entering:

```code
./startlw.sh
```

You are ok to close the terminal if everything worked.

You then can add an icon to your desktop by right clicking on the desktop and picking "Create a new launcher here" from the context menu.

For name use: LaserWeb4 For command use: /usr/local/lw.comm-server/startlw.sh

If you want to change the desktop icon there is one included in usr/local/lw.comm-server/build/ folder.

```code

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