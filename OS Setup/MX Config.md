- [ ] Open `MX Boot Options`  and set these values
![[MX-boot-options 1.png]]


- [ ] Fix Google Chrome error on `sudo apt update`
	1.  Open `google.chrome.list`
	```bash
	sudo nano /etc/apt/sources.list.d/google.chrome.list
	```
	2. Now add `[arch=amd64]` like below:
	```bash
	deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
	```
	3. Save by => ctrl+o => ctrl+x

