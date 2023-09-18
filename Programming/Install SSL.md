# Client
1. Get `server.crt` & `server.key` from [generateTrustedSSL](obsidian://open?vault=obsidian-class&file=Programming%2Fhelpers%2FgenerateTrustedSSL.zip)

2. Create a **ssl** folder in **client** folder.

3. Copy the two files into your ssl folder.

4. Add this to **angular.json**
```json
"serve": {
	"builder": "@angular-devkit/build-angular:dev-server",
	"options": {
		"sslCert": "./ssl/server.crt",
		"sslKey": "./ssl/server.key",
		"ssl": true
},
```
5. Exclude the project's **ssl** folder from github using **.gitignore** file for security. 

6. Restart Angular => `ng serve` again

# API
#### Linux:

1. Get your cert from [generateTrustedSSL](obsidian://open?vault=obsidian-class&file=Programming%2Fhelpers%2FgenerateTrustedSSL.zip)
2. Open Terminal in this folder.
3. Run this command:
##### ubuntu
```bash
sudo cp server.crt /usr/local/share/ca-certificates/server.crt
```
4. Update Certificates
```bash
sudo update-ca-certificates
```
##### Fedora 
```bash
sudo cp server.crt /etc/pki/ca-trust/source/anchors/server.crt
```
4. Update Certificates
```bash
sudo update-ca-trust
```
5. Follow code below and change **http** to **https** in `Program.cs` **OR** [ApplicationServiceExtensions.cs](https://github.com/mrtabaa/hallboard/blob/master/api/Extensions/ApplicationServiceExtensions.cs) links to https
```C#
#region Cors: baraye ta'eede Angular HttpClient requests
builder.Services.AddCors(options =>
    {
        options.AddDefaultPolicy(policy => 
            policy.AllowAnyHeader().AllowAnyMethod().WithOrigins("https://localhost:4200"));
    });
#endregion Cors
```

7. Restart `dotnet`, `ng serve`, and the `browser`.

Back to [Project Steps](obsidian://open?vault=obsidian-class&file=Programming%2F0%20-%20Project%20Steps)