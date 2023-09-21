# Client
1. Get `server.crt` & `server.key` from [[ssl-certificates.zip]]

2. Create a **ssl** folder in **client** folder.

3. Copy the `server.crt` & `server.key` into the **ssl** folder.

4. Add `options` to **angular.json** under `serve` section like below
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
1. Make Linux trust dotnet certificates
```bash
sudo dotnet dev-certs https --trust
```

2. Get `server.crt` & `server.key` from [[ssl-certificates.zip]]
3. Go to **ssl-certificates** folder and open a Terminal.
4. Run this command:
##### Ubuntu / Debian
```bash
sudo cp server.crt /usr/local/share/ca-certificates/server.crt
```
4. Update OS certificates list
```bash
sudo update-ca-certificates
```

1. Follow code below and change **http** to **https** in `Program.cs` **OR** [ApplicationServiceExtensions.cs](https://github.com/mrtabaa/hallboard/blob/master/api/Extensions/ApplicationServiceExtensions.cs) links to https
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