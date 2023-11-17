- [ ] Install the newer .NET Core version (In this example, the older version is 7.0)
```bash
	sudo apt-get update && \
	  sudo apt-get install -y dotnet-sdk-8.0
```

- [ ] See the installed .NET Core versions
```bash
dotnet --list-sdks
```

- [ ] To update your project
	1. Open `api.csproj` file.
	2. Change `net7.0` to `net8.0`

- [ ] Upgrade the **Microsoft** Nuget packages from `Nuget Gallery`

- [ ] Run your project and test it!!!

- [ ] Uninstall the older version. 
```bash
sudo apt purge dotnet-sdk-7.0 && sudo apt autoremove
```

Back to [[0 - Project Steps]]