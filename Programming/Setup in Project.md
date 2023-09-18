**appsettings.Development.json**

```js
"MongoDbSettings": {
	"ConnectionString": "mongodb://localhost:27017",
	"DatabaseName": "hallboard"
},
```

**Copy this Settings folder into API folder:**
[Settings.zip](obsidian://open?vault=obsidian-class&file=Programming%2Fhelpers%2FSettings.zip)

**dotnet 6+: Program.cs** or [**ApplicationServiceExtensions**](https://github.com/mrtabaa/HealthApp/blob/dotnet6/api/Extensions/ApplicationServiceExtensions.cs)

```C#
#region MongoDbSettings
///// get values from this file: appsettings.Development.json /////
// get section
builder.Services.Configure<MongoDbSettings>(builder.Configuration.GetSection(nameof(MongoDbSettings)));

// get values
builder.Services.AddSingleton<IMongoDbSettings>(serviceProvider =>
serviceProvider.GetRequiredService<IOptions<MongoDbSettings>>().Value);

// get connectionString to the db
builder.Services.AddSingleton<IMongoClient>(serviceProvider =>
{
    MongoDbSettings uri = serviceProvider.GetRequiredService<IOptions<MongoDbSettings>>().Value;


    return new MongoClient(uri.ConnectionString);
});
#endregion MongoDbSettings
```

**Use in Repository**

```C#
#region Db and Token Settings
    const string _collectionName = "users";
    private readonly IMongoCollection<AppUser>? _collection;
    private readonly ITokenService _tokenService; // save user credential as a token
    private readonly CancellationToken _cancellationToken;


    // constructor - dependency injection
    public AccountRepository(IMongoClient client, IMongoDbSettings dbSettings, ITokenService tokenService)
    {
        var database = client.GetDatabase(dbSettings.DatabaseName);
        _collection = database.GetCollection<AppUser>(_collectionName);
        _tokenService = tokenService;
        _cancellationToken = new CancellationToken();
    }
    #endregion
```


**OLD: dotnet 5: Startup.cs**
```C#
services.Configure<MongoDbSettings>(config.GetSection(nameof(MongoDbSettings)));

services.AddSingleton<IMongoClient>(serviceProvider => {
	var uri = serviceProvider.GetRequiredService<IOptions<MongoDbSettings>>().Value;

	return new MongoClient(uri.ConnectionString);
});
```

Back to [Project Steps](obsidian://open?vault=obsidian-class&file=Programming%2F0%20-%20Project%20Steps)
