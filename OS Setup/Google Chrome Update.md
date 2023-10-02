
After installing Google Chrome, fix the updating error of `sudo apt update`
1. Execute this code in Terminal
	```bash

	```

2.  Open `google.chrome.list`using this command
	```bash
sudo nano /etc/apt/sources.list.d/google-chrome.list
	```

3. Now add `[arch=amd64]` like below:
	```bash
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
	```

4. Save by => ctrl+o => Enter => ctrl+x

Back to [[MX Config]]