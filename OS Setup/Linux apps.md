#### APPLICATIONS
----------------
##### DNF/APT Packages

- [ ] [Install .NET-Core SDK](https://learn.microsoft.com/en-us/dotnet/core/install/linux?WT.mc_id=dotnet-35129-website)
```bash
sudo dnf install dotnet-sdk-7.0
```

- [x] Install .NET-Core Runtime
```bash
sudo dnf install aspnetcore-runtime-7.0
```

- [ ] Tilix
```bash
sudo dnf install tilix
```

- [ ] Tweaks
```bash
sudo dnf install gnome-tweaks
```

- [ ] TimeShift
```bash
sudo dnf install timeshift
```

- [ ] xkill 
```bash
sudo dnf -y install xkill
```

- [ ] Git
```bash
sudo dnf install git
```

- [x] GParted
```bash
sudo dnf install gparted
```

- [x] Synaptic package (Ubuntu only)
```bash
sudo apt install synaptic
```

- [x] Featherpad (Ubuntu only)
```bash
sudo apt install featherpad
```

##### Flathub Packages
**https://flathub.org

- [x] obsidian
```bash
sudo flatpak install flathub md.obsidian.Obsidian
```

- [x] Kdenlive
```bash
sudo flatpak install flathub org.kde.kdenlive
```

- [x] VidCutter
```bash
sudo flatpak install flathub com.ozmartians.VidCutter
```

- [x] Audacity
```bash
sudo flatpak install flathub org.audacityteam.Audacity
```

- [x] Mailspring
```bash
sudo flatpak install flathub com.getmailspring.Mailspring
```

- [x] Gimp
```bash
sudo flatpak install flathub org.gimp.GIMP
```

- [x] OBS Studio
```bash
sudo flatpak install flathub com.obsproject.Studio
```

Fix OBS blank screen:
 1. Open `custom.conf`
```bash
sudo nano /etc/gdm/custom.conf
```
 2. Uncomment `WaylandEnable=false` by removing `#`
 3. ctrl+o => ctrl+x
 4. Reboot

- [ ] PeaZip
```bash
sudo flatpak install flathub io.github.peazip.PeaZip
```

- [ ] Postman
```bash
sudo flatpak install flathub com.getpostman.Postman
```

- [ ] VLC
```bash
sudo flatpak install flathub org.videolan.VLC
```

##### Snap Packages
1. Install `snapd` by this command
```bash
sudo dnf install snapd
```
2. Restart the computer
3. [Search for your software](https://snapcraft.io/)

##### Website Packages
- [x] [AppImageLauncher ](https://github.com/TheAssassin/AppImageLauncher/releases)

- [x] [Xtreme Downloader Manager](https://github.com/subhra74/xdm/releases)

- [x] [RClone Browser](https://rclone.org/downloads/) and [YouTube setup tutorial](https://youtu.be/ff8Ogk8NIPU)

- [x] [Ledger](https://www.ledger.com/ledger-live)

- [ ] [VS Code](https://code.visualstudio.com/download)

- [ ] Install [MongoDB Community Server](https://www.mongodb.com/try/download/community) (**Fedora**: RedHat/CentOS x64)
- [ ] Install [MongoDB Compose](https://www.mongodb.com/try/download/compass)
* Restart the computer to start the MongoDB server!

#### VPN:
--------------
1. Download [AppImage](https://github.com/Qv2ray/Qv2ray/releases/)
2. Download [Xray-linux-64.zip](https://github.com/XTLS/Xray-core/releases)

![[Qv2ray on Linux.mp4]]