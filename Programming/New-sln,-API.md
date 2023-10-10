- [x] Go to project root folder
- [x] Create `sln` [only if](https://stackoverflow.com/questions/24436042/why-and-when-should-i-ever-be-using-sln-files)
```bash
dotnet new sln
```

- [x] Create webapi:
```bash
dotnet new webapi -o api
```

- [x] Add API to sln: 
```bash
dotnet sln add api
```

- [x] Delete `WeatherForecast.cs` and `WeatherForecastController.cs`

- [x] Exclude `bin` and `obj` folders from VSCode File Explorer
![[exclude vscode folders.png]]

- [x] Use this for `launchSettings.json` [like this](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Properties/launchSettings.json)

- [x] In `appsettings.Development.json` change `Warning` to `Information`

- [x] Install official **Mongo Driver** in VSCode using **Nuget Gallery**

- [x] Create [api folders](https://github.com/mrtabaa/HealthApp/tree/dotnet6/api) only without their files.
* If want a shortcut, replace below folders/files with newly generated ones
<<[replace-with-current.zip](obsidian://open?vault=obsidian-class&file=Programming%2Fhelpers%2Freplace-with-current.zip)>>

- [x] Create [GlobalUsings.cs](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/GlobalUsing.cs) as shown in this git (**dotnet 6+**)

- [ ] Create [BaseApiController.cs](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Controllers/BaseApiController.cs)

- [x] Setup Debugger for api and client [[Programming/Debugger-setup]]

Back to [[0 - Project Steps]]