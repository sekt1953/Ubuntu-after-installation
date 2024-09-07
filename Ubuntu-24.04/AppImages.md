# AppImages

## Where to place my AppImages files

```code
mkdir -p ~/.local/bin && mkdir -p ~/.local/share/icons
```

```code
PATH="$PATH:$HOME/bin"
```

## AppImages Fuse

```code
sudo apt install libfuse2t64
```

## AppImages App Icons

|FreeCAD 0.22.0dev|UltiMaker-Cura|LaserWeb4|Kdenlive|
|:---:|:---:|:---:|:---:|
|![FreeCAD 0.22.0dev](./Images/FreeCAD_0.22.png)|![Cura](./Images/Cura.png)|![LaserWeb4](./Images/LaserWeb4.png)|![kdenlive](./Images/kdenlive_24.png)|

Download *.png to:

```txt
 ~/.local/share/icons
```

## AppImages Desktop Files:

### FreeCAD 0.22.0dev-Linux-x86_64

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

### UltiMaker-Cura-55.8.0-linux-X64

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

### Kdenlive ver.: 24.08.0

```code
nano ~/.local/share/applications/kdenlive-24.08.0-x86_64.desktop
```

Content of file:

```text
[Desktop Entry]
Type=Application
Name=kdenlive-24.08.0-x86_64
Comment=kdenlive-24.08.0-x86_64
Categories=Graphics;Science;Engineering;
Icon=kdenlive_24.png
Exec=kdenlive-24.08.0-x86_64.AppImage
Terminal=false
Name[da_DK]=kdenlive-24.08.0-x86_64
StartupNotify=true

```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

## How to make AppImage run as a program

```code
chmod a+x ~/.local/bin/*.AppImage
```

```code
chmod a+x ~/.local/share/applications/*.desktop
```
