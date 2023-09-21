- [ ] Open `MX Boot Options`  and set these values
![[MX-boot-options.png]]

- [ ] Go to `System Settings` => `Workspace Bahavior` => `Screen Edges` => Change`Activation delay` to `0`. 

- [ ] Go to `System Settings` => `Input Devices` => `Layouts` => `Main Shortcuts` => Change it to `Alt+Shift`

- [ ] Open Volume/Sound and check `Raise maximum volume`

- [ ] Update MX Linux
	1. Get available updates
	```bash
	sudo apt update
	```
	
	2. Check upgradable items (optional)
	```bash
		apt list --upgradable
	```

	3. Install the updates
	```bash
	sudo apt upgrade
	```

- [ ] Fix Google Chrome error on `sudo apt update` (if any)
	1.  Open `google.chrome.list`
	```bash
	sudo nano /etc/apt/sources.list.d/google.chrome.list
	```
	2. Now add `[arch=amd64]` like below:
	```bash
	deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
	```
	3. Save by => ctrl+o => ctrl+x


- [ ] After installing your apps, back up your system with **TimeShift** (DON'T run TimeShift without its **Wizard!**)