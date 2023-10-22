Click here to see [[Why JWT (Token)]]

NOTE: **Token is set in `API` level**

#### Create and Use Token
1. **Command Palette** => **Nuget Gallery** => Install `System.IdentityModel.Tokens.Jwt`
2. Place these files in `Interfaces` and `Services` folders. [[TokenService.zip]]
3. `Program.cs` => Add this for dependency injection:
```c#
builder.Services.AddScoped<ITokenService, TokenService>();
```
4. Update your `UserDto` with Token like this:
```c#
public record UserDto(
    string Id,
    string Email,
    string Token
);
```

5. Inject `ITokenService` in your Repositories.
6. Update your returns like this:
```c#
UserDto userDto = new UserDto(
	Id: appUser.Id,
	Token: _tokenService.CreateToken(appUser),
	Email: appUser.Email // amir@gmail.com
);
```

Back to [[0 - Project Steps]]