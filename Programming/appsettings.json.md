1. In `api` folder => Create a file `appsettings.json` with this code:
This file is used for **Production**. 
```js
{
  "MongoDbSettings": {
    "ConnectionString": "mongodb://localhost:27017",
    "DatabaseName": "dating-app"
  },
  "TokenKey": "null",
  "Logging": {
    "LogLevel": {
      "Default": "Warning",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

Note: 
1. This file is added to `.gitignore` file so it does NOT get uploaded to `github`. **If not, add it yourself!**
2. `appsettings.Development.json` is used for **Development** only. Do NOT store secure values in it! 

Back to [[New-sln,-API]]