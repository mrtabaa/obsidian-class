**Fast Node Manager**

1. Install `FNM`
```bash
# installs fnm (Fast Node Manager)
curl -fsSL https://fnm.vercel.app/install | bash
```

2.  Reset terminal
```bash
source ~/.bashrc
```

3.  Check if `FNM` is installed
```bash
fnm --version
```

2.  Find the latest `NodeJs LTS`  version
```bash
fnm ls-remote
```

4. Install/Use: Change `22` to the latest `NodeJs LTS` version
```bash
# download and install Node.js
fnm use --install-if-missing 22
```

6. Check the installed `NodeJs` version
```bash
nvm list
```
```bash
npm version
```


NOTE: 
If you have multiple `NodeJs` installed on your machine, set one of them as default
```bash
fnm default 20.16.0 # set as default
source ~/.bashrc
```

4. Check in NodeJs is installed
```bash
node -v # should print `v20.16.0`
```

Back to [[Install and Create Angular Project]]
OR
Back to [[Linux apps]]