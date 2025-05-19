# 🛠️ Centralized Build and Package Setup (.NET 9)

This guide documents the shared configuration setup for the `ca-template` backend using `.NET 9`, with centralized `Directory.Build.props` and `Directory.Packages.props` files.

---

## 📁 Folder Structure

```plaintext
/backend/
  └── ca-template/
      ├── Directory.Build.props
      ├── Directory.Packages.props
      ├── ca-template.sln
      ├── Ca.Application/
      ├── Ca.Contracts/
      ├── Ca.Domain/
      ├── Ca.Infrastructure/
      ├── Ca.Shared/
      └── Ca.WebApi/
```

> 🧠 **Important**:  
> MSBuild only picks up `Directory.Build.props` and `Directory.Packages.props` **if they are placed directly in the solution root** (next to the `.sln` file).  
> It will **not work** if you place them inside a subfolder like `Build/`.

---

## ✅ Directory.Build.props

Used to define shared project settings across all `.csproj` files.

### ✅ Example:

```xml
<Project>  

    <PropertyGroup>  
        <TargetFramework>net9.0</TargetFramework>  
        <Nullable>enable</Nullable>  
        <LangVersion>latest</LangVersion>  
        <ImplicitUsings>enable</ImplicitUsings>  
    </PropertyGroup>  

	<!-- These items are applied to all projects-->
    <ItemGroup>  
        <PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" PrivateAssets="all" />  <!-- Without version -->
    </ItemGroup>  
    
</Project>
```

---

## ✅ Directory.Packages.props

Used to define and pin shared NuGet package versions.

### ✅ Example:

```xml
<Project>

	<PropertyGroup>
	    <ManagePackageVersionsCentrally>true</ManagePackageVersionsCentrally>
	</PropertyGroup>

	<ItemGroup>
		<PackageVersion Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="9.0.0" />
		<PackageVersion Include="Microsoft.AspNetCore.OpenApi" Version="9.0.4" />
	</ItemGroup>

</Project>
```

#### Then in `.csproj` files:
```xml

<PackageReference Include="Microsoft.AspNetCore.OpenApi" />
```

**Note:** No version number needed — it's pulled from `Directory.Packages.props`.

---

## ✅ Guidelines

| Task                                       | Do this                          |
| ------------------------------------------ | -------------------------------- |
| Share TargetFramework and language version | ✅ Use `Directory.Build.props`    |
| Share package versions                     | ✅ Use `Directory.Packages.props` |
| Use analyzers                              | ✅ Add them in `Build.props`      |
| Place props files in subfolders            | ❌ Not supported by MSBuild       |

---

## Cleanup
Open all `csproj` files and remove the unnecessary lines. 

## 🧼 Commands
After changing these files:
```bash
dotnet clean
dotnet build
```

Also consider restarting Rider if changes aren't picked up immediately.

---

## 🔍 Reference

- [MSBuild: Directory.Build.props](https://learn.microsoft.com/en-us/visualstudio/msbuild/customize-your-build?view=vs-2022)
- [.NET Analyzers](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/overview)
