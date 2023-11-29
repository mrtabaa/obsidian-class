#### APPLICATIONS
----------------
##### Website Packages
- [ ] [AppImageLauncher - bionic_amd64.deb](https://github.com/TheAssassin/AppImageLauncher/releases)

- [ ] [VS Code - .deb](https://code.visualstudio.com/download)

- [x] [Xtreme Downloader Manager](https://github.com/subhra74/xdm/releases)

- [x] [RClone Browser](https://rclone.org/downloads/) and [YouTube setup tutorial](https://youtu.be/ff8Ogk8NIPU)

- [x] [Ledger](https://www.ledger.com/ledger-live)

- [ ] [Google Chorme](https://www.google.com/chrome/)
	- [ ] Fix Google Chrome update
	```bash
echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list
	```
	To stop Chrome from getting updated automatically:
	```bash
cd /etc/apt/sources.list.d
sudo mv google-chrome.list google-chrome.list.save
	```

##### APT Packages
- [ ] Git
```bash
sudo apt install git
```

- [ ] Synaptic package
```bash
sudo apt install synaptic
```

BirdTray for Thunderbird (Email client)
```bash
sudo apt install birdtray
```

##### MX Package Installer

- [x] Kdenlive

- [x] VidCutter

- [x] Audacity

- [x] Gimp

- [x] OBS Studio

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

- [ ] Postman (similar to ThunderClient)
```bash
sudo snap install postman
```

VidCutter
```bash
sudo snap install vidcutter
```

Go back to [[0- MX Config]]

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
