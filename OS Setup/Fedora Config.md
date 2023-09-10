#### Make DNF installer faster:
```bash
sudo nano /etc/dnf/dnf.conf
```
Add these lines at the end of the file
```
# Added for Speed:
fastestmirror=True
max_parallel_downloads=10
defaultyes=True
keepcache=True
```

Save by 
ctrl+o => Enter
ctrl+x

#### Install Media Codecs
[Multimedia Codecs - RPM Fusion](https://rpmfusion.org/Howto/Multimedia)

If didn't work use this:
[Installing plugins for playing movies and music](https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/)

#### Maintanance:
##### Clear cache sometimes
```bash
sudo dnf clean all
```
##### Update dnf
```bash
sudo dnf update
```

#### GNOME EXTENSIONS:
--------------
##### Installation
1. Install gnome-shell
```bash
sudo dnf install gnome-browser-connector
```

2. Install the browser's extension [Google Chrome](https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep) OR [Firefox](https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/)
##### Extensions
- [ ] ApplicationMenu
- [ ] AATWS - Advanced Alt-Tab Window Switcher (App Switcher => Default Filter => Current Workspace)
- [x] Auto Move Windows
- [ ] Clipboard Indicator
- [x] Just Perfection
- [ ] Launch new instance
- [ ] Removable Drive Menu
- [x] Remove dropdown arrows
- [ ] Resource Monitor
- [ ] Screenshot tool
- [x] Sound Input & Ouput Device chooser


#### Fix Angular Debugging on Chrome
To have Chorme trust ssl on **localhost**
[Click here](obsidian://open?vault=Advance%20Class&file=OS%20Setup%2FDebugger-setup)

