### Get `OpenApi` doc and copy to `Postman`
1. Run the project and go to 
```url
https://localhost:5001/openapi/v1.json
```
2. Download the json file or copy the `Raw Data`
3. Import it in `Postman`

### Show in Swagger UI
2. In `WebApi`
```plaintext
Swashbuckle.AspNetCore.SwaggerUI
```

2. In `Program.cs`
```c#
// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.MapOpenApi();
    app.UseSwaggerUI(
        options =>
        {
            options.SwaggerEndpoint("/openapi/v1.json", "Ca.WebApi");
        }
    );
}
```
3. Run the app and go to
```url
https://localhost:5001/swagger/index.html
```

If not available add these to `launchSettings.json` then step 3
![[Pasted image 20250604220750.png]]