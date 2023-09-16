Add this code to `programm.cs`
```c#
services.AddCors(options => {
            options.AddDefaultPolicy(policy => policy.AllowAnyHeader()
                .AllowAnyMethod().WithOrigins("https://localhost:4200"));
        });
```

Also add this **Cors** like this
```C#
app.UseHttpsRedirection();

app.UseCors(); // this line is added

app.UseAuthentication();
```

Back to [Project Steps](obsidian://open?vault=Advance%20Class&file=Programming%2F0%20-%20Project%20Steps)