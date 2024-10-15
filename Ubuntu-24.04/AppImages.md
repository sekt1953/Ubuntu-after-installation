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

## AppImages App

* Download link:
  * [FreeCAD 1.0.0 Release Candidate](https://github.com/FreeCAD/FreeCAD/releases)
  * [Prusa Slicer](https://www.prusa3d.com/page/prusaslicer_424/)
  * [UltiMaker-Cura](https://ultimaker.com/software/ultimaker-cura/#downloads)
  * [Kdenlive](https://kdenlive.org/en/download/)
* Download *.appimages to:

```txt
 ~/.local/bin
```

## AppImages Icons

|FreeCAD 1.0.0|PrusaSlicer|UltiMaker-Cura|Kdenlive|LaserWeb4|
|:---:|:---:|:---:|:---:|:---:|
|![FreeCAD 1.0.0](./Images/FreeCAD_0.22.png)|![PrusaSlicer](./Images/PrusaSlicer_128px.png)|![Cura](./Images/Cura.png)|![kdenlive](./Images/kdenlive_24.png)|![LaserWeb4](./Images/LaserWeb4.png)|

Download *.png to:

```txt
 ~/.local/share/icons
```

## AppImages Desktop Files:

### FreeCAD_1.0.0RC2-conda-Linux-x86_64-py311.AppImage

```code
nano ~/.local/share/applications/FreeCAD_1.0.0RC2.desktop
```

```txt
[Desktop Entry]
Type=Application
Comment=FreeCAD_1.0.0RC2
Name=FreeCAD_1.0.0RC2
Name[da_DK]=FreeCAD_1.0.0RC2
Categories=Graphics;Science;Engineering;
Icon=FreeCAD_0.22.png
Exec=FreeCAD_1.0.0RC2-conda-Linux-x86_64-py311.AppImage
Terminal=false
Name[da_DK]=FreeCAD_1.0.0RC1-conda-Linux-x86_64
StartupNotify=true
GenericName[da_DK]=CAD-program
```

* Save and Exit nano
  * To Save: [Ctrl]+[o]
  * To Exit: [Ctrl]+[w]

### PrusaSlicer 2.8.1

```code
nano ~/.local/share/applications/Prusa.desktop
```

```txt
[Desktop Entry]
Name=PrusaSlicer-2.8.1
Name[da_DK]=PrusaSlicer-2.8.1
Exec=PrusaSlicer-2.8.1+linux-x64-newer-distros-GTK3-202409181416.AppImage
Terminal=false
Type=Application
Icon=PrusaSlicer_128px.png
MimeType=x-scheme-handler/prusaslicer;
StartupNotify=false
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
