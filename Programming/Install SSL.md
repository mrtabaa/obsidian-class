# Client
1- Get `server.crt` & `server.key` from [generateTrustedSSL](obsidian://open?vault=Advance%20Class&file=Programming%2Fhelpers%2FgenerateTrustedSSL.zip)

2- Create a **ssl** folder in **client** folder.

3- Copy the two files into your ssl folder.

4- Update your Program.cs or [ApplicationServiceExtensions.cs](https://github.com/mrtabaa/hallboard/blob/master/api/Extensions/ApplicationServiceExtensions.cs) links to https

5- Add this to **angular.json**
```json
"serve": {
	"builder": "@angular-devkit/build-angular:dev-server",
	"options": {
		"sslCert": "./ssl/server.crt",
		"sslKey": "./ssl/server.key",
		"ssl": true
},
```

# API
#### Linux:

1- In **terminal**:

cd Downloads/StudentAssets/generateTrustedSSL

2- Run this command:

##### ubuntu
```bash
sudo cp server.crt /usr/local/share/ca-certificates/server.crt
```
Update Certificates
```bash
sudo update-ca-certificates
```
##### Fedora
```bash
sudo cp server.crt /etc/pki/ca-trust/source/anchors/server.crt
```
Update Certificates
```bash
sudo update-ca-trust
```

3- Restart dotnet, ng, and the browser.

4- Exclude the project's **ssl** folder from github from client/**.gitignore** file for security. (See the video below)

Back to [Project Steps](obsidian://open?vault=Advance%20Class&file=Programming%2F0%20-%20Project%20Steps)