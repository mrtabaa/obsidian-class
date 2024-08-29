Fast Node Manager

- [ ] e.g. Installing NVM version 0.39.3
```bash
# installs fnm (Fast Node Manager)
curl -fsSL https://fnm.vercel.app/install | bash

# download and install Node.js
fnm use --install-if-missing 20

# verifies the right Node.js version is in the environment
node -v # should print `v20.16.0`
```
- [ ] Reset terminal
```bash
source ~/.bashrc
```
- [ ] Check the installed version
```bash
fnm --version
```
- [ ] See all available `NPM / NodeJs` (VPN in terminal is needed)
```bash
fnm ls-remote
```
- [ ] Install the LTS version (for example v20.16.0)
```bash
fnm install 20
```
- [ ] Set the installed node as default. Run it at once.
```bash
fnm default 20.16.0 # set as default
source ~/.bashrc
```

Back to [[Install and Create Angular Project]]
