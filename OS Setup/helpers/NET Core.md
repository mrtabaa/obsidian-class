# Mint (Ubuntu based)

##### SDK (Development machine)
Change `8.0` to latest
```bash
sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-8.0
```

##### Runtime (Server only)
```bash
sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-8.0
```

Back to [[Linux apps & update]]

# MX Linux (Debian)
1. First run this command:
```bash
wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
``` 
2. Then install `SDK` or `Runtime`
##### SDK (Development)
Change `8.0` to latest
```bash
sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-8.0
```
##### Runtime (Server only)
```bash
sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-8.0
```

Back to [[Linux apps & update]]

# Upgrade
[[Upgrade .NET Core]]
