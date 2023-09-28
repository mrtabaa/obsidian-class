- [ ] Open `MX Boot Options`  and set these values
![[MX-boot-options.png]]

- [ ] Go to `System Settings` => `Workspace Bahavior` => `Screen Edges` => Change`Activation delay` to `0`. 

- [ ] Go to `System Settings` => `Input Devices` => `Layouts` => `Main Shortcuts` => Change it to `Alt+Shift`

- [ ] Install Microsoft Fonts
```bash
sudo apt install ttf-mscorefonts-installer
```
- [ ] Change Star Menu layout => Right click on Start menu => Show Alternatives

- [ ] Open Volume/Sound and check `Raise maximum volume`

- [ ] From `Conkey Manager` un-check clock and check the `MX-Full` option

- [ ] Update MX Linux
	1. Set Google DNS to bypass the Iran's internet issue.
		* Set these value in DNS settings: `8.8.8.8, 8.8.4.4`
		![[network-dns-settings.jpg]]

		* Restart your WiFi (Internet connection)

		* Check if the new DNS is used: (My WiFi name is Connection_5G )
		![[network-dns-used.jpg]]
		

	2. Get available updates
	```bash
	sudo apt update
	```
	
	3. Check upgradable items (optional)
	```bash
		apt list --upgradable
	```

	4. Install the updates
	```bash
	sudo apt upgrade
	```

- [ ] After installing Google Chrome, fix the updating error of `sudo apt update`
	1.  Open `google.chrome.list`
	```bash
	sudo nano /etc/apt/sources.list.d/google.chrome.list
	```
	2. Now add `[arch=amd64]` like below:
	```bash
	deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
	```
	3. Save by => ctrl+o => ctrl+x


- [ ] Allow KDE Connect ports in MX Firewall
```bash
sudo ufw allow 1714:1764/udp
sudo ufw allow 1714:1764/tcp
sudo ufw reload
```

- [ ] More KDE setting at [KDE Store](https://store.kde.org/browse/)

- [ ] After installing your apps, back up your system with **TimeShift** (DON'T run TimeShift without its **Wizard!**)