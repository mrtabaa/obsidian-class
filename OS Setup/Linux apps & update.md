#### Linux Update and Cleanup
Keep your Linux and your apps updated and clean with these:
##### Update
```bash
# This will update your linux and apt applications
sudo apt update && sudo apt upgrade
```
##### Cleanup
```bash
sudo apt autoremove
```
```bash
sudo apt autoclean
```

#### APPLICATIONS
----------------
##### Main Apps
- [ ] [AppImageLauncher - bionic_amd64.deb](https://github.com/TheAssassin/AppImageLauncher/releases)

- [ ] Git
```bash
sudo apt install git
```
- [ ] [[Github Desktop]]

- [ ] Download `Deb` file: [Obsidian](https://obsidian.md/download)

- [ ] [[Upgrade .NET Core]]

- [ ]  [[NET Core]]

- [ ] A `NodeJs` manager:  [[NVM]] or [[FNM]] 

- [ ] [[Install and Create Angular Project]]

- [ ] [[MongoDB]]

- [ ] [Insomnia](https://insomnia.rest/download)

- [ ] [JetBrains Toolbox](https://www.jetbrains.com/toolbox-app/)
	- [ ] Install `Toolbox`
	- [ ] Install `Rider` (Use VPN or [Shecan DNS](https://shecan.ir/))
	- [ ] Apply these settings: [[Rider (JetBrain) Settings]]


- [ ] VSCode & [Extensions](https://docs.google.com/document/d/1sFEyufsm_JEGFfIeO0ezqVFUIw7tEc6Hgy3vS3PUFRA/edit?usp=sharing) (No need)
```bash
sudo apt install code
```
##### Other Apps
- [x] [Xtreme Downloader Manager](https://github.com/subhra74/xdm/releases)

- [x] [RClone Browser](https://rclone.org/downloads/) and [YouTube setup tutorial](https://youtu.be/ff8Ogk8NIPU)

	```
- [ ] Telegram
	1- Download 
	https://telegram.org/dl/desktop/linux
	
	2- Unzip
	3- Open Telegram
	
	4- Set proxy from here
	https://telegramlite.com/proxy-for-telegram
	** click on Connect

- [ ] OBS Studio
```bash
sudo apt install obs-studio
```
- [ ] Synaptic package
```bash
sudo apt install synaptic
```

BirdTray for Thunderbird (Email client)
```bash
sudo apt install birdtray
```

- [x] Kdenlive

- [x] VidCutter

- [x] Audacity

- [x] Gimp

- [x] VLC

##### Snap Packages
**[https://snapcraft.io](https://snapcraft.io/)**

1. Install Snapd
```bash
sudo apt install snapd
```
2. Install Snap's Core
```bash
sudo snap install core
```
3. VidCutter
```bash
sudo snap install vidcutter
```

##### Flathub Packages 
###### (NOT working in IRAN!)
**https://flathub.org

* Fix Flathub/Flatpak if needed
```bash
flatpak remote-delete --force flathub
flatpak remote-add --if-not-exists fedora oci+https://registry.fedoraproject.org
```

- [ ] Postman
```bash
flatpak install flathub com.getpostman.Postman
```
- [ ]  Mailspring (Email software)
```bash
flatpak install flathub com.getmailspring.Mailspring
```

#### VPN:
--------------

##### Method 1 (Iran)
Open this file for instructions [[Buying a VPN and activating it.docx]]

##### Method 2 (QV2RAY)
1. Download [AppImage](https://github.com/Qv2ray/Qv2ray/releases/)
2. Download [Xray-linux-64.zip](https://github.com/XTLS/Xray-core/releases)

![[Qv2ray on Linux.mp4]]
