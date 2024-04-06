- [ ] Install VSCode extension `.NET Core User Secrets` by `Adrian Wilczyński`.
- [ ] Install Nuget Package `RefreshMicrosoft.Extensions.Configuration.UserSecrets` by Microsoft
- [ ] Right-click on `api.csproj` and use `Manage User Secrets`
- [ ] Set your variables. e.g. Generate a secure key [Key Generator](https://it-tools.tech/token-generator)
- [ ] Add this line to `Program.cs`
```C#
builder.Configuration.AddUserSecrets<Program>(); // Register User Secrets
```

- [ ] Build the app again. 