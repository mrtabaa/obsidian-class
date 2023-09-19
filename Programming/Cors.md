Open `programm.cs` and add this code after `MongoDB`
```C#
#region Cors: baraye ta'eede Angular HttpClient requests
builder.Services.AddCors(options =>
    {
        options.AddDefaultPolicy(policy => 
            policy.AllowAnyHeader().AllowAnyMethod().WithOrigins("https://localhost:4200"));
    });
#endregion Cors
```

Also add this **Cors** like this
```C#
app.UseHttpsRedirection();

app.UseCors(); // this line is added

app.UseAuthentication();
```

Back to [Project Steps](obsidian://open?vault=obsidian-class&file=Programming%2F0%20-%20Project%20Steps)