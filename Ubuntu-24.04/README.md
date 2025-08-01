# Ubuntu 24.04 after Installations

## Update

```code
sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove -y
```

## Add some Directory

```code
mkdir -p ~/.local/bin && mkdir -p ~/.local/share/icons
```

## Firefox settings

* Generelt
  * Filhentning
    * Enable: Spørg mig altid, hvor filer skal gemmes
* Hjem
  * Startside og nye vinduer
    * Tilpassede URL'er..: https://www.google.dk/
    * Click: Anvend nuværende side

|Generelt|Hjem|
|:---:|:---:|
|![Generelt](./Images/Generelt-Filer_og_programmer.png)|![Hjem](./Images/Hejm-Hjem_Nye_vinduer_og_faneblade.png)|

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

## ESPHome interface for ESP32 MCU

```code
sudo usermod -a -G dialout $USER
```

## Some nice to have Programs

### APT

```code
sudo apt install -y rpi-imager geany gparted putty filezilla fritzing dia handbrake brasero solaar curl
```

### Snap

```code
sudo killall snap-store && sudo snap refresh
```

```code
sudo snap install pinta telegram-desktop
```

## [Install Flatpak](https://flathub.org/setup/Ubuntu)

* To install Flatpak on Ubuntu 18.10 (Cosmic Cuttlefish) or later, open the Terminal app and run:

```code
sudo apt install flatpak
```

## [PrusaSlicer 2.9.0](https://flathub.org/apps/com.prusa3d.PrusaSlicer)

* Manual Install
  * Make sure you follow the [setup guide for your Linux distribution](https://flathub.org/setup) before installing
  
```code
flatpak install flathub com.prusa3d.PrusaSlicer
```

* Run

```code
flatpak run com.prusa3d.PrusaSlicer
```

## AppImage

* [./AppImages.md](./AppImages.md)
  * [Where to place my AppImages files](./AppImages.md#where-to-place-my-appimages-files)
  * [AppImages Fuse](./AppImages.md#appimages-fuse)
  * [AppImages App](./AppImages.md#appimages-app)
  * [AppImages Icons](./AppImages.md#appimages-icons)
  * [AppImages Desktop Files](./AppImages.md#appimages-desktop-files)
    * [FreeCAD 1.0.0.](./AppImages.md#freecad_100-conda-linux-x86_64-py311appimage)
    * [Prusa Slicer 2.8.1](./AppImages.md#prusaslicer-281)
    * [UltiMaker-Cura-55.8.0-linux-X64](./AppImages.md#ultimaker-cura-5580-linux-x64)
    * [Kdenlive](./AppImages.md#kdenlive-ver-24080)
  * [How to make AppImage run as a Program](./AppImages.md#how-to-make-appimage-run-as-a-program)

### LaserWeb/CNCWeb (linux free alternative to lightburn)

* Lightburn:
  * [Lightburn Linux support Ending](https://forum.lightburnsoftware.com/t/linux-support-ending/144618)
* LaserWeb/CNCWeb (linux free alternative to lightburn)
  * [https://github.com/LaserWeb/LaserWeb4/wiki](https://github.com/LaserWeb/LaserWeb4/wiki)
  * [https://github.com/LaserWeb/LaserWeb4/wiki/1.3-Installation-on-Linux](https://github.com/LaserWeb/LaserWeb4/wiki/1.3-Installation-on-Linux)
  * [My Short guide](./LaserWeb-CNCWeb.md)

## Video Record, Screencast your keys and Edit

* [./VideoRecEdit.md](./VideoRecEdit.md)
  * [OBS-Studio](./VideoRecEdit.md#obs-studio)
  * [Screencast your keys](./VideoRecEdit.md#screencast-your-keys)
  * [Kdenlive](./VideoRecEdit.md#kdenlive) Use Appimages version

## Samba setup

* [./SambaSetup.md](./SambaSetup.md)
  * [Install Sanba](./SambaSetup.md#install-sanba)
  * [Directory to share files from](./SambaSetup.md#directory-to-share-files-from)
  * [Config Samba](./SambaSetup.md#config-samba)
  * [Edit /etc/samba/smb.conf](./SambaSetup.md#edit-etcsambasmbconf)
  * [Set Samba password](./SambaSetup.md#set-samba-password)
  * [Restart Samba](./SambaSetup.md#restart-samba)

## Do Not Suspend laptop when lid is closed in Ubuntu 24.04

Kilde: [https://askubuntu.com/](https://askubuntu.com/questions/1513028/suspend-laptop-when-lid-is-closed-in-ubuntu-24-04)

ændringer en linie i /etc/systemd/logind.conf

fra: 

```code
#HandleLidSwitch=suspend
```

til:

```code
HandleLidSwitch=ignore
```

After making changes, restart the login service:

```code
sudo systemctl restart systemd-logind
```

For mig var det nødvendigt at genstarte min PC !

