
After installing Google Chrome, fix the updating error of `sudo apt update`
1. Execute this code in Terminal
	```bash
sudo rm /etc/apt/sources.list.d/chrome-remote-desktop.list
echo "deb http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list  
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
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