- [x] Open `MX Boot Options`  and set these values
![[MX-boot-options.png]]

- [x] Go to `System Settings` => `Workspace Bahavior` => `Screen Edges` => Change`Activation delay` to `0`. 

- [x] Go to `System Settings` => `Input Devices` => `Layouts` => `Main Shortcuts` => Change it to `Alt+Shift`

- [x] Install Microsoft Fonts
```bash
sudo apt install ttf-mscorefonts-installer
```
- [ ] Install [[Codex Installer]]

- [x] Change Star Menu layout => Right click on Start menu => Show Alternatives

- [x] Open Volume/Sound and check `Raise maximum volume`

- [x] From `Conkey Manager` un-check clock and check the `MX-Full` option

- [x] Update MX Linux from here: [[MX Update]]

- [ ] Allow KDE Connect ports in MX Firewall **(If using KD Connect with Android/iOS)**
```bash
sudo ufw allow 1714:1764/udp
sudo ufw allow 1714:1764/tcp
sudo ufw reload
```

- [ ] Install your needed apps from [[Linux apps]]

- [ ] After installing your apps, back up your system with **TimeShift**

- [ ] More KDE setting at [KDE Store](https://store.kde.org/browse/)