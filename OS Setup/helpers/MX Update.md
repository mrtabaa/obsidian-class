1. Set Google DNS to bypass the Iran's internet problem:

	- [ ] Set these value in DNS settings: `8.8.8.8, 8.8.4.4`
		![[network-dns-settings.jpg]]

	- [ ] Restart your WiFi (Internet connection)

	- [ ] Check if the new DNS is used: (My WiFi name is Connection_5G )
		![[network-dns-used.jpg]]
		

2. Change MX Linux Mirror (Mirror is the server your Linux gets updates from)
	- [ ] Press `Super/Meta` key
	- [ ] Search for `MX Repo Manager`
	- [ ] Set the mirror to `Los Angeles` (or anywhere has faster download speed)
		![[mx-repo-manager.png]]

3. Get available updates
```bash
sudo apt update
```
	
4. Check what items are going to be updated (optional)
```bash
apt list --upgradable
```

5. Install the updates
```bash
sudo apt upgrade
```

Back to [[0- MX Config]]