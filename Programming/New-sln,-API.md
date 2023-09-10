- [ ] Go to project root folder
- [ ] Create `sln` [only if](https://stackoverflow.com/questions/24436042/why-and-when-should-i-ever-be-using-sln-files)
```bash
dotnet new sln
```

- [ ] Create webapi:
```bash
dotnet new webapi -o api
```

- [ ] Add API to sln: 
```bash
dotnet sln add api
```

- [ ] Exclude `bin` and `obj` folders from VSCode File Explorer
![[exclude vscode folders.png]]

- [ ] Use this for `launchSettings.json` [like this](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Properties/launchSettings.json)

- [ ] In `appsettings.Development.json` change `Warning` to `Information`

- [ ] Create [api folders](https://github.com/mrtabaa/HealthApp/tree/dotnet6/api) only without their files.
* If want a shortcut, replace below folders/files with newly generated ones
<<[replace-with-current.zip](../media/replace-with-current.zip)>>

- [ ] Create [GlobalUsings.cs](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/GlobalUsing.cs) as shown in this git (**dotnet 6+**)

- [ ] Create [BaseApiController.cs](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Controllers/BaseApiController.cs)

- [ ] Setup Debugger for api and client [[Debugger-setup]]

Back to [Project Steps](obsidian://open?vault=Obsidian&file=Programming%2FProjects-Steps%2FProject%20Steps)