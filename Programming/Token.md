#### Create and Use Token
1. Install `System.IdentityModel.Tokens.Jwt` from **Nuget Gallery**
2. Place these files in `Interfaces` and `Services` folders. [[TokenService.zip]]
3. Register TokenService in `Program.cs`
```C#
string? tokenValue = config[AppVariablesExtensions.TokenKey];

if (tokenValue is not null)
{
	services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
		.AddJwtBearer(options =>
		{
			options.TokenValidationParameters = new TokenValidationParameters
			{
				ValidateIssuerSigningKey = true,
				IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(tokenValue)),
				ValidateIssuer = false,
				ValidateAudience = false
			};
		});
}
```
4. 