### Code Format Settings
##### C#:
In `Settings` => `Editor` => `Code Style` => `C#`
- [ ] In `Var usage declarations`
	Change all 3 items to `Use var when evident`
- [ ] In `Code body`
	Change all items to `Expression body`

##### General: 
Settings => `Tools` => `Actions on Save`
- [ ] `Reformat and Cleanup Code`


### Run/Debug Configuration:
##### api :
1. Add `dotnet-watch`
2. Name it `api`
3. Add these
	- [ ] `Suppress launching browser`
	- [ ] `Suppress browser refresh`
	- [ ] `Suppress hot reload`
	- [ ] `Always restart on rude edit`

##### Client:
1. Add `npm`
2. Name it `client`
3. Set the `package.json` of your project
4. Command: `start`
5. Node interpreter: `select the latest nvm node`
