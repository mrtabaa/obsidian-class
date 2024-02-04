- [ ] Download [Postman from here](https://dl.pstmn.io/download/latest/linux_64)
- [ ] Unzip it 
- [ ] Move the `Postman` folder to `Documents`
- [ ] Get this `postman-icon`
![[postman-icon]]
- [ ] Move `postman-icon` in the `Documents/Postman` folder 
- [ ] In `terminal`
```bash
cd /usr/share/applications && sudo nano postman.desktop
```
- [ ] Paste this to terminal
```js
[Desktop Entry]
Name=Postman
Comment=Client
Exec=~/Documents/Postman/app/Postman
Icon=~/Documents/Postman/postman-icon
Terminal=false (or true for terminal apps)
Type=Application
Categories=Category1;Category2;...
```
Now you have it in your Application Menu