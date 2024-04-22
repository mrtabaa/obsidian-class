Check [NVM latest version](https://github.com/nvm-sh/nvm/releases)

- [ ] e.g. Installing NVM version 0.39.3
```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.39.4/install.sh | bash
```
- [ ] Reset terminal
```bash
source ~/.bashrc
```
- [ ] Check the installed version
```bash
nvm --version
```
- [ ] See all available `NPM / NodeJs` (VPN in terminal is needed)
```bash
nvm ls-remote
```
- [ ] Install the LTS version (for example v20.12.2)
```bash
nvm install 20.12.2
```
- [ ] Set the installed node as default. Run it at once.
```bash
nvm alias default 20.12.2 # set as default
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
source ~/.bashrc
```

Back to [[Install and Create Angular Project]]
