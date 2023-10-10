
- [x] [Install .NET-Core SDK](https://learn.microsoft.com/en-us/dotnet/core/install/linux-debian)
	1. Run this command
	```bash
	wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
	sudo dpkg -i packages-microsoft-prod.deb
	rm packages-microsoft-prod.deb
	```
	2. Now install the SDK
	```bash
	sudo apt-get update && \
	  sudo apt-get install -y dotnet-sdk-7.0
	```

- [x] Install .NET-Core Runtime (On real server ONLY)
```bash
sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-7.0
```

- [ ] [[VSCode Setup]]

- [x] [[Install MongoDB]]

- [x] [[Install and Create Angular Project]]

- [ ] Create an API and set debugger [[New-sln,-API]]

- [x] Setup [[GitHub]]

- [x] [[Update Node & Angular]] if needed

- [ ] Install [Authentication.JwtBearer and MongoDriver](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/api.csproj) from NuGet

- [x] Write Requirements

- [x] Desing Project Pages

- [x] Design MongoDB pattern [[Pattern & Schema]]

- [x] Connect MongoDb [[Setup in Project]]

- [ ] Create API [Extension files](https://github.com/mrtabaa/HealthApp/tree/dotnet6/api/Extensions) 

- [x] [[Setup Cors]]

- [x] Check to see if your [[Program.cs]] code looks good.

- [x] **If using code Extensions**, replace auto-generated **Program.cs** codes with [Program.cs](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Program.cs) to add [Extension files](https://github.com/mrtabaa/HealthApp/tree/dotnet6/api/Extensions) and organization.

- [ ] [[Install SSL]]

- [ ] Create [[TokenService]]

- [ ] Add [TokenKey and MongoConnection](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/appsettings.Development.json) if not added

- [ ] Double-check [[CancellationToken]] on all repos

- [ ] Property validations

- [ ] Controllers Authorizations by **Microsoft.AspNetCore.Authentication.JwtBearer** by Microsoft

- [ ] [Repository Example](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Repositories/LabsRepository.cs) for Db CRUD and TokenService

- [ ] Angular Examples: [Directive, Modules, Services](https://github.com/mrtabaa/HealthApp/tree/dotnet6/client/src/app)

- [ ] Dockerhub & gitLab

- [ ] Traffic for cyber security
